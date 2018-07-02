---
title: 第 5 課： 將 SWIFT 解譯器新增至自訂接收管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive pipelines, adding disassembler
- custom pipelines
- disassembler, custom pipelines
- disassembler, adding to pipelines
ms.assetid: 96e26d97-bfab-448f-b7b6-3bc2ec3ccebf
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0af7635b424a74b160991b1d6cfdeb53bfb7f23f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971295"
---
# <a name="lesson-5-adding-the-swift-disassembler-to-a-custom-receive-pipeline"></a><span data-ttu-id="51ef1-102">第 5 課： 將 SWIFT 解譯器新增至自訂接收管線</span><span class="sxs-lookup"><span data-stu-id="51ef1-102">Lesson 5: Adding the SWIFT Disassembler to a Custom Receive Pipeline</span></span>
<span data-ttu-id="51ef1-103">在這一課，您可以新增自訂的 SWIFT 解譯器 (DASM) 到您的管線。</span><span class="sxs-lookup"><span data-stu-id="51ef1-103">In this lesson, you add the custom SWIFT disassembler (DASM) to your pipeline.</span></span> <span data-ttu-id="51ef1-104">DASM 管線元件會分成個別的文件中的訊息批次中的管線元件。</span><span class="sxs-lookup"><span data-stu-id="51ef1-104">A DASM pipeline component is a pipeline component that divides messages in a batch into individual documents.</span></span>  
  
 <span data-ttu-id="51ef1-105">MicrosoftBizTalk Server 中提供的 DASM 管線元件如下：</span><span class="sxs-lookup"><span data-stu-id="51ef1-105">The DASM pipeline components provided in MicrosoftBizTalk Server are:</span></span>  
  
- <span data-ttu-id="51ef1-106">一般檔案解譯器</span><span class="sxs-lookup"><span data-stu-id="51ef1-106">Flat file disassembler</span></span>  
  
- <span data-ttu-id="51ef1-107">BizTalk Framework 解譯器</span><span class="sxs-lookup"><span data-stu-id="51ef1-107">BizTalk Framework disassembler</span></span>  
  
- <span data-ttu-id="51ef1-108">XML 解譯器</span><span class="sxs-lookup"><span data-stu-id="51ef1-108">XML disassembler</span></span>  
  
  <span data-ttu-id="51ef1-109">Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]新增額外的 SWIFT 解譯器。</span><span class="sxs-lookup"><span data-stu-id="51ef1-109">Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] adds an additional SWIFT disassembler.</span></span>  
  
### <a name="to-add-the-swift-custom-disassembler-to-your-pipeline"></a><span data-ttu-id="51ef1-110">將 SWIFT 的自訂解譯器新增至您的管線</span><span class="sxs-lookup"><span data-stu-id="51ef1-110">To add the SWIFT custom disassembler to your pipeline</span></span>  
  
1. <span data-ttu-id="51ef1-111">從 [檢視] 功能表中，按一下**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="51ef1-111">From the View menu, click **Toolbox**.</span></span>  
  
2. <span data-ttu-id="51ef1-112">從**BizTalk 管線元件 [工具箱]**，按一下**SWIFT 解譯器**將它拖曳到**放在此處**下面的方塊**解譯**階段中的圖形**BizTalk 管線設計師**。</span><span class="sxs-lookup"><span data-stu-id="51ef1-112">From the **BizTalk Pipeline Components Toolbox**, click **SWIFT Disassembler** and drag it to the **Drop Here** box below the **Disassemble** stage shape in **BizTalk Pipeline Designer**.</span></span> <span data-ttu-id="51ef1-113">離開**SWIFT 解譯器**中所選取的形狀**BizTalk 管線設計師**。</span><span class="sxs-lookup"><span data-stu-id="51ef1-113">Leave the **SWIFT Disassembler** shape selected in the **BizTalk Pipeline Designer**.</span></span>  
  
3. <span data-ttu-id="51ef1-114">在 **屬性**窗格中，選取**Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema** for **SWIFT 標頭結構描述**屬性。</span><span class="sxs-lookup"><span data-stu-id="51ef1-114">In the **Properties** pane, select **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema** for the **SWIFT Header Schema** property.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="51ef1-115">請勿混淆**SWIFT 標頭結構描述**和訊息標頭結構描述。</span><span class="sxs-lookup"><span data-stu-id="51ef1-115">Do not confuse **SWIFT Header Schema** and Message Header Schema.</span></span> <span data-ttu-id="51ef1-116">您必須設定**SWIFT 標頭結構描述**在步驟 3。</span><span class="sxs-lookup"><span data-stu-id="51ef1-116">You must set **SWIFT Header Schema** in step 3.</span></span>  
  
4. <span data-ttu-id="51ef1-117">在 [**屬性**] 窗格中，請確認**BRE 驗證**屬性設定為 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="51ef1-117">In the **Properties** pane, ensure that the **BRE Validation** property is set to **True**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="51ef1-118">稍後在本教學課程會遵循說明商務規則引擎 (BRE)。</span><span class="sxs-lookup"><span data-stu-id="51ef1-118">An explanation of the Business Rule Engine (BRE) follows later in this tutorial.</span></span>  
  
5. <span data-ttu-id="51ef1-119">在 [**屬性**] 窗格中，請確認**XML 驗證**屬性設定為 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="51ef1-119">In the **Properties** pane, ensure that the **XML Validation** property is set to **True**.</span></span>  
  
6. <span data-ttu-id="51ef1-120">在 [**屬性**] 窗格中，確定**輸入解除批次處理**屬性設定為**False**。</span><span class="sxs-lookup"><span data-stu-id="51ef1-120">In the **Properties** pane, ensure that the **Inbound Debatching** property is set to **False**.</span></span>  
  
7. <span data-ttu-id="51ef1-121">在 **檔案**功能表上，選取**全部儲存**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="51ef1-121">On the **File** menu, select **Save All** to save your changes.</span></span>  
  
   <span data-ttu-id="51ef1-122">請繼續進行[第 6 課： 建立自訂傳送管線](../../adapters-and-accelerators/accelerator-swift/lesson-6-creating-a-custom-send-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="51ef1-122">Proceed to [Lesson 6: Creating a Custom Send Pipeline](../../adapters-and-accelerators/accelerator-swift/lesson-6-creating-a-custom-send-pipeline.md).</span></span>