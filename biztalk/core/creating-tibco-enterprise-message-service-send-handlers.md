---
title: 建立 TIBCO EMS 傳送成品 |Microsoft 文件
description: 建立傳送埠，並設定在 BizTalk Server 使用 TIBCO Enterprise Message Service 配接器的傳輸屬性
ms.custom: ''
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f82609c-1847-4796-a24c-28cb350ec739
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 570693f4d5644f0ea850a53ec537ce30db5ca568
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24014181"
---
# <a name="creating--tibco-enterprise-message-service-send-handlers"></a><span data-ttu-id="96331-103">建立 TIBCO 企業訊息服務傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="96331-103">Creating  TIBCO Enterprise Message Service Send Handlers</span></span>
<span data-ttu-id="96331-104">本節說明如何設定傳送埠以連線至 TIBCO Enterprise Message Service (EMS)，以及如何在協調流程中納入 XML 以在執行階段與 TIBCO EMS 互動。</span><span class="sxs-lookup"><span data-stu-id="96331-104">This section explains how to set the send port to connect to TIBCO Enterprise Message Service (EMS) and how to include XML in your orchestration to interact with TIBCO EMS at run time.</span></span>  


## <a name="create-a-send-port"></a><span data-ttu-id="96331-105">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="96331-105">Create a send port</span></span>  
  
1.  <span data-ttu-id="96331-106">在 BizTalk Server 管理主控台中，展開**BizTalk 群組**，依序展開**應用程式**，然後展開您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="96331-106">In the BizTalk Server Administration Console, expand **BizTalk Group**, expand **Applications**, and then expand your application.</span></span>  
  
2.  <span data-ttu-id="96331-107">以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="96331-107">Right-click **Send Ports**, select **New**, and then select **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="96331-108">在**傳送埠屬性**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="96331-108">In the **Send Port Properties**, do the following:</span></span>  
  
    1.  <span data-ttu-id="96331-109">輸入傳送埠名稱，例如`SendToTIBCOEMS`。</span><span class="sxs-lookup"><span data-stu-id="96331-109">Type a name for the send port, for example, `SendToTIBCOEMS`.</span></span>  
  
    2.  <span data-ttu-id="96331-110">從**類型**下拉式清單中，選取**TIBCO EMS**。</span><span class="sxs-lookup"><span data-stu-id="96331-110">From the **Type** drop-down list, select **TIBCO EMS**.</span></span>  
  
    3.  <span data-ttu-id="96331-111">從**傳送處理常式**下拉式清單中，選取 URI。</span><span class="sxs-lookup"><span data-stu-id="96331-111">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="96331-112">從**傳送管線**下拉式清單中，選取**Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="96331-112">From the **Send Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span> <span data-ttu-id="96331-113">從**接收管線**下拉式清單中，選取 **[microsoft.biztalk.defaultpiplelines.xmlreceive]**。</span><span class="sxs-lookup"><span data-stu-id="96331-113">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  

        > [!NOTE]
        > <span data-ttu-id="96331-114">BizTalk Adapter for TIBCO Enterprise Message Service 需要傳送 和 xmlreceive 選取 xmltransmit，用於接收。</span><span class="sxs-lookup"><span data-stu-id="96331-114">The BizTalk Adapter for TIBCO Enterprise Message Service requires that you select XMLTransmit for send, and XMLReceive for receive.</span></span>  
  
    6.  <span data-ttu-id="96331-115">選取**設定**以設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="96331-115">Select **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="96331-116">在**TIBCO EMS 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="96331-116">In the **TIBCO EMS Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="96331-117">輸入**訊息處理**，**伺服器連線定義**，**交易支援**， **Username**，而**密碼**。</span><span class="sxs-lookup"><span data-stu-id="96331-117">Enter **Message Handling**, **Server Connection Definition**, **Transaction Support**, **Username**, and the **password**.</span></span>  
  
         <span data-ttu-id="96331-118">您不需要設定登入資訊。</span><span class="sxs-lookup"><span data-stu-id="96331-118">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="96331-119">在此清單中，選取您建立用來代表 TIBCO EMS 系統的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="96331-119">In the list, select the affiliate application you created to represent the TIBCO EMS system.</span></span>  
  
    3.  <span data-ttu-id="96331-120">如**使用 SSO**，選取**是**。</span><span class="sxs-lookup"><span data-stu-id="96331-120">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="96331-121">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="96331-121">Select **OK**.</span></span>  
  
