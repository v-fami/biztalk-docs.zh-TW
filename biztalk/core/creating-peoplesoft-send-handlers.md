---
title: "建立 PeopleSoft 配接器傳送成品 |Microsoft 文件"
description: "建立傳送埠、 傳送的傳輸屬性，並更新將訊息傳送至 BizTalk Server 中使用 PeopleSoft Enterprise 配接器的 PeopleSoft 的同時呼叫數目上限"
ms.custom: 
ms.date: 10/19/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce67da59-26a6-44a2-929c-ed3acb21d407
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bc559f4e3c25560540a171b3f47ff25e6f34e89
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="create-peoplesoft-send-artifacts"></a><span data-ttu-id="6a275-103">建立 PeopleSoft 傳送成品</span><span class="sxs-lookup"><span data-stu-id="6a275-103">Create PeopleSoft send artifacts</span></span>
<span data-ttu-id="6a275-104">Microsoft BizTalk Adapter for PeopleSoft Enterprise 會存取 PeopleSoft 並探索可用的元件，或是處理 SOAP 要求。</span><span class="sxs-lookup"><span data-stu-id="6a275-104">Microsoft BizTalk Adapter for PeopleSoft Enterprise accesses PeopleSoft and explores available components or processes SOAP requests.</span></span> <span data-ttu-id="6a275-105">本主題說明如何在使用 PeopleSoft 配接器的 BizTalk Server 管理 中建立的傳送成品。</span><span class="sxs-lookup"><span data-stu-id="6a275-105">This topic shows you how to create the send artifacts in BizTalk Server Administration to use the PeopleSoft adapter.</span></span>


## <a name="create-the-send-port"></a><span data-ttu-id="6a275-106">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="6a275-106">Create the send port</span></span>

1.  <span data-ttu-id="6a275-107">在 BizTalk Server 管理主控台中，展開**BizTalk 群組**，依序展開**應用程式**，然後展開所需的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a275-107">In the BizTalk Server Administration Console,expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="6a275-108">以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="6a275-108">Right-click **Send Ports**, select **New**, and then select **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="6a275-109">在**傳送埠屬性**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6a275-109">In the **Send Port Properties**, do the following:</span></span>  
  
    1.  <span data-ttu-id="6a275-110">輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="6a275-110">Enter a name for the send port.</span></span> <span data-ttu-id="6a275-111">例如，輸入`SSOSendToPeopleSoft`。</span><span class="sxs-lookup"><span data-stu-id="6a275-111">For example, enter `SSOSendToPeopleSoft`.</span></span>  
  
    2.  <span data-ttu-id="6a275-112">從**類型**下拉式清單中，選取**PeopleSoft**。</span><span class="sxs-lookup"><span data-stu-id="6a275-112">From the **Type** drop-down list, select **PeopleSoft**.</span></span>  
  
    3.  <span data-ttu-id="6a275-113">從**傳送處理常式**下拉式清單中，選取 URI。</span><span class="sxs-lookup"><span data-stu-id="6a275-113">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="6a275-114">從 傳送管線 下拉式清單中，選取  **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="6a275-114">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="6a275-115">從**接收管線**下拉式清單中，選取**[microsoft.biztalk.defaultpiplelines.xmlreceive]**。</span><span class="sxs-lookup"><span data-stu-id="6a275-115">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
    6.  <span data-ttu-id="6a275-116">選取**設定**以設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="6a275-116">Select **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="6a275-117">在**PeopleSoft 傳輸屬性**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6a275-117">In the **PeopleSoft Transport Properties**, do the following:</span></span>  
  
    1.  <span data-ttu-id="6a275-118">展開**配接器必要屬性**，並輸入**應用程式伺服器路徑**， **JAVA_HOME**，**使用者名**， **密碼**，以及 Jar 檔案，以連接至 Peoplesoft 系統。</span><span class="sxs-lookup"><span data-stu-id="6a275-118">Expand **Adapter Required Properties**, and enter **Application Server Path**, **JAVA_HOME**, **user name**, **password**, and the Jar file for connecting into the Peoplesoft system.</span></span>  
  
         <span data-ttu-id="6a275-119">您不需要設定登入資訊。</span><span class="sxs-lookup"><span data-stu-id="6a275-119">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="6a275-120">在此清單中，選取您建立用來代表 PeopleSoft 系統的 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a275-120">In the list, select the SSO affiliate application you created to represent the PeopleSoft system.</span></span>  
  
    3.  <span data-ttu-id="6a275-121">如**使用 SSO**，選取**是**。</span><span class="sxs-lookup"><span data-stu-id="6a275-121">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="6a275-122">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="6a275-122">Select **OK**.</span></span>  
  
