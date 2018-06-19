---
title: 在 BizTalk Server 中憑證的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab58264b-2475-4831-9f08-bfbaa293022f
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5aecfca9f58758e72f357439901684a0a617f3c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297574"
---
# <a name="known-issues-with-certificates-in-biztalk-server"></a>在 BizTalk Server 中憑證的已知的問題
本章節描述管理搭配使用的數位簽章的已知的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
## <a name="general-certificate-issues"></a>一般憑證問題  
  
### <a name="lack-of-connectivity-to-the-certificate-revocation-list-will-cause-a-certificate-to-be-rejected"></a>缺乏連線到憑證撤銷清單會遭到拒絕的憑證  
 問題牽涉到下列錯誤: 「 時發生驗證錯誤。 發行用來簽署訊息的憑證的憑證授權單位 (CA) 的狀態是未知的。" 會發生此錯誤，即使簽章憑證是有效檢視下 MMC 時 (使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用者) 上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
 如果接收管線中的 S/MIME 解碼器元件上已啟用 「 檢查憑證撤銷 」 屬性，會發生此狀況。 這個屬性設為 true 時，BizTalk Server 會嘗試將查詢以查看是否已撤銷的連入的憑證的憑證撤銷清單 (CRL)。 並不重要，若憑證本身未被撤銷。 如果 BizTalk Server 無法查詢對應的 CRL，因為連線問題，就不會接受憑證。 若要疑難排解這個錯誤，顯示憑證的屬性，請按兩下您所使用的憑證。 在其詳細資料 索引標籤中，您會看到欄位清單中的屬性 「 CRL 散佈點 」。 應該要有這個屬性中數個 CA 伺服器上的 CRL 所指向的 Url。 BizTalk server 必須能夠存取任何這些 Url 擷取 CRL。 否則，撤銷檢查會失敗並出現上述錯誤，將會公佈。  
  
