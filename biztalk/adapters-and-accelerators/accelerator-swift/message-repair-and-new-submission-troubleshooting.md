---
title: Message Repair 和 New Submission 疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting, Message Repair and New Submission
- Message Repair and New Submission, troubleshooting
ms.assetid: bb07a286-6f02-4639-b5fa-a3647e356ac8
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7bbf5114d26f4f3afd56e4a2a020238d4fe44fae
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001479"
---
# <a name="message-repair-and-new-submission-troubleshooting"></a>Message Repair 和 New Submission 疑難排解
## <a name="a-repaired-message-cannot-be-submitted-if-the-envelope-schema-is-not-deployed"></a>無法提交已修復的訊息，若信封結構描述未部署  
  
### <a name="symptom"></a>徵兆  
 當您嘗試提交的訊息，您必須修復，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]將下列訊息：  
  
 「 配接器無法傳輸訊息到傳送埠 」<http://mrsrtest:80/StsWebReceive/default.aspx?PartnerId=Unparsed&FolderType=MessagesInbox>"。 它會指定此傳送埠的重試間隔後重新傳輸。 詳細資料:"80131600 」。 如需詳細資訊，請參閱 說明及支援中心，在[ http://go.microsoft.com/fwlink/?LinkId=142493 ](http://go.microsoft.com/fwlink/?LinkId=142493)。  
  
### <a name="possible-cause"></a>可能的原因  
 信封結構描述不會部署。 這適用於任何 MT*xxx*訊息或任何具有無法剖析的訊息。  
  
### <a name="solution"></a>方案  
 部署您使用每個訊息結構描述的信封結構描述 (\<磁碟機\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>Message Pack \SWIFT Messages\ A4SWIFT SRG\<版本\>\Category n\MTxxx.xsd) 和未剖析的信封結構描述 (\<磁碟機\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>Message Pack \SWIFT Messages\ A4SWIFT SRG\<版本\>\ 未剖析的 Message\EnvelopeUnparsedMessage.xsd)。 如需詳細資訊，請參閱 <<c0> [ 部署 A4SWIFT 結構描述](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md)。  
  
## <a name="you-cannot-submit-a-fixed-unparsed-message-from-a-mrsr-site-library-named-other-than-unparsed"></a>您無法提交從 MRSR 站台的程式庫，名為"Unparsed"以外的已修正未剖析的訊息  
  
### <a name="symptom"></a>徵兆  
 當您嘗試提交未剖析的訊息，您已修正從 MRSR 網站文件庫不是名為"Unparsed"時，則作業會失敗。  
  
### <a name="possible-cause"></a>可能的原因  
 A4SWIFT 無法成功提交從程式庫不是名為"Unparsed 」 訊息。 如果有現有"Unparsed 」 文件庫 MRSR 站台中安裝 MRSR （訊息修復） 功能之前，A4SWIFT 安裝程式會建立未剖析的訊息標題 「 Unparsed"後置詞的程式庫。 當它收到一則訊息，A4SWIFT 無法剖析時，它會將訊息路由傳送至它所建立的文件庫。 不過，當您嘗試提交訊息，以從該程式庫，則作業將會失敗。  
  
### <a name="solution"></a>方案  
 移除 MRSR 功能、 刪除未剖析的文件庫，然後再重新安裝 MRSR 功能。  
  
## <a name="cannot-loop-back-a-message-in-a-two-stage-workflow"></a>無法回迴圈中的兩個階段工作流程的訊息  
  
### <a name="symptom"></a>徵兆  
 如果您已建立階段和修復階段的工作流程的修復階段拒絕訊息，提交會失敗。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 會將訊息路由至 MessageBox，並將下列的錯誤訊息：  
  
 「 無法重設至工作流程中的第一個階段。 」  
  
### <a name="possible-cause"></a>可能的原因  
 已建立階段和修復階段的工作流程不支援訊息的回送。  
  
### <a name="solution"></a>方案  
 將另一個階段新增至兩個階段的工作流程，或取消提交作業。  
  
## <a name="cannot-open-a-message-in-the-repair-inbox-in-mrsr"></a>無法開啟 MRSR 的修復收件匣中的訊息  
  
