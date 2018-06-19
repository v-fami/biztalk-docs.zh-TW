---
title: 偵錯協調流程執行階段錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7be9ee5a-b9fa-428b-8b92-0fa0f801c724
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87a47c5b2ee432059365c6f9046a75bb5775fc02
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969900"
---
# <a name="debugging-orchestration-runtime-errors"></a><span data-ttu-id="079d2-102">偵錯協調流程執行階段錯誤</span><span class="sxs-lookup"><span data-stu-id="079d2-102">Debugging Orchestration Runtime Errors</span></span>
<span data-ttu-id="079d2-103">本節包含設計用來協助您解決協調流程執行階段問題的問答集。</span><span class="sxs-lookup"><span data-stu-id="079d2-103">This section contains a set of questions and answers designed to help you resolve runtime issues with your orchestrations.</span></span>  
  
## <a name="why-do-i-get-intermittent-subscription-errors-when-sending-to-a-child-orchestration-that-was-just-started-by-the-parent"></a><span data-ttu-id="079d2-104">為何在傳送至剛由父協調流程啟動的子協調流程時，得到間歇性的訂閱錯誤？</span><span class="sxs-lookup"><span data-stu-id="079d2-104">Why do I get intermittent subscription errors when sending to a child orchestration that was just started by the parent?</span></span>  
 <span data-ttu-id="079d2-105">訂閱錯誤「找不到訂閱」是競爭條件的結果。</span><span class="sxs-lookup"><span data-stu-id="079d2-105">The subscription error "could not find subscription" is a result of a race condition.</span></span> <span data-ttu-id="079d2-106">競爭條件是指根據程序發生的特定順序來決定程序的結果。</span><span class="sxs-lookup"><span data-stu-id="079d2-106">A race condition occurs when the outcome of a process depends on the particular order in which the process takes place.</span></span> <span data-ttu-id="079d2-107">在此案例中，當子協調流程未及時啟動來接收父協調流程傳送的訊息時，便會產生此競爭條件。</span><span class="sxs-lookup"><span data-stu-id="079d2-107">In this case, the condition occurs when the child orchestration has not been started in time to receive the message sent by the parent.</span></span>  
  
 <span data-ttu-id="079d2-108">若要避免這個問題，子協調流程可在啟動後準備接收訊息時，傳送訊息給父協調流程。</span><span class="sxs-lookup"><span data-stu-id="079d2-108">To avoid this problem, the child orchestration could send a message back to the parent when it has been started and is prepared to receive a message.</span></span> <span data-ttu-id="079d2-109">如此一來，在傳送訊息之前，啟動子協調流程的父協調流程就會知道有接收器。</span><span class="sxs-lookup"><span data-stu-id="079d2-109">In this way, the parent orchestration that started it would know that there is a receiver before sending a message.</span></span>  
  
## <a name="why-do-i-get-errors-when-i-attach-a-dynamic-send-port-to-a-logical-port"></a><span data-ttu-id="079d2-110">為什麼當我將動態傳送埠附加至邏輯連接埠時，得到錯誤？</span><span class="sxs-lookup"><span data-stu-id="079d2-110">Why do I get errors when I attach a dynamic send port to a logical port?</span></span>  
 <span data-ttu-id="079d2-111">動態連接埠不是設計為繼承指派給它的所有連接埠屬性和特性。</span><span class="sxs-lookup"><span data-stu-id="079d2-111">A dynamic port is not designed to inherit all of the attributes and characteristics of the port assigned to it.</span></span> <span data-ttu-id="079d2-112">動態連接埠只取得位址，不會繼承與邏輯連接埠關聯的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="079d2-112">A dynamic port gets an address only; it does not inherit the other information associated with the logical port.</span></span>  
  
 <span data-ttu-id="079d2-113">例如，如果將動態傳送埠附加至標示為 Delivery Notification = Transmitted 的邏輯連接埠，執行階段將不會傳送傳遞通知。</span><span class="sxs-lookup"><span data-stu-id="079d2-113">For example, if you attach a dynamic send port to a logical port with Delivery Notification = Transmitted, the runtime will not deliver a delivery notification.</span></span> <span data-ttu-id="079d2-114">如果實際上透過該方法靜態設定連接埠，XLANGs 執行階段只會偵聽傳遞通知。</span><span class="sxs-lookup"><span data-stu-id="079d2-114">The XLANGs runtime only listens for a delivery notification if the port has actually been set up that way statically.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="079d2-115">在 XLANGs，只有在靜態設定連接埠時，連接埠才會運作。</span><span class="sxs-lookup"><span data-stu-id="079d2-115">In XLANGs, ports will behave only as they have been configured statically.</span></span>  
  
