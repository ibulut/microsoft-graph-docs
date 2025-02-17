---
title: "List businessFlowTemplates"
description: "In the Azure AD access reviews feature, list all the businessFlowTemplate objects."
localization_priority: Normal
---

# List businessFlowTemplates

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

In the Azure AD [access reviews](../resources/accessreviews-root.md) feature, list all the [businessFlowTemplate](../resources/businessflowtemplate.md) objects.
## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type                        | Permissions (from least to most privileged)              |
|:--------------------------------------|:---------------------------------------------------------|
|Delegated (work or school account)     | AccessReview.Read.All, AccessReview.ReadWrite.All  |
|Delegated (personal Microsoft account) | Not supported. |
|Application                            | AccessReview.Read.All |

The signed in user must also be in a directory role that permits them to read an access review.

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
GET /businessFlowTemplates
```
## Request headers
| Name         | Type        | Description |
|:-------------|:------------|:------------|
| Authorization | string | Bearer \{token\}. Required. |

## Request body
No request body should be supplied.

## Response
If successful, this method returns a `200, OK` response code and an array of [businessFlowTemplate](../resources/businessflowtemplate.md) objects in the response body.

## Example
##### Request

<!-- {
  "blockType": "request",
  "name": "get_businessFlowTemplate"
}-->
```http
GET https://graph.microsoft.com/beta/businessFlowTemplates
```

##### Response
>**Note:** The response object shown here might be shortened for readability. All the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.businessFlowTemplate",
    "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "value":[
        {
            "id": "842169fe-e1b7-4ce9-98b6-6a9db02eec6b",
            "displayName": "Access Reviews for External Users' access to groups"
        },
        {
            "id": "7fbc909b-efe1-4c72-8ae6-99cb30b882de",
            "displayName": "Access Reviews for External Users' access to applications"
        },
        {
            "id": "50839a84-e23c-44a7-a8cc-16e162afc656",
            "displayName": "Access Reviews for All Users' assignment to applications"
        },
        {
            "id": "6e4f3d20-c5c3-407f-9695-8460952bcc68",
            "displayName": "Access Reviews for Office 365 Groups' membership"
        } 
    ]
}

```
#### SDK sample code

# [C#](#tab/cs)
[!INCLUDE [sample-code](../includes/get_businessFlowTemplate-Cs-snippets.md)]

# [Javascript](#tab/javascript)
[!INCLUDE [sample-code](../includes/get_businessFlowTemplate-Javascript-snippets.md)]
# [Objective-C](#tab/objective-c)
[!INCLUDE [sample-code](../includes/get_businessFlowTemplate-Objective-C-snippets.md)]
---

[!INCLUDE [sdk-documentation](../includes/snippets_sdk_documentation_link.md)]

## See also

| Method		   | Return Type	|Description|
|:---------------|:--------|:----------|
|[Create accessReview](accessreview-create.md) |	[accessReview](../resources/accessreview.md) |	Create a new accessReview. |




<!--
{
  "type": "#page.annotation",
  "description": "List business flow template",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
    "Error: /api-reference/beta/api/businessflowtemplate-list.md:\r\n      BookmarkMissing: '[#tab/objective-c](Objective-C)'. Did you mean: #objective-c (score: 4)",
    "Error: /api-reference/beta/api/businessflowtemplate-list.md:\r\n      BookmarkMissing: '[#tab/javascript](Javascript)'. Did you mean: #javascript (score: 4)",
    "Error: /api-reference/beta/api/businessflowtemplate-list.md:\r\n      BookmarkMissing: '[#tab/cs](C#)'. Did you mean: #c (score: 5)"
  ]
}
-->
