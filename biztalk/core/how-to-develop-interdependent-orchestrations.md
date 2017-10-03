---
title: "如何開發具有相依性的協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5464096e-66d8-48de-bc02-c754c5cfbada
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93f8d086a60487e144b02c01a393eb6f10a63b40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-develop-interdependent-orchestrations"></a><span data-ttu-id="5341c-102">如何開發具有相依性的協調流程</span><span class="sxs-lookup"><span data-stu-id="5341c-102">How to Develop Interdependent Orchestrations</span></span>
<span data-ttu-id="5341c-103">您可以使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 開發一組具有相依性 Web 服務的協調流程。</span><span class="sxs-lookup"><span data-stu-id="5341c-103">You can use [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to develop a set of orchestrations that have interdependent Web services.</span></span> <span data-ttu-id="5341c-104">當第一個協調流程呼叫第二個協調流程，而且第二個協調流程參考第一個協調流程中的資料型別和 (或) 連接埠時，會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="5341c-104">This scenario arises when you have orchestrations that reference data types and/or ports in the orchestration from which they were called.</span></span> <span data-ttu-id="5341c-105">這種實例的範例有下列特性：</span><span class="sxs-lookup"><span data-stu-id="5341c-105">An example of this type of scenario is characterized by the following:</span></span>  
  
-   <span data-ttu-id="5341c-106">您有兩個以上的協調流程。</span><span class="sxs-lookup"><span data-stu-id="5341c-106">You have two or more orchestrations.</span></span>  
  
-   <span data-ttu-id="5341c-107">第一個協調流程 (Orch1) 透過單向 Web 服務呼叫來呼叫第二個協調流程 (Orch2)。</span><span class="sxs-lookup"><span data-stu-id="5341c-107">The first orchestration (Orch1) calls the second orchestration (Orch2) with a one-way Web service call.</span></span>  
  
-   <span data-ttu-id="5341c-108">Orch2 透過 Web 服務呼叫來回應 Orch1。</span><span class="sxs-lookup"><span data-stu-id="5341c-108">Orch2 responds back to Orch1 with a Web service call.</span></span>  
  
 <span data-ttu-id="5341c-109">此專案類型的一個範例，請參閱[教學課程 2： 訂單程序](http://msdn.microsoft.com/library/a324ef1b-39b3-49ab-9719-a13f526cb467)。</span><span class="sxs-lookup"><span data-stu-id="5341c-109">For one example of this type of project, see [Tutorial 2: Purchase Order Process](http://msdn.microsoft.com/library/a324ef1b-39b3-49ab-9719-a13f526cb467).</span></span>  
  
### <a name="to-develop-two-interdependent-orchestrations-orch1-and-orch2"></a><span data-ttu-id="5341c-110">若要開發兩個具有相依性的協調流程 Orch1 和 Orch2</span><span class="sxs-lookup"><span data-stu-id="5341c-110">To develop two interdependent orchestrations Orch1 and Orch2</span></span>  
  
1.  <span data-ttu-id="5341c-111">使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，建立其接收埠將公開為 Web 服務的 Orch1 部分版本。</span><span class="sxs-lookup"><span data-stu-id="5341c-111">Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create a partial version of the Orch1 that has a receive port which will be exposed as a Web service.</span></span>  
  
2.  <span data-ttu-id="5341c-112">編譯 Orch1。</span><span class="sxs-lookup"><span data-stu-id="5341c-112">Compile Orch1.</span></span>  
  
3.  <span data-ttu-id="5341c-113">執行 [Web 服務發佈精靈] 並發佈此連接埠。</span><span class="sxs-lookup"><span data-stu-id="5341c-113">Run the Web Services Publishing Wizard and publish the port.</span></span>  
  
4.  <span data-ttu-id="5341c-114">使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，建立並完成 Orch2，其取用 Orch1 的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="5341c-114">Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create and complete all of Orch2, consuming Orch1's web service.</span></span>  
  
5.  <span data-ttu-id="5341c-115">編譯 Orch2。</span><span class="sxs-lookup"><span data-stu-id="5341c-115">Compile Orch2.</span></span>  
  
6.  <span data-ttu-id="5341c-116">執行 [Web 服務發佈精靈] 並發佈連接埠。</span><span class="sxs-lookup"><span data-stu-id="5341c-116">Run the Web Services Publishing Wizard and publish the port(s).</span></span>  
  
7.  <span data-ttu-id="5341c-117">完成 Orch1，並在必要時取用 Orch2 的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="5341c-117">Complete Orch1, consuming Orch2's web service(s) as needed.</span></span>  
  
8.  <span data-ttu-id="5341c-118">重新編譯 Orch1。</span><span class="sxs-lookup"><span data-stu-id="5341c-118">Recompile Orch1.</span></span>  
  
9. <span data-ttu-id="5341c-119">部署 Orch1 和 Orch2。</span><span class="sxs-lookup"><span data-stu-id="5341c-119">Deploy Orch1 and Orch2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5341c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5341c-120">See Also</span></span>  
 [<span data-ttu-id="5341c-121">如何使用 BizTalk Web 服務發佈精靈發佈為 Web 服務的協調流程</span><span class="sxs-lookup"><span data-stu-id="5341c-121">How to Use the BizTalk Web Services Publishing Wizard to Publish an Orchestration as a Web Service</span></span>](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)