---
title: Overview of Enterprise Integration | Microsoft Docs
description: Use the features of Enterprise Integration to enable business process and integration scenarios using Logic apps
services: logic-apps
documentationcenter: .net,nodejs,java
author: msftman
manager: anneta
editor: cgronlun

ms.assetid: dd517c4d-1701-4247-b83c-183c4d8d8aae
ms.service: logic-apps
ms.workload: integration
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 09/08/2016
ms.author: deonhe

---
# Overview of the Enterprise Integration Pack
## What is the Enterprise Integration Pack?
The Enterprise Integration Pack is Microsoft's cloud-based solution for seamlessly enabling business-to-business (B2B) communications. The pack uses industry standard protocols including [AS2](../logic-apps/logic-apps-enterprise-integration-as2.md), [X12](logic-apps-enterprise-integration-x12.md), and [EDIFACT](../logic-apps/logic-apps-enterprise-integration-edifact.md) to exchange messages between business partners. Messages can be optionally secured using both encryption and digital signatures. 

The pack allows organizations that use different protocols and formats to exchange messages electronically by transforming the different formats into a format that both organizations' systems can interpret and take action on. 

If you are familiar with BizTalk Server or Microsoft Azure BizTalk Services, you'll find it easy to use the Enterprise Integration features because most of the concepts are similar. One major difference is that Enterprise Integration uses integration accounts to simplify the storage and management of artifacts used in B2B communications. 

Architecturally, the Enterprise Integration Pack is based on **integration accounts** that store all the artifacts that can be used to design, deploy, and maintain your B2B apps. An integration account is basically a cloud-based container where you store artifacts such as schemas, partners, certificates, maps, and agreements. These artifacts can then be used in Logic apps to build B2B workflows. Before you can use the artifacts in a Logic app, you need to link your integration account to your Logic app. After linking them, your Logic app will have access to the integration account's artifacts.  

## Why should you use enterprise integration?
* With enterprise integration, you are able to store all your artifacts in one place, which is your integration account. 
* You can leverage the Logic apps engine and all its connectors to build B2B workflows and integrate with 3rd party SaaS applications, on-premises apps as well as custom applications
* You can also leverage Azure functions

## How to get started with enterprise integration?
You can build and manage B2B apps using the Enterprise Integration Pack via the Logic apps designer on the **Azure portal**.  

You can also use [PowerShell](https://msdn.microsoft.com/library/azure/mt652195.aspx "Logic apps PowerShell topics") to manage your Logic apps. 

Here is an overview of the steps you need to take before you can create apps in the Azure portal:
![overview image](media/logic-apps-enterprise-integration-overview/overview-0.png)  

## What are some common scenarios?
Enterprise Integration supports these industry standards:   

* EDI - Electronic Data Interchange  
* EAI - Enterprise Application Integration  

## Here's what you need to get started
* An Azure subscription with an integration account
* Visual Studio 2015 to create maps and schemas
* [Microsoft Azure Logic Apps Enterprise Integration Tools for Visual Studio 2015 2.0](https://aka.ms/vsmapsandschemas)  

## Try it
[Try it now](https://github.com/Azure/azure-quickstart-templates/tree/master/201-logic-app-as2-send-receive) to deploy a fully operational sample AS2 send & receive logic app that uses the B2B features of Logic Apps.

## Learn more about:
* [Agreements](../logic-apps/logic-apps-enterprise-integration-agreements.md "Learn about enterprise integration agreements")
* [Business to Business (B2B) scenarios](../logic-apps/logic-apps-enterprise-integration-b2b.md "Learn how to create Logic apps with B2B features ")  
* [Certificates](logic-apps-enterprise-integration-certificates.md "Learn about enterprise integration certificates")
* [Flat file encoding/decoding](logic-apps-enterprise-integration-flatfile.md "Learn how to encode and decode flat file contents")  
* [Integration accounts](../logic-apps/logic-apps-enterprise-integration-accounts.md "Learn about integration accounts")
* [Maps](../logic-apps/logic-apps-enterprise-integration-maps.md "Learn about enterprise integration maps")
* [Partners](logic-apps-enterprise-integration-partners.md "Learn about enterprise integration partners")
* [Schemas](logic-apps-enterprise-integration-schemas.md "Learn about enterprise integration schemas")
* [XML message validation](logic-apps-enterprise-integration-xml.md "Learn how to validate XML messages with Logic apps")
* [XML transform](logic-apps-enterprise-integration-transform.md "Learn about enterprise integration maps")
* [Enterprise Integration Connectors](../connectors/apis-list.md "Learn about enterprise integration pack connectors")
* [Integration Account Metadata](../logic-apps/logic-apps-enterprise-integration-metadata.md "Learn about integration account metadata")
* [Monitor B2B messages](logic-apps-monitor-b2b-message.md "Learn more about monitoring B2B messages")
* [Tracking B2B messages in OMS portal](logic-apps-track-b2b-messages-omsportal.md "Learn more about tracking B2B messages in OMS portal")

