---
title: "規劃高 Availability3 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, high availability
- high availability
- planning, high availability
- high availability, architecture
ms.assetid: 16feada0-b0b1-4e58-9477-fbd1aae2f51e
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a6a8a69af5fd1ff59a4e69e02a52124d89db1ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-high-availability"></a><span data-ttu-id="bcac9-102">高可用性的規劃</span><span class="sxs-lookup"><span data-stu-id="bcac9-102">Planning for High Availability</span></span>
<span data-ttu-id="bcac9-103">許多公司使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 處理其企業所仰賴的資料。</span><span class="sxs-lookup"><span data-stu-id="bcac9-103">Many companies use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to process data that their business depends on.</span></span> <span data-ttu-id="bcac9-104">對於這些公司而言，由於硬體故障而延長停機的結果即可能意謂產能與利潤的下降。</span><span class="sxs-lookup"><span data-stu-id="bcac9-104">For these companies, the consequences of a prolonged downtime because of a hardware outage can mean diminished productivity and profitability.</span></span> <span data-ttu-id="bcac9-105">本節說明如何增加 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境的可用性以最大化 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 解決方案的正常執行時間。</span><span class="sxs-lookup"><span data-stu-id="bcac9-105">This section provides guidance for increasing availability of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment in order to maximize uptime of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bcac9-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="bcac9-106">In This Section</span></span>  
-   [<span data-ttu-id="bcac9-107">使用 SQL Server Alwayson 可用性群組的高可用性</span><span class="sxs-lookup"><span data-stu-id="bcac9-107">High Availability using SQL Server Always On Availability Groups</span></span>](../core/high-availability-using-sql-server-always-on-availability-groups.md)
  
-   [<span data-ttu-id="bcac9-108">規劃您的平台的容錯功能</span><span class="sxs-lookup"><span data-stu-id="bcac9-108">Planning Your Platform for Fault Tolerance</span></span>](../core/planning-your-platform-for-fault-tolerance.md)  
  
-   [<span data-ttu-id="bcac9-109">建立高可用性的 BizTalk Server 環境</span><span class="sxs-lookup"><span data-stu-id="bcac9-109">Creating a Highly Available BizTalk Server Environment</span></span>](../core/creating-a-highly-available-biztalk-server-environment.md)  
  
-   [<span data-ttu-id="bcac9-110">BizTalk Server 高可用性實例範例</span><span class="sxs-lookup"><span data-stu-id="bcac9-110">Sample BizTalk Server High Availability Scenarios</span></span>](../core/sample-biztalk-server-high-availability-scenarios.md)  
  
-   [<span data-ttu-id="bcac9-111">企業單一登入的高可用性</span><span class="sxs-lookup"><span data-stu-id="bcac9-111">High Availability for Enterprise Single Sign-On</span></span>](../core/high-availability-for-enterprise-single-sign-on.md)  
  
-   [<span data-ttu-id="bcac9-112">高可用性和 Microsoft Operations Framework</span><span class="sxs-lookup"><span data-stu-id="bcac9-112">High Availability and the Microsoft Operations Framework</span></span>](../core/high-availability-and-the-microsoft-operations-framework.md)  
  
## <a name="reference"></a><span data-ttu-id="bcac9-113">參考</span><span class="sxs-lookup"><span data-stu-id="bcac9-113">Reference</span></span>  
  
-   <span data-ttu-id="bcac9-114">[開始使用 SQL Server 2008 容錯移轉叢集](http://go.microsoft.com/fwlink/?LinkId=130375)(http://go.microsoft.com/fwlink/?LinkId=130375)</span><span class="sxs-lookup"><span data-stu-id="bcac9-114">[Getting Started with SQL Server 2008 Failover Clustering](http://go.microsoft.com/fwlink/?LinkId=130375) (http://go.microsoft.com/fwlink/?LinkId=130375)</span></span>  
  
-   <span data-ttu-id="bcac9-115">[技術白皮書： SQL Server 2008 容錯移轉叢集](http://go.microsoft.com/fwlink/?LinkId=189522)(http://go.microsoft.com/fwlink/?LinkId=189522)</span><span class="sxs-lookup"><span data-stu-id="bcac9-115">[White Paper: SQL Server 2008 Failover Clustering](http://go.microsoft.com/fwlink/?LinkId=189522) (http://go.microsoft.com/fwlink/?LinkId=189522)</span></span>  
  
-   <span data-ttu-id="bcac9-116">[Windows Server 2008 逐步指南](http://go.microsoft.com/fwlink/?LinkId=189545)(http://go.microsoft.com/fwlink/?LinkId=189545)</span><span class="sxs-lookup"><span data-stu-id="bcac9-116">[Windows Server 2008 Step-by-Step Guides](http://go.microsoft.com/fwlink/?LinkId=189545) (http://go.microsoft.com/fwlink/?LinkId=189545)</span></span>