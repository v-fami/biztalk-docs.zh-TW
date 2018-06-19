---
title: 已知 Issues5 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting, known issues
- BizTalk Accelerator for SWIFT, known issues
- known issues
ms.assetid: 0f1ec7dd-9e74-479a-bdc8-ab9c4397c992
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1356209f700fc7ceff220f4b0f8fcd3dd67db07
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006711"
---
# <a name="known-issues"></a><span data-ttu-id="355d0-102">已知問題</span><span class="sxs-lookup"><span data-stu-id="355d0-102">Known Issues</span></span>
<span data-ttu-id="355d0-103">此章節包含有用的資訊可協助您避免錯誤[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="355d0-103">This section contains useful information that may help you avoid errors with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="355d0-104">已知的問題可分為以下各類：</span><span class="sxs-lookup"><span data-stu-id="355d0-104">The known issues are grouped into the following areas:</span></span>  
  
## <a name="message-repair-and-new-submission"></a><span data-ttu-id="355d0-105">Message Repair 和 New Submission</span><span class="sxs-lookup"><span data-stu-id="355d0-105">Message Repair and New Submission</span></span>

#### <a name="printing-of-a-repair-document-is-recorded-in-the-history-log-even-if-canceled"></a><span data-ttu-id="355d0-106">即使取消，將會記錄在歷程記錄的列印修復文件</span><span class="sxs-lookup"><span data-stu-id="355d0-106">Printing of a repair document is recorded in the history log even if canceled</span></span>  
 <span data-ttu-id="355d0-107">如果您執行修復收件匣中的文件的 [列印] 命令，然後取消列印列印仍然會輸入到歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="355d0-107">If you run the Print command for a document in the Repair Inbox, and then cancel the printing, the printing is still entered into the history log.</span></span> <span data-ttu-id="355d0-108">當您開啟的文件中修復時，發生這種的情況其[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成，按一下 [檔案] 功能表上的 [列印] 命令，然後按一下 [列印] 對話方塊中的 [取消]。</span><span class="sxs-lookup"><span data-stu-id="355d0-108">This occurs when you open the document to be repaired in its [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, click the Print command on the File menu, and then click Cancel in the Print dialog box.</span></span> <span data-ttu-id="355d0-109">您應該忽略歷程記錄中的項目。</span><span class="sxs-lookup"><span data-stu-id="355d0-109">You should ignore the entry in the history log.</span></span>  
  
#### <a name="a-duplicate-signature-can-cause-an-xlangs-error-message"></a><span data-ttu-id="355d0-110">重複的簽章可能會導致 XLANG/s 錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="355d0-110">A duplicate signature can cause an XLANG/s error message</span></span>  
 <span data-ttu-id="355d0-111">當驗證器會使用相同的憑證為 repairer，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]擱置訊息，並指出錯誤訊息中不允許重複的簽章。</span><span class="sxs-lookup"><span data-stu-id="355d0-111">When a verifier uses the same certificate as a repairer, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] suspends the message and indicates in an error message that duplicate signatures are not allowed.</span></span> <span data-ttu-id="355d0-112">不過，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]也會產生 XLANG/s，指出已暫止的 XLANG/s 服務的事件來源的其他錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="355d0-112">However, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] also generates another error message with an event source of XLANG/s, indicating that the XLANG/s service has been suspended.</span></span> <span data-ttu-id="355d0-113">您可以忽略此訊息。</span><span class="sxs-lookup"><span data-stu-id="355d0-113">You can ignore this message.</span></span>  
  
#### <a name="message-size-can-affect-repair-performance"></a><span data-ttu-id="355d0-114">訊息大小可能會影響修復效能</span><span class="sxs-lookup"><span data-stu-id="355d0-114">Message size can affect repair performance</span></span>  
 <span data-ttu-id="355d0-115">當您開啟中的 XML 檔案時，如果您嘗試修復非常大的 XML 檔案，可能會大幅降低系統效能[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]訊息類型的表單。</span><span class="sxs-lookup"><span data-stu-id="355d0-115">If you attempt to repair an unusually large XML file, system performance can significantly degrade when you open the XML file in the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form for the message type.</span></span> <span data-ttu-id="355d0-116">可能會增加記憶體耗用量，可能會降低 CPU 耗用率，和處理程序可能會失敗並出現錯誤訊息指出沒有足夠的儲存體無法完成作業。</span><span class="sxs-lookup"><span data-stu-id="355d0-116">Memory consumption may increase, CPU consumption may decrease, and the process may fail with an error indicating that not enough storage was available to complete the operation.</span></span>  
  
