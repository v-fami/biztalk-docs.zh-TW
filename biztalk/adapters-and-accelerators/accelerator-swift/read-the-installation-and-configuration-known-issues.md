---
title: "讀取的安裝和設定的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c58d9dcb-7835-4181-a6cb-203c5d138e6a
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a09ff5969cc0c47da6a9e885118e227cc27c4ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="read-the-installation-and-configuration-known-issues"></a>讀取的安裝和設定的已知問題
  
## <a name="installing-over-terminal-server-creates-log-files-in-a-different-folder"></a>透過終端機伺服器安裝在不同的資料夾會建立記錄檔  
 當您安裝 A4SWIFT 透過終端機伺服器連線時，A4SWIFT 安裝程式會建立的安裝和組態記錄檔中*\<磁碟機 >*: \Documents and 設定\\ *\<使用者名稱 >*\Local Settings 資料夾。 一般來說，安裝程式會建立這些檔案中的*\<磁碟機 >*: \Documents and 設定\\*\<使用者名稱 >*\Local Settings\temp 資料夾。 您可以檢閱這些記錄檔，以確保您的電腦可以設定並正確設定。  
  
## <a name="silent-installation-is-not-recommended"></a>不建議使用無訊息安裝  
 無訊息安裝 A4SWIFT 安裝程式，支援，但不是建議使用複雜的所需的其他組態步驟。  
  
