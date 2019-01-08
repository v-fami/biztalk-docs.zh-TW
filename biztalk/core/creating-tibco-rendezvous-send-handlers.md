---
title: 建立 TIBCO Rendezvous 配接器傳送成品 |Microsoft Docs
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
ms.openlocfilehash: 6a267b9deac31d729d580cde79c62be96a612b4c
ms.sourcegitcommit: be6273d612669adfbb9dc9208aaae0a8437d4017
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "24014349"
---
# <a name="create-tibco-rendezvous-send-handlers"></a><span data-ttu-id="4bfbf-103">建立 TIBCO Rendezvous 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="4bfbf-103">Create TIBCO Rendezvous Send Handlers</span></span>
<span data-ttu-id="4bfbf-104">本節說明如何建立結構描述，以在 BizTalk Server 協調流程中使用 TIBCO Rendezvous。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-104">This section explains how to create a schema to use TIBCO Rendezvous in a BizTalk Server orchestration.</span></span>  
  
## <a name="create-a-send-port"></a><span data-ttu-id="4bfbf-105">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="4bfbf-105">Create a send port</span></span>
  
1.  <span data-ttu-id="4bfbf-106">在 [ **BizTalk Server 管理]**，展開**BizTalk 群組**，展開**應用程式**，然後展開您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-106">In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand your application.</span></span>  
  
2.  <span data-ttu-id="4bfbf-107">以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="4bfbf-108">在 **傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="4bfbf-108">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="4bfbf-109">輸入傳送埠名稱，例如`SendToTIBCORV`。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-109">Type a name for the send port, for example, `SendToTIBCORV`.</span></span>  
  
    2.  <span data-ttu-id="4bfbf-110">從**型別**下拉式清單中，選取**TIBCO Rendezvous**。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-110">From the **Type** drop-down list, select **TIBCO Rendezvous**.</span></span>  
  
    3.  <span data-ttu-id="4bfbf-111">從**傳送處理常式**下拉式清單中，選取的 URI。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-111">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="4bfbf-112">從 傳送管線 下拉式清單中，選取  **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-112">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  <span data-ttu-id="4bfbf-113">從**接收管線**下拉式清單中，選取 **[microsoft.biztalk.defaultpiplelines.xmlreceive]**。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-113">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  

        > [!NOTE]
        > <span data-ttu-id="4bfbf-114">Microsoft BizTalk Adapter for TIBCO Rendezvous 需要您選取 XMLTransmit 管線傳送和接收的 XMLReceive 管線。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-114">Microsoft BizTalk Adapter for TIBCO Rendezvous requires that you select XMLTransmit pipeline for send, and XMLReceive pipeline for receive.</span></span>
        
    6.  <span data-ttu-id="4bfbf-115">按一下 **設定**以設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-115">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="4bfbf-116">在  **TIBCO Rendezvous 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="4bfbf-116">In the **TIBCO Rendezvous Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="4bfbf-117">輸入屬性。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-117">Enter the properties.</span></span>  
  
         <span data-ttu-id="4bfbf-118">您不需要設定登入資訊。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-118">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="4bfbf-119">在此清單中，選取您建立來代表 TIBCO Rendezvous 系統的 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-119">In the list, select the SSO affiliate application you created to represent the TIBCO Rendezvous system.</span></span>  
  
    3.  <span data-ttu-id="4bfbf-120">針對**使用 SSO**，選取**是**。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-120">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="4bfbf-121">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-121">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="4bfbf-122">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-122">Click **OK**.</span></span>  

