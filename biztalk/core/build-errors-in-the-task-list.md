---
title: "工作清單中的建置錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- building, errors
- errors, building
ms.assetid: 05b36511-3031-4e13-ac2f-bfdbec0f48cb
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1bfd5b9f7b974b00d63831484ecbaa44e2568fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="build-errors-in-the-task-list"></a><span data-ttu-id="c50e7-102">建置工作清單中的錯誤</span><span class="sxs-lookup"><span data-stu-id="c50e7-102">Build Errors in the Task List</span></span>
<span data-ttu-id="c50e7-103">當您建置專案或解決方案時，結果會出現在 [輸出] 視窗中，至於個別錯誤和警告則會出現在工作清單中。</span><span class="sxs-lookup"><span data-stu-id="c50e7-103">When you build your project, or solution, the results will appear in the Output window, while individual errors and warnings will appear in the task list.</span></span>  
  
 <span data-ttu-id="c50e7-104">錯誤和警告會出現在工作清單中。</span><span class="sxs-lookup"><span data-stu-id="c50e7-104">Errors and warnings appear in the task list.</span></span> <span data-ttu-id="c50e7-105">您可以按兩下該錯誤，即會將焦點套用到未正確設定的物件。</span><span class="sxs-lookup"><span data-stu-id="c50e7-105">You can double-click the error, and the focus will be applied to the object that is not correctly configured.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c50e7-106">當您建置時，編譯器不會驗證 XPaths。</span><span class="sxs-lookup"><span data-stu-id="c50e7-106">When you build, the compiler does not validate XPaths.</span></span> <span data-ttu-id="c50e7-107">請謹慎使用有效的 XPath 語法。</span><span class="sxs-lookup"><span data-stu-id="c50e7-107">Take care to use valid XPath syntax.</span></span>  
  
## <a name="insufficient-configuration-action"></a><span data-ttu-id="c50e7-108">動作組態不完整</span><span class="sxs-lookup"><span data-stu-id="c50e7-108">Insufficient configuration Action</span></span>  
 ![](../core/media/ebiz-orch-insufficconfig.gif "ebiz_orch_insufficconfig")  
  
> [!CAUTION]
>  <span data-ttu-id="c50e7-109">雖然「協調流程設計師」會盡可能提供組態不完整警告，不過，並不能保證您的協調流程可以在缺少這類警告的情況下正確編譯。</span><span class="sxs-lookup"><span data-stu-id="c50e7-109">While Orchestration Designer will provide insufficient configuration warnings where it can, there is no guarantee that your orchestration will compile correctly in the absence of such warnings.</span></span>  
  
## <a name="compiler-asks-if-you-are-missing-an-assembly-reference"></a><span data-ttu-id="c50e7-110">編譯器會詢問您是否遺漏了組件參照</span><span class="sxs-lookup"><span data-stu-id="c50e7-110">Compiler asks if you are missing an assembly reference</span></span>  
  
### <a name="problem"></a><span data-ttu-id="c50e7-111">問題</span><span class="sxs-lookup"><span data-stu-id="c50e7-111">Problem</span></span>  
 <span data-ttu-id="c50e7-112">編譯協調流程時，您收到錯誤訊息，其中附帶了一個問題「是否遺漏組件參照?」</span><span class="sxs-lookup"><span data-stu-id="c50e7-112">When you compile your orchestration you get an error message that ends with the question "are you missing an assembly reference?"</span></span> <span data-ttu-id="c50e7-113">兩種常見的訊息為：</span><span class="sxs-lookup"><span data-stu-id="c50e7-113">Two of the more common messages are:</span></span>  
  
-   <span data-ttu-id="c50e7-114">命名空間 'Y' 中沒有型別或命名空間名稱 'X' (您是否遺漏了組件參考?)</span><span class="sxs-lookup"><span data-stu-id="c50e7-114">The type or namespace name 'X' does not exist in the namespace 'Y' (are you missing an assembly reference?)</span></span>  
  
