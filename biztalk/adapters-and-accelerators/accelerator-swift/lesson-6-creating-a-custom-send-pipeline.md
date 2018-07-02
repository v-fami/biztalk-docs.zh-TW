---
title: 第 6 課： 建立自訂傳送管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom pipelines
- send pipelines, custom pipelines
ms.assetid: 73a3a546-1e43-4b93-87d3-9bfb32685a57
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12afba9368554dc85cf57658f674a088db7580d2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973719"
---
# <a name="lesson-6-creating-a-custom-send-pipeline"></a><span data-ttu-id="b5860-102">第 6 課： 建立自訂傳送管線</span><span class="sxs-lookup"><span data-stu-id="b5860-102">Lesson 6: Creating a Custom Send Pipeline</span></span>
<span data-ttu-id="b5860-103">在這一課，您可以建立自訂傳送管線，使用 BizTalk 管線設計師。</span><span class="sxs-lookup"><span data-stu-id="b5860-103">In this lesson, you create a custom send pipeline using BizTalk Pipeline Designer.</span></span> <span data-ttu-id="b5860-104">傳送管線是您在之前的訊息執行的管線[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]傳送訊息至其目的地。</span><span class="sxs-lookup"><span data-stu-id="b5860-104">A send pipeline is a pipeline you run on messages before [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] sends the messages to their destination.</span></span>  
  
 <span data-ttu-id="b5860-105">您設定自訂的管線，以使用 SWIFT 組合器 」 (ASM) 元件。</span><span class="sxs-lookup"><span data-stu-id="b5860-105">You configure the custom pipeline to use the SWIFT assembler (ASM) component.</span></span> <span data-ttu-id="b5860-106">ASM 採用 XML 格式的訊息，並將轉換或將內容序列化至 SWIFT 的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="b5860-106">The ASM takes an XML-formatted message and converts or serializes the content into a SWIFT flat file.</span></span> <span data-ttu-id="b5860-107">這項轉換取決於您在中建立的 MT103 結構描述[第 3 課： 加入自訂接收管線](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="b5860-107">This conversion is based upon the MT103 schema you created in [Lesson 3: Adding a Custom Receive Pipeline](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md).</span></span>  
  
### <a name="to-create-a-custom-send-pipeline"></a><span data-ttu-id="b5860-108">若要建立自訂傳送管線</span><span class="sxs-lookup"><span data-stu-id="b5860-108">To create a custom send pipeline</span></span>  
  
1. <span data-ttu-id="b5860-109">在 [方案總管] 中，以滑鼠右鍵按一下**SWIFTPipelines**專案，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="b5860-109">In Solution Explorer, right-click the **SWIFTPipelines** project, point to **Add**, and then click **New Item**.</span></span>  
  
2. <span data-ttu-id="b5860-110">在 [加入新項目-SWIFTPipelines] 對話方塊中，確認**管線檔案**已選取在 [分類] 窗格中，然後選取**傳送管線**從 [範本] 窗格。</span><span class="sxs-lookup"><span data-stu-id="b5860-110">In the Add New Item-SWIFTPipelines dialog box, verify that **Pipeline Files** is selected in the Categories pane, and then select **Send Pipeline** from the Templates pane.</span></span>  
  
3. <span data-ttu-id="b5860-111">在 **名稱**方塊中，輸入**MT103SendPipeline.btp**。</span><span class="sxs-lookup"><span data-stu-id="b5860-111">In the **Name** box, type **MT103SendPipeline.btp**.</span></span>  
  
4. <span data-ttu-id="b5860-112">按一下 **新增**BizTalk 管線設計師中開啟空白的管線。</span><span class="sxs-lookup"><span data-stu-id="b5860-112">Click **Add** to open the blank pipeline in BizTalk Pipeline Designer.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b5860-113">BizTalk 管線設計師 」 中，會出現空的管線。</span><span class="sxs-lookup"><span data-stu-id="b5860-113">An empty pipeline appears in the BizTalk Pipeline Designer.</span></span> [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="b5860-114"> 將方案總管 中的新管線 SWIFTPipelines 專案底下。</span><span class="sxs-lookup"><span data-stu-id="b5860-114"> adds the new pipeline to Solution Explorer under the SWIFTPipelines project.</span></span>  
  
   <span data-ttu-id="b5860-115">請繼續進行[第 7 課： 將 SWIFT 組合器新增至自訂傳送管線](../../adapters-and-accelerators/accelerator-swift/lesson-7-adding-the-swift-assembler-to-a-custom-send-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="b5860-115">Proceed to [Lesson 7: Adding the SWIFT Assembler to a Custom Send Pipeline](../../adapters-and-accelerators/accelerator-swift/lesson-7-adding-the-swift-assembler-to-a-custom-send-pipeline.md).</span></span>