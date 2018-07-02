---
title: 設定後援驗證屬性 (EDIFACT) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b925d063-e24b-4cfb-acbd-dcadb511011d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4276ad1b5ae995cfb6370377d7d1671ede09bd52
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975447"
---
# <a name="configuring-fallback-validation-properties-edifact"></a>設定後援驗證屬性 (EDIFACT)
本節提供如何避免重複處理控制編號的指示。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-duplicate-validation"></a>設定重複項驗證  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。  
  
2. 在  **EDIFACT 後援設定**對話方塊中，於**EDIFACT 協議頁面**索引標籤之下**交換設定**區段中，按一下**驗證**.  
  
3. 選取 **交換控制編號 (UNB5)** 核取方塊以啟用接收管線封鎖重複的交換。 如果選取，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會檢查所接收交換的交換控制編號，是否與其他所接收交換的交換控制編號相符。 如果偵測到相符項目時，接收管線不會處理交換。  
  
4. 如果**交換控制編號 (UNB5)** 已選取，在**檢查是否有重複的 UNB5 內**欄位中，輸入檢查重複交換的天數。  
  
5. 選取 **交換中的群組控制編號 (UNG5)** ，避免接收管線處理重複的群組。  
  
6. 選取 [**交易集控制編號 (UNH1)] 群組中**，避免接收管線處理重複的交易設定。  
  
7. 按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換處理的 EDIFACT 後援協議屬性](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)