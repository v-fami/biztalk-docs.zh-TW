---
title: "設定信封 （EDIFACT 交易集設定） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec140def-6155-4b8a-8489-6e0a530bd697
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a1d910f52d9ea90ae0c486356a7ecb3b01bf07a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-envelopes-edifact-transaction-set-settings"></a>設定信封 (EDIFACT 交易集設定)
在**信封**頁面**交易集設定** 區段中，您可以定義 BizTalk Server 如何產生傳送至合作對象之 EDIFACT 編碼交換的 UNG 和 UNH 區段。  
  
 UNG 區段是識別和指定 EDIFACT 編碼交換之功能群組的標頭。 其中包含準備功能群組的日期與時間資訊，以及功能群組中文件的類型與版本資訊。  
  
 UNH 區段則是 EDIFACT 編碼交換的訊息標頭區段。 它提供訊息類型以及負責維護訊息類型發佈之代理商的相關資訊。 此區段會指示交換內文件的起始處，以及後面接著的文件的類型。  
  
 在**功能群組標頭 (UNG)**  區段中，您將建立關聯**UNG**值與**UNH**值和命名空間。 BizTalk Server 判斷 BizTalk XML 訊息已設定值**UNH**項目和**目標命名空間**格線資料列，在 BizTalk Server 將會填入**UNG**資料元素，使用方格同一列的值。 值**UNH**項目和**目標命名空間**必須是唯一的。  
  
 如果訊息沒有相符項目與**UNH**項目和**目標命名空間**中任何資料列，BizTalk Server 將會填入值的訊息**UNG**預設資料列中的項目。 即使訊息沒有具有相符項目，就會使用這些值**UNH**項目和**目標命名空間**與預設列。  
  
 當 BizTalk 引擎決定 BizTalk XML 訊息具有為 UNH 項目和目標命名空間設定的值時，引擎會以為它們設定在方格中，提供的值填入訊息中的 UNG 元素**建立群組區段**核取方塊。  
  
> [!NOTE]
>  在**功能群組標頭 (UNG)**區段中，如果您在方格中，輸入欄位的任何設定，然後又刪除該設定，您必須刪除一整列，或該頁面將會通過驗證。  
  
> [!IMPORTANT]
>  所有屬性已停都用**合作對象 a-> 合作對象 B**單向協議索引標籤，如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**檢查方塊的合作對象 a。不過，在相同頁面上啟用的所有屬性**合作對象 B-> 合作對象 A**索引標籤上，如果您建立合作對象 a 時選取此核取方塊  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-define-the-ung-and-unh-segments"></a>若要定義 UNG 和 UNH 區段  
  
1.  建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**交易集設定**區段中，按一下**信封**。  
  
3.  在格線的某列中，輸入下列值：  
  
    -   在**針對訊息類型 UNH2.1**資料行中，輸入交易集類型。 (最多 6 個字元)。  
  
    -   在**UNH2.2**資料行中，輸入訊息版本號碼。 (最少 1 個字元，最多 3 個字元)。  
  
    -   在**UNH2.3**資料行中，輸入訊息版次號碼。 (最少 1 個字元，最多 3 個字元)。  
  
    -   在**UNH2.5**資料行中，輸入指定的代碼。 (最多 6 個字元。 必須是英數字元)。  
  
    -   在**目標命名空間**資料行中，選取的結構描述的目標命名空間。 這是必要的欄位。  
  
        > [!NOTE]
        >  這些值將由 BizTalk Server 用來與其所建置之交換的關聯值進行比較。  
  
4.  在格線的相同列中，輸入下列值：  
  
    -   如**UNG1** （功能群組識別），輸入最少一個字元，最多六個字元的英數字元值。 這是必要的欄位。  
  
    -   如**UNG2.1** （應用程式傳送者識別），輸入最少一個字元，最多 35 個字元的英數字元值。 這是必要的欄位。  
  
    -   如**UNG2.2** （應用程式傳送者辨識符號），輸入英數值，最多四個字元。 這是選擇性欄位。  
  
    -   如**UNG3.1** （應用程式收件者識別），輸入最少一個字元，最多 35 個字元的英數字元值。 這是必要的欄位。  
  
    -   如**UNG3.2** （應用程式收件者代碼辨識符號，） 輸入最多四個字元的英數字元值。 這是選擇性欄位。  
  
    -   如**UNG6** （控管單位），輸入最少 1 個，最多兩個的英數字元值。 這是必要的欄位。  
  
    -   如**UNG7.1** （訊息類型版本號碼），輸入最少一個字元，最多三個字元的英數字元值。 這是必要的欄位。  
  
    -   如**UNG7.2** （訊息類型版次號碼），輸入最少一個字元，最多三個字元的英數字元值。 這是必要的欄位。  
  
    -   如**UNG7.3** （關聯指定代碼），輸入最少 1 個字元，最多 6 個字元的英數字元值。 這是必要的欄位。  
  
    -   如**UNG8** （應用程式密碼），輸入最少一個字元，最多 14 個字元的英數字元值。 這是必要的欄位。  
  
        > [!NOTE]
        >  這些會是 BizTalk Server 將在它本身正在建置如果交換的 UNG 欄位中輸入的值**針對訊息類型 UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**，和**目標命名空間**相同的資料列中的項目都符合與交換關聯。  
  
5.  重複步驟 4 和 5，將其他列輸入到格線中。  
  
6.  在方格中的一個資料列，按一下 **預設**將它指定為預設資料列。  
  
    > [!NOTE]
    >  如果訊息沒有相符項目與**UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**，和**的目標命名空間**任何資料列，BizTalk Server 中的項目將會填入訊息的值**UNG1**， **UNG2.1**， **UNG2.2**， **UNG3.1**， **UNG3.2**， **UNG6**， **UNG7.1**， **UNG7.2**， **UNG7.3**，和**UNG8**預設列中的項目。 即使訊息沒有具有相符項目，就會使用這些值**針對訊息類型 UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**，和**目標命名空間**與預設列的項目。  
  
    > [!NOTE]
    >  如果沒有預設值的資料列已選取，而且訊息沒有相符的項目**UNH2.1**， **UNH2.2**， **UNH2.3**， **UNH2.5**，和**目標命名空間**項目中任何資料列，BizTalk 會擱置該訊息。  
  
7.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交易集設定 (EDIFACT)](../core/configuring-transaction-set-settings-edifact.md)