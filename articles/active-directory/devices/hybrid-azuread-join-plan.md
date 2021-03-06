---
title: How to configure hybrid Azure Active Directory joined devices | Microsoft Docs
description: Learn how to configure hybrid Azure Active Directory joined devices.
services: active-directory
documentationcenter: ''
author: MarkusVi
manager: mtillman
editor: ''

ms.assetid: 54e1b01b-03ee-4c46-bcf0-e01affc0419d
ms.service: active-directory
ms.component: devices
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/31/2018
ms.author: markvi
ms.reviewer: sandeo

---
# How to plan your hybrid Azure Active Directory join implementation

In a similar way to a user, the device is becoming another identity that you as an IT admin, want to protect and use to protect your resources at any time and location. You can accomplish this goal by bringing your device identities to Azure AD. You can do this by doing an Azure AD join, a hybrid Azure AD join or an Azure AD registered device state. By bringing your devices to Azure AD, you get to maximize your end user productivity by enjoying Single-Sign-On (SSO) across your cloud and on-premises resources and at the same time securing access to your cloud and on-premises resources by enabling Conditional Access. For more details, see Conditional Access in Azure AD.

If you have an on-premises Active Directory environment and you want to join your domain-joined devices to Azure AD, you can accomplish this by configuring hybrid Azure AD joined devices. This article provides you with the related steps to implement a hybrid Azure AD join in your environment. 


## Prerequisites

This article assumes that you are familiar with the [Introduction to device management in Azure Active Directory](../device-management-introduction.md).


## Plan your implementation

To plan your hybrid Azure AD implementation, you should familiarize yourself with:

|   |   |
|---|---|
|![Check][1]|Review supported devices|
|![Check][1]|Review things you should know|
|![Check][1]|Select your scenario|


 


## Review supported devices 

Hybrid Azure AD join supports a broad range of Windows devices. Because the configuration for devices running older versions of Windows requires additional or different steps, the supported devices are grouped into two categories:

**Windows current devices**

- Windows 10
    
- Windows Server 2016


For devices running the Windows desktop operating system, the supported version is the Windows 10 Anniversary Update (version 1607) or later. As a best practice, upgrade to the latest version of Windows 10.



 **Windows down-level devices**

- Windows 8.1
 
- Windows 7

- Windows Server 2012 R2
 
- Windows Server 2012 
 
- Windows Server 2008 R2 


As a first planning step, you should review your environment and determine whether you need to support Windows down-level devices.



## Review things you should know

You can't use a hybrid Azure AD join if your environment consists of a single forest that synchronized identity data to more than one Azure AD tenant.

If you are relying on the System Preparation Tool (Sysprep), make sure you create images from an installation of Windows that has not been configured for hybrid Azure AD join.

If you are relying on a Virtual Machine (VM) snapshot to create additional VMs, make sure you use a VM snapshot that has not been configured for hybrid Azure AD join.

The registration of Windows down-level devices is not supported for devices configured for user profile roaming or credential roaming. If you are relying on roaming of profiles or settings, use Windows 10.

The registration of Windows Server running the Domain Controller (DC) role is not supported.

If your organization requires access to the Internet via an authenticated outbound proxy, you must make sure that your Windows 10 computers can successfully authenticate to the outbound proxy. Because Windows 10 computers run device registration using machine context, it is necessary to configure outbound proxy authentication using machine context.

Hybrid Azure AD join is a process to automatically register your on-premises domain-joined devices with Azure AD. There are cases where you don't want all your devices to register automatically. If this is true for you, see How to control the hybrid Azure AD join of your devices.


Hybrid Azure AD join is a process to automatically register your on-premises domain-joined devices with Azure AD. There are cases where you don't want all your devices to register automatically. If this is true for you, see [How to control the hybrid Azure AD join of your devices](hybrid-azuread-join-control.md).



## Select your scenario

You can configure hybrid Azure AD join for the following scenarios:

- Managed domains
- Federated domains  



If your environment has managed domains, hybrid Azure AD join supports:

- Pass Through Authentication (PTA) with Seamless Single Sign On (SSO) 

- Password Has Sync (PHS) with Seamless Single Sign On (SSO) 

Beginning with version 1.1.819.0, Azure AD Connect provides you with a wizard to configure hybrid Azure AD join. The wizard enables you to significantly simplify the configuration process. For more information, see:

- [Configure hybrid Azure Active Directory join for federated domains](hybrid-azuread-join-federated-domains.md)

- [Configure hybrid Azure Active Directory join for managed domains](hybrid-azuread-join-managed-domains.md)


 If installing the required version of Azure AD Connect is not an option for you, see [how to manually configure device registration](../device-management-hybrid-azuread-joined-devices-setup.md). 






## Next steps

> [!div class="nextstepaction"]
> [Configure hybrid Azure Active Directory join for federated domains](hybrid-azuread-join-federated-domains.md)
> [Configure hybrid Azure Active Directory join for managed domains](hybrid-azuread-join-managed-domains.md)




<!--Image references-->
[1]: ./media/hybrid-azuread-join-plan/12.png
