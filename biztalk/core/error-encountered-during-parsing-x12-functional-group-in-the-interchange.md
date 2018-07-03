---
title: 剖析期間發生的錯誤。 X12 交換中的功能群組發生下列錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2229c83-89bd-491f-9504-4afbf0084297
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4175e4057dca49a3187ebf48e333170e06a1099
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982967"
---
# <a name="error-encountered-during-parsing-the-x12-functional-group-in-the-interchange-had-the-following-errors"></a>剖析期間發生的錯誤。 X12 交換中的功能群組發生下列錯誤
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                             |
| 產品版本 |                                                        [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                         |
|    事件識別碼     |                                                                                     -                                                                                     |
|  事件來源   |                                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                           |
|    元件    |                                                                                將 EDI 引擎                                                                                 |
|  符號名稱  |                                                                      X12FunctionalGroupReceiveError                                                                       |
|  訊息文字   | 剖析期間發生的錯誤。 X12 功能群組識別碼 '{0}'，在交換識別碼'{1}'，寄件者識別碼為 '{2}'，接收者識別碼'{3}' 發生下列錯誤： |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線時發生錯誤剖析內送 X12 交換，因為識別的功能群組所述的錯誤。  
  
## <a name="user-action"></a>使用者動作  
 若要解決此錯誤，使用錯誤訊息中的資訊識別群組中的錯誤，然後決定產品說明中的問題解決方法。