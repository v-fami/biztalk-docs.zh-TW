---
title: 建立及部署 A4SWIFT 管線 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, pipelines
- deploying, pipelines
- pipelines, deploying
- pipelines, creating
ms.assetid: 2a614510-7e15-4e88-9012-fc019d3aefee
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bec21ebd5a3b32986969676a78109cad55d870cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210950"
---
# <a name="creating-and-deploying-a4swift-pipelines"></a><span data-ttu-id="175b6-102">建立及部署 A4SWIFT 管線</span><span class="sxs-lookup"><span data-stu-id="175b6-102">Creating and Deploying A4SWIFT Pipelines</span></span>
<span data-ttu-id="175b6-103">執行下列步驟來建立及部署 SWIFT 訊息修復和新送出，管線中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="175b6-103">Perform the following steps to create and deploy SWIFT pipelines for message repair and new submission, as shown in the following figure.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-pipeline-configuration.gif "A4SWIFT_Pipeline_Configuration")  
  
 <span data-ttu-id="175b6-104">**摘要**</span><span class="sxs-lookup"><span data-stu-id="175b6-104">**Summary**</span></span>  
  
 <span data-ttu-id="175b6-105">部署的下列結構描述：</span><span class="sxs-lookup"><span data-stu-id="175b6-105">Deploy the following schemas:</span></span>  
  
-   <span data-ttu-id="175b6-106">自訂接收具有 SWIFT 解譯器管線。</span><span class="sxs-lookup"><span data-stu-id="175b6-106">Custom receive pipeline with the SWIFT Disassembler.</span></span> <span data-ttu-id="175b6-107">設定 BRE 驗證 」 和 「 XML 驗證的屬性為 True，而且此 SWIFT 標頭結構描述屬性為 （無）。</span><span class="sxs-lookup"><span data-stu-id="175b6-107">Set BRE Validation and XML Validation properties to True, and the SWIFT Header Schema property to (None).</span></span>  
  
-   <span data-ttu-id="175b6-108">自訂傳送管線與 SWIFT 組譯工具</span><span class="sxs-lookup"><span data-stu-id="175b6-108">Custom send pipeline with the SWIFT Assembler</span></span>  
  
### <a name="to-create-a-pipeline-project"></a><span data-ttu-id="175b6-109">若要建立管線專案</span><span class="sxs-lookup"><span data-stu-id="175b6-109">To create a pipeline project</span></span>  
  
1.  <span data-ttu-id="175b6-110">在 Visual Studio 中，按一下 **檔案**，指向 **新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="175b6-110">In Visual Studio, click **File**, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="175b6-111">在 [新增專案] 對話方塊中**專案類型**窗格中，選取**BizTalk 專案**資料夾。</span><span class="sxs-lookup"><span data-stu-id="175b6-111">In the New Project dialog box, in the **Project types** pane, select the **BizTalk Projects** folder.</span></span>  
  
3.  <span data-ttu-id="175b6-112">在**範本**窗格中，選取**空白 BizTalk Server 專案**。</span><span class="sxs-lookup"><span data-stu-id="175b6-112">In the **Templates** pane, select **Empty BizTalk Server Project**.</span></span>  
  
4.  <span data-ttu-id="175b6-113">在**名稱**方塊中，輸入您要針對專案名稱的名稱。</span><span class="sxs-lookup"><span data-stu-id="175b6-113">In the **Name** box, type the name you want for the project name.</span></span>  
  
