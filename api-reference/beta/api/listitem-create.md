---
author: JeremyKelley
ms.author: JeremyKelley
ms.date: 09/11/2017
title: Create a new entry in a SharePoint list
localization_priority: Normal
ms.prod: "sharepoint"
---
# Create a new item in a list

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Create a new [listItem][] in a [list][].

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | Sites.ReadWrite.All    |
|Delegated (personal Microsoft account) | Not supported.    |
|Application | Sites.ReadWrite.All |

## HTTP request

<!-- { "blockType": "ignored" } -->

```http
POST https://graph.microsoft.com/beta/sites/{site-id}/lists/{list-id}/items
```

## Request body

In the request body, supply a JSON representation of the [listItem][] resource to create.

## Example

Here is an example of how to create a new generic list item.

<!-- { "blockType": "request", "name": "create-listitem", "scopes": "sites.readwrite.all" } -->

```json
POST https://graph.microsoft.com/beta/sites/{site-id}/lists/{list-id}/items
Content-Type: application/json

{
  "fields": {
    "Title": "Widget",
    "Color": "Purple",
    "Weight": 32
  }
}
```

## Response

If successful, this method returns a [listItem][] in the response body for the created list item.

<!-- { "blockType": "response", "@odata.type": "microsoft.graph.listItem", "truncated": true } -->

```json
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "20",
  "createdDateTime": "2016-08-30T08:26:00Z",
  "createdBy": {
    "user": {
      "displayName": "Ryan Gregg",
      "id": "8606e4d5-d582-4f5f-aeba-7d7c18b20cfd"
    }
  },
  "lastModifiedDateTime": "2016-08-30T08:26:00Z",
  "lastModifiedBy": {
    "user": {
      "displayName": "Ryan Gregg",
      "id": "8606e4d5-d582-4f5f-aeba-7d7c18b20cfd"
    }
  }
}
```
#### SDK sample code
# [C#](#tab/cs)
[!INCLUDE [sample-code](../includes/create-listitem-Cs-snippets.md)]

# [Javascript](#tab/javascript)
[!INCLUDE [sample-code](../includes/create-listitem-Javascript-snippets.md)]

# [Objective-C](#tab/objective-c)
[!INCLUDE [sample-code](../includes/create-listitem-Objective-C-snippets.md)]
---

[!INCLUDE [sdk-documentation](../includes/snippets_sdk_documentation_link.md)]

**Note:** The response object is truncated for clarity. Default properties will be returned from the actual call.

[list]: ../resources/list.md
[listItem]: ../resources/listitem.md

<!--
{
  "type": "#page.annotation",
  "description": "Add a new item to a SharePoint list.",
  "keywords": "",
  "section": "documentation",
  "tocPath": "ListItem/Create",
  "suppressions": [
    "Error: /api-reference/beta/api/listitem-create.md:\r\n      BookmarkMissing: '[#tab/objective-c](Objective-C)'. Did you mean: #objective-c (score: 4)",
    "Error: /api-reference/beta/api/listitem-create.md:\r\n      BookmarkMissing: '[#tab/cs](C#)'. Did you mean: #c (score: 5)",
    "Error: /api-reference/beta/api/listitem-create.md:\r\n      BookmarkMissing: '[#tab/javascript](Javascript)'. Did you mean: #javascript (score: 4)"
  ]
}
-->
