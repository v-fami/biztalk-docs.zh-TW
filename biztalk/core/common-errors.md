---
title: 常見的錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4fe48a8e-def0-4a00-aa7f-9a49ae555351
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b882c44e69489114a2dd8084df71d6414df0cb5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971532"
---
# <a name="common-errors"></a><span data-ttu-id="1610c-102">一般錯誤</span><span class="sxs-lookup"><span data-stu-id="1610c-102">Common Errors</span></span>
<span data-ttu-id="1610c-103">本主題列出使用 BizTalk 對應工具建立對應時可能會遇到的常見錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="1610c-103">This topic lists out common error messages you may encounter while creating maps using BizTalk Mapper.</span></span>  
  
## <a name="you-receive-error-event-id-324-when-parsing-dates"></a><span data-ttu-id="1610c-104">您在剖析日期時接收到錯誤事件識別碼 324。</span><span class="sxs-lookup"><span data-stu-id="1610c-104">You receive error event ID 324 when parsing dates</span></span>  
  
### <a name="problem"></a><span data-ttu-id="1610c-105">問題</span><span class="sxs-lookup"><span data-stu-id="1610c-105">Problem</span></span>  
 <span data-ttu-id="1610c-106">當您使用資料庫**值擷取程式 」** 運算質擷取日期欄位，您的文件引導模式中可能會針對輸出文件定義的驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="1610c-106">When you use the Database **Value Extractor** functoid in a map to extract a date field, your document may fail validation against the outbound document definition.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1610c-107">可能會記錄事件記錄檔中的驗證錯誤，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1610c-107"> may log a validation error similar to the following in the event log:</span></span>  
  
 <span data-ttu-id="1610c-108">事件來源： BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1610c-108">Event Source: BizTalk Server</span></span>  
  
 <span data-ttu-id="1610c-109">事件類別目錄： 文件處理</span><span class="sxs-lookup"><span data-stu-id="1610c-109">Event Category: Document Processing</span></span>  
  
 <span data-ttu-id="1610c-110">事件識別碼： 324</span><span class="sxs-lookup"><span data-stu-id="1610c-110">Event ID: 324</span></span>  
  
 <span data-ttu-id="1610c-111">描述：</span><span class="sxs-lookup"><span data-stu-id="1610c-111">Description:</span></span>  
  
 <span data-ttu-id="1610c-112">BizTalk Server 發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1610c-112">An error occurred in BizTalk Server.</span></span>  
  
 <span data-ttu-id="1610c-113">詳細資料：</span><span class="sxs-lookup"><span data-stu-id="1610c-113">Details:</span></span>  
  
 -----------------------------\-  
  
 <span data-ttu-id="1610c-114">XML 文件驗證因下列原因失敗： 錯誤剖析 '10/12/1995年' 為日期資料類型。</span><span class="sxs-lookup"><span data-stu-id="1610c-114">The XML document has failed validation for the following reason: Error parsing '10/12/1995' as date datatype.</span></span>  
  
 <span data-ttu-id="1610c-115">訊息擱置的佇列識別碼:"{A1127909-CA36-4359-B672-7CBA8B60BDAF}"</span><span class="sxs-lookup"><span data-stu-id="1610c-115">Suspended Queue ID: "{A1127909-CA36-4359-B672-7CBA8B60BDAF}"</span></span>  
  
### <a name="cause"></a><span data-ttu-id="1610c-116">原因</span><span class="sxs-lookup"><span data-stu-id="1610c-116">Cause</span></span>  
 <span data-ttu-id="1610c-117">日期格式 (由資料來源所傳回的格式) 不是 XML 所需要的 ISO 8601 格式。</span><span class="sxs-lookup"><span data-stu-id="1610c-117">The date format (as it is returned from the data source) is not in ISO 8601 format, which is the format required by XML.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="1610c-118">解決方案</span><span class="sxs-lookup"><span data-stu-id="1610c-118">Resolution</span></span>  
 <span data-ttu-id="1610c-119">若要解決這個問題，請執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="1610c-119">To resolve this issue, do one of the following:</span></span>  
  
