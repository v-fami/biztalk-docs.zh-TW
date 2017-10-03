---
title: "端對端課程 2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorial, about the tutorial
- tutorial
- tutorial, workflow
ms.assetid: 1aba93b9-6991-46ef-a3bc-3815a5ff473f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c4022595ed05cb779d11e09d66080024ac76654
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="end-to-end-tutorial"></a><span data-ttu-id="a5032-102">端對端教學課程</span><span class="sxs-lookup"><span data-stu-id="a5032-102">End-to-End Tutorial</span></span>
<span data-ttu-id="a5032-103">本教學課程包含詳細的步驟描述如何建立並設定[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]方案。</span><span class="sxs-lookup"><span data-stu-id="a5032-103">This tutorial contains detailed steps that describe how to create and set up a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] solution.</span></span> <span data-ttu-id="a5032-104">模組和課程使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]建立結構描述，將協調流程和管線元件使用 A4SWIFT 的對應。</span><span class="sxs-lookup"><span data-stu-id="a5032-104">The modules and lessons use [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] to create the schema, maps orchestrations, and pipeline components using A4SWIFT.</span></span>  
  
 <span data-ttu-id="a5032-105">如下圖所示的端對端 A4SWIFT 解決方案的常見整合引擎使用案例的工作流程。</span><span class="sxs-lookup"><span data-stu-id="a5032-105">The following figure shows the workflow of a common Integration Engine usage scenario for an end-to-end A4SWIFT solution.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-tut-wklw.gif "FSA_Tut_wklw")  
  
|<span data-ttu-id="a5032-106">A4SWIFT 教學課程的工作流程的機碼</span><span class="sxs-lookup"><span data-stu-id="a5032-106">A4SWIFT Tutorial Workflow Key</span></span>|  
|-----------------------------------|  
|<span data-ttu-id="a5032-107">**ASM** = SWIFT 組譯工具</span><span class="sxs-lookup"><span data-stu-id="a5032-107">**ASM** = SWIFT Assembler</span></span>|  
|<span data-ttu-id="a5032-108">**DASM** = SWIFT 反組譯工具</span><span class="sxs-lookup"><span data-stu-id="a5032-108">**DASM** = SWIFT Disassembler</span></span>|  
|<span data-ttu-id="a5032-109">**MTxxx** = A4SWIFT 訊息類型</span><span class="sxs-lookup"><span data-stu-id="a5032-109">**MTxxx** = A4SWIFT Message type</span></span>|  
|<span data-ttu-id="a5032-110">**SIPN** = SWIFT 安全 IP 網路</span><span class="sxs-lookup"><span data-stu-id="a5032-110">**SIPN** = SWIFT Secure IP Network</span></span>|  
  
 <span data-ttu-id="a5032-111">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="a5032-111">This section contains:</span></span>  
  
-   [<span data-ttu-id="a5032-112">模組 1： 建立 SWIFT 方案</span><span class="sxs-lookup"><span data-stu-id="a5032-112">Module 1: Creating a SWIFT Solution</span></span>](../../adapters-and-accelerators/accelerator-swift/module-1-creating-a-swift-solution.md)  
  
-   [<span data-ttu-id="a5032-113">模組 2： 加入新的結構描述專案</span><span class="sxs-lookup"><span data-stu-id="a5032-113">Module 2: Adding a New Schemas Project</span></span>](../../adapters-and-accelerators/accelerator-swift/module-2-adding-a-new-schemas-project.md)  
  
-   [<span data-ttu-id="a5032-114">模組 3： 新增管線專案</span><span class="sxs-lookup"><span data-stu-id="a5032-114">Module 3: Adding a Pipeline Project</span></span>](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md)  
  
-   [<span data-ttu-id="a5032-115">模組 4： 加入 XML 接收位置和一般檔案傳送埠</span><span class="sxs-lookup"><span data-stu-id="a5032-115">Module 4: Adding an XML Receive Location and Flat File Send Port</span></span>](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md)  
  
-   [<span data-ttu-id="a5032-116">模組 5： 加入一般檔案接收位置和 XML 傳送埠</span><span class="sxs-lookup"><span data-stu-id="a5032-116">Module 5: Adding a Flat File Receive Location and XML Send Port</span></span>](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md)  
  
-   [<span data-ttu-id="a5032-117">模組 6： 部署商務規則</span><span class="sxs-lookup"><span data-stu-id="a5032-117">Module 6: Deploying the Business Rules</span></span>](../../adapters-and-accelerators/accelerator-swift/module-6-deploying-the-business-rules.md)  
  
-   [<span data-ttu-id="a5032-118">模組 7： 測試有效的一般檔案執行個體</span><span class="sxs-lookup"><span data-stu-id="a5032-118">Module 7: Testing a Valid Flat File Instance</span></span>](../../adapters-and-accelerators/accelerator-swift/module-7-testing-a-valid-flat-file-instance.md)