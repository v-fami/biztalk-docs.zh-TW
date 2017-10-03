---
title: "設定後援本機主機設定 （EDIFACT-交換設定） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eecf5abb-9c12-44b0-bc58-94cb138515c3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6dc98c62870632501c5b5330ed72ad5aee971fdd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-local-host-settings-edifact-interchange-settings"></a>設定後援本機主機設定 (EDIFACT 交換設定)
本機主機設定控制了處理 EDI 交換的方式。 此頁面上的設定可分成兩個類別 - 接收者的設定 (用於內送交換) 與傳送者的設定 (用於外寄交換)。 在接收者的設定中，您可以指定通知控制編號的產生方式。 在傳送者的設定中，您可以指定為外寄訊息產生控制編號的方式。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-local-host--receivers-settings"></a>若要設定本機主機 - 接收者的設定  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。  
  
2.  在**EDIFACT 後援設定**對話方塊中，於**EDIFACT 協議頁面**索引標籤，下方**交換設定**區段中，按一下**本機主機設定**。  
  
3.  在**EDIFACT 通知**區段中，指定要用於通知，交易集參考編號的前置詞、 參考編號和後置詞範圍輸入的值。  
  
     按一下**重設**重設目前的交易集參考編號為下限。 選取**重設為下限超出範圍時**有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]參考編號重設的範圍值下限，如果超過最大限制。  
  
### <a name="to-configure-local-host--senders-settings"></a>若要設定本機主機 - 傳送者的設定  
  
1.  如**交換控制編號 (UNB5)**，輸入要由 BizTalk Server 產生外寄交換時使用的交換控制編號值範圍。 輸入最小為 1，最大為 999999999 的數值。 這是必要的欄位。  
  
    > [!NOTE]
    >  第一個欄位 (**UNB5.1**) 是前置詞; 第二個和第三個欄位 (**UNB5.2**) 包含要做為交換控制編號; 和第四個欄位的數字範圍 (**UNB5.3**)是後置詞。 前置詞和後置詞是選擇性的；控制編號是必要的。 控制編號會隨著每一個新訊息而遞增；前置詞和後置詞則保持不變。 控制編號的字元數上限為 14 個字元，前置詞和後置詞上限為 13 個字元，而三個欄位總共不得超過 14 個字元。  
    >   
    >  若要控制編號重設指定的最小值，請按一下**重設** 按鈕。 請檢查**重設為下限超出範圍時**自動重設的最小值為 如果超出最大值。  
  
2.  如**群組控制編號 (UNG5)**、 輸入前置詞、 參考編號範圍和 BizTalk Server 應該使用它所傳送之第一個交換的群組控制編號的尾碼。  
  
    > [!NOTE]
    >  第一個欄位 (**UNG5.1**) 是前置詞; 第二個和第三個欄位 (**UNG5.2**) 包含要用於群組控制編號; 和第四個欄位的數字的範圍 (**UNG5.3**) 是後置詞。 前置詞和後置詞是選擇性的；控制編號是必要的。 控制編號會隨著每一個新訊息而遞增，直到達到最大值；前置詞和後置詞則保持不變。 數字中允許**UNG5.2**。 控制編號的字元數上限為 14 個字元，前置詞和後置詞上限為 13 個字元，而三個欄位總共不得超過 14 個字元。  
    >   
    >  若要重設的群組控制編號，指定的最小值，請按一下**重設** 按鈕。 請檢查**重設為下限超出範圍時**自動重設的最小值為 如果超出最大值。  
  
3.  如**訊息標頭 (UNH)**，按一下 **套用新識別碼**、 輸入前置詞、 輸入參考編號範圍，然後輸入 BizTalk Server 應用於交易集參考編號的尾碼。  
  
    > [!NOTE]
    >  第一個欄位 (**UNH1.1**) 是前置詞; 第二個和第三個欄位 (**UNH1.2**) 是參考編號範圍，而第四個欄位 (**UNH1.3**) 是後置詞。 前置詞和後置詞是選擇性的；參考編號則是必要的。 參考編號會隨著每一個新訊息而遞增；前置詞和後置詞則保持不變。 參考編號的預設值範圍是 1 到 99999999999999。 數字中允許**UNH1.2**。 控制編號的字元數上限為 14 個字元，前置詞和後置詞上限為 13 個字元，而三個欄位總共不得超過 14 個字元。  
    >   
    >  若要重設目前的交易集控制編號的最小值，請按一下**重設**。 選取**重設為下限超出範圍時**控制編號重設的最小值，如果尚未超過最大值。  
  
4.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDIFACT 後援協議屬性的交換處理](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)