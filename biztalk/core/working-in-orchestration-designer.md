---
title: 使用協調流程設計師 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, saving
- deleting, orchestrations
- projects, orchestrations
- orchestrations, properties
- orchestrations, creating
- creating, orchestrations
- naming conventions, orchestrations
- orchestrations, naming conventions
- orchestrations, deleting
ms.assetid: 13e72b41-d9b6-4508-9a44-b3c7c1804f36
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52eb574f9f6b55b784357ff03c05ccb23774fecb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975476"
---
# <a name="working-in-orchestration-designer"></a><span data-ttu-id="4869f-102">使用協調流程設計師</span><span class="sxs-lookup"><span data-stu-id="4869f-102">Working in Orchestration Designer</span></span>
<span data-ttu-id="4869f-103">啟動 BizTalk 專案之後，您可以建立新的協調流程，並將現有的協調流程加入專案。</span><span class="sxs-lookup"><span data-stu-id="4869f-103">After you have started a BizTalk project, you can create new orchestrations and add existing orchestrations to the project.</span></span> <span data-ttu-id="4869f-104">請參閱下列程序，建立和儲存協調流程、在專案中加入或移除現有協調流程、變更協調流程名稱，以及設定協調流程屬性。</span><span class="sxs-lookup"><span data-stu-id="4869f-104">See the following procedures to create and save an orchestration, to add an existing orchestration to a project or remove one from it, to change the name of an orchestration, and to set orchestration properties.</span></span>  
  
### <a name="to-create-an-orchestration"></a><span data-ttu-id="4869f-105">建立協調流程</span><span class="sxs-lookup"><span data-stu-id="4869f-105">To create an orchestration</span></span>  
  
1.  <span data-ttu-id="4869f-106">在 方案總管 中，以滑鼠右鍵按一下專案名稱，請選取**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="4869f-106">In Solution Explorer, right-click the project name, select **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="4869f-107">在**加入新項目**對話方塊中，於**類別** 窗格中，按一下  **BizTalk 專案項目**，然後在**範本** 窗格中，按一下**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="4869f-107">In the **Add New Item** dialog box, in the **Categories** pane, click **BizTalk Project Items**, and then in the **Templates** pane, click **BizTalk Orchestration**.</span></span>  
  
3.  <span data-ttu-id="4869f-108">在**名稱**方塊 對話方塊底部提供的協調流程的名稱，然後按**新增**。</span><span class="sxs-lookup"><span data-stu-id="4869f-108">In the **Name** box at the bottom of the dialog box, supply a name for the orchestration, and then click **Add**.</span></span>  
  
     <span data-ttu-id="4869f-109">[協調流程設計師] 中便會建立並顯示新的協調流程，而 [方案總管] 中則會建立並顯示對應的 .odx 檔案。</span><span class="sxs-lookup"><span data-stu-id="4869f-109">The new orchestration is created and displayed in Orchestration Designer, and a corresponding .odx file is created and displayed in Solution Explorer.</span></span>  
  
### <a name="to-add-an-existing-orchestration-to-a-project"></a><span data-ttu-id="4869f-110">將現有的協調流程加入至專案</span><span class="sxs-lookup"><span data-stu-id="4869f-110">To add an existing orchestration to a project</span></span>  
  
1.  <span data-ttu-id="4869f-111">在 方案總管 中，以滑鼠右鍵按一下專案名稱，請按一下**新增**，然後按一下 **現有項目**。</span><span class="sxs-lookup"><span data-stu-id="4869f-111">In Solution Explorer, right-click the project name, click **Add**, and then click **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="4869f-112">在**加入現有項目**對話方塊中，瀏覽至包含協調流程的目錄中，選取協調流程，，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="4869f-112">In the **Add Existing Item** dialog box, navigate to the directory containing the orchestration, select the orchestration, and then click **Add**.</span></span>  
  
     <span data-ttu-id="4869f-113">協調流程便會加入專案中。</span><span class="sxs-lookup"><span data-stu-id="4869f-113">The orchestration is added to the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4869f-114">當您加入現有檔案時，會將該檔案複製到專案中</span><span class="sxs-lookup"><span data-stu-id="4869f-114">When you add an existing file, the file is copied to your project.</span></span> <span data-ttu-id="4869f-115">(並非只是加入檔案的參考)。如果您變更專案中的檔案，原始檔案會保持不變。</span><span class="sxs-lookup"><span data-stu-id="4869f-115">(The file is not simply added by reference.) If you change the file in your project, the original file is left unchanged.</span></span>  
  
