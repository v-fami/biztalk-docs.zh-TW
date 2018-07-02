---
title: Edifact 交換 Xml 序列化失敗，因為無效的結構、 無 transactionSet 或 UNE |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ce1c219-f2ed-46c1-ae4b-8a4206f7cd01
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fc0661bfbc88c78a9afda7811c9a183b2160b05
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986583"
---
# <a name="edifact-interchange-xml-serialization-failed-due-to-invalid-structure-no-transactionset-or-une"></a>Edifact 交換 Xml 序列化失敗，因為無效的結構、 無 transactionSet 或 UNE
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                         |
|-----------------|-------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                    |
| 產品版本 |                               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                |
|    事件識別碼     |                                                            -                                                            |
|  事件來源   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                  |
|    元件    |                                                       將 EDI 引擎                                                        |
|  符號名稱  |                                            EfactTransactionSetOrUneNotFound                                             |
|  訊息文字   | Edifact 交換 Xml 序列化失敗，因為無效的結構。 尋找 TransactionSet 或 UNE，但是找不到 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送 EDIFACT 交換，因為第一個區段都不 UNA 或 UNB 區段。 UNA 區段是選擇性的。UNB 區段是必要的。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認訊息的這類交易設定群組中會是後面接著另一個交易集或 UNE 區段的交換結構的寄件者。 讓寄件者，然後重新傳送交換。