---
title: AS2 解碼器發生例外狀況處理期間 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5f16d2e-e83c-4e2c-84be-41b5ed012dce
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e80ce8b53e6b5eb77770d7abcf9dbfbd157d9d64
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010263"
---
# <a name="the-as2-decoder-encountered-an-exception-during-processing"></a>AS2 解碼器發生在處理期間的例外狀況
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                         |
| 產品版本 |                                                                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                     |
|    事件識別碼     |                                                                                                 -                                                                                                 |
|  事件來源   |                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                       |
|    元件    |                                                                                            AS2 引擎                                                                                             |
|  符號名稱  |                                                                          AS2DecoderExceptionEncounteredDuringProcessing                                                                           |
|  訊息文字   | AS2 解碼器在處理過程中發生例外狀況。  訊息和例外狀況的詳細資料如下： AS2-從:"{0}"AS2-來:"{1}"MessageID:"{2}"MessageType:"{3}"例外狀況:"{4}" |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於 AS2 解碼器發生問題，因此接收管線無法處理內送 AS2 訊息。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，檢查 AS2 錯誤程式碼來判斷錯誤狀況的本質。 如需有關 AS2 錯誤碼的詳細資訊，請參閱中的 < AS2 錯誤碼 > 主題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]說明檔。