#### <a name="the-last-signature-used-to-sign-a-message-successfully-will-be-authenticated-by-authenticate-signatures"></a><span data-ttu-id="355d0-117">最後一個用來順利簽署訊息簽章會經過驗證的簽章</span><span class="sxs-lookup"><span data-stu-id="355d0-117">The last signature used to sign a message successfully will be authenticated by Authenticate Signatures</span></span>  
 <span data-ttu-id="355d0-118">按一下 [驗證簽章] 按鈕[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單驗證簽章，您僅用於的使用者如果您已經簽署表單的階段。</span><span class="sxs-lookup"><span data-stu-id="355d0-118">Clicking the Authenticate Signatures button on an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form validates the signature for the stage that you are in only if you have already signed the form.</span></span> <span data-ttu-id="355d0-119">否則，它會驗證簽章上一個階段中，如果有的話，並將張貼下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="355d0-119">Otherwise, it validates the signature for the previous stage, if there was one, and posts the following error:</span></span>  
  
 <span data-ttu-id="355d0-120">簽章的使用者未正確設定為部門 < department_name > 中 < stage_name > 角色。</span><span class="sxs-lookup"><span data-stu-id="355d0-120">The signing user is not correctly configured for the <stage_name> role in department <department_name>.</span></span>  
  
 <span data-ttu-id="355d0-121">例如，假設您在驗證階段之後立即處於核准階段。</span><span class="sxs-lookup"><span data-stu-id="355d0-121">For example, suppose that you are in an approve stage immediately after a verify stage.</span></span> <span data-ttu-id="355d0-122">如果尚未簽署核准者] 的形式，，按一下 [驗證簽章[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]驗證的簽章驗證器工具使用，不核准者的簽章，並將張貼先前的錯誤。</span><span class="sxs-lookup"><span data-stu-id="355d0-122">If you have not yet signed the form as the approver, and you click Authenticate Signatures, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] authenticates the signature that the verifier used, not your approver's signature, and posts the preceding error.</span></span>  

#### <a name="a4swift-cleanup-tool-doesnt-delete-templates"></a><span data-ttu-id="355d0-123">A4SWIFT 清理工具並不會刪除範本</span><span class="sxs-lookup"><span data-stu-id="355d0-123">A4SWIFT cleanup tool doesn’t delete templates</span></span>  
 <span data-ttu-id="355d0-124">A4SWIFT 清理工具不會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="355d0-124">The A4SWIFT cleanup tool doesn’t performs the following operations:</span></span>  
  
-   <span data-ttu-id="355d0-125">從 MRSR 網站移除所有 MT 範本</span><span class="sxs-lookup"><span data-stu-id="355d0-125">Removes all MT templates from MRSR site</span></span>  
  
-   <span data-ttu-id="355d0-126">從 MRSR 網站移除所有合約和夥伴設定檔</span><span class="sxs-lookup"><span data-stu-id="355d0-126">Removes all agreements and partner profiles from MRSR site</span></span>  
  
-   <span data-ttu-id="355d0-127">移除所有的使用者、 角色和部門</span><span class="sxs-lookup"><span data-stu-id="355d0-127">Removes all users, roles, and departments</span></span>  
  
-   <span data-ttu-id="355d0-128">取消註冊 MRSR 網站的 A4SWIFT BizTalk 伺服器</span><span class="sxs-lookup"><span data-stu-id="355d0-128">Unregisters the A4SWIFT BizTalk Server from the MRSR site</span></span>  
  
