---
title: 剖析期間發生的錯誤。 下列的錯誤而擱置的 Edifact 交易集包含在交換 （沒有群組） |Microsoft Docs
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
ms.openlocfilehash: c2e0d8e2b03decf2db806a08f082b7aace276a8e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006415"
---
# <a name="error-encountered-during-parsing-the-edifact-transaction-set-contained-in-interchange-without-group-is-being-suspended-with-following-errors"></a>剖析期間發生的錯誤。 下列的錯誤是而擱置的 Edifact 交易集包含在交換 （沒有群組）
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                   |
| 產品版本 |                                                                              [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                               |
|    事件識別碼     |                                                                                                           -                                                                                                           |
|  事件來源   |                                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                                 |
|    元件    |                                                                                                      將 EDI 引擎                                                                                                       |
|  符號名稱  |                                                                                      EfactTransactionSetReceiveErrorWithoutGroup                                                                                      |
|  訊息文字   | 剖析期間發生的錯誤。 Edifact 交易集識別碼為 '{0}'包含在交換 （沒有群組） 識別碼'{1}'，寄件者識別碼為'{2}'，接收者識別碼 '{3}' 而遭到擱置下列錯誤： |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於交換中的已識別交易集發生所述的錯誤，因此 EDI 接收管線在剖析不含群組的內送 EDIFACT 交換時遇到錯誤。 請注意，交易集不在交換中的群組。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，錯誤訊息中使用的資訊來識別交易集合中的錯誤訊息，然後決定產品說明中的問題解決方法。