---
title: 設定識別項 (EDIFACT) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 097292f2-1aa5-42e4-aeee-c7d4cbdae17c
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 673501923385c956169670eb1dc61e667e611734
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233846"
---
# <a name="configuring-identifiers-edifact"></a>設定識別項 (EDIFACT)
在此夥伴協議中，您必須設定收件者參考密碼，才可以確認該交換的接收者不會是未經授權的使用者。  
  
> [!IMPORTANT]
>  下列屬性會停用此頁面上清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
>   
>  -   **DestinationPartyName**下**其他協議解析程式**> 一節。  
>   
>  只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。 例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 a-> 合作對象 B**單向協議索引標籤。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-set-the-sender-recipient-and-recipient-password"></a>若要設定傳送者、接收者和接收者密碼  
  
1.  建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**交換設定**區段中，按一下**識別碼**。  
  
3.  在**寄件者 (UNB2)** 區段中，執行下列動作：  
  
    1.  如**識別 (UNB2.1)**，輸入最少 1 個，最多 35 個的英數字元值。 這是必要的欄位。  
  
    2.  如**代碼辨識符號 (UNB2.2)**，從下拉式清單中選取值。 這是選擇性欄位。  
  
    3.  如**反向路由位址 (UNB2.3)**，輸入最少一個字元，最多 14 個字元的英數字元值。 這是選擇性欄位。  
  
4.  在**接收者 (UNB3)** 區段中，執行下列動作：  
  
    1.  如**識別 (UNB3.1)**，輸入最少 1 個，最多 35 個的英數字元值。 這是必要的欄位。  
  
    2.  如**代碼辨識符號 (UNB3.2)**，從下拉式清單中選取值。 這是選擇性欄位。  
  
    3.  如**反向路由位址 (UNB3.3)**，輸入最少一個字元，最多 14 個字元的英數字元值。 這是選擇性欄位。  
  
    4.  視需要在**收件者參考密碼 (UNB6)** 區段中，輸入收件者參考密碼的值。 如**值 (UNB6.1)**，輸入最少 1 個，最多 14 個的英數字元值。 如**辨識符號 (UNB6.2)**，輸入最少一個字元，最多兩個字元的英數字元值。 這些是選擇性欄位。 如果這些值與所接收交換中的 UNB6.1 和 UNB6.2 欄位值不相符，BizTalk Server 將會擱置該項交換。  
  
        > [!NOTE]
        >  組合**UNB6.1**和**UNB6.2**必須是唯一的。  
  
        > [!NOTE]
        >  如果同時輸入 UNB6.1 及 UNB6.2 的值並套用變更，然後又清空 UNB6.1，則也會刪除 UNB6.2 中的值，並且停用該欄位。  
  
5.  在**其他協議解析程式** 區段中，針對**DestinationPartyName**屬性，指定目的合作對象的值。 此值也用來將外寄訊息解析為協議。 如需詳細資訊，請參閱[協議解析和外寄 EDI 訊息的結構描述判斷](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)。  
  
    > [!NOTE]
    >  您通常不需要設定**DestinationPartyName**屬性。 此屬性是協議屬性的一部分，用來支援升級案例。 從 BizTalk Server 2006 R2 或 BizTalk Server 2009，升級**DestinationPartyName**屬性設定為在 BizTalk Server 2006 R2 或 BizTalk Server 2009 中的合作對象的名稱。  
  
6.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
    > [!IMPORTANT]
    >  如果您按一下**確定**或**套用**在這個階段，您會收到錯誤。 這是因為您仍需要在上提供 UNB2 與 UNB3 值**識別碼** 索引標籤的 其他單向協議 索引標籤。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換設定 (EDIFACT)](../core/configuring-interchange-settings-edifact.md)