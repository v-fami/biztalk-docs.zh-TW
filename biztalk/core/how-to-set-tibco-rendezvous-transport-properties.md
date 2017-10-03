---
title: "如何設定 TIBCO Rendezvous 傳輸屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setting transport properties
- transport properties, setting
ms.assetid: db8e8a57-a942-44d7-a651-623aa614c6be
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c9ff40d5319daa0a71d67aa3fd132c3d115923e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-tibco-rendezvous-transport-properties"></a><span data-ttu-id="88a4c-102">如何設定 TIBCO Rendezvous 傳輸內容</span><span class="sxs-lookup"><span data-stu-id="88a4c-102">How to Set TIBCO Rendezvous Transport Properties</span></span>
<span data-ttu-id="88a4c-103">TIBCO Rendezvous 傳輸屬性用於執行階段。</span><span class="sxs-lookup"><span data-stu-id="88a4c-103">The TIBCO Rendezvous Transport property is used for run time.</span></span> <span data-ttu-id="88a4c-104">在**傳輸屬性** 畫面上，設定連線參數來識別您要將產生的訊息發佈的 TIBCO Rendezvous 網域。</span><span class="sxs-lookup"><span data-stu-id="88a4c-104">In the **Transport Properties** screen, you set the connection parameters that identify the TIBCO Rendezvous domain where you want to publish the generated messages.</span></span>  
  
### <a name="to-specify-tibco-rendezvous-transport-properties"></a><span data-ttu-id="88a4c-105">若要指定 TIBCO Rendezvous 傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="88a4c-105">To specify TIBCO Rendezvous Transport properties</span></span>  
  
1.  <span data-ttu-id="88a4c-106">在**TIBCO Rendezvous 傳輸屬性**畫面上，依序展開**認證寄件者屬性**並輸入下列資訊。</span><span class="sxs-lookup"><span data-stu-id="88a4c-106">On the **TIBCO Rendezvous Transport Properties** screen, expand **Certified Sender Properties** and enter the following information.</span></span>  
  
     ![](../core/media/sadp-tibcoren-transs.gif "SAdp_TibcoRen_Transs")  
  
    |<span data-ttu-id="88a4c-107">使用</span><span class="sxs-lookup"><span data-stu-id="88a4c-107">Use this</span></span>|<span data-ttu-id="88a4c-108">動作</span><span class="sxs-lookup"><span data-stu-id="88a4c-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="88a4c-109">**分類帳名稱**</span><span class="sxs-lookup"><span data-stu-id="88a4c-109">**Ledger name**</span></span>|<span data-ttu-id="88a4c-110">預設值為空白。</span><span class="sxs-lookup"><span data-stu-id="88a4c-110">Default value is blank.</span></span> <span data-ttu-id="88a4c-111">要用於永續性認證訊息傳遞的分類帳檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="88a4c-111">Ledger file name to use for persistent certified message delivery.</span></span> <span data-ttu-id="88a4c-112">只能使用本機磁碟機。</span><span class="sxs-lookup"><span data-stu-id="88a4c-112">Use local drives only.</span></span>|  
    |<span data-ttu-id="88a4c-113">**可重複使用的名稱**</span><span class="sxs-lookup"><span data-stu-id="88a4c-113">**Reusable name**</span></span>|<span data-ttu-id="88a4c-114">預設值為空白。</span><span class="sxs-lookup"><span data-stu-id="88a4c-114">Default value is blank.</span></span> <span data-ttu-id="88a4c-115">要用於認證訊息傳遞的可重複使用對應名稱。</span><span class="sxs-lookup"><span data-stu-id="88a4c-115">Reusable correspondent name to use for certified message delivery.</span></span> <span data-ttu-id="88a4c-116">在網路上所有認證訊息通訊人名稱當中，這必須是唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="88a4c-116">The name must be unique among all certified message correspondent names on the network.</span></span>|  
  
