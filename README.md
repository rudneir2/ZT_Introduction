# Zero Trust applied to Infrastructure

Introduction for VM, Storage, Network and Identity ZT docs produced by FT Team (DRAFT)

## Introduction

If you get on this document before reading anything about Zero Trust, you will find below a summary about what Zero Trust is and how you will be able to apply it for the primary IT infrastructure components running in the Azure public cloud. If you want more information about Zero Trust approach, please read the article in this link:
https://docs.microsoft.com/en-us/security/zero-trust/zero-trust-overview

**Zero Trust** security model is not a Microsoft product or service, it is an approach in how to get an IT architecture implemented with security in mind. Many documents about Zero Trust you find on the internet or from other vendors describe the Zero Trust model as “never trust, always verify”. 

Microsoft has its own Zero Trust security strategy, that is based on three security principles: 
- Verify explicitly 
- Use least privilege access 
- Assume breach 

Despite the fact Zero Trust is not a product or service, but an approach to deliver Security to IT environments, to get your IT architecture secure based on the Microsoft Zero Trust principles, you will have to consider some Security services to accomplish the Zero Trust approach. 

To make that easier, Microsoft distributes those three principles above, in six pillars: 
- Identity 
- Endpoints 
- Data 
- Apps 
- Infrastructure 
- Network 

## The purpose of this document 

There are many Microsoft documents regarding Zero Trust, starting with the links above, which You will find conceptual explanations, methodologies and deployments guides. This document’s main purpose is to explain explicitly what Security services to consider to your infrastructure IT environment so that you may have Zero Trust approach applied to it and how to implement them step by step. 

This document is divided into 5 articles, including this introduction that explains what this is about and a high-level view of the content you will find in the other 4 articles.  

These articles will cover in detail how to implement Zero Trust for the main infrastructure IT components, that is usually found in most companies. 
- Azure Virtual Machines 
- Azure Storage 
- Azure Network 
- Azure Active Directory identities 

## Common IT infrastructure architecture diagram 

We will consider a very common Customer IT environment as a model to apply Zero Trust approach and explain what Microsoft security services will be considered behind Zero Trust approach and then how to implement them. 

The diagram below shows a scenario that contains a hybrid environment that contains infrastructure components on Azure public cloud and on-premises. Users access Azure environment through the internet, from their branches and from their on-premises Data Center. 

