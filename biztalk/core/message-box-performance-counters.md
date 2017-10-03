---
title: "訊息方塊效能計數器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5eafbd7b-f5fc-4942-a975-18154e6a7ee2
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b51b98d1d9172b40b36cfd496e8bb9c511e5c19
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-box-performance-counters"></a>MessageBox 效能計數器
效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。 效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。  
  
 下列效能計數器會在每個主控件執行個體可存取**biztalk: Message Box： 一般計數器**和**biztalk: Message Box： 主控件計數器**效能物件類別:  
  
> [!NOTE]
>  若要啟用參照 SQL 代理程式工作的計數器，用於執行 BizTalk 主控件/NT 服務的服務帳戶必須隸屬 SQLAgentUserRole 角色。 或者，您也可以使用其他角色來授與權限，或授與該帳戶讀取 MSDB 資料庫的明確權限。  
  
> [!NOTE]
>  如果您已經加入新 MessageBox 至 BizTalk Server 群組，下列計數器方可將無法使用為此新 MessageBox 之前**快取重新整理**BizTalk Server 群組的間隔已經耗盡 （預設值為 60秒為單位）。  
  
|類別目錄|計數器|Description|  
|--------------|-------------|-----------------|  
|一般計數器|執行個體 - 總數|追蹤每個主控件存在特定 MessageBox 中的所有執行個體總和。|  
|一般計數器|MsgBox 終止程序清理 (清除工作)|最近執行的 SQL 代理程式工作 (釋放與已終止的 BizTalk 程序關聯的資料庫資料列) 所花的時間 (秒)。|  
|一般計數器|MsgBox 訊息清理 (清除工作)|最近執行的 SQL 代理程式工作 (清除與已移除之訊息關聯的 MessageBox 表格) 所花的時間 (秒)。|  
|一般計數器|MsgBox 部分清理 (清除工作)|最近執行的 SQL 代理程式工作 (清除與已移除之訊息部分關聯的 MessageBox 表格) 所花的時間 (秒)。|  
|一般計數器|MsgBox 清除訂閱工作 (清除工作)|最近執行的 SQL 代理程式工作 (清除不再使用的訂閱) 所花的時間 (秒)。|  
|一般計數器|多工緩衝處理大小|追蹤特定伺服器上特定 MessageBox 的多工緩衝處理大小。|  
|一般計數器|追蹤訊息複製 (清除工作)|最近執行的 SQL 代理程式工作 (針對追蹤的訊息複製追蹤的訊息內文) 所花的時間 (秒)。|  
|一般計數器|追蹤資料大小|追蹤特定伺服器上特定 MessageBox 中的追蹤資料表大小。|  
|一般計數器|追蹤多工緩衝處理清理 (清除工作)|時間 （秒） 最近執行的清除非作用中的 SQL 代理程式作業追蹤多工緩衝處理資料表。|  
|主控件計數器|主控件佇列 - 執行個體狀態訊息參考 - 長度|追蹤此特定主控件的執行個體狀態佇列中的訊息參考數。|  
|主控件計數器|主控件佇列 - 長度|追蹤特定主控件佇列中的訊息總數。|  
|主控件計數器|主控件佇列 - 執行個體數|追蹤此特定主控件的執行個體數。|  
|主控件計數器|主控件佇列 - 擱置的訊息 - 長度|追蹤特定主控件的擱置訊息總數。|  
  
## <a name="to-access-performance-counters"></a>存取效能計數器  
 使用下列步驟來存取效能計數器。  
  
#### <a name="if-you-are-using-windows-2008"></a>若是使用 Windows 2008  
  
1.  按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。  
  
2.  在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。  
  
3.  在**新增計數器**對話方塊中，從**可用的計數器**清單中，選取**biztalk: Message Box： 一般計數器**或**biztalk： 訊息方塊： 裝載計數器**。 展開選取的效能計數器物件，然後選取要監視的計數器  
  
4.  在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。  若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**>。  
  
5.  新增計數器後, 按一下**確定**。  
  
     選取的效能計數器隨即出現在**效能監視器**螢幕。  
  
## <a name="see-also"></a>另請參閱  
 [效能秘訣和訣竅](../core/performance-tips-and-tricks.md)   
 [測量最大持續性引擎輸送量](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [測量最大持續性追蹤輸送量](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [透過主控件節流將資源使用最佳化](../core/optimizing-resource-usage-through-host-throttling.md)