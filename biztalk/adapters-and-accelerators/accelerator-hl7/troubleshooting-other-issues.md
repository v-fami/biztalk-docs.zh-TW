---
title: 疑難排解其他問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting
ms.assetid: 1f115f64-45ce-445d-ab18-092f4a6a232c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 796482df7234e2699b5b9bd3d1c12f6e98ccb923
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-other-issues"></a><span data-ttu-id="358eb-102">疑難排解其他問題</span><span class="sxs-lookup"><span data-stu-id="358eb-102">Troubleshooting Other Issues</span></span>
<span data-ttu-id="358eb-103">其他相關的問題提供解決[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="358eb-103">Addresses other issues related to [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)].</span></span>  
  
## <a name="message-rejected-by-the-btahl7-engine"></a><span data-ttu-id="358eb-104">BTAHL7 引擎所拒絕的訊息</span><span class="sxs-lookup"><span data-stu-id="358eb-104">Message rejected by the BTAHL7 engine</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="358eb-105">徵兆</span><span class="sxs-lookup"><span data-stu-id="358eb-105">Symptom</span></span>  
 <span data-ttu-id="358eb-106">訊息會隨機拒絕的訊息引擎中。</span><span class="sxs-lookup"><span data-stu-id="358eb-106">Messages are randomly rejected by the message engine.</span></span>  
  
