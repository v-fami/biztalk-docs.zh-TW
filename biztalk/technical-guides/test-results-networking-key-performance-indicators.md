---
title: 測試結果： 網路功能關鍵效能指標 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9bdbc2df-9d19-4ae8-b540-ec1b9a7cdbe9
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3eb4e10c739178e6cd923f65b51f982e05ab7f56
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="test-results-networking-key-performance-indicators"></a><span data-ttu-id="e10c9-102">測試結果： 網路功能關鍵效能指標</span><span class="sxs-lookup"><span data-stu-id="e10c9-102">Test Results: Networking Key Performance Indicators</span></span>
<span data-ttu-id="e10c9-103">本主題摘要說明網路關鍵效能指標 (KPI) 內所觀測到的測試案例。</span><span class="sxs-lookup"><span data-stu-id="e10c9-103">This topic summarizes Network Key Performance Indicators (KPI) observed during the test scenarios.</span></span> <span data-ttu-id="e10c9-104">這些測試評估所測量的網路效能**\Network 介面 (\*) \Bytes Total/sec**效能監視器計數器和藉由測量**SQL Network Interface\Bytes Total/sec （平均）** VSTS 2008 負載測試控制器所傳回。</span><span class="sxs-lookup"><span data-stu-id="e10c9-104">These tests evaluated Network Performance as measured by the **\Network Interface(\*)\Bytes Total/sec** performance monitor counter and by measuring the **SQL Network Interface\Bytes Total/sec (Avg )** returned by the VSTS 2008 Load Test Controller.</span></span>  
  
## <a name="summary-of-network-key-performance-indicators"></a><span data-ttu-id="e10c9-105">網路關鍵效能指標的摘要</span><span class="sxs-lookup"><span data-stu-id="e10c9-105">Summary of Network Key Performance Indicators</span></span>  
 <span data-ttu-id="e10c9-106">**比較的網路功能關鍵效能指標 –** HYPER-V 虛擬機器上執行的 BizTalk Server 的網路輸送量發現，範圍從大約 70%到 96%達成實體 BizTalk 伺服器上的網路輸送量根據特定的測試環境。</span><span class="sxs-lookup"><span data-stu-id="e10c9-106">**Comparison of Networking Key Performance Indicators –** Network throughput for BizTalk Server running on Hyper-V virtual machines was observed to range from approximately 70% to 96% of the network throughput achieved on the physical BizTalk Servers, depending on the particular test environment.</span></span> <span data-ttu-id="e10c9-107">HYPER-V 虛擬機器上執行的 SQL Server 的網路輸送量發現，範圍從大約 68%到 81%達成實體的 SQL Server，再根據特定的測試環境上的網路輸送量。</span><span class="sxs-lookup"><span data-stu-id="e10c9-107">Network throughput for SQL Server running on a Hyper-V virtual machine was observed to range from approximately 68% to 81% of the network throughput achieved on the physical SQL Server, again depending on the particular test environment.</span></span> <span data-ttu-id="e10c9-108">在觀察到的網路輸送量差異可以屬於 HYPER-V Hypervisor 的資源需求。</span><span class="sxs-lookup"><span data-stu-id="e10c9-108">The delta in the observed network throughput can be attributed to the resource requirements of the Hyper-V Hypervisor.</span></span>  
  
 <span data-ttu-id="e10c9-109">請依照[網路最佳化](../technical-guides/network-optimizations.md)來最大化所測量的 HYPER-V 虛擬機器上的網路輸送量**\Network 介面 (\*) \Bytes Total/sec**</span><span class="sxs-lookup"><span data-stu-id="e10c9-109">Follow the steps in [Network Optimizations](../technical-guides/network-optimizations.md) to maximize network throughput on Hyper-V virtual machines as measured by **\Network Interface(\*)\Bytes Total/sec**</span></span>  
  
 <span data-ttu-id="e10c9-110">下圖將說明在不同的測試平台上的網路效能：</span><span class="sxs-lookup"><span data-stu-id="e10c9-110">The graphic below illustrates the network performance on the various test platforms:</span></span>  
  
 <span data-ttu-id="e10c9-111">![網路功能關鍵效能指標](../technical-guides/media/networkkpi.gif "NetworkKPI")</span><span class="sxs-lookup"><span data-stu-id="e10c9-111">![Networking Key Performance Indicators](../technical-guides/media/networkkpi.gif "NetworkKPI")</span></span>  
  
 <span data-ttu-id="e10c9-112">下表說明收集 KPI 的每個組態的相對效能。</span><span class="sxs-lookup"><span data-stu-id="e10c9-112">The table below illustrates the relative performance of the collected KPI’s for each configuration.</span></span> <span data-ttu-id="e10c9-113">每個結果集的計算方式為基準設定 KPI 的百分比</span><span class="sxs-lookup"><span data-stu-id="e10c9-113">Each result set is calculated as a percentage of the Baseline configuration KPI</span></span>  
  
