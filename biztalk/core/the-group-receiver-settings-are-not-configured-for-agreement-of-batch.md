---
title: 群組接收者設定未批次的協議設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57b205e9-aaab-43d1-b373-17d206957814
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ea41ad5c8de88e446a86745b57ff282d5b90af5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279070"
---
# <a name="the-group-receiver-settings-are-not-configured-for-agreement-of-batch"></a>群組接收者設定未批次的協議設定
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|批次處理引擎|  
|符號名稱|GroupReceiverNotSelected|  
|訊息文字|群組接收者設定未批次 {0} 的協議設定。 這必須設定批次處理才能繼續。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示已發生兩個條件的其中一個：  
  
-   批次處理協調流程無法驗證因為沒有設定 UNB1.1 欄位 （適用於 EDIFACT 編碼交換），其中包含編碼的語法已收到的批次項目。  
  
-   批次處理協調流程無法建立批次項目的信封設定值，因為未完成的標頭屬性 (x12 的 ISA、 GS 和 ST 屬性交換] 或 [EDIFACT 交換的 UNA、 UNB、 UNG 和 UNH 屬性)。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列其中一項：  
  
-   如果批次處理協調流程無法驗證，因為沒有設定編碼的語法已收到的批次項目，UNB1.1 欄位的編碼語法中設定 EDI 屬性 對話方塊的 UNB 區段定義 頁面。  
  
-   如果批次處理協調流程無法建立批次項目的信封設定值，因為未完成的標頭屬性，確定交換是的 X12 的 ISA、 GS 和 ST 屬性設定或 UNA、 UNB、 UNG 和 UNH 屬性設定 EDIFACT 交換。