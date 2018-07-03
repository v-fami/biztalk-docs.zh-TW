---
title: 已知 Issues5 |Microsoft Docs
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
ms.openlocfilehash: f7c164e8c0d6713389fd317c8839d72770f07c56
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000551"
---
# <a name="known-issues"></a><span data-ttu-id="891d1-102">已知問題</span><span class="sxs-lookup"><span data-stu-id="891d1-102">Known Issues</span></span>
<span data-ttu-id="891d1-103">本節包含可協助您避免與 Microsoft 的錯誤的有用資訊[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="891d1-103">This section contains useful information that may help you avoid errors with Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="891d1-104">已知的問題可分為以下各類：</span><span class="sxs-lookup"><span data-stu-id="891d1-104">The known issues are grouped into the following areas:</span></span>  
  
## <a name="message-repair-and-new-submission"></a><span data-ttu-id="891d1-105">Message Repair 和 New Submission</span><span class="sxs-lookup"><span data-stu-id="891d1-105">Message Repair and New Submission</span></span>

#### <a name="printing-of-a-repair-document-is-recorded-in-the-history-log-even-if-canceled"></a><span data-ttu-id="891d1-106">即使已取消，將會記錄在歷程記錄的列印修復文件</span><span class="sxs-lookup"><span data-stu-id="891d1-106">Printing of a repair document is recorded in the history log even if canceled</span></span>  
 <span data-ttu-id="891d1-107">如果您執行修復收件匣中的文件的 [列印] 命令，然後取消列印，列印仍然已輸入的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="891d1-107">If you run the Print command for a document in the Repair Inbox, and then cancel the printing, the printing is still entered into the history log.</span></span> <span data-ttu-id="891d1-108">當您開啟的文件中修復時，發生這種的情況其[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單，按一下 [檔案] 功能表上的 [列印] 命令，然後按一下 [列印] 對話方塊中的 [取消]。</span><span class="sxs-lookup"><span data-stu-id="891d1-108">This occurs when you open the document to be repaired in its [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, click the Print command on the File menu, and then click Cancel in the Print dialog box.</span></span> <span data-ttu-id="891d1-109">您應該忽略的歷程記錄中的項目。</span><span class="sxs-lookup"><span data-stu-id="891d1-109">You should ignore the entry in the history log.</span></span>  
  
#### <a name="a-duplicate-signature-can-cause-an-xlangs-error-message"></a><span data-ttu-id="891d1-110">重複的簽章可能會導致 XLANG/s 錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="891d1-110">A duplicate signature can cause an XLANG/s error message</span></span>  
 <span data-ttu-id="891d1-111">當驗證器會使用相同的憑證作為 repairer，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]擱置訊息，並指出錯誤訊息中不允許重複的簽章。</span><span class="sxs-lookup"><span data-stu-id="891d1-111">When a verifier uses the same certificate as a repairer, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] suspends the message and indicates in an error message that duplicate signatures are not allowed.</span></span> <span data-ttu-id="891d1-112">不過，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]也會產生 XLANG/s，指出已暫止的 XLANG/s 服務的事件來源的另一個錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="891d1-112">However, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] also generates another error message with an event source of XLANG/s, indicating that the XLANG/s service has been suspended.</span></span> <span data-ttu-id="891d1-113">您可以忽略此訊息。</span><span class="sxs-lookup"><span data-stu-id="891d1-113">You can ignore this message.</span></span>  
  
#### <a name="message-size-can-affect-repair-performance"></a><span data-ttu-id="891d1-114">訊息大小可能會影響修復效能</span><span class="sxs-lookup"><span data-stu-id="891d1-114">Message size can affect repair performance</span></span>  
 <span data-ttu-id="891d1-115">當您開啟中的 XML 檔案時，如果您嘗試修復異常大的 XML 檔案，可以大幅降低系統效能[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]訊息類型的表單。</span><span class="sxs-lookup"><span data-stu-id="891d1-115">If you attempt to repair an unusually large XML file, system performance can significantly degrade when you open the XML file in the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form for the message type.</span></span> <span data-ttu-id="891d1-116">可能會增加記憶體耗用量、 CPU 耗用量可能會降低，和處理程序可能會失敗並出現錯誤指出沒有足夠的儲存體無法完成作業。</span><span class="sxs-lookup"><span data-stu-id="891d1-116">Memory consumption may increase, CPU consumption may decrease, and the process may fail with an error indicating that not enough storage was available to complete the operation.</span></span>  
  
