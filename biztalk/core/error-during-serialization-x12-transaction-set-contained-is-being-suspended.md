---
title: 序列化期間發生的錯誤。 X12 交易集包含在功能群組下列錯誤而擱置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49b13038-2637-4435-91e9-d6fe2b80ca7a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 745fee9f48d534b750b605268ce63b1c685e3231
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988935"
---
# <a name="error-encountered-during-serialization-the-x12-transaction-set-contained-in-functional-group-is-being-suspended-with-following-errors"></a>序列化期間發生的錯誤。 X12 交易集包含在功能群組下列錯誤而擱置
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                             |
| 產品版本 |                                                                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                         |
|    事件識別碼     |                                                                                                                     -                                                                                                                      |
|  事件來源   |                                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                                           |
|    元件    |                                                                                                                 將 EDI 引擎                                                                                                                 |
|  符號名稱  |                                                                                                         X12TransactionSetSendError                                                                                                         |
|  訊息文字   | 序列化期間發生的錯誤。 X12 交易集識別碼為 '{0}'包含在功能群組識別碼'{1}'，在交換識別碼'{2}'，寄件者識別碼為 '{3}'，接收者識別碼'{4}' 而遭到擱置下列錯誤： |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 傳送管線時發生錯誤序列化 X12 外寄交換，因為識別的交易集與敘述的錯誤。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，錯誤訊息中使用的資訊來識別交易集合中的錯誤訊息，然後決定產品說明中的問題解決方法。