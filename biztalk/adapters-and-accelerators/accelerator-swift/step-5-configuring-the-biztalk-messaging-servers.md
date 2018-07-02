---
title: 步驟 5： 設定 BizTalk 傳訊伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, BizTalk Messaging servers
- BizTalk Messaging servers, configuring
ms.assetid: 598d336d-b006-4d02-9249-e9d6d9b6b7b5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9baea2c567148ead98abf6b3aca3f5cad8258e60
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979999"
---
# <a name="step-5-configuring-the-biztalk-messaging-servers"></a><span data-ttu-id="007a2-102">步驟 5： 設定 BizTalk 傳訊伺服器</span><span class="sxs-lookup"><span data-stu-id="007a2-102">Step 5: Configuring the BizTalk Messaging Servers</span></span>
<span data-ttu-id="007a2-103">此章節提供指導方針設定 BizTalk 傳訊伺服器。</span><span class="sxs-lookup"><span data-stu-id="007a2-103">This section provides guidelines on configuring the BizTalk Messaging servers.</span></span>  
  
### <a name="to-configure-the-biztalk-messaging-servers"></a><span data-ttu-id="007a2-104">若要設定的 BizTalk 傳訊伺服器</span><span class="sxs-lookup"><span data-stu-id="007a2-104">To configure the BizTalk Messaging servers</span></span>  
  
1. <span data-ttu-id="007a2-105">選取 [新增/移除從啟用網路 Distributed Transaction Coordinator (DTC) 存取[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]應用程式伺服器] 類別底下的元件。</span><span class="sxs-lookup"><span data-stu-id="007a2-105">Enable Network Distributed Transaction Coordinator (DTC) access by selecting it from the Add/Remove [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Components under the Application Server category.</span></span> <span data-ttu-id="007a2-106">上已啟用網路 DTC 用戶端存取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]先前步驟中的電腦。</span><span class="sxs-lookup"><span data-stu-id="007a2-106">Network DTC client access was enabled on the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] computer in an earlier step.</span></span> <span data-ttu-id="007a2-107">疑難排解 DTC 問題的相關資訊的 Microsoft 說明及支援 」 網站上，請參閱下列知識庫文件：</span><span class="sxs-lookup"><span data-stu-id="007a2-107">See the following Knowledge Base articles on the Microsoft Help and Support Web site for information about troubleshooting DTC issues:</span></span>  
  
   - <span data-ttu-id="007a2-108">若要疑難排解 MS DTC 防火牆問題，位於如何[ http://go.microsoft.com/fwlink/?linkid=48870 ](http://go.microsoft.com/fwlink/?linkid=48870)。</span><span class="sxs-lookup"><span data-stu-id="007a2-108">How To Troubleshoot MS DTC Firewall Issues, located at [http://go.microsoft.com/fwlink/?linkid=48870](http://go.microsoft.com/fwlink/?linkid=48870).</span></span>  
  
   - <span data-ttu-id="007a2-109">如何使用 DTCTester 工具，位於[ http://go.microsoft.com/fwlink/?linkid=48871 ](http://go.microsoft.com/fwlink/?linkid=48871)。</span><span class="sxs-lookup"><span data-stu-id="007a2-109">How To Use DTCTester Tool, located at [http://go.microsoft.com/fwlink/?linkid=48871](http://go.microsoft.com/fwlink/?linkid=48871).</span></span>  
  
   - <span data-ttu-id="007a2-110">如果 DTC 位於防火牆後方，請參閱 「 設定 Microsoft 分散式交易協調器 (DTC) 來工作透過防火牆 」，位於[ http://go.microsoft.com/fwlink/?linkid=48872 ](http://go.microsoft.com/fwlink/?linkid=48872)。</span><span class="sxs-lookup"><span data-stu-id="007a2-110">If DTC is behind a firewall, see "Configuring Microsoft Distributed Transaction Coordinator (DTC) to Work Through a Firewall", located at [http://go.microsoft.com/fwlink/?linkid=48872](http://go.microsoft.com/fwlink/?linkid=48872).</span></span>  
  
2. <span data-ttu-id="007a2-111">設定並確認 網路負載平衡的 biztalk 接收伺服器中所述[步驟 2： 設定伺服器上的 NLB](../../adapters-and-accelerators/accelerator-swift/step-2-configuring-nlb-on-the-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="007a2-111">Configure and verify Network Load Balancing on the BizTalk receive servers as described in [Step 2: Configuring NLB on the Servers](../../adapters-and-accelerators/accelerator-swift/step-2-configuring-nlb-on-the-servers.md).</span></span>  
  
3. <span data-ttu-id="007a2-112">安裝和設定[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]中所述[安裝和設定 BizTalk Accelerator for SWIFT 傳訊伺服器上](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="007a2-112">Install and configure [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as described in [Installing and Configuring BizTalk Accelerator for SWIFT on Messaging Servers](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md).</span></span>  
  
   <span data-ttu-id="007a2-113">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="007a2-113">This section contains:</span></span>  
  
-   [<span data-ttu-id="007a2-114">在傳訊伺服器上安裝和設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="007a2-114">Installing and Configuring BizTalk Server on the Messaging Server</span></span>](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-messaging-server.md)  
  
-   [<span data-ttu-id="007a2-115">在傳訊伺服器上安裝和設定 BizTalk Accelerator for SWIFT</span><span class="sxs-lookup"><span data-stu-id="007a2-115">Installing and Configuring BizTalk Accelerator for SWIFT on Messaging Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md)