#### <a name="the-last-signature-used-to-sign-a-message-successfully-will-be-authenticated-by-authenticate-signatures"></a><span data-ttu-id="891d1-117">最後一個用來成功地簽署訊息的簽章會經過驗證的簽章</span><span class="sxs-lookup"><span data-stu-id="891d1-117">The last signature used to sign a message successfully will be authenticated by Authenticate Signatures</span></span>  
 <span data-ttu-id="891d1-118">按一下 驗證簽章按鈕[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單驗證簽章，您僅如果您已經簽署表單的階段。</span><span class="sxs-lookup"><span data-stu-id="891d1-118">Clicking the Authenticate Signatures button on an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form validates the signature for the stage that you are in only if you have already signed the form.</span></span> <span data-ttu-id="891d1-119">否則，它會驗證簽章上一個階段中，如果有的話，並將張貼下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="891d1-119">Otherwise, it validates the signature for the previous stage, if there was one, and posts the following error:</span></span>  
  
 <span data-ttu-id="891d1-120">簽章的使用者未正確設定部門 < department_name > 中 < stage_name > 角色。</span><span class="sxs-lookup"><span data-stu-id="891d1-120">The signing user is not correctly configured for the <stage_name> role in department <department_name>.</span></span>  
  
 <span data-ttu-id="891d1-121">例如，假設您在驗證階段之後立即處於 「 核准 」 階段。</span><span class="sxs-lookup"><span data-stu-id="891d1-121">For example, suppose that you are in an approve stage immediately after a verify stage.</span></span> <span data-ttu-id="891d1-122">如果尚未簽署形式的核准者，並按一下驗證簽章[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]驗證的簽章驗證器使用，不核准者的簽章，並將張貼先前的錯誤。</span><span class="sxs-lookup"><span data-stu-id="891d1-122">If you have not yet signed the form as the approver, and you click Authenticate Signatures, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] authenticates the signature that the verifier used, not your approver's signature, and posts the preceding error.</span></span>  

#### <a name="a4swift-cleanup-tool-doesnt-delete-templates"></a><span data-ttu-id="891d1-123">A4SWIFT 清理工具並不會刪除範本</span><span class="sxs-lookup"><span data-stu-id="891d1-123">A4SWIFT cleanup tool doesn’t delete templates</span></span>  
 <span data-ttu-id="891d1-124">A4SWIFT 清理工具不會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="891d1-124">The A4SWIFT cleanup tool doesn’t performs the following operations:</span></span>  
  
-   <span data-ttu-id="891d1-125">移除 MRSR 站台的主要目標的所有範本</span><span class="sxs-lookup"><span data-stu-id="891d1-125">Removes all MT templates from MRSR site</span></span>  
  
-   <span data-ttu-id="891d1-126">移除 MRSR 網站中的所有合約和夥伴設定檔</span><span class="sxs-lookup"><span data-stu-id="891d1-126">Removes all agreements and partner profiles from MRSR site</span></span>  
  
-   <span data-ttu-id="891d1-127">移除所有的使用者、 角色和部門</span><span class="sxs-lookup"><span data-stu-id="891d1-127">Removes all users, roles, and departments</span></span>  
  
-   <span data-ttu-id="891d1-128">取消註冊 MRSR 網站 A4SWIFT BizTalk 伺服器</span><span class="sxs-lookup"><span data-stu-id="891d1-128">Unregisters the A4SWIFT BizTalk Server from the MRSR site</span></span>  
  
