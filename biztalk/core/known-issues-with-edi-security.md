---
title: "EDI 安全性的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d7f68bc-8460-4656-b9f2-955337458d78
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9517f6c5b1aeae06b5989eef12fe269f81a27c74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-edi-security"></a>EDI 安全性的已知問題
本主題描述的安全性的已知的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI 和 AS2 解決方案。  
  
## <a name="biztalk-will-not-suspend-a-signed-message-from-a-party-for-which-no-certificate-is-set"></a>BizTalk 不會擱置來自合作對象 (未設定任何憑證) 的已簽署訊息  
 若您並未在合作對象設定簽章憑證 (位於合作對象之 [合作對象屬性] 頁面的 [憑證] 節點下)，但來自該合作對象的內送訊息已簽署，BizTalk Server 不會擱置該訊息，也不會根據不存在的憑證擲出例外狀況。  
  
 若您覆寫輸入訊息屬性 (位於 [做為 AS2 訊息傳送者的合作對象] 頁面上)，並清除 [訊息應該簽署] 屬性，則 BizTalk Server 會擱置已簽署的內送訊息。  
  
## <a name="access-to-program-files-folder-can-be-limited-to-prevent-file-tampering"></a>可限制程式檔案資料夾的存取，以防檔案遭竄改  
 若含 BizTalk Server 可執行檔和 EDI 結構描述的 [程式檔案] 資料夾可供未經驗證的使用者使用，則這類使用者有可能修改那些檔案。 為了防止此等威脅，您可以使用 [程式檔案] 資料夾的 [存取控制清單] (ACL)，限制只讓信任的使用者存取資料夾。  
  
## <a name="a-schema-with-a-long-field-can-be-susceptible-to-a-denial-of-service-attack"></a>含長欄位的結構描述，可能容易遭拒絕服務攻擊  
 自訂結構描述如果欄位太長，可能容易遭拒絕服務攻擊利用。 隨附的結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不需要大費周章，有的欄位，因此通常不會遭受此等攻擊。  
  
## <a name="message-processing-will-be-aborted-if-a-control-number-exceeds-its-maximum-length"></a>若控制編號超過最大長度，訊息處理會中止  
 交換、群組或交易集之控制編號的最大長度都有限制。 若其中一個控制編號超過最大長度，則單一合作對象該編碼類型之所有訊息的處理都會中止。 其他編碼類型 (例如 EDIFACT，而不是 X12) 的訊息不會受影響。 這可能代表安全性弱點。  
  
 若序號的長度超過最大長度，則使用者必須重新設定受影響的合作對象之 EDI 屬性內的序號。 重新設定編號後，就可以再度處理該編碼類型的所有訊息。  
  
 若是 X12 訊息，控制編號的最大長度為 9 個數字。 若是 EDIFACT 訊息，控制編號的最大長度為三個欄位 14 個數字。  
  
## <a name="using-the-edi-receive-pipeline-with-an-http-adapter-will-leave-the-connection-open-if-no-ack-is-sent"></a>使用具 HTTP 配接器的 EDI 接收管線時，若沒有傳送任何通知，連線會維持開啟  
 若您建立使用 EDIReceive 管線並具有 HTTP 傳輸類型的接收位置，可能會發生安全性問題。 EDIReceive 管線不會產生 HTTP "200 OK" 通知。 若並未傳回 EDI 通知，則不會順利終止連線，而是會維持開啟。 如果超過逾時期間，則連線會逾時。  
  
 這個問題和 AS2EdiREceive 管線無關。  
  
## <a name="an-x12-encoded-message-is-suspended-if-port-based-authentication-is-enabled-and-biztalk-server-does-not-have-access-to-the-authorization-and-security-information"></a>若以連接埠為基礎的驗證已啟用，且 BizTalk Server 無法存取授權和安全性資訊，X12 編碼訊息會遭擱置  
 **徵兆**  
  
 已透過接收埠 (已啟用驗證) 接收訊息，卻無法判斷傳送訊息的合作對象時，BizTalk Server 會擱置該訊息。  
  
 **可能的原因**  
  
 若接收埠已啟用驗證 (已清除接收埠的 [沒有驗證] 屬性)，則 BizTalk Server 需要 "ISA1-2" (授權辨識符號和資訊) 和 "ISA3-4" (安全性辨識符號和資訊) 屬性的設定，才能處理交換。 合作對象的這些屬性，已經在 [合作對象做為交換傳送者] 的 [X12 交換處理屬性] 頁面中設定。 若 BizTalk Server 無法判斷這些屬性的值，就會擱置該訊息。  
  
 發生的情形有兩種。 其一，若 BizTalk Server 無法判斷傳送訊息的合作對象，就會使用 EDI 全域屬性，且無法存取授權和安全性設定， 因此就會擱置該訊息。 其二，若 BizTalk Server 可判斷合作對象，但該合作對象的 ISA1-2 和 ISA3-4 屬性並未設定，BizTalk Server 便無法存取授權和安全性資訊，因此會擱置該訊息。  
  
 **解決方式**  
  
 確保訊息的傳送合作對象一定要可辨識，且合作對象協議內務必定義 ISA1-2 和 ISA3-4 屬性。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 EDI 和 AS2 解決方案](../core/troubleshooting-edi-and-as2-solutions.md)