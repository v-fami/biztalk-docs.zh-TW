---
title: "安裝和設定 BizTalk Server 協調流程伺服器上 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Server, installing on orchestration server
- orchestration server, installing BizTalk Server
ms.assetid: 72376a80-1377-4058-9478-fee668b804d0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d872d58c72110d7af22c6d64e7d212fbee53fae9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="installing-and-configuring-biztalk-server-on-the-orchestration-servers"></a><span data-ttu-id="b4a08-102">安裝和設定 BizTalk Server 協調流程伺服器上</span><span class="sxs-lookup"><span data-stu-id="b4a08-102">Installing and Configuring BizTalk Server on the Orchestration Servers</span></span>
<span data-ttu-id="b4a08-103">本章節描述如何安裝及設定[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]要做為協調流程伺服器用於執行訊息修復/新增提交協調流程和 FIN 修復和重新調整協調流程。</span><span class="sxs-lookup"><span data-stu-id="b4a08-103">This section describes how to install and configure [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] to be used as the orchestration server for running the Message Repair/New Submission orchestration and the FIN Repair and Reconciliation orchestration.</span></span>  
  
### <a name="to-install-and-configure-biztalk-server-on-the-orchestration-server"></a><span data-ttu-id="b4a08-104">安裝和設定 BizTalk Server 協調流程伺服器上</span><span class="sxs-lookup"><span data-stu-id="b4a08-104">To install and configure BizTalk Server on the Orchestration Server</span></span>  
  
1.  <span data-ttu-id="b4a08-105">執行自訂安裝的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]選擇 EDI、 人力工作流程服務 (HWS) 和 MRSR，以外的所有功能，除非需要其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="b4a08-105">Perform a custom installation of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] choosing all the features except EDI, Human Workflow Services (HWS), and MRSR, unless required by other applications.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b4a08-106">在單一電腦部署中，此電腦是指執行 HTTP 前端服務和 BizTalk 傳訊的伺服器在同一部電腦。</span><span class="sxs-lookup"><span data-stu-id="b4a08-106">In the single-computer deployment, this computer is the same computer as the one that runs the HTTP front-end service and the BizTalk Messaging server.</span></span>  
  
2.  <span data-ttu-id="b4a08-107">執行設定[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b4a08-107">Perform configuration of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b4a08-108">設定 BizTalk 協調流程伺服器時，請考慮下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="b4a08-108">Consider the following guidelines when configuring the BizTalk Orchestration servers:</span></span>  
  
    -   <span data-ttu-id="b4a08-109">此伺服器需要只有一個網路介面卡連線到[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="b4a08-109">This server requires only one network adapter to connect it to the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] computer.</span></span> <span data-ttu-id="b4a08-110">不需要像 HTTP 前端伺服器或訊息的伺服器，在公用端的另一個網路介面卡，因此針對駭客嘗試從網際網路或內部/外部網路更安全。</span><span class="sxs-lookup"><span data-stu-id="b4a08-110">It does not require another network adapter on the public side like the HTTP front-end server or the messaging server, and this makes it more secure against hacking attempts coming from the Internet or intranet/extranet.</span></span>  
  
3.  <span data-ttu-id="b4a08-111">安裝所需的任何其他 hotfix[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]為可用安裝指南中。</span><span class="sxs-lookup"><span data-stu-id="b4a08-111">Install any additional hotfixes required by [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as available in the installation guide.</span></span>