2.  <span data-ttu-id="88a4c-117">展開**認證**並輸入伺服器連線的下列資訊。</span><span class="sxs-lookup"><span data-stu-id="88a4c-117">Expand **Credentials** and enter the following information for connection to the server.</span></span>  
  
    |<span data-ttu-id="88a4c-118">使用</span><span class="sxs-lookup"><span data-stu-id="88a4c-118">Use this</span></span>|<span data-ttu-id="88a4c-119">動作</span><span class="sxs-lookup"><span data-stu-id="88a4c-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="88a4c-120">**密碼**</span><span class="sxs-lookup"><span data-stu-id="88a4c-120">**Password**</span></span>|<span data-ttu-id="88a4c-121">預設值為空白。</span><span class="sxs-lookup"><span data-stu-id="88a4c-121">Default value is blank.</span></span> <span data-ttu-id="88a4c-122">登入 Tibco Rendezvous 精靈的密碼。</span><span class="sxs-lookup"><span data-stu-id="88a4c-122">Password for login to a Tibco Rendezvous daemon.</span></span>|  
    |<span data-ttu-id="88a4c-123">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="88a4c-123">**User name**</span></span>|<span data-ttu-id="88a4c-124">預設值為空白。</span><span class="sxs-lookup"><span data-stu-id="88a4c-124">Default value is blank.</span></span> <span data-ttu-id="88a4c-125">Tibco Rendezvous 精靈的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="88a4c-125">User name for Tibco Rendezvous daemon.</span></span>|  
  
3.  <span data-ttu-id="88a4c-126">展開**一般設定**並輸入 TIBCO Rendezvous 伺服器連線的下列資訊。</span><span class="sxs-lookup"><span data-stu-id="88a4c-126">Expand **General Settings** and enter the following information for connection to the TIBCO Rendezvous server.</span></span>  
  
    |<span data-ttu-id="88a4c-127">使用</span><span class="sxs-lookup"><span data-stu-id="88a4c-127">Use this</span></span>|<span data-ttu-id="88a4c-128">動作</span><span class="sxs-lookup"><span data-stu-id="88a4c-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="88a4c-129">**字碼頁編號**</span><span class="sxs-lookup"><span data-stu-id="88a4c-129">**Code Page Number**</span></span>|<span data-ttu-id="88a4c-130">預設值為 65001 (UTF-8 編碼的字碼頁)。</span><span class="sxs-lookup"><span data-stu-id="88a4c-130">Default value is 65001 (code page for UTF-8 encoding).</span></span> <span data-ttu-id="88a4c-131">這是 TIBCO Rendezvous SDK 用於字串編碼的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="88a4c-131">This is the code page that the TIBCO Rendezvous SDK uses for String encoding.</span></span>|  
    |<span data-ttu-id="88a4c-132">**預設的主體名稱**</span><span class="sxs-lookup"><span data-stu-id="88a4c-132">**Default Subject Name**</span></span>|<span data-ttu-id="88a4c-133">預設值是空白。</span><span class="sxs-lookup"><span data-stu-id="88a4c-133">Default is empty.</span></span> <span data-ttu-id="88a4c-134">主體名稱是在協調流程中設定。</span><span class="sxs-lookup"><span data-stu-id="88a4c-134">The subject name is set in the orchestration.</span></span> <span data-ttu-id="88a4c-135">如果某個連接埠用於某種訊息類型，您可以提供預設的主體名稱，這樣可以省去設定主體名稱屬性的需要，而使得協調流程變得更簡單。</span><span class="sxs-lookup"><span data-stu-id="88a4c-135">If a port is used for one message type, you can provide a default subject name, and you can simplify orchestrations by removing the need to set the Subject name property.</span></span>|  
    |<span data-ttu-id="88a4c-136">**啟用時間批次**</span><span class="sxs-lookup"><span data-stu-id="88a4c-136">**Enable Time Batch**</span></span>|<span data-ttu-id="88a4c-137">預設值為 False。</span><span class="sxs-lookup"><span data-stu-id="88a4c-137">Default value is False.</span></span> <span data-ttu-id="88a4c-138">啟用/停用 TIBCO Rendezvous 時間批次功能。</span><span class="sxs-lookup"><span data-stu-id="88a4c-138">Enable/Disable TIBCO Rendezvous Time Batch feature.</span></span>|  
    |<span data-ttu-id="88a4c-139">**將不受支援的型別對應至字串**</span><span class="sxs-lookup"><span data-stu-id="88a4c-139">**Map Unsupported types to string**</span></span>|<span data-ttu-id="88a4c-140">預設值是 True。</span><span class="sxs-lookup"><span data-stu-id="88a4c-140">Default value is True.</span></span> <span data-ttu-id="88a4c-141">如果為 true，不支援的類型會對應到字串 (如果可能的話)。</span><span class="sxs-lookup"><span data-stu-id="88a4c-141">If true, unsupported types are mapped to string if it is possible.</span></span> <span data-ttu-id="88a4c-142">若為 False，就會產生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="88a4c-142">If False, a run-time error is generated.</span></span>|  
    |<span data-ttu-id="88a4c-143">**二進位碼檔案，例如 TIBCO Rendezvous 組件的路徑**</span><span class="sxs-lookup"><span data-stu-id="88a4c-143">**Path to Binaries, such as TIBCO Rendezvous assemblies**</span></span>|<span data-ttu-id="88a4c-144">如果 PATH 環境變數中尚無此資訊，請提供此資訊。</span><span class="sxs-lookup"><span data-stu-id="88a4c-144">Provide this information if it is not already in the PATH environment variable.</span></span>|  
    |<span data-ttu-id="88a4c-145">**保留器順序**</span><span class="sxs-lookup"><span data-stu-id="88a4c-145">**Preserver Order**</span></span>|<span data-ttu-id="88a4c-146">預設值是 True。</span><span class="sxs-lookup"><span data-stu-id="88a4c-146">Default value is True.</span></span> <span data-ttu-id="88a4c-147">啟用以 BizTalk Server 收到訊息的相同順序，將訊息傳送到 TIBCO Rendezvous 的邏輯。</span><span class="sxs-lookup"><span data-stu-id="88a4c-147">Enables logic to send messages to TIBCO Rendezvous in the same order they were received from BizTalk Server.</span></span> <span data-ttu-id="88a4c-148">此參數會強制以相同的順序發佈訊息；這並不表示訂閱者會以相同的順序收到訊息。</span><span class="sxs-lookup"><span data-stu-id="88a4c-148">This parameter forces publishing in the same order; it does not mean that subscribers receive them in the same order.</span></span>|  
    |<span data-ttu-id="88a4c-149">**傳送埠識別碼**</span><span class="sxs-lookup"><span data-stu-id="88a4c-149">**Send Port Identifier**</span></span>|<span data-ttu-id="88a4c-150">這個識別項會出現在與此連接埠相關聯的記錄訊息中。</span><span class="sxs-lookup"><span data-stu-id="88a4c-150">This identifier appears in log messages associated with this port.</span></span> <span data-ttu-id="88a4c-151">這是為了方便您參考而提供。</span><span class="sxs-lookup"><span data-stu-id="88a4c-151">It is provided as a convenience.</span></span>|  
  
