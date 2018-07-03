---
title: 處理傳送埠上的 Edifact 訊息時發生錯誤： 收件者及寄件者識別碼辨識符號配對不一致 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cffc4705-164f-4779-8f04-c6a2a7f1bbda
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c27bc81b24a9d2850bc895f28020df286da17cba
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021868"
---
# <a name="a-failure-occurred-in-processing-edifact-message-on-send-port-no-agreement-for-receiver-and-sender-identifier-qualifier-pairs"></a>處理傳送埠上的 Edifact 訊息時發生錯誤： 收件者及寄件者識別碼辨識符號配對不一致
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                         |
| 產品版本 |                                                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                     |
|    事件識別碼     |                                                                                 -                                                                                 |
|  事件來源   |                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                       |
|    元件    |                                                                            將 EDI 引擎                                                                             |
|  符號名稱  |                                                                                 -                                                                                 |
|  訊息文字   | 處理傳送埠上的 Edifact 訊息時發生失敗{0}。 沒有協議的收件者及寄件者識別碼/辨識符號配對存在{1}， {2}， {3}， {4}。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析 EDIFACT 交換的合作對象，因為它無法符合升級傳送者辨識符號和識別項屬性，並提升接收者辨識符號和識別項使用合作對象的對應值的屬性。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定傳送者辨識符號和識別項 （UNB2.1 和 UNB2.2） 和接收者辨識符號和識別 （UNB3.1 和 UNB3.2） 在 [EDI 屬性] 對話方塊中的合作對象的 [UNB 區段定義] 頁面中定義符合對應交換的內容中的升級的屬性。