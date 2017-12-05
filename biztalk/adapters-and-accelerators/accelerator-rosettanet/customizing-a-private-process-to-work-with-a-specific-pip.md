---
title: "自訂私用程序以處理特定 PIP |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private processes, PIPs
- private processes, customizing
- developing, private processes
- PIPs, private processes
- customizing private processes
ms.assetid: 88494e87-25a0-4c94-9396-61a0e07964aa
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f84cd2de6d5f79062592dbf71947587b6d7a6ff0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="customizing-a-private-process-to-work-with-a-specific-pip"></a><span data-ttu-id="7a138-102">自訂私用程序以處理特定 PIP</span><span class="sxs-lookup"><span data-stu-id="7a138-102">Customizing a Private Process to Work with a Specific PIP</span></span>
<span data-ttu-id="7a138-103">您可以建立一個篩選條件運算式，決定回應者私用程序協調流程是否處理特定夥伴介面程序 (PIP) 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7a138-103">You can create a filter expression that will cause a responder private-process orchestration to process or not process instances of a specific Partner Interface Process (PIP).</span></span> <span data-ttu-id="7a138-104">這可提供您建立自訂私用程序來接收和處理某些 PIP 執行個體，以及使用預設私用程序來處理所有其他 PIP 執行個體的彈性。</span><span class="sxs-lookup"><span data-stu-id="7a138-104">This gives you the flexibility of creating a custom private process to receive and process some PIP instances, and using the default private process to process all other PIP instances.</span></span>  
  
 <span data-ttu-id="7a138-105">如果要建立自訂私用程序來處理特定 PIP 或多個特定 PIP，您可為私用程序協調流程的接收圖形建立篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="7a138-105">To create a custom private process to work with a specific PIP or multiple specific PIPs, you create a filter expression for the receive shape of the private-process orchestration.</span></span> <span data-ttu-id="7a138-106">一個範例就是 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK 中的 PIP3A4PrivateResponder.odx 協調流程，</span><span class="sxs-lookup"><span data-stu-id="7a138-106">An example is the PIP3A4PrivateResponder.odx orchestration in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK.</span></span> <span data-ttu-id="7a138-107">它位於\<*磁碟機*\>: \Program Files\BizTalk\<版本\>Accelerator for RosettaNet\SDK\PIP3A4Process 使用 Business Rules\PIP3A4PrivateResponder。</span><span class="sxs-lookup"><span data-stu-id="7a138-107">It is located at \<*drive*\>:\Program Files\BizTalk \<version\> Accelerator for RosettaNet\SDK\PIP3A4Process Using Business Rules\PIP3A4PrivateResponder.</span></span>  
  
 <span data-ttu-id="7a138-108">除了建立只處理特定 PIP 執行個體的私用程序之外，您還必須自訂預設的 BTARN 私用程序，這樣 BTARN 私用程序才不會處理該 PIP 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7a138-108">Besides creating a private process that process only instances of a specific PIP, you must customize the default BTARN private process so that it will not process instances for that PIP.</span></span>  
  
### <a name="to-customize-a-responder-private-process-to-work-with-a-specific-pip"></a><span data-ttu-id="7a138-109">自訂回應者私用程序以處理特定 PIP</span><span class="sxs-lookup"><span data-stu-id="7a138-109">To customize a responder private process to work with a specific PIP</span></span>  
  
1.  <span data-ttu-id="7a138-110">在 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 中，建立自訂的回應者私用程序協調流程，以處理特定的 PIP。</span><span class="sxs-lookup"><span data-stu-id="7a138-110">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], create a custom responder private-process orchestration for working with a specific PIP.</span></span> <span data-ttu-id="7a138-111">您可以根據預設的 BTARN 回應者私用程序協調流程來建立協調流程。</span><span class="sxs-lookup"><span data-stu-id="7a138-111">You can base the orchestration on the default BTARN responder private-process orchestration.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a138-112">您可在 BTARN SDK 中找到預設的回應者私用程序協調流程，其名稱為 PrivateResponder.odx。</span><span class="sxs-lookup"><span data-stu-id="7a138-112">You can find the default responder private-process orchestration, named PrivateResponder.odx, in the BTARN SDK.</span></span> <span data-ttu-id="7a138-113">它位於*\<磁碟機\>*: \Program Files\BizTalk\<版本\>Accelerator for RosettaNet\SDK\PrivateResponder。</span><span class="sxs-lookup"><span data-stu-id="7a138-113">It is located at *\<drive\>*:\Program Files\BizTalk \<version\> Accelerator for RosettaNet\SDK\PrivateResponder.</span></span>  
  
2.  <span data-ttu-id="7a138-114">新增自訂協調流程到您的 BizTalk 專案中。</span><span class="sxs-lookup"><span data-stu-id="7a138-114">Add the custom orchestration to your BizTalk project.</span></span> <span data-ttu-id="7a138-115">請確定您的專案是參考到 Microsoft.Solutions.BTARN.GlobalSchemas.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="7a138-115">Make sure that your project has a reference to the Microsoft.Solutions.BTARN.GlobalSchemas.dll file.</span></span>  
  
3.  <span data-ttu-id="7a138-116">開啟協調流程設計師中的自訂協調流程。</span><span class="sxs-lookup"><span data-stu-id="7a138-116">Open the custom orchestration in Orchestration Designer.</span></span>  
  
