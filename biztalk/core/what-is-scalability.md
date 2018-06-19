---
title: 什麼是擴充性？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scaling, scalability
ms.assetid: ac6acefd-864a-4f22-a136-a1951fe71e96
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a6208319fb8c195558101433cd1668ab0e0f064
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288854"
---
# <a name="what-is-scalability"></a><span data-ttu-id="ab5c0-103">什麼是擴充性？</span><span class="sxs-lookup"><span data-stu-id="ab5c0-103">What Is Scalability?</span></span>
<span data-ttu-id="ab5c0-104">擴充性是系統能擴展到符合您的商務需求之能力。</span><span class="sxs-lookup"><span data-stu-id="ab5c0-104">Scalability is the ability of a system to expand to meet your business needs.</span></span> <span data-ttu-id="ab5c0-105">您可藉由新增硬體或升級現有硬體來擴充系統，而不需要變更太多應用程式。</span><span class="sxs-lookup"><span data-stu-id="ab5c0-105">You scale a system by adding extra hardware or by upgrading the existing hardware without changing much of the application.</span></span> <span data-ttu-id="ab5c0-106">在 BizTalk Server 系統的環境中，擴充性指的是當您的輸送需求增加，或您需要減少延遲時間時，可擴充 BizTalk 的能力。</span><span class="sxs-lookup"><span data-stu-id="ab5c0-106">In the context of a BizTalk Server system, scalability refers to the ability of BizTalk to scale as your throughput needs increase, and if you need to reduce latency times.</span></span>  
  
 <span data-ttu-id="ab5c0-107">在最佳化及調整不同的 BizTalk 元件之後，您還是可能會遇到 BizTalk 電腦或 MessageBox 資料庫上的瓶頸。</span><span class="sxs-lookup"><span data-stu-id="ab5c0-107">After you optimize and tune various components of BizTalk, you might still encounter bottlenecks on BizTalk computers or on the MessageBox database.</span></span> <span data-ttu-id="ab5c0-108">通常會發生在 BizTalk 環境中的瓶頸類型為 CPU、記憶體、IO 以及鎖定爭用瓶頸。</span><span class="sxs-lookup"><span data-stu-id="ab5c0-108">The types of bottlenecks that usually occur in BizTalk environments are CPU, memory, IO and lock contention bottlenecks.</span></span> <span data-ttu-id="ab5c0-109">當您開始遇到瓶頸時，可能需要升級硬體或加入新硬體到現有的拓樸中。</span><span class="sxs-lookup"><span data-stu-id="ab5c0-109">When you start to encounter bottlenecks, you may need to either upgrade the hardware or add new hardware into the existing topology.</span></span> <span data-ttu-id="ab5c0-110">而很幸運地，BizTalk Server 架構可讓您輕易地進行垂直擴充或向外擴充。例如，您可新增多部 BizTalk Server 電腦到群組中，也可新增額外的 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ab5c0-110">Fortunately, BizTalk Server architecture enables you to easily scale-up and scale-out. For example, you can add multiple BizTalk Server computers into the group and also add extra MessageBox databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab5c0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab5c0-111">See Also</span></span>  
 <span data-ttu-id="ab5c0-112">[向外擴充 BizTalk Server 層](../core/scaling-out-the-biztalk-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="ab5c0-112">[Scaling Out the BizTalk Server Tier](../core/scaling-out-the-biztalk-server-tier.md) </span></span>  
 <span data-ttu-id="ab5c0-113">[向外擴充 SQL Server 層](../core/scaling-out-the-sql-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="ab5c0-113">[Scaling Out the SQL Server Tier](../core/scaling-out-the-sql-server-tier.md) </span></span>  
 <span data-ttu-id="ab5c0-114">[向上擴充 BizTalk Server 層](../core/scaling-up-the-biztalk-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="ab5c0-114">[Scaling Up the BizTalk Server Tier](../core/scaling-up-the-biztalk-server-tier.md) </span></span>  
 <span data-ttu-id="ab5c0-115">[向上擴充 SQL Server 層](../core/scaling-up-the-sql-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="ab5c0-115">[Scaling Up the SQL Server Tier](../core/scaling-up-the-sql-server-tier.md) </span></span>  
 <span data-ttu-id="ab5c0-116">[向外擴充接收主控件](../core/scaled-out-receiving-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="ab5c0-116">[Scaled-Out Receiving Hosts](../core/scaled-out-receiving-hosts.md) </span></span>  
 <span data-ttu-id="ab5c0-117">[向外延展處理主控件](../core/scaled-out-processing-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="ab5c0-117">[Scaled-Out Processing Hosts](../core/scaled-out-processing-hosts.md) </span></span>  
 <span data-ttu-id="ab5c0-118">[向外延展傳送主控件](../core/scaled-out-sending-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="ab5c0-118">[Scaled-Out Sending Hosts](../core/scaled-out-sending-hosts.md) </span></span>  
 <span data-ttu-id="ab5c0-119">[使用 Windows 伺服器叢集以提供高可用性的 BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="ab5c0-119">[Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span></span>  
 <span data-ttu-id="ab5c0-120">[向外延展資料庫](../core/scaled-out-databases.md) </span><span class="sxs-lookup"><span data-stu-id="ab5c0-120">[Scaled-Out Databases](../core/scaled-out-databases.md) </span></span>  
 [<span data-ttu-id="ab5c0-121">叢集 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="ab5c0-121">Clustering the BizTalk Server Databases</span></span>](../core/clustering-the-biztalk-server-databases1.md)