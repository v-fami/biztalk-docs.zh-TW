---
title: 設定本機主機設定 （EDIFACT 交易集設定） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9f7c9cb9-7b4b-41de-a3f3-c0519b18673c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 912af3a047f77f077bf9de58a25802f3c658e6b0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234198"
---
# <a name="configuring-local-host-settings-edifact-transaction-set-settings"></a>設定本機主機設定 (EDIFACT 交易集設定)
為了處理內送的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必須要判斷它需要用來處理和驗證該交換的結構描述。 這個過程包括判斷與該結構描述相關聯的目標命名空間，以及判斷要使用的結構描述。 您要在這頁合作對象協議中，輸入要用來判斷上述目標命名空間的屬性。 BizTalk Server 如何判斷結構描述中描述[協議解析、 結構描述探索和授權接收 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)。  
  
> [!IMPORTANT]
>  任何屬性已停用**合作對象 a-> 合作對象 B**單向協議索引標籤，如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊合作對象 a。不過，所有屬性已停都用中相同頁面**合作對象 B-> 合作對象 A**索引標籤上，如果您建立合作對象 a 時選取此核取方塊  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
## <a name="determining-the-target-namespace"></a>判斷目標命名空間  
 在**自訂目標命名空間**方格中，您可以設定目標命名空間為其中一個隨附於 Microsoft 的標準結構描述命名空間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 在方格中，您將建立關聯的值**目標命名空間**項目的值**UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**， **UNG2.1**，和**UNG2.2**項目。 當 BizTalk 收到之訊息的**UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**， **UNG2.1**，和**UNG2.2**項目符合格線的某列中，BizTalk 會使用對應的命名空間，以判斷它會使用它來處理訊息的結構描述。 您輸入的項目值必須是唯一的。  
  
 如果訊息沒有相符項目與**UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**， **UNG2.1**，和**UNG2.2**方格中，BizTalk Server 的任何資料列中的項目會處理訊息的資料列中使用命名空間的**預設**會檢查資料行。 該命名空間即會做為預設的目標命名空間。 如果找不到任何命名空間，BizTalk 就會使用 `http://schemas.microsoft.com/BizTalk/Edi/Edifact/2006` 的預設命名空間。  
  
> [!NOTE]
>  如果您為格線中的任何欄位輸入設定，然後又要刪除該設定，那麼就必須刪除一整列，否則該頁面將不會讓您通過驗證。  
  
### <a name="to-configure-local-host-settings-for-transaction-sets"></a>若要設定交易集的本機主機設定  
  
1.  建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**交易集設定**區段中，按一下**本機主機設定**。  
  
3.  當交易的一部分設定驗證設定，如果您設定**尾端分隔符號原則**至**選擇性**或**強制**，您可以選取**建立空白針對尾端分隔符號的 XML 標記**將交換傳送者包含尾端分隔符號的空 XML 標記。  
  
4.  選取**使用點 （.） 做為小數分隔符號**BizTalk Server 以啟用含小數的交換建立 XML 訊息中包含點 （.）。  
  
5.  在**自訂目標命名空間**區段中，執行下列動作：  
  
    1.  選取**預設**包含您想要定義的預設目標命名空間的資料列的核取方塊。  
  
    2.  在**UNH2.1**資料行中，指定訊息類型。 (最多 6 個字元)。  
  
    3.  在**UNH2.2**資料行中，指定訊息版本號碼。 (最少 1 個字元，最多 3 個字元)。  
  
    4.  在**UNH2.3**資料行中，指定訊息版次號碼。 (最少 1 個字元，最多 3 個字元)。  
  
    5.  在**UNH2.5**資料行中，指定指派的程式碼。 (最多 6 個字元， 必須是英數字元)。  
  
    6.  在**UNG2.1**資料行中，輸入應用程式傳送者識別最少一個字元和最多 35 個字元的英數字元值。 這是必要欄位。  
  
    7.  在**UNG2.2**資料行中，輸入最少一個字元，最多四個字元的應用程式傳送者代碼辨識符號的英數字元值。 此為選擇性欄位。  
  
    8.  在**目標命名空間**資料行，從下拉式清單中選取或輸入要在格線的任何資料列中的資料項目與交換中的欄位之間不相符時用於交換的目標命名空間。  
  
        > [!NOTE]
        >  這些將是 BizTalk Server 用來與所接收交換之相關值進行比較的值。  
  
    9. 針對其他任何要使用的目標命名空間 重複這些步驟 。  
  
    10. 若要從清單中移除目標命名空間，請在選取的資料列，然後按一下**刪除**。  
  
6.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交易集設定 (EDIFACT)](../core/configuring-transaction-set-settings-edifact.md)