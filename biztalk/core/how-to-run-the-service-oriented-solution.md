---
title: "如何執行服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service solution tutorial, client applications
- service solution tutorial, starting solution
- service solution tutorial, sending requests
- service solution tutorial, SOAP transports
ms.assetid: 764a5ddc-e571-41d8-9e2f-6d0fb3361b2f
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27462716832631fc2a36d577b39e3ff5431b858b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-run-the-service-oriented-solution"></a><span data-ttu-id="282ff-102">如何執行服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="282ff-102">How to Run the Service Oriented Solution</span></span>
<span data-ttu-id="282ff-103">下列步驟描述如何在單一電腦上執行和驗證服務導向解決方案。</span><span class="sxs-lookup"><span data-stu-id="282ff-103">The following steps describe how to run and validate the service oriented solution on a single computer.</span></span> <span data-ttu-id="282ff-104">啟動付款追蹤器模擬器之後，使用 SOAP 或 MQSeries 傳輸來傳送要求 (服務導向解決方案的配接器與內嵌版本分別使用個別程序)。</span><span class="sxs-lookup"><span data-stu-id="282ff-104">After starting the Payment Tracker simulator, you can send requests using either the SOAP or MQSeries transport (with separate procedures for the adapter and inline versions of the service oriented solution).</span></span>  
  