4.  <span data-ttu-id="88a4c-152">展開**Rendezvous 傳輸**並輸入 TIBCO Rendezvous 伺服器的連接資訊，請按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="88a4c-152">Expand **Rendezvous Transport** and enter the information for connection to the TIBCO Rendezvous server, click **Apply**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="88a4c-153">您必須設定連線參數，讓 Microsoft BizTalk Adapter for TIBCO Rendezvous 能夠存取 TIBCO Rendezvous。</span><span class="sxs-lookup"><span data-stu-id="88a4c-153">You must set connection parameters for Microsoft BizTalk Adapter for TIBCO Rendezvous to access TIBCO Rendezvous.</span></span>  
  
    |<span data-ttu-id="88a4c-154">使用</span><span class="sxs-lookup"><span data-stu-id="88a4c-154">Use this</span></span>|<span data-ttu-id="88a4c-155">動作</span><span class="sxs-lookup"><span data-stu-id="88a4c-155">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="88a4c-156">**精靈**</span><span class="sxs-lookup"><span data-stu-id="88a4c-156">**Daemon**</span></span>|<span data-ttu-id="88a4c-157">預設值是空白。</span><span class="sxs-lookup"><span data-stu-id="88a4c-157">Default is empty.</span></span><br /><br /> <span data-ttu-id="88a4c-158">Rendezvous 傳輸精靈參數。</span><span class="sxs-lookup"><span data-stu-id="88a4c-158">Rendezvous Transport Daemon parameter.</span></span>|  
    |<span data-ttu-id="88a4c-159">**網路**</span><span class="sxs-lookup"><span data-stu-id="88a4c-159">**Network**</span></span>|<span data-ttu-id="88a4c-160">預設值是空白。</span><span class="sxs-lookup"><span data-stu-id="88a4c-160">Default is empty.</span></span><br /><br /> <span data-ttu-id="88a4c-161">Rendezvous 傳輸網路參數。</span><span class="sxs-lookup"><span data-stu-id="88a4c-161">Rendezvous Transport Network parameter.</span></span>|  
    |<span data-ttu-id="88a4c-162">**服務**</span><span class="sxs-lookup"><span data-stu-id="88a4c-162">**Service**</span></span>|<span data-ttu-id="88a4c-163">預設值是空白。</span><span class="sxs-lookup"><span data-stu-id="88a4c-163">Default is empty.</span></span><br /><br /> <span data-ttu-id="88a4c-164">Rendezvous 傳輸服務參數。</span><span class="sxs-lookup"><span data-stu-id="88a4c-164">Rendezvous Transport Service parameter.</span></span>|  
  