5.  <span data-ttu-id="96331-122">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="96331-122">Select **OK**.</span></span> 

## <a name="set-send-port-transport-properties"></a><span data-ttu-id="96331-123">設定傳送埠傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="96331-123">Set send port transport properties</span></span>
<span data-ttu-id="96331-124">TIBCO Enterprise Message Service 傳輸屬性是在設計階段設定、在執行階段使用。</span><span class="sxs-lookup"><span data-stu-id="96331-124">The TIBCO Enterprise Message Service transport properties are configured in design time and used in run time.</span></span> <span data-ttu-id="96331-125">在**傳輸屬性**，您將設定的連接和認證參數特定為伺服器系統與您嘗試存取的物件。</span><span class="sxs-lookup"><span data-stu-id="96331-125">In the **Transport Properties**, you set the connection and credential parameters specific to the server system and the objects you are trying to access.</span></span>  
  
 ![](../core/media/tib-tibcoemssendtransportpropertiess.gif "TIB_TIBCOEMSSendTransportPropertiess")  
  
  
1.  <span data-ttu-id="96331-126">在**傳輸屬性**，依序展開**系統定義**，然後輸入 TIBCO EMS 伺服器連線的所有必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="96331-126">In the **Transport Properties**, expand **System Definition**, and enter all required information for connection to the TIBCO EMS server.</span></span>  
  
     <span data-ttu-id="96331-127">您必須設定組態參數，Microsoft BizTalk Adapter for TIBCO Enterprise Message Service 才能連線至 TIBCO EMS。</span><span class="sxs-lookup"><span data-stu-id="96331-127">You must set configuration parameters to connect Microsoft BizTalk Adapter for TIBCO Enterprise Message Service to TIBCO EMS.</span></span> <span data-ttu-id="96331-128">**此資料是區分大小寫。**</span><span class="sxs-lookup"><span data-stu-id="96331-128">**This data is case sensitive.**</span></span>  
  
