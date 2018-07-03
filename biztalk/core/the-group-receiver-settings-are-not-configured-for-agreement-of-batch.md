---
title: 未針對批次協議設定群組接收者設定 |Microsoft Docs
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
ms.openlocfilehash: 534d426d192e27bbe7c6c7e866399b42360a8e3a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990639"
---
# <a name="the-group-receiver-settings-are-not-configured-for-agreement-of-batch"></a>未針對批次協議設定群組接收者設定
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                          |
| 產品版本 |                                     [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                      |
|    事件識別碼     |                                                                  -                                                                  |
|  事件來源   |                       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                        |
|    元件    |                                                           批次引擎                                                           |
|  符號名稱  |                                                      GroupReceiverNotSelected                                                       |
|  訊息文字   | 未針對批次協議設定群組接收者設定{0}。 這需要設定，才能進行批次處理。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示已發生兩個條件之一：  
  
-   批次處理協調流程無法驗證，因為未設定 [UNB1.1] 欄位 （適用於 EDIFACT 編碼交換），其中包含編碼的語法已收到的批次項目。  
  
-   批次處理協調流程無法建立批次元素的信封設定，因為尚未完成的標頭屬性 (針對 X12 的 ISA、 GS 和 ST 屬性交換] 或 [EDIFACT 交換的 UNA、 UNB、 UNG 和 UNH 屬性)。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  
  
-   如果批次處理協調流程無法驗證，因為未設定編碼的語法已收到的批次項目，設定 [UNB1.1] 欄位的編碼語法中的 [EDI 屬性] 對話方塊中的 [UNB 區段定義] 頁面。  
  
-   如果批次處理協調流程無法建立批次元素的信封設定，因為尚未完成的標頭屬性，確定交換是的 X12 的 ISA、 GS 和 ST 屬性設定或 UNA、 UNB、 UNG 和 UNH 屬性設定 EDIFACT 交換。