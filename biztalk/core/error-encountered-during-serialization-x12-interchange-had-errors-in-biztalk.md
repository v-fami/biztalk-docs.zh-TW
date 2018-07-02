---
title: 序列化期間發生的錯誤。 X12 交換發生下列錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9ca3314-6c66-4400-816a-f9c7c7915122
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96c1a186e56fb5c04364187784522f0ba5832581
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008135"
---
# <a name="error-encountered-during-serialization-the-x12-interchange-had-the-following-errors"></a>序列化期間發生的錯誤。 X12 交換發生下列錯誤
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                              |
| 產品版本 |                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                          |
|    事件識別碼     |                                                                      -                                                                      |
|  事件來源   |                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                            |
|    元件    |                                                                 將 EDI 引擎                                                                  |
|  符號名稱  |                                                           X12InterchangeSendError                                                           |
|  訊息文字   | 序列化期間發生的錯誤。 X12 交換識別碼 '{0}'，寄件者識別碼為'{1}'，接收者識別碼 '{2}' 發生下列錯誤 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 傳送管線時發生錯誤序列化 X12 外寄交換，因為敘述的錯誤。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，找出交換中的錯誤訊息，並接著決定產品說明中的問題解決方法需要使用錯誤訊息中的資訊。