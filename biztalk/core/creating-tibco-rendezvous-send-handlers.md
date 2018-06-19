---
title: 建立 TIBCO Rendezvous 配接器傳送成品 |Microsoft 文件
description: 建立傳送埠，請設定將訊息從 BizTalk 傳送至 TIBCO Rendezvous 傳輸屬性
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad996c4f-e6ed-4582-a768-0cb1ad25b1d8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed6d03885423582c2657c9cb624c63f26ce1c6f3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24014349"
---
# <a name="create-tibco-rendezvous-send-handlers"></a><span data-ttu-id="2fdaa-103">建立 TIBCO Rendezvous 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="2fdaa-103">Create TIBCO Rendezvous Send Handlers</span></span>
<span data-ttu-id="2fdaa-104">本節說明如何建立結構描述，以在 BizTalk Server 協調流程中使用 TIBCO Rendezvous。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-104">This section explains how to create a schema to use TIBCO Rendezvous in a BizTalk Server orchestration.</span></span>  
  
## <a name="create-a-send-port"></a><span data-ttu-id="2fdaa-105">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="2fdaa-105">Create a send port</span></span>
  
1.  <span data-ttu-id="2fdaa-106">在**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-106">In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand your application.</span></span>  
  
2.  <span data-ttu-id="2fdaa-107">以滑鼠右鍵按一下**傳送埠**，指向 [**新增**，然後按一下 [**靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="2fdaa-108">在**傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2fdaa-108">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="2fdaa-109">輸入傳送埠名稱，例如`SendToTIBCORV`。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-109">Type a name for the send port, for example, `SendToTIBCORV`.</span></span>  
  
    2.  <span data-ttu-id="2fdaa-110">從**類型**下拉式清單中，選取**TIBCO Rendezvous**。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-110">From the **Type** drop-down list, select **TIBCO Rendezvous**.</span></span>  
  
    3.  <span data-ttu-id="2fdaa-111">從**傳送處理常式**下拉式清單中，選取 URI。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-111">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="2fdaa-112">從 [傳送管線] 下拉式清單中，選取 [ **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-112">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  <span data-ttu-id="2fdaa-113">從**接收管線**下拉式清單中，選取 **[microsoft.biztalk.defaultpiplelines.xmlreceive]**。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-113">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  

        > [!NOTE]
        > <span data-ttu-id="2fdaa-114">Microsoft BizTalk Adapter for TIBCO Rendezvous 需要您選取 XMLTransmit 管線傳送，並針對 receive XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-114">Microsoft BizTalk Adapter for TIBCO Rendezvous requires that you select XMLTransmit pipeline for send, and XMLReceive pipeline for receive.</span></span>
        
    6.  <span data-ttu-id="2fdaa-115">按一下**設定**以設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-115">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="2fdaa-116">在**TIBCO Rendezvous 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2fdaa-116">In the **TIBCO Rendezvous Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="2fdaa-117">輸入屬性。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-117">Enter the properties.</span></span>  
  
         <span data-ttu-id="2fdaa-118">您不需要設定登入資訊。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-118">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="2fdaa-119">在此清單中，選取您建立來代表 TIBCO Rendezvous 系統的 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-119">In the list, select the SSO affiliate application you created to represent the TIBCO Rendezvous system.</span></span>  
  
    3.  <span data-ttu-id="2fdaa-120">如**使用 SSO**，選取**是**。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-120">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="2fdaa-121">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-121">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="2fdaa-122">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-122">Click **OK**.</span></span>  

## <a name="set-the-transport-properties"></a><span data-ttu-id="2fdaa-123">設定傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="2fdaa-123">Set the transport properties</span></span>
<span data-ttu-id="2fdaa-124">TIBCO Rendezvous 傳輸屬性用於執行階段。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-124">The TIBCO Rendezvous Transport property is used for run time.</span></span> <span data-ttu-id="2fdaa-125">在**傳輸屬性**，設定連線參數來識別您要將產生的訊息發佈的 TIBCO Rendezvous 網域。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-125">In the **Transport Properties**, you set the connection parameters that identify the TIBCO Rendezvous domain where you want to publish the generated messages.</span></span>  
  
 
1.  <span data-ttu-id="2fdaa-126">在**TIBCO Rendezvous 傳輸屬性**畫面上，依序展開**認證寄件者屬性**並輸入下列資訊。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-126">On the **TIBCO Rendezvous Transport Properties** screen, expand **Certified Sender Properties** and enter the following information.</span></span>  
  
     ![](../core/media/sadp-tibcoren-transs.gif "SAdp_TibcoRen_Transs")  
  
    |<span data-ttu-id="2fdaa-127">使用</span><span class="sxs-lookup"><span data-stu-id="2fdaa-127">Use this</span></span>|<span data-ttu-id="2fdaa-128">動作</span><span class="sxs-lookup"><span data-stu-id="2fdaa-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2fdaa-129">**分類帳名稱**</span><span class="sxs-lookup"><span data-stu-id="2fdaa-129">**Ledger name**</span></span>|<span data-ttu-id="2fdaa-130">預設值為空白。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-130">Default value is blank.</span></span> <span data-ttu-id="2fdaa-131">要用於永續性認證訊息傳遞的分類帳檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-131">Ledger file name to use for persistent certified message delivery.</span></span> <span data-ttu-id="2fdaa-132">只能使用本機磁碟機。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-132">Use local drives only.</span></span>|  
    |<span data-ttu-id="2fdaa-133">**可重複使用的名稱**</span><span class="sxs-lookup"><span data-stu-id="2fdaa-133">**Reusable name**</span></span>|<span data-ttu-id="2fdaa-134">預設值為空白。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-134">Default value is blank.</span></span> <span data-ttu-id="2fdaa-135">要用於認證訊息傳遞的可重複使用對應名稱。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-135">Reusable correspondent name to use for certified message delivery.</span></span> <span data-ttu-id="2fdaa-136">在網路上所有認證訊息通訊人名稱當中，這必須是唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-136">The name must be unique among all certified message correspondent names on the network.</span></span>|  
  
2.  <span data-ttu-id="2fdaa-137">展開**認證**並輸入伺服器連線的下列資訊。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-137">Expand **Credentials** and enter the following information for connection to the server.</span></span>  
  
    |<span data-ttu-id="2fdaa-138">使用</span><span class="sxs-lookup"><span data-stu-id="2fdaa-138">Use this</span></span>|<span data-ttu-id="2fdaa-139">動作</span><span class="sxs-lookup"><span data-stu-id="2fdaa-139">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2fdaa-140">**密碼**</span><span class="sxs-lookup"><span data-stu-id="2fdaa-140">**Password**</span></span>|<span data-ttu-id="2fdaa-141">預設值為空白。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-141">Default value is blank.</span></span> <span data-ttu-id="2fdaa-142">登入 Tibco Rendezvous 精靈的密碼。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-142">Password for login to a Tibco Rendezvous daemon.</span></span>|  
    |<span data-ttu-id="2fdaa-143">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="2fdaa-143">**User name**</span></span>|<span data-ttu-id="2fdaa-144">預設值為空白。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-144">Default value is blank.</span></span> <span data-ttu-id="2fdaa-145">Tibco Rendezvous 精靈的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-145">User name for Tibco Rendezvous daemon.</span></span>|  
  
3.  <span data-ttu-id="2fdaa-146">展開**一般設定**並輸入 TIBCO Rendezvous 伺服器連線的下列資訊。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-146">Expand **General Settings** and enter the following information for connection to the TIBCO Rendezvous server.</span></span>  
  
    |<span data-ttu-id="2fdaa-147">使用</span><span class="sxs-lookup"><span data-stu-id="2fdaa-147">Use this</span></span>|<span data-ttu-id="2fdaa-148">動作</span><span class="sxs-lookup"><span data-stu-id="2fdaa-148">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2fdaa-149">**字碼頁編號**</span><span class="sxs-lookup"><span data-stu-id="2fdaa-149">**Code Page Number**</span></span>|<span data-ttu-id="2fdaa-150">預設值為 65001 (UTF-8 編碼的字碼頁)。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-150">Default value is 65001 (code page for UTF-8 encoding).</span></span> <span data-ttu-id="2fdaa-151">這是 TIBCO Rendezvous SDK 用於字串編碼的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-151">This is the code page that the TIBCO Rendezvous SDK uses for String encoding.</span></span>|  
    |<span data-ttu-id="2fdaa-152">**預設的主體名稱**</span><span class="sxs-lookup"><span data-stu-id="2fdaa-152">**Default Subject Name**</span></span>|<span data-ttu-id="2fdaa-153">預設值是空白。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-153">Default is empty.</span></span> <span data-ttu-id="2fdaa-154">主體名稱是在協調流程中設定。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-154">The subject name is set in the orchestration.</span></span> <span data-ttu-id="2fdaa-155">如果某個連接埠用於某種訊息類型，您可以提供預設的主體名稱，這樣可以省去設定主體名稱屬性的需要，而使得協調流程變得更簡單。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-155">If a port is used for one message type, you can provide a default subject name, and you can simplify orchestrations by removing the need to set the Subject name property.</span></span>|  
    |<span data-ttu-id="2fdaa-156">**啟用時間批次**</span><span class="sxs-lookup"><span data-stu-id="2fdaa-156">**Enable Time Batch**</span></span>|<span data-ttu-id="2fdaa-157">預設值為 False。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-157">Default value is False.</span></span> <span data-ttu-id="2fdaa-158">啟用/停用 TIBCO Rendezvous 時間批次功能。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-158">Enable/Disable TIBCO Rendezvous Time Batch feature.</span></span>|  
    |<span data-ttu-id="2fdaa-159">**將不受支援的型別對應至字串**</span><span class="sxs-lookup"><span data-stu-id="2fdaa-159">**Map Unsupported types to string**</span></span>|<span data-ttu-id="2fdaa-160">預設值是 True。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-160">Default value is True.</span></span> <span data-ttu-id="2fdaa-161">如果為 true，不支援的類型會對應到字串 (如果可能的話)。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-161">If true, unsupported types are mapped to string if it is possible.</span></span> <span data-ttu-id="2fdaa-162">若為 False，就會產生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-162">If False, a run-time error is generated.</span></span>|  
    |<span data-ttu-id="2fdaa-163">**二進位碼檔案，例如 TIBCO Rendezvous 組件的路徑**</span><span class="sxs-lookup"><span data-stu-id="2fdaa-163">**Path to Binaries, such as TIBCO Rendezvous assemblies**</span></span>|<span data-ttu-id="2fdaa-164">如果 PATH 環境變數中尚無此資訊，請提供此資訊。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-164">Provide this information if it is not already in the PATH environment variable.</span></span>|  
    |<span data-ttu-id="2fdaa-165">**保留器順序**</span><span class="sxs-lookup"><span data-stu-id="2fdaa-165">**Preserver Order**</span></span>|<span data-ttu-id="2fdaa-166">預設值是 True。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-166">Default value is True.</span></span> <span data-ttu-id="2fdaa-167">啟用以 BizTalk Server 收到訊息的相同順序，將訊息傳送到 TIBCO Rendezvous 的邏輯。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-167">Enables logic to send messages to TIBCO Rendezvous in the same order they were received from BizTalk Server.</span></span> <span data-ttu-id="2fdaa-168">此參數會強制以相同的順序發佈訊息；這並不表示訂閱者會以相同的順序收到訊息。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-168">This parameter forces publishing in the same order; it does not mean that subscribers receive them in the same order.</span></span>|  
    |<span data-ttu-id="2fdaa-169">**傳送埠識別碼**</span><span class="sxs-lookup"><span data-stu-id="2fdaa-169">**Send Port Identifier**</span></span>|<span data-ttu-id="2fdaa-170">這個識別項會出現在與此連接埠相關聯的記錄訊息中。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-170">This identifier appears in log messages associated with this port.</span></span> <span data-ttu-id="2fdaa-171">這是為了方便您參考而提供。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-171">It is provided as a convenience.</span></span>|  
  
4.  <span data-ttu-id="2fdaa-172">展開**Rendezvous 傳輸**並輸入 TIBCO Rendezvous 伺服器的連接資訊，請按一下**套用**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-172">Expand **Rendezvous Transport** and enter the information for connection to the TIBCO Rendezvous server, click **Apply**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="2fdaa-173">您必須設定連線參數，讓 Microsoft BizTalk Adapter for TIBCO Rendezvous 能夠存取 TIBCO Rendezvous。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-173">You must set connection parameters for Microsoft BizTalk Adapter for TIBCO Rendezvous to access TIBCO Rendezvous.</span></span>  
  
    |<span data-ttu-id="2fdaa-174">使用</span><span class="sxs-lookup"><span data-stu-id="2fdaa-174">Use this</span></span>|<span data-ttu-id="2fdaa-175">動作</span><span class="sxs-lookup"><span data-stu-id="2fdaa-175">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2fdaa-176">**精靈**</span><span class="sxs-lookup"><span data-stu-id="2fdaa-176">**Daemon**</span></span>|<span data-ttu-id="2fdaa-177">預設值是空白。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-177">Default is empty.</span></span><br /><br /> <span data-ttu-id="2fdaa-178">Rendezvous 傳輸精靈參數。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-178">Rendezvous Transport Daemon parameter.</span></span>|  
    |<span data-ttu-id="2fdaa-179">**網路**</span><span class="sxs-lookup"><span data-stu-id="2fdaa-179">**Network**</span></span>|<span data-ttu-id="2fdaa-180">預設值是空白。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-180">Default is empty.</span></span><br /><br /> <span data-ttu-id="2fdaa-181">Rendezvous 傳輸網路參數。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-181">Rendezvous Transport Network parameter.</span></span>|  
    |<span data-ttu-id="2fdaa-182">**服務**</span><span class="sxs-lookup"><span data-stu-id="2fdaa-182">**Service**</span></span>|<span data-ttu-id="2fdaa-183">預設值是空白。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-183">Default is empty.</span></span><br /><br /> <span data-ttu-id="2fdaa-184">Rendezvous 傳輸服務參數。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-184">Rendezvous Transport Service parameter.</span></span>|  
  
5.  <span data-ttu-id="2fdaa-185">提供使用單一登入 (SSO) 的認證。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-185">Provide credentials using Single Sign-On (SSO).</span></span>  
  
     <span data-ttu-id="2fdaa-186">您可以使用兩種方法來存取 TIBCO Rendezvous 系統。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-186">There are two methods that you can use to access the TIBCO Rendezvous system.</span></span> <span data-ttu-id="2fdaa-187">您可以使用認證 (使用者名稱和密碼參數) 或單一登入。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-187">You can use Credentials (User Name and Password parameters) or Single Sign-On.</span></span>  
  
    1.  <span data-ttu-id="2fdaa-188">選取**是**中**使用 SSO**使用單一登入。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-188">Select **Yes** in the **Use SSO** to use Single Sign-On.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2fdaa-189">請參閱[安全性](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)如需有關如何設定 SSO 資訊。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-189">See [Security](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md) for information about how to set up SSO.</span></span>  
  
    2.  <span data-ttu-id="2fdaa-190">從清單中選取一個分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-190">Select an affiliate application from the list.</span></span>  
  
         <span data-ttu-id="2fdaa-191">企業單一登入工具建立的分支機構應用程式代表一個應用程式 (例如 TIBCO Rendezvous)。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-191">An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as TIBCO Rendezvous.</span></span> <span data-ttu-id="2fdaa-192">Microsoft BizTalk Adapter for TIBCO Rendezvous 會使用應用程式使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-192">Microsoft BizTalk Adapter for TIBCO Rendezvous uses the credentials of an application user.</span></span> <span data-ttu-id="2fdaa-193">這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-193">These credentials are retrieved from the SSO database for the server system for a specified affiliate application.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2fdaa-194">如需如何建立分支機構應用程式資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications1.md)。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-194">For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications1.md).</span></span>  
  
6.  <span data-ttu-id="2fdaa-195">按一下**套用**，然後按一下 [**確定**提供所有必要的資訊，以採用連線資訊之後。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-195">Click **Apply**, and then click **OK** after providing all required information to accept the connection information.</span></span>  
  
     <span data-ttu-id="2fdaa-196">您必須設定連線參數，讓 BizTalk Adapter for TIBCO Rendezvous 能夠存取 TIBCO Rendezvous。</span><span class="sxs-lookup"><span data-stu-id="2fdaa-196">You must set connection parameters for BizTalk Adapter for TIBCO Rendezvous to access TIBCO Rendezvous .</span></span>  


## <a name="next-steps"></a><span data-ttu-id="2fdaa-197">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="2fdaa-197">Next steps</span></span>
  
-   [<span data-ttu-id="2fdaa-198">從 BizTalk Server 使用 TIBCO Rendezvous 傳送埠</span><span class="sxs-lookup"><span data-stu-id="2fdaa-198">Using TIBCO Rendezvous Send Ports from BizTalk Server</span></span>](../core/using-tibco-rendezvous-send-ports-from-biztalk-server.md)  
  
-   [<span data-ttu-id="2fdaa-199">TIBCO Rendezvous 中的傳送處理常式資料類型對應</span><span class="sxs-lookup"><span data-stu-id="2fdaa-199">Data Type Mapping for Send Handlers in TIBCO Rendezvous</span></span>](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md)  
  
-   [<span data-ttu-id="2fdaa-200">BizTalk Server 訊息內容屬性 (傳送處理常式)</span><span class="sxs-lookup"><span data-stu-id="2fdaa-200">BizTalk Server Message Context Properties (Send Handlers)</span></span>](../core/biztalk-server-message-context-properties-send-handlers.md)