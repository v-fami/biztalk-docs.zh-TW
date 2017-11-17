---
title: "使用 Visual Studio，以促進測試自動化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78f622af-08d5-480c-bd5e-f1db52e8d490
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43d6e7d9757ccfe0a5c633dab926f2acbec7e5df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-visual-studio-to-facilitate-automated-testing"></a><span data-ttu-id="f05ed-102">使用 Visual Studio，以促進自動化測試</span><span class="sxs-lookup"><span data-stu-id="f05ed-102">Using Visual Studio to Facilitate Automated Testing</span></span>
<span data-ttu-id="f05ed-103">Visual Studio 2010 提供功能強大的負載測試功能，可以模擬多達數百個使用者同時存取伺服器應用程式的負載設定檔。</span><span class="sxs-lookup"><span data-stu-id="f05ed-103">Visual Studio 2010 provides powerful load test functionality that can simulate a load profile of up to hundreds of users simultaneously accessing a server application.</span></span> <span data-ttu-id="f05ed-104">這個負載測試功能提供即時的度量資訊。 選取的關鍵效能指標，以及供未來分析資料庫中儲存這些度量的能力。</span><span class="sxs-lookup"><span data-stu-id="f05ed-104">This load testing functionality provides real time metrics for selected key performance indicators as well as the ability to store these metrics in a database for future analysis.</span></span> <span data-ttu-id="f05ed-105">本章節描述使用 Visual Studio 負載測試中，評估 BizTalk Server 應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="f05ed-105">This section describes the use of Visual Studio Load testing to evaluate the performance of a BizTalk Server application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f05ed-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="f05ed-106">In This Section</span></span>  
  
-   [<span data-ttu-id="f05ed-107">步驟 1： 建立單元測試，提交至 BizTalk Server 文件</span><span class="sxs-lookup"><span data-stu-id="f05ed-107">Step 1: Create a Unit Test to Submit Documents to BizTalk Server</span></span>](../technical-guides/step-1-create-a-unit-test-to-submit-documents-to-biztalk-server.md)  
  
-   [<span data-ttu-id="f05ed-108">步驟 2： 設定負載測試控制器和代理程式的電腦</span><span class="sxs-lookup"><span data-stu-id="f05ed-108">Step 2: Configure Load Test Controller and Agent Computers</span></span>](../technical-guides/step-2-configure-load-test-controller-and-agent-computers.md)  
  
-   [<span data-ttu-id="f05ed-109">步驟 3： 建立負載測試，以便同時執行多個單元測試</span><span class="sxs-lookup"><span data-stu-id="f05ed-109">Step 3: Create a Load Test to Perform Multiple Unit Tests Simultaneously</span></span>](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md)  
  
-   [<span data-ttu-id="f05ed-110">步驟 4： 設定負載測試 BizTalk Server 的環境</span><span class="sxs-lookup"><span data-stu-id="f05ed-110">Step 4: Configure BizTalk Server Environment for Load Testing</span></span>](~/technical-guides/step-4-configure-biztalk-server-environment-for-load-testing.md)  
  
-   [<span data-ttu-id="f05ed-111">步驟 5： 執行步驟負載模式測試，來判斷最大持續輸送量</span><span class="sxs-lookup"><span data-stu-id="f05ed-111">Step 5: Perform Step Load Pattern Tests to Determine Maximum Sustainable Throughput</span></span>](../technical-guides/step-5-complete-step-load-tests-to-determine-maximum-sustainable-throughput.md)  
  
-   [<span data-ttu-id="f05ed-112">步驟 6： 執行常數負載模式測試，以確認最大持續輸送量</span><span class="sxs-lookup"><span data-stu-id="f05ed-112">Step 6: Perform Constant Load Pattern Tests to Verify Maximum Sustainable Throughput</span></span>](../technical-guides/step-6-complete-load-pattern-tests-to-verify-maximum-sustainable-throughput.md)