#### <a name="the-a4swiftmrsrdepartment-property-is-set-to-an-empty-string-for-a-message-that-did-not-parse"></a><span data-ttu-id="355d0-129">A4SWIFT_MRSRDepartment 屬性設為空字串未剖析的訊息。</span><span class="sxs-lookup"><span data-stu-id="355d0-129">The A4SWIFT_MRSRDepartment property is set to an empty string for a message that did not parse</span></span>  
 <span data-ttu-id="355d0-130">當訊息修復協調流程可將已修正未剖析的訊息路由至 MessageBox 時，它也會設定[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_MRSRDepartment 屬性為空字串，並將它升級。</span><span class="sxs-lookup"><span data-stu-id="355d0-130">When the message-repair orchestration routes to the MessageBox an unparsed message that has been fixed, it will set the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_MRSRDepartment property to an empty string and promote it.</span></span> <span data-ttu-id="355d0-131">傳送埠不能在這個屬性的訂閱。</span><span class="sxs-lookup"><span data-stu-id="355d0-131">A send port will not be able to subscribe on this property.</span></span>  
  
#### <a name="cannot-save-a-department-if-the-sso-service-has-been-stopped"></a><span data-ttu-id="355d0-132">無法儲存一個部門，如果 SSO 服務已停止</span><span class="sxs-lookup"><span data-stu-id="355d0-132">Cannot save a department if the SSO service has been stopped</span></span>  
 <span data-ttu-id="355d0-133">如果您嘗試新增一個部門，SSO 服務停止時，您會收到錯誤指出此問題的主要 SSO 伺服器\<machinename\>失敗。</span><span class="sxs-lookup"><span data-stu-id="355d0-133">If you try to add a department when the SSO service is stopped, you will receive an error indicating that the Primary SSO server \<machinename\> failed.</span></span> <span data-ttu-id="355d0-134">請檢查是否已設定 SSO，以及 SSO 服務是否在該伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="355d0-134">Check that SSO is configured and that the SSO service is running on that server.</span></span>  
  
#### <a name="a-department-name-must-not-contain-the-character-"></a><span data-ttu-id="355d0-135">部門的名稱不可以包含字元"~"</span><span class="sxs-lookup"><span data-stu-id="355d0-135">A department name must not contain the character "~"</span></span>  
 <span data-ttu-id="355d0-136">部門的名稱包含字元"~"A4SWIFT 資料庫將會導致的問題。</span><span class="sxs-lookup"><span data-stu-id="355d0-136">A department name that contains the character "~" will cause issues with the A4SWIFT database.</span></span>  
  
#### <a name="signing-infopath-forms"></a><span data-ttu-id="355d0-137">簽署 Infopath 表單</span><span class="sxs-lookup"><span data-stu-id="355d0-137">Signing Infopath forms</span></span>  
 <span data-ttu-id="355d0-138">InfoPath 表單的簽章必須手動完成。</span><span class="sxs-lookup"><span data-stu-id="355d0-138">The signing of InfoPath forms needs to be done manually.</span></span>  
  
## <a name="security"></a><span data-ttu-id="355d0-139">安全性</span><span class="sxs-lookup"><span data-stu-id="355d0-139">Security</span></span>

#### <a name="mixing-trusted-and-untrusted-hosts-can-enable-spoofing"></a><span data-ttu-id="355d0-140">混用受信任和未受信任的主控件可以啟用詐騙</span><span class="sxs-lookup"><span data-stu-id="355d0-140">Mixing trusted and untrusted hosts can enable spoofing</span></span>  

 <span data-ttu-id="355d0-141">它可能詐騙從其他未受信任的 SWIFT 繫結訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="355d0-141">It may be possible to spoof SWIFT-bound messages from other non-trusted [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] host applications.</span></span> <span data-ttu-id="355d0-142">這是只有問題，在混合的信任模式下執行時 (信任的主控件和未受信任的主機中執行時的應用程式相同[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]群組)。</span><span class="sxs-lookup"><span data-stu-id="355d0-142">This is only a problem when running in mixed-trust mode (when trusted hosts and untrusted hosts run applications in the same [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] group).</span></span> <span data-ttu-id="355d0-143">您可以使用來識別 SWIFT 繫結訊息的來源合作對象解析管線元件來減輕此風險。</span><span class="sxs-lookup"><span data-stu-id="355d0-143">You can mitigate this risk by using party-resolution pipeline components to identify the source of the SWIFT-bound message.</span></span> <span data-ttu-id="355d0-144">這不需要完全信任的環境中或針對大部分的使用方式案例執行時。</span><span class="sxs-lookup"><span data-stu-id="355d0-144">This is not necessary when running in a fully trusted environment or for the majority of usage scenarios.</span></span> <span data-ttu-id="355d0-145">您應該遵循[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]混合時，建立安全應用程式的指導方針信任和未受信任的主機。</span><span class="sxs-lookup"><span data-stu-id="355d0-145">You should follow the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] guidelines for building secure applications when mixing trusted and untrusted hosts.</span></span> 
 
## <a name="miscellaneous"></a><span data-ttu-id="355d0-146">其他</span><span class="sxs-lookup"><span data-stu-id="355d0-146">Miscellaneous</span></span>

