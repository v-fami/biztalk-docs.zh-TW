---
title: Edifact 交易集包含在交換錯誤 |Microsoft 文件
description: 在序列化期間發生錯誤。 Edifact 交易集 （不含群組） 的交換中所含處於暫停狀態，錯誤如下
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a0a33ac-d83e-495c-ba75-88c15ad7cfcd
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67f089e49941ffec7d3392b3bc35edcbc4eefec5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241470"
---
# <a name="edifact-transaction-set-is-suspended-error-and-details"></a>Edifact 交易集是已暫停的錯誤和詳細資料

`Error encountered during serialization. The Edifact transaction set contained in interchange (without group) is being suspended with following errors`

## <a name="details"></a>詳細資料  
  
|||  
|---|---|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|EfactTransactionSetSendErrorWithoutGroup|  
|訊息文字|在序列化期間發生錯誤。 Edifact 交易集識別碼為 '{0}' 中 （不含群組） 的交換 id '{1}'，寄件者識別碼為 '{2}'，與包含收件者 id '{3}' 處於暫停狀態的下列錯誤：|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 傳送管線在外寄 EDIFACT 交換序列化因為識別的交易集與敘述的錯誤時，會發生錯誤。 請注意，在交換中的群組不是交易集。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，錯誤訊息中使用的資訊來識別交易集的錯誤並再判斷解決問題。