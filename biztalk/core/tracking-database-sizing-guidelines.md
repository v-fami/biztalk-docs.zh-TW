---
title: "追蹤資料庫大小的指導方針 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, performance
- Tracking database, size
- Tracking Analysis Server database [BAM]
- performance, Tracking database
ms.assetid: 2188bee5-c0dd-4448-bd4a-4ffb2a0c79f1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c0293ff0a03583e51ee447ec1bd6283f1b02164
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tracking-database-sizing-guidelines"></a>調整追蹤資料庫大小的指導方針
本節描述調整 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中 BizTalk 追蹤 (BizTalkDTADb) 資料庫大小的考量。 它說明如何使用方程式與訊息變數來決定 BizTalk 追蹤資料庫在經過一段指定時間後的大小，並提供如何套用方程式的特定範例。 如此概略提供了 BizTalk 訊息、追蹤設定及追蹤資料庫大小之間的關聯性。 它並未考慮其他 SQL Server 因數，像是追蹤資料表中的索引大小，您可能需要針對這些因數考慮合理的倍數。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用訊息變數調整追蹤資料庫的大小](../core/using-message-variables-to-size-the-tracking-database.md)  
  
-   [追蹤訊息內文追蹤資料庫設定大小](../core/sizing-the-tracking-database-to-track-message-bodies.md)  
  
-   [案例 1： 針對簡單 BizTalk 訊息調整追蹤資料庫](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md)  
  
-   [案例 2： 在協調流程中的訊息調整追蹤資料庫](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)  
  
-   [案例 3： 調整追蹤資料庫外送到通訊群組清單之訊息的大小](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)  
  
-   [案例 4： 所有訊息調整追蹤資料庫](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)  
  
## <a name="see-also"></a>另請參閱  
 [追蹤資料庫中的記錄大小](../core/record-size-in-tracking-databases.md)   
 [備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)