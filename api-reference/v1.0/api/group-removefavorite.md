---
title: "group: removeFavorite"
description: "Remove the group from the list of the current user's favorite groups. Supported for Office 365 Groups only."
localization_priority: Normal
author: "dkershaw10"
ms.prod: "groups"
---

# group: removeFavorite
Remove the group from the list of the current user's favorite groups. Supported for Office 365 Groups only.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | Group.ReadWrite.All    |
|Delegated (personal Microsoft account) | Not supported.    |
|Application | Not supported. |

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
POST /groups/{id}/removeFavorite
```
## Request headers
| Header       | Value |
|:---------------|:--------|
| Authorization  | Bearer {token}. Required.  |
| Prefer | return=minimal. If minimal response header is included in the request header, then a successful response returns `204 No Content` code. Optional.  | 

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns `200 OK` response code. It does not return anything in the response body.

## Example
#### Request
The following is an example of the request.
<!-- {
  "blockType": "request",
  "name": "group_removefavorite"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups/{id}/removeFavorite
```

#### Response
The following is an example of the response.
<!-- {
  "blockType": "response"
} -->
```http
HTTP/1.1 200 OK
```
#### SDK sample code
# [C#](#tab/cs)
[!INCLUDE [sample-code](../includes/group_removefavorite-Cs-snippets.md)]

# [Javascript](#tab/javascript)
[!INCLUDE [sample-code](../includes/group_removefavorite-Javascript-snippets.md)]

# [Objective-C](#tab/objective-c)
[!INCLUDE [sample-code](../includes/group_removefavorite-Objective-C-snippets.md)]
---

[!INCLUDE [sdk-documentation](../includes/snippets_sdk_documentation_link.md)]

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "group: removeFavorite",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
    "Error: /api-reference/v1.0/api/group-removefavorite.md:\r\n      BookmarkMissing: '[#tab/objective-c](Objective-C)'. Did you mean: #objective-c (score: 4)",
    "Error: /api-reference/v1.0/api/group-removefavorite.md:\r\n      BookmarkMissing: '[#tab/cs](C#)'. Did you mean: #c (score: 5)",
    "Error: /api-reference/v1.0/api/group-removefavorite.md:\r\n      BookmarkMissing: '[#tab/javascript](Javascript)'. Did you mean: #javascript (score: 4)"
  ]
}-->
