---
title: 步驟 2： 設定負載測試控制器和代理程式電腦 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9d937ac-55d8-48fa-bba2-3efe151587b8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b03a191269936311d04f7b773ed3159db66e34f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972447"
---
# <a name="step-2-configure-load-test-controller-and-agent-computers"></a><span data-ttu-id="daa9d-102">步驟 2： 設定負載測試控制器和代理程式電腦</span><span class="sxs-lookup"><span data-stu-id="daa9d-102">Step 2: Configure Load Test Controller and Agent Computers</span></span>

## <a name="overview"></a><span data-ttu-id="daa9d-103">概觀</span><span class="sxs-lookup"><span data-stu-id="daa9d-103">Overview</span></span>
<span data-ttu-id="daa9d-104">Visual Studio 可以產生模擬最多 250 個虛擬使用者，在本機的負載測試回合的負載。</span><span class="sxs-lookup"><span data-stu-id="daa9d-104">Visual Studio can generate load simulating up to 250 virtual users on a local load test run.</span></span> <span data-ttu-id="daa9d-105">若要模擬超過 250 位虛擬使用者和/或測試從遠端電腦需要有 Visual Studio 負載測試虛擬使用者。</span><span class="sxs-lookup"><span data-stu-id="daa9d-105">To simulate more than 250 virtual users and/or to initiate testing from a remote computer requires Visual Studio Load Test Virtual User.</span></span>  
  
 <span data-ttu-id="daa9d-106">所有負載測試執行本指南中，是從兩台電腦都起始：</span><span class="sxs-lookup"><span data-stu-id="daa9d-106">All load testing performed for this guide was initiated from two computers:</span></span>  
  
- <span data-ttu-id="daa9d-107">為負載測試控制器和負載測試代理程式執行的一部電腦。</span><span class="sxs-lookup"><span data-stu-id="daa9d-107">One computer running as both a Load Test Controller and a Load Test Agent.</span></span>  
  
- <span data-ttu-id="daa9d-108">執行負載測試代理程式只為另一部電腦。</span><span class="sxs-lookup"><span data-stu-id="daa9d-108">Another computer running as a Load Test Agent only.</span></span>  
  
  <span data-ttu-id="daa9d-109">測試結果已儲存在遠端負載測試結果儲存機制中的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="daa9d-109">Test results were stored in a remote load test results repository in a SQL Server database.</span></span>  
  
  <span data-ttu-id="daa9d-110">如需使用 負載測試分散到多部測試電腦的 測試控制器和測試代理程式的詳細資訊，請參閱[散發負載測試跨多部測試機器使用測試控制器和測試代理程式](https://msdn.microsoft.com/library/dd728093.aspx)。</span><span class="sxs-lookup"><span data-stu-id="daa9d-110">For more information about using test controllers and test agents to distribute load tests across multiple test machines, see [Distributing Load Tests Across Multiple Test Machines Using Test Controllers and Test Agents](https://msdn.microsoft.com/library/dd728093.aspx).</span></span>  
  
## <a name="install-and-configure-the-load-test-controller-and-load-test-agents"></a><span data-ttu-id="daa9d-111">安裝和設定負載測試控制器和負載測試代理程式</span><span class="sxs-lookup"><span data-stu-id="daa9d-111">Install and Configure the Load Test Controller and Load Test Agents</span></span>  
 <span data-ttu-id="daa9d-112">若要安裝並設定負載測試控制器，負載測試代理程式，請參閱[安裝和設定測試代理程式](https://docs.microsoft.com/visualstudio/test/lab-management/install-configure-test-agents)。</span><span class="sxs-lookup"><span data-stu-id="daa9d-112">To install and configure the load test controller and load test agents, see [Install and configure test agents](https://docs.microsoft.com/visualstudio/test/lab-management/install-configure-test-agents).</span></span>
