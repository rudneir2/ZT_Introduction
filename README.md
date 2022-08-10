# Zero Trust applied to Infrastructure - Introduction

Introduction for VM, Storage, Network and Identity ZT docs produced by FT Team

## Introduction

If you get on this document before reading anything about Zero Trust, you will find below a summary about what Zero Trust is and how you will be able to apply it for the primary IT infrastructure components running in the Azure public cloud. If you want more information about Zero Trust approach, please read the article in this link Zero Trust implementation guidance | Microsoft Docs. 

Zero Trust security model is not a Microsoft product or service, it is an approach in how to get an IT architecture implemented with security in mind. Many documents about Zero Trust you find on the internet or from other vendors describe the Zero Trust model as “never trust, always verify”. 

Microsoft has its own Zero Trust security strategy, that is based on three security principles: 
•	Verify explicitly 
•	Use least privilege access 
•	Assume breach 

Despite the fact Zero Trust is not a product or service, but an approach to deliver Security to IT environments, to get your IT architecture secure based on the Microsoft Zero Trust principles, you will have to consider some Security services to accomplish the Zero Trust approach. 

To make that easier, Microsoft distributes those three principles above, in six pillars: 
•	Identity 
•	Endpoints 
•	Data 
•	Apps 
•	Infrastructure 
•	Network 

To read more about Zero Trust conceptually from a market perspective, you may read this content: 
Zero trust security model - Wikipedia 
To understand how Microsoft Zero Trust strategy is, you may read this other content: 
Zero Trust implementation guidance | Microsoft Docs 

## The purpose of this document 

There are many Microsoft documents regarding Zero Trust, starting with the links above, which You will find conceptual explanations, methodologies and deployments guides. This document’s main purpose is to explain explicitly what Security services to consider to your infrastructure IT environment so that you may have Zero Trust approach applied to it and how to implement them step by step. 

This document is divided into 5 articles, including this introduction that explains what this is about and a high-level view of the content you will find in the other 4 articles.  

These articles will cover in detail how to implement Zero Trust for the main infrastructure IT components, that is usually found in most companies. 
•	Azure Virtual Machines 
•	Azure Storage 
•	Azure Network 
•	Azure Active Directory identities 


## Common IT infrastructure architecture diagram 

We will consider a very common Customer IT environment as a model to apply Zero Trust approach and explain what Microsoft security services will be considered behind Zero Trust approach and then how to implement them. 
The diagram below shows a scenario that contains a hybrid environment that contains infrastructure components on Azure public cloud and on-premises. Users access Azure environment through the internet, from their branches and from their on-premises Data Center. 



