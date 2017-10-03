---
title: "如何控制結果清單的大小 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- results list [Orchestration Debugger], deleting columns
- results list [Orchestration Debugger], limiting list size
- Orchestration Debugger, results list
- results list [Orchestration Designer]
- results list [Orchestration Debugger], adding columns
ms.assetid: 4d41003f-5ea9-4599-8ec0-737c342ffdbd
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80787e4c7dbac57aca9c787943846e924a1a7870
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-control-the-size-of-the-results-list"></a><span data-ttu-id="5097d-102">如何控制結果清單的大小</span><span class="sxs-lookup"><span data-stu-id="5097d-102">How to Control the Size of the Results List</span></span>
<span data-ttu-id="5097d-103">在**群組中樞**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，查詢結果 窗格包含這麼多的資料行的資訊，您需要捲動來檢視它們。</span><span class="sxs-lookup"><span data-stu-id="5097d-103">On the **Group Hub** page of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, the Query results pane contains so many columns of information that you need to scroll to view them.</span></span> <span data-ttu-id="5097d-104">您可以新增或移除窗格中的欄位，只顯示您需要的資訊。</span><span class="sxs-lookup"><span data-stu-id="5097d-104">You can add or remove columns in the pane to display only the information that you need.</span></span> <span data-ttu-id="5097d-105">若要新增或移除資料行，以滑鼠右鍵按一下 [查詢結果] 窗格，然後按一下的任何部分**新增/移除欄位**操作功能表上。</span><span class="sxs-lookup"><span data-stu-id="5097d-105">To add or remove columns, right-click any part of the Query results pane and click **Add/Remove Columns** on the context menu.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5097d-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="5097d-106">Prerequisites</span></span>  
 <span data-ttu-id="5097d-107">您必須以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators 群組成員的身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="5097d-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to perform this procedure.</span></span>  
  
### <a name="to-add-or-remove-columns-in-the-results-list"></a><span data-ttu-id="5097d-108">在結果清單中新增或移除欄位</span><span class="sxs-lookup"><span data-stu-id="5097d-108">To add or remove columns in the results list</span></span>  
  
1.  <span data-ttu-id="5097d-109">以滑鼠右鍵按一下任何資料格中**查詢結果**清單，然後再按**新增/移除欄位**操作功能表上。</span><span class="sxs-lookup"><span data-stu-id="5097d-109">Right-click any cell in the **Query results** list, and then click **Add/Remove Columns** on the context menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5097d-110">已存在於結果清單中的項目會出現在下方的右邊**顯示的資料行**。</span><span class="sxs-lookup"><span data-stu-id="5097d-110">Items that are already present in the results list appear on the right side under **Displayed Columns**.</span></span> <span data-ttu-id="5097d-111">不會出現在結果清單中的項目會出現在左側**可用的資料行**。</span><span class="sxs-lookup"><span data-stu-id="5097d-111">Items that are not present in the results list appear on the left side under **Available Columns**.</span></span>  
  
2.  <span data-ttu-id="5097d-112">若要加入資料行，選取其中一個項目從**可用的資料行**按一下**新增**若要將該資料行移到清單**顯示的資料行**。</span><span class="sxs-lookup"><span data-stu-id="5097d-112">To add a column, select one of the items from **Available Columns** and click **Add** to move that column to the list of **Displayed Columns**.</span></span>  
  
3.  <span data-ttu-id="5097d-113">若要移除資料行，選取其中一個項目從**顯示的資料行**按一下**移除**若要將該資料行移到清單**可用的資料行**。</span><span class="sxs-lookup"><span data-stu-id="5097d-113">To remove a column, select one of the items from **Displayed Columns** and click **Remove** to move that column to the list of **Available Columns**.</span></span>  
  
 <span data-ttu-id="5097d-114">透過使用建立或執行查詢時提供的篩選，可以控制查詢傳回的結果數。</span><span class="sxs-lookup"><span data-stu-id="5097d-114">You can control the number of results that the query returns by using the filters that are provided when you create or run a query.</span></span>  
  
