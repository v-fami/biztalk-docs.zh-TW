---
title: "如何啟用的路由失敗訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d33beed4-1ae2-4282-95ac-5d68aab7fb5d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8bfa76ba9378bc2177b31fac085b603971232840
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-routing-for-failed-messages"></a>如何啟用失敗訊息的路由
失敗訊息路由是傳送埠和接收埠的屬性，啟用方式是在連接埠的屬性頁指定 [啟用失敗訊息的路由]。  
  
> [!NOTE]
>  接收埠的組態會套用到與該接收埠相關聯的所有接收位置。  
  
> [!NOTE]
>  傳送埠的組態會同時套用到主要傳輸和備份傳輸。  
  
### <a name="to-configure-failed-message-routing-for-a-receive-port-this-applies-to-both-one-way-and-request-response-receive-ports"></a>若要設定接收埠的失敗訊息路由 (此程序適用於單向及雙向要求-回應接收埠)  
  
1.  開啟 BizTalk Server 管理主控台。  
  
2.  展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 傳送埠所屬的應用程式。  
  
3.  按一下**接收埠**資料夾。  
  
4.  在右邊窗格中，按兩下您要設定的接收埠的名稱。  
  
5.  在接收埠屬性 頁面上，在左窗格中，選取**一般**類別目錄。  
  
6.  在右窗格中，選取**啟用的路由失敗訊息**核取方塊，然後**套用**。  
  
### <a name="to-configure-failed-message-routing-for-a-send-port-this-applies-only-to-static-one-way-and-static-solicit-response-send-ports"></a>若要設定傳送埠的失敗訊息路由 (此程序只適用於靜態單向及靜態雙向請求-回應傳送埠)  
  
1.  開啟 BizTalk Server 管理主控台。  
  
2.  展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 傳送埠所屬的應用程式。  
  
3.  按一下**傳送埠**資料夾。  
  
4.  在右邊窗格中，按兩下您要設定的傳送埠的名稱。  
  
5.  在傳送埠屬性 頁面上，在左窗格中，選取**傳輸進階選項**類別目錄。  
  
6.  在右窗格中，在**傳輸選項**群組方塊中，選取**啟用的路由失敗訊息**核取方塊，然後**套用**。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤處理](../core/error-handling.md)