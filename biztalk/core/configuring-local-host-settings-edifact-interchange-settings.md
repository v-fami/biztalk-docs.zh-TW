---
title: "設定本機主機設定 （EDIFACT-交換設定） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1cf8696-d1f4-49aa-aa0a-ecf66f55e01d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b93833e8143f1b6706d86295e3f5db8292bc6c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-local-host-settings-edifact-interchange-settings"></a>設定本機主機設定 (EDIFACT 交換設定)
本機主機設定控制了處理 EDI 交換的方式。 此頁面上的設定可分成兩個類別 - 接收者的設定 (用於內送交換) 與傳送者的設定 (用於外寄交換)。 在接收者的設定中，您可以指定輸入批次要分割為交易集或是保留。 若是保留，您就可以指定發生錯誤時，BizTalk Server 要暫停交換或交易集。 在傳送者的設定中，您可以指定為外寄訊息產生控制編號的方式。  
  
> [!IMPORTANT]
>  下列屬性已停用**合作對象 a-> 合作對象 B**單向協議索引標籤，如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**合作對象 a 的核取方塊  
>   
>  -   下的所有屬性**寄件者的設定**> 一節。  
>   
>  同樣地，下列屬性已停用中相同頁面**合作對象 B-> 合作對象 A**索引標籤上，如果您建立合作對象 a 時選取此核取方塊  
>   
>  -   下的所有屬性**接收者的設定**> 一節。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-local-host--receivers-settings"></a>若要設定本機主機 - 接收者的設定  
  
1.  建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**交換設定**區段中，按一下**本機主機設定**。  
  
3.  在**EDIFACT 通知**區段中，指定要用於通知，交易集參考編號的前置詞、 參考編號和後置詞範圍輸入的值。  
  
     按一下**重設**重設目前的交易集參考編號為下限。 選取**重設為下限超出範圍時**有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]參考編號重設的範圍值下限，如果超過最大限制。  
  
4.  清除**通知的路由設定為傳送管線在要求-回應接收埠**透過另外通知傳送埠傳回。 將此屬性保持為選取狀態，即可在與雙向要求-回應接收埠關聯的傳送埠傳回通知。  
  
5.  清除**遮罩安全性/授權/密碼資訊**停用的內容屬性，以避免資訊洩漏中授權/密碼安全性資訊 （UNB6.1 和 UNB6.2 欄位） 的遮罩。  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 收到訊息時，會將 UNB 標頭升級至訊息的內容中。 在沒有遮罩的情況下，任何具有系統管理員權限的人員都可以存取內容中的安全性資訊。 若要遮罩此資訊，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]取代資訊的每一個字元 **#** 字元。 這是單向的程序：  **#** 字元無法轉換成實際的字元。  
  
6.  在**輸入批次處理選項**下拉式清單中，執行下列動作：  
  
    1.  選取預設選項**將交換分割為交易集-發生錯誤時暫停交易集**以指定 BizTalk Server 應該剖析每個交易集在個別的 XML 文件的交換。 然後，BizTalk Server 便會將適當的信封套用至交易集，並將交易集文件路由到 MessageBox 中。 使用此選項時，如果交換中的一或多個交易集驗證失敗，BizTalk Server 將只會暫停這些交易集。  
  
    2.  選取**將交換分割為交易集-發生錯誤時暫停交換**以指定 BizTalk Server 應該剖析每個交易集在個別的 XML 文件的交換。 然後，BizTalk Server 便會將適當的信封套用至交易集，並將交易集文件路由到 MessageBox 中。 使用此選項時，如果交換中的一或多個交易集的驗證失敗，BizTalk Server 便會暫停整個交換。  
  
    3.  選取**保留交換-發生錯誤時暫停交換**以指定 BizTalk Server 應該讓交換保持完整，建立整個批次交換的 XML 文件。 使用此選項時，如果交換中的一或多個交易集的驗證失敗，BizTalk Server 便會暫停整個交換。  
  
    4.  選取**保留交換-發生錯誤時暫停交易集**以指定 BizTalk Server 應該讓交換保持完整，建立整個批次交換的 XML 文件。 使用此選項時，如果交換中的一或多個交易集的驗證失敗，BizTalk Server 便只會暫停這些交易集，但繼續處理其他所有的交易集。  
  
        > [!NOTE]
        >  如果您選取**保留交換-發生錯誤時暫停交換**或**保留交換-發生錯誤時暫停交易集**上的屬性設定**ISA 區段定義**和**GS 和 ST 區段定義**（負責決定 BizTalk Server 如何建立外寄交換的 ISA、 GS 和 ST 標頭） 的頁面不會套用。 該交換、群組，以及將保留之交換中的交易集標頭，都會在傳送管線處理該交換的傳送時加以保留。  
  
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
 [設定交換設定 (EDIFACT)](../core/configuring-interchange-settings-edifact.md)