## <a name="when-i-try-to-run-my-application-after-deploying-an-orchestration-with-custom-components-why-do-i-get-the-error-file-or-assembly-name-or-one-of-its-dependencies-not-found"></a><span data-ttu-id="079d2-116">在部署具有自訂元件的協調流程之後，當我嘗試執行應用程式時，為何得到錯誤，指出找不到檔案或組件名稱或其相依檔案或組件的其中之一？</span><span class="sxs-lookup"><span data-stu-id="079d2-116">When I try to run my application after deploying an orchestration with custom components, why do I get the error "File or Assembly name or one of its dependencies not found"?</span></span>  
 <span data-ttu-id="079d2-117">這個錯誤通常表示 BizTalk 協調流程引擎找不到自訂元件。</span><span class="sxs-lookup"><span data-stu-id="079d2-117">This error usually means the BizTalk orchestration engine cannot locate the custom component.</span></span> <span data-ttu-id="079d2-118">您必須在裝載應用程式的電腦上，將 BizTalk 應用程式中包含的所有組件安裝在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="079d2-118">You must install all assemblies included in a BizTalk application in the global assembly cache of the computer that hosts the application.</span></span>  
  
## <a name="an-assemblyname-context-property-was-not-valid-error-occurs-when-submitting-a-document-to-a-web-service-via-an-orchestration"></a><span data-ttu-id="079d2-119">透過協調流程將文件提交至 Web 服務時，發生 AssemblyName 內容屬性無效錯誤</span><span class="sxs-lookup"><span data-stu-id="079d2-119">An "AssemblyName context property was not valid" error occurs when submitting a document to a Web service via an orchestration</span></span>  
  
### <a name="problem"></a><span data-ttu-id="079d2-120">問題</span><span class="sxs-lookup"><span data-stu-id="079d2-120">Problem</span></span>  
 <span data-ttu-id="079d2-121">透過協調流程將文件提交至 Web 服務，造成 AssemblyName 內容屬性無效錯誤。</span><span class="sxs-lookup"><span data-stu-id="079d2-121">Submitting a document to a Web service via an orchestration results in an "AssemblyName context property not valid" error.</span></span>  
  
### <a name="cause"></a><span data-ttu-id="079d2-122">原因</span><span class="sxs-lookup"><span data-stu-id="079d2-122">Cause</span></span>  
 <span data-ttu-id="079d2-123">BizTalk 應用程式原來設計為使用「傳訊」方法，而非中間的協調流程。</span><span class="sxs-lookup"><span data-stu-id="079d2-123">The BizTalk application was originally designed using a "messaging" approach without an intervening orchestration.</span></span> <span data-ttu-id="079d2-124">這種解決方案類型會使用傳送埠篩選條件來連結接收埠和傳送埠，讓文件能在接收時通過到達傳送埠。</span><span class="sxs-lookup"><span data-stu-id="079d2-124">This type of solution uses a send port filter to link the receive port and the send port so that the document is passed through to the send port upon receipt.</span></span> <span data-ttu-id="079d2-125">之後，解決方案會修改為包含繫結至傳送埠的協調流程。</span><span class="sxs-lookup"><span data-stu-id="079d2-125">Later, the solution was modified to include an orchestration that was bound to the send port.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="079d2-126">解決方案</span><span class="sxs-lookup"><span data-stu-id="079d2-126">Resolution</span></span>  
 <span data-ttu-id="079d2-127">移除傳送埠上的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="079d2-127">Remove the filter on the send port.</span></span> <span data-ttu-id="079d2-128">如果您在繫結至協調流程的傳送埠上套用篩選條件，訊息通常會略過協調流程並造成內容屬性錯誤。</span><span class="sxs-lookup"><span data-stu-id="079d2-128">If you apply a filter to a send port that is bound to an orchestration, messages will often bypass the orchestration and cause the context property error.</span></span>  
  
## <a name="a-wrongbodypartexception-occurs-when-handling-a-multipart-mime-message-in-an-orchestration"></a><span data-ttu-id="079d2-129">在協調流程中處理多部分 MIME 訊息時，發生 "WrongBodyPartException"</span><span class="sxs-lookup"><span data-stu-id="079d2-129">A "WrongBodyPartException" occurs when handling a multipart MIME message in an orchestration</span></span>  
  
