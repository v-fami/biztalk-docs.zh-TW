---
title: 模組 3： 新增管線專案 |Microsoft 文件
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
ms.openlocfilehash: 2d14e0f334514fd35a7f8de963f7fb457e3fbbd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22208158"
---
# <a name="module-3-adding-a-pipeline-project"></a><span data-ttu-id="1dbc1-102">模組 3： 新增管線專案</span><span class="sxs-lookup"><span data-stu-id="1dbc1-102">Module 3: Adding a Pipeline Project</span></span>
<span data-ttu-id="1dbc1-103">在此模組中，您可以將新的專案加入至您的方案，其中包含自訂的傳送與接收管線。</span><span class="sxs-lookup"><span data-stu-id="1dbc1-103">In this module, you add a new project to your solution that contains your custom send and receive pipelines.</span></span> <span data-ttu-id="1dbc1-104">由於您正在使用 SWIFT 訊息，也就是一般檔案在本質上，您無法使用隨附的預設管線[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1dbc1-104">Because you are working with SWIFT messages, which are flat file in nature, you cannot use the default pipelines that are included with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)].</span></span>  
  
 <span data-ttu-id="1dbc1-105">SWIFT 的訊息需要其他層級的驗證所以[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]包括自訂解譯器 (DASM) 和 SWIFT 訊息搭配使用的組譯工具 (ASM) 元件。</span><span class="sxs-lookup"><span data-stu-id="1dbc1-105">SWIFT messages require additional levels of validation so [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] includes custom disassembler (DASM) and assembler (ASM) components for use with SWIFT messages.</span></span>  
  
 <span data-ttu-id="1dbc1-106">在此模組中，您也將新的管線專案中，加入接收和傳送管線，而使用 SWIFT DASM 和 ASM。</span><span class="sxs-lookup"><span data-stu-id="1dbc1-106">In this module, you also add a new pipeline project, add receive and send pipelines, and use the SWIFT DASM and ASM.</span></span>  
  
 <span data-ttu-id="1dbc1-107">選取 BizTalk 專案範本內公開 BizTalk 工具的 BizTalk 對應工具，例如[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]開發環境。</span><span class="sxs-lookup"><span data-stu-id="1dbc1-107">Selecting the BizTalk project template exposes the BizTalk tools, such as BizTalk Mapper, within the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] development environment.</span></span>  
  
 <span data-ttu-id="1dbc1-108">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="1dbc1-108">This section contains:</span></span>  
  
-   [<span data-ttu-id="1dbc1-109">第 1 課： 加入方案中的管線專案</span><span class="sxs-lookup"><span data-stu-id="1dbc1-109">Lesson 1: Adding a Pipelines Project to the Solution</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-1-adding-a-pipelines-project-to-the-solution.md)  
  
-   [<span data-ttu-id="1dbc1-110">第 2 課： 加入專案參考</span><span class="sxs-lookup"><span data-stu-id="1dbc1-110">Lesson 2: Adding Project References</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-project-references.md)  
  
-   [<span data-ttu-id="1dbc1-111">第 3 課： 加入自訂接收管線</span><span class="sxs-lookup"><span data-stu-id="1dbc1-111">Lesson 3: Adding a Custom Receive Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md)  
  
-   [<span data-ttu-id="1dbc1-112">第 4 課： SWIFT 組合器和解譯器新增至工具箱</span><span class="sxs-lookup"><span data-stu-id="1dbc1-112">Lesson 4: Adding the SWIFT Assembler and Disassembler to the Toolbox</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-4-adding-the-swift-assembler-and-disassembler-to-the-toolbox.md)  
  
-   [<span data-ttu-id="1dbc1-113">第 5 課： 加入自訂接收管線 SWIFT 反組譯工具</span><span class="sxs-lookup"><span data-stu-id="1dbc1-113">Lesson 5: Adding the SWIFT Disassembler to a Custom Receive Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-5-adding-the-swift-disassembler-to-a-custom-receive-pipeline.md)  
  
-   [<span data-ttu-id="1dbc1-114">第 6 課： 建立自訂傳送管線</span><span class="sxs-lookup"><span data-stu-id="1dbc1-114">Lesson 6: Creating a Custom Send Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-6-creating-a-custom-send-pipeline.md)  
  
-   [<span data-ttu-id="1dbc1-115">第 7 課： 加入自訂傳送管線 SWIFT 組譯工具</span><span class="sxs-lookup"><span data-stu-id="1dbc1-115">Lesson 7: Adding the SWIFT Assembler to a Custom Send Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-7-adding-the-swift-assembler-to-a-custom-send-pipeline.md)  
  
-   [<span data-ttu-id="1dbc1-116">第 8 課： 建立和部署組件</span><span class="sxs-lookup"><span data-stu-id="1dbc1-116">Lesson 8: Building and Deploying the Assembly</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-8-building-and-deploying-the-assembly.md)