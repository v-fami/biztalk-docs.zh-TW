---
title: X12 交易集控制編號已達到 Guest 設定的可接受的最高上限 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e5a4aa5c-13a7-4234-916e-562b52644c51
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b90021a672b3aec71198d8fd6533a2037772346
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014079"
---
# <a name="max-limit-of-acceptable-x12-transaction-set-control-number-has-reached-for-guest-settings"></a>X12 交易集控制編號已達到 Guest 設定的可接受的最高上限
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                            |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                             |
| 產品版本 |                                                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                         |
|    事件識別碼     |                                                                                                     -                                                                                                      |
|  事件來源   |                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                           |
|    元件    |                                                                                                 將 EDI 引擎                                                                                                 |
|  符號名稱  |                                                                                           GlobalX12TsNumberError                                                                                           |
|  訊息文字   | 可接受 X12 交易集控制編號已達到 Guest 設定的最大限制。 瀏覽至 全域設定寄件者角色畫面，欄位 ST 2 在夥伴協議管理員重設計數器 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示傳送管線無法處理外寄 X12 交換，因為交易集控制編號，特別是參考編號欄位 ST02.2 中所述的全域設定，而 ST02 欄位中大於允許的最大值。 交易集控制編號允許的最大值取決於 ST02 中的三個欄位的值。 最大字元數是欄位 UNH1.2，8 UNH1.1 中的前置詞和 UNH1.3，在後置詞的 8 和 9，結合的所有三個欄位中的參考編號的 9。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設的交易集控制編號，參考編號欄位 (ST02.2)，如下所示：  
  
1.  在 EDI 全域屬性 對話方塊中，開啟 GS 和 ST 區段定義頁面。  
  
2.  按一下 編輯欄位與 ST02 欄位相關聯。  
  
3.  新的值設定的群組控制編號 （ST02.2 中的參考編號） 的中間欄位的欄位具有一個可接受的數字。