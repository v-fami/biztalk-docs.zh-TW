---
title: 如何執行服務導向解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service solution tutorial, client applications
- service solution tutorial, starting solution
- service solution tutorial, sending requests
- service solution tutorial, SOAP transports
ms.assetid: 764a5ddc-e571-41d8-9e2f-6d0fb3361b2f
caps.latest.revision: 31
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35c33b914ecbb9f385e5546d100b7572b4b48b6a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973812"
---
# <a name="how-to-run-the-service-oriented-solution"></a><span data-ttu-id="f23d3-102">如何執行服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="f23d3-102">How to Run the Service Oriented Solution</span></span>
<span data-ttu-id="f23d3-103">下列步驟描述如何在單一電腦上執行和驗證服務導向解決方案。</span><span class="sxs-lookup"><span data-stu-id="f23d3-103">The following steps describe how to run and validate the service oriented solution on a single computer.</span></span> <span data-ttu-id="f23d3-104">啟動付款追蹤器模擬器之後，使用 SOAP 或 MQSeries 傳輸來傳送要求 (服務導向解決方案的配接器與內嵌版本分別使用個別程序)。</span><span class="sxs-lookup"><span data-stu-id="f23d3-104">After starting the Payment Tracker simulator, you can send requests using either the SOAP or MQSeries transport (with separate procedures for the adapter and inline versions of the service oriented solution).</span></span>  
  
