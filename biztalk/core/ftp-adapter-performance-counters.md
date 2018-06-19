---
title: FTP 配接器效能計數器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ca5cbe67-9aa3-4194-816e-fab4eb551c07
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5dad67f24f37f661e26f4cb56895c6bcad6b0782
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969436"
---
# <a name="ftp-adapter-performance-counters"></a>FTP 配接器效能計數器
效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。 效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。  
  
 下列效能計數器會在每個主控件執行個體可存取**biztalk: Ftp 接收配接器**和**biztalk: Ftp 傳送配接器**效能物件類別：  
  
|**類別目錄**|**計數器**|**說明**|  
|------------------|-----------------|---------------------|  
|BizTalk:FTP 接收配接器|接收位元組數|FTP 接收配接器接收的位元組總數。 此計數器會在 FTP 接收配接器從 FTP 伺服器完整讀取訊息後遞增。|  
||接收位元組數/秒|FTP 接收配接器每秒收到的位元組數。 此計數器只適用於 FTP 接收配接器從 FTP 伺服器完整讀取的訊息。|  
||接收訊息數|FTP 接收配接器接收的訊息總數。 此計數器會在 FTP 接收配接器從 FTP 伺服器完整讀取訊息後遞增。|  
||接收訊息數/秒|FTP 接收配接器每秒收到的訊息數。 此計數器只適用於 FTP 接收配接器從 FTP 伺服器完整讀取的訊息。|  
|BizTalk:FTP 傳送配接器|傳送位元組數|FTP 傳送配接器傳送的位元組總數。 此計數器只會在訊息已寫入目的地 FTP 伺服器後遞增。|  
||傳送位元組數/秒|FTP 傳送配接器每秒傳送的位元組數。 此計數器只適用於已寫入目的地 FTP 伺服器的訊息。|  
||Messages sent|FTP 傳送配接器傳送的訊息總數。 此計數器只會在訊息已寫入目的地 FTP 伺服器後遞增。|  
||Messages sent/Sec|FTP 傳送配接器每秒傳送的訊息數。 此計數器只適用於已寫入目的地 FTP 伺服器的訊息。|  
  
## <a name="to-access-performance-counters"></a>存取效能計數器  
 使用下列步驟來存取效能計數器。  
  
#### <a name="if-you-are-using-windows-2008"></a>若是使用 Windows 2008  
  
1.  按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。  
  
2.  在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。  
  
3.  在**新增計數器**對話方塊中，從**可用的計數器**清單中，展開**biztalk: Ftp**效能計數器物件，然後選取要監視的計數器  
  
4.  在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。  若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**\>。  
  
5.  新增計數器後, 按一下**確定**。  
  
     選取的效能計數器隨即出現在**效能監視器**螢幕。  
  
## <a name="see-also"></a>請參閱  
 [監控 BizTalk Server](../core/monitoring-biztalk-server.md) [執行叢集主控件中的配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)