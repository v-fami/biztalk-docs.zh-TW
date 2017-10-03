---
title: "可接受的 X12 交易集控制編號已達到 Guest 設定的最高上限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5a4aa5c-13a7-4234-916e-562b52644c51
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16ab48c7bc5615a17c4927d7bf971bdec87a9c2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-x12-transaction-set-control-number-has-reached-for-guest-settings"></a>可接受的 X12 交易集控制編號已達到 Guest 設定的最高上限
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|GlobalX12TsNumberError|  
|訊息文字|可接受的 X12 交易集控制編號已達到 Guest 設定的最高上限。 瀏覽至 通用設定寄件者角色畫面，欄位 ST 2 在夥伴協議管理員 中，重設計數器|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示傳送管線無法處理外寄 X12 交換，因為交易中指定的全域設定，特別是參考編號欄位 ST02.2 中的 ST02 欄位集控制編號大於允許的最大值。 交易集控制編號允許的最大值取決於 ST02 中三個欄位的值。 最大字元數是參考編號欄位 UNH1.2，UNH1.1 中的前置詞為 8 個和 UNH1.3 中的尾碼為 8 和 9 結合的所有三個欄位中 9。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設的交易集控制編號，參考編號欄位 (ST02.2)，如下所示：  
  
1.  在 EDI 全域屬性 對話方塊中，開啟 GS 和 ST 區段定義頁面。  
  
2.  按一下編輯欄位與 ST02 欄位相關聯。  
  
3.  新的值設定的群組控制編號 （ST02.2 中的參考編號） 的中間欄位的欄位具有可接受數。