|<span data-ttu-id="e10c9-114">KPI</span><span class="sxs-lookup"><span data-stu-id="e10c9-114">KPI</span></span>|<span data-ttu-id="e10c9-115">虛擬 BizTalk/實體 SQL</span><span class="sxs-lookup"><span data-stu-id="e10c9-115">Virtual BizTalk/Physical SQL</span></span>|<span data-ttu-id="e10c9-116">在不同的主機虛擬 BizTalk/虛擬 SQL</span><span class="sxs-lookup"><span data-stu-id="e10c9-116">Virtual BizTalk/Virtual SQL on separate Hosts</span></span>|<span data-ttu-id="e10c9-117">合併環境上的虛擬 BizTalk/虛擬 SQL</span><span class="sxs-lookup"><span data-stu-id="e10c9-117">Virtual BizTalk/Virtual SQL on Consolidated environment</span></span>|  
|---------|-----------------------------------|----------------------------------------------------|--------------------------------------------------------------|  
|<span data-ttu-id="e10c9-118">\Network 介面 （\*） \Bytes 總數/秒 （所有 BizTalk 伺服器之間平均總）</span><span class="sxs-lookup"><span data-stu-id="e10c9-118">\Network Interface(\*)\Bytes Total/sec (Total Avg Across all BizTalk Servers)</span></span>|<span data-ttu-id="e10c9-119">96%</span><span class="sxs-lookup"><span data-stu-id="e10c9-119">96%</span></span>|<span data-ttu-id="e10c9-120">82.1%</span><span class="sxs-lookup"><span data-stu-id="e10c9-120">82.1%</span></span>|<span data-ttu-id="e10c9-121">70.2%</span><span class="sxs-lookup"><span data-stu-id="e10c9-121">70.2%</span></span>|  
|<span data-ttu-id="e10c9-122">SQL Network Interface\Bytes Total/sec （平均）</span><span class="sxs-lookup"><span data-stu-id="e10c9-122">SQL Network Interface\Bytes Total/sec (Avg )</span></span>|<span data-ttu-id="e10c9-123">95.5%</span><span class="sxs-lookup"><span data-stu-id="e10c9-123">95.5%</span></span>|<span data-ttu-id="e10c9-124">81.2%</span><span class="sxs-lookup"><span data-stu-id="e10c9-124">81.2%</span></span>|<span data-ttu-id="e10c9-125">68.4%</span><span class="sxs-lookup"><span data-stu-id="e10c9-125">68.4%</span></span>|  
  
 <span data-ttu-id="e10c9-126">如需如何評估網路效能的詳細資訊，請參閱**測量網路效能**主題的章節[檢查清單： 在 HYPER-V 上的測量效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)。</span><span class="sxs-lookup"><span data-stu-id="e10c9-126">For more information about how to evaluate Network performance, see the **Measuring Network Performance** section of the topic [Checklist: Measuring Performance on Hyper-V](../technical-guides/checklist-measuring-performance-on-hyper-v.md).</span></span>