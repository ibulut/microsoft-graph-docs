---
author: JeremyKelley
ms.author: JeremyKelley
ms.date: 09/10/2017
title: Access shared items
localization_priority: Normal
---
# Accessing shared DriveItems

Access a shared [DriveItem](../resources/driveitem.md) or a collection of shared items by using a **shareId** or sharing URL.

To use a sharing URL with this API, your app needs to [transform the URL into a sharing token](#encoding-sharing-urls).

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | Files.ReadWrite, Files.ReadWrite.All, Sites.ReadWrite.All    |
|Delegated (personal Microsoft account) | Files.ReadWrite, Files.ReadWrite.All    |
|Application | Files.ReadWrite.All, Sites.ReadWrite.All |

## HTTP request

<!-- { "blockType": "ignored" } -->

```http
GET /shares/{shareIdOrEncodedSharingUrl}
```

### Path parameters

| Parameter Name                 | Value    | Description                                                                         |
|:-------------------------------|:---------|:------------------------------------------------------------------------------------|
| **shareIdOrEncodedSharingUrl** | `string` | Required. A sharing token as returned by the API or a properly encoded sharing URL. |

### Encoding sharing URLs

To encode a sharing URL, use the following logic:

1. First, use base64 encode the URL.
2. Convert the base64 encoded result to [unpadded base64url format](https://en.wikipedia.org/wiki/Base64) by removing `=` characters
   from the end of the value, replacing `/` with `_` and `+` with `-`.)
3. Append `u!` to be beginning of the string.

As an example, to encode a URL in C#:

```csharp
string sharingUrl = "https://onedrive.live.com/redir?resid=1231244193912!12&authKey=1201919!12921!1";
string base64Value = System.Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(sharingUrl));
string encodedUrl = "u!" + base64Value.TrimEnd('=').Replace('/','_').Replace('+','-');
```

## Optional request headers

| Name       | Type   | Description                                                    |
|:-----------|:-------|:---------------------------------------------------------------|
| **Prefer** | string | Optional. Set to one of the `prefer` values documented below.  |

### Prefer header values

| Name                          | Description                                                                                             |
|:------------------------------|:--------------------------------------------------------------------------------------------------------|
| redeemSharingLink             | If the **shareIdOrEncodedSharingUrl** is a sharing link, grant the caller durable access to the item    |
| redeemSharingLinkIfNecessary  | Same as redeemSharingLink, but access is only guaranteed to be granted for the duration of this request |

redeemSharingLink should be considered equivalent to the caller navigating to the sharing link the browser (accepting the sharing gesture),
whereas redeemSharingLinkIfNecessary is intended for scenarios where the intention is simply to peek at the link's metadata.

## Response

If successful, this method returns a `200 OK` response code and a [sharedDriveItem](../resources/shareddriveitem.md) resource in the response body.

## Example

### Request

Here is an example of the request to retrieve a shared item:

<!-- { "blockType": "request", "name": "get-shared-root" } -->

```http
GET /shares/{shareIdOrEncodedSharingUrl}
```

### Response

Here is an example of the response.

<!-- { "blockType": "response", "truncated": true, "@odata.type": "microsoft.graph.sharedDriveItem" } -->

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "id": "B64397C8-07AE-43E4-920E-32BFB4331A5B",
  "name": "contoso project.docx",
  "owner": {
    "user": {
      "id": "98E88F1C-F8DC-47CC-A406-C090248B30E5",
      "displayName": "Ryan Gregg"
    }
  }
}
```
#### SDK sample code
# [C#](#tab/cs)
[!INCLUDE [sample-code](../includes/get-shared-root-Cs-snippets.md)]

# [Javascript](#tab/javascript)
[!INCLUDE [sample-code](../includes/get-shared-root-Javascript-snippets.md)]

# [Objective-C](#tab/objective-c)
[!INCLUDE [sample-code](../includes/get-shared-root-Objective-C-snippets.md)]
---

[!INCLUDE [sdk-documentation](../includes/snippets_sdk_documentation_link.md)]

## Access the shared item directly

While the [**SharedDriveItem**](../resources/shareddriveitem.md) contains some useful information, most apps will want to directly access the shared [DriveItem](../resources/driveitem.md).
The **SharedDriveItem** resource includes a **root** and **items** relationships which can access content within the scope of the shared item.

## Example (single file)

### Request

By requesting the **driveItem** relationship, the **DriveItem** that was shared will be returned.

<!-- { "blockType": "request", "name": "get-shared-driveitem" } -->

```http
GET /shares/{shareIdOrUrl}/driveItem
```

### Response

<!-- { "blockType": "response", "truncated": true, "@odata.type": "microsoft.graph.driveItem" } -->

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "9FFFDB3C-5B87-4062-9606-1B008CA88E44",
  "name": "contoso project.docx",
  "eTag": "2246BD2D-7811-4660-BD0F-1CF36133677B,1",
  "file": {},
  "size": 109112
}
```
#### SDK sample code
# [C#](#tab/cs)
[!INCLUDE [sample-code](../includes/get-shared-driveitem-Cs-snippets.md)]

