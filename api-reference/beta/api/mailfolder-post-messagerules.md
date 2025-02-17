---
title: "Create rule"
description: "Create a messageRule object by specifying a set of conditions and actions. "
author: "angelgolfer-ms"
localization_priority: Normal
ms.prod: "outlook"
---

# Create rule

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Create a [messageRule](../resources/messagerule.md) object by specifying a set of conditions and actions. 

Outlook carries out those actions if an incoming message in the user's Inbox meets the specified conditions.

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
POST /me/mailFolders/inbox/messagerules
POST /users/{id | userPrincipalName}/mailFolders/inbox/messagerules
```
## Request headers
| Name       | Description|
|:---------------|:----------|
| Authorization  | Bearer {token}. Required. |


## Request body
In the request body, supply the parameters that are applicable to your rule. The following are body parameters that are typically used 
when creating rules. You can specify any other writable **messageRule** properties as appropriate in the request body.

| Parameter       | Type|Description|
|:--------|:-------|:----------|
|actions|[messageRuleActions](../resources/messageruleactions.md)|Actions to be taken on a message when the corresponding conditions, if any, are fulfilled. Required.|
|conditions|[messageRulePredicates](../resources/messagerulepredicates.md)|Conditions that when fulfilled, will trigger the corresponding actions for that rule. Optional.|
|displayName| String  | The display name of the rule. Required.|
|exceptions| [messageRulePredicates](../resources/messagerulepredicates.md)| Represents exception conditions for the rule. Optional. |
|isEnabled | Boolean | Indicates whether the rule is enabled to be applied to messages. Optional. |
|sequence| Int32 | Indicates the order in which the rule is executed, among other rules. Required.|

## Response
If successful, this method returns `201 Created` response code and a **messageRule** object in the response body.

## Example
##### Request
Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "create_messagerule_from_mailfolder"
}-->
```http
POST https://graph.microsoft.com/beta/me/mailFolders/inbox/messagerules
Content-type: application/json

{      
    "displayName": "From partner",      
    "sequence": 2,      
    "isEnabled": true,          
    "conditions": {
        "senderContains": [
          "adele"       
        ]
     },
     "actions": {
        "forwardTo": [
          {
             "emailAddress": {
                "name": "Alex Wilbur",
                "address": "AlexW@contoso.onmicrosoft.com"
              }
           }
        ],
        "stopProcessingRules": true
     }    
}

```
##### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.messageRule"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id":"AQAAAJ5dZqA=",
  "displayName":"From partner",
  "sequence":2,
  "isEnabled":true,
  "hasError":false,
  "isReadOnly":false,
  "conditions":{
    "senderContains":[
      "ADELE"
    ]
  },
  "actions":{
      "stopProcessingRules":true,
      "forwardTo":[
        {
          "emailAddress":{
            "name":"Alex Wilbur",
            "address":"AlexW@contoso.onmicrosoft.com"
          }
        }
      ]
  }
}

```
#### SDK sample code
# [C#](#tab/cs)
[!INCLUDE [sample-code](../includes/create_messagerule_from_mailfolder-Cs-snippets.md)]

# [Javascript](#tab/javascript)
[!INCLUDE [sample-code](../includes/create_messagerule_from_mailfolder-Javascript-snippets.md)]

# [Objective-C](#tab/objective-c)
[!INCLUDE [sample-code](../includes/create_messagerule_from_mailfolder-Objective-C-snippets.md)]
---

[!INCLUDE [sdk-documentation](../includes/snippets_sdk_documentation_link.md)]

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!--
{
  "type": "#page.annotation",
  "description": "Create rule",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
    "Error: /api-reference/beta/api/mailfolder-post-messagerules.md:\r\n      BookmarkMissing: '[#tab/objective-c](Objective-C)'. Did you mean: #objective-c (score: 4)",
    "Error: /api-reference/beta/api/mailfolder-post-messagerules.md:\r\n      BookmarkMissing: '[#tab/cs](C#)'. Did you mean: #c (score: 5)",
    "Error: /api-reference/beta/api/mailfolder-post-messagerules.md:\r\n      BookmarkMissing: '[#tab/javascript](Javascript)'. Did you mean: #javascript (score: 4)"
  ]
}
-->