## <a name="set-the-transport-properties"></a><span data-ttu-id="4bfbf-123">設定傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="4bfbf-123">Set the transport properties</span></span>
<span data-ttu-id="4bfbf-124">TIBCO Rendezvous 傳輸屬性用於執行階段。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-124">The TIBCO Rendezvous Transport property is used for run time.</span></span> <span data-ttu-id="4bfbf-125">在 **傳輸屬性**，設定連線參數來識別您想要用來將產生的訊息發佈的 TIBCO Rendezvous 網域。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-125">In the **Transport Properties**, you set the connection parameters that identify the TIBCO Rendezvous domain where you want to publish the generated messages.</span></span>  
  
 
1.  <span data-ttu-id="4bfbf-126">在上**TIBCO Rendezvous 傳輸屬性**畫面上，展開**認證的寄件者屬性**並輸入下列資訊。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-126">On the **TIBCO Rendezvous Transport Properties** screen, expand **Certified Sender Properties** and enter the following information.</span></span>  
  
     <span data-ttu-id="4bfbf-127">![](../core/media/sadp-tibcoren-transs.gif "SAdp_TibcoRen_Transs")</span><span class="sxs-lookup"><span data-stu-id="4bfbf-127">![](../core/media/sadp-tibcoren-transs.gif "SAdp_TibcoRen_Transs")</span></span>  
  
    |<span data-ttu-id="4bfbf-128">使用</span><span class="sxs-lookup"><span data-stu-id="4bfbf-128">Use this</span></span>|<span data-ttu-id="4bfbf-129">動作</span><span class="sxs-lookup"><span data-stu-id="4bfbf-129">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="4bfbf-130">**分類帳名稱**</span><span class="sxs-lookup"><span data-stu-id="4bfbf-130">**Ledger name**</span></span>|<span data-ttu-id="4bfbf-131">預設值為空白。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-131">Default value is blank.</span></span> <span data-ttu-id="4bfbf-132">要用於永續性認證訊息傳遞的分類帳檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-132">Ledger file name to use for persistent certified message delivery.</span></span> <span data-ttu-id="4bfbf-133">只能使用本機磁碟機。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-133">Use local drives only.</span></span>|  
    |<span data-ttu-id="4bfbf-134">**可重複使用的名稱**</span><span class="sxs-lookup"><span data-stu-id="4bfbf-134">**Reusable name**</span></span>|<span data-ttu-id="4bfbf-135">預設值為空白。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-135">Default value is blank.</span></span> <span data-ttu-id="4bfbf-136">要用於認證訊息傳遞的可重複使用對應名稱。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-136">Reusable correspondent name to use for certified message delivery.</span></span> <span data-ttu-id="4bfbf-137">在網路上所有認證訊息通訊人名稱當中，這必須是唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-137">The name must be unique among all certified message correspondent names on the network.</span></span>|  
  
2.  <span data-ttu-id="4bfbf-138">依序展開**認證**並輸入伺服器連線的下列資訊。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-138">Expand **Credentials** and enter the following information for connection to the server.</span></span>  
  
    |<span data-ttu-id="4bfbf-139">使用</span><span class="sxs-lookup"><span data-stu-id="4bfbf-139">Use this</span></span>|<span data-ttu-id="4bfbf-140">動作</span><span class="sxs-lookup"><span data-stu-id="4bfbf-140">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="4bfbf-141">**密碼**</span><span class="sxs-lookup"><span data-stu-id="4bfbf-141">**Password**</span></span>|<span data-ttu-id="4bfbf-142">預設值為空白。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-142">Default value is blank.</span></span> <span data-ttu-id="4bfbf-143">登入 Tibco Rendezvous 精靈的密碼。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-143">Password for login to a Tibco Rendezvous daemon.</span></span>|  
    |<span data-ttu-id="4bfbf-144">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="4bfbf-144">**User name**</span></span>|<span data-ttu-id="4bfbf-145">預設值為空白。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-145">Default value is blank.</span></span> <span data-ttu-id="4bfbf-146">Tibco Rendezvous 精靈的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-146">User name for Tibco Rendezvous daemon.</span></span>|  
  
