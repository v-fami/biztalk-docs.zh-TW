---
title: "操作工作 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing
- BizTalk Accelerator for SWIFT, administering
- BizTalk Accelerator for SWIFT, managing
- administering
ms.assetid: 555335a0-5a85-4498-b34f-97bb508ea5b1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1bc5b778f3bca84422ca961da4a358d2aa0f7f39
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operational-tasks"></a><span data-ttu-id="2d3c0-102">操作工作</span><span class="sxs-lookup"><span data-stu-id="2d3c0-102">Operational tasks</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="2d3c0-103">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]包含一個或多部伺服器和一系列工具企業應用程式整合 (EAI)，自動化財務商務程序，並加速使用 SWIFT FIN 標準的訊息交換。</span><span class="sxs-lookup"><span data-stu-id="2d3c0-103"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] encompasses one or more servers and a series of tools for enterprise application integration (EAI), automating financial business processes, and facilitating message exchange using the SWIFT FIN standard.</span></span>  
  
 <span data-ttu-id="2d3c0-104">作業會包括管理工作的[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="2d3c0-104">Operations include the administration and management of [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] applications.</span></span> <span data-ttu-id="2d3c0-105">A4SWIFT 會使用下列工具和主控台執行這些作業：</span><span class="sxs-lookup"><span data-stu-id="2d3c0-105">A4SWIFT uses the following tools and consoles to perform these operations:</span></span>  
  
-   <span data-ttu-id="2d3c0-106">**BizTalk Server 管理主控台。**</span><span class="sxs-lookup"><span data-stu-id="2d3c0-106">**BizTalk Server Administration Console.**</span></span> <span data-ttu-id="2d3c0-107">您可以使用此工具來管理 BizTalk 群組，包括所有的 BizTalk 資料庫來追蹤商務程序的效能。</span><span class="sxs-lookup"><span data-stu-id="2d3c0-107">Use this tool to manage the BizTalk group, including all BizTalk databases, to track the performance of business processes.</span></span>  
  
-   <span data-ttu-id="2d3c0-108">**商務活動監控 (BAM) 架構。**</span><span class="sxs-lookup"><span data-stu-id="2d3c0-108">**Business Activity Monitoring (BAM) Framework.**</span></span> <span data-ttu-id="2d3c0-109">使用此工具來追蹤資料的項目和商務交易期間所收集的商務里程碑。</span><span class="sxs-lookup"><span data-stu-id="2d3c0-109">Use this tool to track data items and business milestones collected during business transactions.</span></span>  
  
 <span data-ttu-id="2d3c0-110">SWIFT 解譯器會增強 （裝飾） A4SWIFT 與它所處理的訊息升級屬性。</span><span class="sxs-lookup"><span data-stu-id="2d3c0-110">The SWIFT disassembler enhances (decorates) messages that it processes with A4SWIFT promoted properties.</span></span> <span data-ttu-id="2d3c0-111">因此，HAT 及 BAM 查詢運算式選擇性地包含這些屬性進行篩選。</span><span class="sxs-lookup"><span data-stu-id="2d3c0-111">As such, HAT and BAM query expressions optionally include these properties for filtering.</span></span> <span data-ttu-id="2d3c0-112">如需 A4SWIFT 升級屬性的清單，請參閱[A4SWIFT_ * 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2d3c0-112">For a list of A4SWIFT promoted properties, see [A4SWIFT_* Promoted Properties](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md).</span></span>  
  
 <span data-ttu-id="2d3c0-113">如需有關資訊[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]作業，請參閱中的作業 」 一節[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="2d3c0-113">For information about [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] operations, see the Operations section in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
 <span data-ttu-id="2d3c0-114">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="2d3c0-114">This section contains:</span></span>  
  
-   [<span data-ttu-id="2d3c0-115">修復訊息並提交新的訊息</span><span class="sxs-lookup"><span data-stu-id="2d3c0-115">Repairing Messages and Submitting New Messages</span></span>](../../adapters-and-accelerators/accelerator-swift/repairing-messages-and-submitting-new-messages.md)  
  
-   [<span data-ttu-id="2d3c0-116">管理作業</span><span class="sxs-lookup"><span data-stu-id="2d3c0-116">Administrative Operations</span></span>](../../adapters-and-accelerators/accelerator-swift/administrative-operations.md)