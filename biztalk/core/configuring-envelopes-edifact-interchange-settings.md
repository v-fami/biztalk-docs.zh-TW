---
title: 設定信封 （Edifact-interchange 設定） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 501ccc5f-e21c-4c36-9509-217d5b3ba21f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80957d82a70b0fca8a11ace428f87496b45dcb31
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993591"
---
# <a name="configuring-envelopes-edifact-interchange-settings"></a>設定信封 (EDIFACT-Interchange 設定)
本節提供如何設定外寄 EDIFACT 訊息之信封的指示。  
  
> [!IMPORTANT]
>  所有屬性會停都用此頁面上清除**本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
>   
>  只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。 例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 A]-> [合作對象 B**單向協議索引標籤。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-the-interchange-envelope"></a>若要設定交換信封  
  
1. 建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2. 在單向協議索引標籤底下**交換設定**區段中，按一下**信封**。  
  
3. 針對**處理優先順序代碼 (UNB8)**，輸入最少一個字元，最多 1 個字元的字母值。 這是選擇性欄位。  
  
4. 針對**通訊協議 (UNB10)**，輸入最少一個字元，最多 35 個字元的英數字元值。 這是選擇性欄位。  
  
5. 選取 **測試指示符號 (UNB11)** 表示所產生的交換[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是測試資料。  
  
6. 選取 **套用 UNA 區段 （字串服務建議）** 來產生要傳送交換的 UNA 區段。 如果已核取此選項，然後**UNA6**不可為空白並**UNA 6 尾碼**無法**None**。  
  
   > [!NOTE]
   >  您指定**UNA6**並**UNA6 尾碼**中**字元集和分隔符號**頁面中所述[設定字元集和分隔符號 (EDIFACT)](../core/configuring-charset-and-separators-edifact.md).  
  
7. 選取 **套用 UNG 區段 （功能群組標頭）** 功能群組標頭，在外寄訊息中建立群組區段。  
  
8. 按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換設定 (EDIFACT)](../core/configuring-interchange-settings-edifact.md)