-   [<span data-ttu-id="f23d3-105">使用用戶端應用程式 （虛設常式版本） 透過 SOAP 傳輸傳送要求</span><span class="sxs-lookup"><span data-stu-id="f23d3-105">Send requests by SOAP transport using the client application (stub version)</span></span>](#step1)  
  
-   [<span data-ttu-id="f23d3-106">使用用戶端應用程式 （配接器版本） 傳送要求</span><span class="sxs-lookup"><span data-stu-id="f23d3-106">Send requests using the client application (adapter version)</span></span>](#step3)  
  
-   [<span data-ttu-id="f23d3-107">使用用戶端應用程式 （內嵌版本） 傳送要求</span><span class="sxs-lookup"><span data-stu-id="f23d3-107">Send requests using the client application (inline version)</span></span>](#step5)  
  
##  <a name="step1"></a><span data-ttu-id="f23d3-108">使用用戶端應用程式 （虛設常式版本） 透過 SOAP 傳輸傳送要求</span><span class="sxs-lookup"><span data-stu-id="f23d3-108">Send requests by SOAP transport using the client application (stub version)</span></span>  
  
#### <a name="to-send-requests-by-soap-transport-using-the-client-application-stub-version"></a><span data-ttu-id="f23d3-109">使用用戶端應用程式 (虛設常式版本) 透過 SOAP 傳輸傳送要求</span><span class="sxs-lookup"><span data-stu-id="f23d3-109">To send requests by SOAP transport using the client application (stub version)</span></span>  
  
1.  <span data-ttu-id="f23d3-110">開啟命令提示字元，將目錄變更\< *BizTalk Server 安裝目錄*\>\SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release，，然後執行 BTSScnSOSimpleClient.exe。</span><span class="sxs-lookup"><span data-stu-id="f23d3-110">Open a command prompt, change the directory to the \<*BizTalk Server install Directory*\>\SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release, and then run the BTSScnSOSimpleClient.exe.</span></span>  
  
2.  <span data-ttu-id="f23d3-111">輸入任何字元**RequestType**， **[requestsource]**，和**RequestID**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-111">Type any characters in the **RequestType**, **RequestSource**, and **RequestID** text boxes.</span></span>  
  
3.  <span data-ttu-id="f23d3-112">輸入任何 16 位數的數字中**帳戶號碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-112">Type any 16-digit number in the **Account Number** text box.</span></span>  
  
4.  <span data-ttu-id="f23d3-113">選取**SOAP (WS Call)** 和**虛設常式**中**選取傳輸與參數**群組方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-113">Select **SOAP (WS Call)** and **Stub** in the **Select Transport and Parameters** group box.</span></span>  
  
5.  <span data-ttu-id="f23d3-114">輸入下列 URL 中的**URL**文字方塊中，例如：</span><span class="sxs-lookup"><span data-stu-id="f23d3-114">Type the following URL in the **URL** text box, for example:</span></span>  
  
6.  `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub/CustomerServicePort.asmx`  
  
7.  <span data-ttu-id="f23d3-115">型別`ZipCode`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-115">Type `ZipCode` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
8.  <span data-ttu-id="f23d3-116">型別`CustomerName`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-116">Type `CustomerName` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
9. <span data-ttu-id="f23d3-117">按一下**取得我的平衡**。</span><span class="sxs-lookup"><span data-stu-id="f23d3-117">Click **Get my balance**.</span></span>  
  
10. <span data-ttu-id="f23d3-118">回應會顯示在**回應**文字方塊：**成功**才會顯示已成功處理要求; 如果要求失敗，出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f23d3-118">The response is displayed in the **Response** text box: **SUCCESS** appears if the request is handled successfully; an error message appears if the request fails.</span></span>  
  
     <span data-ttu-id="f23d3-119">![執行虛設常式版本的用戶端應用程式](../core/media/bts-cp-so-deploy-stubversion-success.gif "BTS_CP_SO_Deploy_StubVersion_Success")</span><span class="sxs-lookup"><span data-stu-id="f23d3-119">![Run the client application for the stub version](../core/media/bts-cp-so-deploy-stubversion-success.gif "BTS_CP_SO_Deploy_StubVersion_Success")</span></span>  
  
##  <a name="step3"></a><span data-ttu-id="f23d3-120">使用用戶端應用程式 （配接器版本） 傳送要求</span><span class="sxs-lookup"><span data-stu-id="f23d3-120">Send requests using the client application (adapter version)</span></span>  
  
#### <a name="to-send-requests-using-the-client-application-adapter-version"></a><span data-ttu-id="f23d3-121">使用用戶端應用程式 (配接器版本) 傳送要求</span><span class="sxs-lookup"><span data-stu-id="f23d3-121">To send requests using the client application (adapter version)</span></span>  
  
1.  <span data-ttu-id="f23d3-122">開啟命令提示字元，將目錄變更\< *BizTalk Server 安裝目錄*\>\SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug，然後執行下列命令以啟動付款追蹤器模擬器：</span><span class="sxs-lookup"><span data-stu-id="f23d3-122">Open a command prompt, change the directory to \<*BizTalk Server install Directory*\>\SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug and, then run the following command to start the PaymentTracker simulator:</span></span>  
  
     <span data-ttu-id="f23d3-123">`BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <`*佇列管理員名稱* `> 5 [<` *通道定義*`>]`</span><span class="sxs-lookup"><span data-stu-id="f23d3-123">`BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <` *Queue Manager Name* `> 5 [<` *Channel Definition* `>]`</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f23d3-124">若不是 MQSeries Server，則通道定義為選擇性。</span><span class="sxs-lookup"><span data-stu-id="f23d3-124">The channel definition is optional if it is not remote MQSeries Server.</span></span>  
  
    -   <span data-ttu-id="f23d3-125">讓付款追蹤器模擬器繼續執行。</span><span class="sxs-lookup"><span data-stu-id="f23d3-125">Leave the Payment Tracker simulator running.</span></span>  
  
2.  <span data-ttu-id="f23d3-126">開啟命令提示字元，將目錄變更\< *BizTalk Server 安裝目錄*\>\SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release，，然後執行 BTSScnSOSimpleClient.exe。</span><span class="sxs-lookup"><span data-stu-id="f23d3-126">Open a command prompt, change the directory to the \<*BizTalk Server install Directory*\>\SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release, and then run the BTSScnSOSimpleClient.exe.</span></span>  
  
3.  <span data-ttu-id="f23d3-127">在 BTSScnSOSimpleClient.exe 中，使用下列方式透過 SOAP 傳輸傳送要求：</span><span class="sxs-lookup"><span data-stu-id="f23d3-127">In the BTSScnSOSimpleClient.exe, send a request by SOAP transport using the as follows:</span></span>  
  
    1.  <span data-ttu-id="f23d3-128">輸入任何字元**RequestType**， **[requestsource]**，和**RequestID**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-128">Type any characters in the **RequestType**, **RequestSource**, and **RequestID** text boxes.</span></span>  
  
    2.  <span data-ttu-id="f23d3-129">輸入任何 16 位數的數字中**帳戶號碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-129">Type any 16-digit number in the **Account Number** text box.</span></span>  
  
    3.  <span data-ttu-id="f23d3-130">選取**SOAP (WS Call)** 和**配接器**中**選取傳輸與參數**群組方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-130">Select **SOAP (WS Call)** and **Adapter** in the **Select Transport and Parameters** group box.</span></span>  
  
    4.  <span data-ttu-id="f23d3-131">輸入下列 URL 中的**URL**文字方塊中，例如：</span><span class="sxs-lookup"><span data-stu-id="f23d3-131">Type the following URL in the **URL** text box, for example:</span></span>  
  
         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter/CustomerServicePort.asmx`  
  
    5.  <span data-ttu-id="f23d3-132">型別`ZipCode`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-132">Type `ZipCode` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    6.  <span data-ttu-id="f23d3-133">型別`CustomerName`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-133">Type `CustomerName` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    7.  <span data-ttu-id="f23d3-134">按一下**取得我的平衡**。</span><span class="sxs-lookup"><span data-stu-id="f23d3-134">Click **Get my balance**.</span></span>  
  
    8.  <span data-ttu-id="f23d3-135">回應會顯示在**回應**文字方塊：**成功**才會顯示已成功處理要求; 如果要求失敗，出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f23d3-135">The response is displayed in the **Response** text box: **SUCCESS** appears if the request is handled successfully; an error message appears if the request fails.</span></span>  
  
         <span data-ttu-id="f23d3-136">![執行配接器版本的用戶端應用程式](../core/media/soap-transport-adapter-success.gif "SOAP_Transport_adapter_success")</span><span class="sxs-lookup"><span data-stu-id="f23d3-136">![Run the client application for the adapter version](../core/media/soap-transport-adapter-success.gif "SOAP_Transport_adapter_success")</span></span>  
  
4.  <span data-ttu-id="f23d3-137">在 BTSScnSOSimpleClient.exe 中，依下列方式透過 MQSeries 傳輸傳送要求：</span><span class="sxs-lookup"><span data-stu-id="f23d3-137">In the BTSScnSOSimpleClient.exe, send requests by MQSeries transport as follows:</span></span>  
  
    1.  <span data-ttu-id="f23d3-138">輸入任何字元**RequestType**， **[requestsource]**，和**RequestID**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-138">Type any characters in the **RequestType**, **RequestSource**, and **RequestID** text boxes.</span></span>  
  
    2.  <span data-ttu-id="f23d3-139">輸入 16 位數數字中的**帳戶號碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-139">Type a 16-digit number in the **Account Number** text box.</span></span>  
  
    3.  <span data-ttu-id="f23d3-140">選取**MQSeries**中**選取傳輸與參數**群組方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-140">Select **MQSeries** in the **Select Transport and Parameters** group box.</span></span>  
  
    4.  <span data-ttu-id="f23d3-141">型別\<*佇列管理員名稱*\>中**佇列管理員**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-141">Type \<*Queue Manager Name*\> in the **Queue Manager** text box.</span></span> <span data-ttu-id="f23d3-142">Qm_<\<*您的電腦名稱*\>是預設值\<*佇列管理員名稱*\>。</span><span class="sxs-lookup"><span data-stu-id="f23d3-142">QM_\<*Your Computer Name*\> is the default value for \<*Queue Manager Name*\>.</span></span>  
  
    5.  <span data-ttu-id="f23d3-143">型別`AdapterSOAInputQueue`中**輸入佇列**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-143">Type `AdapterSOAInputQueue` in the **Input Queue** text box.</span></span>  
  
    6.  <span data-ttu-id="f23d3-144">型別`AdapterSOAOutputQueue`中**輸出佇列**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-144">Type `AdapterSOAOutputQueue` in the **Output Queue** text box.</span></span>  
  
    7.  <span data-ttu-id="f23d3-145">型別\<*通道定義*\>中**通道定義**方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-145">Type \<*Channel Definition*\> in the **Channel Definition** box.</span></span> <span data-ttu-id="f23d3-146">S_\<*您的電腦名稱*\>/TCP/\<*您的電腦名稱*\>(1414) 是預設值為\< *通道定義*\>。</span><span class="sxs-lookup"><span data-stu-id="f23d3-146">S_\<*Your Computer Name*\>/TCP/\<*Your Computer Name*\>(1414) is the default value for \<*Channel Definition*\>.</span></span>  
  
    8.  <span data-ttu-id="f23d3-147">型別`ZipCode`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-147">Type `ZipCode` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    9. <span data-ttu-id="f23d3-148">型別`CustomerName`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-148">Type `CustomerName` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    10. <span data-ttu-id="f23d3-149">按一下**取得我的平衡**。</span><span class="sxs-lookup"><span data-stu-id="f23d3-149">Click **Get my balance**.</span></span>  
  
    11. <span data-ttu-id="f23d3-150">回應會顯示在**回應**文字方塊：**成功**才會顯示已成功處理要求; 如果要求失敗，出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f23d3-150">The response is displayed in the **Response** text box: **SUCCESS** appears if the request is handled successfully; an error message appears if the request fails.</span></span>  
  
         <span data-ttu-id="f23d3-151">![執行配接器版本的用戶端應用程式](../core/media/mqseries-transport-adapter.gif "MQSeries_Transport_adapter")</span><span class="sxs-lookup"><span data-stu-id="f23d3-151">![Run the client application for the adapter version](../core/media/mqseries-transport-adapter.gif "MQSeries_Transport_adapter")</span></span>  
  
##  <a name="step5"></a><span data-ttu-id="f23d3-152">使用用戶端應用程式 （內嵌版本） 傳送要求</span><span class="sxs-lookup"><span data-stu-id="f23d3-152">Send requests using the client application (inline version)</span></span>  
  
#### <a name="to-send-requests-using-the-client-application-inline-version"></a><span data-ttu-id="f23d3-153">使用用戶端應用程式 (內嵌版本) 傳送要求</span><span class="sxs-lookup"><span data-stu-id="f23d3-153">To send requests using the client application (inline version)</span></span>  
  
1.  <span data-ttu-id="f23d3-154">開啟命令提示字元，將目錄變更\< *BizTalk Server 安裝目錄*\>\SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug，，然後執行下列命令以啟動付款追蹤器模擬器：</span><span class="sxs-lookup"><span data-stu-id="f23d3-154">Open a command prompt, change the directory to \<*BizTalk Server install Directory*\>\SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug, and then run the following command to start the PaymentTracker simulator:</span></span>  
  
     <span data-ttu-id="f23d3-155">`BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <`*佇列管理員名稱* `> 5 [<` *通道定義*`>]`</span><span class="sxs-lookup"><span data-stu-id="f23d3-155">`BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <` *Queue Manager Name* `> 5 [<` *Channel Definition* `>]`</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f23d3-156">若不是 MQSeries Server，則通道定義為選擇性。</span><span class="sxs-lookup"><span data-stu-id="f23d3-156">The channel definition is optional if it is not remote MQSeries Server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f23d3-157">若付款追蹤器模擬器已經在執行中，請略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="f23d3-157">Skip this step if the PaymentTracker simulator is already running.</span></span>  
  
    -   <span data-ttu-id="f23d3-158">讓付款追蹤器模擬器繼續執行。</span><span class="sxs-lookup"><span data-stu-id="f23d3-158">Leave the Payment Tracker simulator running.</span></span>  
  
2.  <span data-ttu-id="f23d3-159">在**BizTalk Server 管理主控台**，依序展開**BTSScn.SO.CustomerService**，按一下 **接收位置**，以滑鼠右鍵按一下**Paymenttrackingsystemoutputqueue**在右窗格中，然後按一下**停用**。</span><span class="sxs-lookup"><span data-stu-id="f23d3-159">In the **BizTalk Server Administration Console**, expand **BTSScn.SO.CustomerService**, click **Receive Locations**, right-click **PaymentTrackingSystemOutputQueue** in the right pane, and then click **Disable**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f23d3-160">配接器版本和內嵌版本會使用相同的 MQSeries 佇列 LastPaymentsOutputQueue。</span><span class="sxs-lookup"><span data-stu-id="f23d3-160">The adapter version and inline version uses the same MQSeries queue, LastPaymentsOutputQueue.</span></span> <span data-ttu-id="f23d3-161">若要避免兩個版本之間出現競爭條件，請停用 MQSeries 佇列上配接器版本的接收位置待命。</span><span class="sxs-lookup"><span data-stu-id="f23d3-161">To avoid the race condition between two versions, disable the adapter version's receive location listening on the MQSeries queue.</span></span>  
  
3.  <span data-ttu-id="f23d3-162">開啟命令提示字元，將目錄變更\< *BizTalk Server 安裝目錄*\>\SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release，，然後執行 BTSScnSOSimpleClient.exe。</span><span class="sxs-lookup"><span data-stu-id="f23d3-162">Open a command prompt, change the directory to the \<*BizTalk Server install Directory*\>\SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release, and then run the BTSScnSOSimpleClient.exe.</span></span>  
  
4.  <span data-ttu-id="f23d3-163">在 BTSScnSOSimpleClient.exe 中，使用下列方式透過 SOAP 傳輸傳送要求：</span><span class="sxs-lookup"><span data-stu-id="f23d3-163">In the BTSScnSOSimpleClient.exe, send a request by SOAP transport using the as follows:</span></span>  
  
    1.  <span data-ttu-id="f23d3-164">輸入任何字元**RequestType**， **[requestsource]**，和**RequestID**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-164">Type any characters in the **RequestType**, **RequestSource**, and **RequestID** text boxes.</span></span>  
  
    2.  <span data-ttu-id="f23d3-165">輸入任何 16 位數的數字中**帳戶號碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-165">Type any 16-digit number in the **Account Number** text box.</span></span>  
  
    3.  <span data-ttu-id="f23d3-166">選取**SOAP (WS Call)** 和**內嵌**中**選取傳輸與參數**群組方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-166">Select **SOAP (WS Call)** and **Inline** in the **Select Transport and Parameters** group box.</span></span>  
  
    4.  <span data-ttu-id="f23d3-167">輸入下列 URL 中的**URL**文字方塊中，例如：</span><span class="sxs-lookup"><span data-stu-id="f23d3-167">Type the following URL in the **URL** text box, for example:</span></span>  
  
         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline/CustomerServicePort.asmx`  
  
    5.  <span data-ttu-id="f23d3-168">型別`ZipCode`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-168">Type `ZipCode` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    6.  <span data-ttu-id="f23d3-169">型別`CustomerName`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-169">Type `CustomerName` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    7.  <span data-ttu-id="f23d3-170">按一下**取得我的平衡**。</span><span class="sxs-lookup"><span data-stu-id="f23d3-170">Click **Get my balance**.</span></span>  
  
    8.  <span data-ttu-id="f23d3-171">回應會顯示在**回應**文字方塊：**成功**才會顯示已成功處理要求; 如果要求失敗，出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f23d3-171">The response is displayed in the **Response** text box: **SUCCESS** appears if the request is handled successfully; an error message appears if the request fails.</span></span>  
  
         <span data-ttu-id="f23d3-172">![執行內嵌版本的用戶端應用程式](../core/media/soap-transport-inline.gif "SOAP_Transport_inline")</span><span class="sxs-lookup"><span data-stu-id="f23d3-172">![Run the client application for the inline version](../core/media/soap-transport-inline.gif "SOAP_Transport_inline")</span></span>  
  
5.  <span data-ttu-id="f23d3-173">在 BTSScnSOSimpleClient.exe 中，依下列方式透過 MQSeries 傳輸傳送要求：</span><span class="sxs-lookup"><span data-stu-id="f23d3-173">In the BTSScnSOSimpleClient.exe, send requests by MQSeries transport as follows:</span></span>  
  
    1.  <span data-ttu-id="f23d3-174">輸入任何字元**RequestType**， **[requestsource]**，和**RequestID**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-174">Type any characters in the **RequestType**, **RequestSource**, and **RequestID** text boxes.</span></span>  
  
    2.  <span data-ttu-id="f23d3-175">輸入 16 位數數字中的**帳戶號碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-175">Type a 16-digit number in the **Account Number** text box.</span></span>  
  
    3.  <span data-ttu-id="f23d3-176">選取**MQSeries**中**選取傳輸與參數**群組方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-176">Select **MQSeries** in the **Select Transport and Parameters** group box.</span></span>  
  
    4.  <span data-ttu-id="f23d3-177">型別\<*佇列管理員名稱*\>中**佇列管理員**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-177">Type \<*Queue Manager Name*\> in the **Queue Manager** text box.</span></span> <span data-ttu-id="f23d3-178">Qm_<\<*您的電腦名稱*\>是預設值\<*佇列管理員名稱*\>。</span><span class="sxs-lookup"><span data-stu-id="f23d3-178">QM_\<*Your Computer Name*\> is the default value for \<*Queue Manager Name*\>.</span></span>  
  
    5.  <span data-ttu-id="f23d3-179">型別`InlineSOAInputQueue`中**輸入佇列**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-179">Type `InlineSOAInputQueue` in the **Input Queue** text box.</span></span>  
  
    6.  <span data-ttu-id="f23d3-180">型別`InlineSOAOutputQueue`中**輸出佇列**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-180">Type `InlineSOAOutputQueue` in the **Output Queue** text box.</span></span>  
  
    7.  <span data-ttu-id="f23d3-181">型別\<*通道定義*\>中**通道定義**方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-181">Type \<*Channel Definition*\> in the **Channel Definition** box.</span></span> <span data-ttu-id="f23d3-182">S_\<*您的電腦名稱*\>/TCP/\<*您的電腦名稱*\>(1414) 是預設值為\< *通道定義*\>。</span><span class="sxs-lookup"><span data-stu-id="f23d3-182">S_\<*Your Computer Name*\>/TCP/\<*Your Computer Name*\>(1414) is the default value for \<*Channel Definition*\>.</span></span>  
  
    8.  <span data-ttu-id="f23d3-183">型別`ZipCode`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-183">Type `ZipCode` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    9. <span data-ttu-id="f23d3-184">型別`CustomerName`中**名稱**底下的文字方塊**驗證項目**，然後輸入中的任何字元**值**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f23d3-184">Type `CustomerName` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    10. <span data-ttu-id="f23d3-185">按一下**取得我的平衡**。</span><span class="sxs-lookup"><span data-stu-id="f23d3-185">Click **Get my balance**.</span></span>  
  
    11. <span data-ttu-id="f23d3-186">回應會顯示在**回應**文字方塊：**成功**才會顯示已成功處理要求; 如果要求失敗，出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f23d3-186">The response is displayed in the **Response** text box: **SUCCESS** appears if the request is handled successfully; an error message appears if the request fails.</span></span>  
  
         <span data-ttu-id="f23d3-187">![執行內嵌版本的用戶端應用程式](../core/media/mqseries-transport-inline.gif "MQSeries_Transport_inline")</span><span class="sxs-lookup"><span data-stu-id="f23d3-187">![Run the client application for the inline version](../core/media/mqseries-transport-inline.gif "MQSeries_Transport_inline")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f23d3-188">請參閱</span><span class="sxs-lookup"><span data-stu-id="f23d3-188">See Also</span></span>  
 <span data-ttu-id="f23d3-189">[然後再安裝服務導向解決方案](../core/before-installing-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="f23d3-189">[Before Installing the Service Oriented Solution](../core/before-installing-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="f23d3-190">[How to Install 虛設常式版本的服務導向解決方案](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="f23d3-190">[How to Install the Stub Version of the Service Oriented Solution](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="f23d3-191">[如何安裝內嵌和配接器版本的服務導向解決方案](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="f23d3-191">[How to Install the Inline and Adapter Versions of the Service Oriented Solution](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="f23d3-192">服務導向解決方案的開發人員電腦設定</span><span class="sxs-lookup"><span data-stu-id="f23d3-192">Developer Machine Setup for the Service Oriented Solution</span></span>](../core/developer-machine-setup-for-the-service-oriented-solution.md)