---
title: "educationSubmission: submit"
description: "An action that indicates that a student is done with the work and is ready to hand in the assignment. This action can only be taken by the student."
author: "dipakboyed"
localization_priority: Normal
ms.prod: "education"
---

# educationSubmission: submit

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

An action that indicates that a student is done with the work and is ready to hand in the assignment. This action can only be taken by the student. This will change the status of the submission from "working" to "submitted". During the submit process, all the resources will be copied to the submittedResources bucket. The teacher will be looking at the submitted resources list for grading.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) |  EduAssignments.ReadWriteBasic, EduAssignments.ReadWrite  |
|Delegated (personal Microsoft account) |  Not supported.  |
|Application | Not supported. | 

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
POST /education/classes/{id}/assignments/{id}/submissions/{id}/submit

```
## Request headers
| Header       | Value |
|:---------------|:--------|
| Authorization  | Bearer {token}. Required.  |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns `204 No Content` response code. It does not return anything in the response body.

## Example
The following example shows how to call this API.
##### Request
The following is an example of the request.
<!-- {
  "blockType": "request",
  "name": "educationsubmission_submit"
}-->
```http
POST https://graph.microsoft.com/beta/education/classes/11021/assignments/19002/submissions/850f51b7/submit
```

##### Response
The following is an example of the response.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.educationAssignment"
} -->
```http
HTTP/1.1 204 No Content
```
#### SDK sample code
# [C#](#tab/cs)
[!INCLUDE [sample-code](../includes/educationsubmission_submit-Cs-snippets.md)]

# [Javascript](#tab/javascript)
[!INCLUDE [sample-code](../includes/educationsubmission_submit-Javascript-snippets.md)]

# [Objective-C](#tab/objective-c)
[!INCLUDE [sample-code](../includes/educationsubmission_submit-Objective-C-snippets.md)]
---

[!INCLUDE [sdk-documentation](../includes/snippets_sdk_documentation_link.md)]

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!--
{
  "type": "#page.annotation",
  "description": "educationSubmission: submit",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
    "Error: /api-reference/beta/api/educationsubmission-submit.md:\r\n      BookmarkMissing: '[#tab/objective-c](Objective-C)'. Did you mean: #objective-c (score: 4)",
    "Error: /api-reference/beta/api/educationsubmission-submit.md:\r\n      BookmarkMissing: '[#tab/cs](C#)'. Did you mean: #c (score: 5)",
    "Error: /api-reference/beta/api/educationsubmission-submit.md:\r\n      BookmarkMissing: '[#tab/javascript](Javascript)'. Did you mean: #javascript (score: 4)"
  ]
}
-->