#### <a name="the-a4swiftmrsrdepartment-property-is-set-to-an-empty-string-for-a-message-that-did-not-parse"></a><span data-ttu-id="891d1-129">A4SWIFT_MRSRDepartment 屬性設為空字串未剖析的訊息。</span><span class="sxs-lookup"><span data-stu-id="891d1-129">The A4SWIFT_MRSRDepartment property is set to an empty string for a message that did not parse</span></span>  
 <span data-ttu-id="891d1-130">當訊息修復協調流程可將已修正未剖析的訊息路由至 MessageBox 時，它將會設定[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_MRSRDepartment 屬性設為空白字串，並將它升級。</span><span class="sxs-lookup"><span data-stu-id="891d1-130">When the message-repair orchestration routes to the MessageBox an unparsed message that has been fixed, it will set the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_MRSRDepartment property to an empty string and promote it.</span></span> <span data-ttu-id="891d1-131">傳送埠不能訂閱此屬性。</span><span class="sxs-lookup"><span data-stu-id="891d1-131">A send port will not be able to subscribe on this property.</span></span>  
  
#### <a name="cannot-save-a-department-if-the-sso-service-has-been-stopped"></a><span data-ttu-id="891d1-132">無法儲存一個部門，如果 SSO 服務已停止</span><span class="sxs-lookup"><span data-stu-id="891d1-132">Cannot save a department if the SSO service has been stopped</span></span>  
 <span data-ttu-id="891d1-133">如果您嘗試新增部門，SSO 服務停止時，您會收到錯誤，指出主要 SSO 伺服器\<machinename\>失敗。</span><span class="sxs-lookup"><span data-stu-id="891d1-133">If you try to add a department when the SSO service is stopped, you will receive an error indicating that the Primary SSO server \<machinename\> failed.</span></span> <span data-ttu-id="891d1-134">請檢查是否已設定 SSO，以及 SSO 服務是否在該伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="891d1-134">Check that SSO is configured and that the SSO service is running on that server.</span></span>  
  
#### <a name="a-department-name-must-not-contain-the-character-"></a><span data-ttu-id="891d1-135">部門名稱不能包含字元"~"</span><span class="sxs-lookup"><span data-stu-id="891d1-135">A department name must not contain the character "~"</span></span>  
 <span data-ttu-id="891d1-136">包含字元的部門名稱"~"A4SWIFT 資料庫將會導致問題。</span><span class="sxs-lookup"><span data-stu-id="891d1-136">A department name that contains the character "~" will cause issues with the A4SWIFT database.</span></span>  
  
#### <a name="signing-infopath-forms"></a><span data-ttu-id="891d1-137">簽署 Infopath 表單</span><span class="sxs-lookup"><span data-stu-id="891d1-137">Signing Infopath forms</span></span>  
 <span data-ttu-id="891d1-138">簽署 InfoPath 表單必須以手動方式完成。</span><span class="sxs-lookup"><span data-stu-id="891d1-138">The signing of InfoPath forms needs to be done manually.</span></span>  
  
## <a name="security"></a><span data-ttu-id="891d1-139">Security</span><span class="sxs-lookup"><span data-stu-id="891d1-139">Security</span></span>

#### <a name="mixing-trusted-and-untrusted-hosts-can-enable-spoofing"></a><span data-ttu-id="891d1-140">混用受信任和未受信任的主機，可以啟用詐騙</span><span class="sxs-lookup"><span data-stu-id="891d1-140">Mixing trusted and untrusted hosts can enable spoofing</span></span>  

 <span data-ttu-id="891d1-141">它可能詐騙從其他未受信任的繫結的 SWIFT 訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="891d1-141">It may be possible to spoof SWIFT-bound messages from other non-trusted [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] host applications.</span></span> <span data-ttu-id="891d1-142">這是只有問題中混合信任模式下執行時 (當受信任的主機和不受信任的主機執行應用程式在同一個[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]群組)。</span><span class="sxs-lookup"><span data-stu-id="891d1-142">This is only a problem when running in mixed-trust mode (when trusted hosts and untrusted hosts run applications in the same [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] group).</span></span> <span data-ttu-id="891d1-143">您可以使用合作對象解析管線元件來識別 SWIFT 繫結訊息的來源來降低此風險。</span><span class="sxs-lookup"><span data-stu-id="891d1-143">You can mitigate this risk by using party-resolution pipeline components to identify the source of the SWIFT-bound message.</span></span> <span data-ttu-id="891d1-144">在完全信任環境中，或用於大部分的使用案例執行時，這是不必要。</span><span class="sxs-lookup"><span data-stu-id="891d1-144">This is not necessary when running in a fully trusted environment or for the majority of usage scenarios.</span></span> <span data-ttu-id="891d1-145">您應該遵循[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]混合時，建置安全的應用程式的指導方針信任和未受信任的主機。</span><span class="sxs-lookup"><span data-stu-id="891d1-145">You should follow the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] guidelines for building secure applications when mixing trusted and untrusted hosts.</span></span> 
 
## <a name="miscellaneous"></a><span data-ttu-id="891d1-146">其他</span><span class="sxs-lookup"><span data-stu-id="891d1-146">Miscellaneous</span></span>

