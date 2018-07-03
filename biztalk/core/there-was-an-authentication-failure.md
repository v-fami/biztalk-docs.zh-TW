---
title: 發生驗證失敗。 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36524da9-da91-41e7-bf73-7781cde20c80
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5548d448d2c0d45addc72639ad229cf4ee1bf37f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022348"
---
# <a name="there-was-an-authentication-failure"></a>發生驗證錯誤
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                         |
| 產品版本 |                                                                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                     |
|    事件識別碼     |                                                                                                 -                                                                                                 |
|  事件來源   |                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                       |
|    元件    |                                                                                            將 EDI 引擎                                                                                             |
|  符號名稱  |                                                                                         DescPartyNotFound                                                                                         |
|  訊息文字   | 發生驗證錯誤。 請確定正在處理的訊息比對合作對象存在。 與訊息中的安全性/密碼資訊符合合作對象組態 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，因為 BizTalk Server 無法驗證訊息的寄件者。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  
  
-   確認傳送者辨識符號和交換標頭 （欄位 ISA5 和 ISA6 為 X12 或 UNB2.1 和 UNB2.2，對於 EDIFACT） 中的識別項相符的傳送者辨識符號和識別項 （如 [交換處理屬性] 頁面中所定義的合作對象屬性中[EDI 屬性] 對話方塊）。  
  
-   確認交換標頭中的安全性/密碼資訊 (在 X12 中為 [ISA3] 和 [ISA4] 欄位；在 EDIFACT 中為 [UNB6.1] 和 [UNB6.2] 欄位) 和合作對象屬性中的安全性/密碼資訊 (如 [EDI 屬性] 對話方塊 [交換處理屬性] 頁面中定義的內容) 相符。