---
title: 在高可用性環境中的 BAM 攔截器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 555c8200-949f-4c7d-8041-5ba4b6cbaed5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79a697eb2a1a27ceeec1538ad8d46127413e7ed1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230734"
---
# <a name="bam-interceptors-in-a-high-availability-environment"></a>高可用性環境中的 BAM 攔截器
本主題說明高可用性環境中的 BAM WF 攔截器和 BAM WCF 攔截器在發生 SQL Server 容錯移轉時的容錯移轉程序。  
  
## <a name="bam-wf-interceptor"></a>BAM WF 攔截器  
 在高可用性環境中運作時，若在 SQL Server 容錯移轉期間發生 SQL Server 連接問題，BAM WF 攔截器會重新嘗試擷取攔截器組態檔。 不過，當 SQL Server 容錯移轉進行時，若正在寫入資料到「BAM 主要匯入」資料庫，則攔截器不會重新嘗試。 這是因為攔截器的行為會依賴**WorkflowCommitBatchService**類別資料寫入 BAM 主要匯入資料庫。  
  
 在下列範例中， **DefaultWorkflowCommitWorkBatchService**新增為執行階段服務，而且 enableRetries ="true"，以便重試批次中的 App.config 檔案中的程式碼片段所示：  
  
```  
<add type="System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"  enableRetries="True"/>  
```  
  
 不過，如果那里現有的環境交易時**CommitWorkBatch**方法呼叫，當 SQL Server 連接不是可立即終止工作流程執行個體。  
  
 如需有關的行為**WorkflowCommitBatchService**類別在高可用性環境中，請參閱 「 可靠性和高可用性 」 一節中 「 簡介來裝載 Windows Workflow Foundation"在[http://go.microsoft.com/fwlink/?LinkId=88068](http://go.microsoft.com/fwlink/?LinkId=88068)。  
  
## <a name="bam-wcf-interceptor"></a>BAM WCF 攔截器  
 在高可用性環境中，若於 SQL Server 容錯移轉期間發生 SQL Server 連接問題，BAM WCF 攔截器不會重新嘗試擷取攔截器組態檔。 因此，您應該自訂 WCF 程式碼來解決失敗的問題，或使用可靠的傳訊來重新提交訊息。  
  
## <a name="see-also"></a>另請參閱  
 [BAM WF 攔截器](../core/bam-wf-interceptor.md)