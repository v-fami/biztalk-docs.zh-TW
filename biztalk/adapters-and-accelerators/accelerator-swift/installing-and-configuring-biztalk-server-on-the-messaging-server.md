---
title: 安裝和設定 BizTalk Server 傳訊的伺服器上 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Server, installing on BizTalk Messaging servers
- BizTalk Server, configuring
- BizTalk Messaging servers, configuring BizTalk Server
- BizTalk Messaging servers, installing BizTalk Server
ms.assetid: 8aaa1b97-90f0-4317-9403-ac8b5b9f80e3
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5f4013c1fe315646ea7a2ff34772169a03a2d66
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989567"
---
# <a name="installing-and-configuring-biztalk-server-on-the-messaging-server"></a><span data-ttu-id="21511-102">安裝和設定 BizTalk Server 傳訊的伺服器上</span><span class="sxs-lookup"><span data-stu-id="21511-102">Installing and Configuring BizTalk Server on the Messaging Server</span></span>
<span data-ttu-id="21511-103">本節說明如何安裝和設定 BizTalk Server 來作為郵件伺服器連線至 SWIFT 的網路。</span><span class="sxs-lookup"><span data-stu-id="21511-103">This section describes how to install and configure BizTalk Server to be used as the messaging server for connecting to the SWIFT network.</span></span>  

### <a name="to-install-and-configure-biztalk-server-on-the-messaging-server"></a><span data-ttu-id="21511-104">安裝和設定 BizTalk Server 傳訊伺服器上</span><span class="sxs-lookup"><span data-stu-id="21511-104">To install and configure BizTalk Server on the Messaging Server</span></span>  

1. <span data-ttu-id="21511-105">執行自訂安裝的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]選擇 EDI、 人力工作流程服務 (HWS) 和 MRSR 網站除外的所有功能，除非所需的其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="21511-105">Perform a custom installation of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] choosing all the features except EDI, Human Workflow Services (HWS), and MRSR site, unless required by other applications.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="21511-106">請注意，在單一電腦部署中，這台電腦所執行的 HTTP 前端服務的同一部電腦。</span><span class="sxs-lookup"><span data-stu-id="21511-106">Note that in single-computer deployment, this computer is the same computer as the one that runs the HTTP front-end service.</span></span>  

2. <span data-ttu-id="21511-107">執行設定[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="21511-107">Perform configuration of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="21511-108">請勿安裝訊息佇列，因為我們將會安裝[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]又稱為 MSMQT 的 MSMQ 版本。</span><span class="sxs-lookup"><span data-stu-id="21511-108">Do not install Message Queuing, because we will be installing the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] version of MSMQ known as MSMQT.</span></span> <span data-ttu-id="21511-109">MSMQT 的詳細資訊，請參閱 BizTalk 訊息佇列配接器 (MSMQT) 組態，在 MSDN 網站上[ http://go.microsoft.com/fwlink/?LinkID=48875 ](http://go.microsoft.com/fwlink/?LinkID=48875)。</span><span class="sxs-lookup"><span data-stu-id="21511-109">For more information about MSMQT, see BizTalk Message Queuing Adapter (MSMQT) Configuration on the MSDN Web site at [http://go.microsoft.com/fwlink/?LinkID=48875](http://go.microsoft.com/fwlink/?LinkID=48875).</span></span>  

3. <span data-ttu-id="21511-110">安裝所需的任何其他 hotfix[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]可用的安裝指南。</span><span class="sxs-lookup"><span data-stu-id="21511-110">Install any additional hotfixes required by [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as available in the installation guide.</span></span> <span data-ttu-id="21511-111">在此發行集時，沒有必要的 hotfix。</span><span class="sxs-lookup"><span data-stu-id="21511-111">At the time of this publication, there are no required hotfixes.</span></span>