## <a name="columns-in-the-query-results-list"></a><span data-ttu-id="5097d-115">查詢結果清單中的欄位</span><span class="sxs-lookup"><span data-stu-id="5097d-115">Columns in the Query Results List</span></span>  
 <span data-ttu-id="5097d-116">查詢結果會顯示於產生查詢之檢視下方的 [查詢結果] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="5097d-116">The query results are displayed in the Query results pane at the bottom of the view that originated the query.</span></span> <span data-ttu-id="5097d-117">您無法直接存取結果清單。</span><span class="sxs-lookup"><span data-stu-id="5097d-117">You cannot directly access the results list.</span></span> <span data-ttu-id="5097d-118">快顯功能表會顯示您可對目前作用中之檢視內選取的記錄執行的所有動作。</span><span class="sxs-lookup"><span data-stu-id="5097d-118">The context menu shows all of the actions you can perform on the selected record within the currently active view.</span></span> <span data-ttu-id="5097d-119">例如，若記錄包括「服務執行個體識別碼」，則會出現服務相關的動作。</span><span class="sxs-lookup"><span data-stu-id="5097d-119">For example, if the record contains a Service Instance ID, then service-related actions appear.</span></span> <span data-ttu-id="5097d-120">如果有「訊息識別碼」，則會顯示訊息相關動作。</span><span class="sxs-lookup"><span data-stu-id="5097d-120">If there is a Message ID, then message-related actions appear.</span></span>  
  
 <span data-ttu-id="5097d-121">因為您可能不需要此完整清單中包含的所有資訊，您可以僅選取想要檢視的欄位，或取代您移除的欄位。</span><span class="sxs-lookup"><span data-stu-id="5097d-121">Because you might not need all the information contained in this complete list, you can select only those columns you want to view, or you can replace columns that you removed.</span></span> <span data-ttu-id="5097d-122">當您依照時間排序結果清單時，執行個體會排序至毫秒，即使毫秒沒有出現在清單上也一樣。</span><span class="sxs-lookup"><span data-stu-id="5097d-122">When you sort the results list by time, the instances sort up to milliseconds, even if no milliseconds appear on the list.</span></span> <span data-ttu-id="5097d-123">當您重複使用已儲存的查詢時，每次執行查詢，結果都只會顯示選取的欄位。</span><span class="sxs-lookup"><span data-stu-id="5097d-123">When you reuse a saved query the results show only the columns selected each time the query is run.</span></span>  
  
 <span data-ttu-id="5097d-124">下表顯示結果清單上所顯示的完整項目清單。</span><span class="sxs-lookup"><span data-stu-id="5097d-124">The following table shows a complete list of the items that appear in the results list.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5097d-125">**服務或訊息欄位**</span><span class="sxs-lookup"><span data-stu-id="5097d-125">**Service or Message field**</span></span>|<span data-ttu-id="5097d-126">**說明**</span><span class="sxs-lookup"><span data-stu-id="5097d-126">**Description**</span></span>|  
