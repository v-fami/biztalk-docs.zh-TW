---
title: AS2 解碼器處理驗證 MDN 中傳回的 MIC 值時失敗 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3fe2d76d-b0f1-4118-8483-547c2c9fffb7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b15ec1518e4736052e31254283db66395d87fb6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985839"
---
# <a name="the-as2-decoder-failed-processing-when-validating-the-mic-value-returned-in-the-mdn"></a>驗證 MDN 中傳回的 MIC 值時，AS2 解碼器處理失敗
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                       |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                           |
| 產品版本 |                                                                      [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                       |
|    事件識別碼     |                                                                                                   -                                                                                                   |
|  事件來源   |                                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                         |
|    元件    |                                                                                              AS2 引擎                                                                                               |
|  符號名稱  |                                                                                AS2DecoderMdnMicFailureDuringProcessing                                                                                |
|  訊息文字   | 驗證 MDN 中傳回的 MIC 值時，AS2 解碼器處理失敗。  MDN 訊息的詳細資料如下： AS2-從:"{0}"AS2-到:"{1}"MessageID:"{2}"OriginalMessageID:"{3}」 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送 MDN 的 MIC （訊息完整性檢查） 驗證失敗。 因為。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認用來產生 MDN （在原始訊息的簽章-回條-MICalg 標頭） 的演算法是做為 AS2 訊息接收者的簽章-回條-MICalg 屬性中指定的演算法相同。 兩者都應該是 SHA1 或 MD5。 如果指定的演算法都相同，請確認已收到內容現場多部分簽署的 MDN 訊息的第二部分中的延伸模組欄位包含有效的 MIC 摘要。 如果有的話，判斷為什麼 MDN 沒有對應至已傳送交換。