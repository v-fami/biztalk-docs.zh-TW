---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: 314bffd50e152c1e3141e4f644c60bdbe7a3824a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011031"
---
# <a name="deployment-limitations"></a>部署限制
傳輸配接器 」 密碼會儲存為星號 (\*\*\*\*\*\*) 中的繫結檔案匯出 BizTalk 部署精靈 」，並傳遞給管理在相同的格式中的元件。 繫結檔案前先行編輯匯入的星號取代成隨機英數字元值 （也就是不正確的密碼）。 然後輸入正確的密碼使用**傳輸屬性**匯入繫結檔案後的頁面。  
  
 當您匯出繫結資訊時，所產生的繫結檔案不會包含傳輸配接器在接收位置/傳送埠中使用的任何密碼。 這可防止密碼資訊以純文字方式出現。 下次您使用檔案匯入繫結資訊時，必須使用傳輸屬性頁使用者介面輸入密碼。 或者，您可以在匯入前先暫時修改繫結檔案，方法是將密碼輸入繫結檔案。 在這種情況下，您必須在匯入作業順利完成後刪除繫結檔案中的密碼。  
  

## <a name="password-limitation-workaround"></a>密碼限制解決方法  
 作為下列其中一種解決密碼限制問題。  
  
#### <a name="to-work-around-the-password-limitation"></a>解決密碼限制問題  
  
1. 在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為純文字。  
  
   > [!CAUTION]
   >  基於安全理由，並不建議使用這個做法。  
  
2. 在匯入繫結檔案前先行編輯該檔案，方法是將星號取代為某些垃圾值 (亦即不正確的密碼)。 輸入正確的密碼使用**傳輸屬性**匯入繫結檔案後的頁面。  
  
   > [!NOTE]
   >  只有當目標電腦上安裝了 Microsoft Visual Studio，或您開發自訂工具時，才能使用這項解決方法。  
  
   **-或-**  
  
#### <a name="to-work-around-the-password-limitation"></a>解決密碼限制問題  
  
1.  不使用密碼，改為使用「企業單一登入」。  
  
     使用 SSO 選項只需要先匯入繫結檔案，不需要額外操作。  
  
2.  驗證邏輯系統以及「傳輸」和「接收」服務。  
  
## <a name="see-also"></a>另請參閱  
 [將成品新增至 BizTalk 管理](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)   
 [匯入 JD Edwards OneWorld 應用程式](deploying-biztalk-adapter-for-jd-edwards-oneworld.md)