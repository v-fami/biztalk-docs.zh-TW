---
title: 設定後援通知屬性 (EDIFACT) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6062b881-3214-4e68-acbc-1f8c255fd86b
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1422e524d9527b5e7e5362d5867654026cc03768
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974175"
---
# <a name="configuring-fallback-acknowledgement-properties-edifact"></a>設定後援通知屬性 (EDIFACT)
在後援協議中，您可以指定要傳回給合作對象的通知類型。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-edifact-ack-contrl-properties"></a>若要設定 EDIFACT 通知 (CONTRL) 屬性  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。  
  
2. 在  **EDIFACT 後援設定**對話方塊中，於**EDIFACT 協議頁面**索引標籤之下**交換設定**區段中，按一下**通知**。  
  
3. 選取 **訊息回條 (CONTRL 預期)** 技術 (CONTRL) 通知傳回給交換傳送者。  
  
4. 選取 **通知 (CONTRL) 必須是**功能 (CONTRL) 通知傳回給交換傳送者。  
  
5. 按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換處理的 EDIFACT 後援協議屬性](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)