### <a name="to-change-the-name-of-an-orchestration"></a><span data-ttu-id="4869f-116">變更協調流程的名稱</span><span class="sxs-lookup"><span data-stu-id="4869f-116">To change the name of an orchestration</span></span>  
  
1.  <span data-ttu-id="4869f-117">在 [方案總管] 中，以滑鼠右鍵按一下您想要變更，然後再按一下.odx 檔案**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="4869f-117">In Solution Explorer, right-click the .odx file you want to change, and then click **Rename**.</span></span>  
  
2.  <span data-ttu-id="4869f-118">輸入想要的新檔案名稱，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="4869f-118">Type the new file name you want, and then press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4869f-119">當您變更.odx 檔案的名稱時，您也可以按一下設計介面，以顯示 [屬性] 視窗，然後變更的值變更協調流程類型的名稱**Typename**屬性協調流程。</span><span class="sxs-lookup"><span data-stu-id="4869f-119">When you change the name of an .odx file, you might also want to change the name of the orchestration type by clicking on the design surface to bring up the Properties window and changing the value of the **Typename** property of the orchestration.</span></span>  
  
### <a name="to-save-an-orchestration"></a><span data-ttu-id="4869f-120">儲存協調流程</span><span class="sxs-lookup"><span data-stu-id="4869f-120">To save an orchestration</span></span>  
  
-   <span data-ttu-id="4869f-121">在**檔案**功能表上，按一下 **儲存\<協調流程的名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="4869f-121">On the **File** menu, click **Save \<orchestration name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4869f-122">協調流程檔案會儲存為 utf-8。</span><span class="sxs-lookup"><span data-stu-id="4869f-122">Orchestration files are saved as UTF-8.</span></span>  <span data-ttu-id="4869f-123">結構描述、 對應和管線會儲存為 utf-16。</span><span class="sxs-lookup"><span data-stu-id="4869f-123">Schemas, maps, and pipelines are saved as UTF-16.</span></span>  
  
### <a name="to-remove-an-orchestration-from-a-project"></a><span data-ttu-id="4869f-124">從專案移除協調流程</span><span class="sxs-lookup"><span data-stu-id="4869f-124">To remove an orchestration from a project</span></span>  
  
-   <span data-ttu-id="4869f-125">在 方案總管 中，以滑鼠右鍵按一下您想要移除，然後按一下 的檔案**從專案移除**。</span><span class="sxs-lookup"><span data-stu-id="4869f-125">In Solution Explorer, right-click the file you want to remove, and then click **Exclude From Project**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4869f-126">若要從專案移除協調流程並永久刪除檔案，按一下**刪除**改為。</span><span class="sxs-lookup"><span data-stu-id="4869f-126">To remove the orchestration from a project and permanently delete the file, click **Delete** instead.</span></span>  
  
### <a name="to-include-an-excluded-orchestration-in-a-project"></a><span data-ttu-id="4869f-127">在專案中包含已排除的協調流程</span><span class="sxs-lookup"><span data-stu-id="4869f-127">To include an excluded orchestration in a project</span></span>  
  
-   <span data-ttu-id="4869f-128">在 方案總管 中，按一下 **全部顯示**工具列按鈕，以滑鼠右鍵按一下.odx 檔案，並選取**加入至專案**。</span><span class="sxs-lookup"><span data-stu-id="4869f-128">In Solution Explorer, click the **Show All** toolbar button, right-click the .odx file you want, and select **Include in Project**.</span></span>  
  
### <a name="to-set-orchestration-properties"></a><span data-ttu-id="4869f-129">設定協調流程屬性</span><span class="sxs-lookup"><span data-stu-id="4869f-129">To set orchestration properties</span></span>  
  
1.  <span data-ttu-id="4869f-130">按兩下專案中的 .odx 檔案，或選取 [處理區域] 中包含協調流程的索引標籤，以開啟協調流程。</span><span class="sxs-lookup"><span data-stu-id="4869f-130">Open the orchestration by double-clicking on the .odx file in the project, or by selecting the tab containing the orchestration in the Process Area.</span></span>  
  
2.  <span data-ttu-id="4869f-131">在 [協調流程檢視] 視窗中，選取**協調流程屬性**。</span><span class="sxs-lookup"><span data-stu-id="4869f-131">In the Orchestration View window, select **Orchestration Properties**.</span></span>  
  
     <span data-ttu-id="4869f-132">-或者-</span><span class="sxs-lookup"><span data-stu-id="4869f-132">—Or—</span></span>  
  
     <span data-ttu-id="4869f-133">按一下**流程領域**協調流程設計介面的背景。</span><span class="sxs-lookup"><span data-stu-id="4869f-133">Click the **Process Area** background of the Orchestration Design Surface.</span></span>  
  