5.  <span data-ttu-id="6a275-123">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="6a275-123">Select **OK**.</span></span>

## <a name="set-the-transport-properties"></a><span data-ttu-id="6a275-124">設定傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="6a275-124">Set the transport properties</span></span>
<span data-ttu-id="6a275-125">PeopleSoft 傳輸屬性用於設計和執行階段。</span><span class="sxs-lookup"><span data-stu-id="6a275-125">The PeopleSoft transport properties are used for design and run time.</span></span> <span data-ttu-id="6a275-126">在**傳輸屬性**對話方塊中，您設定的連接和認證參數特定伺服器系統和您嘗試存取的物件。</span><span class="sxs-lookup"><span data-stu-id="6a275-126">In the **Transport Properties** dialog box, you set the connection and credential parameters specific to the server system and the objects you are trying to access.</span></span>  
  
 <span data-ttu-id="6a275-127">![](../core/media/peop-peoplesofttransportpropertiess.gif "Peop_PeopleSoftTransportPropertiess")</span><span class="sxs-lookup"><span data-stu-id="6a275-127">![](../core/media/peop-peoplesofttransportpropertiess.gif "Peop_PeopleSoftTransportPropertiess")</span></span>  
  
1.  <span data-ttu-id="6a275-128">展開 [配接器必要屬性]，並填入連線至 PeopleSoft 伺服器的所有必要資訊。</span><span class="sxs-lookup"><span data-stu-id="6a275-128">Expand the Adapter Required Properties and fill in all required information for connection to the PeopleSoft server.</span></span>  
  
     <span data-ttu-id="6a275-129">您必須設定組態參數，Microsoft BizTalk Adapter for PeopleSoft Enterprise 才能連線至 PeopleSoft Enterprise。</span><span class="sxs-lookup"><span data-stu-id="6a275-129">You must set configuration parameters to connect Microsoft BizTalk Adapter for PeopleSoft Enterprise to PeopleSoft Enterprise.</span></span> <span data-ttu-id="6a275-130">此資料區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="6a275-130">This data is case sensitive.</span></span>  
  
    |<span data-ttu-id="6a275-131">參數</span><span class="sxs-lookup"><span data-stu-id="6a275-131">Parameter</span></span>|<span data-ttu-id="6a275-132">Description</span><span class="sxs-lookup"><span data-stu-id="6a275-132">Description</span></span>|  
    |---------------|-----------------|  
    |`Application Server Path`|<span data-ttu-id="6a275-133">字串，表示執行 PeopleSoft Application Server 的電腦和接聽的連接埠。</span><span class="sxs-lookup"><span data-stu-id="6a275-133">A string representing the computer and port on which the PeopleSoft Application Server is running and listening.</span></span> <span data-ttu-id="6a275-134">PeopleSoft 8 應用程式的 URL 路徑的語法是 / / < 電腦名稱 >:\<連接埠\>。</span><span class="sxs-lookup"><span data-stu-id="6a275-134">The syntax of the URL path to the PeopleSoft 8 Application is //<computer_name>:\<port\>.</span></span> <span data-ttu-id="6a275-135">詢問您的 PeopleSoft 系統管理員以\<連接埠\>值。</span><span class="sxs-lookup"><span data-stu-id="6a275-135">Ask your PeopleSoft administrator for the \<port\> value.</span></span> <span data-ttu-id="6a275-136">\<連接埠\>值是 JOLT 通訊協定接聽程式通訊埠，不應用程式伺服器連接埠。</span><span class="sxs-lookup"><span data-stu-id="6a275-136">The \<port\> value is the JOLT protocol listener port, not the App Server port.</span></span> <span data-ttu-id="6a275-137">預設 JOLT 連接埠為 9000。</span><span class="sxs-lookup"><span data-stu-id="6a275-137">The default JOLT port is 9000.</span></span>|  
    |`JAVA_HOME`|<span data-ttu-id="6a275-138">設定 JAVA_HOME 變數以指向 JDK 安裝，例如： **C:\j2sdk1.4.2_08**。</span><span class="sxs-lookup"><span data-stu-id="6a275-138">Set the JAVA_HOME variable to point to your JDK installation, for example: **C:\j2sdk1.4.2_08**.</span></span>|  
    |`Password`|<span data-ttu-id="6a275-139">如果您未選取**使用 SSO**，您必須設定 BizTalk Adapter for PeopleSoft Enterprise 能夠存取伺服器系統的認證參數。</span><span class="sxs-lookup"><span data-stu-id="6a275-139">If you did not select **Use SSO**, you must set credential parameters for the BizTalk Adapter for PeopleSoft Enterprise to access the server system.</span></span><br /><br /> <span data-ttu-id="6a275-140">字串，表示使用者用來登入 PeopleSoft 系統的密碼。</span><span class="sxs-lookup"><span data-stu-id="6a275-140">A string representing the user's password for logon to a PeopleSoft system.</span></span> <span data-ttu-id="6a275-141">字元不會顯示出來，而是以星號 (*) 表示。</span><span class="sxs-lookup"><span data-stu-id="6a275-141">The characters do not appear but are represented by asterisks (*).</span></span>|  
    |`PeopleSoft 8.x Jar Files`|<span data-ttu-id="6a275-142">若要使用 Ccmponent 介面 (僅限 PeopleSoft 8)，您必須更新 CLASSPATH 來包含 PeopleSoft 元件介面 jar 檔案。</span><span class="sxs-lookup"><span data-stu-id="6a275-142">To use Ccmponent interfaces (PeopleSoft 8 only) you must update your CLASSPATH to include the PeopleSoft Component Interface jar file.</span></span> <span data-ttu-id="6a275-143">例如： **< PeopleSoft_Home > \web\PSJOA\psjoa.jar**。</span><span class="sxs-lookup"><span data-stu-id="6a275-143">For example: **<PeopleSoft_Home>\web\PSJOA\psjoa.jar**.</span></span>|  
    |`User Name`|<span data-ttu-id="6a275-144">如果您未選取**使用 SSO**，您必須設定 BizTalk Adapter for PeopleSoft Enterprise 能夠存取伺服器系統的認證參數。</span><span class="sxs-lookup"><span data-stu-id="6a275-144">If you did not select **Use SSO**, you must set credential parameters for the BizTalk Adapter for PeopleSoft Enterprise to access the server system.</span></span><br /><br /> <span data-ttu-id="6a275-145">字串，表示登入 PeopleSoft 系統所需的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="6a275-145">A string representing a user name required for logon to a PeopleSoft system.</span></span>|  
  
