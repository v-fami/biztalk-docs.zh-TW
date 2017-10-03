---
title: "如何設定 「 範圍 」 圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scope shape [Orchestration Designer], about Scope shape
- Scope shape [Orchestration Designer], configuring
- Scope shape [Orchestration Designer], variables
- Scope shape [Orchestration Designer]
- configuring [Orchestration Designer], Scope shape
- Scope shape [Orchestration Designer], transactions
ms.assetid: 3c518db0-d68c-4f72-9d5c-48540811e289
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef17f5d1ab94875af118d17551da4334525535fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-scope-shape"></a>如何設定範圍圖形
**範圍**圖形為其內容提供內容架構。 第一個區塊**範圍**圖形是內容區塊或主體中，基本的動作範圍的發生; 它類似 try/catch 陳述式中的 try 區塊。 緊接著內文，**範圍**圖形可能還包含一個或多個例外狀況處理常式區塊和補償區塊。  
  
> [!NOTE]
>  在多重電腦環境中其中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 SQL Server 位於不同的電腦，如果 Coordinated Universal Time (UTC) 是在不同的兩部電腦上則**逾時**您設定的屬性**範圍**圖形可能會比預期的 UTC 時間因為在較早觸發[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 SQL Server 機器未同步處理。 請注意，這並不是時區問題，因為 Coordinated Universal Time 不受時區影響。  
  
### <a name="to-configure-a-scope-shape-as-a-transaction-boundary"></a>若要將範圍圖形設定為交易界限  
  
1.  在 [屬性] 視窗中，設定**交易類型**屬性**不可部分完成**或**長時間執行**。  
  
    > [!NOTE]
    >  協調流程本身必須為長時間執行的交易，您才能將 [交易類型] 設定為 [不可部分完成] 或 [長時間執行]。  
  
2.  如果**交易類型**設**不可部分完成**，然後在 [屬性] 視窗中，指定下列屬性：  
  
    |屬性|Description|  
    |--------------|-----------------|  
    |批次|布林值，決定此交易是否能與其他交易跨越協調流程的多個執行個體，以批次方式執行。 在 BizTalk Server 中絕對不會使用這個屬性，因為 BizTalk Server 並不支援跨越協調流程的多個執行個體，以批次方式進行不可部分完成的執行。 這個屬性會在未來的版本中被取代。|  
    |隔離等級|決定可在並行交易之間存取資料的程度：<br /><br /> 讀取認可，若要避免選取存取在並行交易中的資料修改，直到經過認可的交易。 此選項為 Microsoft SQL Server 的預設設定。<br />可重複讀取 — 需要讀取的鎖定，直到選取的交易完成為止。<br />可序列化 — 防止並行交易修改資料，直到選取的交易完成為止。 此選項是最嚴格的隔離等級。|  
    |重試|布林值，決定此交易是否在發生錯誤時重試。 預設值為 **True**。 **注意：**如果擲回 Microsoft.XLANG.BaseTypes.RetryTransactionException，或是協調流程引擎無法存放其狀態或認可的交易不可部分完成的交易將會重試。|  
    |逾時|決定由於閒置而視為交易失敗的時間 (以秒為單位)。 如果不想使用逾時，請將此屬性的值設定為 0。 **注意：**這是 DTC 逾時，協調流程引擎不會強制執行。 唯有對於不可部分完成的交易，引擎才不會中斷交易。 在認可之前，引擎都會正常地繼續進行。此時唯有在透過 DTC 交易內的一個物件參與的情況下，認可才會失敗。|  
  
3.  如果**交易類型**設**長時間執行**，然後在 [屬性] 視窗中，指定下列屬性：  
  
    |屬性|Description|  
    |--------------|-----------------|  
    |逾時|決定由於交易逾時而視為失敗之交易的時間 (以秒為單位)。 如果不想使用逾時，請將此屬性的值設定為 0。|  
  
### <a name="to-configure-a-scope-shape-to-contain-local-variables"></a>若要設定範圍圖形以包含區域變數  
  
1.  在 [協調流程檢視] 視窗中，按兩下範圍。  
  
2.  以滑鼠右鍵按一下範圍下的 [變數] 資料夾，然後按一下**新變數**。  
  
3.  在中繼續執行步驟 2 中 [加入變數][如何新增協調流程變數](../core/how-to-add-orchestration-variables.md)。