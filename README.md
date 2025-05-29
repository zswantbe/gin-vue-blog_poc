# gin-vue-blog_poc

/api/config Endpoint Authentication Missing – Configuration Tampering Vulnerability
Vulnerable File: gin-blog-server/internal/manager.go, specifically the line base.PATCH("/config", blogInfoAPI.UpdateConfig)
Impact Scope: Unauthorized attackers can arbitrarily modify core website configurations.

Vulnerability Description:
The UpdateConfig endpoint was mistakenly placed under the base route group, which does not require authentication. As a result, attackers can craft requests to tamper with critical website configurations (e.g., site name, ICP record number, comment review toggle, etc.) without needing to log in or have proper authorization. This may lead to data pollution, security mechanism failure, or service disruption.

Attack Scenario:
An attacker can directly send a carefully crafted PATCH /api/config request to modify the server's configuration without any login or permission checks.
![image](https://github.com/user-attachments/assets/71c4032b-32a4-4c38-b620-f9202a3ae6a5)
![image](https://github.com/user-attachments/assets/8f129c71-4d1e-46a3-b9b9-791634663480)
