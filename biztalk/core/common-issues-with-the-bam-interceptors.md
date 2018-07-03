---
title: BAM 攔截器的常見問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a32145e2-1367-4576-9103-86c9182c11a8
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e6217a96bfbbe0a9dfddef6e8cec5a82cb93254
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004071"
---
# <a name="common-issues-with-the-bam-interceptors"></a>BAM 攔截器的常見問題
這個主題討論以下使用 BAM 攔截器時可能常發生的問題：  
  
-   分散式交易的相關 SQL 例外狀況  
  
## <a name="you-receive-a-sql-exception-concerning-a-completed-distributed-transaction-or-a-transaction-descriptor"></a>您收到已完成之分散式交易或交易描述項相關的 SQL 例外狀況  
 執行 BAM Windows Communication Framework (WCF) 攔截器時，可能出現下列其中一個例外狀況：  
  
- 分散式交易完成。 請在新的交易或是 NULL 交易中編列這個工作階段。  
  
- 不允許啟動新要求，因為要求應該具備有效的交易描述項。  
  
  疑難排解此問題的建議如下：  
  
- 啟用 BAM 追蹤。 此追蹤會包括包含錯誤根本原因的所有相關訊息。 如需有關 BAM 追蹤的詳細資訊，請參閱 <<c0> [ 如何在 BAM 中啟用的追蹤](../core/how-to-enable-tracing-in-bam.md)。  
  
- 看見此分散式交易協調器 (DTC) 例外狀況時，請嘗試在沒有交易的情況下重新執行完全相同的實例。  
  
- 使用 SQL Server Profiler，並尋找追蹤內可能導致交易被中止的錯誤。  
  
## <a name="you-receive-an-error-similar-to-interceptor-configuration-polling-interval-0-must-be-at-least-5-seconds-when-using-the-wcf-interceptor"></a>使用 WCF 攔截器時，您收到類似「攔截器組態輪詢間隔 '0' 必須至少為 '5' 秒」的錯誤。  
 您並未在應用程式組態檔內明確提供攔截器組態輪詢間隔值，或您提供的值小於必要的最小值 5 秒時，就可能發生這個錯誤。  
  
 若要解決這個問題，請提供有效的 PollingIntervalSec 值，如下所示：  
  
```  
<BamEndpointBehaviorExtension ConnectionString="Initial Catalog=BamPrimaryImport;Data Source=MyMachine;Integrated Security=SSPI;" PollingIntervalSec="1500" />  
```  
  
## <a name="see-also"></a>另請參閱  
 [BAM 攔截器疑難排解](../core/troubleshooting-bam-interceptors.md)