### <a name="problem"></a><span data-ttu-id="079d2-130">問題</span><span class="sxs-lookup"><span data-stu-id="079d2-130">Problem</span></span>  
 <span data-ttu-id="079d2-131">為協調流程接收多部分 MIME 訊息導致**WrongBodyPartException**例外狀況。</span><span class="sxs-lookup"><span data-stu-id="079d2-131">Receiving a multipart MIME message into an orchestration results in a **WrongBodyPartException** exception.</span></span>  
  
### <a name="cause"></a><span data-ttu-id="079d2-132">原因</span><span class="sxs-lookup"><span data-stu-id="079d2-132">Cause</span></span>  
 <span data-ttu-id="079d2-133">如果不正確指定訊息部分的順序，或訊息不符合指定的部分位置，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="079d2-133">This error can occur if the order of the parts is specified incorrectly or messages do not conform to the part positions you have specified.</span></span> <span data-ttu-id="079d2-134">例如，如果您指定第三個部分是內文部分，但送達的訊息中第三個位置卻是標頭部分。</span><span class="sxs-lookup"><span data-stu-id="079d2-134">For example, if you specify that the third part is a body part but messages arrive with a header part in the third position.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="079d2-135">解決方案</span><span class="sxs-lookup"><span data-stu-id="079d2-135">Resolution</span></span>  
 <span data-ttu-id="079d2-136">驗證內文部分索引設定是否正確，接著確認透過配接器送達的所有訊息是否都與設定一致。</span><span class="sxs-lookup"><span data-stu-id="079d2-136">Verify that the body part index setting is correct and then ensure that all messages arriving through the adapter are consistent with the setting.</span></span> <span data-ttu-id="079d2-137">您可以停止協調流程 (但保持登錄)，檢查在協調流程中失敗 MIME 訊息的內容。這會強制訊息發佈，所以您可以使用管理主控台來檢查訊息並驗證部分順序。</span><span class="sxs-lookup"><span data-stu-id="079d2-137">You can inspect the contents of MIME messages that fail inside an orchestration by stopping the orchestration (but keeping it enlisted); this will force the message to be published so you can examine it using the Administration console and verify the order of the parts.</span></span>  
  
## <a name="multipart-mime-message-part-cannot-be-found"></a><span data-ttu-id="079d2-138">找不到多部分 MIME 訊息部分</span><span class="sxs-lookup"><span data-stu-id="079d2-138">Multipart MIME message part cannot be found</span></span>  
  
### <a name="problem"></a><span data-ttu-id="079d2-139">問題</span><span class="sxs-lookup"><span data-stu-id="079d2-139">Problem</span></span>  
 <span data-ttu-id="079d2-140">嘗試擷取 MIME 訊息部分的索引值大於 0 的結果，在 BizTalk Server 執行階段擲回類似的錯誤 「 找不到具有索引的多部分訊息 =\<值\>"。</span><span class="sxs-lookup"><span data-stu-id="079d2-140">Attempts to retrieve a MIME message part with an index value greater than 0 results in the BizTalk Server runtime throwing an error similar to "can't find multi-part message with index = \<value\>".</span></span>  
  
### <a name="cause"></a><span data-ttu-id="079d2-141">原因</span><span class="sxs-lookup"><span data-stu-id="079d2-141">Cause</span></span>  
 <span data-ttu-id="079d2-142">導致這個錯誤的最常見原因包括：</span><span class="sxs-lookup"><span data-stu-id="079d2-142">The most common causes for this error are:</span></span>  
  
-   <span data-ttu-id="079d2-143">MIME 訊息部分少於預期。</span><span class="sxs-lookup"><span data-stu-id="079d2-143">The MIME message has fewer parts than expected.</span></span>  
  
-   <span data-ttu-id="079d2-144">無法完全剖析 MIME 訊息。</span><span class="sxs-lookup"><span data-stu-id="079d2-144">The MIME message could not be fully parsed.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="079d2-145">解決方案</span><span class="sxs-lookup"><span data-stu-id="079d2-145">Resolution</span></span>  
 <span data-ttu-id="079d2-146">藉由確認程式碼只從訊息來源預期的範圍內擷取訊息部分，可以解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="079d2-146">You can resolve this problem by ensuring that your code retrieves only message parts that are within the range expected from the message source.</span></span> <span data-ttu-id="079d2-147">在剖析問題這部分，您應該驗證原始 MIME 訊息的結構完整且已正確建構。</span><span class="sxs-lookup"><span data-stu-id="079d2-147">In the case of a parsing issue, you should verify that the original MIME message is structurally sound and properly constructed.</span></span> <span data-ttu-id="079d2-148">如果您預期偶爾會發生剖析問題，請確認協調流程有適當的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="079d2-148">If you expect occasional parsing problems, ensure that your orchestration has appropriate exception handlers.</span></span>  
  
