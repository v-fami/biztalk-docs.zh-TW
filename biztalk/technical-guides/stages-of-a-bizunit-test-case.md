---
title: "BizUnit 測試案例的階段 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed0e725f-2c52-43f7-ae30-343413a703c2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ff435fd1c69118112b0121bf68b38ae3151885f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="stages-of-a-bizunit-test-case"></a><span data-ttu-id="31ab0-102">BizUnit 測試案例的階段</span><span class="sxs-lookup"><span data-stu-id="31ab0-102">Stages of a BizUnit Test Case</span></span>
<span data-ttu-id="31ab0-103">BizUnit 測試的每個案例包含三個階段： **TestSetup**， **TestExecution**，和**TestCleanup**。</span><span class="sxs-lookup"><span data-stu-id="31ab0-103">Each BizUnit test case consists of three stages: **TestSetup**, **TestExecution**, and **TestCleanup**.</span></span> <span data-ttu-id="31ab0-104">每個階段都包含一或多個測試步驟是負責執行單一不連續的工作單位;例如， **FileCreateStep**負責在您使用指定的檔名指定的位置中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="31ab0-104">Each stage contains one or more test steps that are responsible for performing a single discrete unit of work; for example, the **FileCreateStep** is responsible for creating a file in a location you specify with a given filename.</span></span>  <span data-ttu-id="31ab0-105">BizUnit 包含超過 70 種測試步驟，並提供擴充功能，讓新的測試步驟，來輕鬆地新增到架構中。</span><span class="sxs-lookup"><span data-stu-id="31ab0-105">BizUnit includes over 70 test steps and also provides extension capabilities which allow new test steps to be easily added to the framework.</span></span> <span data-ttu-id="31ab0-106">將新的步驟新增至架構的功能可讓 BizUnit 跨廣泛的案例使用。</span><span class="sxs-lookup"><span data-stu-id="31ab0-106">The ability to add new steps to the framework allows BizUnit to be used across a broad range of scenarios.</span></span> <span data-ttu-id="31ab0-107">本主題說明的 BizUnit 測試階段中進一步的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="31ab0-107">This topic describes the BizUnit test stages in further detail.</span></span>  
  
## <a name="setup-stage"></a><span data-ttu-id="31ab0-108">安裝程式階段</span><span class="sxs-lookup"><span data-stu-id="31ab0-108">Setup Stage</span></span>  
 <span data-ttu-id="31ab0-109">此安裝程式階段準備進行測試的平台。</span><span class="sxs-lookup"><span data-stu-id="31ab0-109">This setup stage prepares the platform for the testing.</span></span> <span data-ttu-id="31ab0-110">比方說，您可以執行特定測試之前，檔案可能需要複製到檔案中的卸除的實際執行測試的準備。</span><span class="sxs-lookup"><span data-stu-id="31ab0-110">For example, before a particular test can be run, a file may need to be copied to a file drop in preparation for the actual execution of the test.</span></span> <span data-ttu-id="31ab0-111">您也可以使用此階段中的，清除任何檔案位置或將測試中使用的資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="31ab0-111">You could also use this stage to cleanup any file locations or database tables that will be used in the test.</span></span> <span data-ttu-id="31ab0-112">由於使用 BizUnit 中每個階段，可以加入測試步驟的數目沒有限制，可處理複雜的案例所需的彈性。</span><span class="sxs-lookup"><span data-stu-id="31ab0-112">As with every stage in BizUnit, there is no limit to the number of test steps that can be added, which provides the flexibility required to handle complex scenarios.</span></span>  
  
## <a name="execution-stage"></a><span data-ttu-id="31ab0-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="31ab0-113">Execution Stage</span></span>  
 <span data-ttu-id="31ab0-114">在執行階段是實際執行測試。</span><span class="sxs-lookup"><span data-stu-id="31ab0-114">The execution stage is where the test is actually run.</span></span> <span data-ttu-id="31ab0-115">這是您要驗證的系統函式會實際測試。</span><span class="sxs-lookup"><span data-stu-id="31ab0-115">This is where the function of the system you are validating is actually tested.</span></span>  
  
## <a name="cleanup-stage"></a><span data-ttu-id="31ab0-116">清理階段</span><span class="sxs-lookup"><span data-stu-id="31ab0-116">Cleanup Stage</span></span>  
 <span data-ttu-id="31ab0-117">清理階段是測試步驟的平台返回執行測試之前的一致狀態的容器。</span><span class="sxs-lookup"><span data-stu-id="31ab0-117">The cleanup stage is the container for test steps that returns the platform to the consistent state that it was in before you ran the test.</span></span> <span data-ttu-id="31ab0-118">一律執行這個階段，即使在執行階段中發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="31ab0-118">This stage is always executed, even if an error occurs in the execution stage.</span></span> <span data-ttu-id="31ab0-119">平台應該傳回給它的起點的原因是要防止，讓每個測試案例會做為測試套件的一部分執行自主干擾另一個測試案例。</span><span class="sxs-lookup"><span data-stu-id="31ab0-119">The reason the platform should be returned to its starting point is to prevent one test case from interfering with another so that each test case is run autonomously as part of the test suite.</span></span> <span data-ttu-id="31ab0-120">確保系統的完整清除在這個階段是一個有效 BizUnit 測試的基本原則。</span><span class="sxs-lookup"><span data-stu-id="31ab0-120">Ensuring a complete cleanup of the system at this stage is one of the guiding principles for effective testing with BizUnit.</span></span>  
  
 <span data-ttu-id="31ab0-121">下圖說明範例測試案例，其中包含三個階段中的測試步驟的格式： 安裝、 執行和清除。</span><span class="sxs-lookup"><span data-stu-id="31ab0-121">The following diagram illustrates the format of a sample test case, which contains test steps in the three stages: setup, execution, and cleanup.</span></span> <span data-ttu-id="31ab0-122">請務必定義具有 BizUnit 測試案例時，永遠遵循此結構。</span><span class="sxs-lookup"><span data-stu-id="31ab0-122">It is important to always follow this structure when defining test cases with BizUnit.</span></span>  
  
 <span data-ttu-id="31ab0-123">![BizUnit 測試的階段](../technical-guides/media/0a3e2e30-8329-4e87-ae83-f50f7b6aa0a4.gif "0a3e2e30-8329-4e87-ae83-f50f7b6aa0a4")</span><span class="sxs-lookup"><span data-stu-id="31ab0-123">![Stages of a BizUnit Test](../technical-guides/media/0a3e2e30-8329-4e87-ae83-f50f7b6aa0a4.gif "0a3e2e30-8329-4e87-ae83-f50f7b6aa0a4")</span></span>  
<span data-ttu-id="31ab0-124">BizUnit 測試的階段</span><span class="sxs-lookup"><span data-stu-id="31ab0-124">Stages of a BizUnit test</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31ab0-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31ab0-125">See Also</span></span>  
 [<span data-ttu-id="31ab0-126">使用 BizUnit 促進自動化測試</span><span class="sxs-lookup"><span data-stu-id="31ab0-126">Using BizUnit to Facilitate Automated Testing</span></span>](../technical-guides/using-bizunit-to-facilitate-automated-testing.md)