5.  <span data-ttu-id="88a4c-165">提供使用單一登入 (SSO) 的認證。</span><span class="sxs-lookup"><span data-stu-id="88a4c-165">Provide credentials using Single Sign-On (SSO).</span></span>  
  
     <span data-ttu-id="88a4c-166">您可以使用兩種方法來存取 TIBCO Rendezvous 系統。</span><span class="sxs-lookup"><span data-stu-id="88a4c-166">There are two methods that you can use to access the TIBCO Rendezvous system.</span></span> <span data-ttu-id="88a4c-167">您可以使用認證 (使用者名稱和密碼參數) 或單一登入。</span><span class="sxs-lookup"><span data-stu-id="88a4c-167">You can use Credentials (User Name and Password parameters) or Single Sign-On.</span></span>  
  
    1.  <span data-ttu-id="88a4c-168">選取**是**中**使用 SSO**使用單一登入。</span><span class="sxs-lookup"><span data-stu-id="88a4c-168">Select **Yes** in the **Use SSO** to use Single Sign-On.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="88a4c-169">請參閱[使用單一登入](../core/using-single-sign-on5.md)如需有關如何設定 SSO 資訊。</span><span class="sxs-lookup"><span data-stu-id="88a4c-169">See [Using Single Sign-On](../core/using-single-sign-on5.md) for information about how to set up SSO.</span></span>  
  
    2.  <span data-ttu-id="88a4c-170">從清單中選取一個分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="88a4c-170">Select an affiliate application from the list.</span></span>  
  
         <span data-ttu-id="88a4c-171">企業單一登入工具建立的分支機構應用程式代表一個應用程式 (例如 TIBCO Rendezvous)。</span><span class="sxs-lookup"><span data-stu-id="88a4c-171">An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as TIBCO Rendezvous.</span></span> <span data-ttu-id="88a4c-172">Microsoft BizTalk Adapter for TIBCO Rendezvous 會使用應用程式使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="88a4c-172">Microsoft BizTalk Adapter for TIBCO Rendezvous uses the credentials of an application user.</span></span> <span data-ttu-id="88a4c-173">這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。</span><span class="sxs-lookup"><span data-stu-id="88a4c-173">These credentials are retrieved from the SSO database for the server system for a specified affiliate application.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="88a4c-174">如需如何建立分支機構應用程式資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications1.md)。</span><span class="sxs-lookup"><span data-stu-id="88a4c-174">For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications1.md).</span></span>  
  
6.  <span data-ttu-id="88a4c-175">按一下**套用**，然後按一下 **確定**提供所有必要的資訊，以採用連線資訊之後。</span><span class="sxs-lookup"><span data-stu-id="88a4c-175">Click **Apply**, and then click **OK** after providing all required information to accept the connection information.</span></span>  
  
     <span data-ttu-id="88a4c-176">您必須設定連線參數，讓 BizTalk Adapter for TIBCO Rendezvous 能夠存取 TIBCO Rendezvous。</span><span class="sxs-lookup"><span data-stu-id="88a4c-176">You must set connection parameters for BizTalk Adapter for TIBCO Rendezvous to access TIBCO Rendezvous .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a4c-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88a4c-177">See Also</span></span>  
 [<span data-ttu-id="88a4c-178">建立 TIBCO Rendezvous 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="88a4c-178">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)