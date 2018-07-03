---
title: 接收配接器的 SSO 支援 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4767387c-f24b-4986-aaed-6724c5d6b347
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00948d53ada9dd5eb428b0d1975e16b21b19064d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008431"
---
# <a name="sso-support-for-receive-adapters"></a>接收配接器的 SSO 支援
「企業單一登入」(SSO) 提供的服務能夠跨本機、網路及網域界限，來儲存和傳輸加密的使用者認證。 傳輸配接器寫入器可以利用 SSO API 來處理使用者認證，以便讓傳輸配接器用來存取後端應用程式。  
  
 不支援 SSO 的傳輸配接器，通常都需要以單一組合的認證予以設定，這些會由配接器用來存取後端應用程式。 對於許多後端系統，單一帳戶驗證可能無法滿足所有的安全性強制。 許多應用程式都根據存取的使用者，提供不同的存取權限。 SSO 讓配接器能夠根據嘗試存取的使用者，動態地選擇要對端點使用的認證。  
  
## <a name="how-receive-adapters-work-with-sso"></a>接收配接器如何搭配 SSO 運作  
 支援 SSO 的接收配接器會在接收訊息後，以及將其發佈到 BizTalk Server 前，執行下列步驟：  
  
1. 配接器會模擬寄件者，並取得 SSO 票證代表寄件者使用**ISSOTicket.IssueTicket** API。  
  
2. 在成功取得 SSO 票證後，配接器便會將其儲存在系統命名空間下的訊息內容屬性 SSOTicket 中。  
  
   下列程式碼片段將示範如何取得票證，以及如何將其儲存在訊息內容中。  
  
```  
public class MyAdapter : IBTTransport,   
                         IBTTransportConfig,   
                         IBTTransportControl,  
                         IPersistPropertyBag,   
                         IBaseComponent  
{  
...  
     private string m_SSOToken = null;  
  
 // Get a ticket for the sender  
     private void GetSSOTicket(IntPtr token)  
     {  
       bool impersonated = false;  
      WindowsImpersonationContext wic = null;  
  
 if (token != (IntPtr)0)   
 {  
     try   
 {  
         // Impersonate the user using his security  
 // token  
            WindowsIdentity wi =   
 new WindowsIdentity(token);  
            wic = wi.Impersonate();  
            impersonated = true;  
  
         // Get an SSO ticket for the impersonated  
 // user  
            ISSOTicket ssoTicket = new ISSOTicket();  
            m_SSOToken = ssoTicket.IssueTicket(0);  
         }  
         finally   
 {  
           if (impersonated)  
            // Revert the impersonation  
            wic.Undo();  
          }  
}  
}  
...  
  
     private void WriteSSOTicketToContext(  
 IBaseMessage message )  
     {  
         if (m_SSOTicket != null)   
 {  
 // Write the SSO ticket to the message context  
          message.Context.Write(  
 “SSOTicket”,  
 http://schemas.microsoft.com/BizTalk/2003/system-properties,   
 m_SSOToken);  
        }  
      }  
}  
```  
  
## <a name="party-resolution"></a>合作對象解析  
 合作對象解析管線元件負責將傳送者憑證或傳送者安全性識別碼 (SID) 對應至所對應的已設定 BizTalk Server 合作對象。 擁有這項資訊提供給他們的配接器應該設定兩個系統訊息內容屬性**WindowsUser**並**SignatureCertificate**，以供下游合作對象解析如果設定的元件。  
  
 **WindowsUser**屬性會填入網域使用者，寄件者，例如 redmond\myBtsUser。 **SignatureCertificate**屬性會填入用戶端驗證憑證的指紋。  
  
## <a name="managing-passwords"></a>管理密碼  
 如果您將認證直接放在端點的屬性中，當您需要匯出繫結檔案時，密碼欄位就會變成空白。 這樣您的使用者就需要重新輸入系統管理員的密碼。 您可以對認證使用 SSO 以避免這種困難狀況。  
  
 如果配接器端點具有**密碼**屬性，請注意，實際的值會儲存在 SSO 設定存放區資料庫中的純文字。 即使在使用者介面中顯示為 "*"，依然會是如此。 這個屬性也可透過網路傳輸，而且使用 BizTalk Server 範例 ExplorerOM 的簡單指令碼即可加以讀取。