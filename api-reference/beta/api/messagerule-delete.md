---
title: "Delete messageRule"
description: "Delete the specified messageRule object."
author: "angelgolfer-ms"
localization_priority: Normal
ms.prod: "outlook"
---

# Delete messageRule

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Delete the specified [messageRule](../resources/messagerule.md) object.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | MailboxSettings.ReadWrite    |
|Delegated (personal Microsoft account) | MailboxSettings.ReadWrite    |
|Application | MailboxSettings.ReadWrite |

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
DELETE /me/mailFolders/inbox/messagerules/{id}
DELETE /users/{id | userPrincipalName}/mailFolders/inbox/messagerules/{id}
```
## Request headers
| Name       | Description|
|:---------------|:----------|
| Authorization  | Bearer {token}. Required. |


## Request body
Do not supply a request body for this method.


## Response
If successful, this method returns `204 No Content` response code. It does not return anything in the response body.

## Example
##### Request
Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "delete_messagerule"
}-->
```http
DELETE https://graph.microsoft.com/beta/me/mailfolders/inbox/messagerules('AQAAAJ5dZp8=')

```
##### Response
Here is an example of the response. 
<!-- {
  "blockType": "response",
  "isEmpty": true
} -->
```http
HTTP/1.1 204 No Content
```
#### SDK sample code
# [C#](#tab/cs)
[!INCLUDE [sample-code](../includes/delete_messagerule-Cs-snippets.md)]

# [Javascript](#tab/javascript)
[!INCLUDE [sample-code](../includes/delete_messagerule-Javascript-snippets.md)]

# [Objective-C](#tab/objective-c)
[!INCLUDE [sample-code](../includes/delete_messagerule-Objective-C-snippets.md)]
---

[!INCLUDE [sdk-documentation](../includes/snippets_sdk_documentation_link.md)]

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!--
{
  "type": "#page.annotation",
  "description": "Delete rule",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
    "Error: /api-reference/beta/api/messagerule-delete.md:\r\n      BookmarkMissing: '[#tab/objective-c](Objective-C)'. Did you mean: #objective-c (score: 4)",
    "Error: /api-reference/beta/api/messagerule-delete.md:\r\n      BookmarkMissing: '[#tab/cs](C#)'. Did you mean: #c (score: 5)",
    "Error: /api-reference/beta/api/messagerule-delete.md:\r\n      BookmarkMissing: '[#tab/javascript](Javascript)'. Did you mean: #javascript (score: 4)"
  ]
}
-->
