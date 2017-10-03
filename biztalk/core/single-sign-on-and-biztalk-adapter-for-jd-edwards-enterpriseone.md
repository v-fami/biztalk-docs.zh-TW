---
title: "單一登入與 BizTalk Adapter for JD Edwards EnterpriseOne |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, Single Sign-On
- Single Sign-On, JD Edwards EnterpriseOne adapters
- adapters [JD Edwards EnterpriseOne adapters], Single Sign-On
ms.assetid: efcc3a2d-18a6-4090-9e95-143fb7a356b2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 182e73ed45a1473286a301cf859e619cc5d21287
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-and-biztalk-adapter-for-jd-edwards-enterpriseone"></a>單一登入與 BizTalk Adapter for JD Enterprise OneWorld
當您將單一登入 (SSO) 與 Microsoft Adapter for JD Edwards EnterpriseOne 搭配使用時，此配接器會從 SSO 認證資料庫取得認證。 因此，您不需要在伺服器系統輸入登入認證**傳輸屬性** 對話方塊。  
  
 在設計階段，BizTalk Adapter for JD Edwards EnterpriseOne 會以啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案的使用者身分取得系統 (所指定分支機構應用程式的系統) 的認證。 該使用者應為「應用程式使用者」。 使用 SSO 的通過實例時，請在執行階段使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP 接收配接器做為接收位置。  
  
## <a name="processing-requests"></a>處理要求  
 當 Internet Information Services (IIS) 從 Web 用戶端收到 HTTP 要求時，IIS 會驗證使用者。 ISAPI 延伸模組會模擬 Windows 使用者，然後呼叫 SSO 認證存放區以取得加密的票證。 此票證會在訊息內容中儲存為 SSOTicket 屬性。  
  
 訊息接著會導向到 MessageBox 資料庫。 當 BizTalk Adapter for JD Edwards EnterpriseOne 從 MessageBox 資料庫收到訊息時，它會以加密票證和分支機構應用程式名稱呼叫 `ValidateAndRedeemTicket`，以從 SSO 存放區擷取登入認證。 然後此配接器會使用這些外部認證連接至系統並處理要求。  
  
> [!NOTE]
>  SSO 組態屬於 BizTalk Server 設定的一部分。 收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。 SSO 僅能在網域帳戶運作。  
  
## <a name="see-also"></a>另請參閱  
 [建立分支機構應用程式](../core/creating-affiliate-applications4.md)   
 [使用單一登入](../core/using-single-sign-on1.md)