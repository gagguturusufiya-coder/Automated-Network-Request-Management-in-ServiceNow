# Automated Network Request Management in ServiceNow



## 1. Project Overview

The **Automated Network Request Management in ServiceNow** project focuses on simplifying and accelerating the handling of network-related service requests.

By leveraging ServiceNow's **Service Catalog, workflows, and automation capabilities**, the solution reduces manual bottlenecks and ensures requests are processed efficiently. End users can submit requests through a self-service portal, while automated approvals, routing, task assignments, notifications, and request updates streamline fulfillment.

The solution is designed to provide faster turnaround, improved SLA compliance, reduced manual effort, and better transparency for both users and IT teams.

## 2. Introduction

Modern enterprises rely heavily on robust and efficient network services to support day-to-day business operations. As organizations grow, the demand for network-related requests such as access provisioning, configuration changes, and connectivity support also increases.

Traditional manual request handling can lead to delays, errors, and limited visibility, which can affect productivity and user satisfaction.

The **Automated Network Request Management in ServiceNow** project addresses these challenges by using ServiceNow's workflow engine, Service Catalog, and automation features. End users can submit requests through a self-service portal, while approvals, task assignments, notifications, and request updates are automated.

This approach improves the user experience and helps IT teams reduce repetitive tasks, improve SLA compliance, and focus on higher-value activities.

## 3. Project Objectives

The main objective of this project is to design and implement a streamlined solution for managing network-related service requests within ServiceNow.

The project aims to:

- Enable end users to submit network service requests through a user-friendly self-service portal.
- Capture and validate the required request information.
- Automate approval processes based on request requirements.
- Route requests for fulfillment.
- Automate task assignments and notifications.
- Create and update network-related records.
- Provide better visibility into request status and processing.
- Reduce manual intervention and processing delays.
- Improve SLA compliance and overall service efficiency.

## 4. Key Features

### Custom Service Catalog

A dedicated **Network Request** catalog item is created for common network-related service requests.

### Dynamic Request Forms

Catalog variables are used to capture relevant request information, including connection type, device type, address, device details, user information, and supporting documents.

### Automated Approval Workflows

Approval processes are configured in Flow Designer so that requests can be reviewed and approved before fulfillment.

### Catalog UI Policies

Catalog UI Policies dynamically control the visibility of fields. For example, when the user selects **Others** as the device type, the additional specification field can be displayed.

### Network Database

A dedicated table is used to store network request information and related records.

### Automated Flow Processing

Flow Designer automates the request lifecycle using actions such as:

- Get Catalog Variables
- Create Record
- Ask for Approval
- Flow Logic
- Send Email
- Update Record

### Notifications and Status Updates

Email notifications and record updates provide users and IT teams with information about the progress of requests.

### Request Tracking

The automated process improves visibility into request processing, approvals, fulfillment, and completion.

## 5. ServiceNow Developer Setup

To develop and implement the project, a ServiceNow Developer environment is required.

### Create a Developer Account

1. Go to the [ServiceNow Developer Portal](https://developer.servicenow.com/dev.do).
2. Sign up for a free developer account.
3. Complete the required registration details.
4. Verify the account using the verification email.
5. Open the ServiceNow Developer Portal.
6. Select **Start Building**.
7. Request a **Personal Developer Instance (PDI)** or use the available application development tools.
8. Access the developer instance after it has been provisioned.

The ServiceNow development environment provides the required tools for creating the catalog item, tables, variables, relationships, and automated flows used in this project.

## 6. Project Implementation in ServiceNow

### Service Catalog Creation

Navigate to:

```text
Application Navigator
→ Service Catalog
→ Maintain Items
→ New
```

Create the catalog item with:

- **Name:** Network Request
- **Catalog:** Service Catalog
- **Category:** Network
- **Short Description:** Network request Management

### Variables Configuration

Open the **Network Request** catalog item and create the required variables.

The project uses variables such as:

- New connection or relocation
- Relocated address
- Types of devices
- Address
- Device details
- Additional information
- Opened on behalf of
- Email ID
- User name
- Phone Number
- Proof of Document

The variables can be configured as mandatory, read-only, dependent, or auto-populated according to the requirement.

### Variable Set Configuration

Variable Sets can be configured when reusable groups of variables are required. The variable set can then be applied to the Network Request catalog item.

### Catalog UI Policy Configuration

A Catalog UI Policy is configured for the Network Request catalog item.

Example condition:

```text
Types of devices is Others
```

When this condition is satisfied, the required additional specification field is made visible through a UI Policy Action.

### Table Creation

Navigate to:

```text
System Definition
→ Tables
→ New
```

Create the required table for storing network request information.

### Field Creation

Fields are created at the table level. The required columns can be added to the Network Database table to store the information submitted through the Network Request catalog item.

### Request Approval Related List

An approval relationship is created so that approval information can be displayed as a related list on the Network Database record.

The relationship is configured between the Network Database table and the approval records.

### Flow Designer Implementation

Create a new flow in **Flow Designer**.

```text
Flow Name: Network Request
Trigger: Application → Service Catalog
```

#### Get Catalog Variables

Use the **Get Catalog Variables** action to retrieve the variables submitted through the Network Request catalog item.

#### Create Record

Use the **Create Record** action and select the **Network Database** table. Map the required catalog variables to the appropriate fields.

#### Ask for Approval

Use the **Ask for Approval** action.

Configure the target record as the Network Database record and define the required approval rules and approvers.

#### Flow Logic

Use an **If** condition to evaluate the approval result.

Example:

```text
Approval State = Approved
```

or

```text
Approval State = Rejected
```

The appropriate flow path can then be executed based on the approval result.

#### Send Email

Use the **Send Email** action to notify the required users or teams. Configure the recipients, subject, and email body according to the project requirement.

#### Update Record

Use the **Update Record** action to update the Network Database record after the approval and processing stages.

### End-to-End Implementation Flow

```text
User
  ↓
Network Request Catalog
  ↓
Catalog Variables
  ↓
Flow Designer Trigger
  ↓
Get Catalog Variables
  ↓
Create Network Database Record
  ↓
Ask for Approval
  ↓
Approval Decision
  ↓
Send Email Notification
  ↓
Update Record
  ↓
Request Fulfillment
```

## 7. Conclusion

The **Automated Network Request Management in ServiceNow** project provides a streamlined and user-friendly solution for handling network-related service requests.

By automating approvals, routing, notifications, record creation, and updates, the system reduces delays and errors associated with manual processes while improving transparency and request visibility.

The solution helps improve SLA compliance and user satisfaction while reducing repetitive IT workload. Overall, the project supports faster and more efficient fulfillment of network services.
