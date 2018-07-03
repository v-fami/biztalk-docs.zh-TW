---
title: 可接受 X12 交易集控制編號已達到合作對象的最高上限 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a402f6d0-4399-47c9-a39a-56d7fa1efa86
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bafbafdd799330b9c34179cfd1949629eee4ca3b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001815"
---
# <a name="max-limit-of-acceptable-x12-transaction-set-control-number-has-reached-for-party"></a>可接受 X12 交易集控制編號已達到合作對象的最高上限
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                      |
| 產品版本 |                                                                 [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                  |
|    事件識別碼     |                                                                                              -                                                                                              |
|  事件來源   |                                                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                    |
|    元件    |                                                                                         將 EDI 引擎                                                                                          |
|  符號名稱  |                                                                                    PartyX12TsNumberError                                                                                    |
|  訊息文字   | 可接受 X12 交易集控制編號已達到合作對象的最高上限{0}。 在接收者角色畫面中，欄位 [ST 2 在夥伴協議] 管理員中瀏覽至合作對象，重設計數器 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示傳送管線無法處理外寄 X12 交換，因為交易集設定中指定合作對象，特別是參考編號欄位 ST02.2 中的 [ST02] 欄位中的控制編號已超過允許的最大值。 交易集控制編號允許的最大值取決於 ST02 中的三個欄位的值。 字元數上限是 9 參考編號欄位 ST02.2，8 ST02.1 中的前置詞和 ST02.3，在後置詞的 8 和 9，結合的所有三個欄位中。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設的交易集控制編號，參考編號欄位 (UNH1.2)，如下所示：  
  
1.  在 EDI 屬性 對話方塊中的 合作對象的交換解析，開啟 UNG 和 UNH 區段定義頁面。  
  
2.  按一下 [UNH1] 欄位相關聯的編輯欄位。  
  
3.  新的值設定交易集控制編號 （UNH1.2 中的參考編號） 的中間欄位的欄位具有一個可接受的數字。