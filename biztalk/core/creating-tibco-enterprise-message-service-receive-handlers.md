---
title: "建立 TIBCO EMS 接收成品 |Microsoft 文件"
description: "建立接收埠，並設定在 BizTalk Server 使用 TIBCO Enterprise Message Service 配接器傳輸屬性"
ms.custom: 
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1307e3c-0237-4f19-a642-58e694fe95d0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf5810dc012c7aa5dcc2fbdfcecd9d59d066ced7
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="create-tibco-ems-receive-artifacts"></a><span data-ttu-id="d4ec8-103">建立 TIBCO EMS 接收成品</span><span class="sxs-lookup"><span data-stu-id="d4ec8-103">Create TIBCO EMS receive artifacts</span></span>

## <a name="overview"></a><span data-ttu-id="d4ec8-104">概觀</span><span class="sxs-lookup"><span data-stu-id="d4ec8-104">Overview</span></span>
<span data-ttu-id="d4ec8-105">TIBCO Enterprise Message Service 接收器是一項待命程式服務，能夠註冊特定的佇列或主題，然後接收相關的訊息。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-105">TIBCO Enterprise Message Service receiver is a listener service that registers a particular Queue or Topic and receives the relative messages.</span></span> <span data-ttu-id="d4ec8-106">BizTalk Adapter for TIBCO Enterprise Message Service 會先開啟新的工作階段以向 TIBCO Enterprise Message Service 註冊，然後才繼續輪詢以接收訊息。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-106">BizTalk Adapter for TIBCO Enterprise Message Service first registers with TIBCO Enterprise Message Service by opening a new session, and then it continues polling to receive messages..</span></span> <span data-ttu-id="d4ec8-107">本節將說明如何設定傳送埠以連線至 TIBCO Enterprise Message Service，以及如何在協調流程中納入 XML 以在執行階段與 TIBCO EMS 互動。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-107">This section explains how to set the receive port to connect to TIBCO Enterprise Message Service and how to include XML in your orchestration to interact with TIBCO EMS at run time.</span></span>  

## <a name="create-a-receive-port"></a><span data-ttu-id="d4ec8-108">建立接收埠</span><span class="sxs-lookup"><span data-stu-id="d4ec8-108">Create a receive port</span></span>  
  
1.  <span data-ttu-id="d4ec8-109">在 BizTalk Server 管理主控台中，展開**BizTalk 群組**，依序展開**應用程式**，然後展開您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-109">In the BizTalk Server Administration Console, expand **BizTalk Group**, expand **Applications**, and then expand your application.</span></span>  
  
2.  <span data-ttu-id="d4ec8-110">以滑鼠右鍵按一下**接收埠**，選取**新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-110">Right-click **Receive Ports**, select **New**, and then click **One-way Receive Ports**.</span></span>  
  
3.  <span data-ttu-id="d4ec8-111">在**接收埠屬性**視窗，請在**一般**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d4ec8-111">In the **Receive Port Properties** window, on the **General** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="d4ec8-112">在**名稱**欄位中，輸入`ReceiveFromTIBCOEMS`。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-112">In the **Name** field, type `ReceiveFromTIBCOEMS`.</span></span>  
  
    2.  <span data-ttu-id="d4ec8-113">在**驗證**群組方塊中，指定使用驗證時，如何處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-113">In the **Authentication** group box, specify how messages are handled when using authentication.</span></span>  
  
    3.  <span data-ttu-id="d4ec8-114">選取**啟用的路由失敗訊息**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-114">Select the **Enable routing for failed messages** checkbox.</span></span>  
  
4.  <span data-ttu-id="d4ec8-115">在**接收位置**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d4ec8-115">On the **Receive Locations** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="d4ec8-116">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-116">Click **New**.</span></span>  
  
    2.  <span data-ttu-id="d4ec8-117">在**接收位置**視窗，請在**一般**頁面上，輸入**名稱**接收位置。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-117">In the **Receive Locations** window, on the **General** page, type the **Name** of the receive location.</span></span>  
  
    3.  <span data-ttu-id="d4ec8-118">從**類型**下拉式清單中，選取傳輸類型，以及從**接收處理常式**下拉式清單中，選取傳輸位址。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-118">From the **Type** drop-down list, select the transport type, and from the **Receive handler** drop-down list, select the transport address.</span></span>  
  
    4.  <span data-ttu-id="d4ec8-119">從**接收管線**下拉式清單中，選取接收管線。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-119">From the **Receive pipeline** drop-down list, select the receive pipeline.</span></span>  
  
    5.  <span data-ttu-id="d4ec8-120">在**排程**頁面上，選取**開始日期**和**結束日期**限制接收文件。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-120">On the **Schedule** page, select the **Start date** and the **End date** to restrict receiving documents.</span></span>  
  
    6.  <span data-ttu-id="d4ec8-121">選取**啟用服務窗口**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-121">Select the **Enable service window** checkbox.</span></span>  
  
    7.  <span data-ttu-id="d4ec8-122">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-122">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="d4ec8-123">在**輸入對應**頁面上，選取輸入的對應轉換文件上選取的連接埠。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-123">On the **Inbound Maps** page, select the inbound maps for transforming documents on the selected port.</span></span>  
  
