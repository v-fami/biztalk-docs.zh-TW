---
title: 建立 FRR 傳送管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FRR, creating send pipelines
- creating, send pipelines
- send pipelines, creating
ms.assetid: c6cd2047-ea53-425f-80cc-b02a1deb5292
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d16003e489944016a7b840b870d33d8ebcf671d5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005743"
---
# <a name="creating-the-frr-send-pipeline"></a><span data-ttu-id="36162-102">建立 FRR 傳送管線</span><span class="sxs-lookup"><span data-stu-id="36162-102">Creating the FRR Send Pipeline</span></span>
<span data-ttu-id="36162-103">若要執行 FIN 回應對帳，您需要建立包含 SWIFTAsmFrrMQSeriesHelper 管線元件，除了 SWIFT 組合器的傳送管線。</span><span class="sxs-lookup"><span data-stu-id="36162-103">To perform FIN Response Reconciliation, you need to create a send pipeline that contains the SWIFTAsmFrrMQSeriesHelper pipeline component, in addition to the SWIFT assembler.</span></span>  

 <span data-ttu-id="36162-104">**摘要**</span><span class="sxs-lookup"><span data-stu-id="36162-104">**Summary**</span></span>  

 <span data-ttu-id="36162-105">建立傳送管線的下列階段：</span><span class="sxs-lookup"><span data-stu-id="36162-105">Create a send pipeline with the following stages:</span></span>  

|<span data-ttu-id="36162-106">階段</span><span class="sxs-lookup"><span data-stu-id="36162-106">Stage</span></span>|<span data-ttu-id="36162-107">元件</span><span class="sxs-lookup"><span data-stu-id="36162-107">Component</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="36162-108">組合階段</span><span class="sxs-lookup"><span data-stu-id="36162-108">Assemble stage</span></span>|<span data-ttu-id="36162-109">SWIFT 組合器</span><span class="sxs-lookup"><span data-stu-id="36162-109">SWIFT assembler</span></span>|  
|<span data-ttu-id="36162-110">編碼階段</span><span class="sxs-lookup"><span data-stu-id="36162-110">Encode stage</span></span>|<span data-ttu-id="36162-111">SWIFT 的 Frr MQSeries 傳送元件</span><span class="sxs-lookup"><span data-stu-id="36162-111">SWIFT Frr MQSeries Send Component</span></span>|  

### <a name="to-create-a-custom-send-pipeline-for-frr"></a><span data-ttu-id="36162-112">建立 FRR 自訂傳送管線</span><span class="sxs-lookup"><span data-stu-id="36162-112">To create a custom send pipeline for FRR</span></span>  

1. <span data-ttu-id="36162-113">在 Visual Studio 的方案總管中以滑鼠右鍵按一下管線專案，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="36162-113">In Solution Explorer of Visual Studio, right-click your pipeline project, point to **Add**, and then click **New Item**.</span></span>  

2. <span data-ttu-id="36162-114">在 [加入新項目] 對話方塊中，選取**傳送管線**從 [範本] 窗格。</span><span class="sxs-lookup"><span data-stu-id="36162-114">In the Add New Item dialog box, select **Send Pipeline** from the Templates pane.</span></span>  

3. <span data-ttu-id="36162-115">在 **名稱**方塊中，輸入您的接收管線的名稱，例如**FRRSendPipeline.btp**。</span><span class="sxs-lookup"><span data-stu-id="36162-115">In the **Name** box, type a name for your receive pipeline, such as **FRRSendPipeline.btp**.</span></span> <span data-ttu-id="36162-116">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="36162-116">Click **Add**.</span></span>  

4. <span data-ttu-id="36162-117">在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下**檢視**，然後**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="36162-117">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **View** and then **Toolbox**.</span></span>  

5. <span data-ttu-id="36162-118">BizTalk 管線元件 [工具箱] 拖曳**SWIFT 組合器**要**放置到此處**在下列方塊**組合**階段中的圖形**BizTalk 管線設計工具**。</span><span class="sxs-lookup"><span data-stu-id="36162-118">From the BizTalk Pipeline Components Toolbox, drag **SWIFT Assembler** to the **Drop Here** box below the **Assemble** stage shape in **BizTalk Pipeline Designer**.</span></span>  

6. <span data-ttu-id="36162-119">BizTalk 管線元件 [工具箱] 拖曳**SWIFT Frr MQSeries 傳送元件**要**放置到此處**在下列方塊**編碼**階段中的圖形**BizTalk 管線設計師**。</span><span class="sxs-lookup"><span data-stu-id="36162-119">From the BizTalk Pipeline Components Toolbox, drag **SWIFT Frr MQSeries Send Component** to the **Drop Here** box below the **Encode** stage shape in **BizTalk Pipeline Designer**.</span></span>  

7. <span data-ttu-id="36162-120">在 [BizTalk 總管] 中，以滑鼠右鍵按一下管線專案中，按一下**Undeploy**，然後按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="36162-120">In BizTalk Explorer, right-click your pipeline project, click **Undeploy**, and then click **Yes**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="36162-121">解除部署，然後重新部署管線專案之後，您必須重設任何傳送埠或接收位置，其使用先前部署的專案中的管線。</span><span class="sxs-lookup"><span data-stu-id="36162-121">After undeploying and then redeploying your pipeline project, you must reset any send ports or receive locations that use pipelines in the previously deployed project.</span></span>  

8. <span data-ttu-id="36162-122">在 [方案總管] 中，以滑鼠右鍵按一下您管線的專案，然後**建置**。</span><span class="sxs-lookup"><span data-stu-id="36162-122">In Solution Explorer, right-click your pipeline project, and then click **Build**.</span></span>  

9. <span data-ttu-id="36162-123">建置成功之後，以滑鼠右鍵按一下您管線的專案，然後**部署**。</span><span class="sxs-lookup"><span data-stu-id="36162-123">After the build has succeeded, right-click your pipeline project, and then click **Deploy**.</span></span>