<span data-ttu-id="358eb-107">**可能的原因**： 根據 HL7 標準，列舉值的資料表 0338年包含"L & 我"值。</span><span class="sxs-lookup"><span data-stu-id="358eb-107">**Possible Cause** : According to the HL7 standard, enumeration values for table 0338 contains the "L&I" value.</span></span> <span data-ttu-id="358eb-108">欄位 6 的 PRA 區段可能包含這個值。</span><span class="sxs-lookup"><span data-stu-id="358eb-108">Field 6 of the PRA segment may contain this value.</span></span> <span data-ttu-id="358eb-109">因為[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會將"&"字元做為分隔符號，將會拒絕訊息。</span><span class="sxs-lookup"><span data-stu-id="358eb-109">Since [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] treats the "&" character as a delimiter, the message is rejected.</span></span>  
  
<span data-ttu-id="358eb-110">**解析**： 沒有此問題的三個可能的解決方式：</span><span class="sxs-lookup"><span data-stu-id="358eb-110">**Resolution** : There are three potential resolutions for this issue:</span></span>  
  
1.  <span data-ttu-id="358eb-111">在訊息執行個體，會處理透過逸出序列，例如使用字元組合 L\T\I"&"字元。</span><span class="sxs-lookup"><span data-stu-id="358eb-111">In the message instance, handle the "&" character through an escape sequence, such as using the character combination L\T\I.</span></span>  
  
2.  <span data-ttu-id="358eb-112">L"I"的列舉值在將 PRA 6 結構描述中，並改為使用訊息執行個體中的此值。</span><span class="sxs-lookup"><span data-stu-id="358eb-112">Add an enumeration value of "LI" at PRA 6 in the schema and use this value instead in the message instance.</span></span>  
  
3.  <span data-ttu-id="358eb-113">在 MSH2; 中使用完全不同的子元件分隔符號不過，這個特定的解決方案可能無法實際取決於您的環境而定。</span><span class="sxs-lookup"><span data-stu-id="358eb-113">Use a completely different subcomponent separator in MSH2; however, this particular solution may not be practical depending upon your environment.</span></span>  
  
## <a name="cannot-edit-the-hl7-schema-using-visual-studio"></a><span data-ttu-id="358eb-114">無法編輯 HL7 結構描述使用 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="358eb-114">Cannot edit the HL7 schema using Visual Studio</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="358eb-115">徵兆</span><span class="sxs-lookup"><span data-stu-id="358eb-115">Symptom</span></span>  
 <span data-ttu-id="358eb-116">無法編輯 HL7 結構描述使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="358eb-116">Cannot edit the HL7 schema using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
<span data-ttu-id="358eb-117">**可能的原因**:[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]不支援部分 HL7 結構描述。</span><span class="sxs-lookup"><span data-stu-id="358eb-117">**Possible Cause** : [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] does not support some HL7 schemas.</span></span>  
  
<span data-ttu-id="358eb-118">**解析**： 使用其他編輯器，例如[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][記事本] 來編輯 HL7 結構描述。</span><span class="sxs-lookup"><span data-stu-id="358eb-118">**Resolution** : Use other editors, such as [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Notepad, to edit HL7 schemas.</span></span>  
  
## <a name="message-handling-fails-with-no-errors-logged"></a><span data-ttu-id="358eb-119">訊息處理失敗，並沒有記錄的錯誤</span><span class="sxs-lookup"><span data-stu-id="358eb-119">Message handling fails with no errors logged</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="358eb-120">徵兆</span><span class="sxs-lookup"><span data-stu-id="358eb-120">Symptom</span></span>  
 <span data-ttu-id="358eb-121">系統會處理訊息，但不記錄錯誤訊息，或將訊息放入擱置的訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="358eb-121">The system processes messages without logging error messages or placing messages in the suspended message queue.</span></span>  
  
<span data-ttu-id="358eb-122">**可能的原因**: **HeaderSpecType**和**DocumentSpecType**屬性值會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="358eb-122">**Possible Cause** : The **HeaderSpecType** and **DocumentSpecType** property values are case-sensitive.</span></span> <span data-ttu-id="358eb-123">當您部署您的管線時，在這些名稱的拼字錯誤可能會導致訊息傳送至 mishandled 並沒有記錄的錯誤而中斷。</span><span class="sxs-lookup"><span data-stu-id="358eb-123">When you deploy your pipelines, a typographical error in these names can cause messages to be mishandled and dropped with no errors logged.</span></span>  
  
<span data-ttu-id="358eb-124">**解析**： 使用時，觀察是否區分大小寫**HeaderSpecType**和**DocumentSpecType**屬性值名稱。</span><span class="sxs-lookup"><span data-stu-id="358eb-124">**Resolution** : Observe case-sensitivity when using the **HeaderSpecType** and **DocumentSpecType** property value names.</span></span>  
  
## <a name="message-header-fields-are-not-validated-correctly"></a><span data-ttu-id="358eb-125">訊息標頭欄位未正確驗證</span><span class="sxs-lookup"><span data-stu-id="358eb-125">Message header fields are not validated correctly</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="358eb-126">徵兆</span><span class="sxs-lookup"><span data-stu-id="358eb-126">Symptom</span></span>  
 <span data-ttu-id="358eb-127">標頭欄位的驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="358eb-127">Validation of a header field failed.</span></span>  
  
 <span data-ttu-id="358eb-128">原因：[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]序列化程式會驗證升級的屬性，而不實際的標頭欄位內容屬性。</span><span class="sxs-lookup"><span data-stu-id="358eb-128">Reason: The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer validated a promoted property, not the actual header-field context property.</span></span>  
  
<span data-ttu-id="358eb-129">**可能的原因**： 對應至透過協調流程或對應的標頭的升級屬性發生變更。</span><span class="sxs-lookup"><span data-stu-id="358eb-129">**Possible Cause** : A change occurred to the promoted property corresponding to the header through an orchestration or a map.</span></span>  
  
<span data-ttu-id="358eb-130">**解析**： 內容屬性的訊息標頭 MSH1、 MSH2 和 MSH5 {1-3} 需要更新，使其在同步處理的資料。</span><span class="sxs-lookup"><span data-stu-id="358eb-130">**Resolution** : The context properties of message headers MSH1, MSH2, and MSH5{1-3} need to be updated so that they are in synchronization with the data.</span></span>  
  
## <a name="the-mllp-adapter-is-not-removed-during-uninstall"></a><span data-ttu-id="358eb-131">解除安裝期間將不會移除 MLLP 配接器</span><span class="sxs-lookup"><span data-stu-id="358eb-131">The MLLP adapter is not removed during uninstall</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="358eb-132">徵兆</span><span class="sxs-lookup"><span data-stu-id="358eb-132">Symptom</span></span>  
 <span data-ttu-id="358eb-133">在解除安裝 BTAHL7 期間，BTAHL7 安裝程式並未移除 MLLP 配接器。</span><span class="sxs-lookup"><span data-stu-id="358eb-133">The BTAHL7 setup program did not remove the MLLP adapter during uninstallation of BTAHL7.</span></span>  
  
<span data-ttu-id="358eb-134">**可能的原因**： 時發生傳輸類型為 MLLP 的接收位置或傳送埠。</span><span class="sxs-lookup"><span data-stu-id="358eb-134">**Possible Cause** : There was a receive location or send port with a transport type of MLLP.</span></span> <span data-ttu-id="358eb-135">如果在任何 BizTalk Server 專案正在參考它，BTAHL7 安裝程式無法移除 MLLP 配接器。</span><span class="sxs-lookup"><span data-stu-id="358eb-135">BTAHL7 setup cannot remove the MLLP adapter if it is being referenced in any of the BizTalk Server projects.</span></span>  
  
<span data-ttu-id="358eb-136">**解析**： 解除安裝 BTAHL7 完成後，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="358eb-136">**Resolution** : After uninstallation of BTAHL7 has completed, do the following:</span></span>  
  
1.  <span data-ttu-id="358eb-137">在 BizTalk Server 管理主控台中，移除所有接收位置和傳送埠的傳輸類型 MLLP，或變更傳輸類型的接收位置或傳送埠新增至另一個類型。</span><span class="sxs-lookup"><span data-stu-id="358eb-137">In the BizTalk Server Administration Console, remove all receive locations and send ports that have a transport type of MLLP, or change the transport type of the receive locations or send ports to another type.</span></span>  
  
2.  <span data-ttu-id="358eb-138">在管理主控台中，刪除 MLLP 配接器。</span><span class="sxs-lookup"><span data-stu-id="358eb-138">In the Administration Console, delete the MLLP adapter.</span></span>  
  
3.  <span data-ttu-id="358eb-139">重新啟動主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="358eb-139">Restart the host instance.</span></span>  
  
## <a name="btahl7-cannot-be-uninstalled-if-biztalk-server-has-already-been-uninstalled"></a><span data-ttu-id="358eb-140">無法解除安裝 BTAHL7，如果已解除安裝 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="358eb-140">BTAHL7 cannot be uninstalled if BizTalk Server has already been uninstalled</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="358eb-141">徵兆</span><span class="sxs-lookup"><span data-stu-id="358eb-141">Symptom</span></span>  
 <span data-ttu-id="358eb-142">解除安裝[!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]會導致下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="358eb-142">Uninstalling [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] results in the following error:</span></span>  
  
`A network error while attempting to read from file C:\Windows\Installer\Microsoft BizTalk <version\> Accelerator for HL7.msi`
  
<span data-ttu-id="358eb-143">**可能的原因**:[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]已解除安裝，才能解除安裝[!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]嘗試。</span><span class="sxs-lookup"><span data-stu-id="358eb-143">**Possible Cause** : [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] was uninstalled before uninstallation of [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] was attempted.</span></span> <span data-ttu-id="358eb-144">您必須先解除安裝[!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]再解除安裝[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="358eb-144">You must uninstall [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] before uninstalling [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
<span data-ttu-id="358eb-145">**解析**： 重新安裝[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]，然後解除安裝[!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]，然後再解除安裝[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="358eb-145">**Resolution** : Reinstall [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)], then uninstall [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)], and then uninstall [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="messages-are-still-sent-after-the-applicable-mllp-send-port-has-been-stopped"></a><span data-ttu-id="358eb-146">停止適用 MLLP 傳送埠之後，仍會傳送訊息</span><span class="sxs-lookup"><span data-stu-id="358eb-146">Messages are still sent after the applicable MLLP send port has been stopped</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="358eb-147">徵兆</span><span class="sxs-lookup"><span data-stu-id="358eb-147">Symptom</span></span>  
 <span data-ttu-id="358eb-148">之後您停止 MLLP 傳送埠，傳送埠會透過傳送的訊息不會停止，但繼續傳送。</span><span class="sxs-lookup"><span data-stu-id="358eb-148">After you stop an MLLP send port, the messages that are sent through that send port do not stop, but continue to be sent.</span></span>  
  
<span data-ttu-id="358eb-149">**可能的原因**： 當您停止傳送埠時，連接會保持已建立直到停止 BizTalk 主控件移除為止。</span><span class="sxs-lookup"><span data-stu-id="358eb-149">**Possible Cause** : When you stop a send port, the connection remains established until it is removed by stopping the BizTalk host.</span></span> <span data-ttu-id="358eb-150">如此一來，訊息仍會傳送給之後停止傳送埠。</span><span class="sxs-lookup"><span data-stu-id="358eb-150">As a result, messages are still sent after the send port has been stopped.</span></span> <span data-ttu-id="358eb-151">這是因為 Biztalk Server 不會呼叫執行 MLLP 配接器期間啟動或停止的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="358eb-151">This occurs because Biztalk Server does not call into the MLLP adapter during start or stop of the send port.</span></span> <span data-ttu-id="358eb-152">BizTalk Server 呼叫 MLLP 配接器只在開始和停止主機服務。</span><span class="sxs-lookup"><span data-stu-id="358eb-152">BizTalk Server calls into the MLLP adapter only during the start and stop of the host service.</span></span>  
  
<span data-ttu-id="358eb-153">**解析**： 您可以藉由停止是您在停止的傳送埠的傳送處理常式主控件執行個體移除連線並停止傳輸的訊息。</span><span class="sxs-lookup"><span data-stu-id="358eb-153">**Resolution** : You can remove the connection and stop transmission of messages by stopping the host instance that is the send handler for the send port that you stopped.</span></span> <span data-ttu-id="358eb-154">不過，停止該主控件執行個體可能會影響其他不想停止的訊息。</span><span class="sxs-lookup"><span data-stu-id="358eb-154">However, stopping that host instance might affect other messages that you do not want to stop.</span></span> <span data-ttu-id="358eb-155">如果您知道這種情況，您應該設定傳送埠以不同的方式建立它時。</span><span class="sxs-lookup"><span data-stu-id="358eb-155">If you know that this is the case, you should configure the send port differently when you create it.</span></span> <span data-ttu-id="358eb-156">您應該建立另一個做為 僅此 MLLP 的傳送埠 （或傳送埠的子集） 的傳送處理常式的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="358eb-156">You should create another host instance to serve as the send handler for only this MLLP send port (or a subset of your send ports).</span></span> <span data-ttu-id="358eb-157">您可以停止此主控件執行個體，然後停止傳輸來自此傳送埠的訊息。</span><span class="sxs-lookup"><span data-stu-id="358eb-157">You can then stop transmission of messages from this send port by stopping this host instance.</span></span> <span data-ttu-id="358eb-158">然後不會影響其他使用其他的傳送處理常式的傳送埠上的其他訊息的傳輸。</span><span class="sxs-lookup"><span data-stu-id="358eb-158">This will then not affect transmission of other messages on other send ports that use other send handlers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358eb-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="358eb-159">See Also</span></span>  
 [<span data-ttu-id="358eb-160">HL7 中的疑難排解和已知問題</span><span class="sxs-lookup"><span data-stu-id="358eb-160">Troubleshooting and known issues in HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)