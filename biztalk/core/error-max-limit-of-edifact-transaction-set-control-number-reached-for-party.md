---
title: 可接受 Edifact 交易集控制編號已達到合作對象的最高上限 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a64cc5d3-a845-4044-9c6e-879ecda15fce
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85fd53beb1484d1e9ffbddf1bbc4f4ac69ae1e67
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004535"
---
# <a name="max-limit-of-acceptable-edifact-transaction-set-control-number-has-reached-for-party"></a>合作對象的 Edifact 交易集控制編號已達到可接受的最高上限
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                        |
| 產品版本 |                                                                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                    |
|    事件識別碼     |                                                                                                -                                                                                                 |
|  事件來源   |                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                      |
|    元件    |                                                                                            將 EDI 引擎                                                                                            |
|  符號名稱  |                                                                                   GlobalEdifactUnhNumberError                                                                                    |
|  訊息文字   | 可接受 Edifact 交易集控制編號已達到合作對象的最高上限{0}。 請瀏覽至 [夥伴協議] 管理員中接收者角色畫面中的 [合作對象]，欄位 [UNH 1]，重設計數器 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示傳送管線無法處理外寄交換，因為合作對象設定中指定之 UNH1 欄位的交易集控制編號，特別是欄位 UNH1.2 中的參考編號，大於允許的最大值。 交易集控制編號允許的最大值取決於 UNH1 中三個欄位的值。 字元數上限為 14 個欄位 UNH1.2，13 個 UNH1.1 中的前置詞和 UNH1.3，在後置詞的 13 和 14 個結合的所有三個欄位中的參考編號。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設的交易集控制編號，參考編號欄位 (UNH1.2)，如下所示：  
  
1.  在 EDI 屬性 對話方塊中的 合作對象的交換解析，開啟 UNG 和 UNH 區段定義頁面。  
  
2.  按一下 [UNH1] 欄位相關聯的編輯欄位。  
  
3.  新的值設定交易集控制編號 （UNH1.2 中的參考編號） 的中間欄位的欄位具有一個可接受的數字。