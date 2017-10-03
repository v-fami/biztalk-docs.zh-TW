---
title: "如何建立接續 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities, relating events
- tracking profiles, relating events
- continuations, tracking profiles
- activities, continuations
- events, relating
- orchestrations, business events
- tracking profiles, updating
- activities, tracking profiles
- tracking profiles, continuations
- tracking profiles, connecting activities
ms.assetid: 31d6fc24-676e-418c-8e78-1a46b045905d
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e63983b290f0f4d7dff544cd2faea45f6cf46adc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-continuation"></a>如何建立接續
您可以建立接續，以指出在一或多個協調流程中，哪些商務事件是經由建構連接的活動而相互關聯。  
  
> [!IMPORTANT]
>  如果活動包含 BAM 接續，更新追蹤設定檔可能會影響進行中的活動執行個體。 特別是，如果更新追蹤設定檔時指定由下游攔截的活動項目資料已有記錄，就可能覆寫原始值。 基本上，任何的單一事件資料流都不會受到套用追蹤設定檔更新所影響，因為每個資料流物件均與活動/資料流開始時即已備妥的設定檔特定版本緊密繫結。  但是，由於接續是將多個事件資料流相互關聯的方法，在設定檔更新時還未開始的資料流將會接受更新所指定的變更，以致可能發生上述的資料覆寫情況。  
  
> [!NOTE]
>  您可以建立接續不會處理訊息的協調流程。 只要在協調流程之間傳遞執行呼叫參數，並使用 BAM API 處理接續，就能獲得有如處理訊息之協調流程般相同的功能。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須已部署所要連接的 BAM 活動定義和協調流程。  
  
### <a name="to-create-a-continuation"></a>建立接續  
  
1.  開啟現有的追蹤設定檔或建立追蹤設定檔。 如需建立追蹤設定檔的資訊，請參閱[如何建立追蹤設定檔](../core/how-to-create-a-tracking-profile.md)。  
  
2.  識別*接續 token、*這是一段唯一資訊提供給這兩個活動。 例如，如果**CreditHistory**活動所發出的訊息啟動**LoanProcess**活動內**EquityLoan**協調流程、 的 SSN 欄位訊息可用來當作接續 token，所以這兩個活動通用的。  
  
3.  以滑鼠右鍵按一下活動，然後選取**新的接續**來建立接續 (CreditHistory)。 請為新建立的接續節點命名。  
  
4.  在 [協調流程排程檢視] 下，選取您在步驟 2 所選的接續 Token，例如 SSN (本例是從「傳送」動作選取)，然後將它放置到步驟 3 建立的接續節點上。  
  
5.  以滑鼠右鍵按一下活動，然後選取**新 ContinuationID**建立接續識別碼節點。 請以您在步驟 3 中選擇的名稱為其命名，並將其拖放到含有對應資料項目 (在此情況下為「接收」動作之 SSN) 的節點中。  
  
6.  在**檔案**功能表上，按一下 **另存新檔**，將追蹤設定檔儲存為 BizTalk 管理資料庫中的.btt 檔案，以免覆寫任何現有的.btt 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [Continuation 和 ContinuationID 節點](../core/continuation-and-continuationid-nodes.md)   
 [建立追蹤設定檔](../core/creating-tracking-profiles.md)