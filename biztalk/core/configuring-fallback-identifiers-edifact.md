---
title: "設定後援識別項 (EDIFACT) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2ce56c1-44f1-42dc-94e8-36e5ba664f53
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81ddf25726d7413727fef1f4f41d99916c18c21d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-identifiers-edifact"></a>設定後援識別項 (EDIFACT)
在後援協議中，您必須設定收件者參考密碼，才可以確認交換的接收者不會是未經授權的使用者。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-set-the-sender-recipient-recipient-password"></a>若要設定傳送者、接收者、接收者密碼  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。  
  
2.  在**EDIFACT 後援設定**對話方塊中，於**EDIFACT 協議頁面**索引標籤，下方**交換設定**區段中，按一下**識別項**.  
  
3.  在**寄件者 (UNB2)**區段中，執行下列動作：  
  
    1.  如**識別 (UNB2.1)**，輸入最少 1 個，最多 35 個的英數字元值。 這是必要的欄位。  
  
    2.  如**代碼辨識符號 (UNB2.2)**，從下拉式清單中選取值。 這是選擇性欄位。  
  
    3.  如**反向路由位址 (UNB2.3)**，輸入最少一個字元，最多 14 個字元的英數字元值。 這是選擇性欄位。  
  
    4.  如**應用程式參考識別碼 (UNB7)**，輸入最少一個字元，最多六個字元的英數字元值。 這是必要的欄位。  
  
4.  在**接收者 (UNB3)**區段中，執行下列動作：  
  
    1.  如**識別 (UNB3.1)**，輸入最少 1 個，最多 35 個的英數字元值。 這是必要的欄位。  
  
    2.  如**代碼辨識符號 (UNB3.2)**，從下拉式清單中選取值。 這是選擇性欄位。  
  
    3.  如**反向路由位址 (UNB3.3)**，輸入最少一個字元，最多 14 個字元的英數字元值。 這是選擇性欄位。  
  
    4.  視需要在**收件者參考密碼 (UNB6)**區段中，輸入收件者參考密碼的值。 如**值 (UNB6.1)**，輸入最少 1 個，最多 14 個的英數字元值。 如**辨識符號 (UNB6.2)**，輸入最少一個字元，最多兩個字元的英數字元值。 這些是選擇性欄位。 如果這些值與所接收交換中的 UNB6.1 和 UNB6.2 欄位值不相符，BizTalk Server 將會擱置該項交換。  
  
        > [!NOTE]
        >  組合**UNB6.1**和**UNB6.2**必須是唯一的。  
  
        > [!NOTE]
        >  如果同時輸入 UNB6.1 及 UNB6.2 的值並套用變更，然後又清空 UNB6.1，則也會刪除 UNB6.2 中的值，並且停用該欄位。  
  
5.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定 EDIFACT 後援協議屬性的交換處理](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)