![image](https://user-images.githubusercontent.com/97529152/183962338-a20a7acb-d72f-4add-b31b-362e2e20fc02.png)

From a workload perspective, the Azure environment contains a three-tier application model running on Virtual Machines with a Front-end server, application server and a Database server. Those services are running behind an Azure virtual network, and they are protected by a Security virtual network that contains an Azure Firewall and an Application Gateway with WAF (Web Application Firewall). 

There are many applications that access content on a object storage (Azure blob storage) and on a File Server (Azure File Server). 
Azure environment and some applications rely on Azure Active Directory as identity provider for authentication of many services. Many companies have also Azure Active Directory synchronized with an on-premises identity services such as Active Directory Domain Services (ADDS). 

So, in this scenario below we will have Zero Trust applied for their main infrastructure components: 
1.	Azure Virtual Machine 
2.	Azure Storage 
3.	Azure AD as identity provider 
4.	Azure Virtual Network 

## 1. Azure Virtual Machines implemented with Zero Trust approach 

Virtual Machines may be implemented on-premises or on Azure public cloud. This document will cover Zero Trust applied to Azure Virtual Machines by considering security services available on Azure and also on Microsoft 365 Defender. 
This is what you will have detailed in this document <LINK> that describes how to get Zero Trust for VMs and how to implement them step by step: 
- use RBAC with minimum privileges 
- consider using custom RBAC, whenever you need 
- consider VM type with Secure boot and vTPM, whenever it is possible 
- consider VM disk encryption 
- consider Key Vault to manage your own keys 
- consider a Jump Box VM or Bastion 
- limit access to remote ports such as RDP and SSH 
- consider using MDC with JIT 
- consider System assigned Managed Identity 
- add MSFT Antimalware extension 
- consider MDC for Azure VMs Security recommendation, Security alerts and Security score system 
- consider MDC to: 
- allow VMs to be enrolled on MDE 
- allow for Vulnerability Assessment through Qualys 
- allow for JIT and File integrity monitoring 

## 2. Azure Storage implemented with Zero Trust approach 

Data is one of the most important assets of any Company. All your infrastructure, Application and endpoints produce some type of data, and they need to be stored in somewhere. So, the Data needs to be protected regardless of its state, at rest, in transit or in memory.
  
Microsoft Zero Trust document (https://docs.microsoft.com/en-us/security/zero-trust/deploy/data) presents three core elements for data protection strategy: 
- Know your data 
- Protect your data and prevent data loss 
- Monitor and remediate 
  
You may apply Zero Trust to multiple components that handle or work with Data on your IT environment. This document <<LINK>> presents how to apply Zero Trust approach to your Azure Storage, one of the main components for your Data strategy on the Microsoft public cloud. 
  
This is what you will find step by step to accomplish Zero Trust for Azure Storage: 
- always uses HTTPS to access Azure Storage 
- consider using Azure Active Directory (AAD) to govern accesss to Azure Storage 
- then combine with AAD Conditional Access 
- use Azure Storage SAS (temporary keys) whenever you need 
- try to avoid using anonymous access 
- encrypt data at rest automatically (SSE) 
- use Private endpoint to get only private access, if your architecture design allows for it 
- consider using MDC for Storage recommendations and Security Alert 
  
## 3. Azure Active Directory Identity implemented with Zero Trust approach 

Identity services are very important as Today, it doesn’t authenticate only “people”, but devices and services, as Azure managed identities. Microsoft has one of the Identity solutions most used around the world with both Active Directory and Azure Active Directory. 
This document <<LINK>> contains detailed information about how to implement Zero Trust approach to Azure Active Directory 
  
This is what you will find to accomplish Zero Trust approach for Identity with Azure Active Directory: 
- Conditional Access policies 
- MFA 
- use least privileged access 
- prevent regular users from creating application registration 
- restrict access to Azure AD admin portal 
- restrict group default permissions 
- AAD ID protection 
- Privileged Identity Management 
- AAD Access review 
- AAD Identity governance 
- hybrid identity with AD Connect 
- AAD application proxy 
- AAD as SSO solution 
- Managed identities 

## 4. Azure Network implemented with Zero Trust approach 

According to Microsoft Zero Trust documents for Network <<LINK>>, there are three key objectives to secure your network: 
- be ready at any time to handle attacks before they happen 
- mitigate the damage and attack in case it happens 
- increase the difficulty for attackers to compromise your cloud footprint 
  
To accomplish those objectives above, Microsoft Zero Trust considers the three Zero Trust principles we already talked about it: verify explicitly, use least privileged access and assume breach. 
  
Based on this Zero Trust approach for Azure Network, this is what you will find step by step to accomplish Zero Trust for Azure Network: 
- Turn on Diagnostic Settings (log forwarding) for Azure Firewall 
- Turn on Diagnostic Settings for Application Gateway and WAF 
- deploy NSG with “deny rules” as baseline 
- deploy NSG with specific rules for application 
- configure NSG flow log for Traffic Analytics 
- Network Contributor custom role (recommended) 

## Next Steps
  
Now that you got an introduction about Zero Trust approach for some of the most common IT infrastructure components, you may access those detailed documents to see how to implement Zero Trust for:
  
1. Azure VM - <<LINK TBD>>
2. Azure Storage - <<LINK TBD>>
3. Identity through Azure Active Directory - <<LINK TBD>>
4. Azure Network - <<LINK TBD>>
  
## References

- Link to Zero Trust main doc structure
- Link to Azure VM
- Link to Azure Storage
- Link to Azure Active Directory
- Link to Azure Network
- Link to Azure Security
- Link to ASB