3.  <span data-ttu-id="4bfbf-147">依序展開**一般設定**並輸入 TIBCO Rendezvous 伺服器連線的下列資訊。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-147">Expand **General Settings** and enter the following information for connection to the TIBCO Rendezvous server.</span></span>  
  
    |<span data-ttu-id="4bfbf-148">使用</span><span class="sxs-lookup"><span data-stu-id="4bfbf-148">Use this</span></span>|<span data-ttu-id="4bfbf-149">動作</span><span class="sxs-lookup"><span data-stu-id="4bfbf-149">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="4bfbf-150">**字碼頁編號**</span><span class="sxs-lookup"><span data-stu-id="4bfbf-150">**Code Page Number**</span></span>|<span data-ttu-id="4bfbf-151">預設值為 65001 (UTF-8 編碼的字碼頁)。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-151">Default value is 65001 (code page for UTF-8 encoding).</span></span> <span data-ttu-id="4bfbf-152">這是 TIBCO Rendezvous SDK 用於字串編碼的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-152">This is the code page that the TIBCO Rendezvous SDK uses for String encoding.</span></span>|  
    |<span data-ttu-id="4bfbf-153">**預設的主體名稱**</span><span class="sxs-lookup"><span data-stu-id="4bfbf-153">**Default Subject Name**</span></span>|<span data-ttu-id="4bfbf-154">預設值是空白。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-154">Default is empty.</span></span> <span data-ttu-id="4bfbf-155">主體名稱是在協調流程中設定。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-155">The subject name is set in the orchestration.</span></span> <span data-ttu-id="4bfbf-156">如果某個連接埠用於某種訊息類型，您可以提供預設的主體名稱，這樣可以省去設定主體名稱屬性的需要，而使得協調流程變得更簡單。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-156">If a port is used for one message type, you can provide a default subject name, and you can simplify orchestrations by removing the need to set the Subject name property.</span></span>|  
    |<span data-ttu-id="4bfbf-157">**啟用時間批次**</span><span class="sxs-lookup"><span data-stu-id="4bfbf-157">**Enable Time Batch**</span></span>|<span data-ttu-id="4bfbf-158">預設值為 False。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-158">Default value is False.</span></span> <span data-ttu-id="4bfbf-159">啟用/停用 TIBCO Rendezvous 時間批次功能。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-159">Enable/Disable TIBCO Rendezvous Time Batch feature.</span></span>|  
    |<span data-ttu-id="4bfbf-160">**不支援的型別對應至字串**</span><span class="sxs-lookup"><span data-stu-id="4bfbf-160">**Map Unsupported types to string**</span></span>|<span data-ttu-id="4bfbf-161">預設值是 True。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-161">Default value is True.</span></span> <span data-ttu-id="4bfbf-162">如果為 true，不支援的類型會對應到字串 (如果可能的話)。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-162">If true, unsupported types are mapped to string if it is possible.</span></span> <span data-ttu-id="4bfbf-163">若為 False，就會產生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-163">If False, a run-time error is generated.</span></span>|  
    |<span data-ttu-id="4bfbf-164">**二進位檔，例如 TIBCO Rendezvous 組件的路徑**</span><span class="sxs-lookup"><span data-stu-id="4bfbf-164">**Path to Binaries, such as TIBCO Rendezvous assemblies**</span></span>|<span data-ttu-id="4bfbf-165">如果 PATH 環境變數中尚無此資訊，請提供此資訊。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-165">Provide this information if it is not already in the PATH environment variable.</span></span>|  
    |<span data-ttu-id="4bfbf-166">**保留器順序**</span><span class="sxs-lookup"><span data-stu-id="4bfbf-166">**Preserver Order**</span></span>|<span data-ttu-id="4bfbf-167">預設值是 True。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-167">Default value is True.</span></span> <span data-ttu-id="4bfbf-168">啟用以 BizTalk Server 收到訊息的相同順序，將訊息傳送到 TIBCO Rendezvous 的邏輯。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-168">Enables logic to send messages to TIBCO Rendezvous in the same order they were received from BizTalk Server.</span></span> <span data-ttu-id="4bfbf-169">此參數會強制以相同的順序發佈訊息；這並不表示訂閱者會以相同的順序收到訊息。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-169">This parameter forces publishing in the same order; it does not mean that subscribers receive them in the same order.</span></span>|  
    |<span data-ttu-id="4bfbf-170">**傳送埠識別碼**</span><span class="sxs-lookup"><span data-stu-id="4bfbf-170">**Send Port Identifier**</span></span>|<span data-ttu-id="4bfbf-171">這個識別項會出現在與此連接埠相關聯的記錄訊息中。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-171">This identifier appears in log messages associated with this port.</span></span> <span data-ttu-id="4bfbf-172">這是為了方便您參考而提供。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-172">It is provided as a convenience.</span></span>|  
  
4.  <span data-ttu-id="4bfbf-173">依序展開**Rendezvous 傳輸**並輸入至 TIBCO Rendezvous 伺服器連接資訊，請按一下**套用**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-173">Expand **Rendezvous Transport** and enter the information for connection to the TIBCO Rendezvous server, click **Apply**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="4bfbf-174">您必須設定連線參數，讓 Microsoft BizTalk Adapter for TIBCO Rendezvous 能夠存取 TIBCO Rendezvous。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-174">You must set connection parameters for Microsoft BizTalk Adapter for TIBCO Rendezvous to access TIBCO Rendezvous.</span></span>  
  
    |<span data-ttu-id="4bfbf-175">使用</span><span class="sxs-lookup"><span data-stu-id="4bfbf-175">Use this</span></span>|<span data-ttu-id="4bfbf-176">動作</span><span class="sxs-lookup"><span data-stu-id="4bfbf-176">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="4bfbf-177">**精靈**</span><span class="sxs-lookup"><span data-stu-id="4bfbf-177">**Daemon**</span></span>|<span data-ttu-id="4bfbf-178">預設值是空白。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-178">Default is empty.</span></span><br /><br /> <span data-ttu-id="4bfbf-179">Rendezvous 傳輸精靈參數。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-179">Rendezvous Transport Daemon parameter.</span></span>|  
    |<span data-ttu-id="4bfbf-180">**Network**</span><span class="sxs-lookup"><span data-stu-id="4bfbf-180">**Network**</span></span>|<span data-ttu-id="4bfbf-181">預設值是空白。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-181">Default is empty.</span></span><br /><br /> <span data-ttu-id="4bfbf-182">Rendezvous 傳輸網路參數。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-182">Rendezvous Transport Network parameter.</span></span>|  
    |<span data-ttu-id="4bfbf-183">**服務**</span><span class="sxs-lookup"><span data-stu-id="4bfbf-183">**Service**</span></span>|<span data-ttu-id="4bfbf-184">預設值是空白。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-184">Default is empty.</span></span><br /><br /> <span data-ttu-id="4bfbf-185">Rendezvous 傳輸服務參數。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-185">Rendezvous Transport Service parameter.</span></span>|  
  
