# Introduction
## What is a Container?
A container is an isolated environment for your code. This means that acontainer has no knowledge of your operating system, or your files. Containers have everything that your code needs in order to run, down to a base operating system. But containers and applications must configured to working together.
![VM and Container Deployments](https://www.veritis.com/wp-content/uploads/2019/09/virtual-machine-and-container-deployments.jpg)
<p align="center">Differences between VM and Container Deployment </p>

![image](https://github.com/GrimezSec/Container-Security/assets/128565483/fd2bbc26-c6a6-4e49-9250-2bcc52b17313)
<p align="center">Container Technology Architecture Tiers and Components </p>

## What is Container Security?

Container security refers to measures and practices taken with the goal of ensuring the safety and integrity of containers. Container security comprises everything from the applications inside the containers to the infrastructure they run on. Base image security and quality are critical to ensure that any derivative images come from a trusted source. Build security in your container pipeline by gathering trusted images, managing access with the use of a private registry, integrating security testing and automating deployment, and continuously defending your infrastructure. Container hardening is the process of using container scanning tools to detect possible vulnerabilities and addressing them to minimize the risk of attack.
 
 Robust container security reduces the risk of deploying a container that contains a security flaw or malicious code into a production environment

## Container Security Standarts
1. CIS Docker Benchmark: Developed by the Center for Internet Security (CIS), this benchmark provides a comprehensive set of guidelines for securing Docker containers. It covers areas like container runtime, Docker daemon configuration, image security, container networking, and logging.

2. NIST Guidelines: The National Institute of Standards and Technology (NIST) offers guidelines for container security in its Special Publication (SP) 800-190. This document provides insights into container security challenges and best practices.

3. Docker Security Best Practices: Docker Inc. also provides its own set of security best practices. These guidelines are more practical and tailored to everyday use of Docker.

4. PCI DSS and HIPAA for Compliance: If you're working in environments that require compliance with standards like PCI DSS for payment processing or HIPAA for healthcare information, there are specific guidelines for using containers securely in these environments.

5. OWASP Guidelines: The Open Web Application Security Project (OWASP) also offers resources and tools for securing your Docker containers, especially from an application security perspective.

6. ISO/IEC Standards: While not specific to Docker, ISO/IEC standards related to information security (like ISO/IEC 27001) provide a broad framework that can be applied to Docker environments.

## Types of Container Security Solutions
### Container Monitoring Solutions
Container monitoring is a good solution for security and reliability. Container monitoring tools can give informations about performance and usages to IT Team / DevOps Team. Also monitoring tools offers real-time log streaming, anomaly detection, alerting and other capabilities like usual security solutions.
### Container Scanners
Container scanner tools help identify vulnerabilities, misconfigurations, and other security issues within container images and their runtime environments. Integrating container scanner tools into the DevSecOps pipeline enables continuous security checks, reducing the risk of deploying vulnerable containerized applications into production environments.

### Application-Level Scanning: SCA, SAST, DAST
•SCA: Software Composition Analysis (SCA) is an application security methodology in which development teams can quickly track and analyze any open source component brought into a project. Simply put, SCA is used to scan your dependencies for security vulnerabilities.

•SAST: Static application security testing (SAST), or static analysis, is a testing methodology that analyzes source code to find security vulnerabilities that make your organization’s applications susceptible to attack. SAST scans an application before the code is compiled. It’s also known as white box testing.

•DAST: Dynamic application security testing (DAST) is a type of black-box testing that checks your application from the outside. Software systems rely on inputs and outputs to operate. A DAST tool uses these to check for security problems while the software is actually running

•SBOM: Software Bill of Materials (SBOM) is a list of all the components that are used in a software application. The SBOM helps identify any vulnerabilities and potential security risks in the software supply chain.

### Container Networking
Secure container networking involves restricting unwanted communication and preventing threats from attacking your applications once deployed. These are some strategies for build a secure container network
Secure container networking involves restricting unwanted communication and preventing threats from attacking your applications once deployed. Here are some key strategies to achieve this:

1. Network Isolation:
   
  • Microsegmentation: Divide your container network into smaller, logically isolated segments based on application needs and security requirements. This limits the attack surface and prevents lateral movement of threats within the network.
  
 • Container Network Policies (CNPs): Define granular network access rules for each container or group of containers. These policies specify which containers can communicate with each other and what protocols and ports they can use.

2. Encryption:
   
• Encrypt sensitive data: Use Transport Layer Security (TLS) or similar encryption protocols to protect sensitive data in transit between containers and other services.

• Encrypt container images: Consider encrypting container images at rest to prevent unauthorized access to sensitive information they might contain.

3. Authentication and Authorization:
   
• Implement mutual TLS (mTLS): Require two-way authentication between containers and other services to ensure only authorized communication takes place.

• Role-Based Access Control (RBAC): Grant access to container resources based on user roles and permissions. This minimizes the risk of unauthorized access and privilege escalation.

4. Monitoring and Logging:
   
• Continuously monitor your container network: Look for suspicious activity, such as unusual traffic patterns or unauthorized access attempts.

• Enable logging for all network activity: This will provide valuable data for investigating security incidents and identifying potential vulnerabilities.

5. Tools and Technologies:

• Next-generation firewalls: Deploy containerized next-generation firewalls to filter traffic and block malicious activity at the network layer.

• Security information and event management (SIEM) systems: Collect and analyze security logs from your container environment to identify potential threats and security incidents.

• Service mesh: Utilize service mesh technologies like Istio to provide advanced security features like mTLS, traffic encryption, and access control for containerized microservices.

## Core Threats
   1. Data Breaches: Container security often revolves around data protection. Data breaches occur when malicious users or processes gain unauthorized access to sensitive data stored within containers.
      
   2. Insecure Base Images: Using outdated or unpatched base images increases the risk of vulnerabilities being introduced into the container. This can potentially allow attackers to compromise the container's security.
  
   3. Untrusted Image Registries: When containers are pulled from untrusted registries, there is a risk that malicious images may be introduced into the container environment.

   4. Container Escape Vulnerabilities: Container escape vulnerabilities allow attackers to break out of the container and gain access to the host system.
      
   5. Misconfigurations: Containers often run with excessive privileges or weak security configurations. Misconfigurations in these areas can potentially allow attackers to compromise the container's security.
    
   6. Lack of Regulatory Compliance: Organizations must comply with various regulatory and compliance requirements. Non-compliance with these regulations can lead to security breaches and other consequences.
    
   7. Insider Threats: Containers often operate in highly privileged environments, making them particularly susceptible to insider threats. Unauthorized insiders with access to containers could potentially exploit vulnerabilities to compromise security.
    
   8. Third-Party Vulnerabilities: Third-party components integrated into containers can introduce vulnerabilities that attackers could exploit. These components often have a smaller user base compared to core components, increasing the risk of such vulnerabilities.
    
   9. Complexity: Containers can become complex, leading to a high risk of vulnerabilities being introduced into the system. The more complex a container environment becomes, the higher the risk of a security breach.
    
   10. Container Orchestration and Service Mesh: While these technologies help automate and manage container operations, they can introduce vulnerabilities and increase the risk of a security breach.




## Container Security Practices
• Use container-specific host OSs instead of general-purpose ones to reduce attack surfaces: A container-specific host OS is a minimalist OS designed to only run containers. Using these OSs greatly reduces attack surfaces, allowing fewer opportunities for your containers to be compromised.
Some of Container Specific Operating Systems:
-[CoreOS](https://fedoraproject.org/coreos/)
-[Flatcar](https://www.flatcar.org/)
-[K3OS](https://k3os.io/)
-[Bottlerocket](https://aws.amazon.com/bottlerocket/)
-[Talos Linux](https://www.talos.dev/)
-[Kairos](https://kairos.io/)


• Only group containers with the same purpose, sensitivity, and threat posture on a single host OS kernel to allow for additional in-depth defense: Segmenting containers provides additional defense in-depth. Grouping containers in this manner makes it more difficult for an attacker to expand potential compromises to other groups. It also increases the likelihood that compromises will be detected and contained.

• Adopt container-specific vulnerability management tools and processes for images to prevent compromises: Traditional tools make many assumptions that are misaligned with a containerized model, and are often unable to detect vulnerabilities within containers. Organizations should adopt tools and processes to validate and enforce compliance with secure configuration best practices for images – including centralized reporting, monitoring each image, and preventing non-compliant images from being run.

• Consider using hardware-based countermeasures to provide a basis for trusted computing: Extend security practices across all tiers of the container technology by basing security on a hardware root of trust, such as the Trusted Platform Module (TPM).

• Use container-aware runtime defense tools: Deploy and use a dedicated container security solution capable of monitoring the container environment and providing precise detection of anomalous and malicious activity within it.

## Container Security Architecture
• Container Build Environment (CI/CD)
The container build environment must include automated tests to ensure that container images do not include outdated or insecure libraries or open source components. The continuous integration / continuous delivery (CI/CD) infrastructure itself must also be secured to avoid supply chain attacks. Unauthorized access to build or deployment systems could cause threat actors to inject malicious components into the container environment.

• Container Registries
A container registry is a repository that stores container images. Registries are central to container security because they allow development teams to secure and store container images while scanning them for vulnerabilities. Organizations should treat images as artifacts to ensure their immutability and prevent the introduction of untested or insecure configuration changes into the production environment. This approach also allows organizations to replace or roll back high-risk containers quickly. 

• Container Runtime Environments
Releasing a container into a runtime environment presents several new security risks. Organizations must implement security policies to govern container behavior at runtime, ensuring administrators receive alerts when a container violates a policy. Administrators must also monitor and manage the resources used by containers to ensure the technology stack is not vulnerable to attack.

• Container Orchestration
The container orchestration environment, usually Kubernetes, is one of the most crucial components of container security. Container orchestration tools help manage complex container environments, allowing teams to predictably run and scale their environments. However, the complexity of a container environment can make it an attractive target for attackers, who can exploit misconfigurations to compromise nodes or other infrastructure elements. By compromising a single node, attackers can gain access to additional nodes or even compromise the entire cluster.

# Container Security Checklist

## Secure the Build Pipeline

- [x] Verify the image source (registry)
- [x] Use official base images 
- [x] Lock down access to the image registry (who can push/pull) 
- [x] Scan container image layers for Common Vulnerabilities and Exposures (CVEs) 
- [x] Scan configuration files for security and compliance checks in continuous integration (CI)
- [x] Do a static analysis of the code and libraries used by the code to surface any vulnerabilities in the code and its dependencies
- [x] Tag and automatically prevent vulnerable images from running in certain clusters or prevent them from talking to other containers in the cluster 


## Secure the Host
- [x] Lock down the operating system (like Google’s Container Optimized OS (COS)) 
- [x] Use secure computing (seccomp) to restrict host system call (syscall) access from containers
- [x] Use Security-Enhanced Linux (SELinux) to further isolate containers 
- [x] Utilize container sandboxing projects like gVisor, Kata Containers, etc. to reduce the attack surface


## Secure the Container Runtimes and Configure Admission Control

- [x] Ensure security configurations span across container runtimes, especially if the environment has multiple container runtimes in the cluster (for example, different runtimes for the orchestrator control plane and workloads)
- [x] Use policies (for example, pod security policy in Kubernetes) to restrict which containers can run in the cluster including policies to restrict privileged containers, containers that don’t need write access to a specific volume, and containers that need certain syscalls
- [x] Restrict access to container runtime daemon/APIs


## Secure the Network 

- [x] Secure services that are exposed to the Internet using a firewall 
- [x] Lock down Layer 3 and 4 access for the services using network policy
- [x] Create granular Layer 7 policies using service mesh (such as Istio)
- [x] Use Mutual Transport Layer Security (mTLS) to mutually authenticate containerized workloads (for example, using Istio)
- [x] Segregate containerized workloads with a mix of host segregation and network isolation (for example, separate group of hosts for workload segregation and/or network policies to isolate different group of containerized workloads) 
- [x] Log unsuccessful connection attempts

## Secure the Orchestrator Configuration

- [x] Implement version control for orchestrator service definitions and configurations (using git) for auditing
- [x] Ensure cluster-level policies (such as security policies, network policies, and so on) go through your change request, review, and approval process
- [x] Implement orchestrator API access security using role-based access control (RBAC) and network policies
- [x] Be aware of which third-party plugins (such as Container Network Interfaces [CNIs], Container Storage Interface [CSIs], and Container Runtime Interfaces [CRIs]) are running (binary/DaemonSet/controller), what access they have, and whether they are running as privileged containers
- [x] Control access to the orchestrator control plane APIs from third-party plugins using RBAC and service accounts
- [x] Enable access logs for all API requests to the orchestrator control plane (for example, audit logs in Kubernetes)  
- [x] Scan orchestrator manifests for containerized apps (such as Kubernetes deployment manifests) for security best practices and applicable compliance standards in the CI phase 
- [x] If you have any sensitive configuration information in your cluster that needs to be accessed by containers at runtime make sure the configuration is encrypted (such as encrypted secrets in kubernetes)
- [x] Rorate encryption keys that are used for communication between orchestrator components (for example kubernetes API server and etcd)


## Secure the Cloud Environment

- [x] If you’re running your containers in a cloud, remember the default security configuration (for orchestrator, container runtime, and operating system) can be different for different cloud providers 
- [x] Understand the version of orchestrator and container runtime components your cloud provider is running by default, and whether those components are modified from their open source version
- [x] Scan environment deployment configurations (such as Terraform, Cloud Formation templates, and Azure ARM templates) for security best practices and compliance misalignments 


## Secure the Data

- [x] Use a proper filesystem encryption technology for container storage
- [x] Provide write/execute access only to the containers that need to modify the data in a specific host filesystem path
- [x] Reduce write/execute filesystem access for the host filesystem to a minimum using constructs like Pod Security Policy (for example, only allowing Read-only Root Filesystem access, listing allowed host filesystem paths to mount, and listing allowed Flex volume drivers) 
- [x] Automatically scan container images for sensitive data such as tokens, private keys, and so on, before pushing them to a container registry (can be done locally and in CI) 
- [x] Limit storage related syscalls and capabilities to prevent runtime privilege escalation 
- [x] Log all successful and unsuccessful attempts to access sensitive data


## Secure Workloads
## Application Testing (SCA - SAST - DAST - SBOM)
•SCA: Software Composition Analysis (SCA) is an application security methodology in which development teams can quickly track and analyze any open source component brought into a project. Simply put, SCA is used to scan your dependencies for security vulnerabilities.

•SAST: Static application security testing (SAST), or static analysis, is a testing methodology that analyzes source code to find security vulnerabilities that make your organization’s applications susceptible to attack. SAST scans an application before the code is compiled. It’s also known as white box testing.

•DAST: Dynamic application security testing (DAST) is a type of black-box testing that checks your application from the outside. Software systems rely on inputs and outputs to operate. A DAST tool uses these to check for security problems while the software is actually running

•SBOM: Software Bill of Materials (SBOM) is a list of all the components that are used in a software application. The SBOM helps identify any vulnerabilities and potential security risks in the software supply chain.

## Container Networking
Container network security proactively restricts unwanted communication and prevents threats from attacking your applications once deployed.

Organizations can use containerized next-generation firewalls to protect their containers from network-based threats. Most network based attacks are agnostic of application’s form factor. Therefore, containerized applications are subject to many of the same network-based attacks that infect bare metal and VM based apps, such as cryptojacking, ransomware, BotNetC2, and many more. Containerized next-generation firewalls stop malware from entering and spreading within the cluster, while also preventing malicious outbound connections used in data exfiltration and command-and-control (C2) attacks. While shift-left security tools provide deploy-time protection against known vulnerabilities, containerized next-gen firewalls provide protection against unknown and unpatched vulnerabilities.

Microsegementation tools coupled with next-gen firewalls provide comprehensive container network security. Identity-based microsegmentation helps restrict the communication between applications at layer-3/4 while containerized next-gen firewalls perform layer-7 deep packet inspection and scan all the allowed traffic to identify and prevent known and unknown threats.

## Dockerfile / Docker Container Testing

**Dockerfile Testing**

Focus: Ensures the Dockerfile itself is well-structured, produces the intended image, and includes necessary security measures.

Timing: Conducted during the image building stage, before deployment.

Methods:

   •Linting: Analyzes Dockerfile syntax for errors, best practices, and potential vulnerabilities. Tools: Hadolint, Dockle.
        
   •Static Analysis: Scans for vulnerabilities in base images and dependencies without executing the image. Tools: Snyk, Anchore.

**Docker Container Testing**

Focus: Verifies the functionality and behavior of a running container, including its interactions with other services and the environment.

Timing: Conducted after the image is built and deployed, either in a test environment or production.

Methods:

   •Unit Testing: Tests individual components or functions within the containerized application.
   
   •Integration Testing: Validates interactions between multiple containers or services.
   
   •End-to-End Testing: Simulates real-world user scenarios to ensure overall system functionality.
   
   •Security Testing: Identifies vulnerabilities in running containers. Tools: Clair, Trivy.

**How to Perform Testing:**

Dockerfile Testing:

•Choose tools: Select linters and static analyzers suitable for your requirements.

•Integrate into CI/CD: Automate Dockerfile testing within your CI/CD pipeline to catch issues early.

•Review results: Address any errors, warnings, or vulnerabilities identified by the tools.

Docker Container Testing:

 •Write test cases: Cover various aspects of container functionality and interactions.
    
 •Choose tools: Select appropriate testing frameworks and security scanners.
    
 •Set up a testing environment: Replicate production environment for realistic testing.
    
 •Run tests: Execute test cases and monitor results.
    
 •Address issues: Fix any failures or vulnerabilities found during testing.

# Container Security Tools

## Container Monitoring Tools
| Name | URL | Description |
| :---------- | :---------- | :---------- |
| **Dynatrace** |[Dynatrace](https://www.dynatrace.com/)| APM Solution |
| **Datadog** |[Datadog](https://www.datadoghq.com/)| Cloud-based monitoring platform for Docker|
| **Sematext** |[Sematext](https://sematext.com/)| Docker monitoring tool|
| **Prometheus** |[Prometheus](https://prometheus.io/)| Monitoring and alerting toolkit|
| **Grafana** |[Grafana](https://grafana.com/)|Analytics and monitoring platform  |
| **Elasticsearch** |[Elasticsearch](https://www.elastic.co/)| Search and analytics engine |
| **cAdvisor** |[cAdvisor](https://github.com/google/cadvisor)| A lightweight tool offering real-time metrics on resource usage and performance for Docker containers.|


## Container Scanning Tools

| Name | URL | Description |
| :---------- | :---------- | :---------- |
| **Harbor** | [https://github.com/goharbor/harbor](https://github.com/goharbor/harbor) | Trusted cloud native registry project|
| **Anchore** | [https://github.com/anchore/anchore-engine](https://github.com/anchore/anchore-engine) | Centralized service for inspection, analysis, and certification of container images |
| **Clair** | [https://github.com/quay/clair](https://github.com/quay/clair) | Docker vulnerability scanner|![Clair](https://img.shields.io/github/stars/goharbor/harbor?style=for-the-badge) | 
| **Deepfence ThreatMapper** | [https://github.com/deepfence/ThreatMapper](https://github.com/deepfence/ThreatMapper) | Apache v2, powerful runtime vulnerability scanner for kubernetes, virtual machines and serverless. | 
| **Docker bench** | [https://github.com/docker/docker-bench-security ](https://github.com/docker/docker-bench-security ) | Docker benchmarking against CIS|
| **Falco** | [https://github.com/falcosecurity/falco](https://github.com/falcosecurity/falco) | Container runtime protection |
| **Trivy** | [https://github.com/aquasecurity/trivy](https://github.com/aquasecurity/trivy) | Comprehensive scanner for vulnerabilities in container images |
| **Notary** | [https://github.com/notaryproject/notary](https://github.com/notaryproject/notary) | Docker signing|
| **Cosign** | [https://github.com/sigstore/cosign](https://github.com/sigstore/cosign) | Container signing|
| **watchtower** | [https://github.com/containrrr/watchtower](https://github.com/containrrr/watchtower) | Updates the running version of your containerized app |
| **Grype** | [https://github.com/anchore/grype](https://github.com/anchore/grype) | Vulnerability scanner for container images (and also filesystems). 
# Integrating and Automating Container Security Workflows
Integrating and automating container security workflows is crucial for ensuring the continuous and efficient protection of containerized applications. Here's a step-by-step guide:

1-Define Security Policies:
Clearly define security policies that cover aspects such as image scanning, runtime protection, access controls, and compliance requirements.

2-Select Container Security Tools:
Choose appropriate container security tools based on your defined policies. This may include image scanners, runtime protection tools, and security information and event management (SIEM) solutions.

3-Integrate into CI/CD Pipelines:
Embed container security checks into your continuous integration and continuous deployment (CI/CD) pipelines. This ensures that security measures are applied at every stage of the software development lifecycle.

4-Container Image Scanning:
Implement automated container image scanning tools to check for vulnerabilities and compliance issues in images before they are deployed. Tools like Clair, Trivy, Anchore, or commercial solutions can be integrated.

5-Runtime Protection:
Utilize container-aware runtime defense tools to monitor and detect anomalous activities within the container environment. Tools like Falco, Aqua Security, or Sysdig can provide runtime protection.

6-Orchestration Integration:
Integrate container security measures with your container orchestration platform, such as Kubernetes or Docker Swarm. Leverage security features provided by the orchestration tool.

7-Automate Policy Enforcement:
Use policy enforcement tools to automate the application of security policies. For example, prevent the deployment of containers that do not meet security standards or automatically remediate non-compliant configurations.

8-Incident Response Automation:
Implement automated incident response mechanisms for security events. This could include automatic isolation of compromised containers, alerting, and integration with incident response platforms.

9-Logging and Auditing:
Enable comprehensive logging for container activities and security events. Integrate with logging and auditing tools to track and analyze security-related information.

10-Continuous Monitoring:
Implement continuous monitoring solutions to track changes, detect vulnerabilities, and ensure ongoing compliance. Tools like Prometheus, Grafana, or commercial solutions can aid in continuous monitoring.

11-Automate Security Patching:
Integrate automated patch management tools to ensure that container images are regularly updated with the latest security patches and dependencies.

12-User Training and Awareness:
Include automation for user training and awareness programs related to container security. Regularly update teams on security best practices and emerging threats.

13-Document and Review:
Document the integrated security workflows and conduct regular reviews to ensure that security measures align with evolving threats and organizational requirements.