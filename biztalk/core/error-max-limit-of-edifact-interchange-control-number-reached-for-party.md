---
title: 對象已達到可接受 Edifact 交換控制編號的最高上限 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5c00c357-4c7b-42ea-a031-15bad0195a75
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c11029af5b2f87e4e1bf3e7fc4225bfc5ba46105
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998199"
---
# <a name="max-limit-of-acceptable-edifact-interchange-control-number-has-reached-for-party"></a>對象已達到可接受 Edifact 交換控制編號的最高上限
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                      |
| 產品版本 |                                                                  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                  |
|    事件識別碼     |                                                                                              -                                                                                               |
|  事件來源   |                                                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                    |
|    元件    |                                                                                          將 EDI 引擎                                                                                          |
|  符號名稱  |                                                                                  PartyEdifactUnbNumberError                                                                                  |
|  訊息文字   | 對象已達到可接受 Edifact 交換控制編號的最高上限{0}。 瀏覽至合作對象中接收者角色畫面中，在夥伴協議 管理員中的欄位 UNB 5，重設計數器 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄交換因為已在合作對象設定中，特別是參考編號欄位 UNB5.2，在指定的 UNB5 欄位中的交換控制編號大於允許的最大值。 交換控制編號允許的最大值取決於 UNB5 中的三個欄位的值。 字元數上限為 14 個欄位 UNB5.2，13 個 UNB5.1 中的前置詞和 UNB5.3，在後置詞的 13 和 14 個結合的所有三個欄位中的參考編號。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設的交換控制編號，參考編號欄位 (UNB5.2)，如下所示：  
  
1.  在 EDI 屬性 對話方塊中的 合作對象的交換解析，開啟做為交換接收者的合作對象的 UNB 區段定義 頁面。  
  
2.  按一下 [UNB5] 欄位相關聯的編輯欄位。  
  
3.  新的值設定交換控制編號 （UNB5.2 中的參考編號） 的中間欄位的欄位具有一個可接受的數字。