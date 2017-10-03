---
title: "設定後援識別碼 (X12) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2cb5b32c-96ec-4192-9a10-6668a2cb1195
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58909783b30a0bce855fc56316f687aa9dbc918c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-identifiers-x12"></a>設定後援識別碼 (X12)
在此後援協議中，您必須設定 X12 授權和安全性等屬性，才可以確認該交換的接收者不會是未經授權的使用者。  
  
> [!NOTE]
>  此處所述的交換處理屬性也適用於 HIPAA 交換。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-set-sender-receiver-and-security-properties"></a>設定傳送者、接收者和安全性等屬性  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。  
  
2.  在**X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤，下方**交換設定**區段中，按一下**的識別項**.  
  
3.  輸入的值**ISA1-2 （授權辨識符號和資訊）**。 選取的值**授權辨識符號 (ISA1)**從相關聯的下拉式清單。 如果此值不是**00**，如**值 (ISA2)**文字方塊中，輸入最少一個英數字元，最多 10 個。 這是選擇性欄位。 如果您指定這些值，請確定它們和已接收交換中的 ISA1 與 ISA2 欄位相符，否則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會擱置交換。  
  
4.  輸入的值**ISA3-4 （安全性辨識符號和資訊）**。 選取的值**安全性辨識符號 (ISA3)**從下拉式清單。 如果此值不是**00**，如**值 (ISA4)**文字方塊中，輸入最少一個英數值，最多 10 個。 這是選擇性欄位。 如果這些值與所接收交換中的 ISA3 和 ISA4 欄位值不相符，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會擱置交換。  
  
    > [!NOTE]
    >  值**03-密碼 （用於回溯相容性）**，是為了回溯相容性的[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]將在未來版本中移除。  
  
5.  輸入的值**ISA5-6 （傳送者辨識符號和識別項）**。 選取從辨識符號的值**寄件者識別碼辨識符號 (ISA5)**下拉式清單。 針對該識別碼，在**值 (ISA6)**文字方塊中，輸入最少一個英數字元，最多 15 個字元。  
  
6.  輸入的值**ISA7-8 （接收者辨識符號和識別項）**。 選取從辨識符號的值**接收者識別碼辨識符號 (ISA7)**下拉式清單。 針對該識別碼，在**值 (ISA8)**文字方塊中，輸入最少一個英數字元，最多 15 個字元。  
  
7.  按一下**套用**接受變更，或按一下**確定**輸入並驗證這些變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定 X12 後援協議屬性的交換處理](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)