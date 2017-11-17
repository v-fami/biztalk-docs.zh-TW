---
title: "訊息修復和新送出疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, Message Repair and New Submission
- Message Repair and New Submission, troubleshooting
ms.assetid: bb07a286-6f02-4639-b5fa-a3647e356ac8
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9dab8140c33b5518ec01f28128b5ef15bab0fab6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-repair-and-new-submission-troubleshooting"></a><span data-ttu-id="57189-102">訊息修復和新送出疑難排解</span><span class="sxs-lookup"><span data-stu-id="57189-102">Message Repair and New Submission Troubleshooting</span></span>
## <a name="a-repaired-message-cannot-be-submitted-if-the-envelope-schema-is-not-deployed"></a><span data-ttu-id="57189-103">無法送出修復的訊息，如果未部署信封結構描述</span><span class="sxs-lookup"><span data-stu-id="57189-103">A repaired message cannot be submitted if the envelope schema is not deployed</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="57189-104">徵兆</span><span class="sxs-lookup"><span data-stu-id="57189-104">Symptom</span></span>  
 <span data-ttu-id="57189-105">當您嘗試送出的訊息，您已修復，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]會將下列訊息：</span><span class="sxs-lookup"><span data-stu-id="57189-105">When you attempt to submit a message that you have repaired, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] posts the following message:</span></span>  
  
 <span data-ttu-id="57189-106">「 配接器無法傳輸的傳送埠時，訊息將"http://mrsrtest:80/StsWebReceive/default.aspx?PartnerId=Unparsed & FolderType = MessagesInbox"。</span><span class="sxs-lookup"><span data-stu-id="57189-106">"The adapter failed to transmit message going to send port "http://mrsrtest:80/StsWebReceive/default.aspx?PartnerId=Unparsed&FolderType=MessagesInbox".</span></span> <span data-ttu-id="57189-107">它會指定此傳送埠的重試間隔後重新傳輸。</span><span class="sxs-lookup"><span data-stu-id="57189-107">It will be retransmitted after the retry interval specified for this Send Port.</span></span> <span data-ttu-id="57189-108">詳細資料:"80131600"。</span><span class="sxs-lookup"><span data-stu-id="57189-108">Details:"80131600".</span></span> <span data-ttu-id="57189-109">如需詳細資訊，請參閱說明及支援中心在[http://go.microsoft.com/fwlink/?LinkId=142493](http://go.microsoft.com/fwlink/?LinkId=142493)。</span><span class="sxs-lookup"><span data-stu-id="57189-109">For more information, see Help and Support Center at [http://go.microsoft.com/fwlink/?LinkId=142493](http://go.microsoft.com/fwlink/?LinkId=142493).</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="57189-110">可能的原因</span><span class="sxs-lookup"><span data-stu-id="57189-110">Possible Cause</span></span>  
 <span data-ttu-id="57189-111">未部署信封結構描述。</span><span class="sxs-lookup"><span data-stu-id="57189-111">The envelope schema is not deployed.</span></span> <span data-ttu-id="57189-112">這適用於任何 MT*xxx*剖析失敗的任何訊息。</span><span class="sxs-lookup"><span data-stu-id="57189-112">This is true for any MT*xxx* message or any message that has failed parsing.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="57189-113">方案</span><span class="sxs-lookup"><span data-stu-id="57189-113">Solution</span></span>  
 <span data-ttu-id="57189-114">部署您使用每個訊息結構描述的信封結構描述 (\<磁碟機 >: \Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本 > Message Pack \SWIFT Messages\ A4SWIFT SRG\<版本 > \類別 n\MTxxx.xsd) 和未剖析的信封結構描述 (\<磁碟機 >: \Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本 > Message Pack \SWIFT Messages\ A4SWIFT SRG\<版本 > \ UnparsedMessage\EnvelopeUnparsedMessage.xsd)。</span><span class="sxs-lookup"><span data-stu-id="57189-114">Deploy an envelope schema for each message schema that you are using (\<drive>:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version> Message Pack \SWIFT Messages\ A4SWIFT-SRG\<version>\Category n\MTxxx.xsd) and for unparsed envelope schema (\<drive>:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version> Message Pack \SWIFT Messages\ A4SWIFT-SRG\<version>\ Unparsed Message\EnvelopeUnparsedMessage.xsd).</span></span> <span data-ttu-id="57189-115">如需詳細資訊，請參閱[部署 A4SWIFT 結構描述](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="57189-115">For more information, see [Deploying A4SWIFT Schemas](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md).</span></span>  
  
## <a name="you-cannot-submit-a-fixed-unparsed-message-from-a-mrsr-site-library-named-other-than-unparsed"></a><span data-ttu-id="57189-116">您無法送出固定的未剖析的訊息，從名為"Unparsed"以外的 MRSR 網站庫</span><span class="sxs-lookup"><span data-stu-id="57189-116">You cannot submit a fixed unparsed message from a MRSR site library named other than "Unparsed"</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="57189-117">徵兆</span><span class="sxs-lookup"><span data-stu-id="57189-117">Symptom</span></span>  
 <span data-ttu-id="57189-118">當您嘗試送出您修正從 MRSR 網站文件庫名稱不是"Unparsed"剖析的訊息時，則作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="57189-118">When you try to submit an unparsed message that you have fixed from a MRSR site document library that is not named "Unparsed", the operation fails.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="57189-119">可能的原因</span><span class="sxs-lookup"><span data-stu-id="57189-119">Possible Cause</span></span>  
 <span data-ttu-id="57189-120">A4SWIFT 無法成功送出訊息，以從程式庫不是名為"Unparsed"。</span><span class="sxs-lookup"><span data-stu-id="57189-120">A4SWIFT cannot successfully submit a message from a library that is not named "Unparsed".</span></span> <span data-ttu-id="57189-121">如果您在現有的"Unparsed 」 文件庫 MRSR 站台安裝 MRSR （訊息修復） 功能之前，A4SWIFT 安裝程式會建立未剖析的訊息加上尾碼標題為 「 Unparsed"的程式庫。</span><span class="sxs-lookup"><span data-stu-id="57189-121">If you have an existing "Unparsed" document library in MRSR site before you install the MRSR (message repair) feature, A4SWIFT setup will create a library for unparsed messages entitled "Unparsed" with a suffix.</span></span> <span data-ttu-id="57189-122">當它收到 A4SWIFT 無法剖析的訊息時，它會將訊息路由傳送至它所建立的文件庫。</span><span class="sxs-lookup"><span data-stu-id="57189-122">When it receives a message that A4SWIFT could not parse, it will route the message to that library that it created.</span></span> <span data-ttu-id="57189-123">不過，當您嘗試送出訊息，以從該程式庫時，作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="57189-123">However, when you try to submit a message from that library, the operation will fail.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="57189-124">方案</span><span class="sxs-lookup"><span data-stu-id="57189-124">Solution</span></span>  
 <span data-ttu-id="57189-125">移除 MRSR 功能、 刪除未剖析的文件庫，然後再重新安裝 MRSR 功能。</span><span class="sxs-lookup"><span data-stu-id="57189-125">Remove the MRSR feature, delete the Unparsed library, and then reinstall the MRSR feature.</span></span>  
  
## <a name="cannot-loop-back-a-message-in-a-two-stage-workflow"></a><span data-ttu-id="57189-126">無法送回兩階段的工作流程中的訊息</span><span class="sxs-lookup"><span data-stu-id="57189-126">Cannot loop back a message in a two-stage workflow</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="57189-127">徵兆</span><span class="sxs-lookup"><span data-stu-id="57189-127">Symptom</span></span>  
 <span data-ttu-id="57189-128">如果您在建立階段和修復階段的工作流程的修復階段拒絕訊息，提交會失敗。</span><span class="sxs-lookup"><span data-stu-id="57189-128">If you reject a message in the Repair stage of a workflow that has only a Create stage and a Repair stage, the submission fails.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="57189-129">會將訊息路由至 MessageBox，並會將下列的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="57189-129"> routes the message back to the MessageBox and posts the following error message:</span></span>  
  
 <span data-ttu-id="57189-130">「 無法重設至工作流程中的第一個階段。"</span><span class="sxs-lookup"><span data-stu-id="57189-130">"Could not reset to the first stage in the workflow."</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="57189-131">可能的原因</span><span class="sxs-lookup"><span data-stu-id="57189-131">Possible Cause</span></span>  
 <span data-ttu-id="57189-132">已建立階段和修復階段的工作流程不支援訊息回送。</span><span class="sxs-lookup"><span data-stu-id="57189-132">Message loopback is not supported for a workflow that has only a Create stage and a Repair stage.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="57189-133">方案</span><span class="sxs-lookup"><span data-stu-id="57189-133">Solution</span></span>  
 <span data-ttu-id="57189-134">兩階段的工作流程，加入另一個階段，或取消送出。</span><span class="sxs-lookup"><span data-stu-id="57189-134">Add another stage to the two-stage workflow, or cancel the submission.</span></span>  
  
## <a name="cannot-open-a-message-in-the-repair-inbox-in-mrsr"></a><span data-ttu-id="57189-135">無法開啟 MRSR 的修復收件匣中的訊息</span><span class="sxs-lookup"><span data-stu-id="57189-135">Cannot open a message in the repair inbox in MRSR</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="57189-136">徵兆</span><span class="sxs-lookup"><span data-stu-id="57189-136">Symptom</span></span>  
 <span data-ttu-id="57189-137">當您嘗試開啟郵件中 MRSR 修復收件匣中時，您會收到下列錯誤訊息快顯視窗中：</span><span class="sxs-lookup"><span data-stu-id="57189-137">When you try to open a message in the repair inbox in MRSR, you receive the following error message in a popup:</span></span>  
  
 <span data-ttu-id="57189-138">「 無法開啟所要求的登入 'A4SWIFT' 資料庫。</span><span class="sxs-lookup"><span data-stu-id="57189-138">"Cannot open database requested in login 'A4SWIFT'.</span></span> <span data-ttu-id="57189-139">登入失敗。</span><span class="sxs-lookup"><span data-stu-id="57189-139">Login fails.</span></span> <span data-ttu-id="57189-140">使用者 ' NT AUTHORITY\NETWORK SERVICE' 的登入失敗。</span><span class="sxs-lookup"><span data-stu-id="57189-140">Login failed for user 'NT AUTHORITY\NETWORK SERVICE'.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="57189-141">可能的原因</span><span class="sxs-lookup"><span data-stu-id="57189-141">Possible Cause</span></span>  
 <span data-ttu-id="57189-142">登入帳戶 A4SWIFT_MRSR web 服務之下執行的 web 應用程式是網路服務，不在本機或網域帳戶所屬 A4SWIFT 使用者群組。</span><span class="sxs-lookup"><span data-stu-id="57189-142">The login account for the web application that the A4SWIFT_MRSR web service runs under is Network Service, not a local or domain account that is in the A4SWIFT Users group.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="57189-143">方案</span><span class="sxs-lookup"><span data-stu-id="57189-143">Solution</span></span>  
 <span data-ttu-id="57189-144">變更 web 應用程式執行 A4SWIFT_MRSR web 服務的登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="57189-144">Change the login account for the web application that the A4SWIFT_MRSR web service runs under.</span></span>  
  
##### <a name="to-change-the-login-account-for-the-web-application-that-the-a4swiftmrsr-web-service-runs-under"></a><span data-ttu-id="57189-145">若要變更 web 應用程式執行 A4SWIFT_MRSR web 服務的登入帳戶</span><span class="sxs-lookup"><span data-stu-id="57189-145">To change the login account for the web application that the A4SWIFT_MRSR web service runs under</span></span>  
  
1.  <span data-ttu-id="57189-146">按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**.</span><span class="sxs-lookup"><span data-stu-id="57189-146">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="57189-147">在 IIS 管理員 中，展開 ***\<伺服器名稱 >* （本機電腦）**  節點，**應用程式集區**節點和**網站**節點。</span><span class="sxs-lookup"><span data-stu-id="57189-147">In IIS Manager, expand the ***\<server name>* (local computer)** node, the **Application Pools** node and the **Web Sites** node.</span></span> <span data-ttu-id="57189-148">展開 [網站] 節點底下**Default Web Site**節點。</span><span class="sxs-lookup"><span data-stu-id="57189-148">Under the Web Sites node, expand the **Default Web Site** node.</span></span>  
  
3.  <span data-ttu-id="57189-149">預設的網站] 節點下，以滑鼠右鍵按一下**A4SWIFT_MRSR**，然後按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="57189-149">Under the Default Web Site node, right-click **A4SWIFT_MRSR**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="57189-150">在 A4SWIFT_MRSR 屬性 對話方塊中，記下的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="57189-150">In the A4SWIFT_MRSR Properties dialog box, note the Application pool.</span></span>  
  
