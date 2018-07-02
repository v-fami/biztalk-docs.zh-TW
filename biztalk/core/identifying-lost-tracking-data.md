---
title: 識別遺失的追蹤資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data loss, HAT
- reporting tools
- Orchestration Debugger
- Tracking database, data loss
- HAT, data loss
- HAT, Operation View tool
- HAT, reporting tools
- Operation View tool, MessageBox database
- MessageBox database, Operation View tool
- Operation View tool, data loss
ms.assetid: 1ac13e2c-cd5e-437e-b924-d4547931874e
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17116d3a560e968e8dd9da0e42f5af221c23f5d3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982855"
---
# <a name="identifying-lost-tracking-data"></a>識別遺失的追蹤資料
您可以使用 BizTalk Server 管理主控台，幫助您識別哪些追蹤資料因為硬體失敗而遺失。 您可以使用 BizTalk Server 管理主控台的即時或封存的資料。  
  
 您可以使用 BizTalk Server 管理主控台來判斷復原 MessageBox 時哪些服務為作用中。 因為復原資料庫的時間與發生硬體錯誤的時間之間有差距，您可能無法判斷部分交易的狀態。  
  
 您可以使用追蹤資料來識別哪些服務執行個體完成，而且啟動之後的復原點，如下所示：  
  
- 尋找自您最後一次備份資料庫之後已完成或啟動的執行個體。  
  
- 如果 BizTalk 追蹤 (BizTalkDTADb) 資料庫中的資料指出訊息已啟動但尚未完成，且訊息不在資料庫中，則會在最後一次備份後傳送該訊息。  
  
  追蹤可以報告完成時，任何服務，可能表示服務已啟動。 追蹤資料會先存放在 MessageBox 中，然後再移動到 BizTalk 追蹤資料庫。 存放的資料可能已在 BAM 事件匯流排服務的積存中遺失。  
  
  當所有資料庫因操作因素需要還原為相同的標記時，您可以封存模式來使用 BizTalk 追蹤資料庫 (未遺失的)，以查看標記之後發生了什麼事。  
  
  如果追蹤會顯示已完成的服務執行個體，您可以終止該執行個體。 它可能會顯示在復原時間點之後啟動的執行個體。 如果是這樣，您將需要補償這些執行個體執行的任何動作，然後重新提交它們的初始啟動訊息。  
  
  若要查看執行，然後使用 若要查看哪些訊息應已傳送或接收的 訊息流程的最後一個圖形，您可以使用協調流程偵錯工具。  
  
  如果 BizTalk 追蹤資料庫遺失，必須使用外部系統報告機制來探索還原時間點之後發生的所有動作。  
  
## <a name="see-also"></a>另請參閱  
 [解決資料遺失](../core/resolving-data-loss.md)