-   <span data-ttu-id="1610c-120">編輯您的輸出文件定義以使用字串資料型別而非日期資料型別。</span><span class="sxs-lookup"><span data-stu-id="1610c-120">Edit your outbound document definition to use a string datatype instead of a date datatype.</span></span>  
  
-   <span data-ttu-id="1610c-121">建立自訂[!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsVBNoVersion](../includes/btsvbnoversion-md.md)]**指令碼**將資料庫的輸出轉換的運算質**值擷取程式 」** 成 ISO 8601 格式的運算質。</span><span class="sxs-lookup"><span data-stu-id="1610c-121">Create a custom [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsVBNoVersion](../includes/btsvbnoversion-md.md)]**Script** functoid that will convert the output of the Database **Value Extractor** functoid into the ISO 8601 format.</span></span>  
  
 <span data-ttu-id="1610c-122">如需詳細資訊，請參閱知識庫文章[278737](http://support.microsoft.com/kb/278737/en-us)。</span><span class="sxs-lookup"><span data-stu-id="1610c-122">For more information, see KB article [278737](http://support.microsoft.com/kb/278737/en-us).</span></span>  
  
## <a name="you-receive-internal-compiler-error-0xc0000005-at-address-53624fd6-when-compiling-the-maps"></a><span data-ttu-id="1610c-123">您在編譯對應時收到編譯器內部錯誤 (0xc0000005 於位址 53624FD6)</span><span class="sxs-lookup"><span data-stu-id="1610c-123">You receive Internal Compiler Error (0xc0000005 at address 53624FD6) when compiling the maps</span></span>  
  
### <a name="problem"></a><span data-ttu-id="1610c-124">問題</span><span class="sxs-lookup"><span data-stu-id="1610c-124">Problem</span></span>  
 <span data-ttu-id="1610c-125">當您編譯由大型結構描述、對應或協調流程所構成的單一 BizTalk 專案時，編譯器可能會產生如下錯誤：</span><span class="sxs-lookup"><span data-stu-id="1610c-125">When you compile a single BizTalk project that consists of large schemas, maps, or orchestrations, the compiler may generate an error similar to the following:</span></span>  
  
 <span data-ttu-id="1610c-126">編譯器內部錯誤 (0xc0000005 於位址 53624FD6): 可能的原因，是 'CODEGEN'。</span><span class="sxs-lookup"><span data-stu-id="1610c-126">Internal Compiler Error (0xc0000005 at address 53624FD6): likely culprit is 'CODEGEN'.</span></span>  
  
### <a name="cause"></a><span data-ttu-id="1610c-127">原因</span><span class="sxs-lookup"><span data-stu-id="1610c-127">Cause</span></span>  
 <span data-ttu-id="1610c-128">[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 編譯器在單一專案中，所有字串總大小的限制為 16 MB。</span><span class="sxs-lookup"><span data-stu-id="1610c-128">The [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] compiler has a 16-megabyte limitation on the total size of all strings in a single project.</span></span> <span data-ttu-id="1610c-129">在編譯 BizTalk 專案時，編譯器會序列化結構描述、對應和協調流程以建立組件，這樣便會增加所有字串的總大小，進而可能超過限制。</span><span class="sxs-lookup"><span data-stu-id="1610c-129">While compiling BizTalk projects, the compiler serializes schemas, maps, and orchestrations for creating the assemblies, and this increases the total size of all strings, which may exceed the limitation.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="1610c-130">解決方案</span><span class="sxs-lookup"><span data-stu-id="1610c-130">Resolution</span></span>  
 <span data-ttu-id="1610c-131">若要解決這個問題，您可以將結構描述或對應分散到不同的 BizTalk 專案中。</span><span class="sxs-lookup"><span data-stu-id="1610c-131">To resolve this issue, you can separate schemas or maps into different BizTalk projects.</span></span>  
  
## <a name="you-receive-errors-about-the-type-name-of-a-biztalk-artifact"></a><span data-ttu-id="1610c-132">您收到關於 BizTalk 成品類型名稱的錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="1610c-132">You receive errors about the Type Name of a BizTalk artifact</span></span>  
  
### <a name="problem"></a><span data-ttu-id="1610c-133">問題</span><span class="sxs-lookup"><span data-stu-id="1610c-133">Problem</span></span>  
 <span data-ttu-id="1610c-134">在 BizTalk 專案中，建立對應以檔名**System.btm**或**Microsoft.btm**。</span><span class="sxs-lookup"><span data-stu-id="1610c-134">In a BizTalk project, create a map with filename **System.btm** or **Microsoft.btm**.</span></span> <span data-ttu-id="1610c-135">當您建置專案時，BizTalk 對應工具產生類似下列任一項的錯誤：</span><span class="sxs-lookup"><span data-stu-id="1610c-135">When you build the project, the BizTalk Mapper generates an error similar to any of the following:</span></span>  
  
-   <span data-ttu-id="1610c-136">「類型名稱 'SerializableAttribute' 不存在...」</span><span class="sxs-lookup"><span data-stu-id="1610c-136">“The typename ‘SerializableAttribute’ does not exist…”</span></span>  
  
-   <span data-ttu-id="1610c-137">「類型名稱 'NonSerializableAttribute' 不存在...」</span><span class="sxs-lookup"><span data-stu-id="1610c-137">“The typename ‘NonSerializableAttribute’ does not exist…”</span></span>  
  
-   <span data-ttu-id="1610c-138">「類型名稱 'SerializableAttributeAttribute' 不存在...」</span><span class="sxs-lookup"><span data-stu-id="1610c-138">“The typename ‘SerializableAttributeAttribute’ does not exist…”</span></span>  
  
-   <span data-ttu-id="1610c-139">「類型名稱 'XLANs' 不存在...」</span><span class="sxs-lookup"><span data-stu-id="1610c-139">“The typename ‘XLANs’ does not exist…”</span></span>  
  
### <a name="cause"></a><span data-ttu-id="1610c-140">原因</span><span class="sxs-lookup"><span data-stu-id="1610c-140">Cause</span></span>  
 <span data-ttu-id="1610c-141">**型別名稱**中**屬性**方格不應有任何保留的.NET 命名空間，例如**系統**， **Microsoft**等等。</span><span class="sxs-lookup"><span data-stu-id="1610c-141">The **Type Name** in the **Properties** grid should not have any reserved .NET namespaces, such as **System**, **Microsoft**, etc.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="1610c-142">解決方案</span><span class="sxs-lookup"><span data-stu-id="1610c-142">Resolution</span></span>  
 <span data-ttu-id="1610c-143">若要解決此問題，您可以使用下列任一個因應措施：</span><span class="sxs-lookup"><span data-stu-id="1610c-143">To resolve this issue, you can follow any of these workarounds:</span></span>  
  
-   <span data-ttu-id="1610c-144">將對應的名稱修改成任一個非 .NET 保留字的字串。</span><span class="sxs-lookup"><span data-stu-id="1610c-144">Modify the name of the map to any string which is not a .NET reserved word.</span></span> <span data-ttu-id="1610c-145">根據預設，BizTalk 專案系統會建立**型別名稱**個別成品的名稱。</span><span class="sxs-lookup"><span data-stu-id="1610c-145">By default, the BizTalk project system creates the **Type Name** from the name of the respective artifact.</span></span>  
  
     <span data-ttu-id="1610c-146">針對如： 名稱建立新的對應**Map1.btm**設定**型別名稱**屬性值設定為**Map1**。</span><span class="sxs-lookup"><span data-stu-id="1610c-146">For e.g.: Creating a new map with name **Map1.btm** sets the **Type Name** property value to **Map1**.</span></span> <span data-ttu-id="1610c-147">不過，重新命名現有的 BizTalk 成品不會變更**型別名稱**。</span><span class="sxs-lookup"><span data-stu-id="1610c-147">However, renaming an existing BizTalk artifact does not change the **Type Name**.</span></span>  
  
-   <span data-ttu-id="1610c-148">確認 BizTalk 專案中所有成品的檔案名稱均不是保留的 .NET 命名空間。</span><span class="sxs-lookup"><span data-stu-id="1610c-148">Ensure the filename of any of the artifacts in the BizTalk project is not a .NET reserved namespace.</span></span>  
  
## <a name="you-receive-errors-about-the-file-name-of-a-biztalk-artifact"></a><span data-ttu-id="1610c-149">您收到關於 BizTalk 成品檔案名稱的錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="1610c-149">You receive errors about the File Name of a BizTalk artifact</span></span>  
  
### <a name="problem"></a><span data-ttu-id="1610c-150">問題</span><span class="sxs-lookup"><span data-stu-id="1610c-150">Problem</span></span>  
 <span data-ttu-id="1610c-151">當您欠至 BizTalk 專案時，BizTalk 對應工具產生類似下列任一項的錯誤：</span><span class="sxs-lookup"><span data-stu-id="1610c-151">When you build a BizTalk project, the BizTalk Mapper generates an error similar to any of the following:</span></span>  
  
-   <span data-ttu-id="1610c-152">「 檔案\<filename\>有重複的命名空間和類型名稱屬性的值。 」</span><span class="sxs-lookup"><span data-stu-id="1610c-152">“The File \<filename\> has duplicate values for namespace and type name properties.”</span></span>  
  
-   <span data-ttu-id="1610c-153">"命名空間\<名稱\>已經包含 '_' 的定義。 」</span><span class="sxs-lookup"><span data-stu-id="1610c-153">“The namespace \<name\> already contains a definition for ‘_’.”</span></span>  
  
### <a name="cause"></a><span data-ttu-id="1610c-154">原因</span><span class="sxs-lookup"><span data-stu-id="1610c-154">Cause</span></span>  
 <span data-ttu-id="1610c-155">在 BizTalk 專案中，檢查下列各項：</span><span class="sxs-lookup"><span data-stu-id="1610c-155">In the BizTalk project, check for the following:</span></span>  
  
-   <span data-ttu-id="1610c-156">是否有多個成品具有相同的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="1610c-156">Multiple artifacts have the same filename.</span></span> <span data-ttu-id="1610c-157">如例如**Map1.xsd**和**Map1.btm**。</span><span class="sxs-lookup"><span data-stu-id="1610c-157">For e.g., **Map1.xsd** and**Map1.btm**.</span></span>  
  
-   <span data-ttu-id="1610c-158">檔案名稱包含特殊字元只 (**~**， **！**，  **@** 等。)。</span><span class="sxs-lookup"><span data-stu-id="1610c-158">The filename comprises of only special characters (**~**, **!**, **@**, etc.).</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="1610c-159">解決方案</span><span class="sxs-lookup"><span data-stu-id="1610c-159">Resolution</span></span>  
 <span data-ttu-id="1610c-160">若要解決此問題，您可以使用下列任一個因應措施：</span><span class="sxs-lookup"><span data-stu-id="1610c-160">To resolve this issue, you can follow any of these workarounds:</span></span>  
  
-   <span data-ttu-id="1610c-161">重新命名檔案。</span><span class="sxs-lookup"><span data-stu-id="1610c-161">Rename the files.</span></span> <span data-ttu-id="1610c-162">確認 BizTalk 專案中所有成品的檔案名稱都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="1610c-162">Ensure the filenames for all artifacts in the BizTalk project are unique.</span></span>  
  
-   <span data-ttu-id="1610c-163">確認 BizTalk 專案中所有成品的類型名稱都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="1610c-163">Ensure Type Name for all artifacts in the BizTalk project are unique.</span></span>  
  
## <a name="building-any-c-workflow-project-with-biztalk-mapper-shows-a-warning-regarding-version-conflict-for-envdtedll"></a><span data-ttu-id="1610c-164">使用 BizTalk 對應工具建置任何 C# 工作流程專案時，會顯示關於 EnvDTE.dll 版本衝突的警告</span><span class="sxs-lookup"><span data-stu-id="1610c-164">Building any C# workflow project with BizTalk Mapper shows a warning regarding version conflict for EnvDTE.dll</span></span>  
  
### <a name="problem"></a><span data-ttu-id="1610c-165">問題</span><span class="sxs-lookup"><span data-stu-id="1610c-165">Problem</span></span>  
 <span data-ttu-id="1610c-166">使用 BizTalk 對應工具建置任何 C# 工作流程專案時，一律會顯示下列關於 EnvDTE.dll 版本衝突的警告。</span><span class="sxs-lookup"><span data-stu-id="1610c-166">Building any C# workflow project with BizTalk Mapper acitivity always shows the following warning about version conflict for EnvDTE.dll.</span></span>  
  
 <span data-ttu-id="1610c-167">沒有辦法解決 "EnvDTE，版本=8.0.0.0，文化特性=非語言相關，PublicKeyToken=b03f5f7f11d50a3a" 和 "EnvDTE，版本=7.0.3300.0，文化特性=非語言相關，PublicKeyToken=b03f5f7f11d50a3a" 之間的衝突。</span><span class="sxs-lookup"><span data-stu-id="1610c-167">No way to resolve conflict between "EnvDTE, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" and "EnvDTE, Version=7.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a".</span></span> <span data-ttu-id="1610c-168">選擇"EnvDTE，版本 = 8.0.0.0，Culture = neutral，PublicKeyToken = b03f5f7f11d50a3a"任意。</span><span class="sxs-lookup"><span data-stu-id="1610c-168">Choosing "EnvDTE, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" arbitrarily.</span></span>  <span data-ttu-id="1610c-169">App.config 重新對應組件，請考慮"EnvDTE，Culture = neutral，PublicKeyToken = b03f5f7f11d50a3a"從版本"7.0.3300.0"[] 版本 」 8.0.0.0"[C:\Program Files (x86) \Microsoft Visual Studio 10.0\Common7\IDE\PublicAssemblies\EnvDTE.dll]若要解決衝突，並移除警告。</span><span class="sxs-lookup"><span data-stu-id="1610c-169">Consider app.config remapping of assembly "EnvDTE, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" from Version "7.0.3300.0" [] to Version "8.0.0.0" [C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE\PublicAssemblies\EnvDTE.dll] to solve conflict and get rid of warning.</span></span> <span data-ttu-id="1610c-170">C:\Windows\Microsoft.NET\Framework\v4.0.30319\Microsoft.Common.targets(1360,9)： 警告 MSB3247： 同一個相依組件的不同版本之間發現衝突。</span><span class="sxs-lookup"><span data-stu-id="1610c-170">C:\Windows\Microsoft.NET\Framework\v4.0.30319\Microsoft.Common.targets(1360,9): warning MSB3247: Found conflicts between different versions of the same dependent assembly.</span></span>  
  
 <span data-ttu-id="1610c-171">WorkflowConsoleApplication3]-> [C:\Users\btslabs\Desktop\WorkflowConsoleApplication3\bin\Debug\WorkflowConsoleApplication3.exe</span><span class="sxs-lookup"><span data-stu-id="1610c-171">WorkflowConsoleApplication3 -> C:\Users\btslabs\Desktop\WorkflowConsoleApplication3\bin\Debug\WorkflowConsoleApplication3.exe</span></span>  
  
### <a name="cause"></a><span data-ttu-id="1610c-172">原因</span><span class="sxs-lookup"><span data-stu-id="1610c-172">Cause</span></span>  
 <span data-ttu-id="1610c-173">這是因為 Microsoft.BizTalk.Mapper.OM.dll 即在參考對應工具活動。</span><span class="sxs-lookup"><span data-stu-id="1610c-173">This happens because of the Microsoft.BizTalk.Mapper.OM.dll which the Mapper activity references.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="1610c-174">解決方案</span><span class="sxs-lookup"><span data-stu-id="1610c-174">Resolution</span></span>  
 <span data-ttu-id="1610c-175">忽略此警告。</span><span class="sxs-lookup"><span data-stu-id="1610c-175">Ignore the warning.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1610c-176">請參閱</span><span class="sxs-lookup"><span data-stu-id="1610c-176">See Also</span></span>  
 [<span data-ttu-id="1610c-177">地圖疑難排解</span><span class="sxs-lookup"><span data-stu-id="1610c-177">Troubleshooting Maps</span></span>](../core/troubleshooting-maps.md)