5.  <span data-ttu-id="57189-151">在 IIS 管理員 對話方塊的 應用程式集區 節點下，應用程式集區的 A4SWIFT_MRSR，然後按一下右鍵**屬性**。</span><span class="sxs-lookup"><span data-stu-id="57189-151">In the IIS Manager dialog box, under the Application Pools node, right-click the application pool for A4SWIFT_MRSR, and then click **Properties**.</span></span>  
  
6.  <span data-ttu-id="57189-152">在\<應用程式集區名稱 > 內容] 對話方塊中，按一下 [**識別**附註。</span><span class="sxs-lookup"><span data-stu-id="57189-152">In the \<application pool name> Properties dialog box, click the **Identity** note.</span></span> <span data-ttu-id="57189-153">如果**預先定義**按一下和**網路服務**已選取，按一下**可設定**，輸入您的本機或網域帳戶，，，然後輸入您的密碼。</span><span class="sxs-lookup"><span data-stu-id="57189-153">If **Predefined** is clicked and **Network Service** is selected, click **Configurable**, enter your local or domain account, and then enter your password.</span></span> <span data-ttu-id="57189-154">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="57189-154">Click **OK**.</span></span>  
  
## <a name="a-message-created-in-mrsr-site-on-a-localized-computer-is-not-processed"></a><span data-ttu-id="57189-155">建立當地語系化的電腦上的 MRSR 站台中的訊息則不會處理</span><span class="sxs-lookup"><span data-stu-id="57189-155">A message created in MRSR site on a localized computer is not processed</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="57189-156">徵兆</span><span class="sxs-lookup"><span data-stu-id="57189-156">Symptom</span></span>  
 <span data-ttu-id="57189-157">當工作在當地語系化的平台上執行 A4SWIFT 的英文版上的使用者建立中的訊息[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成中 MRSR，並將訊息提交成功時，訊息似乎是由 Message Repair 和 New Submission協調流程，但不是成功處理。</span><span class="sxs-lookup"><span data-stu-id="57189-157">When a user working on an English version of A4SWIFT that is running on a localized platform creates a message in an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form in MRSR, and submits the message successfully, the message appears to be consumed by the Message Repair and New Submission orchestration, but is not successfully processed.</span></span> <span data-ttu-id="57189-158">訊息提交給寄件匣，但 BizTalk 配接器未收取。</span><span class="sxs-lookup"><span data-stu-id="57189-158">The message is submitted to the outbox, but is not picked up by the BizTalk adapter.</span></span> <span data-ttu-id="57189-159">任何錯誤或警告會公佈在事件檢視器中，並沒有執行中協調流程執行個體在 HAT 中的記錄。</span><span class="sxs-lookup"><span data-stu-id="57189-159">No error or warning is posted in the Event Viewer, and there is no record of a running orchestration instance in HAT.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="57189-160">可能的原因</span><span class="sxs-lookup"><span data-stu-id="57189-160">Possible Cause</span></span>  
 <span data-ttu-id="57189-161">輸入 URI 為 STS 的路徑。寄件匣接收位置包含英文名稱，而不是當地語系化的名稱。</span><span class="sxs-lookup"><span data-stu-id="57189-161">The path entered as the URI for the STS.Outbox receive location contains the English name, not the localized name.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="57189-162">方案</span><span class="sxs-lookup"><span data-stu-id="57189-162">Solution</span></span>  
 <span data-ttu-id="57189-163">變更 STS 的 URI 位址。寄件匣接收位置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="57189-163">Change the URI address for the STS.Outbox receive location as follows:</span></span>  
  
1.  <span data-ttu-id="57189-164">在 BizTalk Server 2009 管理主控台中，展開**BizTalk 群組**，**應用程式**，和**BizTalk Application 1 節點**。</span><span class="sxs-lookup"><span data-stu-id="57189-164">In the BizTalk Server 2009 Administration Console, expand the **BizTalk Group**, **Applications**, and **BizTalk Application 1 nodes**.</span></span>  
  
2.  <span data-ttu-id="57189-165">按一下**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="57189-165">Click **Receive Locations**.</span></span>  
  
3.  <span data-ttu-id="57189-166">按兩下**為 Sts.Outbox.Location**。</span><span class="sxs-lookup"><span data-stu-id="57189-166">Double-click **Sts.Outbox.Location**.</span></span>  
  
4.  <span data-ttu-id="57189-167">在 [接收位置屬性] 對話方塊中，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="57189-167">In the Receive Location Properties dialog box, click **Configure**.</span></span>  
  
5.  <span data-ttu-id="57189-168">在 [傳輸屬性] 對話方塊中，將取代的值**SharePointSite URL**與當地語系化的對等項目。</span><span class="sxs-lookup"><span data-stu-id="57189-168">In the Transport Properties dialog box, replace the value for **SharePointSite URL** with the localized equivalent.</span></span>  
  
6.  <span data-ttu-id="57189-169">按一下**確定**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="57189-169">Click **OK**, and then click **OK**.</span></span>  
  
## <a name="removing-a-role-while-it-is-processing-a-message-results-in-incomplete-removal-of-documents-and-artifacts"></a><span data-ttu-id="57189-170">移除角色，當它正在處理中移除不完全的文件和成品郵件結果</span><span class="sxs-lookup"><span data-stu-id="57189-170">Removing a role while it is processing a message results in incomplete removal of documents and artifacts</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="57189-171">徵兆</span><span class="sxs-lookup"><span data-stu-id="57189-171">Symptom</span></span>  
 <span data-ttu-id="57189-172">當您在設定檔的 Web 用戶端移除的角色時，對話方塊會公佈指出將會移除所有的文件和成品與角色相關聯。</span><span class="sxs-lookup"><span data-stu-id="57189-172">When you remove a role in the Profile Web Client, a dialog box is posted indicating that all documents and artifacts associated with the role will be removed.</span></span> <span data-ttu-id="57189-173">不過，角色不會從 [A4SWIFT 管理] 主控台中的部門移除，而且從 MRSR 不會移除角色的文件資料夾 （收件匣和寄件備份）。</span><span class="sxs-lookup"><span data-stu-id="57189-173">However, the role is not removed from the department in the A4SWIFT Management Console, and the role's document folders (Inbox and Sent Items) are not removed from MRSR.</span></span> <span data-ttu-id="57189-174">移除合作對象、 傳送埠和與角色相關聯的協議，和角色設定檔已解除部署。</span><span class="sxs-lookup"><span data-stu-id="57189-174">The party, send port, and agreement associated with the role are removed, and the profile of the role is undeployed.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="57189-175">可能的原因</span><span class="sxs-lookup"><span data-stu-id="57189-175">Possible Cause</span></span>  
 <span data-ttu-id="57189-176">訊息仍然會在角色的收件匣中 MRSR，而且訊息已在中開啟其[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。</span><span class="sxs-lookup"><span data-stu-id="57189-176">A message is still in the role's inbox in MRSR, and the message is open in its [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="57189-177">方案</span><span class="sxs-lookup"><span data-stu-id="57189-177">Solution</span></span>  
 <span data-ttu-id="57189-178">手動從 MRSR 網站收件匣中，刪除訊息，然後刪除 已移除的角色相關聯的文件庫。</span><span class="sxs-lookup"><span data-stu-id="57189-178">Manually delete the message from the MRSR site inbox, and then delete the document library that is associated with the role that you were removing.</span></span> <span data-ttu-id="57189-179">關閉表單並再次移除角色。</span><span class="sxs-lookup"><span data-stu-id="57189-179">Close the form and remove the role again.</span></span>  
  
## <a name="message-processing-fails-as-a-result-of-an-error-in-the-bic-master-policy"></a><span data-ttu-id="57189-180">訊息處理失敗，因為 BIC 主要原則中的錯誤</span><span class="sxs-lookup"><span data-stu-id="57189-180">Message processing fails as a result of an error in the BIC Master Policy</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="57189-181">徵兆</span><span class="sxs-lookup"><span data-stu-id="57189-181">Symptom</span></span>  
 <span data-ttu-id="57189-182">當您提交訊息，以進行處理時，您會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="57189-182">When you submit a message for processing, you receive the following error:</span></span>  
  
 <span data-ttu-id="57189-183">「 執行 BicMasterPolicy 時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="57189-183">"An error occurred while executing the BicMasterPolicy.</span></span> <span data-ttu-id="57189-184">檢查有效的值的原則。 」</span><span class="sxs-lookup"><span data-stu-id="57189-184">Check the policy for valid values."</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="57189-185">可能的原因</span><span class="sxs-lookup"><span data-stu-id="57189-185">Possible Cause</span></span>  
 <span data-ttu-id="57189-186">SQL Server 名稱、 BIC 資料庫名稱和整合式的安全性的 BIC_Master_Policy.xml 檔案中的值*\<磁碟機 >*: files\ Microsoft BizTalk Accelerator for SWIFT\<版本 > 訊息Pack\SWIFT Messages\A4SWIFT SRG\<版本 > \Base 原則包含在雙引號中。</span><span class="sxs-lookup"><span data-stu-id="57189-186">The SQL Server name, BIC database name, and integrated security value in the BIC_Master_Policy.xml file in *\<drive>*:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version>\Base Policies are contained in double quotes.</span></span> <span data-ttu-id="57189-187">若要啟用 BIC 驗證，您輸入這些字串在預設 BIC_Master_Policy.xml 檔中所述[啟用驗證的銀行識別項代碼](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)。</span><span class="sxs-lookup"><span data-stu-id="57189-187">To enable BIC validation, you enter these strings in the default BIC_Master_Policy.xml file as described in [Enabling Validation of Bank Identifier Codes](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md).</span></span>  
  
### <a name="solution"></a><span data-ttu-id="57189-188">方案</span><span class="sxs-lookup"><span data-stu-id="57189-188">Solution</span></span>  
 <span data-ttu-id="57189-189">若要修復 BIC 主要原則，請繼續進行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="57189-189">To repair the BIC master policy, proceed as follows:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57189-190">如需部署 BIC 主要原則的詳細資訊，請參閱[部署 BRE 規則](../../adapters-and-accelerators/accelerator-swift/deploying-bre-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="57189-190">For more information about deploying the BIC master policy, see [Deploying BRE Rules](../../adapters-and-accelerators/accelerator-swift/deploying-bre-rules.md).</span></span>  
  
1.  <span data-ttu-id="57189-191">在商務規則編輯器 」，BIC_Master_Policy 的 1.0 版解除部署，然後刪除 BIC_Master_Policy。</span><span class="sxs-lookup"><span data-stu-id="57189-191">In Business Rule Composer, undeploy Version 1.0 of the BIC_Master_Policy, and then delete the BIC_Master_Policy.</span></span>  
  
2.  <span data-ttu-id="57189-192">在文字編輯器中，例如 [記事本] 開啟中的 BIC_Master_Policy.xml *\<磁碟機 >*: files\ Microsoft BizTalk Accelerator for SWIFT\<版本 > 訊息 Pack\SWIFT Messages\A4SWIFT-SRG\<版本 > \Base 原則。</span><span class="sxs-lookup"><span data-stu-id="57189-192">In a text editor, such as Notepad, open BIC_Master_Policy.xml in *\<drive>*:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version>\Base Policies.</span></span> <span data-ttu-id="57189-193">移除 SQL Server 名稱前後使用雙引號、 BIC 資料庫名稱和整合式安全性值。</span><span class="sxs-lookup"><span data-stu-id="57189-193">Remove the double quotes around the SQL Server name, BIC database name, and integrated security value.</span></span>  
  
3.  <span data-ttu-id="57189-194">在商務規則引擎部署精靈，請匯入 BIC_Master_Policy.xml，，然後再部署 BIC_Master_Policy.xml。</span><span class="sxs-lookup"><span data-stu-id="57189-194">In the Business Rules Engine Deployment Wizard, import BIC_Master_Policy.xml, and then deploy BIC_Master_Policy.xml.</span></span>  
  
4.  <span data-ttu-id="57189-195">在 [服務] MMC 中，重新啟動 「 規則引擎更新服務和 BizTalk 接收主控件服務。</span><span class="sxs-lookup"><span data-stu-id="57189-195">In the Services MMC, restart the Rule Engine Update Service and the BizTalk Receive Host Service.</span></span>  
  
## <a name="a4swift-will-not-be-able-to-process-an-unparsed-message-without-proper-database-permissions"></a><span data-ttu-id="57189-196">A4SWIFT 將無法處理未剖析的訊息沒有適當的資料庫權限</span><span class="sxs-lookup"><span data-stu-id="57189-196">A4SWIFT will not be able to process an unparsed message without proper database permissions</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="57189-197">徵兆</span><span class="sxs-lookup"><span data-stu-id="57189-197">Symptom</span></span>  
 <span data-ttu-id="57189-198">當您卸除 A4SWIFT 無法剖析訊息時，A4SWIFT 無法處理訊息，但失敗，發生無法攔截的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="57189-198">When you drop a message that A4SWIFT cannot parse, A4SWIFT is unable to process the message, but fails with an uncaught exception.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="57189-199">可能的原因</span><span class="sxs-lookup"><span data-stu-id="57189-199">Possible Cause</span></span>  
 <span data-ttu-id="57189-200">沒有資料庫權限問題。</span><span class="sxs-lookup"><span data-stu-id="57189-200">There is a database permission issue.</span></span> <span data-ttu-id="57189-201">BizTalk 服務，其預設值是 HostSvc，登入帳戶未納入 A4SWIFT 系統管理員和 A4SWIFT 使用者群組。</span><span class="sxs-lookup"><span data-stu-id="57189-201">The Log On account for the BizTalk service, which by default is HostSvc, is not included in the A4SWIFT Administrators and A4SWIFT Users groups.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="57189-202">方案</span><span class="sxs-lookup"><span data-stu-id="57189-202">Solution</span></span>  
 <span data-ttu-id="57189-203">將 BizTalk 服務的登入帳戶加入至 A4SWIFT 系統管理員 和 A4SWIFT 使用者群組。</span><span class="sxs-lookup"><span data-stu-id="57189-203">Add the Log On account for the BizTalk service to the A4SWIFT Administrators and A4SWIFT Users groups.</span></span>  
  
## <a name="a-timeout-of-the-infopath-repair-form-can-result-in-two-copies-of-a-message-in-different-stages-of-the-repair-workflow"></a><span data-ttu-id="57189-204">InfoPath 修復表單的逾時可能會導致訊息的兩個複本中不同階段的修復工作流程</span><span class="sxs-lookup"><span data-stu-id="57189-204">A timeout of the InfoPath repair form can result in two copies of a message in different stages of the repair workflow</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="57189-205">徵兆</span><span class="sxs-lookup"><span data-stu-id="57189-205">Symptom</span></span>  
 <span data-ttu-id="57189-206">當提交訊息，以從 InfoPath 表單 （適用於任何工作流程階段），如果提交表單中的錯誤時，錯誤可能會導致兩個訊息的複本。</span><span class="sxs-lookup"><span data-stu-id="57189-206">When you submit a message from an InfoPath form (for any workflow stage), if there is an error in submission of the form, the error could result in two copies of message.</span></span> <span data-ttu-id="57189-207">一個訊息仍然會在收件匣的目前階段，而且其他訊息是在工作流程中的下一個角色的收件匣中。</span><span class="sxs-lookup"><span data-stu-id="57189-207">One message is still in the inbox for the current stages, and the other message is in the inbox for the next role in the workflow.</span></span> <span data-ttu-id="57189-208">嘗試處理這些訊息將會產生下列：</span><span class="sxs-lookup"><span data-stu-id="57189-208">Attempting to process these messages will result in the following:</span></span>  
  
-   <span data-ttu-id="57189-209">如果您送出工作流程的下一個角色的收件匣中的訊息，訊息會繼續透過工作流程。</span><span class="sxs-lookup"><span data-stu-id="57189-209">If you submit the message from the inbox for the next role of the workflow, the message will continue through the workflow.</span></span>  
  
-   <span data-ttu-id="57189-210">如果從下一個階段的收件匣提交的訊息已完成的處理之後，您可以提交目前階段的收件匣訊息，從目前的收件匣已提交的郵件將被擱置路由失敗。</span><span class="sxs-lookup"><span data-stu-id="57189-210">If you submit the message from the inbox for the current stage after the message submitted from the inbox of the next stage has completed processing, the message submitted from the current inbox will be suspended with a routing failure.</span></span>  
  
-   <span data-ttu-id="57189-211">如果您提交收件匣訊息目前階段才能提交下一個階段的收件匣中的訊息已完成處理，從收件匣提交目前階段將會傳回訊息的收件匣該階段中，而您將收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="57189-211">If you submit the message in the inbox for the current stage before the message submitted from the inbox of the next stage has completed processing, the message submitted from the inbox for the current stage will be returned to the inbox for that stage, and you will receive the following error:</span></span>  
    <span data-ttu-id="57189-212">「 重設工作流程，原因為： 訊息已遭竄改或使用者為此階段不正確。 」</span><span class="sxs-lookup"><span data-stu-id="57189-212">"Resetting workflow due to: either the message was tampered with or the user is invalid for this stage."</span></span>  
    <span data-ttu-id="57189-213">在此之後，如果您提交下一個階段中，要從收件匣訊息的工作流程會也重設。</span><span class="sxs-lookup"><span data-stu-id="57189-213">After this, if you submit the message from the inbox for the next stage, the workflow for it will also be reset.</span></span> <span data-ttu-id="57189-214">將收件匣中傳回目前階段，您將收到上述錯誤。</span><span class="sxs-lookup"><span data-stu-id="57189-214">It will be returned to the inbox for the current stage and you will receive the above error.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="57189-215">可能的原因</span><span class="sxs-lookup"><span data-stu-id="57189-215">Possible Cause</span></span>  
 <span data-ttu-id="57189-216">InfoPath 表單已送出的訊息，BizTalk Server 透過 Microsoft Windows Sharepoint Services 和自訂的 Web 服務會執行驗證。</span><span class="sxs-lookup"><span data-stu-id="57189-216">The InfoPath form has submitted the message to BizTalk Server via Microsoft Windows Sharepoint Services and a custom Web service that performs validations.</span></span> <span data-ttu-id="57189-217">提交訊息完成多個步驟中，這些步驟不是交易式，因為 Windows Sharepoint Services 並不是交易。</span><span class="sxs-lookup"><span data-stu-id="57189-217">Submitting a message is accomplished in multiple steps and these steps are not transactional, because Windows Sharepoint Services is not transactional.</span></span> <span data-ttu-id="57189-218">為了配合這項限制，MRSR 協調流程有內建的復原邏輯，以偵測並從所引發的訊息提交的錯誤中復原。</span><span class="sxs-lookup"><span data-stu-id="57189-218">To accommodate this limitation, the MRSR orchestrations have built in recovery logic to detect and recover from errors arising from the message submission.</span></span> <span data-ttu-id="57189-219">MRSR 協調流程一定會避免重複的訊息傳送至 SWIFT。</span><span class="sxs-lookup"><span data-stu-id="57189-219">The MRSR orchestrations always prevent duplicate messages being sent to SWIFT.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="57189-220">方案</span><span class="sxs-lookup"><span data-stu-id="57189-220">Solution</span></span>  
 <span data-ttu-id="57189-221">如果發生這種情況，您應該挑選更深層的工作流程中的訊息，並完成其工作流程，然後再嘗試將處理工作流程稍早階段中的訊息。</span><span class="sxs-lookup"><span data-stu-id="57189-221">If this occurs, you should pick the message that is further along in the workflow and complete its workflow before attempting to process the other messages that are in the earlier stages of the workflow.</span></span> <span data-ttu-id="57189-222">工作流程中更深層的訊息處理完成之後，您可以處置的第二個訊息 （暫止與路由失敗） 適當地。</span><span class="sxs-lookup"><span data-stu-id="57189-222">After the message that is further along in the workflow has completed processing, you can dispose of the second message (which was suspended with a routing failure) as you see fit.</span></span>  
  
 <span data-ttu-id="57189-223">如果訊息是進一步沿著工作流程中未完成處理在處理第二個訊息之前，應該再次修復途中修復 InfoPath 表單中的工作流程的訊息，然後送出。</span><span class="sxs-lookup"><span data-stu-id="57189-223">If the message that is further along in the workflow did not complete processing before you processed the second message, you should once again repair the message that is further along in the workflow in the repair InfoPath form, and then submit it.</span></span> <span data-ttu-id="57189-224">允許完成處理，並再送出第二個訊息。</span><span class="sxs-lookup"><span data-stu-id="57189-224">Allow it to complete processing, and then submit the second message.</span></span> <span data-ttu-id="57189-225">第二個訊息被擱置時，會處置它。</span><span class="sxs-lookup"><span data-stu-id="57189-225">After the second message has been suspended, dispose of it.</span></span>  
  
## <a name="a-new-submission-with-no-verify-stage-will-result-in-a-suspended-message"></a><span data-ttu-id="57189-226">沒有驗證階段與新送出將導致擱置的訊息</span><span class="sxs-lookup"><span data-stu-id="57189-226">A new submission with no verify stage will result in a suspended message</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="57189-227">徵兆</span><span class="sxs-lookup"><span data-stu-id="57189-227">Symptom</span></span>  
 <span data-ttu-id="57189-228">當您提交新的訊息沒有驗證階段的工作流程中時，則會擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="57189-228">When you submit a new message in a workflow that has no verify stage, the message is suspended.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="57189-229">可能的原因</span><span class="sxs-lookup"><span data-stu-id="57189-229">Possible Cause</span></span>  
 <span data-ttu-id="57189-230">若 A4SWIFT_MRSRLastStage 未設定為建立驗證階段缺乏導致擱置的訊息。</span><span class="sxs-lookup"><span data-stu-id="57189-230">The lack of a verify stage results in a suspended message if A4SWIFT_MRSRLastStage is not set to Create.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="57189-231">方案</span><span class="sxs-lookup"><span data-stu-id="57189-231">Solution</span></span>  
 <span data-ttu-id="57189-232">使用訂閱的 A4SWIFT_MRSRLastStage = = 建立，以便確保會正確路由訊息。</span><span class="sxs-lookup"><span data-stu-id="57189-232">Use a subscription of A4SWIFT_MRSRLastStage == Create to ensure that the message is routed properly.</span></span>  
  
## <a name="validation-of-message-results-a-parse-error-in-the-infopath-form-task-pane"></a><span data-ttu-id="57189-233">「 剖析錯誤 」 的 InfoPath 表單工作窗格中的訊息驗證結果</span><span class="sxs-lookup"><span data-stu-id="57189-233">Validation of message results a "parse error" in the InfoPath form task pane</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="57189-234">徵兆</span><span class="sxs-lookup"><span data-stu-id="57189-234">Symptom</span></span>  
 <span data-ttu-id="57189-235">驗證在 InfoPath 表單工作窗格會顯示 「 剖析錯誤 」 沒有任何描述中的 [郵件] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="57189-235">Validate Message button in the InfoPath form task pane shows “parse error” without any description.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="57189-236">方案</span><span class="sxs-lookup"><span data-stu-id="57189-236">Solution</span></span>  
 <span data-ttu-id="57189-237">重新啟動 MRSR web 服務或執行 iisreset。</span><span class="sxs-lookup"><span data-stu-id="57189-237">Restart the MRSR web service or do iisreset.</span></span>  
  
## <a name="publishing-an-infopath-form-results-an-authorization-error"></a><span data-ttu-id="57189-238">InfoPath 表單發佈結果授權錯誤</span><span class="sxs-lookup"><span data-stu-id="57189-238">Publishing an InfoPath form results an authorization error</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="57189-239">徵兆</span><span class="sxs-lookup"><span data-stu-id="57189-239">Symptom</span></span>  
 <span data-ttu-id="57189-240">InfoPath 表單發佈提供授權錯誤。</span><span class="sxs-lookup"><span data-stu-id="57189-240">Publishing an InfoPath form gives authorization error.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="57189-241">方案</span><span class="sxs-lookup"><span data-stu-id="57189-241">Solution</span></span>  
 <span data-ttu-id="57189-242">機器名稱取代 localhost MRSR 站台 URL 中。</span><span class="sxs-lookup"><span data-stu-id="57189-242">Replace machine name by localhost in the MRSR site URL.</span></span>  
  
## <a name="infopath-form-task-pane-shows-html-source-code"></a><span data-ttu-id="57189-243">InfoPath 表單工作窗格會顯示 HTML 程式碼</span><span class="sxs-lookup"><span data-stu-id="57189-243">InfoPath form task pane shows HTML source code</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="57189-244">徵兆</span><span class="sxs-lookup"><span data-stu-id="57189-244">Symptom</span></span>  
 <span data-ttu-id="57189-245">InfoPath 表單工作窗格會顯示而不是 Web 控制項的 HTML 原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="57189-245">InfoPath form task pane shows HTML source code instead of Web controls.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="57189-246">方案</span><span class="sxs-lookup"><span data-stu-id="57189-246">Solution</span></span>  
 <span data-ttu-id="57189-247">移至**工具**-> **安全性 索引標籤** -> **網際網路區域**，並啟用**內容為基礎的開啟檔案不是在擴充**底下其他。</span><span class="sxs-lookup"><span data-stu-id="57189-247">Go to **Tools**-> **Security Tab** -> **Internet Zone**, and enable **Open file based on content not on extension** under Miscellaneous.</span></span>  
  
## <a name="profile-web-client-website-results-an-authentication-error"></a><span data-ttu-id="57189-248">設定檔的 Web 用戶端的網站會產生驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="57189-248">Profile Web Client website results an Authentication error</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="57189-249">徵兆</span><span class="sxs-lookup"><span data-stu-id="57189-249">Symptom</span></span>  
 <span data-ttu-id="57189-250">設定檔的 Web 用戶端的網站會顯示驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="57189-250">Profile Web Client website displays Authentication error.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="57189-251">方案</span><span class="sxs-lookup"><span data-stu-id="57189-251">Solution</span></span>  
 <span data-ttu-id="57189-252">執行**BTSharePointAdapterWSAppPool**和**DefaultAppPoolApplication** -> ，以及系統管理員帳戶的集區中 網際網路資訊 Services(IIS)。</span><span class="sxs-lookup"><span data-stu-id="57189-252">Run the **BTSharePointAdapterWSAppPool** and **DefaultAppPoolApplication** -> and pool in Internet Information Services(IIS) under the administrator account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57189-253">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57189-253">See Also</span></span>  
 [<span data-ttu-id="57189-254">疑難排解： 問題與解決方式</span><span class="sxs-lookup"><span data-stu-id="57189-254">Troubleshooting: Issues and Resolutions</span></span>](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)