## 1. What is IAM?

- **Definition:** OCI IAM is the **Identity and Access Management service**, also known as fine-grained access control or role-based access control (RBAC).
- **Purpose:**
    - Ensure the **right people** get the **right access** to the **right resources**.
    - Works through two key aspects:
        1. **Authentication (AuthN):** Verifying *who someone is*.
        2. **Authorization (AuthZ):** Determining *what someone is allowed to do*.

## 2. Authentication (AuthN)

- Focuses on **identity**.
- Confirms that a person is **who they claim to be**.
- Example: Username + password, tokens, or federated login.

## 3. Authorization (AuthZ)

- Focuses on **permissions**.
- Determines **what actions** a user can perform.
- Users are assigned to **roles**, and each role comes with **specific permissions**.

## 4. Key Concepts in OCI IAM

### a) Identity Domain

- A **container** for users and groups.
- Represents a **user population** with associated configurations and security settings.
- Workflow:
    1. Create an **Identity Domain**.
    2. Add **Users** and **Groups**.
    3. Apply **Policies** against groups.
    4. Policies are scoped to **tenancy** or **compartments**.

### b) Groups & Policies

- **Groups:** Collections of users.
- **Policies:** Define access rules (what groups can do).
- Enable **role-based access control (RBAC)**.

### c) Compartments

- Logical **isolation boundary** for resources in OCI.
- You place resources (compute, storage, DB, etc.) inside compartments.
- Policies are often written **per compartment** for fine-grained control.

### d) Resources & OCIDs

- In OCI, everything you create (compute instance, block volume, database, etc.) is a **resource**.
- Each resource has a **unique identifier**: **Oracle Cloud Identifier (OCID)**.

**OCID Structure:**

```jsx
ocid1.<resourceType>.<realm>.<region>.<uniqueID>
```

- **ocid1:** Type prefix.
- **Resource Type:** e.g., computeinstance, blockvolume.
- **Realm:** A set of regions (commercial, government, etc.).
- **Region:** Geographic region code.
- **Unique ID:** Oracle-generated.
- **Examples:**
    - **Tenancy OCID:** No region identifier (global scope).
    - **Block Volume OCID:** Includes region identifier (region-specific resource).
- **Note:**
    - In the **Console**, you rarely deal with OCIDs directly.
    - In **CLI** or **SDKs**, you must reference OCIDs.