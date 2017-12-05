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
ms.openlocfilehash: 6d341a7f03c70e1ddcd242d7804b162338798e94
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="message-repair-and-new-submission-troubleshooting"></a>訊息修復和新送出疑難排解
## <a name="a-repaired-message-cannot-be-submitted-if-the-envelope-schema-is-not-deployed"></a>無法送出修復的訊息，如果未部署信封結構描述  
  
### <a name="symptom"></a>徵兆  
 當您嘗試送出的訊息，您已修復，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]會將下列訊息：  
  
 「 配接器無法傳輸的傳送埠時，訊息將"http://mrsrtest:80/StsWebReceive/default.aspx?PartnerId=Unparsed & FolderType = MessagesInbox"。 它會指定此傳送埠的重試間隔後重新傳輸。 詳細資料:"80131600"。 如需詳細資訊，請參閱說明及支援中心在[http://go.microsoft.com/fwlink/?LinkId=142493](http://go.microsoft.com/fwlink/?LinkId=142493)。  
  
### <a name="possible-cause"></a>可能的原因  
 未部署信封結構描述。 這適用於任何 MT*xxx*剖析失敗的任何訊息。  
  
### <a name="solution"></a>方案  
 部署您使用每個訊息結構描述的信封結構描述 (\<磁碟機\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>Message Pack \SWIFT Messages\ A4SWIFT SRG\<版本\>\Category n\MTxxx.xsd) 和未剖析的信封結構描述 (\<磁碟機\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>Message Pack \SWIFT Messages\ A4SWIFT SRG\<版本\>\ 未剖析 Message\EnvelopeUnparsedMessage.xsd)。 如需詳細資訊，請參閱[部署 A4SWIFT 結構描述](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md)。  
  
## <a name="you-cannot-submit-a-fixed-unparsed-message-from-a-mrsr-site-library-named-other-than-unparsed"></a>您無法送出固定的未剖析的訊息，從名為"Unparsed"以外的 MRSR 網站庫  
  
### <a name="symptom"></a>徵兆  
 當您嘗試送出您修正從 MRSR 網站文件庫名稱不是"Unparsed"剖析的訊息時，則作業將會失敗。  
  
### <a name="possible-cause"></a>可能的原因  
 A4SWIFT 無法成功送出訊息，以從程式庫不是名為"Unparsed"。 如果您在現有的"Unparsed 」 文件庫 MRSR 站台安裝 MRSR （訊息修復） 功能之前，A4SWIFT 安裝程式會建立未剖析的訊息加上尾碼標題為 「 Unparsed"的程式庫。 當它收到 A4SWIFT 無法剖析的訊息時，它會將訊息路由傳送至它所建立的文件庫。 不過，當您嘗試送出訊息，以從該程式庫時，作業會失敗。  
  
### <a name="solution"></a>方案  
 移除 MRSR 功能、 刪除未剖析的文件庫，然後再重新安裝 MRSR 功能。  
  
## <a name="cannot-loop-back-a-message-in-a-two-stage-workflow"></a>無法送回兩階段的工作流程中的訊息  
  
### <a name="symptom"></a>徵兆  
 如果您在建立階段和修復階段的工作流程的修復階段拒絕訊息，提交會失敗。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會將訊息路由至 MessageBox，並會將下列的錯誤訊息：  
  
 「 無法重設至工作流程中的第一個階段。"  
  
### <a name="possible-cause"></a>可能的原因  
 已建立階段和修復階段的工作流程不支援訊息回送。  
  
### <a name="solution"></a>方案  
 兩階段的工作流程，加入另一個階段，或取消送出。  
  
## <a name="cannot-open-a-message-in-the-repair-inbox-in-mrsr"></a>無法開啟 MRSR 的修復收件匣中的訊息  
  
### <a name="symptom"></a>徵兆  
 當您嘗試開啟郵件中 MRSR 修復收件匣中時，您會收到下列錯誤訊息快顯視窗中：  
  
 「 無法開啟所要求的登入 'A4SWIFT' 資料庫。 登入失敗。 使用者 ' NT AUTHORITY\NETWORK SERVICE' 的登入失敗。  
  
### <a name="possible-cause"></a>可能的原因  
 登入帳戶 A4SWIFT_MRSR web 服務之下執行的 web 應用程式是網路服務，不在本機或網域帳戶所屬 A4SWIFT 使用者群組。  
  
### <a name="solution"></a>方案  
 變更 web 應用程式執行 A4SWIFT_MRSR web 服務的登入帳戶。  
  
##### <a name="to-change-the-login-account-for-the-web-application-that-the-a4swiftmrsr-web-service-runs-under"></a>若要變更 web 應用程式執行 A4SWIFT_MRSR web 服務的登入帳戶  
  
1.  按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**.  
  
2.  在 IIS 管理員 中，展開 ***\<伺服器名稱\>* （本機電腦）**  節點，**應用程式集區**節點和**Web站台**節點。 展開 [網站] 節點底下**Default Web Site**節點。  
  
3.  預設的網站] 節點下，以滑鼠右鍵按一下**A4SWIFT_MRSR**，然後按一下 [**屬性**。  
  
4.  在 A4SWIFT_MRSR 屬性 對話方塊中，記下的應用程式集區。  
  
5.  在 IIS 管理員 對話方塊的 應用程式集區 節點下，應用程式集區的 A4SWIFT_MRSR，然後按一下右鍵**屬性**。  
  
6.  在\<應用程式集區名稱\>內容] 對話方塊中，按一下 [**識別**附註。 如果**預先定義**按一下和**網路服務**已選取，按一下**可設定**，輸入您的本機或網域帳戶，，，然後輸入您的密碼。 按一下 **[確定]**。  
  
## <a name="a-message-created-in-mrsr-site-on-a-localized-computer-is-not-processed"></a>建立當地語系化的電腦上的 MRSR 站台中的訊息則不會處理  
  
### <a name="symptom"></a>徵兆  
 當工作在當地語系化的平台上執行 A4SWIFT 的英文版上的使用者建立中的訊息[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成中 MRSR，並將訊息提交成功時，訊息似乎是由 Message Repair 和 New Submission協調流程，但不是成功處理。 訊息提交給寄件匣，但 BizTalk 配接器未收取。 任何錯誤或警告會公佈在事件檢視器中，並沒有執行中協調流程執行個體在 HAT 中的記錄。  
  
### <a name="possible-cause"></a>可能的原因  
 輸入 URI 為 STS 的路徑。寄件匣接收位置包含英文名稱，而不是當地語系化的名稱。  
  
### <a name="solution"></a>方案  
 變更 STS 的 URI 位址。寄件匣接收位置，如下所示：  
  
1.  在 BizTalk Server 2009 管理主控台中，展開**BizTalk 群組**，**應用程式**，和**BizTalk Application 1 節點**。  
  
2.  按一下**接收位置**。  
  
3.  按兩下**為 Sts.Outbox.Location**。  
  
4.  在 [接收位置屬性] 對話方塊中，按一下**設定**。  
  
5.  在 [傳輸屬性] 對話方塊中，將取代的值**SharePointSite URL**與當地語系化的對等項目。  
  
6.  按一下**確定**，然後按一下 **確定**。  
  
## <a name="removing-a-role-while-it-is-processing-a-message-results-in-incomplete-removal-of-documents-and-artifacts"></a>移除角色，當它正在處理中移除不完全的文件和成品郵件結果  
  
### <a name="symptom"></a>徵兆  
 當您在設定檔的 Web 用戶端移除的角色時，對話方塊會公佈指出將會移除所有的文件和成品與角色相關聯。 不過，角色不會從 [A4SWIFT 管理] 主控台中的部門移除，而且從 MRSR 不會移除角色的文件資料夾 （收件匣和寄件備份）。 移除合作對象、 傳送埠和與角色相關聯的協議，和角色設定檔已解除部署。  
  
### <a name="possible-cause"></a>可能的原因  
 訊息仍然會在角色的收件匣中 MRSR，而且訊息已在中開啟其[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。  
  
### <a name="solution"></a>方案  
 手動從 MRSR 網站收件匣中，刪除訊息，然後刪除 已移除的角色相關聯的文件庫。 關閉表單並再次移除角色。  
  
## <a name="message-processing-fails-as-a-result-of-an-error-in-the-bic-master-policy"></a>訊息處理失敗，因為 BIC 主要原則中的錯誤  
  
### <a name="symptom"></a>徵兆  
 當您提交訊息，以進行處理時，您會收到下列錯誤：  
  
 「 執行 BicMasterPolicy 時發生錯誤。 檢查有效的值的原則。 」  
  
### <a name="possible-cause"></a>可能的原因  
 SQL Server 名稱、 BIC 資料庫名稱和整合式的安全性的 BIC_Master_Policy.xml 檔案中的值*\<磁碟機\>*: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base 原則包含在雙引號中。 若要啟用 BIC 驗證，您輸入這些字串在預設 BIC_Master_Policy.xml 檔中所述[啟用驗證的銀行識別項代碼](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)。  
  
### <a name="solution"></a>方案  
 若要修復 BIC 主要原則，請繼續進行，如下所示：  
  
> [!NOTE]
>  如需部署 BIC 主要原則的詳細資訊，請參閱[部署 BRE 規則](../../adapters-and-accelerators/accelerator-swift/deploying-bre-rules.md)。  
  
1.  在商務規則編輯器 」，BIC_Master_Policy 的 1.0 版解除部署，然後刪除 BIC_Master_Policy。  
  
2.  在文字編輯器中，例如 [記事本] 開啟中的 BIC_Master_Policy.xml *\<磁碟機\>*: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFTMessages\A4SWIFT SRG\<版本\>\Base 原則。 移除 SQL Server 名稱前後使用雙引號、 BIC 資料庫名稱和整合式安全性值。  
  
3.  在商務規則引擎部署精靈，請匯入 BIC_Master_Policy.xml，，然後再部署 BIC_Master_Policy.xml。  
  
4.  在 [服務] MMC 中，重新啟動 「 規則引擎更新服務和 BizTalk 接收主控件服務。  
  
## <a name="a4swift-will-not-be-able-to-process-an-unparsed-message-without-proper-database-permissions"></a>A4SWIFT 將無法處理未剖析的訊息沒有適當的資料庫權限  
  
### <a name="symptom"></a>徵兆  
 當您卸除 A4SWIFT 無法剖析訊息時，A4SWIFT 無法處理訊息，但失敗，發生無法攔截的例外狀況。  
  
### <a name="possible-cause"></a>可能的原因  
 沒有資料庫權限問題。 BizTalk 服務，其預設值是 HostSvc，登入帳戶未納入 A4SWIFT 系統管理員和 A4SWIFT 使用者群組。  
  
### <a name="solution"></a>方案  
 將 BizTalk 服務的登入帳戶加入至 A4SWIFT 系統管理員 和 A4SWIFT 使用者群組。  
  
## <a name="a-timeout-of-the-infopath-repair-form-can-result-in-two-copies-of-a-message-in-different-stages-of-the-repair-workflow"></a>InfoPath 修復表單的逾時可能會導致訊息的兩個複本中不同階段的修復工作流程  
  
### <a name="symptom"></a>徵兆  
 當提交訊息，以從 InfoPath 表單 （適用於任何工作流程階段），如果提交表單中的錯誤時，錯誤可能會導致兩個訊息的複本。 一個訊息仍然會在收件匣的目前階段，而且其他訊息是在工作流程中的下一個角色的收件匣中。 嘗試處理這些訊息將會產生下列：  
  
-   如果您送出工作流程的下一個角色的收件匣中的訊息，訊息會繼續透過工作流程。  
  
-   如果從下一個階段的收件匣提交的訊息已完成的處理之後，您可以提交目前階段的收件匣訊息，從目前的收件匣已提交的郵件將被擱置路由失敗。  
  
-   如果您提交收件匣訊息目前階段才能提交下一個階段的收件匣中的訊息已完成處理，從收件匣提交目前階段將會傳回訊息的收件匣該階段中，而您將收到下列錯誤：  
    「 重設工作流程，原因為： 訊息已遭竄改或使用者為此階段不正確。 」  
    在此之後，如果您提交下一個階段中，要從收件匣訊息的工作流程會也重設。 將收件匣中傳回目前階段，您將收到上述錯誤。  
  
### <a name="possible-cause"></a>可能的原因  
 InfoPath 表單已送出的訊息，BizTalk Server 透過 Microsoft Windows Sharepoint Services 和自訂的 Web 服務會執行驗證。 提交訊息完成多個步驟中，這些步驟不是交易式，因為 Windows Sharepoint Services 並不是交易。 為了配合這項限制，MRSR 協調流程有內建的復原邏輯，以偵測並從所引發的訊息提交的錯誤中復原。 MRSR 協調流程一定會避免重複的訊息傳送至 SWIFT。  
  
### <a name="solution"></a>方案  
 如果發生這種情況，您應該挑選更深層的工作流程中的訊息，並完成其工作流程，然後再嘗試將處理工作流程稍早階段中的訊息。 工作流程中更深層的訊息處理完成之後，您可以處置的第二個訊息 （暫止與路由失敗） 適當地。  
  
 如果訊息是進一步沿著工作流程中未完成處理在處理第二個訊息之前，應該再次修復途中修復 InfoPath 表單中的工作流程的訊息，然後送出。 允許完成處理，並再送出第二個訊息。 第二個訊息被擱置時，會處置它。  
  
## <a name="a-new-submission-with-no-verify-stage-will-result-in-a-suspended-message"></a>沒有驗證階段與新送出將導致擱置的訊息  
  
### <a name="symptom"></a>徵兆  
 當您提交新的訊息沒有驗證階段的工作流程中時，則會擱置訊息。  
  
### <a name="possible-cause"></a>可能的原因  
 若 A4SWIFT_MRSRLastStage 未設定為建立驗證階段缺乏導致擱置的訊息。  
  
### <a name="solution"></a>方案  
 使用訂閱的 A4SWIFT_MRSRLastStage = = 建立，以便確保會正確路由訊息。  
  
## <a name="validation-of-message-results-a-parse-error-in-the-infopath-form-task-pane"></a>「 剖析錯誤 」 的 InfoPath 表單工作窗格中的訊息驗證結果  
  
### <a name="symptom"></a>徵兆  
 驗證在 InfoPath 表單工作窗格會顯示 「 剖析錯誤 」 沒有任何描述中的 [郵件] 按鈕。  
  
### <a name="solution"></a>方案  
 重新啟動 MRSR web 服務或執行 iisreset。  
  
## <a name="publishing-an-infopath-form-results-an-authorization-error"></a>InfoPath 表單發佈結果授權錯誤  
  
### <a name="symptom"></a>徵兆  
 InfoPath 表單發佈提供授權錯誤。  
  
### <a name="solution"></a>方案  
 機器名稱取代 localhost MRSR 站台 URL 中。  
  
## <a name="infopath-form-task-pane-shows-html-source-code"></a>InfoPath 表單工作窗格會顯示 HTML 程式碼  
  
### <a name="symptom"></a>徵兆  
 InfoPath 表單工作窗格會顯示而不是 Web 控制項的 HTML 原始程式碼。  
  
### <a name="solution"></a>方案  
 移至**工具**-> **安全性 索引標籤** -> **網際網路區域**，並啟用**內容為基礎的開啟檔案不是在擴充**底下其他。  
  
## <a name="profile-web-client-website-results-an-authentication-error"></a>設定檔的 Web 用戶端的網站會產生驗證錯誤  
  
### <a name="symptom"></a>徵兆  
 設定檔的 Web 用戶端的網站會顯示驗證錯誤。  
  
### <a name="solution"></a>方案  
 執行**BTSharePointAdapterWSAppPool**和**DefaultAppPoolApplication** -> ，以及系統管理員帳戶的集區中 網際網路資訊 Services(IIS)。  
  
## <a name="see-also"></a>請參閱  
 [疑難排解：問題與解決方式](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)