4.  <span data-ttu-id="7a138-117">以滑鼠右鍵按一下第一個**接收**圖形啟動協調流程，然後再按一下**編輯篩選條件運算式**。</span><span class="sxs-lookup"><span data-stu-id="7a138-117">Right-click the first **Receive** shape that activates the orchestration, and then click **Edit Filter Expression**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a138-118">預設 BTARN 回應者私用程序協調流程的接收圖形有兩個篩選條件：Microsoft.Solutions.BTARN.GlobalSchemas.SCCategory == "AsyncAction" 或 Microsoft.Solutions.BTARN.GlobalSchemas.SCCategory == "SyncAction"。</span><span class="sxs-lookup"><span data-stu-id="7a138-118">The receive shape for the default BTARN responder private-process orchestration has two filter conditions: Microsoft.Solutions.BTARN.GlobalSchemas.SCCategory == "AsyncAction" or Microsoft.Solutions.BTARN.GlobalSchemas.SCCategory == "SyncAction".</span></span> <span data-ttu-id="7a138-119">這個運算式可確定協調流程會處理 RosettaNet 訊息。</span><span class="sxs-lookup"><span data-stu-id="7a138-119">This expression makes sure that the orchestration processes RosettaNet messages.</span></span> <span data-ttu-id="7a138-120">請在您自訂的協調流程中保留這個篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="7a138-120">Retain this filter expression in your custom orchestration.</span></span>  
  
5.  <span data-ttu-id="7a138-121">在**篩選條件運算式**對話方塊中，屬性資料行中第一個開啟的資料列中，選取**Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode**從下拉式清單中，在 [運算子] 欄位中，選取 **==** 從下拉式清單中，[值] 欄位中，輸入三位數的 PIP 代碼，例如，輸入**3A4**。</span><span class="sxs-lookup"><span data-stu-id="7a138-121">In the **Filter Expression** dialog box, in the Property column in the first open row, select **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** from the drop-down list, in the Operator column, select **==** from the drop-down list, in the Value column, type the three-digit PIP code, for example, type **3A4**.</span></span>  
  
6.  <span data-ttu-id="7a138-122">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="7a138-122">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="7a138-123">開啟協調流程設計師中的預設回應者私用程序協調流程專案 (PrivateResponder.btproj)。</span><span class="sxs-lookup"><span data-stu-id="7a138-123">Open the default responder private-process orchestration project (PrivateResponder.btproj) in Orchestration Designer.</span></span> <span data-ttu-id="7a138-124">請確定專案可以參考到 Microsoft.Solutions.BTARN.GlobalSchemas.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="7a138-124">Make sure that the project has a working reference to the Microsoft.Solutions.BTARN.GlobalSchemas.dll file.</span></span>  
  
8.  <span data-ttu-id="7a138-125">按兩下**PrivateResponder.odx**。</span><span class="sxs-lookup"><span data-stu-id="7a138-125">Double-click **PrivateResponder.odx**.</span></span>  
  
9. <span data-ttu-id="7a138-126">以滑鼠右鍵按一下**ReceiveFromPublicProcessResponder**接收圖形，然後按一下**編輯篩選條件運算式**。</span><span class="sxs-lookup"><span data-stu-id="7a138-126">Right-click the **ReceiveFromPublicProcessResponder** receive shape, and then click **Edit Filter Expression**.</span></span>  
  
10. <span data-ttu-id="7a138-127">在**篩選條件運算式**對話方塊中，屬性資料行中第一個開啟的資料列中，選取**Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="7a138-127">In the **Filter Expression** dialog box, in the Property column in the first open row, select **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** from the drop-down list.</span></span> <span data-ttu-id="7a138-128">在 [運算子] 欄位中，選取**！ =**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="7a138-128">In the Operator column, select **!=** from the drop-down list.</span></span> <span data-ttu-id="7a138-129">在 [值] 欄位中輸入三位數的 PIP 代碼，例如，輸入 「**3A4"**。</span><span class="sxs-lookup"><span data-stu-id="7a138-129">In the Value column, type the three-digit PIP code, for example, type "**3A4"**.</span></span>  
  
11. <span data-ttu-id="7a138-130">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="7a138-130">Click **OK**.</span></span>  
  
12. <span data-ttu-id="7a138-131">在方案總管] 中，以滑鼠右鍵按一下包含協調流程的專案，然後按一下 [**建置**。</span><span class="sxs-lookup"><span data-stu-id="7a138-131">In Solution Explorer, right-click the project that contains the orchestration and then click **Build**.</span></span>  
  
13. <span data-ttu-id="7a138-132">成功建置專案之後，以滑鼠右鍵按一下專案，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="7a138-132">After the project has been successfully built, right-click the project, and then click **Deploy**.</span></span>  
  
14. <span data-ttu-id="7a138-133">在**檔案**功能表上，指向**開啟**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="7a138-133">On the **File** menu, point to **Open**, and then click **Project**.</span></span>  
  
15. <span data-ttu-id="7a138-134">移至\<*磁碟機*\>: \Program Files\BizTalk\<版本\>Accelerator for RosettaNet\SDK\PrivateResponder，選取**PrivateResponder.odx**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="7a138-134">Move to \<*drive*\>:\Program Files\BizTalk \<version\> Accelerator for RosettaNet\SDK\PrivateResponder, select **PrivateResponder.odx**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="7a138-135">在方案總管中，以滑鼠右鍵按一下專案，然後按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="7a138-135">In Solution Explorer, right-click the project, and then click **Build**.</span></span>  
  
17. <span data-ttu-id="7a138-136">成功建置專案之後，以滑鼠右鍵按一下專案，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="7a138-136">After the project has been successfully built, right-click the project, and then click **Deploy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a138-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="7a138-137">See Also</span></span>  
 [<span data-ttu-id="7a138-138">程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7a138-138">Programming Guide</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)