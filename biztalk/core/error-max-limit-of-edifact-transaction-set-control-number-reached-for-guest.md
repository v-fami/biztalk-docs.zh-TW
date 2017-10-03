---
title: "可接受 Edifact 交易集控制編號已達到 Guest 設定的最高上限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3924a18c-87bc-4727-b7cd-598d3e5ade2a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 709d6069d143cea2271e6311fad571a0290133db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-edifact-transaction-set-control-number-has-reached-for-guest-settings"></a>Guest 設定的 Edifact 交易集控制編號已達到可接受的最高上限
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|GlobalEdifactUnhNumberError|  
|訊息文字|Guest 設定的 Edifact 交易集控制編號已達到可接受的最高上限。 請瀏覽至 [夥伴協議] 管理員中的全域組態接收者角色畫面，欄位 [UNH 1]，重設計數器|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄交換的交易集控制編號中指定的全域設定，特別是欄位 UNH1.2 中的參考編號的 UNH1 欄位因為已超過允許的最大值。 群組控制編號允許的最大值取決於 UNH1 中三個欄位的值。 最大字元數是參考編號欄位 UNH1.2，13 for UNH1.1 中的前置詞和 13 for UNH1.3，在後置詞結合的所有三個欄位 14 中 14。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設的交易集控制編號，參考編號欄位 (UNH1.2)，如下所示：  
  
1.  在 EDI 全域屬性 對話方塊中，開啟 UNH 區段定義頁面。  
  
2.  按一下 UNH1 欄位相關聯的編輯欄位。  
  
3.  新的值設定的群組控制編號 （UNH1.2 中的參考編號） 的中間欄位的欄位具有可接受數。