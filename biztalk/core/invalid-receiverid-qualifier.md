---
title: 無效的 ReceiverId 辨識符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52d60f7e-6f16-424d-91b8-dc8181206249
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f4cf13bb338959ca4cd7d2d25a85749f0ff0171
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981815"
---
# <a name="invalid-receiverid-qualifier"></a>無效的 ReceiverId 辨識符號
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                      X12Ta1InvalidReceiverIdQualifierDescription                       |
|  訊息文字   |                              無效的 ReceiverId 辨識符號                              |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為 ISA07 欄位中的接收者辨識符號 (x12 交換) 或 （適用於 EDIFACT 的 [UNB3.2] 欄位中的收件者代碼辨識符號交換） 不符合服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema) 所建立的列舉中的值。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定 ISA07 欄位或 [UNB3.2] 欄位符合其中一個服務結構描述所建立的列舉型別中的值。 重新傳送交換。