-   <span data-ttu-id="c50e7-115">識別項 'X' 不存在於 'Y' 中; 是否遺漏組件參照?</span><span class="sxs-lookup"><span data-stu-id="c50e7-115">Identifier 'X' does not exist in 'Y'; are you missing an assembly reference?</span></span>  
  
### <a name="cause"></a><span data-ttu-id="c50e7-116">原因</span><span class="sxs-lookup"><span data-stu-id="c50e7-116">Cause</span></span>  
 <span data-ttu-id="c50e7-117">這項錯誤可能是由下列任何一項所造成：</span><span class="sxs-lookup"><span data-stu-id="c50e7-117">Any of the following could be the cause of this error.</span></span>  
  
-   <span data-ttu-id="c50e7-118">您的專案未參考一或多個必要的組件。</span><span class="sxs-lookup"><span data-stu-id="c50e7-118">Your project does not reference one or more required assemblies.</span></span>  
  
-   <span data-ttu-id="c50e7-119">您專案中的對應或其他物件類型與專案同名。</span><span class="sxs-lookup"><span data-stu-id="c50e7-119">Your project has a map or other object type that has the same name as the project.</span></span>  
  
-   <span data-ttu-id="c50e7-120">您的專案使用以 XML 結構描述定義語言 (XSD) 為基礎的 Partner Interface Process (PIP) 結構描述，並且在名為 System 的子資料夾中包含了 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="c50e7-120">Your project uses XML Schema definition language (XSD)-based Partner Interface Process (PIP) schemas and contains XSD schemas in a subfolder that is named System.</span></span>  
  
-   <span data-ttu-id="c50e7-121">您專案中使用的某個全域屬性，其命名空間是目前專案命名空間的子集。</span><span class="sxs-lookup"><span data-stu-id="c50e7-121">Your project is using a Global Property whose namespace is a subset of the current project's namespace.</span></span> <span data-ttu-id="c50e7-122">例如，在包含於專案 "Accounts.FILE" 內的協調流程中，使用「全域屬性」命名空間 "File.ReceivedFileName"。</span><span class="sxs-lookup"><span data-stu-id="c50e7-122">For example, using the Global Property namespace "File.ReceivedFileName" in an orchestration contained in the project "Accounts.FILE".</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="c50e7-123">解決方案</span><span class="sxs-lookup"><span data-stu-id="c50e7-123">Resolution</span></span>  
 <span data-ttu-id="c50e7-124">視問題的原因而定，解決方式可以是下列任何一種：</span><span class="sxs-lookup"><span data-stu-id="c50e7-124">Depending upon the cause of the problem, the resolution could be any of the following:</span></span>  
  
-   <span data-ttu-id="c50e7-125">將專案所需組件的遺漏參考加入。</span><span class="sxs-lookup"><span data-stu-id="c50e7-125">Add a reference to the missing assemblies your project requires.</span></span>  
  
-   <span data-ttu-id="c50e7-126">將對應或其他物件的名稱變更為專案名稱以外的名稱。</span><span class="sxs-lookup"><span data-stu-id="c50e7-126">Change the name of the map or other object to something other than the project name.</span></span> <span data-ttu-id="c50e7-127">這通常可以透過物件的屬性頁來完成 (例如，[對應] 屬性頁包含 [名稱] 屬性)。</span><span class="sxs-lookup"><span data-stu-id="c50e7-127">This can typically be done through the object's property page (for example, the Map property page contains a Name property).</span></span>  
  
