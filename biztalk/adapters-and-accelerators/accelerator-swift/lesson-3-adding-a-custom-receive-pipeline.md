---
title: 第 3 課： 加入自訂接收管線 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive locations, creating custom pipelines
- custom pipelines
ms.assetid: 1917b8e2-4f1c-4c20-abe4-ea18a406eeeb
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76abee50cce743dde6c62ea078f5ef9dada0c998
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210006"
---
# <a name="lesson-3-adding-a-custom-receive-pipeline"></a><span data-ttu-id="e66f0-102">第 3 課： 加入自訂接收管線</span><span class="sxs-lookup"><span data-stu-id="e66f0-102">Lesson 3: Adding a Custom Receive Pipeline</span></span>
<span data-ttu-id="e66f0-103">在這一課，您會建立自訂接收管線中使用 BizTalk 管線設計師 」。</span><span class="sxs-lookup"><span data-stu-id="e66f0-103">In this lesson you create a custom receive pipeline using BizTalk Pipeline Designer.</span></span> <span data-ttu-id="e66f0-104">自訂接收管線是配接器之前接收到訊息之後，會將訊息執行的管線[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]將其發行到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e66f0-104">A custom receive pipeline is a pipeline that is run on messages after the adapter receives the messages, but before [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] publishes them to the MessageBox database.</span></span>  
  
 <span data-ttu-id="e66f0-105">您設定自訂管線以使用 SWIFT 反組譯工具 (DASM) 元件。</span><span class="sxs-lookup"><span data-stu-id="e66f0-105">You configure the custom pipeline to use the SWIFT disassembler (DASM) component.</span></span> <span data-ttu-id="e66f0-106">SWIFT 解譯器會採用 SWIFT 格式的一般檔案和轉換或剖析，xml 表示法 SWIFT 的訊息內容的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]可取。</span><span class="sxs-lookup"><span data-stu-id="e66f0-106">The SWIFT disassembler takes a SWIFT-formatted flat file and converts, or parses, the content of the SWIFT message into an XML-based representation, which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] can consume.</span></span>  
  
 <span data-ttu-id="e66f0-107">您在上一個步驟中加入 MT103 執行階段結構描述 ([第 2 課： 加入專案參考](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-project-references.md)) 是使用來進行轉換的格式。</span><span class="sxs-lookup"><span data-stu-id="e66f0-107">The MT103 runtime schema that you added in the previous step ([Lesson 2: Adding Project References](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-project-references.md)) is the format that you use for the conversion.</span></span>  
  
### <a name="to-create-a-new-custom-receive-pipeline"></a><span data-ttu-id="e66f0-108">若要建立新的自訂接收管線</span><span class="sxs-lookup"><span data-stu-id="e66f0-108">To create a new custom receive pipeline</span></span>  
  
1.  <span data-ttu-id="e66f0-109">在 方案總管 中，以滑鼠右鍵按一下**SWIFTPipelines**專案，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="e66f0-109">In Solution Explorer, right-click the **SWIFTPipelines** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="e66f0-110">在 [加入新項目-SWIFTPipelines] 對話方塊中，按一下**管線檔案**在分類窗格中，然後選取**接收管線**從 [範本] 窗格。</span><span class="sxs-lookup"><span data-stu-id="e66f0-110">In the Add New Item-SWIFTPipelines dialog box, click **Pipeline Files** in the Categories pane, and then select **Receive Pipeline** from the Templates pane.</span></span>  
  
3.  <span data-ttu-id="e66f0-111">在**名稱**方塊中，輸入**MT103ReceivePipeline.btp**。</span><span class="sxs-lookup"><span data-stu-id="e66f0-111">In the **Name** box, type **MT103ReceivePipeline.btp**.</span></span>  
  
4.  <span data-ttu-id="e66f0-112">按一下**新增**BizTalk 管線設計師中開啟空白的管線。</span><span class="sxs-lookup"><span data-stu-id="e66f0-112">Click **Add** to open the blank pipeline in BizTalk Pipeline Designer.</span></span>  
  
 <span data-ttu-id="e66f0-113">BizTalk 管線設計師 」 中，會出現空的管線。</span><span class="sxs-lookup"><span data-stu-id="e66f0-113">An empty pipeline appears in the BizTalk Pipeline Designer.</span></span> <span data-ttu-id="e66f0-114">Visual Studio 也會加入至 方案總管新管線 SWIFTPipelines 專案底下。</span><span class="sxs-lookup"><span data-stu-id="e66f0-114">Visual Studio also adds the new pipeline to Solution Explorer under the SWIFTPipelines project.</span></span>  
  
 <span data-ttu-id="e66f0-115">繼續進行[第 4 課： 加入 [工具箱] 的 SWIFT 組合器和解譯器](../../adapters-and-accelerators/accelerator-swift/lesson-4-adding-the-swift-assembler-and-disassembler-to-the-toolbox.md)。</span><span class="sxs-lookup"><span data-stu-id="e66f0-115">Proceed to [Lesson 4: Adding the SWIFT Assembler and Disassembler to the Toolbox](../../adapters-and-accelerators/accelerator-swift/lesson-4-adding-the-swift-assembler-and-disassembler-to-the-toolbox.md).</span></span>