5.  <span data-ttu-id="4bfbf-186">提供使用單一登入 (SSO) 的認證。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-186">Provide credentials using Single Sign-On (SSO).</span></span>  
  
     <span data-ttu-id="4bfbf-187">您可以使用兩種方法來存取 TIBCO Rendezvous 系統。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-187">There are two methods that you can use to access the TIBCO Rendezvous system.</span></span> <span data-ttu-id="4bfbf-188">您可以使用認證 (使用者名稱和密碼參數) 或單一登入。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-188">You can use Credentials (User Name and Password parameters) or Single Sign-On.</span></span>  
  
    1.  <span data-ttu-id="4bfbf-189">選取  **是**中**使用 SSO**使用單一登入。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-189">Select **Yes** in the **Use SSO** to use Single Sign-On.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="4bfbf-190">請參閱[安全性](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)如需如何設定 SSO。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-190">See [Security](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md) for information about how to set up SSO.</span></span>  
  
    2.  <span data-ttu-id="4bfbf-191">從清單中選取一個分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-191">Select an affiliate application from the list.</span></span>  
  
         <span data-ttu-id="4bfbf-192">企業單一登入工具建立的分支機構應用程式代表一個應用程式 (例如 TIBCO Rendezvous)。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-192">An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as TIBCO Rendezvous.</span></span> <span data-ttu-id="4bfbf-193">Microsoft BizTalk Adapter for TIBCO Rendezvous 會使用應用程式使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-193">Microsoft BizTalk Adapter for TIBCO Rendezvous uses the credentials of an application user.</span></span> <span data-ttu-id="4bfbf-194">這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-194">These credentials are retrieved from the SSO database for the server system for a specified affiliate application.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="4bfbf-195">如需有關如何建立分支機構應用程式的資訊，請參閱 <<c0> [ 建立分支機構應用程式](../core/creating-affiliate-applications1.md)。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-195">For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications1.md).</span></span>  
  
6.  <span data-ttu-id="4bfbf-196">按一下 **套用**，然後按一下**確定**提供所有必要的資訊，以採用連線資訊之後。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-196">Click **Apply**, and then click **OK** after providing all required information to accept the connection information.</span></span>  
  
     <span data-ttu-id="4bfbf-197">您必須設定 BizTalk adapter for TIBCO Rendezvous 能夠存取 TIBCO Rendezvous 的連線參數。</span><span class="sxs-lookup"><span data-stu-id="4bfbf-197">You must set connection parameters for BizTalk Adapter for TIBCO Rendezvous to access TIBCO Rendezvous .</span></span>  


## <a name="next-steps"></a><span data-ttu-id="4bfbf-198">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4bfbf-198">Next steps</span></span>
  
-   [<span data-ttu-id="4bfbf-199">從 BizTalk Server 使用 TIBCO Rendezvous 傳送埠</span><span class="sxs-lookup"><span data-stu-id="4bfbf-199">Using TIBCO Rendezvous Send Ports from BizTalk Server</span></span>](../core/using-tibco-rendezvous-send-ports-from-biztalk-server.md)  
  
-   [<span data-ttu-id="4bfbf-200">TIBCO Rendezvous 中的傳送處理常式資料類型對應</span><span class="sxs-lookup"><span data-stu-id="4bfbf-200">Data Type Mapping for Send Handlers in TIBCO Rendezvous</span></span>](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md)  
  
-   [<span data-ttu-id="4bfbf-201">BizTalk Server 訊息內容屬性 (傳送處理常式)</span><span class="sxs-lookup"><span data-stu-id="4bfbf-201">BizTalk Server Message Context Properties (Send Handlers)</span></span>](../core/biztalk-server-message-context-properties-send-handlers.md)