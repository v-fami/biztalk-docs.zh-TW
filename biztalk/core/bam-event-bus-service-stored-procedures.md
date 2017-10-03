---
title: "BAM 事件匯流排服務預存程序 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedures, Even Bus Service [BAM]
- Event Bus Service [BAM], stored procedures
ms.assetid: 18a7bd40-50ce-44f2-88ae-45a2e3c8d3f4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f44dce10113b8a3a85b7c1dd177f637933b582ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-event-bus-service-stored-procedures"></a>BAM 事件匯流排服務預存程序
請使用下列預存程序管理 BAM 事件匯流排服務：  
  
-   若要暫停 BAM 事件匯流排服務，請在 BAM 資料庫的交易中執行 TDDS_BlockTDDS 預存程序 (不認可交易)。 若要繼續 BAM 事件匯流排服務，請認可 TDDS_BlockTDDS 交易。  
  
-   若要在多台電腦上啟用 BAM 事件匯流排服務，請識別要用於追蹤的主控件，然後將這些電腦加入追蹤主控件。  
  
-   若要設定工作階段逾時和活動訊號間隔，請使用 TDDS_UpdateSettings 預存程序。 只有 BTS_ADMIN_USERS 群組的成員才具有執行這個預存程序的權限。  
  
     TDDS_UpdateSettings 預存程序包含下列參數：  
  
    -   @RefreshIntervalint。設定為大於 60 秒。  
  
    -   @SqlCommandTimeoutint。設定為小於 RefreshInterval。  
  
    -   @SessionTimeoutint。設定為大於 RefreshInterval 的兩倍。  
  
    -   @EventLoggingIntervalnvarchar(16)。 設定為大於 60 秒。  
  
    -   @RetryCountint。設定為大於 60 秒。  
  
    -   @ThreadPerSessionint。此參數已經過時。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM](../core/managing-bam.md)