---
title: "Create invitation"
description: "Use this API to create a new invitation. Invitation adds an external user to the organization."
localization_priority: Priority
author: "davidmu1"
ms.prod: "microsoft-identity-platform"
---

# Create invitation

Use this API to create a new [invitation](../resources/invitation.md). Invitation adds an external user to the organization.

When creating a new invitation you have several options available:

1. On invitation creation, Microsoft Graph can automatically send an invitation email directly to the invited user, or your app can use the *inviteRedeemUrl* returned in the creation response to craft your own invitation (through your communication mechanism of choice) to the invited user. If you decide to have Microsoft Graph send an invitation email automatically, you can control the content and language of the email using [*invitedUserMessageInfo*](../resources/invitedusermessageinfo.md).
2. When the user is invited, a user entity (of userType Guest) is created and can now be used to control access to resources. The invited user has to go through the redemption process to access any resources he has been invited to.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).


|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | User.Invite.All, User.ReadWrite.All, Directory.ReadWrite.All    |
|Delegated (personal Microsoft account) | Not supported.    |
|Application | User.Invite.All, User.ReadWrite.All, Directory.ReadWrite.All |

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
POST /invitations
```
## Request headers
| Header       | Value |
|:---------------|:--------|
| Authorization  | Bearer {token}. Required.  |
| Content-Type  | application/json  |

## Request body
In the request body, supply a JSON representation of an [invitation](../resources/invitation.md) object.

The following table shows the properties that are required when you create a invitation.

| Parameter | Type | Description|
|:---------------|:--------|:----------|
|invitedUserEmailAddress |string | The email address of the user you are inviting.|
|inviteRedirectUrl |string |The URL that the user will be redirected to after redemption.|

## Response

If successful, this method returns `201 Created` response code and [invitation](../resources/invitation.md) object in the response body.

## Example
##### Request
Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "create_invitation_post"
}-->
```http
POST https://graph.microsoft.com/v1.0/invitations
Content-type: application/json
Content-length: 551

{
  "invitedUserEmailAddress": "yyy@test.com",
  "inviteRedirectUrl": "https://myapp.com"
}
```

##### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.invitation"
} -->
```http
HTTP/1.1 201 OK
Content-type: application/json
Content-length: 551

{
  "id": "7b92124c-9fa9-406f-8b8e-225df8376ba9",
  "inviteRedeemUrl": "https://invitations.microsoft.com/redeem/?tenant=04dcc6ab-388a-4559-b527-fbec656300ea&user=7b92124c-9fa9-406f-8b8e-225df8376ba9&ticket=VV9dmiExBsfRIVNFjb9ITj9VXAd07Ypv4gTg%2f8PiuJs%3d&lc=1033&ver=2.0",
  "invitedUserDisplayName": "yyy",
  "invitedUserEmailAddress": "yyy@test.com",
  "sendInvitationMessage": false,
  "invitedUserMessageInfo": {
     "messageLanguage": null,
     "ccRecipients": [
          {
             "emailAddress": {
                 "name": null,
                 "address": null
              }
          }
     ],
     "customizedMessageBody": null
  },
  "inviteRedirectUrl": "https://myapp.com/",
  "status": "Completed",
  "invitedUser": { "id": "243b1de4-ad9f-421c-a933-d55305fb165d" }
}
```
#### SDK sample code
# [C#](#tab/cs)
[!INCLUDE [sample-code](../includes/create_invitation_post-Cs-snippets.md)]

# [Javascript](#tab/javascript)
[!INCLUDE [sample-code](../includes/create_invitation_post-Javascript-snippets.md)]

# [Objective-C](#tab/objective-c)
[!INCLUDE [sample-code](../includes/create_invitation_post-Objective-C-snippets.md)]
---

[!INCLUDE [sdk-documentation](../includes/snippets_sdk_documentation_link.md)]

<!-- {
  "type": "#page.annotation",
  "suppressions": [
    "Error: /api-reference/v1.0/api/invitation-post.md:\r\n      BookmarkMissing: '[#tab/objective-c](Objective-C)'. Did you mean: #objective-c (score: 4)",
    "Error: /api-reference/v1.0/api/invitation-post.md:\r\n      BookmarkMissing: '[#tab/cs](C#)'. Did you mean: #c (score: 5)",
    "Error: /api-reference/v1.0/api/invitation-post.md:\r\n      BookmarkMissing: '[#tab/javascript](Javascript)'. Did you mean: #javascript (score: 4)",
    "Error: create_user_from_users/invitedUser:
      Property 'invitedUser' is of type Custom but has no custom members."
  ]
}-->
