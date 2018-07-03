---
title: 失敗發生在處理 X12 訊息在傳送埠： 沒有名稱的合作對象的收件者及寄件者識別碼辨識符號配對不一致 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fdf445e8-51a3-44fb-aa71-e0b0ab9c428f
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30d75c1db7b55d1955eec398d6c8d792b11ca648
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005703"
---
# <a name="a-failure-occurred-in-processing-x12-message-on-send-port-no-agreement-for-receiver-and-sender-identifier-qualifier-pairs-and-no-party-with-name"></a>失敗發生在處理 X12 訊息在傳送埠： 沒有名稱的合作對象的收件者及寄件者識別碼辨識符號配對不一致
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                      |
| 產品版本 |                                                                  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                  |
|    事件識別碼     |                                                                                              -                                                                                               |
|  事件來源   |                                                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                    |
|    元件    |                                                                                          將 EDI 引擎                                                                                          |
|  符號名稱  |                                                                                              -                                                                                               |
|  訊息文字   | 失敗發生在處理 X12 訊息傳送埠上的{0}。 沒有協議的收件者及寄件者識別碼/辨識符號配對存在{1}， {2}， {3}， {4}。 沒有合作對象有名稱{5}。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析合作對象的 EDIFACT 交換因為 BizTalk Server 找不到符合升級傳送者辨識符號和識別項屬性，並提升接收者辨識符號和識別項屬性，與合作對象對應的值。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定傳送者辨識符號和識別項 （ISA5 和 ISA6） 和接收者辨識符號和識別碼 （ISA7 與 ISA8） 在 [EDI 屬性] 對話方塊中的合作對象的 [ISA 區段定義] 頁面中定義符合升級的對應交換的內容中的屬性。