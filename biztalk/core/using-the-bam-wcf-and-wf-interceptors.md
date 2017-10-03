---
title: "使用 BAM WCF 和 WF 攔截器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a87a643-8e15-47d1-8d2a-3d899a1494ff
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ea631ed3a9058128a71373b6e6c7eb55ebad6c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-bam-wcf-and-wf-interceptors"></a><span data-ttu-id="95ba5-102">使用 BAM WCF 和 WF 攔截器</span><span class="sxs-lookup"><span data-stu-id="95ba5-102">Using the BAM WCF and WF Interceptors</span></span>
<span data-ttu-id="95ba5-103">BAM 攔截器可將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 BAM 攔截器功能擴充至 Windows Workflow Foundation (WF)、Windows Communication Framework (WCF) 及其他執行階段環境。</span><span class="sxs-lookup"><span data-stu-id="95ba5-103">BAM interceptors extend the BAM interceptor functionality for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] into Windows Workflow Foundation (WF), Windows Communication Framework (WCF), and other runtime environments.</span></span> <span data-ttu-id="95ba5-104">藉由使用 BAM 攔截器，您可以追蹤商務程序而不需要重新編譯 WF 或 WCF 解決方案；只要透過組態檔利用 XML 和一系列的項目將應用程式事件對應至 BAM 活動並定義資料、相互關聯識別碼、接續 Token 和其他必要和選用的成品，就可以完成整合。</span><span class="sxs-lookup"><span data-stu-id="95ba5-104">By using a BAM interceptor, you can track your business processes without recompiling your WF or WCF solution — integration is done through a configuration file using XML and a series of elements that map application events to BAM activities and define the data, correlation ID, continuation token and other required and optional artifacts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="95ba5-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="95ba5-105">In This Section</span></span>  
  
-   [<span data-ttu-id="95ba5-106">BAM WCF 和 WF 攔截器為何？</span><span class="sxs-lookup"><span data-stu-id="95ba5-106">What Are the BAM WCF and WF Interceptors?</span></span>](../core/what-are-the-bam-wcf-and-wf-interceptors.md)  
  
-   [<span data-ttu-id="95ba5-107">BAM WCF 和 WF 攔截器的已知的問題</span><span class="sxs-lookup"><span data-stu-id="95ba5-107">Known Issues with the BAM WCF and WF Interceptors</span></span>](../core/known-issues-with-the-bam-wcf-and-wf-interceptors.md)  
  
-   [<span data-ttu-id="95ba5-108">在高可用性環境中的 BAM 攔截器</span><span class="sxs-lookup"><span data-stu-id="95ba5-108">BAM Interceptors in a High Availability Environment</span></span>](../core/bam-interceptors-in-a-high-availability-environment.md)  
  
-   [<span data-ttu-id="95ba5-109">BAM 攔截器效能計數器</span><span class="sxs-lookup"><span data-stu-id="95ba5-109">BAM Interceptor Performance Counters</span></span>](../core/bam-interceptor-performance-counters.md)  
  
-   [<span data-ttu-id="95ba5-110">載入使用 BAM API 的 BAM 攔截器</span><span class="sxs-lookup"><span data-stu-id="95ba5-110">Loading BAM Interceptors Using the BAM API</span></span>](../core/loading-bam-interceptors-using-the-bam-api.md)  
  
-   [<span data-ttu-id="95ba5-111">BAM 攔截器疑難排解</span><span class="sxs-lookup"><span data-stu-id="95ba5-111">Troubleshooting BAM Interceptors</span></span>](../core/troubleshooting-bam-interceptors.md)  
  
-   [<span data-ttu-id="95ba5-112">BAM 攔截器的安全性考量</span><span class="sxs-lookup"><span data-stu-id="95ba5-112">Security Considerations for BAM Interceptors</span></span>](../core/security-considerations-for-bam-interceptors.md)  
  
-   [<span data-ttu-id="95ba5-113">攔截器組態檔</span><span class="sxs-lookup"><span data-stu-id="95ba5-113">Interceptor Configuration File</span></span>](../core/interceptor-configuration-file.md)  
  
-   [<span data-ttu-id="95ba5-114">BAM WF 攔截器</span><span class="sxs-lookup"><span data-stu-id="95ba5-114">BAM WF Interceptor</span></span>](../core/bam-wf-interceptor.md)  
  
-   [<span data-ttu-id="95ba5-115">設定 WCF 配接器攔截 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="95ba5-115">Configuring the WCF Adapter to Intercept BAM Data</span></span>](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)  
  
-   [<span data-ttu-id="95ba5-116">BAM WCF 攔截器</span><span class="sxs-lookup"><span data-stu-id="95ba5-116">BAM WCF Interceptor</span></span>](../core/bam-wcf-interceptor.md)