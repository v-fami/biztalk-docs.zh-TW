---
title: 設定後援驗證屬性 (EDIFACT) |Microsoft 文件
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
ms.openlocfilehash: bf0e103eb2e20bb64973cd207ed2a55c2f91e58d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233198"
---
# <a name="configuring-fallback-validation-properties-edifact"></a>設定後援驗證屬性 (EDIFACT)
本節提供如何避免重複處理控制編號的指示。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-duplicate-validation"></a>設定重複項驗證  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。  
  
2.  在**EDIFACT 後援設定**對話方塊中，於**EDIFACT 協議頁面**索引標籤，下方**交換設定**區段中，按一下**驗證**.  
  
3.  選取**交換控制編號 (UNB5)** 核取方塊以啟用接收管線封鎖重複的交換。 如果選取，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會檢查所接收交換的交換控制編號，是否與其他所接收交換的交換控制編號相符。 如果偵測到相符項目時，接收管線不會處理交換。  
  
4.  如果**交換控制編號 (UNB5)** 選取時，在**檢查重複的 unb5 內**欄位中，輸入檢查重複交換的天數。  
  
5.  選取**交換中的群組控制編號 (UNG5)** ，避免接收管線處理重複的群組。  
  
6.  選取**交易集控制編號 (UNH1) 中群組**，避免接收管線處理重複的交易設定。  
  
7.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDIFACT 後援協議屬性的交換處理](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)