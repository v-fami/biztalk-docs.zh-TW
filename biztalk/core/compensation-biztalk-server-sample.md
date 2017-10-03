---
title: "補償 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- compensations, examples
- examples, compensations
- compensations, orchestrations
ms.assetid: 9d10c7be-6a4c-44cc-bf29-78ecdf147bd1
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7d3e2e917f9ac0cc09117f3de83bbcc6166af1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="compensation-biztalk-server-sample"></a><span data-ttu-id="dba27-102">補償 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="dba27-102">Compensation (BizTalk Server Sample)</span></span>
<span data-ttu-id="dba27-103">補償範例示範如何使用**補償**使用協調流程。</span><span class="sxs-lookup"><span data-stu-id="dba27-103">The Compensation sample demonstrates how to use the **Compensate** shape in an orchestration.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="dba27-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="dba27-104">What This Sample Does</span></span>  
 <span data-ttu-id="dba27-105">此範例示範如何使用下列步驟順序補償在協調流程中已認可的交易。</span><span class="sxs-lookup"><span data-stu-id="dba27-105">This sample demonstrates how to compensate the transaction that has already been committed in the orchestration using the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="dba27-106">在 InfoPath 表單中輸入客戶資料，然後將該資料提交到已公開為 Web 服務的協調流程。</span><span class="sxs-lookup"><span data-stu-id="dba27-106">Enter the customer data in the InfoPath form and submit the data to an orchestration that has been exposed as a Web service.</span></span>  
  
2.  <span data-ttu-id="dba27-107">協調流程有兩個平行的動作。</span><span class="sxs-lookup"><span data-stu-id="dba27-107">The orchestration has two parallel actions.</span></span> <span data-ttu-id="dba27-108">一個會傳回通知到 InfoPath 表單，另一個會更新 Northwind 和 BTSCompensationSampleMailingList 資料庫。</span><span class="sxs-lookup"><span data-stu-id="dba27-108">One returns an acknowledgment to the InfoPath form and the other updates the Northwind and BTSCompensationSampleMailingList databases.</span></span>  
  
3.  <span data-ttu-id="dba27-109">在第二個動作中，協調流程會將內送訊息對應至客戶關係管理 (CRM) 應用程式訊息格式，然後更新**客戶**Northwind 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="dba27-109">In the second action, the orchestration maps the incoming message to a customer relationship management (CRM) application message format and then updates the **Customers** table in the Northwind database.</span></span> <span data-ttu-id="dba27-110">這個動作完成後，BTSCompensationSampleMailingList 資料庫中的「郵寄清單」資料表就會更新。</span><span class="sxs-lookup"><span data-stu-id="dba27-110">After this, the Mailing List table in the BTSCompensationSampleMailingList database is updated.</span></span>  
  
