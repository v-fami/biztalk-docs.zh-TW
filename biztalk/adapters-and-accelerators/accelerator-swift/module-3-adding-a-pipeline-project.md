---
title: 模組 3： 新增管線專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tutorial, creating pipelines
- projects, pipelines
- pipelines, adding to projects
ms.assetid: 38bf1629-df29-4bea-840b-60b354b06430
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85305614cec2757a91aa006238b3eb1ca4fbdbba
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970655"
---
# <a name="module-3-adding-a-pipeline-project"></a><span data-ttu-id="637a5-102">模組 3： 新增管線專案</span><span class="sxs-lookup"><span data-stu-id="637a5-102">Module 3: Adding a Pipeline Project</span></span>
<span data-ttu-id="637a5-103">在這個模組中，您可以將新的專案新增至您的解決方案，其中包含您自訂傳送和接收管線。</span><span class="sxs-lookup"><span data-stu-id="637a5-103">In this module, you add a new project to your solution that contains your custom send and receive pipelines.</span></span> <span data-ttu-id="637a5-104">由於您正在使用 SWIFT 的訊息，也就是一般的檔案，在本質上，您無法使用隨附於 Microsoft 的預設管線[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="637a5-104">Because you are working with SWIFT messages, which are flat file in nature, you cannot use the default pipelines that are included with Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)].</span></span>  
  
 <span data-ttu-id="637a5-105">SWIFT 的訊息需要額外的層級的驗證所以 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]包含自訂解譯器 (DASM) 和 SWIFT 訊息搭配使用的組譯工具 (ASM) 元件。</span><span class="sxs-lookup"><span data-stu-id="637a5-105">SWIFT messages require additional levels of validation so Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] includes custom disassembler (DASM) and assembler (ASM) components for use with SWIFT messages.</span></span>  
  
 <span data-ttu-id="637a5-106">在本單元中，您也將新增管線專案中，加入接收和傳送管線，並使用 SWIFT DASM 和 ASM。</span><span class="sxs-lookup"><span data-stu-id="637a5-106">In this module, you also add a new pipeline project, add receive and send pipelines, and use the SWIFT DASM and ASM.</span></span>  
  
 <span data-ttu-id="637a5-107">選取 BizTalk 專案範本會公開的 BizTalk 工具，例如 BizTalk 對應工具 」，在 microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]開發環境。</span><span class="sxs-lookup"><span data-stu-id="637a5-107">Selecting the BizTalk project template exposes the BizTalk tools, such as BizTalk Mapper, within the Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] development environment.</span></span>  
  
 <span data-ttu-id="637a5-108">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="637a5-108">This section contains:</span></span>  
  
-   [<span data-ttu-id="637a5-109">課程 1：將管線專案新增至解決方案</span><span class="sxs-lookup"><span data-stu-id="637a5-109">Lesson 1: Adding a Pipelines Project to the Solution</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-1-adding-a-pipelines-project-to-the-solution.md)  
  
-   [<span data-ttu-id="637a5-110">課程 2：新增專案參考</span><span class="sxs-lookup"><span data-stu-id="637a5-110">Lesson 2: Adding Project References</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-project-references.md)  
  
-   [<span data-ttu-id="637a5-111">課程 3：新增自訂接收管線</span><span class="sxs-lookup"><span data-stu-id="637a5-111">Lesson 3: Adding a Custom Receive Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md)  
  
-   [<span data-ttu-id="637a5-112">課程 4：將 SWIFT 組合器和解譯器新增至工具箱</span><span class="sxs-lookup"><span data-stu-id="637a5-112">Lesson 4: Adding the SWIFT Assembler and Disassembler to the Toolbox</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-4-adding-the-swift-assembler-and-disassembler-to-the-toolbox.md)  
  
-   [<span data-ttu-id="637a5-113">課程 5：將 SWIFT 解譯器新增至自訂接收管線</span><span class="sxs-lookup"><span data-stu-id="637a5-113">Lesson 5: Adding the SWIFT Disassembler to a Custom Receive Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-5-adding-the-swift-disassembler-to-a-custom-receive-pipeline.md)  
  
-   [<span data-ttu-id="637a5-114">課程 6：建立自訂傳送管線</span><span class="sxs-lookup"><span data-stu-id="637a5-114">Lesson 6: Creating a Custom Send Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-6-creating-a-custom-send-pipeline.md)  
  
-   [<span data-ttu-id="637a5-115">課程 7：將 SWIFT 組合器新增至自訂傳送管線</span><span class="sxs-lookup"><span data-stu-id="637a5-115">Lesson 7: Adding the SWIFT Assembler to a Custom Send Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-7-adding-the-swift-assembler-to-a-custom-send-pipeline.md)  
  
-   [<span data-ttu-id="637a5-116">課程 8：建置和部署組件</span><span class="sxs-lookup"><span data-stu-id="637a5-116">Lesson 8: Building and Deploying the Assembly</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-8-building-and-deploying-the-assembly.md)