---
title: 批次元素已遭到擱置，因為它無法驗證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea5e19e8-4592-40f4-bffe-85ab27653fd5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90f82c88adc18899aac6d481b7a5d3e31e1a72c8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021964"
---
# <a name="the-batch-element-is-being-suspended-as-it-failed-validation"></a>批次元素已遭到擱置，因為驗證失敗
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                    批次引擎                                     |
|  符號名稱  |                                 BatchElementSuspended                                  |
|  訊息文字   |    即將擱置批次元素因為驗證失敗。 錯誤是： {0}    |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示批次處理協調流程無法將交易集的批次交換，因為交易集無法批次處理協調流程所執行的驗證。 沒有交易集驗證失敗，就會產生交換。 批次處理協調流程會將設定 EDI。BatchElementValidationFailure 內容屬性為"True"。 BatchSuspend 協調流程將會根據該內容屬性收取訊息、發佈錯誤資訊，然後再擱置訊息。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，表示寄件者的交易集發生錯誤，錯誤訊息中所示。 已解決的問題，導致其無法通過驗證，然後再重新傳送交易集合寄件者。