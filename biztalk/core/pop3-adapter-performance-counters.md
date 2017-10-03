---
title: "POP3 配接器效能計數器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f799175e-e9e7-4937-93bd-aaec1c43b75a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0f48879fcc00041ce0fa1cf842a066c6da59804
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="pop3-adapter-performance-counters"></a>POP3 配接器效能計數器
效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。 效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。  
  
 下列效能計數器會在每個主控件執行個體可存取**biztalk: Pop3 接收配接器**效能物件類別：  
  
|**類別目錄**|**計數器**|**說明**|  
|------------------|-----------------|---------------------|  
|BizTalk:POP3 接收配接器|作用中的工作階段|POP3 配接器一次管理的 POP3 開啟連線數。|  
||接收位元組數|POP3 配接器從郵件伺服器下載的位元組總數。|  
||接收位元組數/秒|POP3 配接器每秒從郵件伺服器下載的位元組數。|  
||接收訊息數|POP3 配接器從郵件伺服器下載的電子郵件訊息總數。|  
||接收訊息數/秒|POP3 配接器每秒從郵件伺服器下載的電子郵件訊息數。|  
  
## <a name="to-access-performance-counters"></a>存取效能計數器  
 請遵照下列步驟來存取 POP3 配接器的效能計數器：  
  
#### <a name="if-you-are-using-windows-2008"></a>若是使用 Windows 2008  
  
1.  按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。  
  
2.  在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。  
  
3.  在**新增計數器**對話方塊中，從**可用的計數器**清單中，展開**biztalk: Pop3 接收配接器**效能計數器物件，然後選取要計數器監視  
  
4.  在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。  若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**>。  
  
5.  新增計數器後, 按一下**確定**。  
  
     選取的效能計數器隨即出現在**效能監視器**螢幕。  
  
## <a name="see-also"></a>另請參閱  
 [監控 BizTalk Server](../core/monitoring-biztalk-server.md)  
 [處理多部分訊息，POP3 配接器](../core/processing-multi-part-messages-with-the-pop3-adapter.md)   
 [執行叢集主控件中的配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)