2.  <span data-ttu-id="96331-129">展開**訊息處理**，然後輸入所有必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="96331-129">Expand **Message Handling**, and enter all required information.</span></span>  
  
    |<span data-ttu-id="96331-130">參數</span><span class="sxs-lookup"><span data-stu-id="96331-130">Parameter</span></span>|<span data-ttu-id="96331-131">Description</span><span class="sxs-lookup"><span data-stu-id="96331-131">Description</span></span>|  
    |---------------|-----------------|  
    |`Message Expiration Time`|<span data-ttu-id="96331-132">整數，描述訊息停留在佇列或主題上的時間長短；過了這段時間後，TIBCO EMS 伺服器就會刪除該訊息。</span><span class="sxs-lookup"><span data-stu-id="96331-132">An integer that describes the length of time the message stays on the queue or topic; after the time expires, the message is deleted by the TIBCO EMS server.</span></span><br /><br /> <span data-ttu-id="96331-133">此意義同於 EMS.Expiration 訊息屬性標頭。</span><span class="sxs-lookup"><span data-stu-id="96331-133">It is synonymous to the EMS.Expiration message property header.</span></span> <span data-ttu-id="96331-134">可以用協調流程覆寫。</span><span class="sxs-lookup"><span data-stu-id="96331-134">It can be overridden with the orchestration.</span></span><br /><br /> <span data-ttu-id="96331-135">預設值為 0 毫秒，意思就是訊息在抵達目的地後永遠不會到期。</span><span class="sxs-lookup"><span data-stu-id="96331-135">Default value is 0 milliseconds, which means that the message will not expire from the destination.</span></span>|  
    |`Message is Persistent`|<span data-ttu-id="96331-136">TIBCO EMS 伺服器會先將訊息寫入磁碟，然後才送出收到訊息的通知。</span><span class="sxs-lookup"><span data-stu-id="96331-136">Messages are written to disk by the TIBCO EMS server before they are acknowledged.</span></span><br /><br /> <span data-ttu-id="96331-137">這是 TibcoEMS.DeliveryMode 標頭屬性。</span><span class="sxs-lookup"><span data-stu-id="96331-137">This is the TibcoEMS.DeliveryMode header property.</span></span> <span data-ttu-id="96331-138">它指示伺服器先將送達的訊息保存在佇列中，再通知配接器已收到訊息。</span><span class="sxs-lookup"><span data-stu-id="96331-138">It instructs sent messages to be persisted in the queue by the server before acknowledging reception of the message to the adapter.</span></span><br /><br /> <span data-ttu-id="96331-139">預設值為 [True]。</span><span class="sxs-lookup"><span data-stu-id="96331-139">Default value is **True**.</span></span>|  
    |`Message Priority`|<span data-ttu-id="96331-140">從 0 到 9 的數字排名，用以定義訊息的優先順序；此值越大，表示優先順序越高。</span><span class="sxs-lookup"><span data-stu-id="96331-140">Numeric ranking from 0 to 9, which defines the priority of the message; the larger the value, the higher the priority.</span></span><br /><br /> <span data-ttu-id="96331-141">優先順序會影響伺服器將訊息傳遞至取用者的順序 (較高的數值優先)。</span><span class="sxs-lookup"><span data-stu-id="96331-141">Priority affects the order in which the server delivers messages to consumers (higher values first).</span></span><br /><br /> <span data-ttu-id="96331-142">JMS 規格定義了從 0 (優先順序最低) 到 9 (優先順序最高) 的 10 個優先順序值等級。</span><span class="sxs-lookup"><span data-stu-id="96331-142">The JMS specification defines ten levels of priority value, from zero (lowest priority) to 9 (highest priority).</span></span> <span data-ttu-id="96331-143">此規格的建議是用戶端可以考慮用 0–4 的優先順序值做為一般優先順序，並用 5–9 的優先順序值做為急件優先順序。</span><span class="sxs-lookup"><span data-stu-id="96331-143">The specification suggests that clients consider 0–4 as gradations of normal priority, and priorities 5–9 as gradations of expedited priority.</span></span><br /><br /> <span data-ttu-id="96331-144">預設值是**4**。</span><span class="sxs-lookup"><span data-stu-id="96331-144">Default value is **4**.</span></span>|  
  
