---
title: "設定後援信封屬性 （EDIFACT-交換設定） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8826041e-02fa-4086-a774-d44a388f42b1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6a141b852f85947165d3d3d4d638cf1cb10ccb0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-envelope-properties-edifact-interchange-settngs"></a>設定後援信封屬性 (EDIFACT-交換設定)
本節提供如何設定外寄 EDIFACT 訊息之信封的指示。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-the-interchange-envelope"></a>若要設定交換信封  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。  
  
2.  在**EDIFACT 後援設定**對話方塊中，於**EDIFACT 協議頁面**索引標籤，下方**交換設定**區段中，按一下**信封**.  
  
3.  如**處理優先順序代碼 (UNB8)**，輸入最少一個字元，最多 1 個字元的字母值。 這是選擇性欄位。  
  
4.  如**通訊協議 (UNB10)**，輸入最少一個字元，最多 35 個字元的英數字元值。 這是選擇性欄位。  
  
5.  選取**測試指示符號 (UNB11)**表示所產生的交換[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是測試資料。  
  
6.  選取**套用 UNA 區段 （字串服務建議）**產生要傳送交換的 UNA 區段。 如果已核取此選項，然後**UNA6**不可為空白和**UNA 6 尾碼**不可**無**。  
  
    > [!NOTE]
    >  您指定**UNA6**和**UNA6 尾碼**中**字元集和分隔符號**頁面中所述[設定後援字元集與分隔符號屬性 (EDIFACT)](../core/configuring-fallback-charset-and-separator-properties-edifact.md)。  
  
7.  選取**套用 UNG 區段 （功能群組標頭）**功能群組標頭外寄訊息中建立群組區段。  
  
8.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDIFACT 後援協議屬性的交換處理](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)