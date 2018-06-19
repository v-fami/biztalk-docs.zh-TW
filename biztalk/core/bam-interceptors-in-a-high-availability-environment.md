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
# <a name="bam-interceptors-in-a-high-availability-environment"></a><span data-ttu-id="1e669-102">高可用性環境中的 BAM 攔截器</span><span class="sxs-lookup"><span data-stu-id="1e669-102">BAM Interceptors in a High Availability Environment</span></span>
<span data-ttu-id="1e669-103">本主題說明高可用性環境中的 BAM WF 攔截器和 BAM WCF 攔截器在發生 SQL Server 容錯移轉時的容錯移轉程序。</span><span class="sxs-lookup"><span data-stu-id="1e669-103">This topic describes the failover processes for the BAM WF interceptor and the BAM WCF interceptor in a high availability environment during a SQL Server failover.</span></span>  
  
## <a name="bam-wf-interceptor"></a><span data-ttu-id="1e669-104">BAM WF 攔截器</span><span class="sxs-lookup"><span data-stu-id="1e669-104">BAM WF Interceptor</span></span>  
 <span data-ttu-id="1e669-105">在高可用性環境中運作時，若在 SQL Server 容錯移轉期間發生 SQL Server 連接問題，BAM WF 攔截器會重新嘗試擷取攔截器組態檔。</span><span class="sxs-lookup"><span data-stu-id="1e669-105">When operating in a high availability environment, the BAM WF interceptor will retry retrieval of the interceptor configuration file when there is a SQL Server connection problem during a SQL Server failover.</span></span> <span data-ttu-id="1e669-106">不過，當 SQL Server 容錯移轉進行時，若正在寫入資料到「BAM 主要匯入」資料庫，則攔截器不會重新嘗試。</span><span class="sxs-lookup"><span data-stu-id="1e669-106">However, the interceptor will not retry when writing data to the BAM Primary Import database when a SQL Server failover is in process.</span></span> <span data-ttu-id="1e669-107">這是因為攔截器的行為會依賴**WorkflowCommitBatchService**類別資料寫入 BAM 主要匯入資料庫。</span><span class="sxs-lookup"><span data-stu-id="1e669-107">This is because the interceptor relies on the behavior of the **WorkflowCommitBatchService** class when writing data to the BAM Primary Import database.</span></span>  
  
 <span data-ttu-id="1e669-108">在下列範例中， **DefaultWorkflowCommitWorkBatchService**新增為執行階段服務，而且 enableRetries ="true"，以便重試批次中的 App.config 檔案中的程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="1e669-108">In the following example, **DefaultWorkflowCommitWorkBatchService** is added as a run-time service with enableRetries="true" so that it retries the batch as shown in a snippet from an App.config file:</span></span>  
  
```  
<add type="System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"  enableRetries="True"/>  
```  
  
 <span data-ttu-id="1e669-109">不過，如果那里現有的環境交易時**CommitWorkBatch**方法呼叫，當 SQL Server 連接不是可立即終止工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="1e669-109">However, if there are existing ambient transactions when the **CommitWorkBatch** method is called, the workflow instance is terminated immediately when a SQL Server connection is not available.</span></span>  
  
 <span data-ttu-id="1e669-110">如需有關的行為**WorkflowCommitBatchService**類別在高可用性環境中，請參閱 「 可靠性和高可用性 」 一節中 「 簡介來裝載 Windows Workflow Foundation"在[http://go.microsoft.com/fwlink/?LinkId=88068](http://go.microsoft.com/fwlink/?LinkId=88068)。</span><span class="sxs-lookup"><span data-stu-id="1e669-110">For more information about the behavior of the **WorkflowCommitBatchService** class in a high availability environment, see the "Reliability and High Availability" section in "Introduction to Hosting Windows Workflow Foundation" at [http://go.microsoft.com/fwlink/?LinkId=88068](http://go.microsoft.com/fwlink/?LinkId=88068).</span></span>  
  
## <a name="bam-wcf-interceptor"></a><span data-ttu-id="1e669-111">BAM WCF 攔截器</span><span class="sxs-lookup"><span data-stu-id="1e669-111">BAM WCF Interceptor</span></span>  
 <span data-ttu-id="1e669-112">在高可用性環境中，若於 SQL Server 容錯移轉期間發生 SQL Server 連接問題，BAM WCF 攔截器不會重新嘗試擷取攔截器組態檔。</span><span class="sxs-lookup"><span data-stu-id="1e669-112">In a high availability environment, the BAM WCF interceptor does not retry retrieval of the interceptor configuration file when there is a SQL Server connection problem during a SQL Server failover.</span></span> <span data-ttu-id="1e669-113">因此，您應該自訂 WCF 程式碼來解決失敗的問題，或使用可靠的傳訊來重新提交訊息。</span><span class="sxs-lookup"><span data-stu-id="1e669-113">You should therefore customize the WCF code to compensate for failure or use reliable messaging to resubmit messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e669-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e669-114">See Also</span></span>  
 [<span data-ttu-id="1e669-115">BAM WF 攔截器</span><span class="sxs-lookup"><span data-stu-id="1e669-115">BAM WF Interceptor</span></span>](../core/bam-wf-interceptor.md)