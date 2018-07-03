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
# <a name="known-issues"></a>已知問題
本節包含可協助您避免與 Microsoft 的錯誤的有用資訊[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]。 已知的問題可分為以下各類：  
  
## <a name="message-repair-and-new-submission"></a>Message Repair 和 New Submission

#### <a name="printing-of-a-repair-document-is-recorded-in-the-history-log-even-if-canceled"></a>即使已取消，將會記錄在歷程記錄的列印修復文件  
 如果您執行修復收件匣中的文件的 [列印] 命令，然後取消列印，列印仍然已輸入的歷程記錄。 當您開啟的文件中修復時，發生這種的情況其[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單，按一下 [檔案] 功能表上的 [列印] 命令，然後按一下 [列印] 對話方塊中的 [取消]。 您應該忽略的歷程記錄中的項目。  
  
#### <a name="a-duplicate-signature-can-cause-an-xlangs-error-message"></a>重複的簽章可能會導致 XLANG/s 錯誤訊息  
 當驗證器會使用相同的憑證作為 repairer，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]擱置訊息，並指出錯誤訊息中不允許重複的簽章。 不過，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]也會產生 XLANG/s，指出已暫止的 XLANG/s 服務的事件來源的另一個錯誤訊息。 您可以忽略此訊息。  
  
#### <a name="message-size-can-affect-repair-performance"></a>訊息大小可能會影響修復效能  
 當您開啟中的 XML 檔案時，如果您嘗試修復異常大的 XML 檔案，可以大幅降低系統效能[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]訊息類型的表單。 可能會增加記憶體耗用量、 CPU 耗用量可能會降低，和處理程序可能會失敗並出現錯誤指出沒有足夠的儲存體無法完成作業。  
  
#### <a name="the-last-signature-used-to-sign-a-message-successfully-will-be-authenticated-by-authenticate-signatures"></a>最後一個用來成功地簽署訊息的簽章會經過驗證的簽章  
 按一下 驗證簽章按鈕[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單驗證簽章，您僅如果您已經簽署表單的階段。 否則，它會驗證簽章上一個階段中，如果有的話，並將張貼下列錯誤：  
  
 簽章的使用者未正確設定部門 < department_name > 中 < stage_name > 角色。  
  
 例如，假設您在驗證階段之後立即處於 「 核准 」 階段。 如果尚未簽署形式的核准者，並按一下驗證簽章[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]驗證的簽章驗證器使用，不核准者的簽章，並將張貼先前的錯誤。  

#### <a name="a4swift-cleanup-tool-doesnt-delete-templates"></a>A4SWIFT 清理工具並不會刪除範本  
 A4SWIFT 清理工具不會執行下列作業：  
  
-   移除 MRSR 站台的主要目標的所有範本  
  
-   移除 MRSR 網站中的所有合約和夥伴設定檔  
  
-   移除所有的使用者、 角色和部門  
  
-   取消註冊 MRSR 網站 A4SWIFT BizTalk 伺服器  
  
#### <a name="the-a4swiftmrsrdepartment-property-is-set-to-an-empty-string-for-a-message-that-did-not-parse"></a>A4SWIFT_MRSRDepartment 屬性設為空字串未剖析的訊息。  
 當訊息修復協調流程可將已修正未剖析的訊息路由至 MessageBox 時，它將會設定[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_MRSRDepartment 屬性設為空白字串，並將它升級。 傳送埠不能訂閱此屬性。  
  
#### <a name="cannot-save-a-department-if-the-sso-service-has-been-stopped"></a>無法儲存一個部門，如果 SSO 服務已停止  
 如果您嘗試新增部門，SSO 服務停止時，您會收到錯誤，指出主要 SSO 伺服器\<machinename\>失敗。 請檢查是否已設定 SSO，以及 SSO 服務是否在該伺服器上執行。  
  
#### <a name="a-department-name-must-not-contain-the-character-"></a>部門名稱不能包含字元"~"  
 包含字元的部門名稱"~"A4SWIFT 資料庫將會導致問題。  
  
#### <a name="signing-infopath-forms"></a>簽署 Infopath 表單  
 簽署 InfoPath 表單必須以手動方式完成。  
  
## <a name="security"></a>Security

#### <a name="mixing-trusted-and-untrusted-hosts-can-enable-spoofing"></a>混用受信任和未受信任的主機，可以啟用詐騙  

 它可能詐騙從其他未受信任的繫結的 SWIFT 訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]裝載應用程式。 這是只有問題中混合信任模式下執行時 (當受信任的主機和不受信任的主機執行應用程式在同一個[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]群組)。 您可以使用合作對象解析管線元件來識別 SWIFT 繫結訊息的來源來降低此風險。 在完全信任環境中，或用於大部分的使用案例執行時，這是不必要。 您應該遵循[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]混合時，建置安全的應用程式的指導方針信任和未受信任的主機。 
 
## <a name="miscellaneous"></a>其他

#### <a name="the-cacheentries-setting-may-be-reset-by-a-setup-program-affecting-performance"></a>CacheEntries 設定可能會重設安裝程式會影響效能  
 CacheEntries 登錄機碼決定 「 商務規則引擎更新服務快取的規則集的最大數目。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝程式預設會設定 CacheEntries 為 32。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式變更 HKEY_LOCAL_MACHINE\SOFTWARE\\Microsoft \BusinessRules\3.0\CacheEntries 設為 512，以獲得最佳效能。 不過，在某些情況下，CacheEntries 可能會自動重設。 這可能會影響系統效能。  
  
 規則引擎更新可能會變更 CacheEntries 介於 512 到 32。 安裝規則引擎更新之後，手動重設 CacheEntries 為 512，如有必要。  
  
 即使[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式設為 512，解除安裝 32 設定 CacheEntries[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]無法重設 CacheEntries 介於 512 到 32。  
  
 如需詳細資訊，請參閱 BizTalk Server 說明中的 「 規則引擎組態和調整參數 > 主題。  
  
#### <a name="building-a-pipeline-project-may-result-in-a-large-number-of-warnings"></a>建置管線專案可能會導致大量的警告  
 當您將 SWIFT 組合器新增至傳送管線或 SWIFT 解譯器，接收管線，然後建立包含這些管線的管線專案時，您可能會收到一系列的管線元件相關的警告。 這些警告會指示 Visual Studio 找不到相依性。 您可以更正導致這些警告，如下所示變更 SWIFTAsm 或 SWIFTDasm 中的組件 [參考] 資料夾中，[複製本機] 屬性的條件：  
  
1.  在 Visual Studio 的方案總管，展開您管線的專案，然後再展開**參考**節點。  
  
2.  在 [參考] 節點中，選取**SWIFTAsm**組件和/或**SWIFTDasm**組件。  
  
3.  在 [屬性] 窗格中，將變更的值**複製到本機**屬性設**False**。  
  
4.  您管線的專案，以滑鼠右鍵按一下，然後按一下 **建置**。  
  
    > [!NOTE]
    >  您應該不會看到找不到的相依性有關的任何警告。   