3.  <span data-ttu-id="96331-145">展開**伺服器連線定義**並輸入所有必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="96331-145">Expand **Server Connection Definition** and enter all required information.</span></span>  
  
    |<span data-ttu-id="96331-146">參數</span><span class="sxs-lookup"><span data-stu-id="96331-146">Parameter</span></span>|<span data-ttu-id="96331-147">Description</span><span class="sxs-lookup"><span data-stu-id="96331-147">Description</span></span>|  
    |---------------|-----------------|  
    |`Destination`|<span data-ttu-id="96331-148">必要設定。</span><span class="sxs-lookup"><span data-stu-id="96331-148">Mandatory setting.</span></span> <span data-ttu-id="96331-149">定義目的地的名稱與類型。</span><span class="sxs-lookup"><span data-stu-id="96331-149">Defines the name and type of the destination.</span></span> <span data-ttu-id="96331-150">例如： staticqueue [Q1]。</span><span class="sxs-lookup"><span data-stu-id="96331-150">For example: staticqueue[Q1].</span></span><br /><br /> <span data-ttu-id="96331-151">使用下列格式定義佇列或主題: {static} {dynamic] Queue [queuename] 或 {static} {dynamic] Topic [topicname]。</span><span class="sxs-lookup"><span data-stu-id="96331-151">Defines the queue or topic with the following format: {static}{dynamic]Queue[queuename] or {static}{dynamic]Topic[topicname].</span></span> <span data-ttu-id="96331-152">**注意：** 您可以傳送訊息至不存在的目的地。</span><span class="sxs-lookup"><span data-stu-id="96331-152">**Note:**  You can send a message to a destination that does not exist.</span></span> <span data-ttu-id="96331-153">在此情況下，TIBCO Enterprise Message Service 會建立目的地;這指*動態目的地*。</span><span class="sxs-lookup"><span data-stu-id="96331-153">In such a case, TIBCO Enterprise Message Service creates the destination; this is referred to as a *Dynamic Destination*.</span></span> <span data-ttu-id="96331-154">這是由產生者所建立的目的地，當訊息使用完畢和當產生者中斷連線時即會刪除。</span><span class="sxs-lookup"><span data-stu-id="96331-154">This is a destination created by a producer and deleted when the message is consumed and the producer disconnects.</span></span> <span data-ttu-id="96331-155">A*靜態目的地*目的地只可以建立由 TIBCO Enterprise Message Service 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="96331-155">A *static destination* is a destination which can only created by a TIBCO Enterprise Message Service Administrator.</span></span> <span data-ttu-id="96331-156">由於 BizTalk Adapter for TIBCO Enterprise Message Service 在伺服器上使用名稱對應機制，因此您無法在開啟目的地連線期間連線至動態連接埠。</span><span class="sxs-lookup"><span data-stu-id="96331-156">You cannot connect to a dynamic port when you open a connection to a destination because BizTalk Adapter for TIBCO Enterprise Message Service uses a name lookup mechanism on the server.</span></span> <span data-ttu-id="96331-157">當您使用名稱對應功能時，只會顯示靜態連接埠。</span><span class="sxs-lookup"><span data-stu-id="96331-157">Only static ports are visible when you are using the name lookup.</span></span> <span data-ttu-id="96331-158">連線至動態連接埠時，可以使用靜態目的地；但是，如果該名稱的目的地不存在，則系統會建立一個目的地。</span><span class="sxs-lookup"><span data-stu-id="96331-158">When connecting to a dynamic port, you can use static destinations; however, if no destination by that name exists, a destination is created.</span></span> <span data-ttu-id="96331-159">目的地可讓您明確指定，定義連接埠時要使用的目的地類型。</span><span class="sxs-lookup"><span data-stu-id="96331-159">Destination lets you explicitly specify the type of destination to use when defining the port.</span></span> <span data-ttu-id="96331-160">目的地語法不區分大小寫： staticqueue [queue_name]，statictopic [topic_name]，dynamicqueue [queue_name];dynamictopic [topic_name]。</span><span class="sxs-lookup"><span data-stu-id="96331-160">The syntax for the Destination is not case sensitive: staticqueue[queue_name], statictopic[topic_name], dynamicqueue[queue_name]; dynamictopic[topic_name].</span></span>|  
    |`Port Number`|<span data-ttu-id="96331-161">TIBCO EMS 伺服器所收聽的連接埠。</span><span class="sxs-lookup"><span data-stu-id="96331-161">Port on which the TIBCO EMS server listens.</span></span>|  
    |`Server Name`|<span data-ttu-id="96331-162">必要設定。</span><span class="sxs-lookup"><span data-stu-id="96331-162">Mandatory setting.</span></span> <span data-ttu-id="96331-163">裝載 TIBCO EMS 伺服器的系統名稱。</span><span class="sxs-lookup"><span data-stu-id="96331-163">Name of the system hosting the TIBCO EMS server.</span></span>|  
  
4.  <span data-ttu-id="96331-164">提供使用單一登入 (SSO) 的認證。</span><span class="sxs-lookup"><span data-stu-id="96331-164">Provide credentials using Single Sign-On (SSO).</span></span>  
  
     <span data-ttu-id="96331-165">您可以透過兩種方式來存取 TIBCO EMS 系統。</span><span class="sxs-lookup"><span data-stu-id="96331-165">You can use two methods to access the TIBCO EMS system.</span></span> <span data-ttu-id="96331-166">您可以使用認證 (使用者名稱和密碼參數) 或單一登入。</span><span class="sxs-lookup"><span data-stu-id="96331-166">You can use Credentials (User Name and Password parameters) or Single Sign-On.</span></span>  
  
    -   <span data-ttu-id="96331-167">選取**是**中**使用 SSO**使用單一登入。</span><span class="sxs-lookup"><span data-stu-id="96331-167">Select **Yes** in the **Use SSO** to use Single Sign-On.</span></span>  
  
    -   <span data-ttu-id="96331-168">從清單中選取一個分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="96331-168">Select an affiliate application from the list.</span></span>  
  
         <span data-ttu-id="96331-169">由企業單一登入工具所建立的分支機構應用程式代表如 TIBCO EMS 之類的應用程式。</span><span class="sxs-lookup"><span data-stu-id="96331-169">An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as TIBCO EMS.</span></span> <span data-ttu-id="96331-170">BizTalk Adapter for TIBCO EMS 會使用應用程式使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="96331-170">BizTalk Adapter for TIBCO EMS uses the credentials of an application user.</span></span> <span data-ttu-id="96331-171">這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。</span><span class="sxs-lookup"><span data-stu-id="96331-171">These credentials are retrieved from the SSO database for the server system for a specified affiliate application.</span></span>  
  
         <span data-ttu-id="96331-172">如需如何建立分支機構應用程式的詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications5.md)。</span><span class="sxs-lookup"><span data-stu-id="96331-172">For more information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications5.md).</span></span>  
  
