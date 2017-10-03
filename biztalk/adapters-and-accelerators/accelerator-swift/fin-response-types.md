---
title: "FIN 回應類型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54c890a5e0f51207cce1897b10095a87ae438793
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="fin-response-types"></a>FIN 回應類型
FIN 回應對帳 (FRR) 會調解任何類別 0 到 9 的 SWIFT FIN 訊息的回應。 在其中一個 FIN 訊息回應，SWIFT FIN 應用程式一定會傳送至少一個，可能是多個一個通知 (ACK) 或負值通知 (NAK)。 下表顯示訊息類型的傳出和傳入 （回應） FRR 處理訊息。  
  
|輸出 /<br /><br /> 輸入|訊息類型|訊息狀態|  
|----------------------------|------------------|--------------------|  
|輸出|所有類別 0 到 9 SWIFT FIN 訊息類型|不適用|  
|輸入|MQ 系列取景位置調整/NAN (MQ Series 傳輸層級 ACK/NAK)|MQSeries 傳輸通知|  
||MT010 （非傳遞警告）|SWIFT 成功傳送原始訊息給夥伴，但夥伴已收到訊息的指示。 如果[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]收到多個未傳遞警告 (NDW) 訊息，執行迴圈，並等候下一個預期的訊息。|  
||MT011 （傳遞通知）|SWIFT 成功傳送原始訊息給夥伴，並接收夥伴已收到訊息的指示。|  
||MT012 （寄件者通知）|SWIFT 已順利接收原始訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。|  
||MT015 （DNK 或延遲的 NAK）|SWIFT 尚未成功傳送原始訊息給夥伴。|  
||MT019 （中止通知）|在 SWIFT 中止訊息傳輸。|  
||MTS21_FIN_ACKNAK （認可或負值通知 (ACK/NAK) LT 傳送 FIN 訊息）|SWIFT 成功或失敗訊息從[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 此訊息會涵蓋這兩種案例。 它是通知或 NAK 取決於訊息 ("0"代表 ACK) 和"1"的 NAK 451 欄位中的值。 這會是第一個回應傳送回[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。|  
  
## <a name="deployment-of-schemas-for-frr"></a>部署結構描述的 FRR  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式 （如上述表格中所示），將部署 FrrSchemas.dll 中的所有系統層級訊息的結構描述。 FRR 協調流程需要部署這些結構描述。 因為[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式會部署在 FrrSchemas.dll 這些結構描述，您不必，並不是，必須部署這些結構描述，另一個專案中的。 這樣會產生錯誤。  
  
 FRRSchemas.dll 包含下列結構描述：  
  
-   TransportAck  
  
-   MT010  
  
-   MT011  
  
-   MT012  
  
-   MT015  
  
-   MT019  
  
-   MTS21_FIN_ACKNAK