2.  <span data-ttu-id="6a275-146">輸入**其他參數**時使用日期做為索引鍵的值; 它有不同的格式。</span><span class="sxs-lookup"><span data-stu-id="6a275-146">Enter an **Additional parameters** value when a date is used as a key; it has a different format.</span></span> <span data-ttu-id="6a275-147">YYYY-MM-DD 是預設格式。</span><span class="sxs-lookup"><span data-stu-id="6a275-147">YYYY-MM-DD is the default format.</span></span>  
  
3.  <span data-ttu-id="6a275-148">輸入**並行控制**值中代表的呼叫，例如 200，**同時呼叫數目上限**如有必要。</span><span class="sxs-lookup"><span data-stu-id="6a275-148">Enter a **Concurrency control** value representing the number of calls, for example 200, in **Max Concurrent Calls** if it is required.</span></span>  
  
     <span data-ttu-id="6a275-149">**同時呼叫數目上限**參數啟動的多載保護，如果後端伺服器無法處理的資料量。</span><span class="sxs-lookup"><span data-stu-id="6a275-149">The **Max Concurrent Calls** parameter activates an overload protection if the back-end server cannot process the amount of data.</span></span> <span data-ttu-id="6a275-150">同時呼叫是指配接器尚未回覆的要求。</span><span class="sxs-lookup"><span data-stu-id="6a275-150">A concurrent call is a request for which the adapter does not yet have a reply.</span></span> <span data-ttu-id="6a275-151">設定**同時呼叫數目上限**在輸送量超過後端處理能力。</span><span class="sxs-lookup"><span data-stu-id="6a275-151">Set **Max Concurrent Calls** in instances where the throughput exceeds back-end processing capabilities.</span></span>  
  
     <span data-ttu-id="6a275-152">此欄位 的預設值為 -1，表示不會提供保護 。</span><span class="sxs-lookup"><span data-stu-id="6a275-152">The default value for this field is -1, meaning no protection occurs.</span></span>  
  
     <span data-ttu-id="6a275-153">如果 BizTalk Server 提交要求至傳輸配接器的並行連線數目呼叫等於或超過設定的值**同時呼叫數目上限**、 送出要求會儲存，直到同時呼叫數目的執行緒若要減少設定值以下。</span><span class="sxs-lookup"><span data-stu-id="6a275-153">If BizTalk Server submits a request to the Transmit adapter, and the number of concurrent calls equals or exceeds the value set for **Max Concurrent Calls**, the thread submitting the request is saved until the concurrent calls number decreases to below the set value.</span></span>  