5.  <span data-ttu-id="96331-173">在**交易支援**，選取**是**如果此傳送埠支援交易。</span><span class="sxs-lookup"><span data-stu-id="96331-173">In **Transaction Support**, select **Yes** if this send port will support transactions.</span></span>  
  
     <span data-ttu-id="96331-174">如果您在連接埠上啟用交易支援，所有使用此連接埠的協調流程都必須是交易式的；否則，所有呼叫都會回復 (例如，不會認可呼叫)。</span><span class="sxs-lookup"><span data-stu-id="96331-174">If you enable transaction support on the port, all orchestrations using this port must be transactional; otherwise, all calls are rolled back (for example, are not committed).</span></span> <span data-ttu-id="96331-175">新增至協調流程的範圍物件控制了交易的生命週期。</span><span class="sxs-lookup"><span data-stu-id="96331-175">The scope object added to the orchestration controls the transaction life-cycle.</span></span>  
  
6.  <span data-ttu-id="96331-176">展開**使用者認證**輸入**使用者名**和**密碼**來存取 TIBCO EMS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="96331-176">Expand **User Credentials** and enter the **User Name** and **Password** to access the TIBCO EMS server.</span></span>  
  
    |<span data-ttu-id="96331-177">參數</span><span class="sxs-lookup"><span data-stu-id="96331-177">Parameter</span></span>|<span data-ttu-id="96331-178">Description</span><span class="sxs-lookup"><span data-stu-id="96331-178">Description</span></span>|  
    |---------------|-----------------|  
    |`Password`|<span data-ttu-id="96331-179">用來與 TIBCO EMS 精靈通訊的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="96331-179">The user’s Password used to communicate with a TIBCO EMS daemon.</span></span><br /><br /> <span data-ttu-id="96331-180">如果您未選取**使用 SSO**，您必須設定 BizTalk Adapter for TIBCO EMS 才能與 TIBCO EMS 精靈通訊的認證參數。</span><span class="sxs-lookup"><span data-stu-id="96331-180">If you did not select **Use SSO**, you must set credential parameters for the BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.</span></span>|  
    |`User Name`|<span data-ttu-id="96331-181">用來與 TIBCO EMS 精靈通訊的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="96331-181">Name of a user used to communicate with a TIBCO EMS daemon.</span></span><br /><br /> <span data-ttu-id="96331-182">如果您未選取**使用 SSO**，您必須設定 BizTalk Adapter for TIBCO EMS 才能與 TIBCO EMS 精靈通訊的認證參數。</span><span class="sxs-lookup"><span data-stu-id="96331-182">If you did not select **Use SSO**, you must set credential parameters for the BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.</span></span>|  
  
7.  <span data-ttu-id="96331-183">按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="96331-183">Click **Apply**, and then click **OK**.</span></span>  

   
## <a name="next-steps"></a><span data-ttu-id="96331-184">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="96331-184">Next steps</span></span>
[<span data-ttu-id="96331-185">建立接收成品</span><span class="sxs-lookup"><span data-stu-id="96331-185">Create receive artifacts</span></span>](../core/creating-tibco-enterprise-message-service-receive-handlers.md)  
[<span data-ttu-id="96331-186">TIBCO EMS 訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="96331-186">TIBCO EMS message context properties</span></span>](../core/message-context-properties-in-biztalk-server.md)