### <a name="symptom"></a>徵兆  
 當您嘗試開啟 MRSR 的修復收件匣中的訊息時，您會收到下列錯誤訊息快顯視窗中：  
  
 「 無法開啟登入 'A4SWIFT' 所要求的資料庫。 登入失敗。 使用者 ' NT AUTHORITY\NETWORK SERVICE' 的登入失敗。  
  
### <a name="possible-cause"></a>可能的原因  
 登入帳戶下執行 A4SWIFT_MRSR web 服務的 web 應用程式是網路服務，不在本機或網域帳戶位於 A4SWIFT 使用者群組。  
  
### <a name="solution"></a>方案  
 變更執行 A4SWIFT_MRSR web 服務的 web 應用程式的登入帳戶。  
  
##### <a name="to-change-the-login-account-for-the-web-application-that-the-a4swiftmrsr-web-service-runs-under"></a>若要變更執行 A4SWIFT_MRSR web 服務的 web 應用程式的登入帳戶  
  
1.  按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.  
  
2.  在 IIS 管理員 中，展開 ***\<伺服器名稱\>* （本機電腦）**  節點，**應用程式集區**節點和**Web站台**節點。 在 [網站] 節點下展開**Default Web Site**節點。  
  
3.  在 [預設的網站] 節點中，以滑鼠右鍵按一下**A4SWIFT_MRSR**，然後按一下**屬性**。  
  
4.  在 [A4SWIFT_MRSR 屬性] 對話方塊中，記下應用程式集區。  
  
5.  在 IIS 管理員 對話方塊中的 應用程式集區 節點下，應用程式集區的 A4SWIFT_MRSR，然後按一下右鍵**屬性**。  
  
6.  在 [\<應用程式集區名稱\>內容] 對話方塊中，按一下**身分識別**附註。 如果**預先定義**按下並**Network Service**是選取狀態，按一下**可設定**，輸入您的本機或網域帳戶，然後輸入您的密碼。 按一下 [確定] 。  
  
## <a name="a-message-created-in-mrsr-site-on-a-localized-computer-is-not-processed"></a>建立當地語系化的電腦上的 MRSR 站台中的訊息則不會處理  
  
