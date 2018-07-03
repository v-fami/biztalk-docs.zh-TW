---
title: 安裝和設定 BizTalk Server HTTP 前端伺服器上 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HTTP server, installing BizTalk Server
- BizTalk Server, installing on HTTP servers
ms.assetid: dc1b3675-483a-478f-b30d-62efb73ad13c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38605a921a1c2761f73c5871544d8853814f6e0f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014167"
---
# <a name="installing-and-configuring-biztalk-server-on-the-http-front-end-servers"></a><span data-ttu-id="cfe70-102">安裝和設定 BizTalk Server HTTP 前端伺服器上</span><span class="sxs-lookup"><span data-stu-id="cfe70-102">Installing and Configuring BizTalk Server on the HTTP Front-End Servers</span></span>
<span data-ttu-id="cfe70-103">本節說明如何安裝和設定 BizTalk Server 來裝載 MRSR 站台使用與 HTTP 前端伺服器和[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]範本表單。</span><span class="sxs-lookup"><span data-stu-id="cfe70-103">This section describes how to install and configure BizTalk Server to be used as the HTTP front-end server for hosting the MRSR site and the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] template forms.</span></span>  

### <a name="to-install-and-configure-biztalk-server-on-the-biztalk-http-front-end-servers"></a><span data-ttu-id="cfe70-104">安裝和設定 BizTalk HTTP 前端伺服器上的 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cfe70-104">To install and configure BizTalk Server on the BizTalk HTTP front-end servers</span></span>  

1. <span data-ttu-id="cfe70-105">執行自訂安裝[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]選擇下列功能：**商務規則引擎**並**SharePoint 配接器**。</span><span class="sxs-lookup"><span data-stu-id="cfe70-105">Perform a custom installation of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] choosing the following features: **Business Rules Engine** and **SharePoint Adapter**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="cfe70-106">其他功能不需要這項安裝。</span><span class="sxs-lookup"><span data-stu-id="cfe70-106">Other features are not required for this installation.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="cfe70-107">其中一個 BizTalk HTTP 前端伺服器，當您執行組態，建立 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="cfe70-107">On one of the BizTalk HTTP front-end servers, when you perform configuration, create the BizTalk Group.</span></span>  

2. <span data-ttu-id="cfe70-108">執行設定[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cfe70-108">Perform configuration of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  

3. <span data-ttu-id="cfe70-109">安裝所需的任何其他 hotfix[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]可用的安裝指南。</span><span class="sxs-lookup"><span data-stu-id="cfe70-109">Install any additional hotfixes required by [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as available in the installation guide.</span></span>