## <a name="update-max-concurrent-calls"></a><span data-ttu-id="6a275-154">更新最大並行呼叫</span><span class="sxs-lookup"><span data-stu-id="6a275-154">Update Max Concurrent Calls</span></span>

<span data-ttu-id="6a275-155">`Max Concurrent Calls` 參數是一項可讓您最佳化組態的功能。</span><span class="sxs-lookup"><span data-stu-id="6a275-155">The `Max Concurrent Calls` parameter is a feature that enables you to optimize your configuration.</span></span> <span data-ttu-id="6a275-156">您可以在輸送量超過後端處理能力的情況下使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="6a275-156">You use this parameter in instances where the throughput exceeds back-end processing capabilities.</span></span> <span data-ttu-id="6a275-157">您可以將參數新增到中的配接器**傳送埠傳輸屬性**對話方塊，即可啟動訊息多載保護。</span><span class="sxs-lookup"><span data-stu-id="6a275-157">You can add the parameter to the adapters in the **Send Port Transport Properties** dialog box to activate message overload protection.</span></span> <span data-ttu-id="6a275-158">預設值為 -1，表示呼叫沒有上限。</span><span class="sxs-lookup"><span data-stu-id="6a275-158">The default is -1, meaning the calls are unlimited.</span></span>  
  
