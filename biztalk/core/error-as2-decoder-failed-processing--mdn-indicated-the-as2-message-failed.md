---
title: AS2 解碼器處理失敗，因為 MDN 表示 AS2 訊息處理失敗 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bce620a-f336-435e-b7c3-3db060f2819d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 240c90d488d313bf43982c7c98db3e8a1ea05e75
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984495"
---
# <a name="the-as2-decoder-failed-processing-because-the-mdn-indicated-the-as2-message-failed-processing"></a>AS2 解碼器處理失敗，因為 MDN 表示 AS2 訊息處理失敗
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                |
| 產品版本 |                                                                            [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                            |
|    事件識別碼     |                                                                                                        -                                                                                                         |
|  事件來源   |                                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                              |
|    元件    |                                                                                                    AS2 引擎                                                                                                    |
|  符號名稱  |                                                                                      AS2DecoderMdnProcessingFailureReturned                                                                                      |
|  訊息文字   | AS2 解碼器處理失敗，因為 MDN 表示 AS2 訊息處理失敗。  MDN 訊息的詳細資料如下： AS2-從:"{0}"AS2-到:"{1}"MessageID:"{2}"OriginalMessageID:"{3}」 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，MDN 回應指出，原始 AS2 訊息的接收者無法處理原始 AS2 訊息。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請連絡 AS2 訊息的接收者，判斷接收者無法處理的原因，接著在修正原始 AS2 訊息後重新傳送。