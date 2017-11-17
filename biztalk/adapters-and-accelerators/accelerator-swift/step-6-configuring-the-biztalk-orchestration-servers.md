---
title: "步驟 6： 設定 BizTalk 協調流程伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestration server, configuring
- configuring, orchestration servers
ms.assetid: 1eb38fac-264d-4730-b16b-572dbb6fabd9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acf5cb36908031f9256f25dd68435003b74d2633
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-configuring-the-biztalk-orchestration-servers"></a><span data-ttu-id="1e68b-102">步驟 6： 設定 BizTalk 協調流程伺服器</span><span class="sxs-lookup"><span data-stu-id="1e68b-102">Step 6: Configuring the BizTalk Orchestration Servers</span></span>
<span data-ttu-id="1e68b-103">本節提供設定的 BizTalk 協調流程伺服器上的指導方針。</span><span class="sxs-lookup"><span data-stu-id="1e68b-103">This section provides guidelines on configuring the BizTalk Orchestration servers.</span></span>  
  
### <a name="to-configure-the-biztalk-orchestration-servers"></a><span data-ttu-id="1e68b-104">若要設定 BizTalk 協調流程伺服器</span><span class="sxs-lookup"><span data-stu-id="1e68b-104">To configure the BizTalk Orchestration servers</span></span>  
  
1.  <span data-ttu-id="1e68b-105">啟用從 [新增/移除選取的網路分散式交易協調器 (DTC) 存取[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]應用程式伺服器] 類別底下的元件。</span><span class="sxs-lookup"><span data-stu-id="1e68b-105">Enable Network Distributed Transaction Coordinator (DTC) access by selecting it from the Add/Remove [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Components under the Application Server category.</span></span> <span data-ttu-id="1e68b-106">已啟用網路 DTC 用戶端存取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]在先前步驟中的電腦。</span><span class="sxs-lookup"><span data-stu-id="1e68b-106">Network DTC client access was enabled on the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] computer in an earlier step.</span></span> <span data-ttu-id="1e68b-107">請參閱下列知識庫文件[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]DTC 問題進行疑難排解的相關資訊的說明及支援 」 網站：</span><span class="sxs-lookup"><span data-stu-id="1e68b-107">See the following Knowledge Base articles on the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Help and Support Web site for information about troubleshooting DTC issues:</span></span>  
  
    -   <span data-ttu-id="1e68b-108">若要疑難排解 MS DTC 防火牆問題、 位於如何[http://go.microsoft.com/fwlink/?linkid=48870](http://go.microsoft.com/fwlink/?linkid=48870)。</span><span class="sxs-lookup"><span data-stu-id="1e68b-108">How To Troubleshoot MS DTC Firewall Issues, located at [http://go.microsoft.com/fwlink/?linkid=48870](http://go.microsoft.com/fwlink/?linkid=48870).</span></span>  
  
    -   <span data-ttu-id="1e68b-109">如何使用 DTCTester 工具，位於[http://go.microsoft.com/fwlink/?linkid=48871](http://go.microsoft.com/fwlink/?linkid=48871)。</span><span class="sxs-lookup"><span data-stu-id="1e68b-109">How To Use DTCTester Tool, located at [http://go.microsoft.com/fwlink/?linkid=48871](http://go.microsoft.com/fwlink/?linkid=48871).</span></span>  
  
    -   <span data-ttu-id="1e68b-110">如果 DTC 位於防火牆後方，請參閱設定[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]Distributed Transaction Coordinator (DTC) 來工作透過防火牆，位於[http://go.microsoft.com/fwlink/?linkid=48872](http://go.microsoft.com/fwlink/?linkid=48872)。</span><span class="sxs-lookup"><span data-stu-id="1e68b-110">If DTC is behind a firewall, see Configuring [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Distributed Transaction Coordinator (DTC) to Work Through a Firewall, located at [http://go.microsoft.com/fwlink/?linkid=48872](http://go.microsoft.com/fwlink/?linkid=48872).</span></span>  
  
2.  <span data-ttu-id="1e68b-111">安裝 BizTalk Server 的其他軟體必要元件，安裝並設定[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]中所述，[安裝和設定 BizTalk Server 協調流程伺服器上](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-orchestration-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="1e68b-111">Install additional software prerequisites for BizTalk Server, and install and configure [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], as described in [Installing and Configuring BizTalk Server on the Orchestration Servers](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-orchestration-servers.md).</span></span>  
  
3.  <span data-ttu-id="1e68b-112">安裝和設定[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]安裝中所述，[安裝和設定 BizTalk Accelerator for SWIFT 傳訊的伺服器上](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="1e68b-112">Install and configure [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as described in Installing and [Installing and Configuring BizTalk Accelerator for SWIFT on Messaging Servers](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md).</span></span>  
  
 <span data-ttu-id="1e68b-113">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="1e68b-113">This section contains:</span></span>  
  
-   [<span data-ttu-id="1e68b-114">安裝和設定 BizTalk Server 協調流程伺服器上</span><span class="sxs-lookup"><span data-stu-id="1e68b-114">Installing and Configuring BizTalk Server on the Orchestration Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-orchestration-servers.md)  
  
-   [<span data-ttu-id="1e68b-115">安裝和設定 BizTalk Accelerator for SWIFT 協調流程伺服器上</span><span class="sxs-lookup"><span data-stu-id="1e68b-115">Installing and Configuring BizTalk Accelerator for SWIFT on Orchestration Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/install-and-configure-biztalk-accelerator-for-swift-on-orchestration-servers.md)