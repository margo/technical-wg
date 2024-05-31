# Technical Working Group Repository
Repository for Technical Working Group facilitation
* Location to view the meeting agenda and minutes for technical working sessions.
    * These are auto generated as an issue within this repository every week per focus group. Focus group leads should edit the agenda post auto creation to inform attendees of topics to be discussed. 
    * Meeting minutes are attached to the Meeting agenda MDs then the issue is closed for record keeping.
* General Information regarding the current Focus groups and planned focus groups for the Margo Release 1 System Design.

## Overall Margo Release 1 Github Project
* https://github.com/orgs/margo/projects/7

## Current Technical Focus Group Details
Below are details regarding the current focus groups, leads, meeting information, associated Github Project, and associated markdowns within the specification repository. 

### FG: Workload Orchestration Agent Interfaces
* Focus Group Lead
    * Armand Craig(ajcraig@rockwellautomation.com)
* Focus Group Meeting Details
    * Tuesdays, 2pm CET meeting
* Associated Github Project to track activites
    * https://github.com/orgs/margo/projects/3 
* Associated Mardowns within specification repository
    * [Workload Orchestration Agent](https://github.com/margo/specification/blob/pre-draft/system-design/app-interoperability/workload-orchestration-agent.md)
    * [Device Capability Discovery](https://github.com/margo/specification/blob/pre-draft/system-design/app-interoperability/device-capability-discovery.md)
    * [Orchestrator App Config and Deploy](https://github.com/margo/specification/blob/pre-draft/system-design/app-interoperability/orchestator-app-config-deploy.md)
### FG: Observability requirements
* Focus Group Lead
    * Philip Presson(philip.presson@us.abb.com) 
* Focus Group Meeting Details
    * Tuesdays, 3PM CET
* Associated Github Project to track activites
    * https://github.com/orgs/margo/projects/4
* Associated Mardowns within specification repository
     * [Observability](https://github.com/margo/specification/blob/pre-draft/system-design/app-interoperability/observability.md)
### FG: Application Package definitions
* Focus Group Lead
    * Arne Broering(arne.broering@siemens.com)
* Focus Group Meeting Details
    * Wednesdays, 2PM CET
* Associated Github Project to track activites
    * https://github.com/orgs/margo/projects/5
* Associated Mardowns within specification repository
    * [Application Package Definition](https://github.com/margo/specification/blob/pre-draft/system-design/app-interoperability/application-package-definition.md)
### FG: Device Requirements
* Focus Group Lead
    * Merrill Harriman(merrill.harriman@se.com) 
* Focus Group Meeting Details
    * Wednesdays, 3PM CET
* Associated Github Project to track activites
    * https://github.com/orgs/margo/projects/6
* Associated Mardowns within specification repository
    * [Device Requirements](https://github.com/margo/specification/blob/pre-draft/system-design/device-interoperability/device-requirements.md)

## Future Planned Focus Group Details
Note: These are theoretical focus groups that ensure coverage for the full envisioned system design within Margo. We are looking for volunteers/contributers within these focus groups. 

### FG: Device Orchestration Agent
* Short Description: This describes the functionality of the Agent intended to interact with the Device Orchestration software along with applying updates to host device.
* Additional features:
    * Device Onboarding
    * Agent supported interfaces
    * Device Update API
    * Device Update deployment concept
    * Device Certificate / Authentication Management
### FG: Device Update Definition
* Short Description: This describes the interoperable definition of the Device Update file and repository. functionality of the Agent intended to interact with the Device Orchestration software along with applying updates to host device.
* Additional features:
    * Abstract Device Update file utilized by the Device Orchestration Software
    * Define interfaces to the Device Update Repository
### FG: Policy Agent
* Short Description: This focus group is related to the Policy Agent that exists within the Margo Compliant Devices. 
### FG: Test and Compliance Suite
* Short Description: This focus group is intended to tackle and plan the test and compliance suite that will be utilized by product vendors to ensure compliance with the Margo Specification
### FG: Official Reference Implementation
* Short Description: This focus group is intended to work on the official reference implementation.