-   [<span data-ttu-id="282ff-105">使用用戶端應用程式 （虛設常式版本） 透過 SOAP 傳輸傳送要求</span><span class="sxs-lookup"><span data-stu-id="282ff-105">Send requests by SOAP transport using the client application (stub version)</span></span>](#step1)  
  
-   [<span data-ttu-id="282ff-106">使用用戶端應用程式 （配接器版本） 傳送要求</span><span class="sxs-lookup"><span data-stu-id="282ff-106">Send requests using the client application (adapter version)</span></span>](#step3)  
  
-   [<span data-ttu-id="282ff-107">使用用戶端應用程式 （內嵌版本） 傳送要求</span><span class="sxs-lookup"><span data-stu-id="282ff-107">Send requests using the client application (inline version)</span></span>](#step5)  
  
##  <span data-ttu-id="282ff-108"><a name="step1"></a>使用用戶端應用程式 （虛設常式版本） 透過 SOAP 傳輸傳送要求</span><span class="sxs-lookup"><span data-stu-id="282ff-108"><a name="step1"></a> Send requests by SOAP transport using the client application (stub version)</span></span>  
  
#### <a name="to-send-requests-by-soap-transport-using-the-client-application-stub-version"></a><span data-ttu-id="282ff-109">使用用戶端應用程式 (虛設常式版本) 透過 SOAP 傳輸傳送要求</span><span class="sxs-lookup"><span data-stu-id="282ff-109">To send requests by SOAP transport using the client application (stub version)</span></span>  
  
1.  <span data-ttu-id="282ff-110">開啟命令提示字元，將目錄變更\< *BizTalk Server 安裝目錄*> \SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release，，然後執行 BTSScnSOSimpleClient.exe。</span><span class="sxs-lookup"><span data-stu-id="282ff-110">Open a command prompt, change the directory to the \<*BizTalk Server install Directory*>\SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release, and then run the BTSScnSOSimpleClient.exe.</span></span>  
  
2.  <span data-ttu-id="282ff-111">輸入任何字元**RequestType**， **[requestsource]**，和**RequestID**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-111">Type any characters in the **RequestType**, **RequestSource**, and **RequestID** text boxes.</span></span>  
  
3.  <span data-ttu-id="282ff-112">輸入任何 16 位數的數字中**帳戶號碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-112">Type any 16-digit number in the **Account Number** text box.</span></span>  
  
4.  <span data-ttu-id="282ff-113">選取**SOAP (WS Call)**和**虛設常式**中**選取傳輸與參數**群組方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-113">Select **SOAP (WS Call)** and **Stub** in the **Select Transport and Parameters** group box.</span></span>  
  
5.  <span data-ttu-id="282ff-114">輸入下列 URL 中的**URL**文字方塊中，例如：</span><span class="sxs-lookup"><span data-stu-id="282ff-114">Type the following URL in the **URL** text box, for example:</span></span>  
  
6.  `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub/CustomerServicePort.asmx`  
  
7.  <span data-ttu-id="282ff-115">型別`ZipCode`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-115">Type `ZipCode` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
8.  <span data-ttu-id="282ff-116">型別`CustomerName`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-116">Type `CustomerName` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
9. <span data-ttu-id="282ff-117">按一下**取得我的平衡**。</span><span class="sxs-lookup"><span data-stu-id="282ff-117">Click **Get my balance**.</span></span>  
  
10. <span data-ttu-id="282ff-118">回應會顯示在**回應**文字方塊：**成功**才會顯示已成功處理要求; 如果要求失敗，出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="282ff-118">The response is displayed in the **Response** text box: **SUCCESS** appears if the request is handled successfully; an error message appears if the request fails.</span></span>  
  
     <span data-ttu-id="282ff-119">![執行虛設常式版本的用戶端應用程式](../core/media/bts-cp-so-deploy-stubversion-success.gif "BTS_CP_SO_Deploy_StubVersion_Success")</span><span class="sxs-lookup"><span data-stu-id="282ff-119">![Run the client application for the stub version](../core/media/bts-cp-so-deploy-stubversion-success.gif "BTS_CP_SO_Deploy_StubVersion_Success")</span></span>  
  
##  <span data-ttu-id="282ff-120"><a name="step3"></a>使用用戶端應用程式 （配接器版本） 傳送要求</span><span class="sxs-lookup"><span data-stu-id="282ff-120"><a name="step3"></a> Send requests using the client application (adapter version)</span></span>  
  
#### <a name="to-send-requests-using-the-client-application-adapter-version"></a><span data-ttu-id="282ff-121">使用用戶端應用程式 (配接器版本) 傳送要求</span><span class="sxs-lookup"><span data-stu-id="282ff-121">To send requests using the client application (adapter version)</span></span>  
  
1.  <span data-ttu-id="282ff-122">開啟命令提示字元，將目錄變更\< *BizTalk Server 安裝目錄*> \SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug，然後執行下列命令以啟動付款追蹤器模擬器：</span><span class="sxs-lookup"><span data-stu-id="282ff-122">Open a command prompt, change the directory to \<*BizTalk Server install Directory*>\SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug and, then run the following command to start the PaymentTracker simulator:</span></span>  
  
     <span data-ttu-id="282ff-123">`BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <`*佇列管理員名稱* `> 5 [<` *通道定義*`>]`</span><span class="sxs-lookup"><span data-stu-id="282ff-123">`BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <` *Queue Manager Name* `> 5 [<` *Channel Definition* `>]`</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="282ff-124">若不是 MQSeries Server，則通道定義為選擇性。</span><span class="sxs-lookup"><span data-stu-id="282ff-124">The channel definition is optional if it is not remote MQSeries Server.</span></span>  
  
    -   <span data-ttu-id="282ff-125">讓付款追蹤器模擬器繼續執行。</span><span class="sxs-lookup"><span data-stu-id="282ff-125">Leave the Payment Tracker simulator running.</span></span>  
  
2.  <span data-ttu-id="282ff-126">開啟命令提示字元，將目錄變更\< *BizTalk Server 安裝目錄*> \SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release，，然後執行 BTSScnSOSimpleClient.exe。</span><span class="sxs-lookup"><span data-stu-id="282ff-126">Open a command prompt, change the directory to the \<*BizTalk Server install Directory*>\SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release, and then run the BTSScnSOSimpleClient.exe.</span></span>  
  
3.  <span data-ttu-id="282ff-127">在 BTSScnSOSimpleClient.exe 中，使用下列方式透過 SOAP 傳輸傳送要求：</span><span class="sxs-lookup"><span data-stu-id="282ff-127">In the BTSScnSOSimpleClient.exe, send a request by SOAP transport using the as follows:</span></span>  
  
    1.  <span data-ttu-id="282ff-128">輸入任何字元**RequestType**， **[requestsource]**，和**RequestID**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-128">Type any characters in the **RequestType**, **RequestSource**, and **RequestID** text boxes.</span></span>  
  
    2.  <span data-ttu-id="282ff-129">輸入任何 16 位數的數字中**帳戶號碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-129">Type any 16-digit number in the **Account Number** text box.</span></span>  
  
    3.  <span data-ttu-id="282ff-130">選取**SOAP (WS Call)**和**配接器**中**選取傳輸與參數**群組方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-130">Select **SOAP (WS Call)** and **Adapter** in the **Select Transport and Parameters** group box.</span></span>  
  
    4.  <span data-ttu-id="282ff-131">輸入下列 URL 中的**URL**文字方塊中，例如：</span><span class="sxs-lookup"><span data-stu-id="282ff-131">Type the following URL in the **URL** text box, for example:</span></span>  
  
         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter/CustomerServicePort.asmx`  
  
    5.  <span data-ttu-id="282ff-132">型別`ZipCode`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-132">Type `ZipCode` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    6.  <span data-ttu-id="282ff-133">型別`CustomerName`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-133">Type `CustomerName` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    7.  <span data-ttu-id="282ff-134">按一下**取得我的平衡**。</span><span class="sxs-lookup"><span data-stu-id="282ff-134">Click **Get my balance**.</span></span>  
  
    8.  <span data-ttu-id="282ff-135">回應會顯示在**回應**文字方塊：**成功**才會顯示已成功處理要求; 如果要求失敗，出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="282ff-135">The response is displayed in the **Response** text box: **SUCCESS** appears if the request is handled successfully; an error message appears if the request fails.</span></span>  
  
         <span data-ttu-id="282ff-136">![執行配接器版本的用戶端應用程式](../core/media/soap-transport-adapter-success.gif "SOAP_Transport_adapter_success")</span><span class="sxs-lookup"><span data-stu-id="282ff-136">![Run the client application for the adapter version](../core/media/soap-transport-adapter-success.gif "SOAP_Transport_adapter_success")</span></span>  
  
4.  <span data-ttu-id="282ff-137">在 BTSScnSOSimpleClient.exe 中，依下列方式透過 MQSeries 傳輸傳送要求：</span><span class="sxs-lookup"><span data-stu-id="282ff-137">In the BTSScnSOSimpleClient.exe, send requests by MQSeries transport as follows:</span></span>  
  
    1.  <span data-ttu-id="282ff-138">輸入任何字元**RequestType**， **[requestsource]**，和**RequestID**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-138">Type any characters in the **RequestType**, **RequestSource**, and **RequestID** text boxes.</span></span>  
  
    2.  <span data-ttu-id="282ff-139">輸入 16 位數數字中的**帳戶號碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-139">Type a 16-digit number in the **Account Number** text box.</span></span>  
  
    3.  <span data-ttu-id="282ff-140">選取**MQSeries**中**選取傳輸與參數**群組方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-140">Select **MQSeries** in the **Select Transport and Parameters** group box.</span></span>  
  
    4.  <span data-ttu-id="282ff-141">型別\<*佇列管理員名稱*> 中**佇列管理員**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-141">Type \<*Queue Manager Name*> in the **Queue Manager** text box.</span></span> <span data-ttu-id="282ff-142">Qm_<\<*您的電腦名稱*> 是預設值\<*佇列管理員名稱*>。</span><span class="sxs-lookup"><span data-stu-id="282ff-142">QM_\<*Your Computer Name*> is the default value for \<*Queue Manager Name*>.</span></span>  
  
    5.  <span data-ttu-id="282ff-143">型別`AdapterSOAInputQueue`中**輸入佇列**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-143">Type `AdapterSOAInputQueue` in the **Input Queue** text box.</span></span>  
  
    6.  <span data-ttu-id="282ff-144">型別`AdapterSOAOutputQueue`中**輸出佇列**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-144">Type `AdapterSOAOutputQueue` in the **Output Queue** text box.</span></span>  
  
    7.  <span data-ttu-id="282ff-145">型別\<*通道定義*> 中**通道定義**方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-145">Type \<*Channel Definition*> in the **Channel Definition** box.</span></span> <span data-ttu-id="282ff-146">S_\<*您的電腦名稱*> /TCP/\<*您的電腦名稱*> (1414) 是預設值為\<*通道定義*>。</span><span class="sxs-lookup"><span data-stu-id="282ff-146">S_\<*Your Computer Name*>/TCP/\<*Your Computer Name*>(1414) is the default value for \<*Channel Definition*>.</span></span>  
  
    8.  <span data-ttu-id="282ff-147">型別`ZipCode`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-147">Type `ZipCode` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    9. <span data-ttu-id="282ff-148">型別`CustomerName`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-148">Type `CustomerName` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    10. <span data-ttu-id="282ff-149">按一下**取得我的平衡**。</span><span class="sxs-lookup"><span data-stu-id="282ff-149">Click **Get my balance**.</span></span>  
  
    11. <span data-ttu-id="282ff-150">回應會顯示在**回應**文字方塊：**成功**才會顯示已成功處理要求; 如果要求失敗，出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="282ff-150">The response is displayed in the **Response** text box: **SUCCESS** appears if the request is handled successfully; an error message appears if the request fails.</span></span>  
  
         <span data-ttu-id="282ff-151">![執行配接器版本的用戶端應用程式](../core/media/mqseries-transport-adapter.gif "MQSeries_Transport_adapter")</span><span class="sxs-lookup"><span data-stu-id="282ff-151">![Run the client application for the adapter version](../core/media/mqseries-transport-adapter.gif "MQSeries_Transport_adapter")</span></span>  
  
##  <span data-ttu-id="282ff-152"><a name="step5"></a>使用用戶端應用程式 （內嵌版本） 傳送要求</span><span class="sxs-lookup"><span data-stu-id="282ff-152"><a name="step5"></a> Send requests using the client application (inline version)</span></span>  
  
#### <a name="to-send-requests-using-the-client-application-inline-version"></a><span data-ttu-id="282ff-153">使用用戶端應用程式 (內嵌版本) 傳送要求</span><span class="sxs-lookup"><span data-stu-id="282ff-153">To send requests using the client application (inline version)</span></span>  
  
1.  <span data-ttu-id="282ff-154">開啟命令提示字元，將目錄變更\< *BizTalk Server 安裝目錄*> \SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug，，然後執行下列命令以啟動付款追蹤器模擬器：</span><span class="sxs-lookup"><span data-stu-id="282ff-154">Open a command prompt, change the directory to \<*BizTalk Server install Directory*>\SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug, and then run the following command to start the PaymentTracker simulator:</span></span>  
  
     <span data-ttu-id="282ff-155">`BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <`*佇列管理員名稱* `> 5 [<` *通道定義*`>]`</span><span class="sxs-lookup"><span data-stu-id="282ff-155">`BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <` *Queue Manager Name* `> 5 [<` *Channel Definition* `>]`</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="282ff-156">若不是 MQSeries Server，則通道定義為選擇性。</span><span class="sxs-lookup"><span data-stu-id="282ff-156">The channel definition is optional if it is not remote MQSeries Server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="282ff-157">若付款追蹤器模擬器已經在執行中，請略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="282ff-157">Skip this step if the PaymentTracker simulator is already running.</span></span>  
  
    -   <span data-ttu-id="282ff-158">讓付款追蹤器模擬器繼續執行。</span><span class="sxs-lookup"><span data-stu-id="282ff-158">Leave the Payment Tracker simulator running.</span></span>  
  
2.  <span data-ttu-id="282ff-159">在**BizTalk Server 管理主控台**，依序展開**BTSScn.SO.CustomerService**，按一下 **接收位置**，以滑鼠右鍵按一下**Paymenttrackingsystemoutputqueue**在右窗格中，然後按一下**停用**。</span><span class="sxs-lookup"><span data-stu-id="282ff-159">In the **BizTalk Server Administration Console**, expand **BTSScn.SO.CustomerService**, click **Receive Locations**, right-click **PaymentTrackingSystemOutputQueue** in the right pane, and then click **Disable**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="282ff-160">配接器版本和內嵌版本會使用相同的 MQSeries 佇列 LastPaymentsOutputQueue。</span><span class="sxs-lookup"><span data-stu-id="282ff-160">The adapter version and inline version uses the same MQSeries queue, LastPaymentsOutputQueue.</span></span> <span data-ttu-id="282ff-161">若要避免兩個版本之間出現競爭條件，請停用 MQSeries 佇列上配接器版本的接收位置待命。</span><span class="sxs-lookup"><span data-stu-id="282ff-161">To avoid the race condition between two versions, disable the adapter version's receive location listening on the MQSeries queue.</span></span>  
  
3.  <span data-ttu-id="282ff-162">開啟命令提示字元，將目錄變更\< *BizTalk Server 安裝目錄*> \SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release，，然後執行 BTSScnSOSimpleClient.exe。</span><span class="sxs-lookup"><span data-stu-id="282ff-162">Open a command prompt, change the directory to the \<*BizTalk Server install Directory*>\SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release, and then run the BTSScnSOSimpleClient.exe.</span></span>  
  
4.  <span data-ttu-id="282ff-163">在 BTSScnSOSimpleClient.exe 中，使用下列方式透過 SOAP 傳輸傳送要求：</span><span class="sxs-lookup"><span data-stu-id="282ff-163">In the BTSScnSOSimpleClient.exe, send a request by SOAP transport using the as follows:</span></span>  
  
    1.  <span data-ttu-id="282ff-164">輸入任何字元**RequestType**， **[requestsource]**，和**RequestID**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-164">Type any characters in the **RequestType**, **RequestSource**, and **RequestID** text boxes.</span></span>  
  
    2.  <span data-ttu-id="282ff-165">輸入任何 16 位數的數字中**帳戶號碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-165">Type any 16-digit number in the **Account Number** text box.</span></span>  
  
    3.  <span data-ttu-id="282ff-166">選取**SOAP (WS Call)**和**內嵌**中**選取傳輸與參數**群組方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-166">Select **SOAP (WS Call)** and **Inline** in the **Select Transport and Parameters** group box.</span></span>  
  
    4.  <span data-ttu-id="282ff-167">輸入下列 URL 中的**URL**文字方塊中，例如：</span><span class="sxs-lookup"><span data-stu-id="282ff-167">Type the following URL in the **URL** text box, for example:</span></span>  
  
         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline/CustomerServicePort.asmx`  
  
    5.  <span data-ttu-id="282ff-168">型別`ZipCode`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-168">Type `ZipCode` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    6.  <span data-ttu-id="282ff-169">型別`CustomerName`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-169">Type `CustomerName` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    7.  <span data-ttu-id="282ff-170">按一下**取得我的平衡**。</span><span class="sxs-lookup"><span data-stu-id="282ff-170">Click **Get my balance**.</span></span>  
  
    8.  <span data-ttu-id="282ff-171">回應會顯示在**回應**文字方塊：**成功**才會顯示已成功處理要求; 如果要求失敗，出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="282ff-171">The response is displayed in the **Response** text box: **SUCCESS** appears if the request is handled successfully; an error message appears if the request fails.</span></span>  
  
         <span data-ttu-id="282ff-172">![執行內嵌版本的用戶端應用程式](../core/media/soap-transport-inline.gif "SOAP_Transport_inline")</span><span class="sxs-lookup"><span data-stu-id="282ff-172">![Run the client application for the inline version](../core/media/soap-transport-inline.gif "SOAP_Transport_inline")</span></span>  
  
5.  <span data-ttu-id="282ff-173">在 BTSScnSOSimpleClient.exe 中，依下列方式透過 MQSeries 傳輸傳送要求：</span><span class="sxs-lookup"><span data-stu-id="282ff-173">In the BTSScnSOSimpleClient.exe, send requests by MQSeries transport as follows:</span></span>  
  
    1.  <span data-ttu-id="282ff-174">輸入任何字元**RequestType**， **[requestsource]**，和**RequestID**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-174">Type any characters in the **RequestType**, **RequestSource**, and **RequestID** text boxes.</span></span>  
  
    2.  <span data-ttu-id="282ff-175">輸入 16 位數數字中的**帳戶號碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-175">Type a 16-digit number in the **Account Number** text box.</span></span>  
  
    3.  <span data-ttu-id="282ff-176">選取**MQSeries**中**選取傳輸與參數**群組方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-176">Select **MQSeries** in the **Select Transport and Parameters** group box.</span></span>  
  
    4.  <span data-ttu-id="282ff-177">型別\<*佇列管理員名稱*> 中**佇列管理員**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-177">Type \<*Queue Manager Name*> in the **Queue Manager** text box.</span></span> <span data-ttu-id="282ff-178">Qm_<\<*您的電腦名稱*> 是預設值\<*佇列管理員名稱*>。</span><span class="sxs-lookup"><span data-stu-id="282ff-178">QM_\<*Your Computer Name*> is the default value for \<*Queue Manager Name*>.</span></span>  
  
    5.  <span data-ttu-id="282ff-179">型別`InlineSOAInputQueue`中**輸入佇列**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-179">Type `InlineSOAInputQueue` in the **Input Queue** text box.</span></span>  
  
    6.  <span data-ttu-id="282ff-180">型別`InlineSOAOutputQueue`中**輸出佇列**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-180">Type `InlineSOAOutputQueue` in the **Output Queue** text box.</span></span>  
  
    7.  <span data-ttu-id="282ff-181">型別\<*通道定義*> 中**通道定義**方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-181">Type \<*Channel Definition*> in the **Channel Definition** box.</span></span> <span data-ttu-id="282ff-182">S_\<*您的電腦名稱*> /TCP/\<*您的電腦名稱*> (1414) 是預設值為\<*通道定義*>。</span><span class="sxs-lookup"><span data-stu-id="282ff-182">S_\<*Your Computer Name*>/TCP/\<*Your Computer Name*>(1414) is the default value for \<*Channel Definition*>.</span></span>  
  
    8.  <span data-ttu-id="282ff-183">型別`ZipCode`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-183">Type `ZipCode` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    9. <span data-ttu-id="282ff-184">型別`CustomerName`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="282ff-184">Type `CustomerName` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    10. <span data-ttu-id="282ff-185">按一下**取得我的平衡**。</span><span class="sxs-lookup"><span data-stu-id="282ff-185">Click **Get my balance**.</span></span>  
  
    11. <span data-ttu-id="282ff-186">回應會顯示在**回應**文字方塊：**成功**才會顯示已成功處理要求; 如果要求失敗，出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="282ff-186">The response is displayed in the **Response** text box: **SUCCESS** appears if the request is handled successfully; an error message appears if the request fails.</span></span>  
  
         <span data-ttu-id="282ff-187">![執行內嵌版本的用戶端應用程式](../core/media/mqseries-transport-inline.gif "MQSeries_Transport_inline")</span><span class="sxs-lookup"><span data-stu-id="282ff-187">![Run the client application for the inline version](../core/media/mqseries-transport-inline.gif "MQSeries_Transport_inline")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="282ff-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="282ff-188">See Also</span></span>  
 <span data-ttu-id="282ff-189">[然後再安裝服務導向解決方案](../core/before-installing-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="282ff-189">[Before Installing the Service Oriented Solution](../core/before-installing-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="282ff-190">[How to Install 虛設常式版本的服務導向解決方案](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="282ff-190">[How to Install the Stub Version of the Service Oriented Solution](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="282ff-191">[如何安裝內嵌和配接器版本的服務導向解決方案](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="282ff-191">[How to Install the Inline and Adapter Versions of the Service Oriented Solution](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="282ff-192">開發人員電腦設定為服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="282ff-192">Developer Machine Setup for the Service Oriented Solution</span></span>](../core/developer-machine-setup-for-the-service-oriented-solution.md)