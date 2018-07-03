---
title: FIN 回應類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, response types
- deploying, schemas
- FIN Response Reconciliation, message types
- FRR, deploying schemas
- schemas, deploying
- FIN Response Reconciliation, response types
- messages, message types
- response types [FIN Response Reconciliation]
ms.assetid: a6ef2f20-08ab-40d3-a0a5-cc4048ce0987
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 382e0e628d01903a6274dd3f0321379f71fc7a15
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995399"
---
# <a name="fin-response-types"></a>FIN 回應類型
FIN 回應對帳 (FRR) 會調解的任何類別 0 到 9 SWIFT FIN 訊息的回應。 在其中一個 FIN 訊息回應，SWIFT FIN 應用程式一律會傳送至少一個，可能會超過一個通知 (ACK) 或負認可 (NAK)。 下表顯示的訊息類型的輸出和輸入 （回應） FRR 處理訊息。  


| 輸出 /<br /><br /> 輸入 |                                             訊息類型                                              |                                                                                                                                                                                                                             訊息狀態                                                                                                                                                                                                                              |
|-------------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           輸出            |                              所有類別 0 到 9 SWIFT FIN 訊息類型                              |                                                                                                                                                                                                                                   不適用                                                                                                                                                                                                                                   |
|            輸入            |                         MQ 系列移動瀏覽/NAN (MQ Series 傳輸層級通知/NAK)                         |                                                                                                                                                                                                                    MQSeries 傳輸通知                                                                                                                                                                                                                    |
|                               |                                     MT010 （非傳遞警告）                                      |                                                                     SWIFT 成功傳送原始訊息給夥伴，但不夥伴已收到的訊息會指出。 如果[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]收到多個非傳遞警告 (NDW) 訊息，它執行迴圈並等候下一個預期的訊息。                                                                     |
|                               |                                     MT011 （傳遞通知）                                     |                                                                                                                                                                     SWIFT 成功傳送原始訊息給夥伴，並接收夥伴已收到訊息的指示。                                                                                                                                                                      |
|                               |                                      MT012 （寄件者通知）                                      |                                                                                                                                                            SWIFT 順利接收原始訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。                                                                                                                                                             |
|                               |                                      MT015 （DNK 或延遲的 NAK）                                      |                                                                                                                                                                                                  SWIFT 具有未成功傳送原始訊息給夥伴。                                                                                                                                                                                                   |
|                               |                                      MT019 （中止通知）                                       |                                                                                                                                                                                                                 在 SWIFT，中止訊息傳輸。                                                                                                                                                                                                                  |
|                               | MTS21_FIN_ACKNAK （「 通知 」 或 「 L (認可/NAK) 所傳送 FIN 訊息的負值通知 」） | SWIFT 成功或失敗的接收來自訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 此訊息說明上述兩種情況。 它是 ACK 或 NAK 取決於訊息 ("0"代表 ACK) 和"1"的 NAK 451 欄位中的值。 這會是第一個回應傳遞回[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 |

## <a name="deployment-of-schemas-for-frr"></a>部署結構描述的 FRR  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] （如上述表格所示），安裝程式會部署在 FrrSchemas.dll 的系統層級的所有訊息的結構描述。 FRR 協調流程需要部署這些結構描述。 因為[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式會部署在 FrrSchemas.dll 這些結構描述、 您沒有，而不是，必須部署另一個專案中的這些結構描述。 這樣會產生錯誤。  

 FRRSchemas.dll 包含下列結構描述：  

-   TransportAck  

-   MT010  

-   MT011  

-   MT012  

-   MT015  

-   MT019  

-   MTS21_FIN_ACKNAK