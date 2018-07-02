---
title: Edifact 交易集包含在交換錯誤 |Microsoft Docs
description: 序列化期間發生的錯誤。 下列的錯誤是而擱置的 Edifact 交易集包含在交換 （沒有群組）
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
ms.openlocfilehash: e5fcd7702ce791037d8a7320f647955fca1c9489
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981927"
---
# <a name="edifact-transaction-set-is-suspended-error-and-details"></a>Edifact 交易集時暫停的錯誤和詳細資料

`Error encountered during serialization. The Edifact transaction set contained in interchange (without group) is being suspended with following errors`

## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                              |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                      |
| 產品版本 |                                                                                  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                  |
|    事件識別碼     |                                                                                                              -                                                                                                               |
|  事件來源   |                                                                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                                    |
|    元件    |                                                                                                          將 EDI 引擎                                                                                                          |
|  符號名稱  |                                                                                           EfactTransactionSetSendErrorWithoutGroup                                                                                           |
|  訊息文字   | 序列化期間發生的錯誤。 Edifact 交易集識別碼為 '{0}'包含在交換 （沒有群組） 識別碼'{1}'，寄件者識別碼為'{2}'，接收者識別碼 '{3}' 而遭到擱置下列錯誤： |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 傳送管線在序列化傳出的 EDIFACT 交換因為識別的交易集與敘述的錯誤時，會發生錯誤。 請注意，交易集不在交換中的群組。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，錯誤訊息中使用的資訊來識別交易集合中的錯誤訊息，並再判斷解決問題。