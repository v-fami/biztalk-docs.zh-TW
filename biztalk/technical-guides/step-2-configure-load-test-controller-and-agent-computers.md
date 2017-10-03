---
title: "步驟 2： 設定負載測試控制器和代理程式電腦 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9d937ac-55d8-48fa-bba2-3efe151587b8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f931a05796856816e19b53ff5cba9f53b48c3e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-load-test-controller-and-agent-computers"></a><span data-ttu-id="c0820-102">步驟 2： 設定負載測試控制器和代理程式的電腦</span><span class="sxs-lookup"><span data-stu-id="c0820-102">Step 2: Configure Load Test Controller and Agent Computers</span></span>
<span data-ttu-id="c0820-103">Visual Studio 2010 Ultimate 版可能會產生模擬本機負載測試回合上的最多 250 個虛擬使用者負載。</span><span class="sxs-lookup"><span data-stu-id="c0820-103">Visual Studio 2010 Ultimate edition can generate load simulating up to 250 virtual users on a local load test run.</span></span> <span data-ttu-id="c0820-104">若要模擬超過 250 位虛擬使用者和/或起始測試從遠端電腦需要有 Visual Studio 負載測試虛擬使用者組件 2010年。</span><span class="sxs-lookup"><span data-stu-id="c0820-104">To simulate more than 250 virtual users and/or to initiate testing from a remote computer requires Visual Studio Load Test Virtual User Pack 2010.</span></span>  
  
 <span data-ttu-id="c0820-105">所有負載測試執行本指南是從兩台電腦都起始：</span><span class="sxs-lookup"><span data-stu-id="c0820-105">All load testing performed for this guide was initiated from two computers:</span></span>  
  
-   <span data-ttu-id="c0820-106">為負載測試控制器和負載測試代理程式執行的一部電腦。</span><span class="sxs-lookup"><span data-stu-id="c0820-106">One computer running as both a Load Test Controller and a Load Test Agent.</span></span>  
  
-   <span data-ttu-id="c0820-107">執行負載測試代理程式只能以另一部電腦。</span><span class="sxs-lookup"><span data-stu-id="c0820-107">Another computer running as a Load Test Agent only.</span></span>  
  
 <span data-ttu-id="c0820-108">測試結果儲存在遠端的負載測試結果儲存機制中的 SQL Server 2008 R2 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c0820-108">Test results were stored in a remote load test results repository in a SQL Server 2008 R2 database.</span></span>  
  
 <span data-ttu-id="c0820-109">如需可以分散多部測試電腦上的負載測試中使用測試控制器和測試代理程式的詳細資訊，請參閱[散發負載測試跨多個測試機器使用測試控制器和測試代理程式](http://go.microsoft.com/fwlink/?LinkId=208406)(http://go.microsoft.com/fwlink/ 嗎？LinkId = 208406)。</span><span class="sxs-lookup"><span data-stu-id="c0820-109">For more information about using test controllers and test agents to distribute load tests across multiple test machines, see [Distributing Load Tests Across Multiple Test Machines Using Test Controllers and Test Agents](http://go.microsoft.com/fwlink/?LinkId=208406) (http://go.microsoft.com/fwlink/?LinkId=208406).</span></span>  
  
## <a name="install-and-configure-the-load-test-controller-and-load-test-agents"></a><span data-ttu-id="c0820-110">安裝和設定負載測試控制器和負載測試代理程式</span><span class="sxs-lookup"><span data-stu-id="c0820-110">Install and Configure the Load Test Controller and Load Test Agents</span></span>  
 <span data-ttu-id="c0820-111">若要安裝和設定負載測試控制器和負載測試代理程式，請參閱本主題中的下列章節[安裝和設定 Visual Studio Agents 和測試和組建控制器](http://go.microsoft.com/fwlink/?LinkId=208455)(http://go.microsoft.com/fwlink/?LinkId=208455):</span><span class="sxs-lookup"><span data-stu-id="c0820-111">To install and configure the load test controller and load test agents, see the following sections in the topic [Installing and Configuring Visual Studio Agents and Test and Build Controllers](http://go.microsoft.com/fwlink/?LinkId=208455) (http://go.microsoft.com/fwlink/?LinkId=208455):</span></span>  
  
-   <span data-ttu-id="c0820-112">若要安裝測試控制器，請依照中的程序[安裝測試控制器](http://go.microsoft.com/fwlink/?LinkId=208454)(http://go.microsoft.com/fwlink/?LinkId=208454) 一節。</span><span class="sxs-lookup"><span data-stu-id="c0820-112">To setup a test controller, follow the procedures in the [Install a Test Controller](http://go.microsoft.com/fwlink/?LinkId=208454) (http://go.microsoft.com/fwlink/?LinkId=208454) section.</span></span>  
  
-   <span data-ttu-id="c0820-113">若要安裝測試代理程式，請依照中的程序[安裝測試代理程式](http://go.microsoft.com/fwlink/?LinkId=208456)(http://go.microsoft.com/fwlink/?LinkId=208456) 一節。</span><span class="sxs-lookup"><span data-stu-id="c0820-113">To setup test agents, follow the procedures in the [Install a Test Agent](http://go.microsoft.com/fwlink/?LinkId=208456) (http://go.microsoft.com/fwlink/?LinkId=208456) section.</span></span>