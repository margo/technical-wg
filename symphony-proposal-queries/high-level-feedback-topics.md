My suggestion, we split up learning sessions that focus on the tools that we see advantageous to adopt via Symphony. Below is an attempt to break up the components and some light topic suggestions.

1. Maestro – CLI Tool

- https://github.com/eclipse-symphony/symphony/blob/main/docs/symphony-book/get-started/quick_start_maestro.md

2. An additional way to manage the Symphony orchestration system is via Kubectl, if that is where the symphony instance has been deployed. Note: This is how I have typically interacted with Symphony.

- https://github.com/eclipse-symphony/symphony/blob/main/docs/symphony-book/get-started/quick_start_helm.md

3. Symphony Orchestration “system”:
- Object model
  - https://github.com/eclipse-symphony/symphony/blob/main/docs/symphony-book/concepts/orchestration_model.md
  - And how we could integrate Margo’s into it
    - Deployment specification
    - Application description
    - Device Description
  - Back-end storage
  - Visual only GUI
  - OTEL Backend

4. Symphony Agent
- https://github.com/eclipse-symphony/symphony/blob/main/docs/symphony-book/agent/_overview.md
- Components
    - Currently the Symphony agent package has many providers included.
- API
    - How we could integrate the WOA api into the Symphony system
