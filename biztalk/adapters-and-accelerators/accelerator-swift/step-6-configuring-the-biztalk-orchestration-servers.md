---
title: 步驟 6： 設定 BizTalk 協調流程伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestration server, configuring
- configuring, orchestration servers
ms.assetid: 1eb38fac-264d-4730-b16b-572dbb6fabd9
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51ca589433d945dfdc5acac0602151b9f7cf6374
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991719"
---
# <a name="step-6-configuring-the-biztalk-orchestration-servers"></a><span data-ttu-id="8091f-102">步驟 6： 設定 BizTalk 協調流程伺服器</span><span class="sxs-lookup"><span data-stu-id="8091f-102">Step 6: Configuring the BizTalk Orchestration Servers</span></span>
<span data-ttu-id="8091f-103">本章節提供指導方針設定 BizTalk 協調流程伺服器。</span><span class="sxs-lookup"><span data-stu-id="8091f-103">This section provides guidelines on configuring the BizTalk Orchestration servers.</span></span>  
  
### <a name="to-configure-the-biztalk-orchestration-servers"></a><span data-ttu-id="8091f-104">若要設定 BizTalk 協調流程伺服器</span><span class="sxs-lookup"><span data-stu-id="8091f-104">To configure the BizTalk Orchestration servers</span></span>  
  
1. <span data-ttu-id="8091f-105">選取 [新增/移除從啟用網路 Distributed Transaction Coordinator (DTC) 存取[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]應用程式伺服器] 類別底下的元件。</span><span class="sxs-lookup"><span data-stu-id="8091f-105">Enable Network Distributed Transaction Coordinator (DTC) access by selecting it from the Add/Remove [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Components under the Application Server category.</span></span> <span data-ttu-id="8091f-106">上已啟用網路 DTC 用戶端存取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]先前步驟中的電腦。</span><span class="sxs-lookup"><span data-stu-id="8091f-106">Network DTC client access was enabled on the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] computer in an earlier step.</span></span> <span data-ttu-id="8091f-107">疑難排解 DTC 問題的相關資訊的 Microsoft 說明及支援 」 網站上，請參閱下列知識庫文件：</span><span class="sxs-lookup"><span data-stu-id="8091f-107">See the following Knowledge Base articles on the Microsoft Help and Support Web site for information about troubleshooting DTC issues:</span></span>  
  
   - <span data-ttu-id="8091f-108">若要疑難排解 MS DTC 防火牆問題，位於如何[ http://go.microsoft.com/fwlink/?linkid=48870 ](http://go.microsoft.com/fwlink/?linkid=48870)。</span><span class="sxs-lookup"><span data-stu-id="8091f-108">How To Troubleshoot MS DTC Firewall Issues, located at [http://go.microsoft.com/fwlink/?linkid=48870](http://go.microsoft.com/fwlink/?linkid=48870).</span></span>  
  
   - <span data-ttu-id="8091f-109">如何使用 DTCTester 工具，位於[ http://go.microsoft.com/fwlink/?linkid=48871 ](http://go.microsoft.com/fwlink/?linkid=48871)。</span><span class="sxs-lookup"><span data-stu-id="8091f-109">How To Use DTCTester Tool, located at [http://go.microsoft.com/fwlink/?linkid=48871](http://go.microsoft.com/fwlink/?linkid=48871).</span></span>  
  
   - <span data-ttu-id="8091f-110">如果 DTC 位於防火牆後方，請參閱 < 設定 Microsoft Distributed Transaction Coordinator (DTC) 來工作透過防火牆，位於[ http://go.microsoft.com/fwlink/?linkid=48872 ](http://go.microsoft.com/fwlink/?linkid=48872)。</span><span class="sxs-lookup"><span data-stu-id="8091f-110">If DTC is behind a firewall, see Configuring Microsoft Distributed Transaction Coordinator (DTC) to Work Through a Firewall, located at [http://go.microsoft.com/fwlink/?linkid=48872](http://go.microsoft.com/fwlink/?linkid=48872).</span></span>  
  
2. <span data-ttu-id="8091f-111">安裝 BizTalk Server 的其他軟體必要元件，安裝並設定 BizTalk Server 中所述[安裝和設定 BizTalk Server 協調流程伺服器上](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-orchestration-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="8091f-111">Install additional software prerequisites for BizTalk Server, and install and configure BizTalk Server, as described in [Installing and Configuring BizTalk Server on the Orchestration Servers](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-orchestration-servers.md).</span></span>  
  
3. <span data-ttu-id="8091f-112">安裝和設定[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]安裝中所述，[安裝和設定 BizTalk Accelerator for SWIFT 傳訊伺服器上](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="8091f-112">Install and configure [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as described in Installing and [Installing and Configuring BizTalk Accelerator for SWIFT on Messaging Servers](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md).</span></span>  
  
   <span data-ttu-id="8091f-113">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="8091f-113">This section contains:</span></span>  
  
-   [<span data-ttu-id="8091f-114">在協調流程伺服器上安裝和設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="8091f-114">Installing and Configuring BizTalk Server on the Orchestration Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-orchestration-servers.md)  
  
-   [<span data-ttu-id="8091f-115">在協調流程伺服器上安裝和設定 BizTalk Accelerator for SWIFT</span><span class="sxs-lookup"><span data-stu-id="8091f-115">Installing and Configuring BizTalk Accelerator for SWIFT on Orchestration Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/install-and-configure-biztalk-accelerator-for-swift-on-orchestration-servers.md)