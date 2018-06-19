---
title: 步驟 5： 設定 BizTalk 傳訊的伺服器 |Microsoft 文件
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
ms.openlocfilehash: 9e1aea1187417b77071f0821547869a5b84549c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214006"
---
# <a name="step-5-configuring-the-biztalk-messaging-servers"></a><span data-ttu-id="c8159-102">步驟 5： 設定 BizTalk 傳訊的伺服器</span><span class="sxs-lookup"><span data-stu-id="c8159-102">Step 5: Configuring the BizTalk Messaging Servers</span></span>
<span data-ttu-id="c8159-103">此章節提供的指導方針設定 BizTalk 傳訊的伺服器。</span><span class="sxs-lookup"><span data-stu-id="c8159-103">This section provides guidelines on configuring the BizTalk Messaging servers.</span></span>  
  
### <a name="to-configure-the-biztalk-messaging-servers"></a><span data-ttu-id="c8159-104">若要設定 BizTalk 傳訊的伺服器</span><span class="sxs-lookup"><span data-stu-id="c8159-104">To configure the BizTalk Messaging servers</span></span>  
  
1.  <span data-ttu-id="c8159-105">啟用從 [新增/移除選取的網路分散式交易協調器 (DTC) 存取[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]應用程式伺服器] 類別底下的元件。</span><span class="sxs-lookup"><span data-stu-id="c8159-105">Enable Network Distributed Transaction Coordinator (DTC) access by selecting it from the Add/Remove [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Components under the Application Server category.</span></span> <span data-ttu-id="c8159-106">已啟用網路 DTC 用戶端存取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]在先前步驟中的電腦。</span><span class="sxs-lookup"><span data-stu-id="c8159-106">Network DTC client access was enabled on the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] computer in an earlier step.</span></span> <span data-ttu-id="c8159-107">請參閱下列知識庫文件[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]DTC 問題進行疑難排解的相關資訊的說明及支援 」 網站：</span><span class="sxs-lookup"><span data-stu-id="c8159-107">See the following Knowledge Base articles on the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Help and Support Web site for information about troubleshooting DTC issues:</span></span>  
  
    -   <span data-ttu-id="c8159-108">若要疑難排解 MS DTC 防火牆問題、 位於如何[http://go.microsoft.com/fwlink/?linkid=48870](http://go.microsoft.com/fwlink/?linkid=48870)。</span><span class="sxs-lookup"><span data-stu-id="c8159-108">How To Troubleshoot MS DTC Firewall Issues, located at [http://go.microsoft.com/fwlink/?linkid=48870](http://go.microsoft.com/fwlink/?linkid=48870).</span></span>  
  
    -   <span data-ttu-id="c8159-109">如何使用 DTCTester 工具，位於[http://go.microsoft.com/fwlink/?linkid=48871](http://go.microsoft.com/fwlink/?linkid=48871)。</span><span class="sxs-lookup"><span data-stu-id="c8159-109">How To Use DTCTester Tool, located at [http://go.microsoft.com/fwlink/?linkid=48871](http://go.microsoft.com/fwlink/?linkid=48871).</span></span>  
  
    -   <span data-ttu-id="c8159-110">如果 DTC 位於防火牆後方，請參閱 「 設定[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]Distributed Transaction Coordinator (DTC) 通過防火牆的工作 」，位於[http://go.microsoft.com/fwlink/?linkid=48872](http://go.microsoft.com/fwlink/?linkid=48872)。</span><span class="sxs-lookup"><span data-stu-id="c8159-110">If DTC is behind a firewall, see "Configuring [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Distributed Transaction Coordinator (DTC) to Work Through a Firewall", located at [http://go.microsoft.com/fwlink/?linkid=48872](http://go.microsoft.com/fwlink/?linkid=48872).</span></span>  
  
2.  <span data-ttu-id="c8159-111">設定及驗證網路負載平衡上 BizTalk 接收伺服器中所述[步驟 2： 設定伺服器上的 NLB](../../adapters-and-accelerators/accelerator-swift/step-2-configuring-nlb-on-the-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="c8159-111">Configure and verify Network Load Balancing on the BizTalk receive servers as described in [Step 2: Configuring NLB on the Servers](../../adapters-and-accelerators/accelerator-swift/step-2-configuring-nlb-on-the-servers.md).</span></span>  
  
3.  <span data-ttu-id="c8159-112">安裝和設定[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]中所述[安裝和設定 BizTalk Accelerator for SWIFT 傳訊的伺服器上](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="c8159-112">Install and configure [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as described in [Installing and Configuring BizTalk Accelerator for SWIFT on Messaging Servers](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md).</span></span>  
  
 <span data-ttu-id="c8159-113">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="c8159-113">This section contains:</span></span>  
  
-   [<span data-ttu-id="c8159-114">安裝和設定 BizTalk Server 傳訊的伺服器上</span><span class="sxs-lookup"><span data-stu-id="c8159-114">Installing and Configuring BizTalk Server on the Messaging Server</span></span>](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-messaging-server.md)  
  
-   [<span data-ttu-id="c8159-115">上安裝和設定 BizTalk Accelerator for SWIFT 訊息伺服器</span><span class="sxs-lookup"><span data-stu-id="c8159-115">Installing and Configuring BizTalk Accelerator for SWIFT on Messaging Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md)