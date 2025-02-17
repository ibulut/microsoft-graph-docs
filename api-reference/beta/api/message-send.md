---
title: "message: send"
description: "Send a message in the draft folder. The draft message can be a new message draft, reply draft, reply-all draft, or"
localization_priority: Normal
author: "angelgolfer-ms"
ms.prod: "outlook"
---

# message: send

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Send a message in the draft folder. The draft message can be a new message draft, reply draft, reply-all draft, or
a forward draft. The message is then saved in the Sent Items folder.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | Mail.Send    |
|Delegated (personal Microsoft account) | Mail.Send    |
|Application | Mail.Send |

## HTTP request

<!-- { "blockType": "ignored" } -->

```http
POST /me/messages/{id}/send
POST /users/{id | userPrincipalName}/messages/{id}/send
```

## Request headers

| Name       | Type | Description|
|:---------------|:--------|:----------|
| Authorization  | string  | Bearer {token}. Required. |
| Content-Length | number | 0. Required. |

## Request body

## Response

If successful, this method returns `202 Accepted` response code. It does not return anything in the response body.

## Example

Here is an example of how to call this API.
##### Request

Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "message_send"
}-->

```http
POST https://graph.microsoft.com/beta/me/messages/{id}/send
```

##### Response

Here is an example of the response.
<!-- {
  "blockType": "response",
  "truncated": true
} -->

```http
HTTP/1.1 202 Accepted
```
#### SDK sample code
# [C#](#tab/cs)
[!INCLUDE [sample-code](../includes/message_send-Cs-snippets.md)]

# [Javascript](#tab/javascript)
[!INCLUDE [sample-code](../includes/message_send-Javascript-snippets.md)]

# [Objective-C](#tab/objective-c)
[!INCLUDE [sample-code](../includes/message_send-Objective-C-snippets.md)]
---

[!INCLUDE [sdk-documentation](../includes/snippets_sdk_documentation_link.md)]

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!--
{
  "type": "#page.annotation",
  "description": "message: send",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
    "Error: /api-reference/beta/api/message-send.md:\r\n      BookmarkMissing: '[#tab/objective-c](Objective-C)'. Did you mean: #objective-c (score: 4)",
    "Error: /api-reference/beta/api/message-send.md:\r\n      BookmarkMissing: '[#tab/cs](C#)'. Did you mean: #c (score: 5)",
    "Error: /api-reference/beta/api/message-send.md:\r\n      BookmarkMissing: '[#tab/javascript](Javascript)'. Did you mean: #javascript (score: 4)"
  ]
}
-->
