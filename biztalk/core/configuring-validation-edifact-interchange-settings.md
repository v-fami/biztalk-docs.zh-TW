---
title: 設定驗證 （EDIFACT 交換設定） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55820ebc-fe21-48a3-8985-1bf4184176ac
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a700282aee9651b8f259c931a460a774f900a4a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999727"
---
# <a name="configuring-validation-edifact-interchange-settings"></a>設定驗證 (EDIFACT-Interchange 設定)
本節提供如何避免重複處理控制編號的指示。  
  
> [!IMPORTANT]
>  沒有屬性會停用此頁面上即使您清除**本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-duplicate-validation"></a>設定重複項驗證  
  
1. 建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2. 在單向協議索引標籤底下**交換設定**區段中，按一下**驗證**。  
  
3. 選取 **交換控制編號 (UNB5)** 核取方塊以啟用接收管線封鎖重複的交換。 如果選取，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會檢查所接收交換的交換控制編號，是否與其他所接收交換的交換控制編號相符。 如果偵測到相符項目時，接收管線不會處理交換。  
  
4. 如果**交換控制編號 (UNB5)** 已選取，在**檢查是否有重複的 UNB5 內**欄位中，輸入檢查重複交換的天數。  
  
5. 選取 **交換中的群組控制編號 (UNG5)** ，避免接收管線處理重複的群組。  
  
6. 選取 [**交易集控制編號 (UNH1)] 群組中**，避免接收管線處理重複的交易設定。  
  
7. 按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換設定 (EDIFACT)](../core/configuring-interchange-settings-edifact.md)