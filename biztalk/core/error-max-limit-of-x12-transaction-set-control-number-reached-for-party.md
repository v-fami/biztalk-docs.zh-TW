---
title: "可接受 X12 交易集控制編號已達到合作對象的最高上限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a402f6d0-4399-47c9-a39a-56d7fa1efa86
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c46a221e0e69d159ee1f5d8cdeee0e0c31389e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-x12-transaction-set-control-number-has-reached-for-party"></a>可接受 X12 交易集控制編號已達到合作對象的最高上限
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|PartyX12TsNumberError|  
|訊息文字|可接受的 X12 交易集控制編號的合作對象 {0}，已達到最高上限。 瀏覽至合作對象中接收者角色畫面，欄位 [ST 2 在夥伴協議管理員] 中，重設計數器|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示傳送管線無法處理外寄 X12 交換，因為交易集控制編號設定中指定合作對象，特別是參考編號欄位 ST02.2 中的 [ST02] 欄位中已超過允許的最大值。 交易集控制編號允許的最大值取決於 ST02 中三個欄位的值。 最大字元數為 9 中的欄位 ST02.2，ST02.1 中的前置詞為 8 個 ST02.3 中的尾碼為 8 和 9 結合的所有三個欄位的參考編號。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設的交易集控制編號，參考編號欄位 (UNH1.2)，如下所示：  
  
1.  在 EDI 屬性 對話方塊中的 合作對象的交換解析，開啟 UNG 和 UNH 區段定義頁面。  
  
2.  按一下 UNH1 欄位相關聯的編輯欄位。  
  
3.  新的值設定交易集控制編號 （UNH1.2 中的參考編號） 的中間欄位的欄位具有可接受數。