-   <span data-ttu-id="c50e7-128">在 Visual Studio 中變更結構描述的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c50e7-128">Change the namespace for the schemas in Visual Studio.</span></span> <span data-ttu-id="c50e7-129">若要這樣做使用 Visual Studio，請按一下**顯示所有檔案**上**專案**功能表，然後展開**系統**方案總管 中的節點。</span><span class="sxs-lookup"><span data-stu-id="c50e7-129">To do this using Visual Studio, click **Show All Files** on the **Project** menu, and then expand the **System** node in Solution Explorer.</span></span> <span data-ttu-id="c50e7-130">按一下每個檔案系統資料夾及任何子資料夾，並因此的任何變更命名空間中的項目 [屬性] 視窗出現**系統**部分都變成 _**系統**。</span><span class="sxs-lookup"><span data-stu-id="c50e7-130">Click each file in the System folder and in any subfolders, and then change the namespace entry in the Properties window so that any occurrence of **System** becomes _**System**.</span></span> <span data-ttu-id="c50e7-131">例如，變更**MyProject.System.SubFolder**命名空間加入**MyProject._System.Subfolder**命名空間。</span><span class="sxs-lookup"><span data-stu-id="c50e7-131">For example, change the **MyProject.System.SubFolder** namespace to **the MyProject._System.Subfolder** namespace.</span></span> <span data-ttu-id="c50e7-132">如需有關此問題，請參閱知識庫文章[916649](http://support.microsoft.com/?kbid=916649)。</span><span class="sxs-lookup"><span data-stu-id="c50e7-132">For more information about this issue, see KB article [916649](http://support.microsoft.com/?kbid=916649).</span></span>  
  
-   <span data-ttu-id="c50e7-133">從專案中移除衝突的「全域屬性」命名空間。</span><span class="sxs-lookup"><span data-stu-id="c50e7-133">Remove the conflicting Global Property namespace from the project.</span></span>  
  
## <a name="you-receive-a-message-has-not-been-initialized-in-construct-statement-error-when-building-your-project"></a><span data-ttu-id="c50e7-134">當您建置專案時，收到錯誤：在建構陳述式中尚未初始化訊息</span><span class="sxs-lookup"><span data-stu-id="c50e7-134">You receive a "Message has not been initialized in construct statement" error when building your project</span></span>  
  
### <a name="problem"></a><span data-ttu-id="c50e7-135">問題</span><span class="sxs-lookup"><span data-stu-id="c50e7-135">Problem</span></span>  
 <span data-ttu-id="c50e7-136">當您編譯 BizTalk 應用程式時，收到錯誤「在建構陳述式中尚未初始化訊息」。</span><span class="sxs-lookup"><span data-stu-id="c50e7-136">When you compile your BizTalk application, you get the error "Message has not been initialized in construct statement".</span></span>  
  