#### <a name="the-cacheentries-setting-may-be-reset-by-a-setup-program-affecting-performance"></a><span data-ttu-id="355d0-147">CacheEntries 設定可能會重設安裝程式會影響效能</span><span class="sxs-lookup"><span data-stu-id="355d0-147">The CacheEntries setting may be reset by a Setup program, affecting performance</span></span>  
 <span data-ttu-id="355d0-148">CacheEntries 登錄機碼決定 ruleset 「 商務規則引擎更新服務快取的最大數目。</span><span class="sxs-lookup"><span data-stu-id="355d0-148">The CacheEntries registry key determines the maximum number of rulesets cached by the Business Rule Engine Update service.</span></span> <span data-ttu-id="355d0-149">[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝程式預設會 CacheEntries 設定為 32。</span><span class="sxs-lookup"><span data-stu-id="355d0-149">The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Setup program sets CacheEntries to 32 by default.</span></span> <span data-ttu-id="355d0-150">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式變更 HKEY_LOCAL_MACHINE\SOFTWARE\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]\BusinessRules\3.0\CacheEntries 為 512，為了取得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="355d0-150">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Setup program changes HKEY_LOCAL_MACHINE\SOFTWARE\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]\BusinessRules\3.0\CacheEntries to 512 for optimum performance.</span></span> <span data-ttu-id="355d0-151">不過，在某些情況下，CacheEntries 可能會自動重設。</span><span class="sxs-lookup"><span data-stu-id="355d0-151">However, in certain circumstances, CacheEntries may be reset automatically.</span></span> <span data-ttu-id="355d0-152">這可能會影響系統效能。</span><span class="sxs-lookup"><span data-stu-id="355d0-152">This may affect system performance.</span></span>  
  
 <span data-ttu-id="355d0-153">規則引擎更新可能會變更 CacheEntries 介於 512 到 32。</span><span class="sxs-lookup"><span data-stu-id="355d0-153">Rule Engine updates may change CacheEntries from 512 to 32.</span></span> <span data-ttu-id="355d0-154">安裝規則引擎更新之後，手動重設 CacheEntries 為 512，如有必要。</span><span class="sxs-lookup"><span data-stu-id="355d0-154">After installing a Rule Engine update, manually reset CacheEntries to 512, if necessary.</span></span>  
  
 <span data-ttu-id="355d0-155">即使[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式設定 CacheEntries 32 到 512，解除安裝[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]不重設 CacheEntries 介於 512 到 32。</span><span class="sxs-lookup"><span data-stu-id="355d0-155">Even though the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Setup program sets CacheEntries from 32 to 512, uninstalling [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] does not reset CacheEntries from 512 to 32.</span></span>  
  
 <span data-ttu-id="355d0-156">如需詳細資訊，請參閱在 BizTalk Server 說明中的 「 規則引擎組態和調整參數 > 主題。</span><span class="sxs-lookup"><span data-stu-id="355d0-156">For more information, see the "Rule Engine Configuration and Tuning Parameters" topic in BizTalk Server Help.</span></span>  
  
#### <a name="building-a-pipeline-project-may-result-in-a-large-number-of-warnings"></a><span data-ttu-id="355d0-157">建立管線專案可能會導致大量的警告</span><span class="sxs-lookup"><span data-stu-id="355d0-157">Building a pipeline project may result in a large number of warnings</span></span>  
 <span data-ttu-id="355d0-158">當您將 SWIFT 組譯工具加入至傳送管線或 SWIFT 接收管線解譯器，然後建立包含這些管線的管線專案時，您可能會收到一系列的管線元件相關的警告。</span><span class="sxs-lookup"><span data-stu-id="355d0-158">When you add the SWIFT assembler to a send pipeline, or the SWIFT disassembler to a receive pipeline, and then build the pipeline project containing those pipelines, you may receive a series of warnings related to the pipeline components.</span></span> <span data-ttu-id="355d0-159">這些警告會指示 Visual Studio 找不到相依性。</span><span class="sxs-lookup"><span data-stu-id="355d0-159">These warnings indicate that Visual Studio could not find dependencies.</span></span> <span data-ttu-id="355d0-160">您可以更正導致這些警告，如下所示變更 SWIFTAsm 或 SWIFTDasm 中組件的 [參考] 資料夾中，[複製本機] 屬性的條件：</span><span class="sxs-lookup"><span data-stu-id="355d0-160">You can correct the condition leading to these warnings by changing the Copy Local property of the SWIFTAsm or SWIFTDasm assembly in the reference folder, as follows:</span></span>  
  
1.  <span data-ttu-id="355d0-161">在 方案總管的 Visual Studio 中，展開您管線專案，然後再展開**參考**節點。</span><span class="sxs-lookup"><span data-stu-id="355d0-161">In Solution Explorer of Visual Studio, expand your pipeline project, and then expand the **References** node.</span></span>  
  
2.  <span data-ttu-id="355d0-162">在 [參考] 節點下選取**SWIFTAsm**組件及/或**SWIFTDasm**組件。</span><span class="sxs-lookup"><span data-stu-id="355d0-162">Under the References node, select the **SWIFTAsm** assembly and/or the **SWIFTDasm** assembly.</span></span>  
  
3.  <span data-ttu-id="355d0-163">在 [屬性] 窗格中，將變更的值**複製到本機**屬性**False**。</span><span class="sxs-lookup"><span data-stu-id="355d0-163">In the Properties pane, change the value for the **Copy Local** property to **False**.</span></span>  
  
4.  <span data-ttu-id="355d0-164">以滑鼠右鍵按一下管線專案，然後按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="355d0-164">Right-click your pipeline project, and then click **Build**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="355d0-165">您應該不會看到找不到相依性的任何警告。</span><span class="sxs-lookup"><span data-stu-id="355d0-165">You should not see any warnings about dependencies not being found.</span></span>   