### <a name="symptom"></a>徵兆  
 當工作在當地語系化的平台上執行 A4SWIFT 的英文版上的使用者建立中的訊息[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成 MRSR，並將訊息提交成功，會顯示訊息，可供 Message Repair 和 New Submission協調流程，但未成功處理。 訊息提交給寄件匣，但 BizTalk 配接器未收取。 任何錯誤或警告張貼在事件檢視器，並沒有執行中協調流程執行個體在 HAT 中的記錄。  
  
### <a name="possible-cause"></a>可能的原因  
 輸入 URI 作為 STS 的路徑。寄件匣接收位置包含英文的名稱，而不是當地語系化的名稱。  
  
### <a name="solution"></a>方案  
 變更 STS 的 URI 位址。寄件匣接收位置，如下所示：  
  
1.  在 BizTalk Server 2009 管理主控台中，展開**BizTalk 群組**，**應用程式**，並**BizTalk Application 1 節點**。  
  
2.  按一下 **接收位置**。  
  
3.  按兩下**為 Sts.Outbox.Location**。  
  
4.  在 [接收位置屬性] 對話方塊中，按一下**設定**。  
  
5.  在 [傳輸屬性] 對話方塊中中的值取代**SharePointSite URL**當地語系化的對等。  
  
6.  按一下  **確定**，然後按一下**確定**。  
  
## <a name="removing-a-role-while-it-is-processing-a-message-results-in-incomplete-removal-of-documents-and-artifacts"></a>移除角色，正在處理訊息導致移除不完全的文件和成品  
  
### <a name="symptom"></a>徵兆  
 當您在設定檔 Web 用戶端移除的角色時，對話方塊會公佈指示將會移除所有的文件與角色相關聯的成品。 不過，角色不會從 [A4SWIFT 管理] 主控台中的部門移除，而且從 MRSR 不會移除角色的文件資料夾 （收件匣和寄件備份）。 移除合作對象、 傳送埠和角色相關聯的協議，和角色的設定檔已解除部署。  
  
### <a name="possible-cause"></a>可能的原因  
 訊息仍處於 MRSR 中的收件匣的角色和訊息已在中開啟其[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。  
  
### <a name="solution"></a>方案  
 以手動方式從 MRSR 網站收件匣] 中刪除訊息，然後再刪除 [已移除的角色相關聯的文件庫。 關閉表單，然後再移除角色。  
  
## <a name="message-processing-fails-as-a-result-of-an-error-in-the-bic-master-policy"></a>訊息處理失敗，因為 BIC 主要原則中的錯誤  
  
### <a name="symptom"></a>徵兆  
 當您提交訊息，以進行處理時，您會收到下列錯誤：  
  
 「 執行 BicMasterPolicy 時發生錯誤。 檢查有效的值的原則。 」  
  
### <a name="possible-cause"></a>可能的原因  
 SQL Server 名稱、 BIC 資料庫名稱和 BIC_Master_Policy.xml 檔案中的整合式的安全性價值*\<磁碟機\>*: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base 原則包含在雙引號中。 若要啟用 BIC 驗證，您輸入這些字串在預設 BIC_Master_Policy.xml 檔中所述[啟用驗證的銀行識別代碼](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)。  
  
### <a name="solution"></a>方案  
 若要修復 BIC 主要原則，繼續進行，如下所示：  
  
> [!NOTE]
>  如需部署 BIC 主要原則的詳細資訊，請參閱 <<c0> [ 部署 BRE 規則](../../adapters-and-accelerators/accelerator-swift/deploying-bre-rules.md)。  
  
1.  在商務規則編輯器，請解除部署的 BIC_Master_Policy，1.0 版，然後再刪除 BIC_Master_Policy。  
  
2.  在文字編輯器，例如 記事本，開啟 在 BIC_Master_Policy.xml *\<磁碟機\>*: files\ Microsoft BizTalk Accelerator for SWIFT\<版本\>訊息 Pack\SWIFTMessages\A4SWIFT SRG\<版本\>\Base 原則。 移除 SQL Server 名稱的雙引號，BIC 資料庫名稱，並整合安全性值。  
  
3.  在商務規則引擎部署精靈中，匯入 BIC_Master_Policy.xml，並接著部署 BIC_Master_Policy.xml。  
  
4.  在 [服務] MMC 中，重新啟動 「 規則引擎更新服務 」 和 「 BizTalk 接收主控件服務 」。  
  
## <a name="a4swift-will-not-be-able-to-process-an-unparsed-message-without-proper-database-permissions"></a>A4SWIFT 將無法處理未剖析的訊息不具適當的資料庫權限  
  
### <a name="symptom"></a>徵兆  
 當您卸除 A4SWIFT 無法剖析的訊息時，A4SWIFT 無法處理訊息，但會失敗並發生無法攔截的例外狀況。  
  
### <a name="possible-cause"></a>可能的原因  
 沒有資料庫權限問題。 BizTalk 服務，其預設值是 HostSvc，登入帳戶不會納入 A4SWIFT 系統管理員 和 A4SWIFT 使用者群組。  
  
### <a name="solution"></a>方案  
 BizTalk 服務的登入帳戶加入 A4SWIFT 系統管理員 和 A4SWIFT 使用者群組。  
  
## <a name="a-timeout-of-the-infopath-repair-form-can-result-in-two-copies-of-a-message-in-different-stages-of-the-repair-workflow"></a>InfoPath 修復表單的逾時可能會導致訊息的兩個複本中的修復工作流程的不同階段  
  
### <a name="symptom"></a>徵兆  
 當提交 InfoPath 表單中的訊息 （適用於任何工作流程階段），如果在提交表單中的錯誤時，錯誤可能會導致兩個訊息的複本。 一則訊息是仍在收件匣中的目前階段，而其他訊息為工作流程中的下一個角色的收件匣中。 嘗試處理這些訊息將會產生下列：  
  
-   如果您提交的工作流程的下一個角色的收件匣中的訊息，訊息會繼續執行工作流程。  
  
-   如果提交從下一個階段的收件匣的訊息已完成的處理之後，您可以提交的目前階段的收件匣中的訊息，從目前的收件匣已提交的郵件將被擱置的路由失敗。  
  
-   如果您送出收件匣訊息的目前階段完成提交從下一個階段的收件匣的訊息之前處理提交從收件匣的目前階段將會傳回訊息的收件匣該階段中，和您將會會收到下列錯誤：  
    「 重設工作流程，因為： 訊息已遭竄改，或在這個階段，使用者不正確。 」  
    在此之後，如果您提交下一個階段中，從收件匣訊息的工作流程會也會重設。 將收件匣中傳回目前的階段，您將收到上述錯誤。  
  
### <a name="possible-cause"></a>可能的原因  
 InfoPath 表單已提交至 BizTalk Server 透過 Microsoft Windows Sharepoint Services 和自訂的 Web 服務會執行驗證的訊息。 提交訊息透過多個步驟完成，這些步驟不是交易式，因為 Windows Sharepoint Services 並不是交易。 為了滿足這項限制，MRSR 協調流程具有內建的復原邏輯，以偵測和復原錯誤所造成的訊息提交。 MRSR 協調流程一定會防止重複傳送至 SWIFT 的訊息。  
  
### <a name="solution"></a>方案  
 如果發生這種情況，您應該挑選更深層的工作流程中的訊息，並完成其工作流程，然後再嘗試處理工作流程的早期階段中的訊息。 工作流程中更深層的訊息完成處理之後，您可以處置的第二個訊息 （已暫停，路由失敗） 的適當地。  
  
 如果訊息是進一步沿著工作流程中未完成處理在處理第二個訊息之前，您應該再次修復更深層中修復 InfoPath 表單的工作流程中的訊息，並提交。 完成處理，以允許它，然後提交第二個訊息。 第二個訊息已暫止之後，處置它。  
  
## <a name="a-new-submission-with-no-verify-stage-will-result-in-a-suspended-message"></a>沒有驗證階段與新的提交將會導致擱置的訊息  
  
### <a name="symptom"></a>徵兆  
 當您提交任何驗證階段的工作流程中的新訊息時，則會擱置訊息。  
  
### <a name="possible-cause"></a>可能的原因  
 驗證階段的缺乏會導致擱置的訊息，如果 A4SWIFT_MRSRLastStage 未設定為建立。  
  
### <a name="solution"></a>方案  
 使用訂用帳戶的 A4SWIFT_MRSRLastStage = = 建立以確保會正確地路由訊息。  
  
## <a name="validation-of-message-results-a-parse-error-in-the-infopath-form-task-pane"></a>驗證訊息會產生 「 剖析錯誤 」 在 InfoPath 表單工作窗格  
  
### <a name="symptom"></a>徵兆  
 驗證在 InfoPath 表單工作窗格會顯示 「 剖析錯誤 」 沒有任何描述中的 [郵件] 按鈕。  
  
### <a name="solution"></a>方案  
 重新啟動 MRSR web 服務，或執行 iisreset。  
  
## <a name="publishing-an-infopath-form-results-an-authorization-error"></a>發佈 InfoPath 表單會產生授權錯誤  
  
### <a name="symptom"></a>徵兆  
 發佈 InfoPath 表單，可讓授權錯誤。  
  
### <a name="solution"></a>方案  
 機器名稱取代 localhost MRSR 網站 URL 中。  
  
## <a name="infopath-form-task-pane-shows-html-source-code"></a>InfoPath 表單工作窗格會顯示 HTML 原始碼  
  
### <a name="symptom"></a>徵兆  
 InfoPath 表單工作窗格會顯示 HTML 原始程式碼，而不是 Web 控制項。  
  
### <a name="solution"></a>方案  
 移至**工具**-> **安全性 索引標籤** -> **網際網路區域**，並啟用**內容為基礎的開啟檔案不是在延伸模組**其他底下。  
  
## <a name="profile-web-client-website-results-an-authentication-error"></a>設定檔 Web 用戶端的網站會產生驗證錯誤  
  
### <a name="symptom"></a>徵兆  
 設定檔 Web 用戶端的網站會顯示驗證錯誤。  
  
### <a name="solution"></a>方案  
 執行**BTSharePointAdapterWSAppPool**並**DefaultAppPoolApplication** -> ，以及系統管理員帳戶的集區中 網際網路資訊 Services(IIS)。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解：問題與解決方式](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)