### <a name="the-other-people-certificate-store-is-not-initialized-until-accessed"></a>在存取之前，未初始化的其他人 」 憑證存放區  
 當您嘗試加入或修改傳送/接收埠/位置使用時，此問題牽涉到下列憑證存放區錯誤[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理員主控台從遠端: 「 無法開啟憑證存放區 」。 和 「 系統找不到指定的檔案。 （系統） 」。  
  
> [!NOTE]  
>  您可以修改使用 [管理] 主控台，如果您直接登入這些成品[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
 新安裝的電腦上，**其他人 」 憑證**除非您一次存取未初始化存放區。 群組在設定期間，您可以初始化這個**其他人 」 憑證**儲存和結果的群組進行設定的電腦上未看到此錯誤。  
  
### <a name="biztalk-server-only-supports-one-personal-certificate-for-each-biztalk-group"></a>BizTalk Server 只支援一個個人憑證的每個 BizTalk 群組  
 在 BizTalk 群組屬性中設定個人憑證的指紋，來指定所使用的 BizTalk 群組的個人憑證。 BizTalk 群組代表日用企業、 部門、 集線器或其他商務單位。  
  
## <a name="as2-certificate-issues"></a>AS2 憑證問題  
  
### <a name="the-as2-decoder-will-not-validate-that-a-certificate-is-configured-on-the-host-or-for-the-destination-party"></a>AS2 解碼器將不會驗證憑證已在主機或目的合作對象  
 只要憑證存放區中已設定訊息的私用憑證，AS2 解碼器就會解密訊息。 不過，AS2 解碼器將不會驗證解密憑證是否與主控件上設定的憑證相同。 收到的訊息可以使用一個以上的憑證加密。  
  
### <a name="biztalk-server-will-be-unable-to-decrypt-a-message-saved-in-wire-format-if-the-certificate-is-not-valid"></a>BizTalk Server 將無法解密以電傳格式儲存，如果憑證不是有效的訊息  
 **徵兆**  
  
 BizTalk Server 無法解密以電傳格式儲存在不可否認性資料庫中的內送 AS2 訊息。  
  
 **可能的原因**  
  
 解密訊息時所需的憑證已過期或已撤銷。 當 AS2 訊息儲存在不可否認性資料庫一段時間後，就可能會發生這種狀況。 這時您可能無法立即存取訊息的有效憑證。  
  
 **解決方式**  
  
 取得有效憑證來解密訊息。  
  
### <a name="if-an-as2-message-cannot-be-decrypted-the-problem-may-be-fixed-by-re-importing-the-certificate"></a>如果無法解密 AS2 訊息，可能會藉由重新匯入憑證修正的問題  
 **徵兆**  
  
 AS2 解碼器遇到例外狀況時若嘗試解密 AS2 訊息，擲回下列錯誤：  
  
```  
"The AS2 Decoder encountered an exception during processing. Details of the message and exception are as follows:   
   AS2-From:"PARTNER" AS2-To:"HOME" MessageID:"<137706.1178060412333@servername>"   
   MessageType: "unknown" Exception:"An error occurred when decrypting an AS2 message."  
System.ArgumentNullException: Value cannot be null.  
Parameter name: PayloadContentType  
at Microsoft.BizTalk.Edi.Reporting.Common.Utilities.ValidateArgument(Object o,  
String parameterName, Boolean isEmptyStringValidationRequired)  
at Microsoft.BizTalk.EdiInt.Reporting.AS2MessageActivity.ValidateParameters()  
at Microsoft.BizTalk.EdiInt.Reporting.AS2MessageActivity.Create()"  
  
```  
  
 **可能的原因**  
  
 用來解密 AS2 訊息的憑證必須重新載入「個人存放區」。  
  
 **解決方式**  
  
 從 [個人存放區] 刪除現有的憑證，然後使用 [憑證匯入精靈] 將憑證重新匯入 [個人存放區]。 以滑鼠右鍵按一下執行這項操作**憑證**下的資料夾**個人存放區**、 指向**所有工作**，然後按一下**匯入**。  
  
### <a name="use-the-same-logon-for-the-in-process-host-instance-and-the-isolated-host-instance-to-ensure-that-personal-store-is-recognized"></a>若要確定已辨識的個人存放區使用內含式主控件執行個體和外掛式主控的件執行個體相同的登入  
 只有在針對其登入認證與主控件執行個體相關聯的使用者載入使用者設定檔時，個人憑證存放區才能用於訊息處理。 個人存放區是用於簽章和解密憑證 (使用者專屬的私密金鑰)。 預設會為內含式主控件執行個體載入使用者設定檔，但是不會為外掛式主控件執行個體載入使用者設定檔。 您可以讓應用程式針對外掛式主控件載入使用者設定檔。 或者，您也可以為內含式主控件執行個體和外掛式主控件執行個體使用相同的登入，以解決這個問題。  
  
 除了由應用程式載入使用者設定檔，您也可以建立空的服務來載入設定檔。 如需建立空的服務的詳細資訊，請參閱[How to： 建立 Windows 服務](http://go.microsoft.com/fwlink/?LinkId=155149)(http://go.microsoft.com/fwlink/?LinkId=155149) 在 Visual Studio 說明。  
  
 建立空的服務，來載入設定檔之後, 請繼續進行，如下所示：  
  
1.  按一下**啟動**，然後按一下 [**執行**開啟**執行**] 對話方塊。  
  
2.  在**執行** 對話方塊中，輸入**service.msc**按**ENTER**開啟**服務**MMC 嵌入式管理單元。  
  
3.  開啟**屬性**您建立的服務 對話方塊。 以滑鼠右鍵按一下服務，然後選取**屬性**。  
  
4.  按一下**登入**索引標籤上，選取**這個帳戶**，然後輸入 外掛式主控的件執行個體所使用的登入名稱。  
  
5.  按一下 **[確定]**。  
  
6.  手動啟動服務以載入該登入使用者的使用者設定檔。  
  
### <a name="the-key-usage-attribute-of-a-certificate-must-match-the-certificates-use"></a>憑證的金鑰使用方式屬性必須符合憑證使用方式  
 AS2 傳輸所使用的憑證必須有憑證預定使用方式的必要屬性。 針對簽署和簽章驗證，憑證的 [金鑰使用方式] 屬性必須是 [數位簽章]。 針對加密和解密，憑證的 [金鑰使用方式] 屬性必須是 [資料編密] 或 [金鑰編密]。 您可以按兩下憑證，然後按一下確認金鑰使用方法屬性**詳細資料**索引標籤中**憑證**對話方塊中，並檢查**金鑰使用方法**欄位.  
  
### <a name="the-certificate-resolution-list-will-be-verified-for-an-outgoing-mdn-if-the-as2-to-property-is-not-set-for-the-party"></a>如果未設定合作對象的 AS2-To 屬性，則會針對外寄 MDN 驗證憑證解析清單  
 在外寄 MDN 的預設協議中，會執行憑證解析清單驗證。 如果您不要執行此驗證，請確認已設定正確的 AS2-To 合作對象屬性，以便解析接收的合作對象並判斷合作對象屬性。 如此一來，便不會使用預設協議 (會提示要驗證憑證解析清單)。 您也將需要停用 AS2 合作對象屬性 [一般] 頁面上的 [檢查憑證撤銷清單] 屬性。