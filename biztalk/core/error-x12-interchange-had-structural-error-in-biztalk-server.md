---
title: '交換發生結構錯誤。 最後一個結構有效的功能群組識別碼為: |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd62855b-ecc6-4cfd-be9c-0025348eb841
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3da8a701e543fe5bfb9453af3cfa2514414f5c2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988094"
---
# <a name="the-interchange-had-structural-error-last-structurally-valid-functional-group-id-was"></a>交換發生結構錯誤。 最後一個結構有效的功能群組識別碼是：
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                 |
| 產品版本 |                                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                             |
|    事件識別碼     |                                                                         -                                                                          |
|  事件來源   |                               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                               |
|    元件    |                                                                     將 EDI 引擎                                                                     |
|  符號名稱  |                                                     X12InterchangeStructuralErrorAfter1stGroup                                                     |
|  訊息文字   | 交換識別碼 '{0}'，寄件者識別碼為'{1}'，接收者識別碼 '{2}' 發生結構錯誤。 最後一個結構有效的功能群組識別碼為 '{3}' |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換，因為指定的功能群組後，所發生交換中的結構化的錯誤。 發生此狀況可能是使用已被保留，與在錯誤時暫停交易集的交換。 此錯誤，交易集 （或集合） 包含錯誤的結果暫止，但其餘的交易設定已處理保留批次的一部分。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，交換修正程式結構的錯誤，將傳送者與然後重新傳送交換。