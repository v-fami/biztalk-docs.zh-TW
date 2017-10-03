---
title: "管理和執行時間工具 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTAHL7, tools
- Configuration Explorer
- Windows performance monitors
- BizTalk Explorer
- Business Rule Engine (BRE)
- HAT
- analysis tools
- Health and Activity Tracking (HAT)
- administrative tools
- runtime tools
ms.assetid: 6dad8451-0f77-4d62-bea5-86182c44216a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af9663c5b199c8f0b77da5a0207f370a515ad030
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="administration-and-run-time-tools"></a><span data-ttu-id="0c42a-102">管理和執行的階段工具</span><span class="sxs-lookup"><span data-stu-id="0c42a-102">Administration and Run Time Tools</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="0c42a-103">[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]和[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 提供一組工具來執行系統管理和執行階段工作，例如部署、 設定管理、 管理、 商務規則管理及監視。</span><span class="sxs-lookup"><span data-stu-id="0c42a-103"> [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] and [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) provides a set of tools for performing administrative and run time tasks, such as deployment, configuration management, administration, business-rule management, and monitoring.</span></span> <span data-ttu-id="0c42a-104">如需有關[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]工具，請參閱[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="0c42a-104">For more information about [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] tools, see [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="biztalk-explorer"></a><span data-ttu-id="0c42a-105">BizTalk Explorer (BizTalk 總管)</span><span class="sxs-lookup"><span data-stu-id="0c42a-105">BizTalk Explorer</span></span>  
 <span data-ttu-id="0c42a-106">「BizTalk 總管」可以設定和管理專案、合作對象及協調流程。</span><span class="sxs-lookup"><span data-stu-id="0c42a-106">You use BizTalk Explorer to configure and manage projects, parties, and orchestrations.</span></span> <span data-ttu-id="0c42a-107">BizTalk 總管 中顯示組態資料庫 （也稱為 「 BizTalk 管理資料庫），的內容顯示項目，例如組件、 連接埠和合作對象 （在階層的樹狀目錄中）。</span><span class="sxs-lookup"><span data-stu-id="0c42a-107">BizTalk Explorer displays the contents of the Configuration database (also known as the BizTalk Management database), showing items such as assemblies, ports, and parties (in a hierarchical tree).</span></span>  
  
## <a name="btahl7-configuration-explorer"></a><span data-ttu-id="0c42a-108">BTAHL7 組態總管</span><span class="sxs-lookup"><span data-stu-id="0c42a-108">BTAHL7 Configuration Explorer</span></span>  
 <span data-ttu-id="0c42a-109">與[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管 中，您可以檢閱並設定批次定義、 通知組態和記錄資料存放區設定。</span><span class="sxs-lookup"><span data-stu-id="0c42a-109">With [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer, you can review and configure batch definitions, acknowledgment configurations, and logging data store settings.</span></span> <span data-ttu-id="0c42a-110">使用[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管 中，您可以 initiative 啟用、 要求和處理合作對象層級的批次終止。</span><span class="sxs-lookup"><span data-stu-id="0c42a-110">Using [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer, you can initiative activation, request, and termination of batch processing at the party level.</span></span>  
  
## <a name="business-rule-engine"></a><span data-ttu-id="0c42a-111">商務規則引擎</span><span class="sxs-lookup"><span data-stu-id="0c42a-111">Business Rule Engine</span></span>  
 <span data-ttu-id="0c42a-112">「BizTalk 商務規則引擎」(BRE) 是執行階段推論引擎 (Inference Engine)，可以根據事實評估規則，然後依照評估結果初始化動作。</span><span class="sxs-lookup"><span data-stu-id="0c42a-112">The BizTalk Business Rule Engine (BRE) is a run-time inference engine that you can use to evaluate rules against facts and initiate actions based on the results of the evaluation.</span></span>  
  
## <a name="windows-performance-monitors"></a><span data-ttu-id="0c42a-113">Windows 效能監視器</span><span class="sxs-lookup"><span data-stu-id="0c42a-113">Windows Performance Monitors</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="0c42a-114">支援使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]效能監視的連線狀態以及整個 （處理和已拒絕）。</span><span class="sxs-lookup"><span data-stu-id="0c42a-114"> supports the use of [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] performance monitors for connection status and throughout (both processes and rejected).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c42a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c42a-115">See Also</span></span>  
 <span data-ttu-id="0c42a-116">[工具和功能](../../adapters-and-accelerators/accelerator-hl7/tools-and-features.md) </span><span class="sxs-lookup"><span data-stu-id="0c42a-116">[Tools and Features](../../adapters-and-accelerators/accelerator-hl7/tools-and-features.md) </span></span>  
 <span data-ttu-id="0c42a-117">[設計階段工具](../../adapters-and-accelerators/accelerator-hl7/design-time-tools.md) </span><span class="sxs-lookup"><span data-stu-id="0c42a-117">[Design Time Tools](../../adapters-and-accelerators/accelerator-hl7/design-time-tools.md) </span></span>  
 [<span data-ttu-id="0c42a-118">分析工具</span><span class="sxs-lookup"><span data-stu-id="0c42a-118">Analysis Tools</span></span>](../../adapters-and-accelerators/accelerator-hl7/analysis-tools2.md)