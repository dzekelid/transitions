---
swagger: "2.0"
x-collection-name: Xibo
x-complete: 0
info:
  title: Xibo API Adds In/Out transition
  description: Adds In/Out transition to a specified widget
  termsOfService: http://xibo.org.uk/legal
  version: 1.0.0
basePath: /api
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /playlist/widget/transition/{type}/{widgetId}:
    put:
      summary: Adds In/Out transition
      description: Adds In/Out transition to a specified widget
      operationId: WidgetEditTransition
      x-api-path-slug: playlistwidgettransitiontypewidgetid-put
      parameters:
      - in: formData
        name: transitionDirection
        description: The direction for this transition, only appropriate for transitions
          that move, such as fly
      - in: formData
        name: transitionDuration
        description: Duration of this transition in milliseconds
      - in: formData
        name: transitionType
        description: 'Type of a transition, available Options: fly, fadeIn, fadeOut'
      - in: path
        name: type
        description: 'Transition type, available options: in, out'
      - in: path
        name: widgetId
        description: The widget ID to add the transition to
      responses:
        200:
          description: OK
      tags:
      - S
      - In
      - Out
      - Transition
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