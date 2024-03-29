---
title: 設定後援通知屬性 (X12) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce33f5dd-fbd5-448c-8ea3-05dd1467131a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed4ce98bd4191d79ef05742b389e1d065325d8ed
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008975"
---
# <a name="configuring-fallback-acknowledgement-properties-x12"></a>設定後援通知屬性 (X12)
在後援協議中，您可以指定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在收到來自合作對象的 X12 編碼交換後，應如何產生通知，以及應對合作對象傳回哪種類型的通知。 本節提供如何進行相同設定的指示。  
  
> [!NOTE]
>  此處所說明的通知屬性也適用於 HIPAA 通知。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-x12-ack-properties"></a>若要設定 X12 通知屬性  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。  
  
2. 在  **X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤之下**交換設定**區段中，按一下**通知**.  
  
3. 選取  **預期 TA1**將技術 (TA1) 通知傳回給交換傳送者。  
  
4. 選取  **預期 997**功能 (997) 通知傳回給交換傳送者。  
  
5. 按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換處理的 X12 後援協議屬性](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)