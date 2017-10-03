---
title: "單一登入與 BizTalk Adapter for TIBCO Enterprise Message Service |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, processing requests
- Single Sign-On, using with adapter
- processing requests
- HTTP requests, processing
ms.assetid: 68e85ceb-bf4c-489a-a2c2-1558e718ceed
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 181e54426d568857a9116aa47022adbc7788edaf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-and-biztalk-adapter-for-tibco-enterprise-message-service"></a>單一登入與 BizTalk Adapter for TIBCO Enterprise Message Service
當您使用單一登入 (SSO) 搭配 Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 時，配接器會從 SSO 認證資料庫取得認證因此，您沒有在伺服器系統輸入登入認證**傳輸屬性** 對話方塊。  
  
 在設計階段，配接器會以啟動 BizTalk Server 專案的使用者身分取得系統的認證 (針對指定的分支機構應用程式)。 該使用者應為「應用程式使用者」。 在執行階段，當使用 SSO 時，請在通過實例中使用 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP 接收配接器做為接收位置。  
  
## <a name="processing-requests"></a>處理要求  
 當 Internet Information Services (IIS) 從 Web 用戶端收到 HTTP 要求時，IIS 會驗證使用者。 ISAPI 延伸模組會模擬 Windows 使用者，然後呼叫 SSO 認證存放區以取得加密的票證。 此票證會在訊息內容中儲存為 SSOTicket 屬性。  
  
 訊息接著會導向到 MessageBox 資料庫。 當 BizTalk Adapter for TIBCO EMS 從 MessageBox 資料庫接收訊息時，它會呼叫具有加密票證及分支機構應用程式名稱的 ValidateAndRedeemTicket 方法，從 SSO 存放區擷取登入認證。 然後此配接器會使用這些外部認證連接至系統並處理要求。  
  
> [!NOTE]
>  SSO 組態屬於 BizTalk Server 設定的一部分。 收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。 SSO 僅能在網域帳戶運作。  
  
## <a name="see-also"></a>另請參閱  
 [建立分支機構應用程式](../core/creating-affiliate-applications5.md)   
 [使用單一登入](../core/using-single-sign-on4.md)