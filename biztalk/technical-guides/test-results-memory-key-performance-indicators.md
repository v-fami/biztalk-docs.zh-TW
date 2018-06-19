---
title: 測試結果： 記憶體關鍵效能指標 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 224c40e5-08a7-4d30-b03a-4b6add5cde1f
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4edf88023ee9e30e7fd0c808346b6231112f8ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22301870"
---
# <a name="test-results-memory-key-performance-indicators"></a><span data-ttu-id="1a7b4-102">測試結果： 記憶體關鍵效能指標</span><span class="sxs-lookup"><span data-stu-id="1a7b4-102">Test Results: Memory Key Performance Indicators</span></span>
<span data-ttu-id="1a7b4-103">本主題摘要說明記憶體關鍵效能指標 (KPI) 內所觀測到的測試案例。</span><span class="sxs-lookup"><span data-stu-id="1a7b4-103">This topic summarizes Memory Key Performance Indicators (KPI) observed during the test scenarios.</span></span> <span data-ttu-id="1a7b4-104">這些測試會評估可用的記憶體，測量由**\Memory\Available Mbytes**效能監視器計數器。</span><span class="sxs-lookup"><span data-stu-id="1a7b4-104">These tests evaluated available memory as measured by the **\Memory\Available Mbytes** performance monitor counter.</span></span>  
  
## <a name="summary-of-memory-key-performance-indicators"></a><span data-ttu-id="1a7b4-105">記憶體關鍵效能指標的摘要</span><span class="sxs-lookup"><span data-stu-id="1a7b4-105">Summary of Memory Key Performance Indicators</span></span>  
 <span data-ttu-id="1a7b4-106">**記憶體關鍵效能指標 – 比較**適用於 SQL Server，並以所測量的 BizTalk Server 的記憶體總計**\Memory\Available Mbytes**跨所有已相當一致效能監視器計數器測試案例。</span><span class="sxs-lookup"><span data-stu-id="1a7b4-106">**Comparison of Memory Key Performance Indicators –** Total memory available to SQL Server and BizTalk Server as measured by the **\Memory\Available Mbytes** performance monitor counter was fairly consistent across all test scenarios.</span></span> <span data-ttu-id="1a7b4-107">實體 BizTalk Server 電腦，並提供給虛擬機器上執行的 BizTalk Server 電腦的平均記憶體可用的平均記憶體差異是因為，兩個實體的 BizTalk Server 電腦用於測試在三個虛擬機器上執行的 BizTalk Server 電腦用於測試。</span><span class="sxs-lookup"><span data-stu-id="1a7b4-107">The difference in the average memory available to the physical BizTalk Server computers and the average memory available to the BizTalk Server computers running on virtual machines is due to the fact that two physical BizTalk Server computers were used for testing while three BizTalk Server computers running on virtual machines were used for testing.</span></span>  
  
 <span data-ttu-id="1a7b4-108">下圖將說明在不同的測試平台上的記憶體效能：</span><span class="sxs-lookup"><span data-stu-id="1a7b4-108">The graphic below illustrates Memory performance on the various test platforms:</span></span>  
  
 <span data-ttu-id="1a7b4-109">![記憶體關鍵效能指標](../technical-guides/media/memorykpi.gif "MemoryKPI")</span><span class="sxs-lookup"><span data-stu-id="1a7b4-109">![Memory Key Performance Indicators](../technical-guides/media/memorykpi.gif "MemoryKPI")</span></span>  
  
 <span data-ttu-id="1a7b4-110">下表說明收集 KPI 的每個組態的相對效能。</span><span class="sxs-lookup"><span data-stu-id="1a7b4-110">The table below illustrates the relative performance of the collected KPI’s for each configuration.</span></span> <span data-ttu-id="1a7b4-111">每個結果集的計算方式為基準設定 KPI 的百分比</span><span class="sxs-lookup"><span data-stu-id="1a7b4-111">Each result set is calculated as a percentage of the Baseline configuration KPI</span></span>  
  
|<span data-ttu-id="1a7b4-112">KPI</span><span class="sxs-lookup"><span data-stu-id="1a7b4-112">KPI</span></span>|<span data-ttu-id="1a7b4-113">虛擬 BizTalk/實體 SQL</span><span class="sxs-lookup"><span data-stu-id="1a7b4-113">Virtual BizTalk/Physical SQL</span></span>|<span data-ttu-id="1a7b4-114">在不同的主機虛擬 BizTalk/虛擬 SQL</span><span class="sxs-lookup"><span data-stu-id="1a7b4-114">Virtual BizTalk/Virtual SQL on separate Hosts</span></span>|<span data-ttu-id="1a7b4-115">合併環境上的虛擬 BizTalk/虛擬 SQL</span><span class="sxs-lookup"><span data-stu-id="1a7b4-115">Virtual BizTalk/Virtual SQL on Consolidated environment</span></span>|  
|---------|-----------------------------------|----------------------------------------------------|--------------------------------------------------------------|  
|<span data-ttu-id="1a7b4-116">SQL Server 可用的記憶體 (Mb) 每個伺服器</span><span class="sxs-lookup"><span data-stu-id="1a7b4-116">SQL Server Available Memory (Mbytes) Per Server</span></span>|<span data-ttu-id="1a7b4-117">100.1%</span><span class="sxs-lookup"><span data-stu-id="1a7b4-117">100.1%</span></span>|<span data-ttu-id="1a7b4-118">97.1%</span><span class="sxs-lookup"><span data-stu-id="1a7b4-118">97.1%</span></span>|<span data-ttu-id="1a7b4-119">103.2%</span><span class="sxs-lookup"><span data-stu-id="1a7b4-119">103.2%</span></span>|  
|<span data-ttu-id="1a7b4-120">BizTalk 的總可用記憶體 (Mb)</span><span class="sxs-lookup"><span data-stu-id="1a7b4-120">Total BizTalk Available Memory (Mbytes)</span></span>|<span data-ttu-id="1a7b4-121">88.3%</span><span class="sxs-lookup"><span data-stu-id="1a7b4-121">88.3%</span></span>|<span data-ttu-id="1a7b4-122">95.9%</span><span class="sxs-lookup"><span data-stu-id="1a7b4-122">95.9%</span></span>|<span data-ttu-id="1a7b4-123">96%</span><span class="sxs-lookup"><span data-stu-id="1a7b4-123">96%</span></span>|  
|<span data-ttu-id="1a7b4-124">平均每個伺服器 / BizTalk 可用記憶體 (Mb)</span><span class="sxs-lookup"><span data-stu-id="1a7b4-124">Average Per Server / BizTalk Available Memory (Mbytes)</span></span>|<span data-ttu-id="1a7b4-125">58.9%</span><span class="sxs-lookup"><span data-stu-id="1a7b4-125">58.9%</span></span>|<span data-ttu-id="1a7b4-126">63.9%</span><span class="sxs-lookup"><span data-stu-id="1a7b4-126">63.9%</span></span>|<span data-ttu-id="1a7b4-127">64%</span><span class="sxs-lookup"><span data-stu-id="1a7b4-127">64%</span></span>|  
  
 <span data-ttu-id="1a7b4-128">如需如何評估記憶體效能的詳細資訊，請參閱**測量記憶體效能**主題的章節[檢查清單： 在 HYPER-V 上的測量效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)。</span><span class="sxs-lookup"><span data-stu-id="1a7b4-128">For more information about how to evaluate Memory performance, see the **Measuring Memory Performance** section of the topic [Checklist: Measuring Performance on Hyper-V](../technical-guides/checklist-measuring-performance-on-hyper-v.md).</span></span>