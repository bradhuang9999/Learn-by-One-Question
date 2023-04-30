# Learn-by-one-question

<h2>Security</h2>

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



<details id='vpn'>
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


<details id='xss'>
  <summary><b>XSS</b>: Introduce the reflected, stored, and DOM-based XSS types, and what are the prevention methods for XSS risk?</summary>
<br>
<b>Answer:</b>  

- Reflected: A type of XSS where a hyperlink URL, cookie, or form contains an XSS string. If the backend dynamically composes a frontend webpage with this data, the XSS program will be executed when the page is displayed.
- Stored: A type of XSS where a database stores an XSS string, and when the database data is dynamically composed to form a frontend webpage, the webpage will execute the XSS program.
- DOM-based: A type of XSS where an AJAX response returns an XSS string, and when this string is directly inserted into the webpage DOM, the webpage will execute the XSS program.

**The prevention methods for XSS risk include:**

- Using CSP (Content Security Policy) to limit the execution of risky content on webpages.
- Performing HTML encoding on output data to avoid displaying risky content.
- Checking the data transmitted to the backend to avoid using or storing risky content.
</details>

<details id='CSRF'>
  <summary><b>CSRF</b>: Can you give me an example scenario of a CSRF attack and explain how to prevent this attack?</summary>
<br>
<b>Answer:</b>  

Example scenario:
Background: A user is logged in to the target website, and the browser stores the website's cookie.
Attack: The user visits a high-risk website that sends a request with attack content to the attacker's website through an image or hyperlink. As the request contains the cookie obtained during login, the target website trusts the request, and therefore falls victim to the attack.

To prevent this attack, the following methods can be used:

1. The server-side should check if the 'Origin' in the request header is from the same domain. If it fails, the request should be discarded.
2. The server-side should generate a CSRF token when creating the webpage, which is stored in the session rather than a cookie. Each request must carry this token to determine if it is from the correct webpage.
</details>

<details id='sql-injection'>
  <summary><b>SQL Injection</b>: How to prevent SQL injection attacks?</summary>
<br>
<b>Answer:</b>  

SQL injection attacks occur when untrusted variables are directly concatenated into SQL strings. If these variables contain attack content, the database may be attacked or unauthorized data may be retrieved. There are two ways to avoid SQL injection:

1. Do not directly concatenate untrusted variables into SQL strings. Instead, use a component to pass variables. For example, in Java, PreparedStatement can be used to pass variables:
    
    Example of code with SQL injection risk:
    
    ```java
    String title = request.getParameter("title"); // variable from front-end
    String sql = "SELECT * FROM booking WHERE title = " + title;
    Statement stmt = conn.createStatement();
    stmt.executeQuery(sql);
    ```
    
    Corrected example:
    
    ```java
    String title = request.getParameter("title"); // variable from front-end
    String sql = "SELECT * FROM booking WHERE title = ?";
    PreparedStatement stmt = conn.prepareStatement(sql);
    stmt.setString(1, title);
    stmt.executeQuery();
    ```
    
2. Check whether untrusted variables contain dangerous strings or unexpected content, such as single quotes, semicolons, etc. If they contain dangerous strings, throw an error or perform appropriate processing.
</details>


<details id='csp'>
  <summary><b>Content Security Policy</b>: What does Content Security Policy primarily set and what attacks can it prevent?</summary>
<br>
<b>Answer:</b>  

Content Security Policy (CSP) can separately set the sources that various resources are allowed to load from, whether inline JS and CSS are allowed, and whether only HTTPS requests are allowed. CSP can prevent attacks such as XSS and CSRF.
</details>


<details id='same-origin-policy'>
  <summary><b>Same-origin policy</b>: What is Same-origin policy and how can different web pages from different origins access each other?</summary>
<br>
<b>Answer:</b>  

Same-origin policy is a browser security mechanism that prevents JavaScript from accessing cookies, DOM, localStorage, indexedDB from other domains. Calls to other domains using AJAX are also restricted to reduce the risk of XSS, cookie leakage, and other external attacks. To access resources from other domains, Cross-Origin Resource Sharing (CORS) can be used. CORS adds Access-Control-Allow-Origin to response headers to allow resources from other domains to be accessed.
</details>

<h2 id="object-oriented">Object-Oriented</h2>

### SOLID Principles

<details id='SRP'>
  <summary><b>SRP</b>: Explain and give an example of the Single Responsibility Principle.</summary>
<br>
<b>Answer:</b>  

A piece of code, such as a class, interface, or function, should only be responsible for a single responsibility in order to reduce coupling, improve readability, maintainability, and testability. For example, in a book order system, order management, order validation, and order SQL should be separated into different classes.
</details>


<details id='ISP'>
  <summary><b>ISP</b>: Explain and give an example of the Interface Segregation Principle.</summary>
<br>
<b>Answer:</b>  

In order to improve the readability and maintainability of code, classes should not be forced to implement methods that they do not need. Therefore, if in some cases, some methods of an interface are not needed to be implemented, that interface should be split into multiple interfaces. For example, if there is an interface called DataManager that is responsible for querying and modifying data, but in some cases only the querying methods is needed, then DataManager should be split into two interfaces: DataReader and DataModifier.
</details>

<details id='LSP'>
  <summary><b>LSP</b>: What problems can occur if a subclass is not designed according to the Liskov substitution principle? How should a subclass be handled if it needs different functionality from its parent class?</summary>
<br>
<b>Answer:</b>  

If a subclass is not designed according to the Liskov substitution principle, there may be conflicts with the behavior of the parent class that can cause errors in calling programs. A subclass should maintain the same behavior as its parent class, with additional details as needed. If different functionality is truly needed, it is best to create a new class instead of inheriting from the parent class.
</details>

<details id='OCP'>
  <summary><b>OCP</b>: What are some ways to achieve the Open-Closed Principle?</summary>
<br>
<b>Answer:</b>  

The Open-Closed Principle states that software entities should be open for extension but closed for modification. To achieve this principle, we can use inheritance, polymorphism, or design patterns, among other ways.

Specifically, some common ways include:
1. Inheritance: Subclasses can inherit existing functionality from parent classes and override only the differences. Implementing interfaces can also achieve similar results.
2. Polymorphism: The same method can have different implementations depending on the input value. This allows for handling different cases without changing existing methods.
3. There are many classic solutions in design patterns that are designed for flexible design, such as using the Builder pattern to provide a flexible way of building objects, using the Decorator pattern to dynamically add additional functionality, and using Dependency Injection to extract changing logic into independent interfaces that are implemented differently based on the input interface, resulting in different processing logic.
</details>


<details id='DIP'>
  <summary><b>DIP</b>: How to implement the Dependency Inversion Principle?</summary>
<br>
<b>Answer:</b>  

The Dependency Inversion Principle refers to the practice of high-level modules using interfaces instead of specific classes when interacting with components, in order to reduce coupling.
There are two ways to implement this principle:

1. Dependency Injection: Components specify the interfaces they return, and determine the implementation classes dynamically when used, instead of being determined by the high-level module. Alternatively, the component provides a setter method.
2. Dependency Lookup: The container management mechanism, such as Spring, dynamically returns the implementation objects of the specified class.
</details>

<!--Template
<details id=''>
  <summary><b></b>: </summary>
<br>
<b>Answer:</b>  


</details>
-->
