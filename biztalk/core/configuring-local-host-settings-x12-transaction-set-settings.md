---
title: 設定本機主機設定 （X12-交易集設定） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e31b41c3-49fc-46ef-ab69-889e30dfc58e
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fcc099535e6a7b96c5c4bbdd29112da46af3522
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234302"
---
# <a name="configuring-local-host-settings-x12-transaction-set-settings"></a>設定本機主機設定 (X12 交易集設定)
為了處理內送的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必須要判斷它需要用來處理和驗證該交換的結構描述。 這個過程包括判斷與該結構描述相關聯的目標命名空間，以及判斷要使用的結構描述。 您要在這頁合作對象協議中，輸入要用來判斷上述目標命名空間的屬性。 如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]判斷結構描述所述[協議解析、 結構描述探索和授權接收 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)。  
  
> [!NOTE]
>  這個主題也適用於 HIPAA 相關設定。  
  
> [!IMPORTANT]
>  任何屬性已停用**合作對象 a-> 合作對象 B**單向協議索引標籤，如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊合作對象 a。不過，所有屬性已停都用中相同頁面**合作對象 B-> 合作對象 A**索引標籤上，如果您建立合作對象 a 時選取此核取方塊  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
## <a name="determining-the-target-namespace"></a>判斷目標命名空間  
 在**自訂目標命名空間**方格中，您可以將目標命名空間設其中一個命名空間的標準結構描述隨附[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 在方格中，您將建立關聯的值**目標命名空間**項目的值應用程式傳送者 (**GS2**) 和交易集識別項代碼 (**ST1**)。 當 BizTalk 收到之訊息的**GS2**和**ST1**資料項目符合方格的資料列中，BizTalk 會使用對應的命名空間來處理訊息。 您輸入的項目值必須是唯一的。  
  
 如果訊息沒有相符項目與**GS2**和**ST1**資料方格中，BizTalk Server 的任何資料列中的項目會處理訊息的資料列中使用命名空間的**預設**會檢查資料行。 該命名空間即會做為預設的目標命名空間。 如果找不到任何命名空間，BizTalk Server 就會使用 `http://schemas.microsoft.com/BizTalk/Edi/EDIFACT/2006` 的預設命名空間。  
  
> [!NOTE]
>  如果您為格線中的任何欄位輸入設定，然後又要刪除該設定，那麼就必須刪除一整列，否則該頁面將不會讓您通過驗證。  
  
> [!NOTE]
>  如需這個方格的使用示範，請完整執行 EDI 介面開發人員教學課程，並特別注意設定要交換接收來源的合作對象。 如需詳細資訊，請參閱[步驟 4： 為您的交易夥伴設定合作對象與商務設定檔](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner1.md)。  
  
### <a name="to-configure-local-host-settings-for-transaction-sets"></a>若要設定交易集的本機主機設定  
  
1.  建立 X12 編碼協議中所述[設定一般設定 (X12)](../core/configuring-general-settings-x12.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**交易集設定**區段中，按一下**本機主機設定**。  
  
3.  選取**轉換隱含的小數格式 Nn 10 進制數值**来轉換成 BizTalk Server 中的中繼 XML 中的基底 10 數值將格式 Nn 指定的 EDI 數字。  
  
    > [!NOTE]
    >  轉換後，中繼 XML 可能會在長度驗證時失敗。 這是因為以 10 為基底的數值格式包含小數點，這使得它的長度比 Nn 格式數字大一。 您可以藉由新增的值來解決這個問題**1**最小/最大長度值。  
  
4.  當交易的一部分設定驗證設定，如果您設定**尾端分隔符號原則**至**選擇性**或**強制**，您可以選取**建立空白針對尾端分隔符號的 XML 標記**將交換傳送者包含尾端分隔符號的空 XML 標記。  
  
5.  在**自訂目標命名空間**區段中，執行下列動作：  
  
    1.  選取**預設**包含您想要定義的預設目標命名空間的資料列的核取方塊。  
  
    2.  在**針對 ST1**資料行中，選取一個值的交易集識別項代碼，從下拉式清單。  
  
    3.  在**GS2**資料行中，輸入應用程式傳送者最少 2 個字元，最多 15 個字元的英數字元值。 這是必要的欄位。  
  
    4.  在**目標命名空間**資料行，從下拉式清單中選取或輸入要在格線的任何資料列中的資料項目與交換中的欄位之間不相符時用於交換的目標命名空間。  
  
        > [!NOTE]
        >  這些將是 BizTalk Server 用來與所接收交換之相關值進行比較的值。  
  
    5.  針對其他任何要使用的目標命名空間 重複這些步驟 。  
  
    6.  若要從清單中移除目標命名空間，請在選取的資料列，然後按一下**刪除**。  
  
6.  按一下**套用**接受變更，或按一下**確定**輸入並驗證這些變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交易集設定 (X12)](../core/configuring-transaction-set-settings-x12.md)