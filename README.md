**Project: Streamlining Ticket Assignment for Efficient Support Operations
Objective**

The objective of this initiative is to implement an automated system for ticket routing at ABC Corporation to improve operational efficiency. By accurately assigning support tickets to the appropriate teams, the solution reduces delays in issue resolution, enhances customer satisfaction, and optimizes resource utilization within the support department.

**Implementation Steps**

**1. User Creation**

Open **ServiceNow.**

Navigate: **All → Users (under System Security).**

Click **New** and enter user details.

Click **Submit.**

Repeat the same process to create another user.

**2. Group Creation**

Open **ServiceNow.**

Navigate: **All → Groups (under System Security).**

Click **New** and enter group details.

Click **Submit.**

Repeat to create another group.

**3. Role Creation**

Open **ServiceNow.**

Navigate: **All → Roles (under System Security).**

Click **New** and enter role details.

Click **Submit.**

Repeat to create another role.

**4. Table Creation**

Open **ServiceNow.**

Navigate: **All → Tables (under System Definition).**

Click **New** and enter details:

**Label:** Operations Related

Enable **Create module** & **Create mobile module**

**New menu name:** Operations Related

Add required **Table columns**

Click **Submit.**

**Choices for Issue Field (via Form Design):**

Unable to login to platform

404 Error

Regarding Certificates

Regarding User Expired

**5. Assign Roles & Users to Groups
Certificates Group**

Navigate: **All → Tables → Certificates Group**

Under **Group Members**, **add Katherine Pierce.**

Under **Roles**, assign **Certification_Role.**

**Platform Group**

Navigate: **All → Tables → Platform Group**

Under **Group Members**, add **Manne Niranjan**.

Under **Roles**, assign **Platform_Role**.

**6. Assign Roles to Table**

Navigate: **All → Tables → Operations Related Table.**

Under **Application Access**:

For **Read Operation**: Require Platform_Role and Certification_Role.

For **Write Operation**: Require Platform_Role and Certification_Role.

**7. Create ACL (Access Control List)**

Navigate: **All → ACL (under System Security).**

Click **New** and create ACL.

Under **Requires Role**, add **Admin Role**.

Create 4 ACLs for the necessary fields.

**8. Flow Designer – Ticket Assignment
Flow 1: Regarding Certificates**

Open **Flow Designer → New Flow**.

**Flow Name:** Regarding Certificate

**Application**: Global

**Run User**: System User

**Trigger:** Create or update a record

**Table:** Operations Related

**Condition**: Issue → is → Regarding Certificates

**Action**: Update record

**Field**: Assigned to group → Value: Certificates

Save & Activate.

**Flow 2: Regarding Platform**

Open **Flow Designer → New Flow.**

**Flow Name:** Regarding Platform

**Application**: Global

**Run User**: System User

**Trigger**: Create or update a record

**Table:** Operations Related

**Condition:**

Issue → is → Unable to login to platform

Issue → is → 404 Error

Issue → is → Regarding User Expired

**Action**: Update record

**Field**: Assigned to group → Value: Platform

Save & Activate.

## 📂 Project Structure
ABC-Ticket-Routing/

│

├── Users/

│   ├── Katherine Pierce (Certificate group)

│   ├── Manne Niranjan (Platform group)

│

├── Groups/

│   ├── Certificates Group

│   ├── Platform Group

│

├── Roles/

│   ├── Certification_role

│   ├── Platform_role

│

├── Tables/

│   ├── u_operations_related

│   │   ├── Issue (Choice field)

│   │   ├── Assigned to Group

│   │   └── Other custom columns

│

├── ACLs/

│   ├── Read access

│   ├── Write access

│   ├── Field-level restrictions

│

├── Flows/

│   ├── Regarding Certificate → Assigns to Certificates Group

│   └── Regarding Platform → Assigns to Platform Group


**Outcome**

This automated ticket routing system in ServiceNow ensures that:

Tickets are automatically directed to the appropriate support groups.

Resolution delays are minimized.

Customer satisfaction is enhanced.

Resources within the support department are utilized efficiently.
