### 1️⃣ **Simple Routing**

- The most basic routing method.
- All requests are directed to a **single** resource (e.g., a single IP or domain).
- No special rules, just a straightforward mapping from domain to resource.
- Example:
    - `example.com` → `192.168.1.1`

### 2️⃣ **Weighted Routing**

- Traffic is distributed among multiple resources **based on assigned weights**.
- Useful for **gradual deployment, testing, or traffic splitting**.
- Example:
    - `example.com` → **80%** traffic to `192.168.1.1`
    - `example.com` → **20%** traffic to `192.168.1.2`

### 3️⃣ **Latency-Based Routing**

- Traffic is directed to the resource with the **lowest latency (fastest response time)** for the user.
- Helpful for **global applications** where users should connect to the nearest server.
- Example:
    - A user in **India** is routed to an **India-based server**.
    - A user in **US** is routed to a **US-based server**.

### 4️⃣ **Geolocation Routing**

- Routes traffic based on the **geographic location of the user**.
- Useful for region-specific content, compliance, or legal requirements.
- Example:
    - Users from **India** → `india.example.com`
    - Users from **USA** → `usa.example.com`
	

### 6️⃣ **Failover Routing**

- Used for **high availability**.
- Routes traffic to a **primary resource**, and if it fails, traffic is sent to a **secondary (backup) resource**.
- Example:
    - `example.com` → **Primary Server** (`192.168.1.1`)
    - If it goes **down**, traffic is routed to **Backup Server** (`192.168.1.2`