<span data-ttu-id="6a275-159">當 BizTalk Server 提交訊息給傳輸配接器時，它會先從配接器接收批次，然後在該批次上叫用 `TransmitMessage()` 來傳輸每個訊息。</span><span class="sxs-lookup"><span data-stu-id="6a275-159">When BizTalk Server submits messages to the transmit adapter, it first receives a batch from the adapter and invokes `TransmitMessage()` on the batch to transmit each message.</span></span> <span data-ttu-id="6a275-160">完成傳輸時，BizTalk Server 會在批次上叫用 `Done()`，這時配接器就會開始將訊息傳輸至後端。</span><span class="sxs-lookup"><span data-stu-id="6a275-160">When done, BizTalk Server invokes `Done()` on the batch, and the adapter starts transmitting the messages to the back-end.</span></span> <span data-ttu-id="6a275-161">如果 BizTalk Server 在叫用 `Done` 之前會取得多個批次，`Done` 命令可能就永遠不會發生。</span><span class="sxs-lookup"><span data-stu-id="6a275-161">If BizTalk Server obtains multiple batches before `Done` is invoked, the `Done` command might never occur.</span></span> <span data-ttu-id="6a275-162">藉由設定批次中的訊息數目上限，您便可以控制送到後端的訊息。</span><span class="sxs-lookup"><span data-stu-id="6a275-162">By setting the maximum number of messages in a batch, you can control messages to the back-end.</span></span> <span data-ttu-id="6a275-163">此參數的變更會立刻生效。</span><span class="sxs-lookup"><span data-stu-id="6a275-163">Changing this parameter takes effect in a minute.</span></span> <span data-ttu-id="6a275-164">BizTalk Server 必須擷取 SQL 資料庫中儲存的配接器組態變更。</span><span class="sxs-lookup"><span data-stu-id="6a275-164">BizTalk Server must retrieve the changes to the adapter configuration that is saved in the SQL database.</span></span>  
  
### <a name="change-the-max-concurrent-calls-parameter"></a><span data-ttu-id="6a275-165">變更同時呼叫數目上限參數</span><span class="sxs-lookup"><span data-stu-id="6a275-165">Change the Max Concurrent Calls parameter</span></span>  
  
1.  <span data-ttu-id="6a275-166">在**傳送埠傳輸屬性**對話方塊方塊中，輸入**連接**值。</span><span class="sxs-lookup"><span data-stu-id="6a275-166">In the **Send Port Transport Properties** dialog box, enter a **Connection** value.</span></span>  
  
     <span data-ttu-id="6a275-167">預設值為 40 個工作階段。</span><span class="sxs-lookup"><span data-stu-id="6a275-167">The default value is 40 sessions.</span></span> <span data-ttu-id="6a275-168">如果您使用較小的值，則可能會遇到執行階段效能降低的情形。</span><span class="sxs-lookup"><span data-stu-id="6a275-168">If you use a smaller value, you might experience degradation in run-time performance.</span></span> <span data-ttu-id="6a275-169">使用較大的值也是一樣，因為較大的值會超出伺服器的能力，而造成執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="6a275-169">The opposite is also true; a bigger value could exceed the ability of the server and result in run-time errors.</span></span>  
  
2.  <span data-ttu-id="6a275-170">選取**是**如**重新整理代理程式**強制 runtimeagent.exe 和 browsingagent.exe 程序在必要時自動重新啟動。</span><span class="sxs-lookup"><span data-stu-id="6a275-170">Select **Yes** for **Refresh Agent** to force the runtimeagent.exe and the browsingagent.exe processes to restart automatically when required.</span></span>  
  
     <span data-ttu-id="6a275-171">例如，您希望處理程序在與伺服器中斷連線時自動重新啟動，或是您在伺服器加上其他項目，但是該項目並未出現在 Microsoft 配接器精靈的選項中。</span><span class="sxs-lookup"><span data-stu-id="6a275-171">For example, you want the process to restart automatically if it loses connection with the server, or if you add something to the server and it does not appear in the Microsoft Adapter Wizard for selection.</span></span>  
  
     <span data-ttu-id="6a275-172">**重新整理代理程式**參數會重新整理瀏覽與執行階段代理程式。</span><span class="sxs-lookup"><span data-stu-id="6a275-172">The **Refresh Agent** parameter refreshes both the browsing and the run-time agents.</span></span> <span data-ttu-id="6a275-173">runtimeagent.exe 會在一分鐘之後或是下一次呼叫 Send 時更新。</span><span class="sxs-lookup"><span data-stu-id="6a275-173">The runtimeagent.exe updates after a delay of one minute or at the next send call.</span></span>  
  
