---
title: 端對端 Tutorial2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tutorial, about the tutorial
- tutorial
- tutorial, workflow
ms.assetid: 1aba93b9-6991-46ef-a3bc-3815a5ff473f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da298e0c69de7a351e64aa33ac48611700de3621
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980671"
---
# <a name="end-to-end-tutorial"></a><span data-ttu-id="10787-102">端對端教學課程</span><span class="sxs-lookup"><span data-stu-id="10787-102">End-to-End Tutorial</span></span>
<span data-ttu-id="10787-103">本教學課程包含詳細的步驟，說明如何建立和設定 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]解決方案。</span><span class="sxs-lookup"><span data-stu-id="10787-103">This tutorial contains detailed steps that describe how to create and set up a Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] solution.</span></span> <span data-ttu-id="10787-104">模組和所使用的 Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]建立結構描述，將協調流程和管線元件使用 A4SWIFT 的對應。</span><span class="sxs-lookup"><span data-stu-id="10787-104">The modules and lessons use Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] to create the schema, maps orchestrations, and pipeline components using A4SWIFT.</span></span>  
  
 <span data-ttu-id="10787-105">下圖顯示常見的整合引擎使用案例的端對端部署 A4SWIFT 解決方案的工作流程。</span><span class="sxs-lookup"><span data-stu-id="10787-105">The following figure shows the workflow of a common Integration Engine usage scenario for an end-to-end A4SWIFT solution.</span></span>  
  
 <span data-ttu-id="10787-106">![](../../adapters-and-accelerators/accelerator-swift/media/fsa-tut-wklw.gif "FSA_Tut_wklw")</span><span class="sxs-lookup"><span data-stu-id="10787-106">![](../../adapters-and-accelerators/accelerator-swift/media/fsa-tut-wklw.gif "FSA_Tut_wklw")</span></span>  
  
|<span data-ttu-id="10787-107">A4SWIFT 教學課程的工作流程的索引鍵</span><span class="sxs-lookup"><span data-stu-id="10787-107">A4SWIFT Tutorial Workflow Key</span></span>|  
|-----------------------------------|  
|<span data-ttu-id="10787-108">**ASM** = SWIFT 組合器</span><span class="sxs-lookup"><span data-stu-id="10787-108">**ASM** = SWIFT Assembler</span></span>|  
|<span data-ttu-id="10787-109">**DASM** = SWIFT 解譯器</span><span class="sxs-lookup"><span data-stu-id="10787-109">**DASM** = SWIFT Disassembler</span></span>|  
|<span data-ttu-id="10787-110">**MTxxx** = A4SWIFT 訊息類型</span><span class="sxs-lookup"><span data-stu-id="10787-110">**MTxxx** = A4SWIFT Message type</span></span>|  
|<span data-ttu-id="10787-111">**SIPN** = SWIFT 安全 IP 網路</span><span class="sxs-lookup"><span data-stu-id="10787-111">**SIPN** = SWIFT Secure IP Network</span></span>|  
  
 <span data-ttu-id="10787-112">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="10787-112">This section contains:</span></span>  
  
-   [<span data-ttu-id="10787-113">模組 1：建立 SWIFT 解決方案</span><span class="sxs-lookup"><span data-stu-id="10787-113">Module 1: Creating a SWIFT Solution</span></span>](../../adapters-and-accelerators/accelerator-swift/module-1-creating-a-swift-solution.md)  
  
-   [<span data-ttu-id="10787-114">模組 2：新增結構描述專案</span><span class="sxs-lookup"><span data-stu-id="10787-114">Module 2: Adding a New Schemas Project</span></span>](../../adapters-and-accelerators/accelerator-swift/module-2-adding-a-new-schemas-project.md)  
  
-   [<span data-ttu-id="10787-115">模組 3：新增管線專案</span><span class="sxs-lookup"><span data-stu-id="10787-115">Module 3: Adding a Pipeline Project</span></span>](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md)  
  
-   [<span data-ttu-id="10787-116">模組 4：新增 XML 接收位置和一般檔案傳送埠</span><span class="sxs-lookup"><span data-stu-id="10787-116">Module 4: Adding an XML Receive Location and Flat File Send Port</span></span>](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md)  
  
-   [<span data-ttu-id="10787-117">模組 5：新增一般檔案接收位置和 XML 傳送埠</span><span class="sxs-lookup"><span data-stu-id="10787-117">Module 5: Adding a Flat File Receive Location and XML Send Port</span></span>](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md)  
  
-   [<span data-ttu-id="10787-118">模組 6：部署商務規則</span><span class="sxs-lookup"><span data-stu-id="10787-118">Module 6: Deploying the Business Rules</span></span>](../../adapters-and-accelerators/accelerator-swift/module-6-deploying-the-business-rules.md)  
  
-   [<span data-ttu-id="10787-119">模組 7：測試有效一般檔案執行個體</span><span class="sxs-lookup"><span data-stu-id="10787-119">Module 7: Testing a Valid Flat File Instance</span></span>](../../adapters-and-accelerators/accelerator-swift/module-7-testing-a-valid-flat-file-instance.md)