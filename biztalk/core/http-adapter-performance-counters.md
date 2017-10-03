---
title: "HTTP 配接器效能計數器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d85473f1-1d67-4990-8d2f-fc7fe0e80108
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21ae11dfb3ecd9a2b5e63449961af70aa3bc6f7d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="http-adapter-performance-counters"></a>HTTP 配接器效能計數器
效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。 效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。  
  
 下列效能計數器會在每個主控件執行個體可存取**biztalk: Http 接收配接器**和**biztalk: Http 傳送配接器**效能物件類別：  
  
|**類別目錄**|**計數器**|**說明**|  
|------------------|-----------------|---------------------|  
|BizTalk:HTTP 接收配接器|Memory queue size|HTTP 接收配接器的內部記憶體佇列中的內送訊息數。|  
||接收訊息數|HTTP 接收配接器接收的 HTTP 要求總數。 此計數器會在 HTTP 接收配接器從 HTTP 用戶端完整讀取要求訊息後遞增。|  
||接收訊息數/秒|HTTP 接收配接器每秒接收的 HTTP 要求數。 此計數器只適用於 HTTP 接收配接器從 HTTP 用戶端完整讀取的要求訊息。|  
||Messages sent|HTTP 接收配接器傳送的 HTTP 回應總數。 此計數器只會在回應訊息已成功傳送至 HTTP 用戶端後遞增。|  
||Messages sent/Sec|HTTP 接收配接器每秒傳送的 HTTP 回應數。 此計數器只適用於已成功傳送至 HTTP 用戶端的回應訊息。|  
||新增訊息至批次的時間|IIS 將訊息提供給 HTTP 接收配接器，到該訊息新增至某個批次之間的平均時間。|  
||建置批次時間|HTTP 接收配接器建立訊息批次的平均時間。|  
|BizTalk:HTTP 傳送配接器|Memory queue size|HTTP 傳送配接器的內部記憶體佇列中的外寄訊息數。|  
||接收訊息數|HTTP 傳送配接器接收的 HTTP 回應訊息總數。 此計數器會在 HTTP 傳送配接器從 HTTP 伺服器完整讀取回應訊息後遞增。|  
||接收訊息數/秒|HTTP 傳送配接器每秒接收的 HTTP 回應數。 此計數器只適用於 HTTP 傳送配接器從 HTTP 伺服器完整讀取的回應訊息。|  
||Messages sent|HTTP 傳送配接器傳送的 HTTP 要求總數。 此計數器只會在要求訊息已到達目的地 URL 後遞增。|  
||Messages sent/Sec|HTTP 傳送配接器每秒傳送的 HTTP 要求數。 此計數器只適用於已到達目的地 URL 的要求訊息。|  
  
## <a name="to-access-performance-counters"></a>存取效能計數器  
 使用下列步驟來存取效能計數器。  
  
#### <a name="if-you-are-using-windows-2008"></a>若是使用 Windows 2008  
  
1.  按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。  
  
2.  在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。  
  
3.  在**新增計數器**對話方塊中，從**可用的計數器**清單中，展開**biztalk: Http**效能計數器物件，然後選取要監視的計數器  
  
4.  在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。  若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**>。  
  
5.  新增計數器後, 按一下**確定**。  
  
     選取的效能計數器隨即出現在**效能監視器**螢幕。  
  
## <a name="see-also"></a>另請參閱  
 [監控 BizTalk Server](../core/monitoring-biztalk-server.md)   
 [HTTP 配接器組態和調整參數](../core/http-adapter-configuration-and-tuning-parameters.md)   
 [執行叢集主控件中的配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)