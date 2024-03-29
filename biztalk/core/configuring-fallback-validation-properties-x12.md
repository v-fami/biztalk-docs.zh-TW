---
title: 設定後援驗證屬性 (X12) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a64431d-373a-4d63-9b83-cbb323620152
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34f9dca1416b106e951b32efe79d18260201dc48
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973927"
---
# <a name="configuring-fallback-validation-properties-x12"></a>設定後援驗證屬性 (X12)
X12 交換驗證產生後援設定定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 如何在收到的交換中檢查重複的控制編號。  
  
> [!NOTE]
>  此處所說明的設定也適用於 HIPAA 交換驗證。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-validation"></a>若要設定驗證  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。  
  
2. 在  **X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤之下**交換設定**區段中，按一下**驗證**.  
  
3. 選取 **交換控制編號**核取方塊以啟用接收管線封鎖重複的交換。 若選取上述核取方塊，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會檢查該交換控制編號，確定所接收交換的交換控制編號 (ISA13) 與該交換控制編號不相符。 如果偵測到相符項目時，接收管線不會處理交換。  
  
4. 如果**交換控制編號**已選取，在**檢查是否有重複的 ISA13 內**欄位中，輸入將使用特定執行檢查重複交換的天數交換控制編號。  
  
5. 選取 **群組控制編號**，避免接收管線處理具有重複群組控制編號 (GS6) 的交換。  
  
6. 選取 **交易集控制編號**，避免接收管線處理具有重複交易集控制編號 (ST2) 的交換。  
  
7. 按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換處理的 X12 後援協議屬性](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)