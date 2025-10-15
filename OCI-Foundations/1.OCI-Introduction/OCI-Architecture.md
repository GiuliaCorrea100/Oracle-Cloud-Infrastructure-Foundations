## 1. Regions

- **Definition:** A *region* is a localized geographic area that contains one or more **Availability Domains (ADs)**.
- **Key Points:**
    - Provides lowest latency when chosen near users.
    - Must be selected carefully based on:
        1. **Proximity to users** → lowest latency, best performance.
        2. **Data residency & compliance** → meet local regulations.
        3. **Service availability** → not all services are in all regions.

## 2. Availability Domains (ADs)

- **Definition:** One or more **fault-tolerant data centers** within a region, connected by low-latency, high-bandwidth networks.
- **Properties:**
    - Isolated from each other.
    - Do not share physical infrastructure (power, cooling, or internal network).
    - Unlikely to fail simultaneously.
- **Example:**
    - A region may have 3 ADs. If one fails, the others remain operational.

## 3. Fault Domains (FDs)

- **Definition:** Logical groupings of hardware and infrastructure *within an Availability Domain*.
- **Purpose:** Provide anti-affinity → reduce single point of hardware failure.
- **Typical Setup:**
    - Each AD has **3 Fault Domains**.
    - Protects against failures in servers, racks, switches, or power units.
- **Guidelines:**
    - Spread resources across FDs to achieve **high availability (HA)**.
    - At any time, Oracle updates only 1 FD to limit impact.
    - You can select which FD to use when launching instances.

## 4. Designing for High Availability

- **Basic Strategy:**
    - Deploy applications across multiple FDs within an AD.
    - Replicate database and application tiers across different FDs.
- **Advanced Strategy:**
    - Replicate across multiple ADs in the same region.
    - Use technologies (e.g., **Oracle Data Guard**) to synchronize databases.
- **Single-AD Regions:**
    - Even when only 1 AD exists, FDs can still be used to increase redundancy.

## 5. Disaster Recovery & Region Pairing

- **Concept:** Most countries have at least **two regions** (region pairs).
- **Use Cases:**
    - Backup & disaster recovery.
    - Meeting data residency and compliance requirements.