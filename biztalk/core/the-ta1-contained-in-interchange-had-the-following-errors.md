---
title: 包含在交換中的 TA1 發生下列錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e2d63fe9-63ef-44b3-8cb9-45a7abf8d0e4
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23bc06cd5f7a7b1e46b34daf5cac2106dcbd543a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002135"
---
# <a name="the-ta1-contained-in-interchange-had-the-following-errors"></a>包含在交換中的 TA1 發生下列錯誤
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                |
| 產品版本 |                            [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                            |
|    事件識別碼     |                                                        -                                                         |
|  事件來源   |              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI              |
|    元件    |                                                    將 EDI 引擎                                                    |
|  符號名稱  |                                                   X12TA1Error                                                    |
|  訊息文字   | {0} TA1 包含在交換識別碼 '{1}'，寄件者識別碼'{2}'，接收者識別碼 '{3}' 發生下列錯誤： |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送的 TA1 通知因為指定的錯誤情況。 這可能表示通知不符合 TA1Schema。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，讓傳送者的通知解決的問題與通知，確保該通知會符合 TA1Schema，然後再重新傳送通知。