#### <a name="the-cacheentries-setting-may-be-reset-by-a-setup-program-affecting-performance"></a><span data-ttu-id="891d1-147">CacheEntries 設定可能會重設安裝程式會影響效能</span><span class="sxs-lookup"><span data-stu-id="891d1-147">The CacheEntries setting may be reset by a Setup program, affecting performance</span></span>  
 <span data-ttu-id="891d1-148">CacheEntries 登錄機碼決定 「 商務規則引擎更新服務快取的規則集的最大數目。</span><span class="sxs-lookup"><span data-stu-id="891d1-148">The CacheEntries registry key determines the maximum number of rulesets cached by the Business Rule Engine Update service.</span></span> <span data-ttu-id="891d1-149">[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝程式預設會設定 CacheEntries 為 32。</span><span class="sxs-lookup"><span data-stu-id="891d1-149">The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Setup program sets CacheEntries to 32 by default.</span></span> <span data-ttu-id="891d1-150">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式變更 HKEY_LOCAL_MACHINE\SOFTWARE\\Microsoft \BusinessRules\3.0\CacheEntries 設為 512，以獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="891d1-150">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Setup program changes HKEY_LOCAL_MACHINE\SOFTWARE\\Microsoft \BusinessRules\3.0\CacheEntries to 512 for optimum performance.</span></span> <span data-ttu-id="891d1-151">不過，在某些情況下，CacheEntries 可能會自動重設。</span><span class="sxs-lookup"><span data-stu-id="891d1-151">However, in certain circumstances, CacheEntries may be reset automatically.</span></span> <span data-ttu-id="891d1-152">這可能會影響系統效能。</span><span class="sxs-lookup"><span data-stu-id="891d1-152">This may affect system performance.</span></span>  
  
 <span data-ttu-id="891d1-153">規則引擎更新可能會變更 CacheEntries 介於 512 到 32。</span><span class="sxs-lookup"><span data-stu-id="891d1-153">Rule Engine updates may change CacheEntries from 512 to 32.</span></span> <span data-ttu-id="891d1-154">安裝規則引擎更新之後，手動重設 CacheEntries 為 512，如有必要。</span><span class="sxs-lookup"><span data-stu-id="891d1-154">After installing a Rule Engine update, manually reset CacheEntries to 512, if necessary.</span></span>  
  
 <span data-ttu-id="891d1-155">即使[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式設為 512，解除安裝 32 設定 CacheEntries[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]無法重設 CacheEntries 介於 512 到 32。</span><span class="sxs-lookup"><span data-stu-id="891d1-155">Even though the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Setup program sets CacheEntries from 32 to 512, uninstalling [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] does not reset CacheEntries from 512 to 32.</span></span>  
  
 <span data-ttu-id="891d1-156">如需詳細資訊，請參閱 BizTalk Server 說明中的 「 規則引擎組態和調整參數 > 主題。</span><span class="sxs-lookup"><span data-stu-id="891d1-156">For more information, see the "Rule Engine Configuration and Tuning Parameters" topic in BizTalk Server Help.</span></span>  
  
#### <a name="building-a-pipeline-project-may-result-in-a-large-number-of-warnings"></a><span data-ttu-id="891d1-157">建置管線專案可能會導致大量的警告</span><span class="sxs-lookup"><span data-stu-id="891d1-157">Building a pipeline project may result in a large number of warnings</span></span>  
 <span data-ttu-id="891d1-158">當您將 SWIFT 組合器新增至傳送管線或 SWIFT 解譯器，接收管線，然後建立包含這些管線的管線專案時，您可能會收到一系列的管線元件相關的警告。</span><span class="sxs-lookup"><span data-stu-id="891d1-158">When you add the SWIFT assembler to a send pipeline, or the SWIFT disassembler to a receive pipeline, and then build the pipeline project containing those pipelines, you may receive a series of warnings related to the pipeline components.</span></span> <span data-ttu-id="891d1-159">這些警告會指示 Visual Studio 找不到相依性。</span><span class="sxs-lookup"><span data-stu-id="891d1-159">These warnings indicate that Visual Studio could not find dependencies.</span></span> <span data-ttu-id="891d1-160">您可以更正導致這些警告，如下所示變更 SWIFTAsm 或 SWIFTDasm 中的組件 [參考] 資料夾中，[複製本機] 屬性的條件：</span><span class="sxs-lookup"><span data-stu-id="891d1-160">You can correct the condition leading to these warnings by changing the Copy Local property of the SWIFTAsm or SWIFTDasm assembly in the reference folder, as follows:</span></span>  
  
1.  <span data-ttu-id="891d1-161">在 Visual Studio 的方案總管，展開您管線的專案，然後再展開**參考**節點。</span><span class="sxs-lookup"><span data-stu-id="891d1-161">In Solution Explorer of Visual Studio, expand your pipeline project, and then expand the **References** node.</span></span>  
  
2.  <span data-ttu-id="891d1-162">在 [參考] 節點中，選取**SWIFTAsm**組件和/或**SWIFTDasm**組件。</span><span class="sxs-lookup"><span data-stu-id="891d1-162">Under the References node, select the **SWIFTAsm** assembly and/or the **SWIFTDasm** assembly.</span></span>  
  
3.  <span data-ttu-id="891d1-163">在 [屬性] 窗格中，將變更的值**複製到本機**屬性設**False**。</span><span class="sxs-lookup"><span data-stu-id="891d1-163">In the Properties pane, change the value for the **Copy Local** property to **False**.</span></span>  
  
4.  <span data-ttu-id="891d1-164">您管線的專案，以滑鼠右鍵按一下，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="891d1-164">Right-click your pipeline project, and then click **Build**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="891d1-165">您應該不會看到找不到的相依性有關的任何警告。</span><span class="sxs-lookup"><span data-stu-id="891d1-165">You should not see any warnings about dependencies not being found.</span></span>   