3.  <span data-ttu-id="6a275-174">提供認證以存取 PeopleSoft 系統。</span><span class="sxs-lookup"><span data-stu-id="6a275-174">Provide credentials to access the PeopleSoft system.</span></span>  
  
     <span data-ttu-id="6a275-175">您可以透過兩種方式來存取系統：</span><span class="sxs-lookup"><span data-stu-id="6a275-175">You can use two methods to access the system:</span></span>  
  
    -   <span data-ttu-id="6a275-176">登入認證 (傳輸屬性登入參數)</span><span class="sxs-lookup"><span data-stu-id="6a275-176">Login Credentials (Transport Properties Login parameters)</span></span>  
  
    -   <span data-ttu-id="6a275-177">單一登入 (SSO)</span><span class="sxs-lookup"><span data-stu-id="6a275-177">Single Sign-On</span></span>  
  
4.  <span data-ttu-id="6a275-178">選取**是**如**使用 SSO**使用單一登入。</span><span class="sxs-lookup"><span data-stu-id="6a275-178">Select **Yes** for **Use SSO** to use Single Sign-On.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6a275-179">如需詳細資訊，請參閱[安全配接器](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)。</span><span class="sxs-lookup"><span data-stu-id="6a275-179">For more information, see [Secure the adapter](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md).</span></span> 
  
5.  <span data-ttu-id="6a275-180">在清單中選取分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a275-180">Select an affiliate application in the list.</span></span>  
  
     <span data-ttu-id="6a275-181">由企業單一登入工具所建立的分支機構應用程式，代表像是 PeopleSoft 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a275-181">An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as PeopleSoft.</span></span> <span data-ttu-id="6a275-182">Microsoft BizTalk Adapter for PeopleSoft Enterprise 會使用應用程式使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="6a275-182">Microsoft BizTalk Adapter for PeopleSoft Enterprise uses the credentials of an application user.</span></span> <span data-ttu-id="6a275-183">這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。</span><span class="sxs-lookup"><span data-stu-id="6a275-183">These credentials are retrieved from the SSO database for the server system for a specified affiliate application.</span></span> <span data-ttu-id="6a275-184">這些認證就是啟動 BizTalk 專案之使用者 (應用程式使用者) 的認證。</span><span class="sxs-lookup"><span data-stu-id="6a275-184">The credentials are those of the user (the application user) who launched the BizTalk project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6a275-185">如需如何建立分支機構應用程式的詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications2.md)，或 Microsoft BizTalk Server 線上說明。</span><span class="sxs-lookup"><span data-stu-id="6a275-185">For more information about how to create affiliate applications, see [Creating Affiliate Applications](../core/creating-affiliate-applications2.md), or the Microsoft BizTalk Server online Help.</span></span>  
  
6.  <span data-ttu-id="6a275-186">提供所有必要的資訊，以採用連線資訊之後, 按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6a275-186">After providing all required information to accept the connection information, click **Apply**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="6a275-187">您必須設定連線參數，讓 BizTalk Adapter for PeopleSoft Enterprise 能夠存取 PeopleSoft。</span><span class="sxs-lookup"><span data-stu-id="6a275-187">You must set connection parameters for the BizTalk Adapter for PeopleSoft Enterprise to access PeopleSoft.</span></span>  
  

## <a name="next"></a><span data-ttu-id="6a275-188">下一個</span><span class="sxs-lookup"><span data-stu-id="6a275-188">Next</span></span>
  
[<span data-ttu-id="6a275-189">PeopleSoft 結構描述匯入至 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="6a275-189">Import PeopleSoft Schemas into BizTalk Server Projects</span></span>](../core/importing-peoplesoft-schemas-into-biztalk-server-projects.md)  
[<span data-ttu-id="6a275-190">從 PeopleSoft 接收</span><span class="sxs-lookup"><span data-stu-id="6a275-190">Receive from PeopleSoft</span></span>](../core/receiving-from-peoplesoft.md)