5.  <span data-ttu-id="175b6-114">在**方案**方塊中，選取**將加入至方案**。</span><span class="sxs-lookup"><span data-stu-id="175b6-114">In the **Solution** box, select **Add to Solution**.</span></span> <span data-ttu-id="175b6-115">在**位置**方塊中，輸入您在建立結構描述專案的位置[部署 A4SWIFT 結構描述](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="175b6-115">In the **Location** box, enter the location of the schema project that you created in [Deploying A4SWIFT Schemas](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md).</span></span>  
  
6.  <span data-ttu-id="175b6-116">按一下**確定**開啟新的專案。</span><span class="sxs-lookup"><span data-stu-id="175b6-116">Click **OK** to open the new project.</span></span>  
    [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="175b6-117">[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]將新專案加入方案總管 中，並在指定的資料夾中建立的專案資料夾和檔案。</span><span class="sxs-lookup"><span data-stu-id="175b6-117">[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] adds a new project to Solution Explorer, and creates the project folder and files in the folder specified.</span></span>  
  
7.  <span data-ttu-id="175b6-118">建立並指派強式金鑰檔案加入專案。</span><span class="sxs-lookup"><span data-stu-id="175b6-118">Create and assign a strong key file to the project.</span></span> <span data-ttu-id="175b6-119">如需詳細資訊，請參閱建立強式名稱的 SWIFT 專案 」 中[部署 A4SWIFT 結構描述](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="175b6-119">For more information, see "To create a strong-named SWIFT project" in [Deploying A4SWIFT Schemas](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md).</span></span>  
  
### <a name="to-add-a-custom-receive-pipeline"></a><span data-ttu-id="175b6-120">若要加入自訂接收管線</span><span class="sxs-lookup"><span data-stu-id="175b6-120">To add a custom receive pipeline</span></span>  
  
1.  <span data-ttu-id="175b6-121">在 方案總管 中，以滑鼠右鍵按一下管線專案，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="175b6-121">In Solution Explorer, right-click your pipeline project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="175b6-122">在 [加入新項目] 對話方塊中，按一下**管線檔案**在分類窗格中，然後選取**接收管線**從 [範本] 窗格。</span><span class="sxs-lookup"><span data-stu-id="175b6-122">In the Add New Item dialog box, click **Pipeline Files** in the Categories pane, and then select **Receive Pipeline** from the Templates pane.</span></span>  
  
3.  <span data-ttu-id="175b6-123">在**名稱**方塊中，輸入管線的名稱。</span><span class="sxs-lookup"><span data-stu-id="175b6-123">In the **Name** box, type a name for the pipeline.</span></span>  
  
4.  <span data-ttu-id="175b6-124">按一下**新增**BizTalk 管線設計師中開啟空白的管線。</span><span class="sxs-lookup"><span data-stu-id="175b6-124">Click **Add** to open the blank pipeline in BizTalk Pipeline Designer.</span></span>  
  
5.  <span data-ttu-id="175b6-125">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下 **檢視**然後**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="175b6-125">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **View** and then **Toolbox**.</span></span>  
  
6.  <span data-ttu-id="175b6-126">從**BizTalk 管線元件工具箱**，拖曳**SWIFT 解譯器**至**放置到此處**下列方塊**解譯**階段圖形中**BizTalk 管線設計師**。</span><span class="sxs-lookup"><span data-stu-id="175b6-126">From the **BizTalk Pipeline Components Toolbox**, drag the **SWIFT Disassembler** to the **Drop Here** box below the **Disassemble** stage shape in **BizTalk Pipeline Designer**.</span></span> <span data-ttu-id="175b6-127">保留**SWIFT 解譯器**中為已選取**BizTalk 管線設計師**。</span><span class="sxs-lookup"><span data-stu-id="175b6-127">Leave the **SWIFT Disassembler** as selected in the **BizTalk Pipeline Designer**.</span></span>  
  
7.  <span data-ttu-id="175b6-128">在**屬性**，確認**BRE 驗證**和**XML 驗證**屬性會設為**True**。</span><span class="sxs-lookup"><span data-stu-id="175b6-128">In **Properties**, verify that the **BRE Validation** and **XML Validation** properties are set to **True**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="175b6-129">SWIFT 標頭結構描述屬性應該設定為 **（無）**。</span><span class="sxs-lookup"><span data-stu-id="175b6-129">The SWIFT Header Schema property should be set to **(None)**.</span></span>  
  
8.  <span data-ttu-id="175b6-130">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下 **檔案**，然後**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="175b6-130">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **File**, and then **Save All**.</span></span>  
  
### <a name="to-add-a-custom-send-pipeline"></a><span data-ttu-id="175b6-131">若要加入自訂傳送管線</span><span class="sxs-lookup"><span data-stu-id="175b6-131">To add a custom send pipeline</span></span>  
  
1.  <span data-ttu-id="175b6-132">在 方案總管 中，以滑鼠右鍵按一下**SWIFTPipelines**專案，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="175b6-132">In Solution Explorer, right-click the **SWIFTPipelines** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="175b6-133">在 [加入新項目] 對話方塊中，確認**管線檔案**是在分類窗格中，選取，然後選取**傳送管線**從 [範本] 窗格。</span><span class="sxs-lookup"><span data-stu-id="175b6-133">In the Add New Item dialog box, verify that **Pipeline Files** is selected in the Categories pane, and then select **Send Pipeline** from the Templates pane.</span></span>  
  
3.  <span data-ttu-id="175b6-134">在**名稱**方塊中，輸入管線的名稱。</span><span class="sxs-lookup"><span data-stu-id="175b6-134">In the **Name** box, type a name for the pipeline.</span></span>  
  
4.  <span data-ttu-id="175b6-135">按一下**新增**BizTalk 管線設計師中開啟空白的管線。</span><span class="sxs-lookup"><span data-stu-id="175b6-135">Click **Add** to open the blank pipeline in BizTalk Pipeline Designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="175b6-136">BizTalk 管線設計師 」 中，會出現空的管線。</span><span class="sxs-lookup"><span data-stu-id="175b6-136">An empty pipeline appears in the BizTalk Pipeline Designer.</span></span> [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="175b6-137">加入方案總管 中的新管線 SWIFTPipelines 專案底下。</span><span class="sxs-lookup"><span data-stu-id="175b6-137"> adds the new pipeline to Solution Explorer under the SWIFTPipelines project.</span></span>  
  
5.  <span data-ttu-id="175b6-138">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下 **檢視**然後**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="175b6-138">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **View** and then **Toolbox**.</span></span>  
  
6.  <span data-ttu-id="175b6-139">在**BizTalk 管線元件 [工具箱]**，拖曳**SWIFT 組譯工具**至**放置到此處**下列方塊**組合**階段中的圖形**BizTalk 管線設計師**。</span><span class="sxs-lookup"><span data-stu-id="175b6-139">In the **BizTalk Pipeline Components Toolbox**, drag **SWIFT Assembler** to the **Drop Here** box below the **Assemble** stage shape in **BizTalk Pipeline Designer**.</span></span>  
  
7.  <span data-ttu-id="175b6-140">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下 **檔案**，然後**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="175b6-140">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **File**, and then **Save All**.</span></span>  
  
8.  <span data-ttu-id="175b6-141">以滑鼠右鍵按一下管線專案，然後再按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="175b6-141">Right click the pipelines project, and then click **Build**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="175b6-142">在編譯過程中，您應該不會看到任何失敗。</span><span class="sxs-lookup"><span data-stu-id="175b6-142">During the compilation process, you should not see any failures.</span></span> <span data-ttu-id="175b6-143">如果您這樣做，請檢查錯誤的來源、 修正和重新建置專案。</span><span class="sxs-lookup"><span data-stu-id="175b6-143">If you do, check the source of the error, correct it and then re-build the project.</span></span> <span data-ttu-id="175b6-144">不過，您可能會看到警告。</span><span class="sxs-lookup"><span data-stu-id="175b6-144">You may, however, see warnings.</span></span> <span data-ttu-id="175b6-145">您可以修正警告前置條件。</span><span class="sxs-lookup"><span data-stu-id="175b6-145">You can correct the condition leading to the warnings.</span></span> <span data-ttu-id="175b6-146">如需詳細資訊，請參閱 「 建置管線專案可能會導致警告 」，在[其他已知問題](http://msdn.microsoft.com/library/bc94c781-2a56-4f80-8ecb-e654de2f6ed6)。</span><span class="sxs-lookup"><span data-stu-id="175b6-146">For more information, see "Building a pipeline project may result in warnings" in [Miscellaneous Known Issues](http://msdn.microsoft.com/library/bc94c781-2a56-4f80-8ecb-e654de2f6ed6).</span></span>  
  
9. <span data-ttu-id="175b6-147">以滑鼠右鍵按一下管線專案，然後再按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="175b6-147">Right click the pipelines project, and then click **Deploy**.</span></span>