6.  <span data-ttu-id="d4ec8-124">在**追蹤**頁面上，選取所需的追蹤訊息內文和追蹤訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-124">On the **Tracking** page, select the desired tracking message bodies and tracking message properties.</span></span>  
  
7.  <span data-ttu-id="d4ec8-125">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-125">Click **OK**.</span></span>  

## <a name="set-the-receive-port-transport-properties"></a><span data-ttu-id="d4ec8-126">設定接收埠傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="d4ec8-126">Set the receive port transport properties</span></span>
<span data-ttu-id="d4ec8-127">如 TIBCO Enterprise Message System (EMS) 接收位置， **URL**和**目標命名空間**至 TIBCO EMS 系統是所需的組態值。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-127">For a TIBCO Enterprise Message System (EMS) receive location, the **URL** and **Target Namespace** to the TIBCO EMS System are the only configuration values required.</span></span>    
 
1.  <span data-ttu-id="d4ec8-128">展開**系統定義**並輸入 TIBCO EMS 伺服器連線的所有必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-128">Expand the **System Definition** and enter all required information for connection to the TIBCO EMS server.</span></span>  
  
2.  <span data-ttu-id="d4ec8-129">展開**訊息處理**並輸入所有必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-129">Expand **Message Handling** and enter all required information.</span></span>  
  
    |<span data-ttu-id="d4ec8-130">參數</span><span class="sxs-lookup"><span data-stu-id="d4ec8-130">Parameter</span></span>|<span data-ttu-id="d4ec8-131">Description</span><span class="sxs-lookup"><span data-stu-id="d4ec8-131">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="d4ec8-132">**訊息選取器**</span><span class="sxs-lookup"><span data-stu-id="d4ec8-132">**Message Selector**</span></span>|<span data-ttu-id="d4ec8-133">只有在對目的地中的訊息評估此字串得到 True 時，才會接收訊息。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-133">Messages are received only if this string evaluates to True with the message in the destination.</span></span><br /><br /> <span data-ttu-id="d4ec8-134">允許接收埠只接收內部標頭屬性與此欄位所述運算式相符的訊息。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-134">Allows the receive port to retrieve only messages that contain header properties that match the expression described in this field.</span></span><br /><br /> <span data-ttu-id="d4ec8-135">訊息選取器的語法是以 SQL92 條件運算式語法的子集為基礎。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-135">The syntax of message selectors is based on a subset of the SQL92 conditional expression syntax.</span></span> <span data-ttu-id="d4ec8-136">TIBCO EMS 使用者指南含有此語法的完整說明。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-136">The syntax is fully described in the TIBCO EMS users guide.</span></span><br /><br /> <span data-ttu-id="d4ec8-137">例如，如果訊息中包含名為 NewsType 的標頭屬性，則接收埠只能擷取屬於 Sports 或 Editorial 類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-137">For example, if a message contains a header property name NewsType, a receive port can retrieve only those that are of type Sports or Editorial.</span></span>|  
    |<span data-ttu-id="d4ec8-138">**重試計數**</span><span class="sxs-lookup"><span data-stu-id="d4ec8-138">**Retry Count**</span></span>|<span data-ttu-id="d4ec8-139">傳輸的重試計數。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-139">The retry count for the transport.</span></span> <span data-ttu-id="d4ec8-140">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-140">Default value is 0.</span></span>|  
    |<span data-ttu-id="d4ec8-141">**重試間隔**</span><span class="sxs-lookup"><span data-stu-id="d4ec8-141">**Retry Interval**</span></span>|<span data-ttu-id="d4ec8-142">配接器進行重試之前所等候的時間。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-142">The period of time the adapter waits before initiating a retry.</span></span> <span data-ttu-id="d4ec8-143">預設值為五分鐘。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-143">Default value is five minutes.</span></span>|  
  
