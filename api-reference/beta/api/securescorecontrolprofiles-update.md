---
title: "Update secureScoreControlProfiles"
description: "Update an editable secureScoreControlProfiles property within any integrated solution to change various properties, such as assignedTo or tenantNote."
localization_priority: Normal
---

# Update secureScoreControlProfiles

 [!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update an editable **secureScoreControlProfiles** property within any integrated solution to change various properties, such as **assignedTo** or **tenantNote**.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) |   SecurityEvents.ReadWrite.All.  |
|Delegated (personal Microsoft account) |  Not supported.  |
|Application | SecurityEvents.ReadWrite.All. |

## HTTP request

<!-- { "blockType": "ignored" } -->

```http
PATCH /security/secureScoreControlProfiles/{id}
```

## Request headers

| Name       | Description|
|:-----------|:-----------|
| Authorization  | Bearer {code}. Required.|
|Prefer | return=representation. |

## Request body

In the request body, supply a JSON representation of the values for relevant fields that should be updated. The following table lists the fields that can be updated for a secureScoreControlProfile. The values for existing properties that are not included in the request body will not change. For best performance, don't include existing values that haven't changed.

| Property   | Type |Description|
|:---------------|:--------|:----------|
|assignedTo|String|Name of the analyst the control is assigned to for triage, implementation, or remediation.|
|tenantNote|String|Analyst comments on the control (for customer control management).|
|controlStateUpdates| String|Analyst driven setting on the control. Possible values are: `ignore`, `thirdParty`, `reviewed`.|


## Response

If successful, this method returns a `204 No Content` response code.

If the optional request header is used, the method returns a `200 OK` response code and the updated [secureScoreControlProfiles](../resources/securescorecontrolprofiles.md) object in the response body.

## Example

### Request

The following is an example of the request.
<!-- {
  "blockType": "request",
  "name": "securescorecontrolprofiles_update"
}-->

```http
PATCH https://graph.microsoft.com/beta/security/secureScoreControlProfiles/AdminMFA
Content-type: application/json

{
  "controlStateUpdates": "controlStateUpdates-value"
}
```

### Response

The following is an example of a successful response.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.secureScoreControlProfile"
} -->

```http
HTTP/1.1 204 No Content
```
#### SDK sample code
# [C#](#tab/cs)
[!INCLUDE [sample-code](../includes/securescorecontrolprofiles_update-Cs-snippets.md)]

# [Javascript](#tab/javascript)
[!INCLUDE [sample-code](../includes/securescorecontrolprofiles_update-Javascript-snippets.md)]

# [Objective-C](#tab/objective-c)
[!INCLUDE [sample-code](../includes/securescorecontrolprofiles_update-Objective-C-snippets.md)]
---

[!INCLUDE [sdk-documentation](../includes/snippets_sdk_documentation_link.md)]




<!--
{
  "type": "#page.annotation",
  "description": "Update secureScoreControlProfiles",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
    "Error: /api-reference/beta/api/securescorecontrolprofiles-update.md:\r\n      BookmarkMissing: '[#tab/objective-c](Objective-C)'. Did you mean: #objective-c (score: 4)",
    "Error: /api-reference/beta/api/securescorecontrolprofiles-update.md:\r\n      BookmarkMissing: '[#tab/cs](C#)'. Did you mean: #c (score: 5)",
    "Error: /api-reference/beta/api/securescorecontrolprofiles-update.md:\r\n      BookmarkMissing: '[#tab/javascript](Javascript)'. Did you mean: #javascript (score: 4)"
  ]
}
-->
