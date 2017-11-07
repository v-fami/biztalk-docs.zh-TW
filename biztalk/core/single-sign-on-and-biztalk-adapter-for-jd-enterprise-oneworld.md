---
title: "單一登入與 BizTalk Adapter for JD Enterprise OneWorld |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Single Sign-On
ms.assetid: 44fea3a4-8073-4b64-94e5-1eacbae845d9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3b0fbe7aa671d543a0fd6cd7da78e05d18c63c3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="single-sign-on-and-biztalk-adapter-for-jd-enterprise-oneworld"></a>單一登入與 BizTalk Adapter for JD Enterprise OneWorld
從 SSO 認證資料庫取得單一登入 (SSO) 認證因此，您不需要輸入伺服器系統的登入認證在**傳輸屬性**視窗。  
  
 在設計階段，Microsoft BizTalk Adapter for JD Edwards OneWorld 會以啟動 BizTalk Server 專案的使用者身分取得系統的認證 (針對指定分支機構應用程式)。 該使用者應為「應用程式使用者」。  
  
 在執行階段，當使用 SSO 時，請在通過實例中使用 BizTalk Adapter for JD Edwards OneWorld 做為接收位置。  
  
 當 Internet Information Services (IIS) 從 Web 用戶端收到 HTTP 要求時，IIS 會驗證使用者。 ISAPI 延伸模組會模擬 Windows 使用者，然後呼叫 SSO 認證存放區以取得加密的票證。 此票證會在訊息內容中儲存為 SSOTicket 屬性。  
  
 訊息接著會導向到 MessageBox 資料庫。 當配接器從 MessageBox 資料庫接收訊息時，它會呼叫具有加密票證及分支機構應用程式名稱的 IBTSTicket.ValidateAndRedeemTicket 方法，從 SSO 存放區擷取登入認證。 BizTalk Adapter for JD Edwards OneWorld 配接器接著就會使用外部認證連接到系統並處理要求。  
  
> [!NOTE]
>  SSO 組態屬於 BizTalk Server 設定的一部分。 收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。 SSO 僅能在網域帳戶運作。  
  
## <a name="see-also"></a>另請參閱  
 [建立分支機構應用程式](../core/creating-affiliate-applications3.md)   
 [在配接器的安全性](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)