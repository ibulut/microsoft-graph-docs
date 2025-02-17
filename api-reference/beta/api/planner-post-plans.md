---
title: "Create plannerPlan"
description: "Use this API to create a new **plannerPlan**."
localization_priority: Normal
author: "TarkanSevilmis"
ms.prod: "planner"
---

# Create plannerPlan

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Use this API to create a new **plannerPlan**.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

| Permission type                        | Permissions (from least to most privileged) |
| :------------------------------------- | :------------------------------------------ |
| Delegated (work or school account)     | Group.ReadWrite.All                         |
| Delegated (personal Microsoft account) | Not supported.                              |
| Application                            | Not supported.                              |

## HTTP request

<!-- { "blockType": "ignored" } -->
``` http
POST /planner/plans
```

## Request headers

| Name          | Description               |
| :------------ | :------------------------ |
| Authorization | Bearer {token}. Required. |

## Request body

In the request body, supply a JSON representation of [plannerPlan](../resources/plannerplan.md) object.
The **plannerPlan** owner property must be set to an id of a [group](../resources/group.md) object.

>**Note:** The user who is creating the plan must be a member of the group that will own the plan. When you create a new group by using [Create group](../api/group-post-groups.md), you are not added to the group as a member. After the group is created, add yourself as a member by using [group post members](../api/group-post-members.md).

## Response

If successful, this method returns `201 Created` response code and [plannerPlan](../resources/plannerplan.md) object in the response body.

This method can return any of the [HTTP status codes](/graph/errors). The most common errors that apps should handle for this method are the 400, 403 and 404 responses. For more information about these errors, see [Common Planner error conditions](../resources/planner-overview.md#common-planner-error-conditions).

## Example

### Request

Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "create_plannerplan_from_planner"
}-->
``` http
POST https://graph.microsoft.com/beta/planner/plans
Content-type: application/json
Content-length: 381

{
  "owner": "ebf3b108-5234-4e22-b93d-656d7dae5874",
  "title": "title-value"
}
```

In the request body, supply a JSON representation of [plannerPlan](../resources/plannerplan.md) object.

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.plannerPlan"
} -->
``` http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 357

{
  "createdBy": {
    "application": {
      "id": "95e27074-6c4a-447a-aa24-9d718a0b86fa"
    },
    "user": {
      "id": "ebf3b108-5234-4e22-b93d-656d7dae5874"
    }
  },
  "createdDateTime": "2015-03-30T18:36:49.2407981Z",
  "owner": "ebf3b108-5234-4e22-b93d-656d7dae5874",
  "title": "title-value",
  "id": "xqQg5FS2LkCp935s-FIFm2QAFkHM"
}
```
#### SDK sample code
# [C#](#tab/cs)
[!INCLUDE [sample-code](../includes/create_plannerplan_from_planner-Cs-snippets.md)]

# [Javascript](#tab/javascript)
[!INCLUDE [sample-code](../includes/create_plannerplan_from_planner-Javascript-snippets.md)]

# [Objective-C](#tab/objective-c)
[!INCLUDE [sample-code](../includes/create_plannerplan_from_planner-Objective-C-snippets.md)]
---

[!INCLUDE [sdk-documentation](../includes/snippets_sdk_documentation_link.md)]

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!--
{
  "type": "#page.annotation",
  "description": "Create plannerPlan",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
    "Error: /api-reference/beta/api/planner-post-plans.md:\r\n      BookmarkMissing: '[#tab/objective-c](Objective-C)'. Did you mean: #objective-c (score: 4)",
    "Error: /api-reference/beta/api/planner-post-plans.md:\r\n      BookmarkMissing: '[#tab/cs](C#)'. Did you mean: #c (score: 5)",
    "Error: /api-reference/beta/api/planner-post-plans.md:\r\n      BookmarkMissing: '[#tab/javascript](Javascript)'. Did you mean: #javascript (score: 4)"
  ]
}
-->
