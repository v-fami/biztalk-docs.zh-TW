---
title: 已知問題的 EDI 接收處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bbb3fd6a-381b-479e-a9f2-7b6371fac39e
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75ab2769ab4a6eacf885dbf675a6bd3fda371007
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262958"
---
# <a name="known-issues-with-edi-receive-processing"></a>EDI 接收處理的已知問題
本主題說明 EDI 接收管線中已知的處理問題。  
  
## <a name="receive-side-processing-of-trailing-separators-fails"></a>接收端處理尾端分隔符號失敗  
 **徵兆**  
  
 具有尾端分隔符號的交易集會失敗，並針對 X12 編碼訊息會顯示錯誤碼 AK403= 6，針對 EDIFACT 編碼訊息則會顯示錯誤碼 UCM3=4/UCD1=45。  
  
 **可能的原因**  
  
 尾端分隔符號的處理功能未啟用。  
  
 **解決方式**  
  
 開啟傳送訊息之合作對象的 [EDI 屬性]。 在 [EDI 屬性] 對話方塊的 [驗證和通知產生] 頁面中 (針對 X12 或 EDIFACT)，選取 [允許尾端分隔符號]。 按一下這個核取方塊之後，您可以再按一下 [針對尾端分隔符號建立空的 XML 標記]，指定針對中繼 XML 內的尾端分隔符號建立空的 XML 標記。  
  
## <a name="contrl-ack-is-enabled-but-not-generated"></a>CONTRL 通知已啟用，但無法產生  
 **徵兆**  
  
 已核取傳送方合作對象的 [驗證和通知產生] 中的 [產生功能通知] 核取方塊，但 EDI 接收管線未產生 CONTRL 通知。  
  
 **可能的原因**  
  
 CONTRL 訊息包含數個必須從交換複製過來的必要資料元素。 如果交換中的資料元素遺失或語法無效，則接收管線無法產生語法有效的 CONTRL 訊息。  
  
 **解決方式**  
  
 以 CONTRL 通知以外的其他方式報告錯誤狀況。  
  
## <a name="there-was-a-failure-executing-the-receive-pipeline-error-message"></a>「 沒有執行接收管線失敗 」 錯誤訊息  
 **徵兆**  
  
 嘗試執行 AS2 接收管線會產生 80040154 錯誤。  
  
 **可能的原因**  
  
 64 位元主控件執行個體不支援管線。  
  
 **解決方式**  
  
 請將管線與 32 位元主控件產生關聯。  
  
## <a name="an-x12-encoded-message-is-suspended-if-port-based-authentication-is-enabled-and-biztalk-server-does-not-have-access-to-the-authorization-and-security-information"></a>若以連接埠為基礎的驗證已啟用，且 BizTalk Server 無法存取授權和安全性資訊，X12 編碼訊息會遭擱置  
 **徵兆**  
  
 已透過接收埠 (已啟用驗證) 接收訊息，卻無法判斷傳送訊息的合作對象時，BizTalk Server 會擱置該訊息。  
  
 **可能的原因**  
  
 若接收埠已啟用驗證 (已清除接收埠的 [沒有驗證] 屬性)，則 BizTalk Server 需要 "ISA1-2" (授權辨識符號和資訊) 和 "ISA3-4" (安全性辨識符號和資訊) 屬性的設定，才能處理交換。 合作對象的這些屬性，已經在 [合作對象做為交換傳送者] 的 [X12 交換處理屬性] 頁面中設定。 若 BizTalk Server 無法判斷這些屬性的值，就會擱置該訊息。  
  
 發生的情形有兩種。 其一，若 BizTalk Server 無法判斷傳送訊息的合作對象，就會使用 EDI 全域屬性，且無法存取授權和安全性設定， 因此就會擱置該訊息。 其二，若 BizTalk Server 可判斷合作對象，但該合作對象的 ISA1-2 和 ISA3-4 屬性並未設定，BizTalk Server 便無法存取授權和安全性資訊，因此會擱置該訊息。  
  
 **解決方式**  
  
 確保訊息的傳送合作對象一定要可辨識，且合作對象協議內務必定義 ISA1-2 和 ISA3-4 屬性。  
  
## <a name="incorrect-se01-in-a-split-hipaa-subdocument"></a>分割的 HIPAA 子文件中有不正確的 SE01  
 **徵兆**  
  
 交易集結尾 (SE01 欄位) 會提供資料區段 (包括 X12/HIPAA 文件的標頭和結尾區段) 的計數。 然而對於分割的 HIPAA 子文件，EDI 接收管線會套用和原始文件相同的 SE01 值，而非重新計算。  
  
 **可能的原因**  
  
 EDI 接收管線會將原始 HIPAA 文件中的 SE01 值複製到分割的子文件中。  
  
## <a name="error-message-for-duplicate-unb5-or-unh1-is-not-descriptive"></a>重複 UNB5 或 UNH1 的錯誤訊息不具描述性  
 如果 BizTalk Server 收到的訊息內含重複 UNB5 (交換控制編號) 或 UNH1 (交易集參考編號)，它傳送的錯誤碼和描述不會清楚指出問題本質。  
  
## <a name="biztalk-server-will-suspend-a-very-large-interchange-if-it-runs-out-of-memory"></a>如果記憶體不足，BizTalk Server 會擱置非常大的交換  
 BizTalk Server 在剖析非常大的交換時，可能會耗盡記憶體。 因此，它會傳送錯誤並擱置交換。 在 [群組中樞] 頁面中，您將無法檢視此已擱置、非常大之交換的所有內容。 您將能夠看到訊息的初始部分，但 BizTalk Server 會受限於它可以顯示的已擱置交換的資料量。  
  
## <a name="korean-characters-added-to-an-enumeration-in-a-kedifact-schema-must-be-in-unicode"></a>加入 KEDIFACT 結構描述中之列舉的韓文字元必須是 UNICODE 格式  
 當 BizTalk Server 接收內含韓文字元的 KEDIFACT 編碼交換時，它會使用 UNB2 欄位中的字碼頁/字元集值來處理交換。 不過，如果您將具有 ID 資料類型的韓文字元加入列舉以修改 KEDIFACT 結構描述，則必須以 UTF-16 UNICODE 格式加入此值，如結構描述頂端所指定。  
  
## <a name="executing-an-edi-receive-pipeline-from-within-an-orchestration-is-not-supported"></a>不支援從協調流程內執行 EDI 接收管線  
 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您通常可以執行的協調流程中接收 「 運算式 」 圖形內的管線。 這個功能尚未針對 EDIReceive 管線或 AS2EdiReceive 管線進行測試，因此不受支援。  
  
## <a name="biztalk-edi-application-must-not-be-modified"></a>不得修改 BizTalk EDI 應用程式  
 不得修改或刪除 BizTalk EDI 應用程式內的成品。 應用程式一經修改就無法還原，取消設定和重新設定 EDI 與 AS2 的功能也不行。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 處理的已知的問題](../core/known-issues-with-edi-processing.md)   
 [BizTalk Server 如何接收 EDI 訊息](../core/how-biztalk-server-receives-edi-messages.md)   
 [逐步解說 (X12)： 接收 EDI 交換並傳回通知](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)