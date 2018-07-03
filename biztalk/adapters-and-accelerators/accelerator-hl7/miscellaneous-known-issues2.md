---
title: 其他已知的 Issues2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- known issues
ms.assetid: 01cd896f-6c7f-4734-b953-81a92195a5c0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0e845a6a178b66d2a817414666455eb20b5bb4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007855"
---
# <a name="miscellaneous-known-issues"></a>其他已知的問題
本節中的其他錯誤的實用資訊。  
  
## <a name="duplicate-errors-logged-for-the-same-message-segment-sequence-and-field-number"></a>重複的錯誤記錄的相同訊息區段、 序列和欄位的數目  
 如果元件中的複雜資料的欄位的錯誤類型，Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 將會針對每個這類錯誤的一個錯誤報告。 區段識別碼欄位的數目完全相同。 錯誤號碼和描述可能會不同因為 HL7 錯誤報告機制並不支援 reporting 元件和子元件層級的錯誤。  
  
## <a name="segment-sequence-errors"></a>區段的順序錯誤  
 如果遺漏必要的訊息區段，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]報告 」 區段順序錯誤 （非預期的結尾找到的訊息內文） 」 中的訊息，由引擎所剖析的最後一個正確的區段。  
  
## <a name="invalid-error-can-be-recorded-when-the-msh3-header-field-is-structurally-incorrect"></a>結構不正確的 MSH3 標頭欄位時，就可以記錄無效的錯誤  
 結構不正確，MSH3 標頭欄位是否[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]序列化程式無法將 MSH3 欄位內容複製到 MSH5 標頭和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]無法傳送通知 (ACK)。 這可能表示問題是與 MSH5 欄位，而不是 MSH3 欄位。  
  
## <a name="access-database-errors"></a>存取資料庫錯誤  
 HL7 存取資料庫包含下列錯誤：  
  
- 欄位 27 OBR 區段 HL7 V2.3 Access 資料庫中的不正確地被標示為非可重複且必須。 在此發生了變更[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]結構描述欄位的可重複和選擇性的正確值。  
  
- 在資料庫已不正確地標示為 HL7 V2.3 存取 OBX 區段的欄位 2 所需，與欄位 10 OBX 區段 HL7 V2.3 Access 資料庫中的不正確地標示為不可重複。 在 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]結構描述標示為選擇性欄位 2 和欄位 10 會標示為可重複。  
  
- 在資料庫已不正確地標示為 HL7 V2.3.1 存取 OBX 區段的 Field 4 所需。 在此欄位[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]結構描述標示為選擇性的正確。  
  
## <a name="logging-service-account-may-not-have-access-to-databases-that-are-not-created-by-the-setup-program"></a>記錄服務帳戶可能沒有存取權不會建立安裝程式的資料庫  
 當您設定的記錄存放區，以指向新建立的資料庫，安裝程式未建立，新的資料庫可能沒有存取所列的記錄服務帳戶。 請確定記錄服務帳戶具有所有新建立的記錄資料庫的存取權。  
  
## <a name="leading-spaces-not-allowed-in-nm-and-si-data-types"></a>前置 NM 和 SI 資料類型中不允許空格  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 會拒絕 NM 和 SI 資料類型有開頭和尾端空格的執行個體。  
  
## <a name="btahl7-accepts-a-value-of-0-for-hl7-v21-si-data-type"></a>BTAHL7 接受的值為"0"HL7 V2.1 SI 資料類型  
 HL7 V2.1 HL7 標準，值為"0"不是可接受的 SI 資料類型執行個體中。 不過，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]接受 SI 資料類型的執行個體中的有效值為"0"。  
  
## <a name="mismatch-of-source-and-destination-party-namespaces"></a>不相符的來源和目的合作對象命名空間  
 如果在設定的命名空間[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]上的組態檔案總管**驗證** 索引標籤不符合 HL7 V2 來源中的命名空間的結構描述。訊息，序列化程式可能會產生無法清楚地識別問題的錯誤訊息。 這類的錯誤訊息可能表示在找到的區段順序錯誤或訊息內文中非預期的結尾。 如果您無法解釋的錯誤原因，您可以檢查合作對象的命名空間不相符。  
  
## <a name="lack-of-segments-fts-or-bts-results-in-error-but-the-message-still-parses"></a>缺乏區段下，FTS 或 BTS 會導致錯誤，但訊息仍會剖析  
 當[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]解譯器剖析批次訊息包含區段 FHS 或 BHS，但不包含對應區段下，FTS 和/或 BTS，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生錯誤，但仍會剖析訊息。  
  
## <a name="modifying-a-message-header-tag-results-in-multiple-errors"></a>修改訊息標頭標記會導致多個錯誤  
 如果協調流程設計工具修改訊息標頭標記，您可能會看到不是可理解的例如 「 無效的第一個區段 」 或 「 區段順序錯誤 」 的錯誤。  
  
## <a name="configuration-data-can-be-affected-by-other-biztalk-server-applications"></a>設定資料可能會受到其他 BizTalk Server 應用程式  
 如果您在輸入中的自訂資料[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管 中或以程式設計方式透過設定應用程式發展介面 (Api)，自訂資料的資料會儲存在組態資料庫的設定。  您可以使用 「 組態 」 資料庫從其他的 BizTalk 應用程式其他廠商特定的資訊。 如果另一個應用程式會將資料儲存在相同的位置[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態資料，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]資料可能不正確地儲存。 如果發生這種情況，變更儲存體位置的另一個應用程式資料，並儲存[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]再次設定資料。  
  
## <a name="errors-might-not-be-logged-in-the-error-log-due-to-a-size-limitation-of-the-event-log-store"></a>錯誤可能不會記錄在錯誤記錄檔，因為事件記錄檔存放區的大小限制  
 當[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]序列化程式會產生大量的錯誤，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]可能不會記錄的一些錯誤，因為事件記錄檔存放區的大小限制。 您可以檢視所有的錯誤狀況與活動追蹤 (HAT) 工具，但您可能無法檢視錯誤記錄檔中的所有檔案。  
  
## <a name="reinstalling-btahl7-under-a-different-folder-will-cause-the-default-receive-locations-not-to-work"></a>重新 BTAHL7 安裝在不同的資料夾下將原因預設的接收位置不能運作嗎  
 重新 BTAHL7 安裝在不同的資料夾下，會導致 BatchControlPort 或啟動教學課程所建立的連接埠無法正常運作，因為這些連接埠的 Uri （因為參考之前的安裝中） 將不會符合新的資料夾所建立的預設位置安裝程式。 若要使用這些連接埠，您必須更新這些連接埠 [FILE 傳輸屬性] 對話方塊中的資料夾路徑。  
  
 如果在 BizTalk 中的一或多個 MLLP 連接埠存在，解除安裝 BTAHL7 時，將不會移除 MLLP 配接器。 發生此情況，如果您安裝不同的位置處的產品之後，所有新的或舊 MLLP 連接埠將會停止運作。 MLLP 運作，您必須先解除安裝再重新安裝 MLLP 配接器。 如需詳細資訊，請參閱 「 解除安裝期間不會移除 MLLP 配接器 」，在[疑難排解其他問題](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-other-issues.md)。  
  
## <a name="see-also"></a>另請參閱  
 [已知問題](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)