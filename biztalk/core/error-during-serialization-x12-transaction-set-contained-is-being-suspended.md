---
title: "在序列化期間發生錯誤。 X12 交易集包含在功能群組中處於暫停狀態，錯誤如下 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49b13038-2637-4435-91e9-d6fe2b80ca7a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c8b1402974c53007e8488df3fbdedc666ac2753
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-serialization-the-x12-transaction-set-contained-in-functional-group-is-being-suspended-with-following-errors"></a>在序列化期間發生錯誤。 X12 交易集包含在功能群組中處於暫停狀態，錯誤如下
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12TransactionSetSendError|  
|訊息文字|在序列化期間發生錯誤。 X12 交易集識別碼為 '{0}' 中識別碼為 '{1}'，識別碼為 '{2}'，交換中使用寄件者識別碼 '{3}'，'\ {4' 的接收者識別碼的功能群組處於暫停狀態，錯誤如下：|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 傳送管線發生錯誤，當序列化 X12 外寄交換，因為識別的交易集與敘述的錯誤。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，錯誤訊息中使用的資訊中的交易集識別錯誤，，然後決定產品說明中的問題解決方法。