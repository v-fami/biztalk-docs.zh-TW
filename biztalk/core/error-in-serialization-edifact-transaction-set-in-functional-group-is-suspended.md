---
title: "在序列化期間發生錯誤。 Edifact 交易集包含在功能群組中處於暫停狀態，錯誤如下 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24b76086-334b-45fb-85f8-82e3335daac4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb09bfecc2efc5e6878b7cc3d0149f2b56c07b68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-serialization-the-edifact-transaction-set-contained-in-functional-group-is-being-suspended-with-following-errors"></a>在序列化期間發生錯誤。 功能群組中包含的 Edifact 交易集處於暫停狀態，錯誤如下
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|EfactTransactionSetSendError|  
|訊息文字|在序列化期間發生錯誤。 Edifact 交易集識別碼為 '{0}' 包含在功能群組識別碼為 '{1}'，識別碼為 '{2}'，與寄件者識別碼 '{3}' 交換中接收者識別碼為 '\ {4' 處於暫停狀態，錯誤如下：|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 傳送管線在外寄 EDIFACT 交換序列化因為識別的交易集與敘述的錯誤時，會發生錯誤。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，錯誤訊息中使用的資訊中的交易集識別錯誤，，然後決定產品說明中的問題解決方法。