3.  <span data-ttu-id="d4ec8-144">展開**伺服器連線定義**並輸入所有必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-144">Expand the **Server Connection Definition** and enter all required information.</span></span>  
  
    |<span data-ttu-id="d4ec8-145">參數</span><span class="sxs-lookup"><span data-stu-id="d4ec8-145">Parameter</span></span>|<span data-ttu-id="d4ec8-146">Description</span><span class="sxs-lookup"><span data-stu-id="d4ec8-146">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="d4ec8-147">**目的地**</span><span class="sxs-lookup"><span data-stu-id="d4ec8-147">**Destination**</span></span>|<span data-ttu-id="d4ec8-148">必要設定。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-148">Mandatory setting.</span></span> <span data-ttu-id="d4ec8-149">定義目的地的名稱與類型。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-149">Defines the name and type of the destination.</span></span> <span data-ttu-id="d4ec8-150">使用下列格式定義佇列或主題：Queue[queue.name] 或 Topic[topic.name]。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-150">Defines the queue or topic with the following format: Queue[queue.name] or Topic[topic.name].</span></span>|  
    |<span data-ttu-id="d4ec8-151">**通訊埠編號**</span><span class="sxs-lookup"><span data-stu-id="d4ec8-151">**Port Number**</span></span>|<span data-ttu-id="d4ec8-152">TIBCO EMS 伺服器所收聽的連接埠。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-152">Port on which the TIBCO EMS server listens.</span></span>|  
    |<span data-ttu-id="d4ec8-153">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="d4ec8-153">**Server Name**</span></span>|<span data-ttu-id="d4ec8-154">必要設定。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-154">Mandatory setting.</span></span> <span data-ttu-id="d4ec8-155">裝載 TIBCO EMS 伺服器的系統名稱。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-155">Name of the system hosting the TIBCO EMS server.</span></span>|  
  
4.  <span data-ttu-id="d4ec8-156">提供使用單一登入 (SSO) 的認證。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-156">Provide credentials using Single Sign-On (SSO).</span></span>  
  
     <span data-ttu-id="d4ec8-157">有兩種方法可以用來存取 TIBCO EMS 系統。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-157">There are two methods that you can use to access the TIBCO EMS system.</span></span> <span data-ttu-id="d4ec8-158">您可以使用「認證」(使用者名稱與密碼參數) 或「單一登入」。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-158">You can use Credentials (user name and password parameters) or Single Sign-On.</span></span>  
  
    -   <span data-ttu-id="d4ec8-159">選取**是**中**使用 SSO**使用單一登入。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-159">Select **Yes** in **Use SSO** to use Single Sign-On.</span></span>  
  
    -   <span data-ttu-id="d4ec8-160">在清單中選取分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-160">Select an affiliate application in the list.</span></span>  
  
         <span data-ttu-id="d4ec8-161">由企業單一登入工具所建立的分支機構應用程式代表如 TIBCO EMS 之類的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-161">An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as TIBCO EMS.</span></span> <span data-ttu-id="d4ec8-162">Microsoft BizTalk Adapter for TIBCO EMS 會使用應用程式使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-162">Microsoft BizTalk Adapter for TIBCO EMS uses the credentials of an application user.</span></span> <span data-ttu-id="d4ec8-163">這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-163">These credentials are retrieved from the SSO database for the server system for a specified affiliate application.</span></span>  
  
         <span data-ttu-id="d4ec8-164">如需如何建立分支機構應用程式的詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications5.md)。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-164">For more information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications5.md).</span></span>  
  
5.  <span data-ttu-id="d4ec8-165">展開**使用者認證**輸入**使用者名**和**密碼**來存取 TIBCO EMS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-165">Expand **User Credentials** and enter the **User Name** and **Password** to access the TIBCO EMS server.</span></span>  
  
    |<span data-ttu-id="d4ec8-166">參數</span><span class="sxs-lookup"><span data-stu-id="d4ec8-166">Parameter</span></span>|<span data-ttu-id="d4ec8-167">Description</span><span class="sxs-lookup"><span data-stu-id="d4ec8-167">Description</span></span>|  
    |---------------|-----------------|  
    |`Password`|<span data-ttu-id="d4ec8-168">用來與 TIBCO EMS 精靈通訊的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-168">The user’s password that is used to communicate with a TIBCO EMS daemon.</span></span><br /><br /> <span data-ttu-id="d4ec8-169">如果您未選取**使用 SSO**，您必須設定為 BizTalk Adapter for TIBCO EMS 才能與 TIBCO EMS 精靈通訊的認證參數。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-169">If you did not select **Use SSO**, you must set credential parameters for BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.</span></span>|  
    |`User Name`|<span data-ttu-id="d4ec8-170">用來與 TIBCO EMS 精靈通訊的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-170">Name of a user that is used to communicate with a TIBCO EMS daemon.</span></span><br /><br /> <span data-ttu-id="d4ec8-171">如果您未選取**使用 SSO**，您必須設定為 BizTalk Adapter for TIBCO EMS 才能與 TIBCO EMS 精靈通訊的認證參數。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-171">If you did not select **Use SSO**, you must set credential parameters for BizTalk Adapter for TIBCO EMS to communicate with a TIBCO EMS daemon.</span></span>|  
  
6.  <span data-ttu-id="d4ec8-172">按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d4ec8-172">Click **Apply**, and then click **OK**.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="d4ec8-173">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="d4ec8-173">Next steps</span></span>
[<span data-ttu-id="d4ec8-174">TIBCO EMS 訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="d4ec8-174">TIBCO EMS message context properties</span></span>](../core/message-context-properties-in-biztalk-server.md)