3.  <span data-ttu-id="4869f-134">在 [屬性] 視窗中，指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="4869f-134">In the Properties window, specify the following properties.</span></span> <span data-ttu-id="4869f-135">請注意，某些屬性只有在特定情況下才會出現。</span><span class="sxs-lookup"><span data-stu-id="4869f-135">Note that some properties appear only under certain circumstances.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4869f-136">協調流程、連接埠類型及多部分訊息類型的名稱在模組的範圍內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4869f-136">The names of orchestrations, port types and multi-part message types must be unique within the scope of a module.</span></span>  
  
    |<span data-ttu-id="4869f-137">屬性</span><span class="sxs-lookup"><span data-stu-id="4869f-137">Property</span></span>|<span data-ttu-id="4869f-138">Description</span><span class="sxs-lookup"><span data-stu-id="4869f-138">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="4869f-139">批次</span><span class="sxs-lookup"><span data-stu-id="4869f-139">Batch</span></span>|<span data-ttu-id="4869f-140">決定「不可部分完成交易」的協調流程是否能和其他執行個體一起，以批次方式執行。</span><span class="sxs-lookup"><span data-stu-id="4869f-140">Determines whether an orchestration that is an atomic transaction can be batched with other instances.</span></span>|  
    |<span data-ttu-id="4869f-141">補償</span><span class="sxs-lookup"><span data-stu-id="4869f-141">Compensation</span></span>|<span data-ttu-id="4869f-142">指定要在協調流程上執行的補償類型。</span><span class="sxs-lookup"><span data-stu-id="4869f-142">Specifies what type of compensation to perform on the orchestration.</span></span>|  
    |<span data-ttu-id="4869f-143">隔離等級</span><span class="sxs-lookup"><span data-stu-id="4869f-143">Isolation Level</span></span>|<span data-ttu-id="4869f-144">決定交易式協調流程可在並行交易之間存取資料的權限等級。</span><span class="sxs-lookup"><span data-stu-id="4869f-144">For transactional orchestrations, determines the degree to which data is accessible among concurrent transactions.</span></span>|  
    |<span data-ttu-id="4869f-145">模組可匯出</span><span class="sxs-lookup"><span data-stu-id="4869f-145">Module Exportable</span></span>|<span data-ttu-id="4869f-146">決定是否可以將模組匯出至 BPEL4WS。</span><span class="sxs-lookup"><span data-stu-id="4869f-146">Determines whether or not the module can be exported to BPEL4WS.</span></span>|  
    |<span data-ttu-id="4869f-147">模組 XML 目標命名空間</span><span class="sxs-lookup"><span data-stu-id="4869f-147">Module XML Target Namespace</span></span>|<span data-ttu-id="4869f-148">在匯出類型至 BPEL4WS 時所使用的 XML 目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="4869f-148">The XML target namespace used when exporting types to BPEL4WS.</span></span>|  
    |<span data-ttu-id="4869f-149">命名空間</span><span class="sxs-lookup"><span data-stu-id="4869f-149">Namespace</span></span>|<span data-ttu-id="4869f-150">決定將包括協調流程和協調流程類型之容納模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="4869f-150">Determines the name of the containing module that includes the orchestration and the orchestration types.</span></span>|  
    |<span data-ttu-id="4869f-151">協調流程可匯出</span><span class="sxs-lookup"><span data-stu-id="4869f-151">Orchestration Exportable</span></span>|<span data-ttu-id="4869f-152">指出此協調流程是否可供匯出至 BPEL4WS。</span><span class="sxs-lookup"><span data-stu-id="4869f-152">Indicates whether this orchestration is intended to be exportable to BPEL4WS.</span></span>|  
    |<span data-ttu-id="4869f-153">協調流程 XML 目標命名空間</span><span class="sxs-lookup"><span data-stu-id="4869f-153">Orchestration XML Target Namespace</span></span>|<span data-ttu-id="4869f-154">在匯出此協調流程至 BPEL4WS 時所使用的 XML 目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="4869f-154">The XML target namespace used when exporting this orchestration to BPEL4WS.</span></span>|  
    |<span data-ttu-id="4869f-155">重試</span><span class="sxs-lookup"><span data-stu-id="4869f-155">Retry</span></span>|<span data-ttu-id="4869f-156">指定是否在交易式協調流程失敗時進行重試。</span><span class="sxs-lookup"><span data-stu-id="4869f-156">Specify whether to retry a transactional orchestration if it fails.</span></span>|  
    |<span data-ttu-id="4869f-157">逾時</span><span class="sxs-lookup"><span data-stu-id="4869f-157">Timeout</span></span>|<span data-ttu-id="4869f-158">交易式協調流程閒置多久之後即視為失敗的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="4869f-158">The time in seconds until a transactional orchestration fails due to inactivity.</span></span>|  
    |<span data-ttu-id="4869f-159">交易識別項</span><span class="sxs-lookup"><span data-stu-id="4869f-159">Transaction Identifier</span></span>|<span data-ttu-id="4869f-160">交易式協調流程的唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="4869f-160">Unique identifier for a transactional orchestration.</span></span>|  
    |<span data-ttu-id="4869f-161">[交易類型]</span><span class="sxs-lookup"><span data-stu-id="4869f-161">Transaction Type</span></span>|<span data-ttu-id="4869f-162">決定協調流程是不可部分完成的交易、長時間執行的交易，或者不是交易。</span><span class="sxs-lookup"><span data-stu-id="4869f-162">Determines whether the orchestration is an atomic transaction, a long-running transaction, or is not transacted.</span></span>|  
    |<span data-ttu-id="4869f-163">型別修飾詞</span><span class="sxs-lookup"><span data-stu-id="4869f-163">Type Modifier</span></span>|<span data-ttu-id="4869f-164">決定協調流程層級變數的範圍：</span><span class="sxs-lookup"><span data-stu-id="4869f-164">Determines the scope of orchestration-level variables:</span></span><br /><br /> <span data-ttu-id="4869f-165">私用：只限包含的模組存取此協調流程。</span><span class="sxs-lookup"><span data-stu-id="4869f-165">Private—Access to this orchestration is limited to the containing module.</span></span><br /><br /> <span data-ttu-id="4869f-166">公用：存取此協調流程不受任何限制。</span><span class="sxs-lookup"><span data-stu-id="4869f-166">Public—Access to this orchestration is not limited.</span></span><br /><br /> <span data-ttu-id="4869f-167">內部：只限相同專案中的模組存取此協調流程。</span><span class="sxs-lookup"><span data-stu-id="4869f-167">Internal—Access to this orchestration is limited to modules within the same project.</span></span>|  
    |<span data-ttu-id="4869f-168">類型名稱</span><span class="sxs-lookup"><span data-stu-id="4869f-168">Typename</span></span>|<span data-ttu-id="4869f-169">決定此協調流程在包含的模組中的名稱。</span><span class="sxs-lookup"><span data-stu-id="4869f-169">Determines the name of this orchestration within the containing module.</span></span> <span data-ttu-id="4869f-170">**注意：** 如果您使用的根層級命名空間，與相同類型名稱時可能會收到錯誤來自協調流程設計師定義訊息，並根據類型名稱，嘗試執行變數指派的運算。</span><span class="sxs-lookup"><span data-stu-id="4869f-170">**Note:**  If you to use a Typename that is the same as a root-level namespace, you may receive an error from Orchestration Designer when you define messages and variables based on the Typename and attempt to perform assign operations on them.</span></span> <span data-ttu-id="4869f-171">例如，如果您指定類型名稱的系統，然後定義訊息和變數，如下 System.String，您可能會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="4869f-171">For example, if you specify a Typename of System, and then define messages and variables like System.String, you may receive an error.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4869f-172">請參閱</span><span class="sxs-lookup"><span data-stu-id="4869f-172">See Also</span></span>  
 <span data-ttu-id="4869f-173">[協調流程圖形](../core/orchestration-shapes.md) </span><span class="sxs-lookup"><span data-stu-id="4869f-173">[Orchestration Shapes](../core/orchestration-shapes.md) </span></span>  
 <span data-ttu-id="4869f-174">[如何新增圖形至協調流程](../core/how-to-add-shapes-to-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="4869f-174">[How to Add Shapes to Orchestrations](../core/how-to-add-shapes-to-orchestrations.md) </span></span>  
 <span data-ttu-id="4869f-175">[如何新增參數至協調流程](../core/how-to-add-parameters-to-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="4869f-175">[How to Add Parameters to Orchestrations](../core/how-to-add-parameters-to-orchestrations.md) </span></span>  
 [<span data-ttu-id="4869f-176">如何使用選取成品類型對話方塊</span><span class="sxs-lookup"><span data-stu-id="4869f-176">How to Use the Select Artifact Type Dialog Box</span></span>](../core/how-to-use-the-select-artifact-type-dialog-box.md)