|<span data-ttu-id="5097d-127">服務名稱</span><span class="sxs-lookup"><span data-stu-id="5097d-127">Service Name</span></span>|<span data-ttu-id="5097d-128">服務執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="5097d-128">Name of the service instance.</span></span>|  
|<span data-ttu-id="5097d-129">事件類型</span><span class="sxs-lookup"><span data-stu-id="5097d-129">Event Type</span></span>|<span data-ttu-id="5097d-130">服務類型 (例如，傳訊 (報告為「管線」)、協調流程、傳輸配接器)。</span><span class="sxs-lookup"><span data-stu-id="5097d-130">Type of service (for example, messaging (reported as Pipeline), orchestration, transport adapter).</span></span>|  
|<span data-ttu-id="5097d-131">錯誤描述</span><span class="sxs-lookup"><span data-stu-id="5097d-131">Error Description</span></span>|<span data-ttu-id="5097d-132">錯誤發生時的描述。</span><span class="sxs-lookup"><span data-stu-id="5097d-132">Description of the error if one occurred.</span></span>|  
|<span data-ttu-id="5097d-133">State</span><span class="sxs-lookup"><span data-stu-id="5097d-133">State</span></span>|<span data-ttu-id="5097d-134">執行查詢時的作業狀態。</span><span class="sxs-lookup"><span data-stu-id="5097d-134">State of the operation when the query was run.</span></span>|  
|<span data-ttu-id="5097d-135">錯誤碼</span><span class="sxs-lookup"><span data-stu-id="5097d-135">Error Code</span></span>|<span data-ttu-id="5097d-136">錯誤發生時的代碼。</span><span class="sxs-lookup"><span data-stu-id="5097d-136">Code of the error if one occurred.</span></span>|  
|<span data-ttu-id="5097d-137">解密憑證</span><span class="sxs-lookup"><span data-stu-id="5097d-137">Decryption Certificate</span></span>|<span data-ttu-id="5097d-138">顯示和訊息或服務相關的憑證資訊。</span><span class="sxs-lookup"><span data-stu-id="5097d-138">Shows the certificate information relating to the message or service.</span></span>|  
|<span data-ttu-id="5097d-139">有效期間</span><span class="sxs-lookup"><span data-stu-id="5097d-139">Duration</span></span>|<span data-ttu-id="5097d-140">完成作業所需的時間。</span><span class="sxs-lookup"><span data-stu-id="5097d-140">Time for the operation to complete.</span></span>|  
|<span data-ttu-id="5097d-141">連接埠名稱</span><span class="sxs-lookup"><span data-stu-id="5097d-141">Port Name</span></span>|<span data-ttu-id="5097d-142">與執行個體流程相關的連接埠。</span><span class="sxs-lookup"><span data-stu-id="5097d-142">Port involved in the flow of the instance.</span></span>|  
|<span data-ttu-id="5097d-143">簽章</span><span class="sxs-lookup"><span data-stu-id="5097d-143">Signature</span></span>|<span data-ttu-id="5097d-144">訊息的數位簽章資訊。</span><span class="sxs-lookup"><span data-stu-id="5097d-144">Digital signature information of the message.</span></span>|  
|<span data-ttu-id="5097d-145">大小</span><span class="sxs-lookup"><span data-stu-id="5097d-145">Size</span></span>|<span data-ttu-id="5097d-146">訊息大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="5097d-146">Size of the message in bytes.</span></span>|  
|<span data-ttu-id="5097d-147">Start Time</span><span class="sxs-lookup"><span data-stu-id="5097d-147">Start Time</span></span>|<span data-ttu-id="5097d-148">作業開始的時間。</span><span class="sxs-lookup"><span data-stu-id="5097d-148">Time the operation started.</span></span>|  
|<span data-ttu-id="5097d-149">結束時間</span><span class="sxs-lookup"><span data-stu-id="5097d-149">End Time</span></span>|<span data-ttu-id="5097d-150">作業結束的時間。</span><span class="sxs-lookup"><span data-stu-id="5097d-150">Time the operation ended.</span></span>|  
|<span data-ttu-id="5097d-151">部分計數</span><span class="sxs-lookup"><span data-stu-id="5097d-151">Part Count</span></span>|<span data-ttu-id="5097d-152">訊息的部分數目。</span><span class="sxs-lookup"><span data-stu-id="5097d-152">Number of parts in the message.</span></span>|  
|<span data-ttu-id="5097d-153">Party</span><span class="sxs-lookup"><span data-stu-id="5097d-153">Party</span></span>|<span data-ttu-id="5097d-154">開始作業的合作對象識別碼。</span><span class="sxs-lookup"><span data-stu-id="5097d-154">Identifier of the party starting the operation.</span></span>|  
|<span data-ttu-id="5097d-155">URI</span><span class="sxs-lookup"><span data-stu-id="5097d-155">URI</span></span>|<span data-ttu-id="5097d-156">發起合作對象的 URI。</span><span class="sxs-lookup"><span data-stu-id="5097d-156">URI of the initiating party.</span></span>|  
|<span data-ttu-id="5097d-157">TimeStamp</span><span class="sxs-lookup"><span data-stu-id="5097d-157">TimeStamp</span></span>|<span data-ttu-id="5097d-158">作業開始的時間。</span><span class="sxs-lookup"><span data-stu-id="5097d-158">Time the operation started.</span></span>|  
|<span data-ttu-id="5097d-159">Host</span><span class="sxs-lookup"><span data-stu-id="5097d-159">Host</span></span>|<span data-ttu-id="5097d-160">執行服務執行個體的 BizTalk 主控件名稱。</span><span class="sxs-lookup"><span data-stu-id="5097d-160">Name of the BizTalk Host running the service instance.</span></span>|  
|<span data-ttu-id="5097d-161">組件名稱</span><span class="sxs-lookup"><span data-stu-id="5097d-161">Assembly Name</span></span>|<span data-ttu-id="5097d-162">實作服務執行個體的 .NET 組件名稱。</span><span class="sxs-lookup"><span data-stu-id="5097d-162">Name of the .NET assembly that implements the service instance.</span></span>|  
|<span data-ttu-id="5097d-163">組件版本</span><span class="sxs-lookup"><span data-stu-id="5097d-163">Assembly Version</span></span>|<span data-ttu-id="5097d-164">相關組件的版本編號。</span><span class="sxs-lookup"><span data-stu-id="5097d-164">Version number of the related assembly.</span></span>|  
|<span data-ttu-id="5097d-165">部署時間</span><span class="sxs-lookup"><span data-stu-id="5097d-165">Deployment Time</span></span>|<span data-ttu-id="5097d-166">部署服務執行個體組件到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的時間。</span><span class="sxs-lookup"><span data-stu-id="5097d-166">Time that the service instance assembly deployed into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>|  
|<span data-ttu-id="5097d-167">活動識別碼</span><span class="sxs-lookup"><span data-stu-id="5097d-167">Activity ID</span></span>|<span data-ttu-id="5097d-168">識別唯一的服務執行個體活動 (例如，管線/協調流程所傳送/接收具有相同識別碼的訊息)。</span><span class="sxs-lookup"><span data-stu-id="5097d-168">Identifies unique service instance activity (for example, messages sent/received by the pipeline/orchestration have the same ID).</span></span>|  
|<span data-ttu-id="5097d-169">服務執行個體識別碼</span><span class="sxs-lookup"><span data-stu-id="5097d-169">Service Instance ID</span></span>|<span data-ttu-id="5097d-170">識別服務執行個體執行的「全域唯一識別碼」(GUID)。</span><span class="sxs-lookup"><span data-stu-id="5097d-170">Globally unique identifier (GUID) that identifies a run of a service instance.</span></span>|  
|<span data-ttu-id="5097d-171">訊息執行個體識別碼</span><span class="sxs-lookup"><span data-stu-id="5097d-171">Message Instance ID</span></span>|<span data-ttu-id="5097d-172">識別訊息執行個體的「全域唯一識別碼」(GUID)。</span><span class="sxs-lookup"><span data-stu-id="5097d-172">Globally unique identifier (GUID) that identifies a message instance.</span></span>|  
|<span data-ttu-id="5097d-173">服務識別碼</span><span class="sxs-lookup"><span data-stu-id="5097d-173">Service ID</span></span>|<span data-ttu-id="5097d-174">識別服務的「全域唯一識別碼」(GUID)。</span><span class="sxs-lookup"><span data-stu-id="5097d-174">Globally unique identifier (GUID) that identifies a service.</span></span>|  
|<span data-ttu-id="5097d-175">服務類別</span><span class="sxs-lookup"><span data-stu-id="5097d-175">Service Class</span></span>|<span data-ttu-id="5097d-176">類別的類型 (管線或協調流程)。</span><span class="sxs-lookup"><span data-stu-id="5097d-176">Type of class (pipeline or orchestration).</span></span>|  
|<span data-ttu-id="5097d-177">服務類別識別碼</span><span class="sxs-lookup"><span data-stu-id="5097d-177">Service Class ID</span></span>|<span data-ttu-id="5097d-178">識別服務 (例如，協調流程) 的服務獨立 GUID。</span><span class="sxs-lookup"><span data-stu-id="5097d-178">A service-independent GUID that identifies a service (for example, orchestration).</span></span>|  
|<span data-ttu-id="5097d-179">圖示</span><span class="sxs-lookup"><span data-stu-id="5097d-179">Icon</span></span>|<span data-ttu-id="5097d-180">結果列的圖示。</span><span class="sxs-lookup"><span data-stu-id="5097d-180">Icon of the result row.</span></span>|  
|<span data-ttu-id="5097d-181">配接器</span><span class="sxs-lookup"><span data-stu-id="5097d-181">Adapter</span></span>|<span data-ttu-id="5097d-182">作業使用的配接器。</span><span class="sxs-lookup"><span data-stu-id="5097d-182">Adapter used in the operation.</span></span>|