---
title: 單一登入與 BizTalk Adapter for PeopleSoft Enterprise |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- processing HTTP requests
- Single Sign-On, using with the adapter
- HTTP requests, processing
ms.assetid: d8ad75f1-a83f-4722-a43f-50dc95df2f9d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bb898906bfd3087ef909e59990a16ce16c2822c
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015597"
---
# <a name="single-sign-on-and-biztalk-adapter-for-peoplesoft-enterprise"></a>單一登入與 BizTalk Adapter for PeopleSoft Enterprise
當您使用單一登入 (SSO) 搭配 Microsoft BizTalk Adapter for PeopleSoft Enterprise 時，配接器會從 SSO 認證資料庫取得認證因此，您沒有在伺服器系統輸入登入認證**傳輸屬性** 對話方塊。  
  
 在設計階段，BizTalk Adapter for PeopleSoft Enterprise 會以用於啟動 BizTalk Server 專案的使用者身分取得系統的認證 (針對指定的分支機構應用程式)。 該使用者應為「應用程式使用者」。  
  
## <a name="processing-requests"></a>處理要求  
 當 Internet Information Services (IIS) 從 Web 用戶端收到 HTTP 要求時，IIS 會驗證使用者。 ISAPI 延伸模組會模擬 Windows 使用者，然後呼叫 SSO 認證存放區以取得加密的票證。 此票證會在訊息內容中儲存為 SSOTicket 屬性。  
  
 訊息接著會導向到 MessageBox 資料庫。 當 BizTalk Adapter for PeopleSoft Enterprises 從 MessageBox 資料庫收到訊息時，它會以加密票證和分支機構應用程式名稱呼叫 ValidateAndRedeemTicket，以從 SSO 存放區擷取登入認證。 然後此配接器會使用這些外部認證連接至系統並處理要求。  
  
> [!NOTE]
>  SSO 組態屬於 BizTalk Server 設定的一部分。 收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。 SSO 僅能在網域帳戶運作。  
  
## <a name="see-also"></a>另請參閱  
 [建立分支機構應用程式](../core/creating-affiliate-applications2.md)   
 [保護配接器](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)