## <a name="a4swift-setup-runs-with-the-installplatform-argument-that-overwrites-dlls-for-visualstudionet"></a>A4SWIFT 安裝程式會執行與 /InstallPlatform 引數的 VisualStudio.Net 覆寫 Dll  
 /InstallPlatform 引數永遠會執行 A4SWIFT 安裝程式。 如此一來，A4SWIFT 安裝程式一定會安裝 msvcr71.dll、 mfc71u.dll、 msvcp71.dll，與 atl71.dll，所需的[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 A4SWIFT 安裝程式會安裝這些 DLL 檔案至 %WINDIR%\System32 資料夾中，是否不論先前安裝的 Dll。  
  
## <a name="canceling-a4swift-configuration-will-fail"></a>取消 A4SWIFT 組態將會失敗  
 按一下**取消**期間 A4SWIFT 組態不會取消設定。 設定程序會繼續直到完成為止。  
  
## <a name="after-unconfiguring-a4swift-you-cannot-reconfigure-in-the-same-instance-of-the-configuration-console"></a>之後取消設定 A4SWIFT，您無法重新設定相同的執行個體的 [設定] 主控台中  
 如果您取消設定 A4SWIFT、 或的 A4SWIFT 元件時，您無法重新 A4SWIFT 或其元件設定不需要先關閉 A4SWIFT 組態主控台中，再後再重新開啟它。 如果不這樣做，某些欄位的 [設定] 主控台將會呈現灰色，並不能為其選取值。  
  
## <a name="configuration-of-a-web-components-only-installation-will-succeed-even-if-no-a4swift-database-exists"></a>即使 A4SWIFT 資料庫不存在，也會成功設定 Web 元件僅限安裝  
 如果您執行只 Message Repair 和 New Submission 功能的 Web 元件的自訂安裝，然後執行 Microsoft BizTalk Accelerator for SWIFT 組態精靈將即使已成功完成 「 組態 」 程式雖然沒有 A4SWIFT 資料庫。  
  
 A4SWIFT 資料庫將會顯示在**Web 元件 Message Repair 和 New Submission**窗格的 [A4SWIFT 組態] 對話方塊，即使該資料庫不存在。 警告將會顯示 A4SWIFT 資料中的資料庫會儲存窗格中，但警告會防止繼續設定程序。  
  
## <a name="upgrade-process-does-not-create-a-new-root-folder"></a>升級程序不會建立新的根資料夾  
 升級程序更新現有的 A4SWIFT 檔案*\<磁碟機 >*: \Program Files\Microsoft BizTalk Accelerator for A4SWIFT 2.3/3.0 資料夾。 不會建立新的資料夾，針對升級的檔案，也不會改變現有的資料夾名稱*\<磁碟機 >*: \Program Files\Microsoft BizTalk Accelerator for SWIFT。  
  
## <a name="canceling-setup-during-an-upgrade-for-a4swift-may-leave-your-system-in-an-unknown-state"></a>取消安裝程式在升級期間，如 A4SWIFT 可能會使您的系統處於不明狀態  
 在某些情況下，按一下**取消**按鈕，在升級期間可能會保留檔案、 組件、 BizTalk Server 成品和登錄機碼之後，安裝程式已完成其復原。  
  
 您可以順利地以手動方式移除所有項目。  
  
## <a name="download-the-a4swift-setup-exe-file-from-the-web-into-a-temp-folder"></a>從 Web 下載 A4SWIFT 安裝 exe 檔案至暫存資料夾  
 如果您要安裝 A4SWIFT 自我解壓縮的可執行檔，您從 Web 下載，請務必下載該檔案至暫存資料夾。 不要下載檔案放在 BizTalk 伺服器根資料夾 (BizTalk Server \Program Files\Microsoft \<*版本*>)。  
  
 如果您在 BizTalk 伺服器根資料夾中執行 exe 檔案，它會執行 BizTalk Server 安裝精靈中，不是 A4SWIFT 安裝精靈。  
  
## <a name="installing-a4swift-in-a-location-other-than-the-default-requires-changes-to-the-bredeploymentexeconfig-file"></a>預設值以外的位置安裝 A4SWIFT 需要變更過的 BREDeployment.exe.config 檔案  
 如果您安裝 BizTalk Accelerator for SWIFT 路徑以外的預設路徑 %programfiles%\Microsoft BizTalk Accelerator for SWIFT，您必須編輯過的 BREDeployment.exe.config 檔案，以反映正確的路徑產品 SDK\Tools 子目錄中BasePoliciesDirectory、 SchemasDirectory，和 VocabularyDirectory。  
  
 您必須進行這項變更，然後再嘗試將部署 SWIFT 的結構描述包含在您的專案，若要成功部署的相關規則和詞彙相關聯的規則。  
  
## <a name="message-repair-is-not-supported-for-certain-batched-message-scenarios"></a>特定批次的訊息的情況下不支援訊息修復  
 A4SWIFT 訊息修復僅支援批次處理案例的片段。 在這些情況下，您可以修復只有批次訊息的交換部分。  
  
## <a name="you-cannot-submit-a-fixed-unparsed-message-from-a-mrsr-site-library-named-anything-other-than-unparsed"></a>您無法送出固定的未剖析的訊息，從名為 Unparsed 以外的任何 MRSR 站台程式庫  
 當您嘗試送出您修正從 MRSR 網站文件庫名稱不是"Unparsed"剖析的訊息時，操作失敗，因為 A4SWIFT 無法成功送出訊息，以從程式庫不是名為"Unparsed。 」  
  
 如果您在現有的 「 剖析 」 文件庫 MRSR 站台安裝的訊息修復和重新調整功能之前，A4SWIFT 安裝程式會建立標題為 「 剖析 」 具有後置詞的訊息未剖析的程式庫。  
  
 當 A4SWIFT 收到無法剖析訊息時，它會將訊息路由至安裝程式建立的文件庫中。 不過，當您嘗試送出訊息，以從該程式庫時，作業將會失敗。  
  
 如果您 uninstal A4SWIFT 並不會從 MRSR 網站移除 「 剖析 」 文件庫，通常就會發生此問題。  重新 SWIFT 安裝在這些情況下，當安裝程式會建立新的文件庫名稱"Unparsed"後置詞。 」  
  
 若要解決此問題，請遵循此程序：  
  
#### <a name="to-name-a-library-unparsed-in-order-to-submit-unparsed-messages"></a>命名文件庫 」 Unparsed 」 才能提交未剖析的訊息  
  
1.  移除訊息修復和重新調整功能。  
  
2.  手動刪除未剖析的文件庫。 這並不會刪除解除安裝 A4SWIFT 時。  
  
3.  重新安裝訊息修復和重新調整。 重新安裝時，文件庫將會建立具有名稱"Unparsed 」，您可以送出固定的未剖析的訊息，透過此文件庫。  
  
## <a name="bredeployment-utility-cannot-deploy-or-undeploy-policies-if-a4swift-vocabularies-are-not-correctly-configured"></a>無法在部署或解除部署原則，如果未正確設定 A4SWIFT 詞彙 BREDeployment 公用程式  
 如果您嘗試使用 BREDeployment.exe 工具，解除部署 A4SWIFT 商務規則引擎原則 BREDeployment.exe 組態檔並未指向正確的詞彙檔案位置，此工具可能會報告錯誤。 如果您變更 BREDeployment.exe 組態檔中的位置，而且新的位置不包含詞彙檔案，就會發生這個問題。 錯誤會通知您找不到詞彙，並設定停止的部署和/或解除部署原則。  
  
 若要解決此問題，請使用標準**商務規則引擎部署精靈**。 UI 的詳細資料[!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)]。
  
## <a name="see-also"></a>另請參閱  
 [已知問題](../../adapters-and-accelerators/accelerator-swift/known-issues5.md)