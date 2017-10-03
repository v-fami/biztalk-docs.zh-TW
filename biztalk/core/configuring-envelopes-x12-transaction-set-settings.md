---
title: "設定信封 （X12-交易集設定） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9313a7b9-72fa-4071-8c65-007371643179
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 519062fa4647cdc2c7c39dda19373ff888eaf601
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-envelopes-x12-transaction-set-settings"></a>設定信封 (X12 交易集設定)
在**可以**頁面**交易集設定** 區段中，您可以定義 BizTalk Server 如何產生傳送至合作對象的 X12 編碼交換的 GS 和 ST 區段。 GS 區段可識別並指定 X12 編碼交換的功能群組。 ST 區段則是 X12 編碼交換的訊息標頭。  
  
 在此頁面上，您將相關聯的值**GS1**， **GS2**， **GS3**， **GS4**， **GS5**， **GS7**，和**GS8**資料元素的值與**交易類型**，**版本/版次**，和**目標命名空間**資料元素。 當 BizTalk 決定 BizTalk XML 訊息已設定值**交易類型**，**版本/版次**，和**目標命名空間**格線的某列中的項目BizTalk 將會填入**GS1**， **GS2**， **GS3**， **GS4**， **GS5**， **GS7**，和**GS8**資料元素中之信封的外寄交換使用方格同一列的值。 值**交易類型**，**版本/版次**，和**目標命名空間**必須是唯一的項目。  
  
> [!NOTE]
>  如果您為格線中的任何欄位輸入設定，然後又要刪除該設定，那麼就必須刪除一整列，否則該頁面將不會讓您通過驗證。  
  
> [!NOTE]
>  這個主題也適用於 HIPAA 相關設定。  
  
> [!IMPORTANT]
>  所有屬性已停都用**合作對象 a-> 合作對象 B**單向協議索引標籤，如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**檢查方塊的合作對象 a。不過，在相同頁面上啟用的所有屬性**合作對象 B-> 合作對象 A**索引標籤上，如果您建立合作對象 a 時選取此核取方塊  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-define-the-gs-and-st-segments"></a>若要定義 GS 和 ST 區段  
  
1.  建立 X12 編碼協議中所述[設定一般設定 (X12)](../core/configuring-general-settings-x12.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**交易集設定**區段中，按一下**信封**。  
  
3.  在方格的某一列，輸入下列值：  
  
    -   如**交易類型**欄位中，選取代表 「 交易集識別項代碼，從下拉式清單的值。  
  
    -   如**版本/版次**，輸入最少一個字元，最多 12 個字元的英數字元值。  
  
    -   如**目標命名空間**項目，從下拉式清單中選取值，或輸入命名空間。  
  
        > [!NOTE]
        >  這些值將由 BizTalk Server 用來與其所建置之交換的關聯值進行比較。  
  
4.  在方格的同一列中，輸入下列值：  
  
    -   如**GS1**，從下拉式清單中選取功能代碼的值。 這是選擇性欄位。  
  
    -   如**GS2**，輸入應用程式傳送者最少 2 個字元，最多 15 個字元的英數字元值。 這是必要的欄位。  
  
    -   如**GS3**，輸入最少 2 個字元，最多 15 個字元的應用程式接收者的英數字元值。 這是必要的欄位。  
  
    -   如**GS4**，選取**CCYYMMDD**或**YYMMDD**。 這是選擇性欄位。  
  
    -   如**GS5**，選取**HHMM**， **HHMMSS**，或**[hhmmssdd]**。 這是選擇性欄位。  
  
    -   如**GS7**，從下拉式清單中選取負責單位的值。 這是選擇性欄位。  
  
    -   如**GS8**，輸入最少一個字元，最多 12 個字元的識別文件的英數字元值。 這是選擇性欄位。  
  
        > [!NOTE]
        >  這些會是 BizTalk Server 將在它本身正在建置如果交換的 GS 欄位中輸入的值**交易類型**，**版本/版次**，和**目標命名空間**相同的資料列中的項目都符合與交換關聯。  
  
5.  重複步驟 3 和 4 方格中輸入額外的資料列。  
  
6.  在方格中的一個資料列，按一下 **預設**將它指定為預設資料列。  
  
    > [!NOTE]
    >  如果訊息沒有相符項目與**交易類型**，**版本/版次**，和**目標命名空間**任何資料列，BizTalk Server 中的項目將會填入訊息值與**GS1**， **GS2**， **GS3**， **GS5**， **GS7**，和**GS8**預設列中的項目。 即使訊息沒有具有相符項目，就會使用這些值**交易類型**，**版本/版次**，和**目標命名空間**與預設列的項目。  
  
    > [!NOTE]
    >  如果沒有預設值是已選取，內送文件不符合**交易類型**，**版本/版次**，和**目標命名空間**的任何資料列的項目將會遭到擱置.  
  
7.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交易集設定 (X12)](../core/configuring-transaction-set-settings-x12.md)