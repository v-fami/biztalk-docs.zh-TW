---
title: "在剖析期間發生錯誤。 Edifact 交易集包含在功能群組中處於暫停狀態，錯誤如下 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 986a7220-d35a-4047-8996-7d44c7d2b823
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70428ae8f430ea5ccb9ff13e068716cb35555f69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-parsing-the-edifact-transaction-set-contained-in-functional-group-is-being-suspended-with-following-errors"></a>在剖析期間發生錯誤。 功能群組中包含的 Edifact 交易集處於暫停狀態，錯誤如下
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|EfactTransactionSetReceiveError|  
|訊息文字|在剖析期間發生錯誤。 Edifact 交易集識別碼為 '{0}' 包含在功能群組識別碼為 '{1}'，識別碼為 '{2}'，與寄件者識別碼 '{3}' 交換中接收者識別碼為 '\ {4' 處於暫停狀態，錯誤如下：|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線無法剖析內送 EDIFACT 交換和群組，因為識別的交易集與敘述的錯誤。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，錯誤訊息中使用的資訊來識別交易集的錯誤並再判斷文件中的問題解決方法。