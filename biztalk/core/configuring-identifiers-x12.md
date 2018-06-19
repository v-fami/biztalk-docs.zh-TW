---
title: 設定識別項 (X12) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 665698d1-c46c-4149-9715-381b4966dd92
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4cbe3ce7badc9258e823034e5ed443d6f3d60e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234134"
---
# <a name="configuring-identifiers-x12"></a>設定識別項 (X12)
在夥伴協議中，您必須設定 X12 驗證和安全性等屬性，才可以確認該交換的接收者不會是未經授權的使用者。  
  
> [!NOTE]
>  此處所述的交換處理屬性也適用於 HIPAA 交換。  
  
> [!IMPORTANT]
>  下列屬性會停用此頁面上清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
>   
>  -   **DestinationPartyName**下**其他協議解析程式**> 一節。  
>   
>  只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。 例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 a-> 合作對象 B**單向協議索引標籤。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-set-sender-receiver-and-security-properties"></a>設定傳送者、接收者和安全性等屬性  
  
1.  建立 X12 編碼協議中所述[設定一般設定 (X12)](../core/configuring-general-settings-x12.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**交換設定**區段中，按一下**識別碼**。  
  
3.  輸入的值**ISA1-2 （授權辨識符號和資訊）**。 選取的值**授權辨識符號 (ISA1)** 從相關聯的下拉式清單。 如果此值不是**00**，如**值 (ISA2)** 文字方塊中，輸入最少一個英數字元，最多 10 個。 這是選擇性欄位。 如果您指定這些值，請確定它們和已接收交換中的 ISA1 與 ISA2 欄位相符，否則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會擱置交換。  
  
4.  輸入的值**ISA3-4 （安全性辨識符號和資訊）**。 選取的值**安全性辨識符號 (ISA3)** 從下拉式清單。 如果此值不是**00**，如**值 (ISA4)** 文字方塊中，輸入最少一個英數值，最多 10 個。 這是選擇性欄位。 如果這些值與所接收交換中的 ISA3 和 ISA4 欄位值不相符，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會擱置交換。  
  
    > [!NOTE]
    >  值**03-密碼 （用於回溯相容性）**，是為了回溯相容性的[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]將在未來版本中移除。  
  
5.  輸入的值**ISA5-6 （傳送者辨識符號和識別項）**。 選取從辨識符號的值**寄件者識別碼辨識符號 (ISA5)** 下拉式清單。 針對該識別碼，在**值 (ISA6)** 文字方塊中，輸入最少一個英數字元，最多 15 個字元。  
  
6.  輸入的值**ISA7-8 （接收者辨識符號和識別項）**。 選取從辨識符號的值**寄件者識別碼辨識符號 (ISA7)** 下拉式清單。 針對該識別碼，在**值 (ISA8)** 文字方塊中，輸入最少一個英數字元，最多 15 個字元。  
  
7.  在**其他協議解析程式** 區段中，針對**DestinationPartyName**屬性，指定目的合作對象的值。 此值也用來將外寄訊息解析為協議。 如需詳細資訊，請參閱[協議解析和外寄 EDI 訊息的結構描述判斷](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)。  
  
    > [!NOTE]
    >  您通常不需要設定**DestinationPartyName**屬性。 此屬性是協議屬性的一部分，用來支援升級案例。 從 BizTalk Server 2006 R2 或 BizTalk Server 2009，升級**DestinationPartyName**屬性設定為在 BizTalk Server 2006 R2 或 BizTalk Server 2009 中的合作對象的名稱。  
  
8.  按一下**套用**接受變更，或按一下**確定**輸入並驗證這些變更，然後關閉對話方塊。  
  
    > [!IMPORTANT]
    >  如果您按一下**確定**或**套用**在這個階段，您會收到錯誤。 這是因為您仍需要提供 ISA5 到 ISA8 的值**識別碼** 索引標籤的 其他單向協議 索引標籤。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換設定 (X12)](../core/configuring-interchange-settings-x12.md)