### <a name="cause"></a><span data-ttu-id="c50e7-137">原因</span><span class="sxs-lookup"><span data-stu-id="c50e7-137">Cause</span></span>  
 <span data-ttu-id="c50e7-138">建構訊息時，您指定所有的訊息變數，</span><span class="sxs-lookup"><span data-stu-id="c50e7-138">When you construct a message, you specify all the message variables.</span></span> <span data-ttu-id="c50e7-139">然後對訊息或其部分進行指派。</span><span class="sxs-lookup"><span data-stu-id="c50e7-139">Then you make assignments to the message or its parts.</span></span> <span data-ttu-id="c50e7-140">如果特定訊息指派的組件會包含在個別**建構訊息**圖形，您可能會收到初始化錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c50e7-140">If part of a specific message assignment is included in a separate **Construct Message** shape, you may receive the initialization error message.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="c50e7-141">解決方案</span><span class="sxs-lookup"><span data-stu-id="c50e7-141">Resolution</span></span>  
 <span data-ttu-id="c50e7-142">若要解決這個問題，請確定您在同一個包含所有組件的特定訊息指派**建構訊息**圖形。</span><span class="sxs-lookup"><span data-stu-id="c50e7-142">To resolve this behavior, make sure that you include all parts of a specific message assignment in the same **Construct Message** shape.</span></span> <span data-ttu-id="c50e7-143">如需相關的支援問題，請參閱知識庫文章[870606](http://support.microsoft.com/?kbid=870606)。</span><span class="sxs-lookup"><span data-stu-id="c50e7-143">For a related support issue, see KB article [870606](http://support.microsoft.com/?kbid=870606).</span></span>  
  
 <span data-ttu-id="c50e7-144">您也可以藉由建立您的訊息中解決此行為**建構**圖形，才能使用它在執行個體**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="c50e7-144">You can also resolve this behavior by creating your message in a **Construct** shape before using an instance of it in an **Expression** shape.</span></span> <span data-ttu-id="c50e7-145">例如，下列程式碼會造成錯誤如果放在**運算式**圖形：</span><span class="sxs-lookup"><span data-stu-id="c50e7-145">For example, the following code will cause an error if placed in an **Expression** shape:</span></span>  
  
```  
XMLDOM = new System.Xml.XmlDocument();  
POAckMsg = XMLDOM;  
```  
  
 <span data-ttu-id="c50e7-146">若要修正，建立在 XMLDOM 執行個體**建構**圖形，然後再進行指派，在下游**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="c50e7-146">To fix, create the instance of XMLDOM in a **Construct** shape, and then do the assignment in a downstream **Expression** shape.</span></span>  
  
## <a name="you-receive-a-use-of-unconstructed-message-error-when-building-your-project"></a><span data-ttu-id="c50e7-147">當您建置專案時，收到錯誤：使用未建構的訊息</span><span class="sxs-lookup"><span data-stu-id="c50e7-147">You receive a "use of unconstructed message" error when building your project</span></span>  
  
### <a name="problem"></a><span data-ttu-id="c50e7-148">問題</span><span class="sxs-lookup"><span data-stu-id="c50e7-148">Problem</span></span>  
 <span data-ttu-id="c50e7-149">當您編譯 BizTalk 專案時，您會收到錯誤 「 使用未建構的訊息 '\<訊息 >' 」。</span><span class="sxs-lookup"><span data-stu-id="c50e7-149">When you compile your BizTalk project, you receive the error "use of unconstructed message '\<message>'".</span></span>  
  
### <a name="cause"></a><span data-ttu-id="c50e7-150">原因</span><span class="sxs-lookup"><span data-stu-id="c50e7-150">Cause</span></span>  
 <span data-ttu-id="c50e7-151">當使用未建構的訊息時，就會發生此錯誤**傳送**圖形。</span><span class="sxs-lookup"><span data-stu-id="c50e7-151">This error occurs when an unconstructed message is used in a **Send** shape.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="c50e7-152">解決方案</span><span class="sxs-lookup"><span data-stu-id="c50e7-152">Resolution</span></span>  
 <span data-ttu-id="c50e7-153">若要解決此問題，請加入**建構訊息**圖形至協調流程。</span><span class="sxs-lookup"><span data-stu-id="c50e7-153">To resolve this issue, add a **Construct Message** shape to the orchestration.</span></span> <span data-ttu-id="c50e7-154">包含**建構訊息**圖形之前**傳送**繫結至 Web 服務的圖形。</span><span class="sxs-lookup"><span data-stu-id="c50e7-154">Include the **Construct Message** shape before the **Send** shape that is bound to the Web service.</span></span>  
  
 <span data-ttu-id="c50e7-155">如需有關此錯誤與 Web 服務，請參閱知識庫文章[921043](http://support.microsoft.com/?kbid=921043)。</span><span class="sxs-lookup"><span data-stu-id="c50e7-155">For more information about this error and Web services, see KB article [921043](http://support.microsoft.com/?kbid=921043).</span></span>  
  
## <a name="setting-a-transaction-level-for-a-scope-results-in-an-error"></a><span data-ttu-id="c50e7-156">設定範圍的交易層級會產生錯誤</span><span class="sxs-lookup"><span data-stu-id="c50e7-156">Setting a transaction level for a scope results in an error</span></span>  
  
### <a name="problem"></a><span data-ttu-id="c50e7-157">問題</span><span class="sxs-lookup"><span data-stu-id="c50e7-157">Problem</span></span>  
 <span data-ttu-id="c50e7-158">在協調流程中設定範圍或其他支援交易之實體的交易類型之後，看到錯誤「非交易式的協調流程不能包含任何其他交易」。</span><span class="sxs-lookup"><span data-stu-id="c50e7-158">After configuring the transaction type for a scope or other entity supporting transactions in an orchestration, you receive the error "A Non-transactional Orchestration cannot contain any other Transactions".</span></span>  
  
### <a name="cause"></a><span data-ttu-id="c50e7-159">原因</span><span class="sxs-lookup"><span data-stu-id="c50e7-159">Cause</span></span>  
 <span data-ttu-id="c50e7-160">如果協調流程本身的交易類型為「無」，當您嘗試在協調流程中，將範圍 (或其他實體) 的交易類型設定為「不可部分完成」或「長時間執行」，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="c50e7-160">This error occurs when you try to configure the transaction type of a scope (or other entity) in an orchestration to "Atomic" or "Long-Running" when the orchestration itself has a transaction type of "None".</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="c50e7-161">解決方案</span><span class="sxs-lookup"><span data-stu-id="c50e7-161">Resolution</span></span>  
 <span data-ttu-id="c50e7-162">請確定您的協調流程和構成物件的交易類型設定為相容。</span><span class="sxs-lookup"><span data-stu-id="c50e7-162">Ensure that the transaction type settings of your orchestration and constituent objects are compatible.</span></span>  
  
## <a name="project-build-results-in-the-error-you-must-specify-at-least-one-already-initialized-correlation-set-for-a-non-activation-receive-that-is-on-a-non-selfcorrelating-port"></a><span data-ttu-id="c50e7-163">建置專案時，發生錯誤：您必須為位於非自我相互關聯連接埠上的非啟動接收，至少指定一個已經初始化的相互關聯集合</span><span class="sxs-lookup"><span data-stu-id="c50e7-163">Project build results in the error "you must specify at least one already-initialized correlation set for a non-activation receive that is on a non-selfcorrelating port"</span></span>  
  
### <a name="problem"></a><span data-ttu-id="c50e7-164">問題</span><span class="sxs-lookup"><span data-stu-id="c50e7-164">Problem</span></span>  
 <span data-ttu-id="c50e7-165">當您編譯 BizTalk 專案時，看到錯誤「您必須為位於非自我相互關聯連接埠上的非啟動接收，至少指定一個已經初始化的相互關聯集合」。</span><span class="sxs-lookup"><span data-stu-id="c50e7-165">When you compile your BizTalk project, you receive the error "you must specify at least one already-initialized correlation set for a non-activation receive that is on a non-selfcorrelating port".</span></span>  
  
### <a name="cause"></a><span data-ttu-id="c50e7-166">原因</span><span class="sxs-lookup"><span data-stu-id="c50e7-166">Cause</span></span>  
 <span data-ttu-id="c50e7-167">如果沒有啟動協調流程，會發生此錯誤**接收**圖形 (Activate = true) 或沒有啟動**接收**圖形，且不直接由另一個協調流程呼叫。</span><span class="sxs-lookup"><span data-stu-id="c50e7-167">This error can occur if your orchestration has no activating **Receive** shapes (Activate = true) or has no activating **Receive** shapes and is not called directly by another orchestration.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="c50e7-168">解決方案</span><span class="sxs-lookup"><span data-stu-id="c50e7-168">Resolution</span></span>  
 <span data-ttu-id="c50e7-169">如果您的協調流程不由另一個協調流程呼叫，您必須設定其中一種**接收**圖形，來為啟動接收。</span><span class="sxs-lookup"><span data-stu-id="c50e7-169">If your orchestration is not called by another orchestration, you must configure one of the **Receive** shapes to be an activated receive.</span></span> <span data-ttu-id="c50e7-170">如需有關設定**接收**圖形，包括連結的相互關聯，請參閱[如何設定 「 接收 」 圖形](../core/how-to-configure-the-receive-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="c50e7-170">For more information about configuring the **Receive** shape, including links to correlation, see [How to Configure the Receive Shape](../core/how-to-configure-the-receive-shape.md).</span></span>  
  
## <a name="you-receive-the-error-assembly-generation-failed----referenced-assembly-assembly-does-not-have-a-strong-name-when-building-your-solution"></a><span data-ttu-id="c50e7-171">您會收到錯誤 「 組件產生失敗--參考的組件 '\<組件 >' 沒有強式名稱 」 您建置方案時</span><span class="sxs-lookup"><span data-stu-id="c50e7-171">You receive the error "Assembly generation failed -- Referenced assembly '\<assembly>' does not have a strong name" when building your solution</span></span>  
  
### <a name="problem"></a><span data-ttu-id="c50e7-172">問題</span><span class="sxs-lookup"><span data-stu-id="c50e7-172">Problem</span></span>  
 <span data-ttu-id="c50e7-173">您會收到錯誤 「 組件產生失敗--參考的組件 '\<組件 >' 沒有強式名稱 」 時，建置您的方案含有協調流程。</span><span class="sxs-lookup"><span data-stu-id="c50e7-173">You receive the error "Assembly generation failed -- Referenced assembly '\<assembly>' does not have a strong name" when building your solution that has an orchestration.</span></span>  
  
### <a name="cause"></a><span data-ttu-id="c50e7-174">原因</span><span class="sxs-lookup"><span data-stu-id="c50e7-174">Cause</span></span>  
 <span data-ttu-id="c50e7-175">如果在協調流程中使用來自未簽署的參考組件的類型，就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="c50e7-175">This problem occurs when a type from an unsigned referenced assembly is used within an orchestration.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="c50e7-176">解決方案</span><span class="sxs-lookup"><span data-stu-id="c50e7-176">Resolution</span></span>  
 <span data-ttu-id="c50e7-177">將強式名稱套用至參考組件。</span><span class="sxs-lookup"><span data-stu-id="c50e7-177">Apply a strong name to the referenced assembly.</span></span> <span data-ttu-id="c50e7-178">如果是可以重新編譯的自訂組件，請使用強式名稱工具建立 .snk (金鑰) 檔案，然後在專案的組件屬性中參考該金鑰檔案。</span><span class="sxs-lookup"><span data-stu-id="c50e7-178">If it is a custom assembly that you can recompile, use the strong name tool to create an .snk (key) file and then reference that key file in the assembly properties for the project.</span></span> <span data-ttu-id="c50e7-179">如需有關強式命名組件的詳細資訊，請參閱[如何設定強式名稱組件金鑰檔案](../core/how-to-configure-a-strong-name-assembly-key-file.md)。</span><span class="sxs-lookup"><span data-stu-id="c50e7-179">For more information about strong naming an assembly, see [How to Configure a Strong Name Assembly Key File](../core/how-to-configure-a-strong-name-assembly-key-file.md).</span></span>  
  
## <a name="the-error-failed-to-add-resources-change-requests-failed-for-some-resources-occurs-when-deploying-an-orchestration"></a><span data-ttu-id="c50e7-180">部署協調流程時，發生錯誤：無法新增資源。</span><span class="sxs-lookup"><span data-stu-id="c50e7-180">The error "Failed to add resource(s).</span></span> <span data-ttu-id="c50e7-181">某些資源的變更要求失敗。</span><span class="sxs-lookup"><span data-stu-id="c50e7-181">Change requests failed for some resources" occurs when deploying an orchestration</span></span>  
  
### <a name="problem"></a><span data-ttu-id="c50e7-182">問題</span><span class="sxs-lookup"><span data-stu-id="c50e7-182">Problem</span></span>  
 <span data-ttu-id="c50e7-183">部署協調流程時，顯示了類似下列的錯誤，協調流程部署於是失敗：</span><span class="sxs-lookup"><span data-stu-id="c50e7-183">When deploying an orchestration, an error similar to the following is displayed and deployment of the orchestration fails:</span></span>  
  
```  
Failed to add resource(s). Change requests failed for some resources. BizTalkAssemblyResourceManager failed to complete end type change request. Object reference not set to an instance of an object.  
```  
  
### <a name="cause"></a><span data-ttu-id="c50e7-184">原因</span><span class="sxs-lookup"><span data-stu-id="c50e7-184">Cause</span></span>  
 <span data-ttu-id="c50e7-185">如果協調流程包含任何使用 C# 關鍵字的物件，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="c50e7-185">This error can occur if the orchestration contains any objects that use C# keywords.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="c50e7-186">解決方案</span><span class="sxs-lookup"><span data-stu-id="c50e7-186">Resolution</span></span>  
 <span data-ttu-id="c50e7-187">從協調流程中移除任何 C# 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c50e7-187">Remove any C# keywords from the orchestration.</span></span> <span data-ttu-id="c50e7-188">如需 C# 關鍵字的清單，請參閱[http://go.microsoft.com/fwlink/?LinkId=74346](http://go.microsoft.com/fwlink/?LinkId=74346)。</span><span class="sxs-lookup"><span data-stu-id="c50e7-188">For a list of C# keywords, see [http://go.microsoft.com/fwlink/?LinkId=74346](http://go.microsoft.com/fwlink/?LinkId=74346).</span></span>  
  
## <a name="you-receive-an-invalid-property-value-error-when-compiling-your-orchestration"></a><span data-ttu-id="c50e7-189">當您編譯協調流程時，收到錯誤：無效的屬性值</span><span class="sxs-lookup"><span data-stu-id="c50e7-189">You receive an "invalid property value" error when compiling your orchestration</span></span>  
  
### <a name="problem"></a><span data-ttu-id="c50e7-190">問題</span><span class="sxs-lookup"><span data-stu-id="c50e7-190">Problem</span></span>  
 <span data-ttu-id="c50e7-191">當您建置協調流程時，看到錯誤對話方塊顯示「無效的屬性值」。</span><span class="sxs-lookup"><span data-stu-id="c50e7-191">You receive the error dialog "Invalid property value" when building your orchestration.</span></span>  
  
### <a name="cause"></a><span data-ttu-id="c50e7-192">原因</span><span class="sxs-lookup"><span data-stu-id="c50e7-192">Cause</span></span>  
 <span data-ttu-id="c50e7-193">方案中的一或多個物件與另一個物件的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="c50e7-193">One or more of the objects in your solution has the same name as another object.</span></span> <span data-ttu-id="c50e7-194">例如，訊息名稱與連接埠名稱相同。</span><span class="sxs-lookup"><span data-stu-id="c50e7-194">For example, a message name is the same as a port name.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="c50e7-195">解決方案</span><span class="sxs-lookup"><span data-stu-id="c50e7-195">Resolution</span></span>  
 <span data-ttu-id="c50e7-196">確定方案中的每個物件都有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="c50e7-196">Ensure that every object in your solution has a unique name.</span></span> <span data-ttu-id="c50e7-197">遵循命名慣例，即可降低發生此錯誤的風險。</span><span class="sxs-lookup"><span data-stu-id="c50e7-197">You can minimize the risk of this error by adhering to a naming convention.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c50e7-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c50e7-198">See Also</span></span>  
 [<span data-ttu-id="c50e7-199">如何建置協調流程</span><span class="sxs-lookup"><span data-stu-id="c50e7-199">How to Build Orchestrations</span></span>](../core/how-to-build-orchestrations.md)