# [Javascript](#tab/javascript)
[!INCLUDE [sample-code](../includes/get-shared-driveitem-Javascript-snippets.md)]

# [Objective-C](#tab/objective-c)
[!INCLUDE [sample-code](../includes/get-shared-driveitem-Objective-C-snippets.md)]
---

[!INCLUDE [sdk-documentation](../includes/snippets_sdk_documentation_link.md)]

## Example (shared folder)

### Request

By requesting the **driveItem** relationship and expanding the **children** collection, the **DriveItem** that was shared will be returned along with the files within the shared folder.

<!-- { "blockType": "request", "name": "get-shared-driveitem-expand-children" } -->

```http
GET /shares/{shareIdOrUrl}/driveItem?$expand=children
```

### Response

<!-- { "blockType": "response", "truncated": true, "@odata.type": "microsoft.graph.driveItem" } -->

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "9FFFDB3C-5B87-4062-9606-1B008CA88E44",
  "name": "Contoso Project",
  "eTag": "2246BD2D-7811-4660-BD0F-1CF36133677B,1",
  "folder": {},
  "size": 10911212,
  "children": [
    {
      "id": "AFBBDD79-868E-452D-AD4D-24697D4A4044",
      "name": "Propsoal.docx",
      "file": {},
      "size": 19001
    },
    {
      "id": "A91FE90A-2F2C-4EE6-B412-C4FFBA3F71A6",
      "name": "Update to Proposal.docx",
      "file": {},
      "size": 91001
    }
  ]
}
```
#### SDK sample code
# [C#](#tab/cs)
[!INCLUDE [sample-code](../includes/get-shared-driveitem-expand-children-Cs-snippets.md)]

# [Javascript](#tab/javascript)
[!INCLUDE [sample-code](../includes/get-shared-driveitem-expand-children-Javascript-snippets.md)]

# [Objective-C](#tab/objective-c)
[!INCLUDE [sample-code](../includes/get-shared-driveitem-expand-children-Objective-C-snippets.md)]
---

[!INCLUDE [sdk-documentation](../includes/snippets_sdk_documentation_link.md)]

## Error Responses

Read the [Error Responses][error-response] topic for more information about
how errors are returned.

## Remarks

* For OneDrive for Business and SharePoint, the Shares API always requires authentication and cannot be used to access anonymously shared content without a user context.

[error-response]: /graph/errors

<!-- {
  "type": "#page.annotation",
  "description": "Access the contents of a sharing link with the OneDrive API.",
  "keywords": "shares,shared,sharing,share link, sharing link, share id, share token",
  "section": "documentation",
  "tocPath": "Sharing/Use a link",
  "suppressions": [
    "Error: /api-reference/v1.0/api/shares-get.md:\r\n      BookmarkMissing: '[#tab/objective-c](Objective-C)'. Did you mean: #objective-c (score: 4)",
    "Error: /api-reference/v1.0/api/shares-get.md:\r\n      BookmarkMissing: '[#tab/cs](C#)'. Did you mean: #c (score: 5)",
    "Error: /api-reference/v1.0/api/shares-get.md:\r\n      BookmarkMissing: '[#tab/javascript](Javascript)'. Did you mean: #javascript (score: 4)",
    "Error: /api-reference/v1.0/api/shares-get.md:\r\n      BookmarkMissing: '[#tab/cs](C#)'. Did you mean: #c (score: 5)",
    "Error: /api-reference/v1.0/api/shares-get.md:\r\n      BookmarkMissing: '[#tab/javascript](Javascript)'. Did you mean: #javascript (score: 4)",
    "Error: /api-reference/v1.0/api/shares-get.md:\r\n      BookmarkMissing: '[#tab/cs](C#)'. Did you mean: #c (score: 5)",
    "Error: /api-reference/v1.0/api/shares-get.md:\r\n      BookmarkMissing: '[#tab/javascript](Javascript)'. Did you mean: #javascript (score: 4)"
  ]
} -->
