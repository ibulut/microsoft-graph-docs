---
title: "message: replyAll"
description: "Reply to all recipients of a message by specifying a comment and modifying any updateable properties "
author: "angelgolfer-ms"
localization_priority: Normal
ms.prod: "outlook"
---

# message: replyAll

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Reply to all recipients of a message by specifying a comment and modifying any updateable properties 
for the reply, all by using the **replyAll** method. The message is then saved in the Sent Items folder.

Alternatively, you can first [create a draft reply-all message](../api/message-createreplyall.md) to include a comment or 
update any message properties, and then [send](../api/message-send.md) the reply.

**Note**

- You can specify either a comment or the **body** property of the `message` parameter. Specifying both will return an HTTP 400 Bad Request error.
- If the **replyTo** property is specified in the original message, per Internet Message Format 
([RFC 2822](https://www.rfc-editor.org/info/rfc2822)), you should send the reply to the recipients in the  
**replyTo** and **toRecipients** properties, and not the recipients in the **from** and **toRecipients** properties. 


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
POST /users/me/messages/{id}/replyAll
POST /users/{id | userPrincipalName}/messages/{id}/replyAll
POST /me/mailFolders/{id}/messages/{id}/replyAll
POST /users/{id | userPrincipalName}/mailFolders/{id}/messages/{id}/replyAll
```
## Request headers
| Name       | Type | Description|
|:---------------|:--------|:----------|
| Authorization  | string  | Bearer {token}. Required. |
| Content-Type | string  | Nature of the data in the body of an entity. Required. |

## Request body
In the request body, provide a JSON object with the following parameters.

| Parameter	   | Type	|Description|
|:---------------|:--------|:----------|
|comment|String|A comment to include. Can be an empty string.|
|message|[message](../resources/message.md)|Any writeable properties to update in the reply message.|

## Response

If successful, this method returns `202 Accepted` response code. It does not return anything in the response body.

## Example
The following example includes a comment and adds an attachment to the reply-all message.
##### Request
Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "message_replyall"
}-->
```http
POST https://graph.microsoft.com/beta/me/messages/AAMkADA1MTAAAH5JaKAAA=/replyAll
Content-Type: application/json

{
    "message":{
      "attachments": [ 
        { 
          "@odata.type": "#microsoft.graph.fileAttachment", 
          "name": "guidelines.txt", 
          "contentBytes": "bWFjIGFuZCBjaGVlc2UgdG9kYXk=" 
        } 
      ]
    },
    "comment": "Please take a look at the attached guidelines before you decide on the name." 
}
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
[!INCLUDE [sample-code](../includes/message_replyall-Cs-snippets.md)]

# [Javascript](#tab/javascript)
[!INCLUDE [sample-code](../includes/message_replyall-Javascript-snippets.md)]

# [Objective-C](#tab/objective-c)
[!INCLUDE [sample-code](../includes/message_replyall-Objective-C-snippets.md)]
---

[!INCLUDE [sdk-documentation](../includes/snippets_sdk_documentation_link.md)]

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!--
{
  "type": "#page.annotation",
  "description": "message: replyAll",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
    "Error: /api-reference/beta/api/message-replyall.md:\r\n      BookmarkMissing: '[#tab/objective-c](Objective-C)'. Did you mean: #objective-c (score: 4)",
    "Error: /api-reference/beta/api/message-replyall.md:\r\n      BookmarkMissing: '[#tab/cs](C#)'. Did you mean: #c (score: 5)",
    "Error: /api-reference/beta/api/message-replyall.md:\r\n      BookmarkMissing: '[#tab/javascript](Javascript)'. Did you mean: #javascript (score: 4)"
  ]
}
-->
