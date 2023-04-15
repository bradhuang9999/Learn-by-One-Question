# Learn-by-one-question

## Security

<details id='defenseInDepth'>
  <summary><b>Defense in Depth</b>: What is defense in depth, what are its layers, and what are their respective definitions?</summary>
<br>
<b>Answer:</b>  

- Physical: Ensuring the security of devices in the physical world
- Identity & access: Ensuring that data access is in compliance with authentication and authorization, with RBAC as the standard
- Perimeter: Defending against DDOS attacks, firewall protection
- Network: Allowing access only from necessary IP ranges, subnet segmentation
- Compute: Ensuring that the operating system is up-to-date and free from malicious code
- Application: Ensuring that the program has no security vulnerabilities and does not store sensitive data
- Data: Ensuring that data access is protected
</details>

<details>
  <summary><b>Zero Trust</b>: What are the differences between zero trust architecture and traditional architecture?</summary>
<br>
<b>Answer:</b> 

In traditional architecture, firewalls and identity authentication are only set up at the network boundary, and the identity of the user is trusted once they enter the internal network.

In contrast, zero trust architecture involves cutting up the network into multiple layers and assuming that the previous layer may have already been penetrated. Firewalls, whitelists, account security authentication, and the principle of least privilege are still implemented between different layers and services. Dangerous signs are constantly monitored and MFA is usually set up at the network boundary.
</details>

### Identity and access management

<details id='MFA'>
  <summary><b>MFA</b>: What is the impact of MFA on user experience? How do you balance security and user experience?</summary>
<br>
<b>Answer:</b>  

MFA requires users to go through multiple verification methods, which can negatively impact user experience. To balance security and user experience, simplified authentication methods such as Passwordless can be used, which can utilize mobile devices or fingerprint verification to confirm user identity. Another approach is to use Conditional Access, which intelligently assesses the user's location and behavior and requires additional verification if there is a higher level of suspicion.
</details>

<details id='RBAC'>
  <summary><b>RBAC</b>: List important design principles related to RBAC?</summary>
<br>
<b>Answer:</b>  

- Role-Based Access Control (RBAC): Replaces the traditional action-based access control framework with an abstracted system of roles, which are assigned specific permissions for system resources. User access is then granted according to the roles assigned to them, thereby reducing complexity and minimizing the risk of errors.
- Least Privilege: Users should be granted only the minimum permissions necessary for them to perform their assigned tasks, to minimize the security risks associated with granting excessive privileges.
- Separation of Duties: Reduces the risk of a particular role being compromised or abused by internal members by minimizing the overlap of permissions between different roles.
- Layered Access Control: Establishes different levels of control based on the importance and sensitivity of resources, with caution exercised when granting high-level permissions to reduce the risk of misuse or leakage of high-risk resources.
</details>



<details id='OAuth2'>
  <summary><b>OAuth2</b>: Introduction to important roles and authorization process of Oauth2</summary>
<br>
<b>Answer:</b>  

Roles include: client, resource provider, authorization provider
Authorization process:

1. The client requests resources from the resource provider.
2. The resource provider determines that the client does not have permission to access the requested data and redirects the client to the authorization provider.
3. The client completes identity authentication with the authorization provider, who then issues an Access Token signed with its private key.
4. The client uses the Access Token to request resources from the resource provider.
5. The resource provider verifies the validity and contents of the Access Token using a public key and allows access to the resources if it is valid and its content and expiration are correct.
</details>


<details id='JWT'>
  <summary><b>JWT</b>: What is the core concept of JWT? What are the advantages of JWT?</summary>
<br>
<b>Answer:</b>  

The core concept of JWT is to store authorization information and signature content together in an open standard, making it easy to exchange this authorization information.

Advantages:
- Stateless: JWT itself contains authorization information and signature content, and the server does not need to store additional information, which improves server fault tolerance and scalability.
- High security: JWT contains signature information to prevent data tampering.
- Cross-domain usage: JWT can be used for cross-domain authentication by placing it in the Authorization header of the HTTP header.
- Cross-platform usage: JWT uses the standard JSON format, which is easy to generate and verify in various environments.
- Extensible: JWT can place custom attributes to provide more authorization information.
</details>

### Network Security

<details id='sub-network'>
  <summary><b>Sub network</b>: How to segment a large enterprise network into independent subnets for each department, while allowing inter-department communication?</summary>
<br>
<b>Answer:</b>  

- Segmentation: Divide the network into subnets according to the estimated size of each department.
- Linking: Determine the connectivity requirements between departments, estimate the traffic size, and set up sufficient routers.
- Redundancy: Automatically switch to backup networks and routers when service disruption is detected.
- Security:
  - Set up firewalls between domains, open IP whitelist for communication, and retain network transmission records.
  - IDS (Intrusion Detection System): Monitor network traffic to detect intrusion threats.
  - IPS (Intrusion Prevention System): Monitor network devices to detect suspicious traffic and commands.
</details>


<details id='firewall'>
  <summary><b>Firewall</b>: Introduce common protection mechanisms of firewalls.</summary>
<br>
<b>Answer:</b>  

- Layer 4 firewall
    - Allow specific IP addresses
    - Allow specific ports
- Layer 7 firewall
    - Allow specific URLs
    - Allow specific headers
    - Web application firewall
        - Check for attack strings such as XSS, SQL injection, etc.
    - Stateful firewall
        - Record the behavior of this IP address before and after to determine if there is any risk.
</details>



<details id=''>
  <summary><b>VPN</b>: What are the advantages and disadvantages of using VPN in cloud architecture?</summary>
<br>
<b>Answer:</b>  

Advantages:

- It can establish secure encrypted connections over public networks.
- It can establish communication between multiple private networks in different regions.
- It allows remote workers to securely connect to private networks.
- It can provide an additional layer of security protection for network applications.

Disadvantages:

- Encryption and decryption require computational resources, which can slow down transmission speed.
- The technology is more complex and requires additional devices, resulting in higher management and setup costs.
- VPN facilities are vulnerable to network attacks such as DDOS.
</details>

<!--Template
<details id=''>
  <summary><b></b>: </summary>
<br>
<b>Answer:</b>  


</details>
-->
