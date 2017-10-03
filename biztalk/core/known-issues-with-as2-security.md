---
title: "AS2 安全性的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b291e000-630d-49a1-8e19-f76c4dfee294
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1bb633e092ed568bb3817df7be788364934be446
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-as2-security"></a>AS2 安全性的已知問題
本主題描述的安全性的已知的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]AS2 解決方案。  
  
## <a name="the-as2-decoder-will-not-validate-that-a-certificate-is-configured-on-the-host-or-for-the-destination-party"></a>AS2 解碼器不會驗證是否已在主控件上設定憑證或已針對目的合作對象設定憑證  
 只要憑證存放區中已設定訊息的私用憑證，AS2 解碼器就會解密訊息。 不過，AS2 解碼器將不會驗證解密憑證是否與主控件上設定的憑證相同。 收到的訊息可以使用一個以上的憑證加密。  
  
## <a name="storing-as2-messages-in-wire-format-can-lead-to-a-security-issue"></a>以電傳格式儲存 AS2 訊息可能導致安全性問題  
 未使用憑證時，不建議以電傳格式將 AS2 訊息儲存在接收不可否認性的資料庫中。 這樣做可能會導致安全性問題。  
  
## <a name="messages-or-mdns-to-be-stored-in-the-nrr-database-should-be-signed"></a>要儲存在 NRR 資料庫中的訊息或 MDN 必須經過簽署  
 為了確保接收不可否認性，您必須建立相關訊息的真實性和完整性。 建議做法是對訊息使用數位簽章。 因此，如果您設定 AS2 合作對象屬性將訊息或 MDN 儲存在不可否認性的資料庫中，就必須設定 AS2 屬性來簽署要儲存的訊息或 MDN。  
  
## <a name="biztalk-server-will-be-unable-to-decrypt-a-message-saved-in-wire-format-if-the-certificate-is-not-valid"></a>如果憑證無效，BizTalk Server 便無法解密以電傳格式儲存的訊息  
 **徵兆**  
  
 BizTalk Server 無法解密以電傳格式儲存在不可否認性資料庫中的內送 AS2 訊息。  
  
 **可能的原因**  
  
 解密訊息時所需的憑證已過期或已撤銷。 當 AS2 訊息儲存在不可否認性資料庫一段時間後，就可能會發生這種狀況。 這時您可能無法立即存取訊息的有效憑證。  
  
 **解決方式**  
  
 取得有效憑證來解密訊息。  
  
## <a name="the-inner-envelope-of-a-signed-as2-message-must-not-be-changed-after-the-signature-has-been-calculated"></a>計算簽章之後，不可變更已簽署之 AS2 訊息的內部信封  
 簽署 AS2 訊息時，簽章是根據內部信封標頭和內容來計算。 如果在計算簽章之後變更內部信封，簽章便會損毀。 界限標頭 (或界限標頭外的任何內容) 可以變更，但在界限標頭內的任何內容都不可以變更。  
  
## <a name="use-the-same-logon-for-the-in-process-host-instance-and-the-isolated-host-instance-to-ensure-that-personal-store-is-recognized"></a>為內含式主控件執行個體和外掛式主控件執行個體使用相同的登入，確保可辨識個人存放區  
 只有在針對其登入認證與主控件執行個體相關聯的使用者載入使用者設定檔時，個人憑證存放區才能用於訊息處理。 個人存放區是用於簽章和解密憑證 (使用者專屬的私密金鑰)。 預設會為內含式主控件執行個體載入使用者設定檔，但是不會為外掛式主控件執行個體載入使用者設定檔。 您可以讓應用程式針對外掛式主控件載入使用者設定檔。 或者，您也可以為內含式主控件執行個體和外掛式主控件執行個體使用相同的登入，以解決這個問題。  
  
 除了由應用程式載入使用者設定檔，您也可以建立空的服務來載入設定檔。 如需建立空的服務資訊，請參閱[How to： 建立 Windows 服務](http://go.microsoft.com/fwlink/?LinkId=196492)。 您已建立服務之後，開啟 [電腦管理] 對話方塊中，開啟服務的 [屬性] 對話方塊，按一下**登入**索引標籤上，選取**這個帳戶**，輸入所使用的登入名稱隔離的主控件執行個體，並再按**確定**。 您可以接著手動啟動服務以載入該登入使用者的使用者設定檔。  
  
## <a name="the-key-usage-attribute-of-a-certificate-must-match-the-certificates-use"></a>憑證的金鑰使用方式屬性必須符合憑證使用方式  
 AS2 傳輸所使用的憑證必須有憑證預定使用方式的必要屬性。 針對簽署和簽章驗證，憑證的 [金鑰使用方式] 屬性必須是 [數位簽章]。 針對加密和解密，憑證的 [金鑰使用方式] 屬性必須是 [資料編密] 或 [金鑰編密]。 若要確認 [金鑰使用方式] 屬性，請按兩下憑證，然後按一下 [憑證] 對話方塊的 [詳細資料] 索引標籤，再檢查 [金鑰使用方式] 欄位。  
  
## <a name="the-certificate-resolution-list-will-be-verified-for-an-outgoing-mdn-if-the-as2-to-property-is-not-set-for-the-party"></a>如果未設定合作對象的 AS2-To 屬性，則會針對外寄 MDN 驗證憑證解析清單  
 在外寄 MDN 的預設協議中，會執行憑證解析清單驗證。 如果您不要執行此驗證，請確認已設定正確的 AS2-To 合作對象屬性，以便解析接收的合作對象並判斷合作對象屬性。 如此一來，便不會使用預設協議 (會提示要驗證憑證解析清單)。 您也將需要停用 AS2 合作對象屬性 [一般] 頁面上的 [檢查憑證撤銷清單] 屬性。