## <a name="you-receive-a-the-file-send-adapter-cannot-open-file-for-writing-error-when-sending-using-a-dynamic-send-port"></a><span data-ttu-id="079d2-149">使用動態傳送埠進行傳送時收到「FILE 傳送配接器無法開啟檔案進行寫入」錯誤</span><span class="sxs-lookup"><span data-stu-id="079d2-149">You receive a "The FILE send adapter cannot open file for writing" error when sending using a dynamic send port</span></span>  
  
### <a name="problem"></a><span data-ttu-id="079d2-150">問題</span><span class="sxs-lookup"><span data-stu-id="079d2-150">Problem</span></span>  
 <span data-ttu-id="079d2-151">您會收到 「 FILE 傳送配接器無法開啟檔案 *\<filename\>* 進行寫入 」 錯誤時使用動態傳送 BizTalk Server 事件記錄檔中的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="079d2-151">You receive a "The FILE send adapter cannot open file *\<filename\>* for writing" error in the BizTalk Server event log when sending using a dynamic send port.</span></span>  
  
 <span data-ttu-id="079d2-152">發生此問題時**BTS。OutBoundTransportLocation**屬性已定義在協調流程運算式中和已指定檔案傳輸，例如，下列運算式會造成這個錯誤，在執行階段：</span><span class="sxs-lookup"><span data-stu-id="079d2-152">This problem occurs when the **BTS.OutBoundTransportLocation** property is defined in an orchestration expression and the file transport is specified, for example the following expressions will cause this error at runtime:</span></span>  
  
```  
Message2=Message1;  
Message2(BTS.OutboundTransportLocation) = "file:///c:/test/out";  
MySendPort(Microsoft.XLANGs.BaseTypes.Address)=Message2(BTS.OutboundTransportLocation);  
```  
  
 <span data-ttu-id="079d2-153">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="079d2-153">\- Or -</span></span>  
  
```  
Message2=Message1;  
Message2(BTS.OutboundTransportLocation) = "file://mymachine/test/out";  
MySendPort(Microsoft.XLANGs.BaseTypes.Address)=Message2(BTS.OutboundTransportLocation);  
```  
  
### <a name="cause"></a><span data-ttu-id="079d2-154">原因</span><span class="sxs-lookup"><span data-stu-id="079d2-154">Cause</span></span>  
 <span data-ttu-id="079d2-155">因為協調流程引擎會在執行階段移除文字，就會發生這個問題 「**file://"** 從指定的 URL。</span><span class="sxs-lookup"><span data-stu-id="079d2-155">This problem occurs because at runtime the orchestration engine removes the text "**file://"** from the specified URL.</span></span> <span data-ttu-id="079d2-156">因此，使用上述範例時，"file:///c:/test/out" 為評估為 \c:\test\out，而 "file://mymachine/test/out" 會評估為 mymachine\test\out。</span><span class="sxs-lookup"><span data-stu-id="079d2-156">So, using the examples above, "file:///c:/test/out" is evaluated as \c:\test\out and "file://mymachine/test/out" is evaluated as mymachine\test\out.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="079d2-157">解決方案</span><span class="sxs-lookup"><span data-stu-id="079d2-157">Resolution</span></span>  
 <span data-ttu-id="079d2-158">當指定之 URL 的**BTS。OutBoundTransportLocation**屬性的運算式中，新增或移除"/"字元視。</span><span class="sxs-lookup"><span data-stu-id="079d2-158">When specifying the URL for the **BTS.OutBoundTransportLocation** property in an expression, add or remove "/" characters as needed.</span></span> <span data-ttu-id="079d2-159">使用上述範例**BTS。OutBoundTransportLocation**屬性應定義為"file://c:/test/out"，這會評估為 c:\test\out 或 「 file:///mymachine/test/out"，這會評估為\\\mymachine\test\out。</span><span class="sxs-lookup"><span data-stu-id="079d2-159">Using the examples above the **BTS.OutBoundTransportLocation** property should be defined as "file://c:/test/out", which would evaluate to c:\test\out or "file:////mymachine/test/out", which would evaluate to \\\mymachine\test\out.</span></span>