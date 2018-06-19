---
title: 企業單一登入疑難排解 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb54af9f-a6ef-46c1-b987-2019cff3f837
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 450b2df7ec043dfd4bc775cfec7acdec0fb3ca1f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975308"
---
# <a name="troubleshooting-enterprise-single-sign-on"></a><span data-ttu-id="173c8-102">疑難排解企業單一登入</span><span class="sxs-lookup"><span data-stu-id="173c8-102">Troubleshooting Enterprise Single Sign-On</span></span>
<span data-ttu-id="173c8-103">本主題描述使用企業單一登入 (SSO) 時可能遇到之常見問題的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="173c8-103">This topic describes information about common problems you may encounter while using Enterprise Single Sign-On (SSO).</span></span>  
  
 <span data-ttu-id="173c8-104">當您開始對 SSO 環境進行疑難排解時，逐步檢查下表所列事項將有助於確保所有的元件都能如預期運作：</span><span class="sxs-lookup"><span data-stu-id="173c8-104">As you begin to troubleshoot your SSO environment, it may be useful to walk through the items in the following table to ensure all components are working as expected:</span></span>  
  
|<span data-ttu-id="173c8-105">問題</span><span class="sxs-lookup"><span data-stu-id="173c8-105">Question</span></span>|<span data-ttu-id="173c8-106">註解</span><span class="sxs-lookup"><span data-stu-id="173c8-106">Comments</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="173c8-107">SSO 系統中的應用程式事件記錄中是否有任何訊息？</span><span class="sxs-lookup"><span data-stu-id="173c8-107">Is there anything in the Application event log from the SSO system?</span></span>|<span data-ttu-id="173c8-108">事件記錄中的 SSO 訊息可以幫助您縮小 SSO 系統中的問題。</span><span class="sxs-lookup"><span data-stu-id="173c8-108">The SSO messages in the event log can help you narrow down the problem in the SSO system.</span></span> <span data-ttu-id="173c8-109">SSO 系統中訊息的來源是 ENTSSO。</span><span class="sxs-lookup"><span data-stu-id="173c8-109">The source of the messages from the SSO system is ENTSSO.</span></span> <span data-ttu-id="173c8-110">**重要事項：** 許多 SSO 錯誤和事件會顯示為警告事件記錄檔中不視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="173c8-110">**Important:**  Many of the SSO errors and events appear as Warnings in the event log, not as Errors.</span></span> <span data-ttu-id="173c8-111">當問題僅影響到 SSO 服務中的單一用戶端時，SSO 會產生「警告」，而當問題影響範圍擴及整個 SSO 系統 (所有用戶端) 時，SSO 便會產生「錯誤」。</span><span class="sxs-lookup"><span data-stu-id="173c8-111">The SSO system generates a Warning when the problem affects a single client of the SSO service, whereas it generates Errors when the problem affects the entire SSO system (all clients).</span></span>|  
|<span data-ttu-id="173c8-112">SSO 服務是否安裝正確？</span><span class="sxs-lookup"><span data-stu-id="173c8-112">Is the SSO service installed correctly?</span></span><br /><br /> <span data-ttu-id="173c8-113">是否依預期方式啟動？</span><span class="sxs-lookup"><span data-stu-id="173c8-113">Does it start as expected?</span></span><br /><br /> <span data-ttu-id="173c8-114">SSO 服務在哪一種服務帳戶下執行？</span><span class="sxs-lookup"><span data-stu-id="173c8-114">Under which service account is the SSO service running?</span></span>|<span data-ttu-id="173c8-115">請確定 SSO 服務安裝正確，而且該服務帳戶是 SSO 系統管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="173c8-115">Ensure the SSO service is correctly installed, and that the service account is member of the SSO administrators group.</span></span>|  
|<span data-ttu-id="173c8-116">SSO 資料庫在哪裡？</span><span class="sxs-lookup"><span data-stu-id="173c8-116">Where is the SSO database?</span></span>|<span data-ttu-id="173c8-117">使用命令列 **ssoconfig -showdb**。</span><span class="sxs-lookup"><span data-stu-id="173c8-117">Use the command line **ssoconfig -showdb**.</span></span> <span data-ttu-id="173c8-118">如需此命令的詳細資訊，請參閱[如何顯示 SSO 資料庫資訊](../core/how-to-display-the-sso-database-information.md)。</span><span class="sxs-lookup"><span data-stu-id="173c8-118">For more information about this command, see [How to Display the SSO Database Information](../core/how-to-display-the-sso-database-information.md).</span></span>|  
|<span data-ttu-id="173c8-119">正在使用哪一部 SSO 伺服器？</span><span class="sxs-lookup"><span data-stu-id="173c8-119">Which SSO server is being used?</span></span>|<span data-ttu-id="173c8-120">使用命令列 **ssomanage -showserver**。</span><span class="sxs-lookup"><span data-stu-id="173c8-120">Use the command line **ssomanage -showserver**.</span></span> <span data-ttu-id="173c8-121">如需此命令的詳細資訊，請參閱[如何設定 SSO 伺服器](../core/how-to-set-the-sso-server.md)。</span><span class="sxs-lookup"><span data-stu-id="173c8-121">For more information about this command, see [How to Set the SSO Server](../core/how-to-set-the-sso-server.md).</span></span>|  
|<span data-ttu-id="173c8-122">SSO 管理員帳戶為何？</span><span class="sxs-lookup"><span data-stu-id="173c8-122">What is the SSO Administrator account?</span></span>|<span data-ttu-id="173c8-123">使用命令列 **ssomanage –displaydb**。</span><span class="sxs-lookup"><span data-stu-id="173c8-123">Use the command line **ssomanage –displaydb**.</span></span> <span data-ttu-id="173c8-124">如需此命令的詳細資訊，請參閱[如何顯示 SSO 資料庫資訊](../core/how-to-display-the-sso-database-information.md)。</span><span class="sxs-lookup"><span data-stu-id="173c8-124">For more information about this command, see [How to Display the SSO Database Information](../core/how-to-display-the-sso-database-information.md).</span></span>|  
|<span data-ttu-id="173c8-125">是否已正確啟用所有項目？</span><span class="sxs-lookup"><span data-stu-id="173c8-125">Is everything correctly enabled?</span></span>|<span data-ttu-id="173c8-126">使用命令列 **ssomanage –displaydb**。</span><span class="sxs-lookup"><span data-stu-id="173c8-126">Use the command line **ssomanage –displaydb**.</span></span> <span data-ttu-id="173c8-127">如需此命令的詳細資訊，請參閱[如何顯示 SSO 資料庫資訊](../core/how-to-display-the-sso-database-information.md)。</span><span class="sxs-lookup"><span data-stu-id="173c8-127">For more information about this command, see [How to Display the SSO Database Information](../core/how-to-display-the-sso-database-information.md).</span></span>|  
|<span data-ttu-id="173c8-128">是否有分支機構應用程式？</span><span class="sxs-lookup"><span data-stu-id="173c8-128">Do the affiliate applications exist?</span></span>|<span data-ttu-id="173c8-129">使用命令列 **ssomanage –listapps all**。</span><span class="sxs-lookup"><span data-stu-id="173c8-129">Use the command line **ssomanage –listapps all**.</span></span> <span data-ttu-id="173c8-130">如需此命令的詳細資訊，請參閱[如何列出分支機構應用程式](../core/how-to-list-affiliate-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="173c8-130">For more information about this command, see [How to List Affiliate Applications](../core/how-to-list-affiliate-applications.md).</span></span>|  
|<span data-ttu-id="173c8-131">特定的分支機構應用程式外觀是否正確？</span><span class="sxs-lookup"><span data-stu-id="173c8-131">Does the specific affiliate application look correct?</span></span><br /><br /> <span data-ttu-id="173c8-132">哪些帳戶正在使用此分支機構應用程式？</span><span class="sxs-lookup"><span data-stu-id="173c8-132">What accounts are using this affiliate application?</span></span>|<span data-ttu-id="173c8-133">使用命令列**ssomanage-displayapp***\<應用程式名稱\>*。</span><span class="sxs-lookup"><span data-stu-id="173c8-133">Use the command line **ssomanage –displayapp***\<application name\>*.</span></span> <span data-ttu-id="173c8-134">如需此命令的詳細資訊，請參閱[如何列出分支機構應用程式的屬性](../core/how-to-list-the-properties-of-an-affiliate-application.md)。</span><span class="sxs-lookup"><span data-stu-id="173c8-134">For more information about this command, see [How to List the Properties of an Affiliate Application](../core/how-to-list-the-properties-of-an-affiliate-application.md).</span></span>|  
|<span data-ttu-id="173c8-135">此分支機構應用程式是否有任何對應？</span><span class="sxs-lookup"><span data-stu-id="173c8-135">Are there any mappings for this affiliate application?</span></span>|<span data-ttu-id="173c8-136">使用命令列**ssomanage – listmappings***\<應用程式名稱\>*。</span><span class="sxs-lookup"><span data-stu-id="173c8-136">Use the command line **ssomanage –listmappings***\<application name\>*.</span></span> <span data-ttu-id="173c8-137">如需此命令的詳細資訊，請參閱[如何列出使用者對應](../core/how-to-list-user-mappings.md)。</span><span class="sxs-lookup"><span data-stu-id="173c8-137">For more information about this command, see [How to List User Mappings](../core/how-to-list-user-mappings.md).</span></span>|  
|<span data-ttu-id="173c8-138">哪些帳戶是 SSO 群組的成員？</span><span class="sxs-lookup"><span data-stu-id="173c8-138">What accounts are members of the SSO groups?</span></span>|<span data-ttu-id="173c8-139">請驗證所有 SSO 群組和帳戶的群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="173c8-139">Verify the group membership for all SSO groups and accounts.</span></span>|  
|<span data-ttu-id="173c8-140">SSO 伺服器的 COM+ 應用程式的執行是否符合預期？</span><span class="sxs-lookup"><span data-stu-id="173c8-140">Is the COM+ application for the SSO server running as expected?</span></span>|<span data-ttu-id="173c8-141">驗證 COM+ 應用程式 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="173c8-141">Verify the COM+ application SSO server.</span></span> <span data-ttu-id="173c8-142">**注意：** 您也可以檢查事件記錄檔的詳細資訊，例如事件和警告訊息。</span><span class="sxs-lookup"><span data-stu-id="173c8-142">**Note:**  You can also check the event log for detailed information, such as event and warning messages.</span></span>|  
  
## <a name="known-issues"></a><span data-ttu-id="173c8-143">已知問題</span><span class="sxs-lookup"><span data-stu-id="173c8-143">Known Issues</span></span>  
  
#### <a name="entsso-service-fails-to-start"></a><span data-ttu-id="173c8-144">ENTSSO 服務無法啟動</span><span class="sxs-lookup"><span data-stu-id="173c8-144">ENTSSO Service Fails to Start</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="173c8-145">問題</span><span class="sxs-lookup"><span data-stu-id="173c8-145">Problem</span></span>  
 <span data-ttu-id="173c8-146">ENTSSO 服務無法啟動。</span><span class="sxs-lookup"><span data-stu-id="173c8-146">The ENTSSO service fails to start.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="173c8-147">原因</span><span class="sxs-lookup"><span data-stu-id="173c8-147">Cause</span></span>  
 <span data-ttu-id="173c8-148">如果 ENTSSO 服務不是以有效的 SSO 系統管理員帳戶執行，便無法啟動。</span><span class="sxs-lookup"><span data-stu-id="173c8-148">If the ENTSSO service is not running under a valid SSO Administrator account, it will fail to start.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="173c8-149">解決方案</span><span class="sxs-lookup"><span data-stu-id="173c8-149">Resolution</span></span>  
 <span data-ttu-id="173c8-150">為 ENTSSO 服務指定有效的 SSO 系統管理員帳戶，並從服務控制管理員 (SCM) 嵌入式管理單元重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="173c8-150">Specify a valid SSO administrator account for the ENTSSO Service and restart the service from Services Control Manager (SCM) snap-in.</span></span>  
  
#### <a name="biztalk-services-dependent-on-the-enterprise-single-sign-on-service-entsso-fail-to-start-after-a-reboot"></a><span data-ttu-id="173c8-151">相依於企業單一登入服務 (ENTSSO) 的 BizTalk 服務無法在重新開機後啟動</span><span class="sxs-lookup"><span data-stu-id="173c8-151">BizTalk Services Dependent on the Enterprise Single Sign-On Service (ENTSSO) fail to start after a reboot</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="173c8-152">問題</span><span class="sxs-lookup"><span data-stu-id="173c8-152">Problem</span></span>  
 <span data-ttu-id="173c8-153">BTSSvc$BizTalkServerApplication 相依於企業單一登入服務 (ENTSSO)，重新開機後可能會在啟動時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="173c8-153">BTSSvc$BizTalkServerApplication has a dependency on the Enterprise Single Sign-On Service (ENTSSO) and may timeout during start up after a reboot.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="173c8-154">原因</span><span class="sxs-lookup"><span data-stu-id="173c8-154">Cause</span></span>  
 <span data-ttu-id="173c8-155">企業單一登入服務可能需要約 3 分鐘的時間才能啟動。</span><span class="sxs-lookup"><span data-stu-id="173c8-155">The Enterprise Single Sign-On Service may take around 3 minutes to start.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="173c8-156">解決方案</span><span class="sxs-lookup"><span data-stu-id="173c8-156">Resolution</span></span>  
 <span data-ttu-id="173c8-157">將 “BizTalk Service BizTalk Group：BizTalkServerApplication” 服務的啟動類型選項設定為 [自動 (延遲開始)]。</span><span class="sxs-lookup"><span data-stu-id="173c8-157">Configure the “BizTalk Service BizTalk Group: BizTalkServerApplication” service with the Automatic (Delayed Start) startup type option.</span></span> <span data-ttu-id="173c8-158">這會在所有自動服務皆完成啟動程序後，再啟動該服務。</span><span class="sxs-lookup"><span data-stu-id="173c8-158">This will initiate the start of the service after all Automatic services have completed their startup routines.</span></span>  
  
#### <a name="cannot-access-an-affiliate-application"></a><span data-ttu-id="173c8-159">無法存取分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="173c8-159">Cannot Access an Affiliate Application</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="173c8-160">問題</span><span class="sxs-lookup"><span data-stu-id="173c8-160">Problem</span></span>  
 <span data-ttu-id="173c8-161">如果與分支機構應用程式相關聯的應用程式系統管理員帳戶無效，企業單一登入服務就會停用該分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="173c8-161">The Enterprise Single Sign-On service disables an affiliate application if the application administrator account associated with it is not valid.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="173c8-162">原因</span><span class="sxs-lookup"><span data-stu-id="173c8-162">Cause</span></span>  
 <span data-ttu-id="173c8-163">SSO 應用程式系統管理員帳戶無效。</span><span class="sxs-lookup"><span data-stu-id="173c8-163">The SSO application administrator account is not valid.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="173c8-164">解決方案</span><span class="sxs-lookup"><span data-stu-id="173c8-164">Resolution</span></span>  
 <span data-ttu-id="173c8-165">建立分支機構應用程式之前，請先確定 SSO 應用程式系統管理員帳戶是否有效。</span><span class="sxs-lookup"><span data-stu-id="173c8-165">Ensure that the SSO application administrator account is valid before you create an affiliate application.</span></span> <span data-ttu-id="173c8-166">接著，您必須啟用分支機構應用程式，才能使用該應用程式。</span><span class="sxs-lookup"><span data-stu-id="173c8-166">You must then enable the affiliate application to use the application.</span></span>  
  
#### <a name="rpc-error-occurs-when-connecting-to-a-client-computer"></a><span data-ttu-id="173c8-167">連接到用戶端電腦時發生 RPC 錯誤</span><span class="sxs-lookup"><span data-stu-id="173c8-167">RPC Error Occurs When Connecting to a Client Computer</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="173c8-168">問題</span><span class="sxs-lookup"><span data-stu-id="173c8-168">Problem</span></span>  
 <span data-ttu-id="173c8-169">當使用者執行命令例如**ssomanage-displayapp***\<applicationname\>*，其中電腦嘗試連線到遠端 SSO 伺服器以擷取資訊，他們會收到下列錯誤： 錯誤： 0x800706BA: RPC 伺服器不存在。</span><span class="sxs-lookup"><span data-stu-id="173c8-169">When a user runs a command such as **ssomanage -displayapp***\<applicationname\>*, where the computer attempt to connect to a remote SSO Server to retrieve the information, they receive the following error: ERROR: 0x800706BA: The RPC server is unavailable.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="173c8-170">原因</span><span class="sxs-lookup"><span data-stu-id="173c8-170">Cause</span></span>  
 <span data-ttu-id="173c8-171">當使用者指定的伺服器不正確，或是遠端伺服器上的 SSO 服務無法使用時，都會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="173c8-171">This error occurs when the user specifies the wrong server information, or when the SSO Service is not available on the remote server.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="173c8-172">解決方案</span><span class="sxs-lookup"><span data-stu-id="173c8-172">Resolution</span></span>  
  
-   <span data-ttu-id="173c8-173">請依照[如何設定 SSO 伺服器](../core/how-to-set-the-sso-server.md)來確認您已連接到正確的 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="173c8-173">Follow the steps in [How to Set the SSO Server](../core/how-to-set-the-sso-server.md) to make sure you are connected to the correct SSO Server.</span></span>  
  
-   <span data-ttu-id="173c8-174">確定 SSO 服務已在您所連接的 SSO 伺服器上啟用及執行。</span><span class="sxs-lookup"><span data-stu-id="173c8-174">Make sure the SSO Service is enabled and running in the SSO Server to which you are connecting.</span></span>  
  
#### <a name="master-secret-is-missing-or-corrupt"></a><span data-ttu-id="173c8-175">主要密碼遺漏或損毀</span><span class="sxs-lookup"><span data-stu-id="173c8-175">Master Secret Is Missing or Corrupt</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="173c8-176">問題</span><span class="sxs-lookup"><span data-stu-id="173c8-176">Problem</span></span>  
 <span data-ttu-id="173c8-177">主要密碼遺漏或損毀。</span><span class="sxs-lookup"><span data-stu-id="173c8-177">The master secret is missing or corrupt.</span></span> <span data-ttu-id="173c8-178">這個密碼通常會在設定組態時產生。</span><span class="sxs-lookup"><span data-stu-id="173c8-178">It normally generates during configuration.</span></span> <span data-ttu-id="173c8-179">若遺漏此密碼，則企業單一登入服務啟動時，事件記錄中就會出現下列其中一則訊息。</span><span class="sxs-lookup"><span data-stu-id="173c8-179">If the secret is missing, one of the following messages will display in the event log as the Enterprise Single Sign-On service starts.</span></span>  
  
 <span data-ttu-id="173c8-180">MessageId=10520</span><span class="sxs-lookup"><span data-stu-id="173c8-180">MessageId=10520</span></span>  
  
 <span data-ttu-id="173c8-181">Severity=Warning</span><span class="sxs-lookup"><span data-stu-id="173c8-181">Severity=Warning</span></span>  
  
 <span data-ttu-id="173c8-182">SSO_WARN_NO_SECRETS</span><span class="sxs-lookup"><span data-stu-id="173c8-182">SSO_WARN_NO_SECRETS</span></span>  
  
 <span data-ttu-id="173c8-183">MessageId=10565</span><span class="sxs-lookup"><span data-stu-id="173c8-183">MessageId=10565</span></span>  
  
 <span data-ttu-id="173c8-184">Severity=Error</span><span class="sxs-lookup"><span data-stu-id="173c8-184">Severity=Error</span></span>  
  
 <span data-ttu-id="173c8-185">SSO_ERROR_SECRET_VALIDATE_FAILED</span><span class="sxs-lookup"><span data-stu-id="173c8-185">SSO_ERROR_SECRET_VALIDATE_FAILED</span></span>  
  
 <span data-ttu-id="173c8-186">MessageId=10521</span><span class="sxs-lookup"><span data-stu-id="173c8-186">MessageId=10521</span></span>  
  
 <span data-ttu-id="173c8-187">Severity=Error</span><span class="sxs-lookup"><span data-stu-id="173c8-187">Severity=Error</span></span>  
  
 <span data-ttu-id="173c8-188">SSO_ERROR_SECRETS_NOT_LOADED</span><span class="sxs-lookup"><span data-stu-id="173c8-188">SSO_ERROR_SECRETS_NOT_LOADED</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="173c8-189">原因</span><span class="sxs-lookup"><span data-stu-id="173c8-189">Cause</span></span>  
 <span data-ttu-id="173c8-190">如果密碼是在企業單一登入服務 (SSO) 使用某個服務帳戶執行時產生，但後來服務帳戶發生變更，就有可能發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="173c8-190">This problem can occur if a secret is generated while the Enterprise Single Sign-On service (SSO) was running under one service account, and then the service account was changed.</span></span> <span data-ttu-id="173c8-191">此密碼是以加密的形式儲存在登錄中，加密時則是使用依據服務帳戶 (用來執行 ENTSSO 者) 的識別所產生的金鑰。</span><span class="sxs-lookup"><span data-stu-id="173c8-191">The secret is stored in the registry in encrypted form, and is encrypted using a key based on the identity of the service account (which ENTSSO runs under).</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="173c8-192">解決方案</span><span class="sxs-lookup"><span data-stu-id="173c8-192">Resolution</span></span>  
 <span data-ttu-id="173c8-193">將 ENTSSO 執行時所用的服務帳戶變更為建立主要密碼時的原始服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="173c8-193">Change the service account ENTSSO is running under to the original service account when the master secret was created.</span></span>  
  
 <span data-ttu-id="173c8-194">若要變更 ENTSSO 服務帳戶：</span><span class="sxs-lookup"><span data-stu-id="173c8-194">To change the ENTSSO service account:</span></span>  
  
1.  <span data-ttu-id="173c8-195">備份主要密碼。</span><span class="sxs-lookup"><span data-stu-id="173c8-195">Back up the master secret.</span></span> <span data-ttu-id="173c8-196">如需詳細資訊，請參閱[如何重新設定主要密碼](../core/how-to-back-up-the-master-secret.md)。</span><span class="sxs-lookup"><span data-stu-id="173c8-196">For more information, see [How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md).</span></span>  
  
2.  <span data-ttu-id="173c8-197">停止企業單一登入服務。</span><span class="sxs-lookup"><span data-stu-id="173c8-197">Stop Enterprise Single Sign-On Services.</span></span>  
  
3.  <span data-ttu-id="173c8-198">變更服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="173c8-198">Change the service account.</span></span>  
  
4.  <span data-ttu-id="173c8-199">重新啟動 SSO，並忽略任何與密碼損毀有關的事件記錄錯誤。</span><span class="sxs-lookup"><span data-stu-id="173c8-199">Restart SSO and ignore any event log errors about a corrupted secret.</span></span>  
  
5.  <span data-ttu-id="173c8-200">還原主要密碼。</span><span class="sxs-lookup"><span data-stu-id="173c8-200">Restore the master secret.</span></span> <span data-ttu-id="173c8-201">如需詳細資訊，請參閱[如何還原主要密碼](../core/how-to-restore-the-master-secret.md)。</span><span class="sxs-lookup"><span data-stu-id="173c8-201">For more information, see [How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="173c8-202">請參閱</span><span class="sxs-lookup"><span data-stu-id="173c8-202">See Also</span></span>  
 [<span data-ttu-id="173c8-203">實作企業單一登入</span><span class="sxs-lookup"><span data-stu-id="173c8-203">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)