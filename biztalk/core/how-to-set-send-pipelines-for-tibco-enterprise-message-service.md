---
title: "如何設定傳送管線 for TIBCO Enterprise Message Service |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send pipelines
- setting send pipelines
- pipelines, send
ms.assetid: 6a84d874-4b4d-4b23-913f-f5c72af1e96e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d037782e2580d52c6609c3669e2805aae92ce9eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-send-pipelines-for-tibco-enterprise-message-service"></a>如何設定 TIBCO Enterprise Message Service 的傳送管線
Microsoft BizTalk Adapter for TIBCO Enterprise Message Service 需要您分別為傳送管線和接收管線選取 XMLTransmit 與 XMLReceive。  
  
### <a name="to-set-pipelines"></a>設定管線  
  
1.  在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。  
  
2.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。  
  
3.  在**傳送埠屬性**對話方塊方塊中，執行下列動作：  
  
    1.  輸入傳送埠名稱，例如`SendToTIBCOEMS`。  
  
    2.  從**類型**下拉式清單中，選取**TIBCO EMS**。  
  
    3.  從**傳送處理常式**下拉式清單中，選取 URI。  
  
    4.  從 傳送管線 下拉式清單中，選取  **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。  
  
    5.  從**接收管線**下拉式清單中，選取**[microsoft.biztalk.defaultpiplelines.xmlreceive]**。  
  
4.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 TIBCO Enterprise Message Service 的接收管線](../core/how-to-set-receive-pipelines-for-tibco-enterprise-message-service.md)