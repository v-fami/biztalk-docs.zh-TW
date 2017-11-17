---
title: "執行功能測試 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b9c8c95-5a25-4255-a4c2-e26c67b7a620
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f17c2701d6aa90393b8839bafc933bea2fba5746
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="performing-functional-testing"></a><span data-ttu-id="68f6f-102">執行功能測試</span><span class="sxs-lookup"><span data-stu-id="68f6f-102">Performing Functional Testing</span></span>
<span data-ttu-id="68f6f-103">若要測試特定的端對端案例或指定的使用案例特定的 BizTalk 應用程式的內容中使用的功能測試。</span><span class="sxs-lookup"><span data-stu-id="68f6f-103">You use functional testing to test a specific end-to-end scenario or a given use case in the context of a particular BizTalk application.</span></span> <span data-ttu-id="68f6f-104">功能測試應該涵蓋所有可能的途徑給定的狀況中，包括失敗路徑。</span><span class="sxs-lookup"><span data-stu-id="68f6f-104">A functional test should cover all the possible paths through a given scenario, including the failure paths.</span></span> <span data-ttu-id="68f6f-105">應該評估失敗的路徑，以確保應用程式適當地處理失敗的狀況。</span><span class="sxs-lookup"><span data-stu-id="68f6f-105">Failure paths should be evaluated to ensure that the application deals with failure conditions appropriately.</span></span>  
  
 <span data-ttu-id="68f6f-106">應叫用 （例如協調流程、 自訂管線元件，以及自訂組件） 的所有成品，並透過這些物件的所有程式碼分支應該經過測試，以及。</span><span class="sxs-lookup"><span data-stu-id="68f6f-106">All the artifacts (such as orchestrations, custom pipeline components, and custom assemblies) should be invoked, and all the code branches through these objects should be tested as well.</span></span> <span data-ttu-id="68f6f-107">應該執行訊息的所有可能組合，以確保訊息正確地通過系統。</span><span class="sxs-lookup"><span data-stu-id="68f6f-107">All the possible combinations of messages should be exercised to ensure that messages flow through the system correctly.</span></span> <span data-ttu-id="68f6f-108">也應該測試無效的訊息，請確定應用程式中發生錯誤時的預期方式會做出反應，及測試包含協調流程和自訂元件的所有例外狀況區塊中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="68f6f-108">Invalid messages should be tested as well to make sure that the application reacts in the expected way in case of error and to test the code contained in all the exception blocks of orchestrations and custom components.</span></span>  
  
## <a name="automating-functional-testing"></a><span data-ttu-id="68f6f-109">自動化功能測試</span><span class="sxs-lookup"><span data-stu-id="68f6f-109">Automating Functional Testing</span></span>  
 <span data-ttu-id="68f6f-110">您應該自動化功能測試，使它快，以便可以重複，且，好讓它將會避免的人為錯誤。</span><span class="sxs-lookup"><span data-stu-id="68f6f-110">You should automate functional testing so that it is fast, so that it can be repeated, and so that it will avoid human errors.</span></span> <span data-ttu-id="68f6f-111">**BizUnit**是宣告式的測試架構，可讓開發人員快速設計測試案例所設計。</span><span class="sxs-lookup"><span data-stu-id="68f6f-111">**BizUnit** is a declarative test framework designed to enable developers to rapidly design test cases.</span></span> <span data-ttu-id="68f6f-112">事實上，XML 組態檔稱為 BizUnit XML 測試案例即已足夠定義應該如何執行測試。</span><span class="sxs-lookup"><span data-stu-id="68f6f-112">In fact, an XML configuration file called BizUnit XML test case is enough to define how a test should be performed.</span></span> <span data-ttu-id="68f6f-113">若要執行測試您可以建立您自己自訂的驅動程式或更輕鬆地利用**Visual Studio 單元測試**或**NUnit**裝載和執行測試。</span><span class="sxs-lookup"><span data-stu-id="68f6f-113">To run tests you can create your own custom driver or more easily leverage **Visual Studio Unit Testing** or **NUnit** to host and run your tests.</span></span>  
  
 <span data-ttu-id="68f6f-114">每個 XML BizUnit 測試案例包含三個階段： **TestSetup**， **TestExecution**，和**TestCleanup**。</span><span class="sxs-lookup"><span data-stu-id="68f6f-114">Every BizUnit XML test case contains three phases: **TestSetup**, **TestExecution**, and **TestCleanup**.</span></span> <span data-ttu-id="68f6f-115">每一個階段可以包含零或多個測試步驟。</span><span class="sxs-lookup"><span data-stu-id="68f6f-115">Each of these phases can contain zero or more test steps.</span></span> <span data-ttu-id="68f6f-116">每個步驟代表工作單位，並實作為.NET 類別，設計用來執行特定工作。</span><span class="sxs-lookup"><span data-stu-id="68f6f-116">Each step represents a unit of work and is implemented as a .NET class designed to perform a certain task.</span></span> <span data-ttu-id="68f6f-117">這個架構會提供一組豐富的元件。</span><span class="sxs-lookup"><span data-stu-id="68f6f-117">This framework provides a rich set of components.</span></span> <span data-ttu-id="68f6f-118">如果您需要了解特定的元件，以符合特定需求，不過，您可以撰寫自己的自訂測試步驟的元件。</span><span class="sxs-lookup"><span data-stu-id="68f6f-118">If you need to realize specialized components to meet specific requirements, however, you can write your own custom test step components.</span></span> <span data-ttu-id="68f6f-119">如需有關這些工具的詳細資訊，請參閱[工具測試](~/technical-guides/tools-for-testing.md)。</span><span class="sxs-lookup"><span data-stu-id="68f6f-119">For more information about these tools, see [Tools for Testing](~/technical-guides/tools-for-testing.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="68f6f-120">使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。</span><span class="sxs-lookup"><span data-stu-id="68f6f-120">Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this program.</span></span> <span data-ttu-id="68f6f-121">請自行承擔使用這個程式的一切風險。</span><span class="sxs-lookup"><span data-stu-id="68f6f-121">Use of this program is entirely at your own risk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f6f-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68f6f-122">See Also</span></span>  
 [<span data-ttu-id="68f6f-123">檢查清單： 測試操作整備</span><span class="sxs-lookup"><span data-stu-id="68f6f-123">Checklist: Testing Operational Readiness</span></span>](../technical-guides/checklist-testing-operational-readiness.md)