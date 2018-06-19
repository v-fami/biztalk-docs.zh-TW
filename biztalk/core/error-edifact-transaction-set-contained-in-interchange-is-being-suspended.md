---
title: 在剖析期間發生錯誤。 Edifact 交易集 （不含群組） 的交換中所含處於暫停狀態，錯誤如下 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 901fef68-4649-480a-997c-b061d7d069d6
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2dc5633917c708f457f11fc824997fa7eb6d4c59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240230"
---
# <a name="error-encountered-during-parsing-the-edifact-transaction-set-contained-in-interchange-without-group-is-being-suspended-with-following-errors"></a>在剖析期間發生錯誤。 Edifact 交易集 （不含群組） 的交換中所含處於暫停狀態，錯誤如下
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|EfactTransactionSetReceiveErrorWithoutGroup|  
|訊息文字|在剖析期間發生錯誤。 Edifact 交易集識別碼為 '{0}' 中 （不含群組） 的交換 id '{1}'，寄件者識別碼為 '{2}'，與包含收件者 id '{3}' 處於暫停狀態的下列錯誤：|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於交換中的已識別交易集發生所述的錯誤，因此 EDI 接收管線在剖析不含群組的內送 EDIFACT 交換時遇到錯誤。 請注意，在交換中的群組不是交易集。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，錯誤訊息中使用的資訊中的交易集識別錯誤，，然後決定產品說明中的問題解決方法。