---
title: 其他已知的 Issues2 |Microsoft 文件
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
ms.openlocfilehash: af644ead6ecb825d6d6960145958c176946e844c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207062"
---
# <a name="miscellaneous-known-issues"></a>其他已知的問題
本節中的其他錯誤的相關實用資訊。  
  
## <a name="duplicate-errors-logged-for-the-same-message-segment-sequence-and-field-number"></a>重複記錄的同一個訊息區段、 sequence、 和欄位的數目錯誤  
 如果元件的複雜資料類型的欄位中有錯誤[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 將會報告每一個這類錯誤的一個錯誤。 區段識別碼，欄位號碼將會相同。 錯誤號碼和描述可能會不同因為 HL7 錯誤報告機制並不支援在元件和子元件層級的錯誤。  
  
## <a name="segment-sequence-errors"></a>區段順序錯誤  
 如果遺漏必要的訊息區段，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]報告 」 區段順序錯誤 （結尾找到的訊息內文） 」 中的訊息，由引擎所剖析的最後一個正確的區段。  
  
## <a name="invalid-error-can-be-recorded-when-the-msh3-header-field-is-structurally-incorrect"></a>結構不正確 MSH3 標頭欄位時，可記錄無效的錯誤  
 如果 MSH3 標頭欄位是結構不正確，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]序列化程式無法將 MSH3 欄位內容複製到 MSH5 標頭和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]無法傳送通知 (ACK)。 這可能表示問題是使用 MSH5 欄位，而不是 MSH3 欄位。  
  
## <a name="access-database-errors"></a>存取資料庫錯誤  
 HL7 存取資料庫包含下列錯誤：  
  
-   OBR 區段 HL7 V2.3 Access 資料庫中的欄位 27 已正確地標示為非可重複且需要。 在這已經發生變更[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]為正確的值可重複的和選擇性的欄位結構描述。  
  
-   在資料庫已正確地標示為 HL7 V2.3 存取 OBX 區段的欄位 2 需要，而且欄位 10 OBX 區段 HL7 V2.3 Access 資料庫中的已正確地標示為不可重複。 在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]結構描述標示為選擇性欄位 2 和欄位 10 會標示為可重複。  
  
-   欄位 4 在資料庫已正確地標示為 HL7 V2.3.1 存取 OBX 區段的必要項。 此欄位在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]結構描述標示為正確為選擇性。  
  
## <a name="logging-service-account-may-not-have-access-to-databases-that-are-not-created-by-the-setup-program"></a>記錄服務帳戶可能沒有存取不由安裝程式建立的資料庫  
 當您設定的記錄存放區，以指向新建立的資料庫，安裝程式未建立，新的資料庫可能沒有存取所列的記錄服務帳戶。 請記錄服務帳戶具有所有新建立的記錄資料庫的存取權。  
  
## <a name="leading-spaces-not-allowed-in-nm-and-si-data-types"></a>開頭空白 NM 和 SI 資料類型中不允許  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會拒絕具有開頭和尾端空白 NM 和 SI 資料類型的執行個體。  
  
## <a name="btahl7-accepts-a-value-of-0-for-hl7-v21-si-data-type"></a>BTAHL7 接受值為"0"代表 HL7 V2.1 SI 資料類型  
 HL7 V2.1 HL7 標準，值為"0"不是可接受 SI 資料類型的執行個體中。 不過，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]接受 SI 資料類型的執行個體有效的值為"0"。  
  
## <a name="mismatch-of-source-and-destination-party-namespaces"></a>不相符的來源和目的合作對象命名空間  
 如果在命名空間設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管上**驗證** 索引標籤並不符合 HL7 V2 結構描述中的來源命名空間。X 訊息時，序列化程式可能會產生無法清楚地識別問題的錯誤訊息。 這類的錯誤訊息可能表示區段順序錯誤或非預期的訊息本文結尾找到。 如果您無法解釋的錯誤原因，您可以檢查合作對象的命名空間不相符。  
  
## <a name="lack-of-segments-fts-or-bts-results-in-error-but-the-message-still-parses"></a>缺乏區段下，FTS 或 BTS 會導致錯誤，但訊息仍會剖析  
 當[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]解譯器會剖析包含區段 FHS 或 BHS，但不包含對應的批次訊息區段下，FTS 及/或 BTS，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生錯誤，但仍會剖析訊息。  
  
## <a name="modifying-a-message-header-tag-results-in-multiple-errors"></a>修改訊息標頭標記會導致多個錯誤  
 如果協調流程設計師 」 修改訊息標頭標記，您會看到不易於瞭解，例如 「 無效的第一個區段 」 或 「 區段順序錯誤 」 的錯誤。  
  
## <a name="configuration-data-can-be-affected-by-other-biztalk-server-applications"></a>設定資料可能會受到其他 BizTalk Server 應用程式  
 如果您在輸入中的自訂資料[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管 中或以程式設計方式透過設定應用程式發展介面 (Api)，自訂資料的資料會儲存在組態資料庫的設定組態。  您可以使用 「 組態 」 資料庫從其他的 BizTalk 應用程式的其他合作對象特有資訊。 如果另一個應用程式會將資料儲存在相同的位置[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態資料[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]資料可能不正確地儲存。 如果發生這種情況，變更的其他應用程式資料的儲存位置，並儲存[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]再次設定資料。  
  
## <a name="errors-might-not-be-logged-in-the-error-log-due-to-a-size-limitation-of-the-event-log-store"></a>錯誤可能不會記錄在錯誤記錄檔，因為事件記錄檔存放區的大小限制  
 當[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]序列化程式會產生大量的錯誤，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]可能不會記錄某些錯誤，因為事件記錄檔存放區的大小限制。 您可以在 「 狀況與活動追蹤 (HAT) 工具，檢視所有的錯誤，但您可能無法檢視所有的錯誤記錄檔中。  
  
## <a name="reinstalling-btahl7-under-a-different-folder-will-cause-the-default-receive-locations-not-to-work"></a>重新 BTAHL7 安裝在不同的資料夾會造成預設接收位置不能運作  
 在不同的資料夾下重新安裝 BTAHL7 會導致 BatchControlPort 或啟動教學課程所建立的連接埠不能運作，因為這些連接埠的 Uri （如同在先前安裝中） 不會符合新的資料夾所建立的預設位置安裝程式。 若要使用這些通訊埠，您必須更新這些連接埠的 [FILE 傳輸屬性] 對話方塊中的資料夾路徑。  
  
 如果一或多個 MLLP 連接埠存在於 BizTalk 中解除安裝 BTAHL7 時，將不會移除 MLLP 配接器。 發生此情況，如果您安裝不同的位置處的產品之後，所有新或舊 MLLP 連接埠將會停止運作。 為 MLLP 運作，您必須解除安裝再重新安裝 MLLP 配接器。 如需詳細資訊，請參閱"解除安裝期間不會移除 MLLP 配接器 」 中的[疑難排解其他問題](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-other-issues.md)。  
  
## <a name="see-also"></a>另請參閱  
 [已知問題](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)