4.  <span data-ttu-id="dba27-111">如果這兩項更新其中一項失敗，就會呼叫外部組件將原始客戶資料寫回資料庫，來補償對 Northwind 資料庫所做的變更。</span><span class="sxs-lookup"><span data-stu-id="dba27-111">If either update fails, the changes made to the Northwind database are compensated by calling an external assembly to write the original customer data back to the database.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="dba27-112">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="dba27-112">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="dba27-113">A**範圍**圖形主要用於交易執行以及例外狀況處理，包括補償。</span><span class="sxs-lookup"><span data-stu-id="dba27-113">A **Scope** shape is primarily used for transactional execution and exception handling, including compensation.</span></span> <span data-ttu-id="dba27-114">範圍由兩個區塊組成。</span><span class="sxs-lookup"><span data-stu-id="dba27-114">A scope consists of two blocks.</span></span> <span data-ttu-id="dba27-115">第一個區塊是內容區塊，而第二個區塊可以是一或多個例外狀況處理或補償區塊。</span><span class="sxs-lookup"><span data-stu-id="dba27-115">The first block is the context block and the second block can be one or more exception-handling or compensation blocks.</span></span> <span data-ttu-id="dba27-116">這和 .NET 程式設計語言中的 try-catch 陳述式相似。</span><span class="sxs-lookup"><span data-stu-id="dba27-116">This is similar to the try-catch statement in the .NET programming language.</span></span> <span data-ttu-id="dba27-117">在 UpdateContact.odx 協調流程中，有兩個平行的動作。</span><span class="sxs-lookup"><span data-stu-id="dba27-117">In the UpdateContact.odx orchestration, there are two parallel actions.</span></span> <span data-ttu-id="dba27-118">在右邊的分支中，是在 try 區塊**範圍**圖形名為更新後端系統有長時間執行的交易類型以及 Upd_Backend 交易識別項。</span><span class="sxs-lookup"><span data-stu-id="dba27-118">At the right-side branch, the try block is the **Scope** shape named Updated Backend Systems, which has a Long-Running transaction type and an Upd_Backend transaction identifier.</span></span> <span data-ttu-id="dba27-119">在接下來的流程中，有一個 Catch 區塊，可取得一般例外狀況，並初始化補償。</span><span class="sxs-lookup"><span data-stu-id="dba27-119">Further down in the flow, there is a catch block that catches the general exception and initiates the compensation.</span></span>  
  
 <span data-ttu-id="dba27-120">如需有關**範圍**圖形，請參閱[範圍](../core/scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="dba27-120">For more information about the **Scope** shape, see [Scopes](../core/scopes.md).</span></span> <span data-ttu-id="dba27-121">另請參閱[如何設定 「 範圍 」 圖形](../core/how-to-configure-the-scope-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="dba27-121">Also see [How to Configure the Scope Shape](../core/how-to-configure-the-scope-shape.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dba27-122">協調流程本身必須為長時間執行的交易，您才能將交易類型設為「不可部分完成」或是「長時間執行」。</span><span class="sxs-lookup"><span data-stu-id="dba27-122">The orchestration must itself be a long-running transaction for you to set the transaction type to Atomic or Long-Running.</span></span>  
  
 <span data-ttu-id="dba27-123">在 try 區塊中，有兩個範圍，名為**更新 CRM**和**更新郵件**。</span><span class="sxs-lookup"><span data-stu-id="dba27-123">In the try block, there are two scopes named **Update CRM** and **Update Mailing**.</span></span> <span data-ttu-id="dba27-124">這兩個範圍都是不可部分完成的交易。</span><span class="sxs-lookup"><span data-stu-id="dba27-124">Both of these scopes are atomic transactions.</span></span> <span data-ttu-id="dba27-125">在「更新 CRM」範圍中，有 try 區塊和補償區塊。</span><span class="sxs-lookup"><span data-stu-id="dba27-125">In the Update CRM scope, there is a try block and a compensation block.</span></span> <span data-ttu-id="dba27-126">try 區塊會透過對外部組件的方法呼叫來更新 Northwind 資料庫。</span><span class="sxs-lookup"><span data-stu-id="dba27-126">The try block updates the Northwind database through a method call to an external assembly.</span></span> <span data-ttu-id="dba27-127">補償區塊是補償動作發生的地方。</span><span class="sxs-lookup"><span data-stu-id="dba27-127">The compensation block is where the compensation action takes place.</span></span> <span data-ttu-id="dba27-128">當「更新後端系統」範圍中發生例外狀況時，「復原 CRM 運算式」圖形會將記錄更新回其原始狀態。</span><span class="sxs-lookup"><span data-stu-id="dba27-128">When an exception happens in the Update Backend Systems scope, the code in Undo CRM Expression Shape updates the record back to its original state.</span></span> <span data-ttu-id="dba27-129">這由觸發**補償**Catch 例外狀況區塊中的圖形。</span><span class="sxs-lookup"><span data-stu-id="dba27-129">This is triggered by the **Compensate** shape in the Catch Exception block.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dba27-130">不可部分完成的交易可保證任何部分更新在交易更新期間作業失敗時都會自動復原，且會清除交易的結果 (在交易中進行的任何 .NET 呼叫結果除外)。</span><span class="sxs-lookup"><span data-stu-id="dba27-130">Atomic transactions guarantee that any partial updates are rolled back automatically in the event of a failure during the transactional update, and that the effects of the transaction are erased (except for the effects of any .NET calls that are made in the transaction).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dba27-131">當長時間執行的交易中的最後一個陳述式完成時，該交易就會被視為已認可。</span><span class="sxs-lookup"><span data-stu-id="dba27-131">A long-running transaction is considered committed when the last statement in it has completed.</span></span> <span data-ttu-id="dba27-132">在交易中止的情況下不會自動回復狀態。</span><span class="sxs-lookup"><span data-stu-id="dba27-132">There is no automatic rollback of state in case of a transaction abort.</span></span> <span data-ttu-id="dba27-133">您可透過此範例中示範的例外狀況和補償處理常式以程式設計方式達到這個結果。</span><span class="sxs-lookup"><span data-stu-id="dba27-133">You can achieve this programmatically through the exception and compensation handlers demonstrated in this sample.</span></span>  
  
 <span data-ttu-id="dba27-134">在 catch 區塊中，有一個**延遲**圖形設定為 10 秒。</span><span class="sxs-lookup"><span data-stu-id="dba27-134">In the catch block, there is one **Delay** shape set for ten seconds.</span></span> <span data-ttu-id="dba27-135">這會延遲補償動作。</span><span class="sxs-lookup"><span data-stu-id="dba27-135">This delays the compensation action.</span></span> <span data-ttu-id="dba27-136">另外還有**補償**初始化 Upd_Backend 交易的補償動作的圖形。</span><span class="sxs-lookup"><span data-stu-id="dba27-136">There is also a **Compensate** shape that initiates the compensation action in the Upd_Backend transaction.</span></span>  
  
 <span data-ttu-id="dba27-137">下列動作會在協調流程收到輸入訊息後發生：</span><span class="sxs-lookup"><span data-stu-id="dba27-137">The following happens after the orchestration receives the input message:</span></span>  
  
1.  <span data-ttu-id="dba27-138">UpdateCrm 組件會更新 Northwind 資料庫中的資料列。</span><span class="sxs-lookup"><span data-stu-id="dba27-138">The UpdateCrm assembly updates a row in the Northwind database.</span></span>  
  
2.  <span data-ttu-id="dba27-139">UpdateMailingList 組件會更新 BTSCompensationSampleMailingList 資料庫中的相符記錄。</span><span class="sxs-lookup"><span data-stu-id="dba27-139">The UpdateMailingList assembly updates a matching record in the BTSCompensationSampleMailingList database.</span></span>  
  
3.  <span data-ttu-id="dba27-140">在更新 Northwind 資料庫時若作業失敗，會引發例外狀況，且協調流程會結束此程序。</span><span class="sxs-lookup"><span data-stu-id="dba27-140">In the event of a failure while updating the Northwind database, an exception is raised and the orchestration exits the process.</span></span>  
  
4.  <span data-ttu-id="dba27-141">在更新 BTSCompensationSampleMailingList 資料庫時若作業失敗，會引發例外狀況，且在將原始客戶資料重新寫回 Northwind 資料庫之前，每十秒會產生一次延遲。</span><span class="sxs-lookup"><span data-stu-id="dba27-141">In the event of a failure while updating the BTSCompensationSampleMailingList database, an exception is raised and a ten-second delay takes place before rewriting the original customer data back to the Northwind database.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="dba27-142">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="dba27-142">Where to Find This Sample</span></span>  
 <span data-ttu-id="dba27-143">\<*範例路徑*> \Orchestrations\Compensation\\</span><span class="sxs-lookup"><span data-stu-id="dba27-143">\<*Samples Path*>\Orchestrations\Compensation\\</span></span>  
  
 <span data-ttu-id="dba27-144">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="dba27-144">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="dba27-145">檔案</span><span class="sxs-lookup"><span data-stu-id="dba27-145">File(s)</span></span>|<span data-ttu-id="dba27-146">Description</span><span class="sxs-lookup"><span data-stu-id="dba27-146">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dba27-147">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="dba27-147">Cleanup.bat</span></span>|<span data-ttu-id="dba27-148">用來解除安裝範例的批次檔案。</span><span class="sxs-lookup"><span data-stu-id="dba27-148">Batch file used to uninstall the sample.</span></span>|  
|<span data-ttu-id="dba27-149">CompensationOrchestration.btproj</span><span class="sxs-lookup"><span data-stu-id="dba27-149">CompensationOrchestration.btproj</span></span>|<span data-ttu-id="dba27-150">協調流程專案。</span><span class="sxs-lookup"><span data-stu-id="dba27-150">Orchestration project.</span></span>|  
|<span data-ttu-id="dba27-151">CompensationSample.sln</span><span class="sxs-lookup"><span data-stu-id="dba27-151">CompensationSample.sln</span></span>|<span data-ttu-id="dba27-152">範例方案。</span><span class="sxs-lookup"><span data-stu-id="dba27-152">Sample solution.</span></span>|  
|<span data-ttu-id="dba27-153">CompensationSampleBinding.xml</span><span class="sxs-lookup"><span data-stu-id="dba27-153">CompensationSampleBinding.xml</span></span>|<span data-ttu-id="dba27-154">繫結協調流程的資料 (用於安裝期間)。</span><span class="sxs-lookup"><span data-stu-id="dba27-154">Binding data for the orchestration (used during installation).</span></span>|  
|<span data-ttu-id="dba27-155">ContactInfo.xsd</span><span class="sxs-lookup"><span data-stu-id="dba27-155">ContactInfo.xsd</span></span>|<span data-ttu-id="dba27-156">連絡人資訊訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="dba27-156">Contact information message schema.</span></span>|  
|<span data-ttu-id="dba27-157">ContactInfo.xsx</span><span class="sxs-lookup"><span data-stu-id="dba27-157">ContactInfo.xsx</span></span>|<span data-ttu-id="dba27-158">協調流程設計師配置檔案。</span><span class="sxs-lookup"><span data-stu-id="dba27-158">Orchestration Designer layout file.</span></span>|  
|<span data-ttu-id="dba27-159">CreateSQLDataStore.sql</span><span class="sxs-lookup"><span data-stu-id="dba27-159">CreateSQLDataStore.sql</span></span>|<span data-ttu-id="dba27-160">建立和填入範例資料庫的 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="dba27-160">SQL script to create and populate the sample database.</span></span>|  
|<span data-ttu-id="dba27-161">CrmSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="dba27-161">CrmSchema.xsd</span></span>|<span data-ttu-id="dba27-162">CRM 更新訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="dba27-162">CRM update message schema.</span></span>|  
|<span data-ttu-id="dba27-163">MailingListSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="dba27-163">MailingListSchema.xsd</span></span>|<span data-ttu-id="dba27-164">郵件清單訊息更新結構描述。</span><span class="sxs-lookup"><span data-stu-id="dba27-164">Mailing list message update schema.</span></span>|  
|<span data-ttu-id="dba27-165">RemoveVirDir.vbs</span><span class="sxs-lookup"><span data-stu-id="dba27-165">RemoveVirDir.vbs</span></span>|<span data-ttu-id="dba27-166">Microsoft Visual Basic Scripting Edition (VBScript) 指令碼，可移除 Web 服務虛擬和實體目錄 (用於解除安裝期間)。</span><span class="sxs-lookup"><span data-stu-id="dba27-166">Microsoft Visual Basic Scripting Edition (VBScript) script to remove Web service virtual and physical directories (used during uninstallation).</span></span>|  
|<span data-ttu-id="dba27-167">Request2Crm.btm</span><span class="sxs-lookup"><span data-stu-id="dba27-167">Request2Crm.btm</span></span>|<span data-ttu-id="dba27-168">從要求 (連絡人資訊) 解譯到 CRM 更新訊息的訊息對應。</span><span class="sxs-lookup"><span data-stu-id="dba27-168">Message map to translate from request (contact info) to CRM update message.</span></span>|  
|<span data-ttu-id="dba27-169">Request2MailingList.btm</span><span class="sxs-lookup"><span data-stu-id="dba27-169">Request2MailingList.btm</span></span>|<span data-ttu-id="dba27-170">從要求 (連絡人資訊) 解譯到郵件清單資訊的訊息對應。</span><span class="sxs-lookup"><span data-stu-id="dba27-170">Message map to translate from request (contact info) to mailing list message.</span></span>|  
|<span data-ttu-id="dba27-171">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="dba27-171">Setup.bat</span></span>|<span data-ttu-id="dba27-172">安裝此範例的批次檔案。</span><span class="sxs-lookup"><span data-stu-id="dba27-172">Batch file to install this sample.</span></span>|  
|<span data-ttu-id="dba27-173">UpdateContact.odx</span><span class="sxs-lookup"><span data-stu-id="dba27-173">UpdateContact.odx</span></span>|<span data-ttu-id="dba27-174">協調流程檔案。</span><span class="sxs-lookup"><span data-stu-id="dba27-174">Orchestration file.</span></span>|  
|<span data-ttu-id="dba27-175">UpdateRequest2UpdateResponse.btm</span><span class="sxs-lookup"><span data-stu-id="dba27-175">UpdateRequest2UpdateResponse.btm</span></span>|<span data-ttu-id="dba27-176">從要求 (連絡人資訊) 解譯到回應訊息的訊息對應。</span><span class="sxs-lookup"><span data-stu-id="dba27-176">Message map to translate from request (contact info) to a response message.</span></span>|  
|<span data-ttu-id="dba27-177">UpdateResponse.xsd</span><span class="sxs-lookup"><span data-stu-id="dba27-177">UpdateResponse.xsd</span></span>|<span data-ttu-id="dba27-178">回應訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="dba27-178">Response message schema.</span></span>|  
|<span data-ttu-id="dba27-179">InfoPath\Contact Info Update.xsn</span><span class="sxs-lookup"><span data-stu-id="dba27-179">InfoPath\Contact Info Update.xsn</span></span>|<span data-ttu-id="dba27-180">用來提交表單至協調流程 Web 服務的 Microsoft InfoPath 檔案。</span><span class="sxs-lookup"><span data-stu-id="dba27-180">Microsoft InfoPath file used to submit forms to the orchestration Web service.</span></span>|  
|<span data-ttu-id="dba27-181">UpdateCrm\AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="dba27-181">UpdateCrm\AssemblyInfo.cs</span></span>|<span data-ttu-id="dba27-182">UpdateCrm 組件的組件資訊來源檔案。</span><span class="sxs-lookup"><span data-stu-id="dba27-182">Assembly information source file for the UpdateCrm assembly.</span></span> <span data-ttu-id="dba27-183">(UpdateCrm 組件會更新 Northwind 資料庫。)</span><span class="sxs-lookup"><span data-stu-id="dba27-183">(The UpdateCrm assembly updates the Northwind database.)</span></span>|  
|<span data-ttu-id="dba27-184">UpdateCrm\UpdateCrm.cs</span><span class="sxs-lookup"><span data-stu-id="dba27-184">UpdateCrm\UpdateCrm.cs</span></span>|<span data-ttu-id="dba27-185">UpdateCrm 組件的主要原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="dba27-185">Main source code for the UpdateCrm assembly.</span></span>|  
|<span data-ttu-id="dba27-186">UpdateCrm\UpdateCRM.csproj</span><span class="sxs-lookup"><span data-stu-id="dba27-186">UpdateCrm\UpdateCRM.csproj</span></span>|<span data-ttu-id="dba27-187">UpdateCrm 專案檔。</span><span class="sxs-lookup"><span data-stu-id="dba27-187">UpdateCrm project file.</span></span>|  
|<span data-ttu-id="dba27-188">UpdateMailingList\AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="dba27-188">UpdateMailingList\AssemblyInfo.cs</span></span>|<span data-ttu-id="dba27-189">UpdateMailingList 組件的組件資訊來源檔案。</span><span class="sxs-lookup"><span data-stu-id="dba27-189">Assembly information source file for the UpdateMailingList assembly.</span></span> <span data-ttu-id="dba27-190">(UpdateMailingList 組件會更新範例資料庫。)</span><span class="sxs-lookup"><span data-stu-id="dba27-190">(The UpdateMailingList assembly updates the sample database.)</span></span>|  
|<span data-ttu-id="dba27-191">UpdateMailingList\UpdateMailingList.cs</span><span class="sxs-lookup"><span data-stu-id="dba27-191">UpdateMailingList\UpdateMailingList.cs</span></span>|<span data-ttu-id="dba27-192">UpdateMailingList 組件的主要原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="dba27-192">Main source code for the UpdateMailingList assembly.</span></span>|  
|<span data-ttu-id="dba27-193">UpdateMailingList\UpdateMailingList.csproj</span><span class="sxs-lookup"><span data-stu-id="dba27-193">UpdateMailingList\UpdateMailingList.csproj</span></span>|<span data-ttu-id="dba27-194">UpdateMailingList 專案檔案。</span><span class="sxs-lookup"><span data-stu-id="dba27-194">UpdateMailingList project file.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="dba27-195">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="dba27-195">Building and Initializing This Sample</span></span>  
  
#### <a name="to-build-and-initialize-the-compensation-sample"></a><span data-ttu-id="dba27-196">建置和初始化補償範例</span><span class="sxs-lookup"><span data-stu-id="dba27-196">To build and initialize the Compensation sample</span></span>  
  
1.  <span data-ttu-id="dba27-197">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="dba27-197">In a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="dba27-198">\<*範例路徑*> \Orchestrations\Compensation\\</span><span class="sxs-lookup"><span data-stu-id="dba27-198">\<*Samples Path*>\Orchestrations\Compensation\\</span></span>  
  
2.  <span data-ttu-id="dba27-199">執行 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="dba27-199">Run Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="dba27-200">建置和部署範例組件。</span><span class="sxs-lookup"><span data-stu-id="dba27-200">Build and deploy the sample assembly.</span></span>  
  
    -   <span data-ttu-id="dba27-201">當 BizTalk Web 服務發佈精靈啟動時，請手動執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="dba27-201">When the BizTalk Web Services Publishing Wizard launches, do the following manually:</span></span>  
  
    1.  <span data-ttu-id="dba27-202">在**歡迎使用 BizTalk Web 服務發佈精靈**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dba27-202">On the **Welcome to the BizTalk Web Services Publishing Wizard** page, click **Next**.</span></span>  
  
    2.  <span data-ttu-id="dba27-203">在**建立 Web 服務**頁面上，選取**BizTalk 協調流程發佈為 web 服務**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="dba27-203">On the **Create Web Service** page, select **Publish BizTalk orchestration as web services**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="dba27-204">在**BizTalk 組件**頁面上，瀏覽並選取\<*範例路徑*> \Orchestrations\Compensation\bin\Release\CompensationOrchestration.dll，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dba27-204">On the **BizTalk Assembly** page, browse and select \<*Samples Path*>\Orchestrations\Compensation\bin\Release\CompensationOrchestration.dll, and then click **Next**.</span></span>  
  
    4.  <span data-ttu-id="dba27-205">在**協調流程和連接埠**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dba27-205">On the **Orchestrations and Ports** page, click **Next**.</span></span>  
  
    5.  <span data-ttu-id="dba27-206">在**Web 服務屬性**頁面上，於**web 服務目標命名空間**，型別**http://Microsoft.BizTalk.Samples.Compensation/**，然後按一下  **下一步**。</span><span class="sxs-lookup"><span data-stu-id="dba27-206">On the **Web Service Properties** page, in **Target namespace of web service**, type **http://Microsoft.BizTalk.Samples.Compensation/**, and then click **Next**.</span></span>  
  
    6.  <span data-ttu-id="dba27-207">在**Web 服務專案**頁面上，於**位置**，型別**http://localhost/CompensationOrchestrationWebServiceProxy**。</span><span class="sxs-lookup"><span data-stu-id="dba27-207">On the **Web Service Project** page, in **Location**, type **http://localhost/CompensationOrchestrationWebServiceProxy**.</span></span>  
  
    7.  <span data-ttu-id="dba27-208">選取**允許匿名存取 web 服務**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="dba27-208">Select the **Allow anonymous access to web service** check box.</span></span>  
  
    8.  <span data-ttu-id="dba27-209">選取**建立 BizTalk 接收位置，在下列應用程式中**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="dba27-209">Select the **Create BizTalk receive location in the following application** check box.</span></span>  
  
    9. <span data-ttu-id="dba27-210">在**建立 BizTalk 接收位置，在下列應用程式中**下拉式選單中，選取**BizTalk Application 1**從下拉式清單，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dba27-210">In the **Create BizTalk receive location in the following application** drop-down menu, select **BizTalk Application 1** from the drop-down list, and then click **Next**.</span></span>  
  
    10. <span data-ttu-id="dba27-211">在**Web 服務專案摘要**頁面上，按一下**建立**。</span><span class="sxs-lookup"><span data-stu-id="dba27-211">On the **Web Service Project Summary** page, click **Create**.</span></span>  
  
    11. <span data-ttu-id="dba27-212">在**完成 BizTalk Web 服務發佈精靈**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="dba27-212">On the **Completing the BizTalk Web Services Publishing Wizard** page, click **Finish**.</span></span>  
  
3.  <span data-ttu-id="dba27-213">安裝程式會建立和繫結連接埠、建立此範例的後端資料庫，並新增 C# 組件至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="dba27-213">Setup creates and binds ports, creates the back-end database for the sample, and adds C# assemblies to the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dba27-214">在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="dba27-214">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="dba27-215">執行此範例</span><span class="sxs-lookup"><span data-stu-id="dba27-215">Running This Sample</span></span>  
 <span data-ttu-id="dba27-216">建置和初始化此範例後，請考慮下列事項後再執行它：</span><span class="sxs-lookup"><span data-stu-id="dba27-216">After you build and initialize this sample, consider the following before you run it:</span></span>  
  
-   <span data-ttu-id="dba27-217">如果您執行此範例[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]，您必須建立 IIS 應用程式集區，並將其識別為屬於 BizTalk 應用程式使用者 Windows 群組成員的帳戶。</span><span class="sxs-lookup"><span data-stu-id="dba27-217">If you are running this sample on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], you must create an IIS application pool and set its identity to an account that is a member of the BizTalk Application Users Windows group.</span></span> <span data-ttu-id="dba27-218">此外，您需要更新協調流程 Web 服務虛擬目錄，才可在此應用程式集區中執行。</span><span class="sxs-lookup"><span data-stu-id="dba27-218">You also need to update the orchestration Web service virtual directory to run within this application pool.</span></span>  
  
-   <span data-ttu-id="dba27-219">將 ASPNET 帳戶新增至 BizTalk 外掛式主控件使用者群組。</span><span class="sxs-lookup"><span data-stu-id="dba27-219">Add the ASPNET account to the BizTalk Isolated Host Users group.</span></span>  
  
-   <span data-ttu-id="dba27-220">授與 BizTalk 應用程式使用者群組 db_owner 權限**BTSCompensationSampleMailingList**和**Northwind**資料庫。</span><span class="sxs-lookup"><span data-stu-id="dba27-220">Give the BizTalk Application Users group db_owner permission to the **BTSCompensationSampleMailingList** and **Northwind** databases.</span></span>  
  
-   <span data-ttu-id="dba27-221">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]未安裝在預設位置 (磁碟機： files\microsoft BizTalk Server\<版本 >\\)，您必須發佈 Contact Info Update.xsn 表單後才能使用它。</span><span class="sxs-lookup"><span data-stu-id="dba27-221">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is not installed in the default location (drive:\Program Files\Microsoft BizTalk Server \<version>\\), you must publish the Contact Info Update.xsn form before using it.</span></span> <span data-ttu-id="dba27-222">若要這樣做，請執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="dba27-222">To do so, do the following.</span></span>  
  
    #### <a name="to-publish-the-infopath-form"></a><span data-ttu-id="dba27-223">若要發佈 InfoPath 表單</span><span class="sxs-lookup"><span data-stu-id="dba27-223">To publish the InfoPath form</span></span>  
  
    1.  <span data-ttu-id="dba27-224">在 Internet Explorer 上**工具**功能表上，按一下 **網際網路選項**。</span><span class="sxs-lookup"><span data-stu-id="dba27-224">In Internet Explorer, on the **Tools** menu, click **Internet Options**.</span></span>  
  
    2.  <span data-ttu-id="dba27-225">在**安全性**索引標籤上，按一下 **網際網路**，然後按一下 **自訂層級**。</span><span class="sxs-lookup"><span data-stu-id="dba27-225">On the **Security** tab, click **Internet**, and then click **Custom Level**.</span></span>  
  
    3.  <span data-ttu-id="dba27-226">在**其他**區段中，確定**跨網域存取資料來源**設定已啟用，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="dba27-226">In the **Miscellaneous** section, ensure that the **Access data sources across domains** setting is enabled, and then click **OK**.</span></span> <span data-ttu-id="dba27-227">需要有此設定 InfoPath 使用者介面方案指令碼處理程式碼才能執行。</span><span class="sxs-lookup"><span data-stu-id="dba27-227">This setting is required for the InfoPath user interface solution scripting code to run.</span></span>  
  
    4.  <span data-ttu-id="dba27-228">在 Windows 檔案總管，瀏覽至\<*範例路徑*> \Orchestrations\Compensation\InfoPath，以滑鼠右鍵按一下**Contact Info Update.xsn** ，然後按一下 **設計**.</span><span class="sxs-lookup"><span data-stu-id="dba27-228">In Windows Explorer, navigate to \<*Samples Path*>\Orchestrations\Compensation\InfoPath, right-click **Contact Info Update.xsn** and then click **Design**.</span></span>  
  
    5.  <span data-ttu-id="dba27-229">InfoPath Contact Info Update 方案就會以設計模式開啟。</span><span class="sxs-lookup"><span data-stu-id="dba27-229">The InfoPath Contact Info Update solution opens in design mode.</span></span>  
  
    6.  <span data-ttu-id="dba27-230">在 InfoPath Contact Info Update 應用程式上**檔案**功能表上，按一下 **發行**。</span><span class="sxs-lookup"><span data-stu-id="dba27-230">In the InfoPath Contact Info Update application, on the **File** menu, click **Publish**.</span></span>  
  
    7.  <span data-ttu-id="dba27-231">會顯示 [組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="dba27-231">The Publish Wizard appears.</span></span>  
  
    8.  <span data-ttu-id="dba27-232">選取**到此電腦上或在網路上的共用資料夾**及發佈方案至路徑\<*範例路徑*> \Orchestrations\Compensation\InfoPath\Contact Info Update.xsn。</span><span class="sxs-lookup"><span data-stu-id="dba27-232">Select **To a shared folder on this computer or on a network** and publish the solution to the path \<*Samples Path*>\Orchestrations\Compensation\InfoPath\Contact Info Update.xsn.</span></span>  
  
    9. <span data-ttu-id="dba27-233">關閉設計模式 InfoPath。</span><span class="sxs-lookup"><span data-stu-id="dba27-233">Close the design mode InfoPath.</span></span>  
  
-   <span data-ttu-id="dba27-234">您已準備好執行這個範例。</span><span class="sxs-lookup"><span data-stu-id="dba27-234">You are ready to run this sample.</span></span>  
  
    #### <a name="to-run-the-compensation-sample"></a><span data-ttu-id="dba27-235">若要執行補償範例</span><span class="sxs-lookup"><span data-stu-id="dba27-235">To run the Compensation sample</span></span>  
  
    1.  <span data-ttu-id="dba27-236">按兩下**Contact Info Update.xsn**在 InfoPath 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="dba27-236">Double-click **Contact Info Update.xsn** to open it in InfoPath.</span></span>  
  
    2.  <span data-ttu-id="dba27-237">為同時存在這兩個資料庫中的帳戶填寫表單。</span><span class="sxs-lookup"><span data-stu-id="dba27-237">Fill out the form for an account that exists in both databases.</span></span> <span data-ttu-id="dba27-238">例如，使用 Northwind Customers 資料表內的現有帳戶識別碼 "ALFKI"。</span><span class="sxs-lookup"><span data-stu-id="dba27-238">For example, use an existing account ID "ALFKI" from the Northwind Customers table.</span></span>  
  
    3.  <span data-ttu-id="dba27-239">在**檔案**功能表上，選取**送出**，然後按一下**送出**。</span><span class="sxs-lookup"><span data-stu-id="dba27-239">On the **File** menu, select **Submit**, and click **Submit**.</span></span>  
  
    4.  <span data-ttu-id="dba27-240">回應文件應該會出現在\<*範例路徑*> \Orchestrations\Compensation\Out 資料夾，而 Northwind 和 BTSCompensationSampleMailingList 資料庫應與新更新InfoPath 表單中的資料。</span><span class="sxs-lookup"><span data-stu-id="dba27-240">The response document should appear in the \<*Samples Path*>\Orchestrations\Compensation\Out folder, and both the Northwind and the BTSCompensationSampleMailingList databases should be updated with the new data from the InfoPath form.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="dba27-241">您可以中斷連線 BTSCompensationSampleMailingList 資料庫或讓它離線，以測試協調流程所執行的補償動作。</span><span class="sxs-lookup"><span data-stu-id="dba27-241">You can detach the BTSCompensationSampleMailingList database or take it offline to test the compensation action that the orchestration performs.</span></span> <span data-ttu-id="dba27-242">請注意，會先更新 Northwind 資料庫內的記錄。</span><span class="sxs-lookup"><span data-stu-id="dba27-242">Observe that the record is updated in the Northwind database first.</span></span> <span data-ttu-id="dba27-243">接著，協調流程嘗試更新 BTSCompensationSampleMailingList 資料庫會失敗，因為該資料庫已中斷連線。</span><span class="sxs-lookup"><span data-stu-id="dba27-243">Then, when the orchestration tries to update the BTSCompensationSampleMailingList database, because that database is detached, the update fails.</span></span> <span data-ttu-id="dba27-244">因此會引發例外狀況，而且在補償動作開始將原始客戶資料寫回 Northwind 資料庫之前，會產生十秒延遲。</span><span class="sxs-lookup"><span data-stu-id="dba27-244">Therefore, an exception is raised and there is a ten-second delay before the compensation action takes place to write the original customer data back to the Northwind database.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="dba27-245">您可能會得到「使用者 'IIS APPPOOL\DefaultAppPool' 的登入失敗」錯誤。</span><span class="sxs-lookup"><span data-stu-id="dba27-245">You may get a "Login failed for user 'IIS APPPOOL\DefaultAppPool' error.</span></span> <span data-ttu-id="dba27-246">這可能是因為以權杖為基礎的伺服器存取驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="dba27-246">It might be because of the token-based server access validation failure.</span></span> <span data-ttu-id="dba27-247">若要解決這個錯誤，請建立新的應用程式集區，並在其中使用系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="dba27-247">To resolve this error, create a new application pool and use the administrator account in it.</span></span>  
  
## <a name="uninstalling-this-sample"></a><span data-ttu-id="dba27-248">解除安裝這個範例</span><span class="sxs-lookup"><span data-stu-id="dba27-248">Uninstalling This Sample</span></span>  
  
#### <a name="to-uninstall-the-compensation-sample"></a><span data-ttu-id="dba27-249">解除安裝補償範例</span><span class="sxs-lookup"><span data-stu-id="dba27-249">To uninstall the Compensation sample</span></span>  
  
1.  <span data-ttu-id="dba27-250">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="dba27-250">In a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="dba27-251">\<*範例路徑*> \Orchestrations\Compensation\\</span><span class="sxs-lookup"><span data-stu-id="dba27-251">\<*Samples Path*>\Orchestrations\Compensation\\</span></span>  
  
2.  <span data-ttu-id="dba27-252">執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="dba27-252">Run Cleanup.bat.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba27-253">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dba27-253">See Also</span></span>  
 [<span data-ttu-id="dba27-254">協調流程 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="dba27-254">Orchestrations (BizTalk Server Samples Folder)</span></span>](../core/orchestrations-biztalk-server-samples-folder.md)