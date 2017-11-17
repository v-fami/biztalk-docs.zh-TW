---
title: "檢查清單： 監視操作整備 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef77ccc2-1d39-4e78-8fea-5c17d05c8174
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 913ed00da2bda4126ba298bbb9bce2980efa4366
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-monitoring-operational-readiness"></a><span data-ttu-id="0283a-102">檢查清單： 監視操作整備</span><span class="sxs-lookup"><span data-stu-id="0283a-102">Checklist: Monitoring Operational Readiness</span></span>
<span data-ttu-id="0283a-103">本主題列出監視生產環境時，您應該遵循的步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="0283a-103">This topic lists the steps that you should follow when monitoring a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  
  
|<span data-ttu-id="0283a-104">步驟</span><span class="sxs-lookup"><span data-stu-id="0283a-104">Steps</span></span>|<span data-ttu-id="0283a-105">參考</span><span class="sxs-lookup"><span data-stu-id="0283a-105">Reference</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="0283a-106">選取及實作您的 BizTalk 應用程式和基礎結構的監視策略。</span><span class="sxs-lookup"><span data-stu-id="0283a-106">Select and implement a monitoring strategy for your BizTalk applications and infrastructure.</span></span>|[<span data-ttu-id="0283a-107">監控 BizTalk Server 環境</span><span class="sxs-lookup"><span data-stu-id="0283a-107">Monitoring the BizTalk Server Environment</span></span>](../technical-guides/monitoring-the-biztalk-server-environment.md)|  
|<span data-ttu-id="0283a-108">監視磁碟空間使用量。</span><span class="sxs-lookup"><span data-stu-id="0283a-108">Monitor disk space usage.</span></span>|[<span data-ttu-id="0283a-109">監視磁碟空間使用量</span><span class="sxs-lookup"><span data-stu-id="0283a-109">Monitoring Disk Space Usage</span></span>](../technical-guides/monitoring-disk-space-usage.md)|  
|<span data-ttu-id="0283a-110">監視 SQL Server:</span><span class="sxs-lookup"><span data-stu-id="0283a-110">Monitor SQL Server:</span></span><br /><br /> <span data-ttu-id="0283a-111">-確認執行 SQL Server 外罩該電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]受監視的資料庫。</span><span class="sxs-lookup"><span data-stu-id="0283a-111">-   Verify that computers running SQL Server housing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are being monitored.</span></span><br /><span data-ttu-id="0283a-112">-確認[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]受監視的工作。</span><span class="sxs-lookup"><span data-stu-id="0283a-112">-   Verify that the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] jobs are being monitored.</span></span>|<span data-ttu-id="0283a-113">-   [監視 SQL Server](../technical-guides/monitoring-sql-servers.md)</span><span class="sxs-lookup"><span data-stu-id="0283a-113">-   [Monitoring SQL Servers](../technical-guides/monitoring-sql-servers.md)</span></span><br /><span data-ttu-id="0283a-114">-   [監控 BizTalk Server 資料庫](../technical-guides/monitoring-biztalk-server-databases.md)</span><span class="sxs-lookup"><span data-stu-id="0283a-114">-   [Monitoring BizTalk Server Databases](../technical-guides/monitoring-biztalk-server-databases.md)</span></span>|  
|<span data-ttu-id="0283a-115">監控 BizTalk 應用程式：</span><span class="sxs-lookup"><span data-stu-id="0283a-115">Monitor BizTalk applications:</span></span><br /><br /> <span data-ttu-id="0283a-116">-修改現有的規則和 （或） 複製到自訂管理組件來監視自訂 BizTalk 應用程式的規則。</span><span class="sxs-lookup"><span data-stu-id="0283a-116">-   Modify existing rules and/or copy rules to a custom management pack to monitor a custom BizTalk application.</span></span><br /><span data-ttu-id="0283a-117">-建立每個已定義的規則的動作。</span><span class="sxs-lookup"><span data-stu-id="0283a-117">-   Create actions for each defined rule.</span></span><br /><span data-ttu-id="0283a-118">-建立反覆的程序來自動化手動工作。</span><span class="sxs-lookup"><span data-stu-id="0283a-118">-   Create iterative processes to automate manual tasks.</span></span><br /><span data-ttu-id="0283a-119">-使用臨界值規則以自動執行的手動工作。</span><span class="sxs-lookup"><span data-stu-id="0283a-119">-   Use threshold rules to automate manual tasks.</span></span>|<span data-ttu-id="0283a-120">-   [監視應用程式和主控件執行個體](../technical-guides/monitoring-applications-and-host-instances.md)</span><span class="sxs-lookup"><span data-stu-id="0283a-120">-   [Monitoring Applications and Host Instances](../technical-guides/monitoring-applications-and-host-instances.md)</span></span><br /><span data-ttu-id="0283a-121">-   [監控 BizTalk Server2](../technical-guides/monitoring-biztalk-server2.md)</span><span class="sxs-lookup"><span data-stu-id="0283a-121">-   [Monitoring BizTalk Server2](../technical-guides/monitoring-biztalk-server2.md)</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="0283a-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="0283a-122">In This Section</span></span>  
  
-   [<span data-ttu-id="0283a-123">監視磁碟空間使用量</span><span class="sxs-lookup"><span data-stu-id="0283a-123">Monitoring Disk Space Usage</span></span>](../technical-guides/monitoring-disk-space-usage.md)