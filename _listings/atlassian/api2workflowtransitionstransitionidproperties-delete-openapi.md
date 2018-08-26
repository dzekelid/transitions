---
swagger: "2.0"
x-collection-name: Atlassian
x-complete: 0
info:
  title: Jira Cloud API Delete workflow transition property
  description: |-
    Deletes a property from a workflow transition. Transition properties are used to change the behavior of a transition. For more information, see [Transition properties](https://confluence.atlassian.com/x/zIhKLg#Advancedworkflowconfiguration-transitionproperties) and [Workflow properties](https://confluence.atlassian.com/x/JYlKLg).

    **[Permissions](https://confluence.atlassian.com/x/FQiiLQ) required:** _Administer Jira_ global permission.
  termsOfService: http://atlassian.com/terms/
  version: 1.0.0
basePath: /
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /api/2/issue/{issueIdOrKey}/transitions:
    get:
      summary: Get transitions
      description: |-
        Returns a list of transitions available for this issue for the current user.

        Specify `expand=transitions.fields` parameter to retrieve the fields required for a transition together with their types.

        Fields metadata corresponds to the fields available in a transition screen for a particular transition. Fields hidden from the screen will not be returned in the metadata.
      operationId: com.atlassian.jira.rest.v2.issue.IssueResource.getTransitions_get
      x-api-path-slug: api2issueissueidorkeytransitions-get
      parameters:
      - in: path
        name: issueIdOrKey
        description: ID or key of the issue to return transitions for
      - in: query
        name: skipRemoteOnlyCondition
        description: Flag to skip evaluation of {@link RemoteOnlyCondition}
      - in: query
        name: transitionId
      responses:
        200:
          description: OK
      tags:
      - Transitions
    post:
      summary: Do transition
      description: |-
        Performs the issue transition. While performing the transition you can modify other issue fields.

        The fields that can be set on transition, in either `fields` or `update` parameter can be determined using the **/rest/api/2/issue/{issueIdOrKey}/transitions?expand=transitions.fields** resource. If a field is not configured to appear on the transition screen, it will not be returned in the transition metadata. A field validation error will occur if such field is submitted in issue transition request.
      operationId: com.atlassian.jira.rest.v2.issue.IssueResource.doTransition_post
      x-api-path-slug: api2issueissueidorkeytransitions-post
      parameters:
      - in: path
        name: issueIdOrKey
        description: ID or key of the issue to transition
      responses:
        200:
          description: OK
      tags:
      - Do
      - Transition
  /api/2/workflow/transitions/{transitionId}/properties:
    get:
      summary: Get workflow transition properties
      description: |-
        Returns the properties on a workflow transition. Transition properties are used to change the behavior of a transition. For more information, see [Transition properties](https://confluence.atlassian.com/x/zIhKLg#Advancedworkflowconfiguration-transitionproperties) and [Workflow properties](https://confluence.atlassian.com/x/JYlKLg).

        **[Permissions](https://confluence.atlassian.com/x/FQiiLQ) required:** _Administer Jira_ global permission.
      operationId: com.atlassian.jira.rest.v2.admin.WorkflowTransitionResource.getWorkflowTransitionProperties_get
      x-api-path-slug: api2workflowtransitionstransitionidproperties-get
      parameters:
      - in: query
        name: includeReservedKeys
        description: Some properties with keys that have the _jira
      - in: query
        name: key
        description: The key of the property being returned, also known as the name
          of the property
      - in: path
        name: transitionId
        description: The ID of the transition
      - in: query
        name: workflowMode
        description: The workflow status
      - in: query
        name: workflowName
        description: The name of the workflow that the transition belongs to
      responses:
        200:
          description: OK
      tags:
      - Workflow
      - Transition
      - Properties
    post:
      summary: Create workflow transition property
      description: |-
        Adds a property to a workflow transition. Transition properties are used to change the behavior of a transition. For more information, see [Transition properties](https://confluence.atlassian.com/x/zIhKLg#Advancedworkflowconfiguration-transitionproperties) and [Workflow properties](https://confluence.atlassian.com/x/JYlKLg).

        **[Permissions](https://confluence.atlassian.com/x/FQiiLQ) required:** _Administer Jira_ global permission.
      operationId: com.atlassian.jira.rest.v2.admin.WorkflowTransitionResource.createWorkflowTransitionProperty_post
      x-api-path-slug: api2workflowtransitionstransitionidproperties-post
      parameters:
      - in: query
        name: key
        description: The key of the property being added, also known as the name of
          the property
      - in: path
        name: transitionId
        description: The ID of the transition
      - in: query
        name: workflowMode
        description: The workflow status
      - in: query
        name: workflowName
        description: The name of the workflow that the transition belongs to
      responses:
        200:
          description: OK
      tags:
      - Workflow
      - Transition
      - Property
    put:
      summary: Update workflow transition property
      description: |-
        Updates a workflow transition by changing the property value. Trying to update a property that does not exist results in a new property being added to the transition. Transition properties are used to change the behavior of a transition. For more information, see [Transition properties](https://confluence.atlassian.com/x/zIhKLg#Advancedworkflowconfiguration-transitionproperties) and [Workflow properties](https://confluence.atlassian.com/x/JYlKLg).

        **[Permissions](https://confluence.atlassian.com/x/FQiiLQ) required:** _Administer Jira_ global permission.
      operationId: com.atlassian.jira.rest.v2.admin.WorkflowTransitionResource.updateWorkflowTransitionProperty_put
      x-api-path-slug: api2workflowtransitionstransitionidproperties-put
      parameters:
      - in: query
        name: key
        description: The key of the property being updated, also known as the name
          of the property
      - in: path
        name: transitionId
        description: The ID of the transition
      - in: query
        name: workflowMode
        description: The workflow status
      - in: query
        name: workflowName
        description: The name of the workflow that the transition belongs to
      responses:
        200:
          description: OK
      tags:
      - Workflow
      - Transition
      - Property
    delete:
      summary: Delete workflow transition property
      description: |-
        Deletes a property from a workflow transition. Transition properties are used to change the behavior of a transition. For more information, see [Transition properties](https://confluence.atlassian.com/x/zIhKLg#Advancedworkflowconfiguration-transitionproperties) and [Workflow properties](https://confluence.atlassian.com/x/JYlKLg).

        **[Permissions](https://confluence.atlassian.com/x/FQiiLQ) required:** _Administer Jira_ global permission.
      operationId: com.atlassian.jira.rest.v2.admin.WorkflowTransitionResource.deleteWorkflowTransitionProperty_delete
      x-api-path-slug: api2workflowtransitionstransitionidproperties-delete
      parameters:
      - in: query
        name: key
        description: The name of the transition property to delete, also known as
          the name of the property
      - in: path
        name: transitionId
        description: The ID of the transition
      - in: query
        name: workflowMode
        description: The workflow status
      - in: query
        name: workflowName
        description: The name of the workflow that the transition belongs to
      responses:
        200:
          description: OK
      tags:
      - Workflow
      - Transition
      - Property
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---