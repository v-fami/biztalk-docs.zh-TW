---
title: "執行 BizTalk Server 之電腦的災害復原 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10a2c26d-55d5-45d1-9fb1-e0664f005c21
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac655c10aaa443f9971fc40f7301a9e608e0e7eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="disaster-recovery-for-computers-running-biztalk-server"></a>執行 BizTalk Server 的電腦的嚴重損毀修復
如果在您的組織中，執行 BizTalk Server 的電腦遇到無法復原的硬體失敗問題，您應該更換一台相同的電腦。 這麼做是假設 BizTalk Server 資料庫仍然完整，而此次失敗是發生在其中一台執行 BizTalk Server 的電腦上。  
  
 有一個可行方式，即是在安裝時維護每一台執行 BizTalk Server 的電腦的更新映像。 當電腦遇到硬體失敗的問題時，復原動作就像在新電腦上部署儲存的映像一樣簡單。 本損毀修復主題主要是針對無法儲存這類映像的狀況進行處理。  
## <a name="recovering-different-editions-of-biztalk-server"></a>復原不同版本的 BizTalk Server  
 復原方式會因電腦執行的 BizTalk Server 版本不同而有所不同。  
  
 如[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]Developer Edition 和[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]Enterprise 版本中，執行多部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]允許。 當其中一台執行 BizTalk Server 的電腦無法正常運作時，您可以準備替換的電腦，並將它加入現有的 BizTalk 群組。 此時，您可以將相同名稱或不同名稱的電腦加入 BizTalk 群組。  
  
 如[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]Standard Edition 中，您無法將電腦加入 BizTalk 群組中，因此上述的方法不適合。 相反地，我們概述設定新的電腦和還原所需的步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態設定，讓它可以做為替代函式。 如需詳細資訊，請參閱[如何復原 BizTalk 群組](../core/how-to-recover-the-biztalk-group.md)。  
  
## <a name="recovery-phases"></a>復原階段  
 對執行 BizTalk Server 的電腦進行復原，可以分為下列三個階段：  
  
1.  **準備基底平台**  
  
     這個階段包括基底平台電腦的準備工作，準備的項目包括作業系統、軟體必要元件和適當的 BizTalk Server 元件。 這份指南假設您在嘗試還原 BizTalk Server 組態之前，已經有一台安裝了基底平台、必要元件和 BizTalk Server 元件的電腦。 本指南沒有說明如何還原基底平台。  
  
2.  **還原 BizTalk Server 組態**  
  
     這個階段假設您有失敗的電腦上所設定之功能的記錄，包括該電腦的 BizTalk Server 組態檔複本。 這份指南僅提供還原 BizTalk Server 組態的指導。  
  
3.  **還原 BizTalk 應用程式**  
  
     這個階段包括在替換的電腦上還原與 BizTalk Server 程序所裝載應用程式相連接的 .NET 組件。 所需的任何成品 (例如 BizTalk 組件以外的使用者組件) 都應該各自安裝在電腦上的對應位置或全域組件快取 (GAC) 中。 這份指南提供了一些在此階段的指導， 不過並沒有另外提供用來還原 BizTalk 應用程式的指令碼或工具。  
  
## <a name="see-also"></a>另請參閱  
 [備份和還原 BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md)