---
title: "Create rejectedSender"
description: "Add a new user or group to the rejectedSender list."
author: "dkershaw10"
localization_priority: Normal
ms.prod: "groups"
---

# Create rejectedSender

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Add a new user or group to the rejectedSender list.

Specify the user or group in `@odata.id` in the request body. Users in the rejected senders list cannot post to conversations of the group (identified in the POST request URL). Make sure you do not specify the same user or group in the rejected senders and accepted senders lists, otherwise you will get an error.

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
POST /groups/{id}/rejectedSenders/$ref
```

## Request headers
| Header       | Value |
|:---------------|:--------|
| Authorization  | Bearer {token}. Required.  |

## Request body
In the request body, supply the id of a user or group object.

## Response
This method returns `204 No Content` response code and no response body.

## Example
#### Request
The following is an example of the request.
<!-- {
  "blockType": "request",
  "name": "create_rejectedsender"
}-->
```http
POST https://graph.microsoft.com/beta/groups/{id}/rejectedSenders/$ref
Content-type: application/json
Content-length: 30

{
  "@odata.id":"https://graph.microsoft.com/beta/users/alexd@contoso.com"
}
```

#### Response
The following is an example of the response.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 204 No Content
```
#### SDK sample code

# [Javascript](#tab/javascript)
[!INCLUDE [sample-code](../includes/create_rejectedsender-Javascript-snippets.md)]

# [Objective-C](#tab/objective-c)
[!INCLUDE [sample-code](../includes/create_rejectedsender-Objective-C-snippets.md)]
---

[!INCLUDE [sdk-documentation](../includes/snippets_sdk_documentation_link.md)]

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!--
{
  "type": "#page.annotation",
  "description": "Create rejectedSender",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
    "Error: /api-reference/beta/api/group-post-rejectedsenders.md:\r\n      BookmarkMissing: '[#tab/objective-c](Objective-C)'. Did you mean: #objective-c (score: 4)",
    "Error: /api-reference/beta/api/group-post-rejectedsenders.md:\r\n      BookmarkMissing: '[#tab/javascript](Javascript)'. Did you mean: #javascript (score: 4)"
  ]
}
-->
