# Zero Trust Applied to Infrastructure
<!Introduction for VM, Storage, Network and Identity ZT docs produced by FTA Team!>

The **Zero Trust** security model is not a Microsoft product or service. It is an approach to  implementing IT architecture with security at the forefront of every decision. Zero Trust is a mindset shift to “never trust, always verify” and will require changes to cloud infrastructure deployment strategy and implementation.
Microsoft has its own Zero Trust security strategy which is based on three security principles: 

- Verify explicitly 
- Use least privilege access 
- Assume breach 

In order to   secure your cloud infrastructure in adherence to the Microsoft Zero Trust principles, you should  implement various security best practices and services across your Azure workloads.

To simplify the process,  consider the following  six pillars: 

- Identity 
- Endpoints 
- Data 
- Apps 
- Infrastructure 
- Network 

To learn more about Microsoft’s Zero Trust strategy, review [Zero Trust implementation guidance](https://docs.microsoft.com/en-us/security/zero-trust/zero-trust-overview).

To read more about Zero Trust conceptually, refer to [NIST Zero Trust Architecture](https://www.nist.gov/publications/zero-trust-architecture).

## Getting started
There are many Microsoft documents regarding Zero Trust, starting with the links above, in which you will find conceptual explanations, methodologies, and deployment guides. This document’s main purpose is to explain step-by-step the  the security services and best practices that you should  consider adding to your cloud infrastructure so that you can meet the requirements of the Zero Trust approach.

This document is divided into 5 articles, including this introduction -a high-level review of the content you will find in the other 4 articles. These articles will cover in detail how to implement Zero Trust for core Azure infrastructure components:
- Azure Virtual Machines 
- Azure Storage
- Azure Networks
- Azure Active Directory and hybrid identity model

## Azure Virtual Machines secured with Zero Trust approach

To enforce Zero Trust across your Azure Virtual Machines, consider a holistic approach that creates a secure baseline for new machines, enables encryption and utilizes a key store such as Key Vault, restricts network access to VMs, leverages Microsoft Defender for Cloud capabilities, and several other security-focused configurations.
For step-by-step instructions on implementing Zero Trust for Azure VMs, please review [Create Zero Trust in Virtual Machines](../Infra/VMs.md). 

## Azure Storage secured with Zero Trust approach
Data is one of the most important assets of any company. All infrastructure deployments, applications, and endpoints will produce some type of data assets, and they will need to be stored somewhere securely. Data should be protected regardless of its state - at rest, in transit, or in memory.

The Microsoft Zero Trust document [Secure data with Zero Trust](https://docs.microsoft.com/en-us/security/zero-trust/deploy/data) presents three core elements for a data protection strategy:
- Know your data 
- Protect your data and prevent data loss 
- Monitor and remediate 
  
For step-by-step instructions on implementing Zero Trust for Azure Storage, please review [Create Zero Trust in Storage](../Data/Storage.md). 
  
## Azure Active Directory Identity secured with Zero Trust approach 
Identity services are very important as  they not only authenticate and authorize  individuals, , but also devices and services, such as Azure Managed Identities. Active Directory and Azure Active Directory are two of the most utilized Identity solutions across enterprises, and features such as Conditional Access and Privileged Identity Management can be used to secure them according to the Zero Trust model. Aside from these two tools, it is also recommended to take measures such as implementing MFA across users, conducting access reviews periodically, restricting access to the AAD Admin Portal, to list a few. 
 For step-by-step instructions on implementing Zero Trust for Azure Azure Active Directory, please review [Create Zero Trust in Azure Active Directory/Hybrid Identity](../Identity/identity.md). 

## Azure Networks secured with Zero Trust approach 
According to [Microsoft Zero Trust documents for Networks](https://docs.microsoft.com/en-us/security/zero-trust/deploy/networks), there are three key objectives to secure your network:
- be ready at any time to handle attacks before they happen 
- mitigate the damage and attack in case it happens
- increase the difficulty for attackers to compromise your cloud footprint
  
To accomplish the above objectives, consider the  Zero Trust principles discussed earlier: verify explicitly, use least privileged access, and assume breach.
To secure Azure Hub and Spoke Network Topology with Zero Trust, consider the following changes - utilizing Network Security Groups (NSGs) to restrict and limit unnecessary communication between resources, deploying Application Security Groups, and monitoring NSGs by enabling logging, to name a few.

For step-by-step instructions on implementing Zero Trust for Azure Networks, please review [**INSERT LINK TO Networks DOC**]. 

## Common enterprise infrastructure architecture

We will consider a very common customer IT environment as a model to apply the Zero Trust approach and explain which Microsoft security services to consider and how to implement them accordingly. 

The diagram below shows a hybrid environment with components in the Azure public cloud and on-premises. Users access the Azure environment through the Internet, from their branches, and from their on-premises data center.

![image](https://user-images.githubusercontent.com/97529152/185668544-fafc77b3-3edb-4e00-a336-62eeea2ae185.png)

From a workload perspective, the scenario above contains at Azure environment a three-tier application model running on Virtual Machines with a front-end server, application server, and a database server. Those services are running in an hub-spoken network topology with security implemented through Azure Firewall at Layer 4 and an Application Gateway with WAF (Web Application Firewall) at Layer 7.

In this scenario, workloads running on those VMs connect on Azure Storage and they are also able to communicate with on-premises environment through a VPN.

The Azure environment and hosted applications rely on Azure Active Directory as the Identity Provider for authentication and authorization of users. This environment have Azure Active Directory synchronized with on-premises Active Directory Domain Services (ADDS).

To give you an idea of how that environment can be implemented securely with some of the Security services implemented based on Zero Trust approach, this presents a step by step that may be followed (see the workflow through the diagram above):

1. configure Azure AD users that will be used in the entire environment, considering those ones that will authenticate to access Azure Portal and access Applications and Storage

2. define RBAC permissions for users that will manage and deploy on Azure environment

3. build all the Azure network VNETs and their subnets

4. configure the NSG (Network Security Group) and ASG (Application Security Group) according to the Security rules for the environment

5.create the VPN gateway on Azure VNET to communicate with on-premises environment

6. Deploy Azure Firewall and the policies (rules) that will be considered

7. Deploy Application Gateway with Web Application Firewall

Once we have network topology implemented with some of the main Security components, we may:

8. deploy Azure VMs, then apply ASG to the VMs

9. Configure the backend pool for Application Gateway

10. Configure Azure Bastion to access VMs securely

11. Deploy Storage Account, configure the blob storage and file servers

12. Set Storage security parameteres

13. set Azure AD Security features: MFA, Conditional Access, Identity Protection and Privileged Identity Management

14. Turn on Microsoft Defender for Cloud (MDC) for the components on the environment

15. Configure Azure Monitor to collect VMs logs, set metrics and alerts

## Next Steps

Review detailed guidance on implementing the Zero Trust approach: 
  
1. [Create Zero Trust in Virtual Machines](../Infra/VMs.md)
2. [Create Zero Trust in Azure Storage](../Data/Storage.md)
3. [Create Zero Trust in Azure Active Directory/Hybrid Identity](../Identity/identity.md)
4. ZT for Azure Network - **LINK TBD**

## References

Links below will help you understand more about the infrastructure services mentioned in this series of articles.

- Azure Virtual Machines: https://azure.microsoft.com/en-us/services/virtual-machines/
- Azure Storage: https://docs.microsoft.com/en-us/azure/storage/common/storage-introduction
- Azure Active Directory: https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-whatis
- Azure Network: https://docs.microsoft.com/en-us/azure/networking/fundamentals/networking-overview
