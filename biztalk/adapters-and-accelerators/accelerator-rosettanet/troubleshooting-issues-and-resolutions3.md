---
title: 疑難排解： 問題與 Resolutions3 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting
ms.assetid: 40f59f54-183e-43db-afb5-0a45b437697f
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab1f869d8d7c06260a1f7f8388991a0e18a2ff09
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50758693"
---
# <a name="troubleshooting-issues-and-resolutions"></a><span data-ttu-id="6ccc4-102">疑難排解： 問題與解決方式</span><span class="sxs-lookup"><span data-stu-id="6ccc4-102">Troubleshooting: Issues and Resolutions</span></span>
<span data-ttu-id="6ccc4-103">本主題說明執行 Microsoft® 相關的問題[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-103">This topic addresses issues related to running Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="6ccc4-104">每個問題的說明都會詳細描述其特殊徵狀、可能的原因以及解決方式。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-104">The individual issues detail a specific symptom, a possible cause, and a solution.</span></span>  
  
## <a name="error-publishing-a-batch-of-n-messages"></a><span data-ttu-id="6ccc4-105">發佈 n 個訊息的批次作業時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="6ccc4-105">Error publishing a batch of "n" messages</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-106">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-106">Symptom</span></span>  
 <span data-ttu-id="6ccc4-107">您在事件日誌中收到下列或類似的錯誤：</span><span class="sxs-lookup"><span data-stu-id="6ccc4-107">You receive the following or similar error in the event log:</span></span>  
  
 <span data-ttu-id="6ccc4-108">為傳輸配接器「BizTalk HTTP 接收者」發佈 n 個訊息的批次作業至 MessageBox 資料庫時，傳訊引擎發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-108">The Messaging Engine encountered an error publishing a batch of "n" messages to the Message Box database for the transport adapter "BizTalk HTTP Receiver".</span></span> <span data-ttu-id="6ccc4-109">如需有關此失敗的詳細資訊，請參考「狀況與活動追蹤」工具，並檢查是否已正確設定結束點繫結。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-109">Please refer to Health and Activity Tracking tool for more detailed information on this failure and check the endpoint bindings are correctly configured.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-110">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-110">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-111">此錯誤可能是由下列其中一項原因所造成：</span><span class="sxs-lookup"><span data-stu-id="6ccc4-111">This error could be caused by one of the following reasons:</span></span>  
  
- <span data-ttu-id="6ccc4-112">遺失解密憑證</span><span class="sxs-lookup"><span data-stu-id="6ccc4-112">Missing decryption certificate</span></span>  
  
- <span data-ttu-id="6ccc4-113">未正確加密的訊息</span><span class="sxs-lookup"><span data-stu-id="6ccc4-113">Incorrectly encrypted message</span></span>  
  
- <span data-ttu-id="6ccc4-114">未授權的訊息 (來源無法辨識為有效的夥伴)</span><span class="sxs-lookup"><span data-stu-id="6ccc4-114">Unauthorized message (source not recognized as a valid partner)</span></span>  
  
- <span data-ttu-id="6ccc4-115">訊息的任何標頭部分驗證失敗：前序、傳遞標頭或服務標頭。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-115">Message failing validation of any header part: preamble, delivery header, or service header.</span></span>  
  
  <span data-ttu-id="6ccc4-116">此訊息之前可能有另一錯誤訊息，詳細說明原因。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-116">This message may be preceded by another error message that details the cause.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-117">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-117">Solution</span></span>  
 <span data-ttu-id="6ccc4-118">請檢閱錯誤訊息所提供的詳細資訊，可取得額外的協助。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-118">Review the details provided with the error message for additional help.</span></span> <span data-ttu-id="6ccc4-119">正在重新啟動 Microsoft [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]™ 可能可以解決此問題。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-119">Restarting Microsoft [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]™ may resolve this issue.</span></span>  
  
## <a name="you-cannot-unenlist-all-artifacts"></a><span data-ttu-id="6ccc4-120">無法取消登錄所有成品</span><span class="sxs-lookup"><span data-stu-id="6ccc4-120">You cannot unenlist all artifacts</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-121">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-121">Symptom</span></span>  
 <span data-ttu-id="6ccc4-122">執行 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Clean 公用程式並未取消登錄所有成品。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-122">Running the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Clean utility does not unenlist all artifacts.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-123">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-123">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-124">如果您執行[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]之前刪除協議與夥伴從 Microsoft® Management Console (MMC) 的 Clean 公用程式，BtarnClean 公用程式將無法取消登錄所有成品，因為仍在使用。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-124">If you run the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Clean utility before deleting agreements and partners from the Microsoft® Management Console (MMC), the BtarnClean utility will not be able to unenlist all artifacts because they are still used.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-125">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-125">Solution</span></span>  
  
##### <a name="to-remove-artifacts-using-the-loopback-utility"></a><span data-ttu-id="6ccc4-126">用回送公用程式移除成品</span><span class="sxs-lookup"><span data-stu-id="6ccc4-126">To remove artifacts using the Loopback utility</span></span>  
  
1.  <span data-ttu-id="6ccc4-127">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="6ccc4-127">At the command prompt, type:</span></span>  
  
    ```  
    lookback.exe /disable <home org or partner>  
    ```  
  
2.  <span data-ttu-id="6ccc4-128">執行 BtarnClean.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-128">Run the BtarnClean.exe file.</span></span>  
  
3.  <span data-ttu-id="6ccc4-129">在 [BizTalk 總管] 中刪除合作對象。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-129">In BizTalk Explorer, delete the parties.</span></span>  
  
## <a name="installing-btarn-on-a-computer-without-biztalk-server-causes-missing-files"></a><span data-ttu-id="6ccc4-130">沒有 BizTalk Server 的電腦上安裝 BTARN 會導致檔案遺失</span><span class="sxs-lookup"><span data-stu-id="6ccc4-130">Installing BTARN on a computer without BizTalk Server causes missing files</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-131">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-131">Symptom</span></span>  
 <span data-ttu-id="6ccc4-132">執行 ConfigFramework.exe 檔案會產生任何結果，並沒有 MicrosoftBizTalk Server 或 Microsoft 的電腦上[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-132">Running the ConfigFramework.exe file yields no results on a computer that does not have MicrosoftBizTalk Server or Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] installed.</span></span> <span data-ttu-id="6ccc4-133">這個 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 組態只能當作 HTTP 用戶端使用。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-133">You can only use this [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration as an HTTP client.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-134">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-134">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-135">在安裝中遺失兩個 DLL 檔案。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-135">Two DLL files are missing from the installation.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-136">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-136">Solution</span></span>  
 <span data-ttu-id="6ccc4-137">在電腦上安裝 SQLXML，然後手動將 Msxml4.dll 與 Atl71.dll 檔案複製到 [System] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-137">Install SQLXML on the computer, and then manually copy the Msxml4.dll and Atl71.dll files to the System folder.</span></span>  
  
## <a name="you-receive-an-access-error-when-attempting-to-change-the-btarn-configuration"></a><span data-ttu-id="6ccc4-138">要變更 BTARN 組態時收到存取錯誤</span><span class="sxs-lookup"><span data-stu-id="6ccc4-138">You receive an access error when attempting to change the BTARN configuration</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-139">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-139">Symptom</span></span>  
 <span data-ttu-id="6ccc4-140">當您使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台匯入組態檔案時，收到下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="6ccc4-140">You receive the following error message when you import a configuration file using the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console:</span></span>  
  
 <span data-ttu-id="6ccc4-141">無法將「傳送埠」'RNSTT.Async' 的「主要傳輸」之傳輸類型資料存放至組態存放區。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-141">Could not store transport type data for Primary Transport of Send Port 'RNSTT.Async' to config store.</span></span> <span data-ttu-id="6ccc4-142">存取遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-142">Access is denied.</span></span>  
  
 <span data-ttu-id="6ccc4-143">當您嘗試變更組態 (例如要建立新的夥伴) 時，也可能會收到這種錯誤。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-143">You can also receive this error when you try to change the configuration, such as by creating a new partner.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-144">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-144">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-145">目前使用者並非「BizTalk 系統管理員」群組中的成員。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-145">The current user is not a member of the BizTalk Administrators group.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-146">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-146">Solution</span></span>  
 <span data-ttu-id="6ccc4-147">請確認目前使用者為「BizTalk 系統管理員」群組中的成員。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-147">Make sure that the current user is a member of the BizTalk Administrators group.</span></span>  
  
## <a name="you-receive-bam-errors"></a><span data-ttu-id="6ccc4-148">收到 BAM 錯誤</span><span class="sxs-lookup"><span data-stu-id="6ccc4-148">You receive BAM errors</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-149">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-149">Symptom</span></span>  
 <span data-ttu-id="6ccc4-150">「事件檢視器」中出現以下錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="6ccc4-150">You receive the following error messages in the Event Viewer:</span></span>  
  
 <span data-ttu-id="6ccc4-151">在追蹤「訊息」活動中發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-151">Error happened in tracking Message activity.</span></span> <span data-ttu-id="6ccc4-152">錯誤訊息為「預存程序不存在」。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-152">Error message is Stored Procedure Does Not Exist.</span></span>  
  
 <span data-ttu-id="6ccc4-153">-或-</span><span class="sxs-lookup"><span data-stu-id="6ccc4-153">-or-</span></span>  
  
 <span data-ttu-id="6ccc4-154">終止 BAM 訊息活動識別碼的錯誤 *\<ID 編號\>*。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-154">Error in terminating BAM message activity with id *\<ID number\>*.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-155">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-155">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-156">未安裝商務活動監控 (BAM) 追蹤工具。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-156">The Business Activity Monitoring (BAM) tracking tool is not installed.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-157">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-157">Solution</span></span>  
 <span data-ttu-id="6ccc4-158">安裝追蹤工具使用 BAM **Custom Installation**選項。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-158">Install the BAM tracking tool using the **Custom Installation** option.</span></span> <span data-ttu-id="6ccc4-159">如果您不需要 BAM 功能，可以忽略這些訊息，或利用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台停用追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-159">If you do not need BAM functionality, you can ignore these messages or disable tracking using the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console.</span></span> <span data-ttu-id="6ccc4-160">停用追蹤功能之後，必須重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 與 Internet Information Services (IIS)。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-160">After you disable tracking, you must restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and Internet and Information Services (IIS).</span></span>  
  
## <a name="your-xsd-schema-does-not-display-properly-in-biztalk-editor"></a><span data-ttu-id="6ccc4-161">您的 XSD 結構描述無法正確顯示在 BizTalk 編輯器中</span><span class="sxs-lookup"><span data-stu-id="6ccc4-161">Your XSD Schema does not display properly in BizTalk Editor</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-162">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-162">Symptom</span></span>  
 <span data-ttu-id="6ccc4-163">無法用 BizTalk 編輯器正確檢視結構描述的內容。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-163">You cannot view the content of a schema properly in BizTalk Editor.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-164">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-164">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-165">結構描述缺少 `displayroot_reference` 項目的 `schemaInfo` 屬性。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-165">The schema is missing the `displayroot_reference` attribute for the `schemaInfo` element.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-166">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-166">Solution</span></span>  
 <span data-ttu-id="6ccc4-167">使用 [記事本] 或其他文字編輯器開啟這個結構描述，並將 `displayroot_reference` 屬性加入至 `schemaInfo` 項目內。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-167">Open the schema in Notepad or another text editor and add the `displayroot_reference` attribute to the `schemaInfo` element.</span></span> <span data-ttu-id="6ccc4-168">`displayroot_reference` 屬性的值應該與 `root_reference` 屬性相同。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-168">The value of the `displayroot_reference` attribute should be the same as the `root_reference` attribute.</span></span>  
  
 <span data-ttu-id="6ccc4-169">例如：</span><span class="sxs-lookup"><span data-stu-id="6ccc4-169">For example:</span></span>  
  
 <span data-ttu-id="6ccc4-170">\<schemaInfo document_type ="4A1"版本 ="V02_00"xmlns ="<http://schemas.microsoft.com/BizTalk/2003>」 *displayroot_reference ="Pip4A1StrategicForecastNotification"* root_reference ="Pip4A1StrategicForecastNotification 」 \></span><span class="sxs-lookup"><span data-stu-id="6ccc4-170">\<schemaInfo document_type="4A1" version="V02_00" xmlns="<http://schemas.microsoft.com/BizTalk/2003>" *displayroot_reference="Pip4A1StrategicForecastNotification"* root_reference="Pip4A1StrategicForecastNotification" \></span></span>  
  
## <a name="404-not-found-error-when-sending-a-http-request"></a><span data-ttu-id="6ccc4-171">發出 HTTP 要求卻收到「404 找不到」(404 Not Found) 錯誤</span><span class="sxs-lookup"><span data-stu-id="6ccc4-171">404 Not found error when sending a HTTP request</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-172">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-172">Symptom</span></span>  
 <span data-ttu-id="6ccc4-173">當傳送 HTTP 要求時，收到下列或類似的錯誤：</span><span class="sxs-lookup"><span data-stu-id="6ccc4-173">You receive the following or similar errors when sending a HTTP request:</span></span>  
  
 <span data-ttu-id="6ccc4-174">遠端伺服器傳回錯誤：(404) 找不到。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-174">The remote server returned an error: (404) Not Found.</span></span>  
  
 <span data-ttu-id="6ccc4-175">訊息無法傳送至 ../BTSHttpReceive.dll。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-175">Message cannot be sent to ../BTSHttpReceive.dll.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-176">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-176">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-177">Internet Information Services (IIS) 中的 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 網際網路伺服器 API (ISAPI) 擴充程式 DLL (BTSHttpReceive.dll) 尚未設定好。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-177">The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Internet Server API (ISAPI) extension DLL (BTSHttpReceive.dll) has not been configured in Internet Information Services (IIS).</span></span> <span data-ttu-id="6ccc4-178">如果 HwsMessages HttpReceive Web 服務延伸模組未設定，或這個 Web 服務延伸模組已設定但不被允許，就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-178">This occurs if the HwsMessages HttpReceive web service extension is not configured and if this web service extension is configured, but not allowed.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-179">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-179">Solution</span></span>  
 <span data-ttu-id="6ccc4-180">請執行下列程序，判斷 HwsMessages HttpReceive Web 服務延伸模組是否已設定為允許 (或尚未設定)。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-180">To determine whether the HwsMessages HttpReceive web service extension is configured, and if it is not configured, to allow it, perform the following procedure.</span></span>  
  
##### <a name="to-configure-the-biztalk-isapi-extension-dll-in-iis"></a><span data-ttu-id="6ccc4-181">在 IIS 中設定 BizTalk ISAPI 擴充程式 DLL</span><span class="sxs-lookup"><span data-stu-id="6ccc4-181">To configure the BizTalk ISAPI extension DLL in IIS</span></span>  
  
1. <span data-ttu-id="6ccc4-182">按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-182">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2. <span data-ttu-id="6ccc4-183">依序展開 **\<電腦名稱\>（本機電腦)**，然後按一下 **網頁服務延伸** 。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-183">Expand **\<computer name\> (local computer)**, and then click **Web Service Extensions**.</span></span>  
  
3. <span data-ttu-id="6ccc4-184">在 [ **Web 服務延伸模組**] 窗格中，確認是否允許 HwsMessages HttpReceive 的狀態。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-184">In the **Web Service Extension** pane, verify that the status for HwsMessages HttpReceive is Allowed.</span></span> <span data-ttu-id="6ccc4-185">如果沒有，請以滑鼠右鍵按一下**HwsMessages HttpReceive**，然後按一下**允許**。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-185">If not, right-click **HwsMessages HttpReceive**, and then click **Allow**.</span></span>  
  
   <span data-ttu-id="6ccc4-186">如果 HwsMessages HttpReceive Web 服務延伸模組未設定 (未包含於 IIS 管理員的 Web 服務延伸模組清單中)，請執行下列程序。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-186">If the HwsMessages HttpReceive web service extension is not configured (it is not included in the Web Service Extensions list in IIS Manager), perform the following procedure.</span></span>  
  
##### <a name="to-configure-the-biztalk-isapi-extension-dll-in-iis"></a><span data-ttu-id="6ccc4-187">在 IIS 中設定 BizTalk ISAPI 擴充程式 DLL</span><span class="sxs-lookup"><span data-stu-id="6ccc4-187">To configure the BizTalk ISAPI extension DLL in IIS</span></span>  
  
1.  <span data-ttu-id="6ccc4-188">按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-188">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="6ccc4-189">依序展開**\<電腦名稱\>（本機電腦）**，以滑鼠右鍵按一下**網頁服務延伸**，然後按一下**新增新的 Web 服務延伸**.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-189">Expand **\<computer name\> (local computer)**, right-click **Web Service Extensions**, and then click **Add a new Web service extension**.</span></span>  
  
3.  <span data-ttu-id="6ccc4-190">中**新增網頁服務延伸**對話方塊中，於**延伸模組名稱**方塊中，輸入**BizTalk ISAPI 擴充程式**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-190">In the **New Web Service Extension** dialog box, in the **Extension Name** box, type **BizTalk ISAPI Extension**, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="6ccc4-191">在  **Add File**對話方塊的 **檔案路徑** 方塊中，輸入 **\<磁碟機\>: \Program Files\Microsoft BizTalk Server\<版本\>\HttpReceive\BTSHttpReceive.dll** ，然後按一下 **確定** 。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-191">In the **Add File** dialog box, in the **Path to file** box, type **\<drive\>:\Program Files\Microsoft BizTalk Server \<version\>\HttpReceive\BTSHttpReceive.dll**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="6ccc4-192">在 **新增網頁服務延伸**對話方塊中，選取**設定延伸狀態成允許**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-192">In the **New Web Service Extension** dialog box, select **Set extension status to Allowed**, and then click **OK**.</span></span>  
  
## <a name="an-access-violation-occurs-when-running-the-configuration-wizard"></a><span data-ttu-id="6ccc4-193">執行組態精靈時發生違規存取</span><span class="sxs-lookup"><span data-stu-id="6ccc4-193">An access violation occurs when running the Configuration Wizard</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-194">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-194">Symptom</span></span>  
 <span data-ttu-id="6ccc4-195">您在事件日誌中收到下列或類似的錯誤：</span><span class="sxs-lookup"><span data-stu-id="6ccc4-195">You receive the following or similar error in the event log:</span></span>  
  
 <span data-ttu-id="6ccc4-196">設定成使用者帳戶 \HostSvc 身分的 BizTalk 外掛式主控件執行個體並未執行，或不在這台電腦上。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-196">A BizTalk isolated host instance configured with the user account '\HostSvc' was either not running or does not exist on this computer.</span></span> <span data-ttu-id="6ccc4-197">請用 BizTalk 管理主控台建立一個新的外掛式主控件，或將已經設定好的外掛式主控件重新設定成以 \hostsvc 身分執行。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-197">Use the BizTalk Administration Console to create a new isolated host or reconfigure an existing to run as '\hostsvc'.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-198">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-198">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-199">若要執行 「 組態精靈 」，使用者應該設定為\<*電腦名稱*\>\hostsvc'，不是 '\hostsvc'。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-199">To run the Configuration Wizard, the user should be configured as '\<*machine name*\>\hostsvc', not '\hostsvc'.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-200">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-200">Solution</span></span>  
 <span data-ttu-id="6ccc4-201">開啟 BizTalk 管理主控台中，並變更 '\hostsvc'，在帳戶下執行的主機，使他們的帳戶下執行 '\<*電腦名稱*\>\hostsvc'。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-201">Open the BizTalk Administration Console, and change hosts that are running under the account '\hostsvc', so that they run under the account '\<*machine name*\>\hostsvc'.</span></span>  
  
## <a name="you-receive-an-error-when-importing-and-compiling-a-rosettanet-next-generation-pip-schema"></a><span data-ttu-id="6ccc4-202">匯入編譯 RosettaNet 下一代 PIP 結構描述時收到錯誤</span><span class="sxs-lookup"><span data-stu-id="6ccc4-202">You receive an error when importing and compiling a RosettaNet Next Generation PIP schema</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-203">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-203">Symptom</span></span>  
 <span data-ttu-id="6ccc4-204">您在事件日誌中收到下列或類似的錯誤：</span><span class="sxs-lookup"><span data-stu-id="6ccc4-204">You receive the following or similar error in the event log:</span></span>  
  
 <span data-ttu-id="6ccc4-205">錯誤 CS0234： 類型或命名空間名稱 'SerializableAttribute' 不存在於類別或命名空間 'RosettaNet.Schemas.System' （您是否遺漏了組件參考？）。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-205">error CS0234: The type or namespace name 'SerializableAttribute' does not exist in the class or namespace 'RosettaNet.Schemas.System' (are you missing an assembly reference?).</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-206">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-206">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-207">您的其中一個結構描述 (例如 StandardDocumentHeader.xsd) 擁有 RosettaNet.Schemas.System 的 [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] 命名空間。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-207">One of your schemas, for example, StandardDocumentHeader.xsd, has a [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] namespace of RosettaNet.Schemas.System.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-208">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-208">Solution</span></span>  
 <span data-ttu-id="6ccc4-209">將該結構描述 [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] 命名空間中的 System 移除，使該命名空間變成 RosettaNet.Schemas。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-209">Remove the "System" from the [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] namespace for the schema, so that the namespace is RosettaNet.Schemas.</span></span>  
  
## <a name="you-receive-an-error-when-trying-to-manually-deploy-the-bam-package"></a><span data-ttu-id="6ccc4-210">嘗試手動部署 BAM 封裝時收到錯誤</span><span class="sxs-lookup"><span data-stu-id="6ccc4-210">You receive an error when trying to manually deploy the BAM Package</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-211">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-211">Symptom</span></span>  
 <span data-ttu-id="6ccc4-212">當您嘗試手動部署 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] BAM 封裝時，收到您不能部署該封裝的錯誤。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-212">When you manually try to deploy the BAM package for [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], you receive an error indicating that you cannot deploy the package.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-213">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-213">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-214">您的系統上已安裝了 BAM_DM_Process 和 BAM_DM_Message 這兩個 DTS 封裝，導致您無法部署 BAM 封裝。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-214">The DTS packages BAM_DM_Process and BAM_DM_Message are installed on your system, preventing deployment of the BAM package.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-215">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-215">Solution</span></span>  
  
##### <a name="to-recover-from-the-error-condition-and-deploy-the-bam-package"></a><span data-ttu-id="6ccc4-216">修正此錯誤狀況並部署 BAM 封裝</span><span class="sxs-lookup"><span data-stu-id="6ccc4-216">To recover from the error condition and deploy the BAM package</span></span>  
  
1.  <span data-ttu-id="6ccc4-217">按一下 **開始**，指向**所有程式**，指向**Microsoft SQL Server**，然後按一下**Enterprise Manager**。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-217">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **Enterprise Manager**.</span></span>  
  
2.  <span data-ttu-id="6ccc4-218">在 Enterprise Manager 中，展開**Microsoft SQL Servers**， **SQL Server 群組**， **（本機） (Windows NT)**，和**Data Transformation Services**.</span><span class="sxs-lookup"><span data-stu-id="6ccc4-218">In Enterprise Manager, expand **Microsoft SQL Servers**, **SQL Server Group**, **(local) (Windows NT)**, and **Data Transformation Services**.</span></span>  
  
3.  <span data-ttu-id="6ccc4-219">按一下 **本機封裝**，以滑鼠右鍵按一下**bam_dm_message 這兩個**，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-219">Click **Local Packages**, right-click **BAM_DM_Message**, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="6ccc4-220">以滑鼠右鍵按一下**BAM_DM_Process**，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-220">Right-click **BAM_DM_Process**, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="6ccc4-221">按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-221">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="6ccc4-222">在命令提示字元中，輸入下列的程式碼來部署此追蹤檔案，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-222">At the command prompt, type the following code to deploy the tracking file, and then click **OK**.</span></span>  
  
    ```  
    cd %ProgramFiles%\Microsoft BizTalk Server <version>\Tracking  
    bm deploy all  "%ProgramFiles%\Microsoft BizTalk <version> Accelerator for RosettaNet\BAMTracking\tracking.xml"  
    ```  
  
## <a name="you-receive-an-error-when-adding-a-new-pip"></a><span data-ttu-id="6ccc4-223">新增 PIP 時收到錯誤</span><span class="sxs-lookup"><span data-stu-id="6ccc4-223">You receive an error when adding a new PIP</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-224">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-224">Symptom</span></span>  
 <span data-ttu-id="6ccc4-225">您在事件日誌中收到下列或類似的錯誤：</span><span class="sxs-lookup"><span data-stu-id="6ccc4-225">You receive the following or similar error in the event log:</span></span>  
  
 <span data-ttu-id="6ccc4-226">UNP.SCON.VALERR：驗證服務內容時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-226">UNP.SCON.VALERR: A failure occurred while validating the service content.</span></span>  
  
 <span data-ttu-id="6ccc4-227">詳細資料：依據訊息類型尋找文件規格失敗。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-227">Details: Finding document specification by message type failed.</span></span> <span data-ttu-id="6ccc4-228">請確認已正確部署結構描述。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-228">Verify that the schema is deployed properly.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-229">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-229">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-230">Pip4A5NotifyofForecastReply 執行個體已部署的結構描述中，文件命名空間或根節點屬性不正確。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-230">Either the document namespace or the root node property the deployed schema for the instance Pip4A5NotifyofForecastReply is incorrect.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-231">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-231">Solution</span></span>  
 <span data-ttu-id="6ccc4-232">請檢查 Pip4A5NotifyofForecastReply 執行個體已部署結構描述的文件命名空間與根節點屬性是否正確。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-232">Verify that the document namespace and the root node property for the deployed schema for instance Pip4A5NotifyofForecastReply is correct.</span></span>  
  
## <a name="error-during-the-configuration-of-btarn-at-installation-time-caused-by-presumed-network-connectivity-issues"></a><span data-ttu-id="6ccc4-233">安裝過程中設定 BTARN 組態時發生錯誤，系統推測原因可能是網路連線問題</span><span class="sxs-lookup"><span data-stu-id="6ccc4-233">Error during the configuration of BTARN at installation time, caused by presumed network connectivity issues</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-234">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-234">Symptom</span></span>  
 <span data-ttu-id="6ccc4-235">在設定組態的過程中收到錯誤對話方塊，指出電腦並未正確連上網路，但事實上電腦已正確連上網路了。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-235">During the configuration process, you receive an error in the error dialog box indicating that the computer is not properly connected to the network, when in fact it is.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-236">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-236">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-237">此錯誤可能是因為 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 組態程式錯誤解譯 IP 位址而造成的。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-237">This error may be caused by the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration program misinterpreting IP addresses.</span></span> <span data-ttu-id="6ccc4-238">C:\Windows\system32\drivers\etc 中的 Hosts 檔案內含有一個項目，會將 localhost 主機名稱對應成 IP 位址 127.0.0.1。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-238">The hosts file in C:\Windows\system32\drivers\etc contains an entry mapping the localhost host name to the IP address 127.0.0.1.</span></span> <span data-ttu-id="6ccc4-239">此組態程式可能把這個值和回送位址混淆了，所以才認為電腦並未正確連上網路。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-239">The configuration program may confuse this value with the loopback address, and assume that the computer is not connected properly to the network.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-240">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-240">Solution</span></span>  
  
##### <a name="to-avoid-this-error-and-complete-the-configuration-process"></a><span data-ttu-id="6ccc4-241">避免此種錯誤並完成組態程序</span><span class="sxs-lookup"><span data-stu-id="6ccc4-241">To avoid this error and complete the configuration process</span></span>  
  
1. <span data-ttu-id="6ccc4-242">在 [[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] 總管] 中，移到 C:\Windows\system32\drivers\etc，用「記事本」開啟 Hosts 檔案。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-242">In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to C:\Windows\system32\drivers\etc, and open the hosts file using Notepad.</span></span>  
  
2. <span data-ttu-id="6ccc4-243">行註解 「 127.0.0.1 localhost 」 藉由將"#"放在一行的開頭。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-243">Comment out the line "127.0.0.1        localhost" by placing "# " at the start of the line.</span></span> <span data-ttu-id="6ccc4-244">將變更後的 Hosts 檔案存檔。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-244">Save the changed hosts file.</span></span>  
  
3. <span data-ttu-id="6ccc4-245">按一下 **重試**錯誤 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-245">Click **Retry** in the error dialog box.</span></span>  
  
4. <span data-ttu-id="6ccc4-246">等組態設定成功完成後，再用「記事本」開啟 Hosts 檔案，把對應 localhost 那一行開頭的註解標記刪除，然後再將 Hosts 檔案存檔。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-246">After configuration has completed successfully, re-open the hosts file in Notepad, remove the comment mark at the start of the line mapping localhost, and then save the hosts file.</span></span>  
  
## <a name="you-receive-an-error-regarding-incorrect-signature-length"></a><span data-ttu-id="6ccc4-247">收到簽章長度不正確的錯誤</span><span class="sxs-lookup"><span data-stu-id="6ccc4-247">You receive an error regarding incorrect signature length</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-248">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-248">Symptom</span></span>  
 <span data-ttu-id="6ccc4-249">您在事件日誌中收到下列或類似的錯誤：</span><span class="sxs-lookup"><span data-stu-id="6ccc4-249">You receive the following or similar error in the event log:</span></span>  
  
 <span data-ttu-id="6ccc4-250">執行接收管線失敗: "Microsoft.Solutions.BTARN.Pipelines.Receive" 來源: "MIME/SMIME decoder" 接收位置: "/BTARNHttpReceive/BTSHTTPReceive.dll?xRNResponseType=async" 原因: 簽章長度不正確，值 = 1935897193。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-250">There was a failure executing the receive pipeline: "Microsoft.Solutions.BTARN.Pipelines.Receive" Source: "MIME/SMIME decoder" Receive Location: "/BTARNHttpReceive/BTSHTTPReceive.dll?xRNResponseType=async" Reason: Incorrect signature length, value = 1935897193.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-251">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-251">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-252">此錯誤訊息表示簽章的長度不正確。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-252">This error message indicates that the signature length is incorrect.</span></span> <span data-ttu-id="6ccc4-253">除了以上的原因之外，標頭內容長度不正確或不完整，導致讀取的簽章長度位元組數不正確，也可能是造成此錯誤的原因。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-253">In addition to the above cause, this error could also due to the incorrect or incomplete header content length which leads to the wrong bytes read on the signature length.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-254">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-254">Solution</span></span>  
 <span data-ttu-id="6ccc4-255">檢查簽章長度與標頭內容長度是否正確。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-255">Verify that both of the signature length and header content length is correct.</span></span>  
  
## <a name="you-receive-503-service-unavailable-from-internet-explorer-on-64-bit-machine"></a><span data-ttu-id="6ccc4-256">您會從 64 位元電腦上的 Internet Explorer 收到「503：服務無法使用」</span><span class="sxs-lookup"><span data-stu-id="6ccc4-256">You receive "503: Service Unavailable" from Internet Explorer on 64-bit machine</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-257">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-257">Symptom</span></span>  
 <span data-ttu-id="6ccc4-258">在後[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]完成組態設定，當您嘗試存取[ http://localhost ](http://localhost/)或是[ http://localhost/BtarnApp/RnifSend.aspx ](http://localhost/BtarnApp/RnifSend.aspx)，可能會收到下列或類似的錯誤：</span><span class="sxs-lookup"><span data-stu-id="6ccc4-258">After [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] configuration is completed, when you try to access [http://localhost](http://localhost/) or [http://localhost/BtarnApp/RnifSend.aspx](http://localhost/BtarnApp/RnifSend.aspx), you may receive the following or similar error:</span></span>  
  
 <span data-ttu-id="6ccc4-259">503：服務無法使用</span><span class="sxs-lookup"><span data-stu-id="6ccc4-259">503: Service Unavailable</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-260">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-260">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-261">此錯誤可能是由於 IIS 網站設定 C:\windows\system32\rpcproxy\rpcproxy.dll 底下的 ISAPI 篩選常式所造成的。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-261">This error may be caused by the ISAPI filter found under C:\windows\system32\rpcproxy\rpcproxy.dll being set on IIS Web Sites.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-262">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-262">Solution</span></span>  
  
##### <a name="to-remove-rpcproxy-filter-entry-in-iis"></a><span data-ttu-id="6ccc4-263">移除 IIS 中的 RpcProxy 篩選常式項目</span><span class="sxs-lookup"><span data-stu-id="6ccc4-263">To remove RpcProxy filter entry in IIS</span></span>  
  
1.  <span data-ttu-id="6ccc4-264">按一下 **開始**，指向 **系統管理工具**，然後按一下 **Internet Information Services (IIS) 管理員**。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-264">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="6ccc4-265">依序展開**\<電腦名稱\>（本機電腦）**，以滑鼠右鍵按一下**網站**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-265">Expand **\<computer name\> (local computer)**, right-click **Web Sites**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="6ccc4-266">選取 [ **ISAPI 篩選器**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-266">Select **ISAPI Filters** tab.</span></span>  
  
4.  <span data-ttu-id="6ccc4-267">選取 [ **RpcProxy 篩選常式]**，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-267">Select **RpcProxy filter**, and click **Remove**.</span></span>  
  
5.  <span data-ttu-id="6ccc4-268">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-268">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="6ccc4-269">按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-269">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="6ccc4-270">在命令提示字元下，輸入下列程式碼以重設 IIS。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-270">At the command prompt, type the following code to reset IIS.</span></span>  
  
    ```  
    iisreset  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="6ccc4-271">如果您嘗試存取 http://localhost 或 http://localhost/BtarnApp/RnifSend.aspx 再次執行上述步驟之後，您會收到 HTTP 400 訊息從 Internet Explorer，這表示，IIS 已經正常運作。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-271">If you try to access http://localhost or http://localhost/BtarnApp/RnifSend.aspx again after performing the above steps, you will receive HTTP 400 message back from the Internet Explorer which means that IIS is now functioning properly.</span></span>  
  
## <a name="the-hubscenario-sample-will-not-be-installed-correctly-if-the-assembly-key-files-are-not-entered-for-the-projects"></a><span data-ttu-id="6ccc4-272">如果沒有輸入專案的組件金鑰檔，HubScenario 範例就不會正確安裝</span><span class="sxs-lookup"><span data-stu-id="6ccc4-272">The HubScenario sample will not be installed correctly if the assembly key files are not entered for the projects</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-273">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-273">Symptom</span></span>  
 <span data-ttu-id="6ccc4-274">當您執行 setup.bat *\<磁碟機\>*: \Program Files\\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\HubScenario 設定HubScenario 範例中，作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-274">When you run setup.bat in *\<drive\>*:\Program Files\\Microsoft  BizTalk \<version\> Accelerator for RosettaNet\SDK\HubScenario to set up the HubScenario sample, the operation fails.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-275">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-275">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-276">HubScenario 和 HubHelper 組件未正確部署，因為未在專案中設定組件金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-276">The HubScenario and HubHelper assemblies were not deployed correctly because the assembly key files were not set in the projects.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-277">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-277">Solution</span></span>  
 <span data-ttu-id="6ccc4-278">對 HubScenario 和 HubHelper 專案設定組件金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-278">Set the assembly key files for the HubScenario and HubHelper projects.</span></span> <span data-ttu-id="6ccc4-279">如需詳細資訊，請參閱 < [HubScenario 範例](../../adapters-and-accelerators/accelerator-rosettanet/hubscenario-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-279">For more information, see [HubScenario Sample](../../adapters-and-accelerators/accelerator-rosettanet/hubscenario-sample.md).</span></span>  
  
## <a name="run-setupx64bat-to-set-up-the-double-action-pipautomation-orchestration-sample-on-sql-server-2008-r22008-sp1"></a><span data-ttu-id="6ccc4-280">執行 setupx64.bat，以設定 SQL Server 2008 R2/2008 SP1 中的雙向動作 PIPAutomation 協調流程範例</span><span class="sxs-lookup"><span data-stu-id="6ccc4-280">Run setupx64.bat to set up the Double Action PIPAutomation Orchestration sample on SQL Server 2008 R2/2008 SP1</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6ccc4-281">徵兆</span><span class="sxs-lookup"><span data-stu-id="6ccc4-281">Symptom</span></span>  
 <span data-ttu-id="6ccc4-282">執行 setup.bat 以建置和初始化設定「雙向動作 PIPAutomation 協調流程」範例時，BTARNData 資料庫中的 PipAutomationGetAction 預存程序未建立。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-282">When you run setup.bat to build and initialize the Double Action PIPAutomation Orchestration sample, the PipAutomationGetAction stored procedure in the BTARNData database is not created.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="6ccc4-283">可能的原因</span><span class="sxs-lookup"><span data-stu-id="6ccc4-283">Possible Cause</span></span>  
 <span data-ttu-id="6ccc4-284">在 64 位元電腦上或在 SQL Server 2008 R2/2008 SP1 執行的 BizTalk Server 安裝上，執行 setup.bat。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-284">You ran setup.bat on a 64-bit computer or on a BizTalk Server installation that is running on SQL Server 2008 R2/2008 SP1.</span></span> <span data-ttu-id="6ccc4-285">這兩個執行個體都需要您執行 setupx64.bat。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-285">Both of these instances require you to run setupx64.bat.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="6ccc4-286">方案</span><span class="sxs-lookup"><span data-stu-id="6ccc4-286">Solution</span></span>  
 <span data-ttu-id="6ccc4-287">請執行 setupx64.bat 以建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-287">Run setupx64.bat to create the stored procedure.</span></span> <span data-ttu-id="6ccc4-288">如需詳細資訊，請參閱 <<c0> [ 雙向動作 PIPAutomation 協調流程](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-288">For more information, see [Double Action PIPAutomation Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md).</span></span>  
  
## <a name="enable-the-btarn-application-pools-for-32-bit-on-windows-server-2008-64-bit-windows-operating-system-os"></a><span data-ttu-id="6ccc4-289">啟用 Windows Server 2008 64 位元 Windows 作業系統 (OS) 上的 32 位元的 BTARN 應用程式集區</span><span class="sxs-lookup"><span data-stu-id="6ccc4-289">Enable the BTARN Application Pools for 32 bit on Windows Server 2008, 64-bit Windows Operating System (OS)</span></span>  
 <span data-ttu-id="6ccc4-290">在 Windows Server 2008、64 位元的 Windows 作業系統 (OS)、Internet Information Services Manager 7.5/7.0 上執行 BTARN 端對端實例。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-290">To run the BTARN End to End scenario on Windows Server 2008,64-bit Windows Operating System (OS), Internet Information Services Manager 7.5/7.0.</span></span>  
  
 1. <span data-ttu-id="6ccc4-291">啟用 32 位元的 BTARN 應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-291">Enable the BTARN Application Pools for 32 bit.</span></span>  
  
 2. <span data-ttu-id="6ccc4-292">新增的 HTTP 處理常式\*.dll 參考 IsapiModule 篩選器。</span><span class="sxs-lookup"><span data-stu-id="6ccc4-292">Add a HTTP Handler for \*.dll referring the IsapiModule Filters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ccc4-293">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ccc4-293">See Also</span></span>  
 <span data-ttu-id="6ccc4-294">[BtarnClean](../../adapters-and-accelerators/accelerator-rosettanet/btarnclean.md) </span><span class="sxs-lookup"><span data-stu-id="6ccc4-294">[BtarnClean](../../adapters-and-accelerators/accelerator-rosettanet/btarnclean.md) </span></span>  
 [<span data-ttu-id="6ccc4-295">回送</span><span class="sxs-lookup"><span data-stu-id="6ccc4-295">Loopback</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/loopback.md)
