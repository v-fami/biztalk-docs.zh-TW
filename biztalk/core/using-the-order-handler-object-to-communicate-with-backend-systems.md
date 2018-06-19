---
title: 使用訂單處理常式物件與後端系統通訊 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IOrderHandler interface
- process management solution tutorial, IOrderHandler interface
ms.assetid: b9fe4120-bf2a-4d15-a34b-6b98f026b984
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d7621c4e5737def0e9fc0682de709ae57f98790
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288062"
---
# <a name="using-the-order-handler-object-to-communicate-with-backend-systems"></a><span data-ttu-id="d211e-102">使用訂單處理常式物件與後端系統通訊</span><span class="sxs-lookup"><span data-stu-id="d211e-102">Using the Order Handler Object to Communicate with Backend Systems</span></span>
<span data-ttu-id="d211e-103">商務程序管理解決方案和傳統的後端訂單系統有多種通訊方式，而後端訂單系統就是接收最後訂單的網路供給系統。</span><span class="sxs-lookup"><span data-stu-id="d211e-103">There are many ways in which the business process management solution could communicate with the legacy back-end order system, the cable provisioning system that receives the final orders.</span></span> <span data-ttu-id="d211e-104">解決方案會使用 Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] 中的 .NET 遠端處理功能來和供給系統通訊。</span><span class="sxs-lookup"><span data-stu-id="d211e-104">The solution uses the .NET remoting facilities found in Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] to communicate with the provisioning system.</span></span>  
  
 <span data-ttu-id="d211e-105">解決方案使用一般的技術，藉由使用介面定義後端系統的存取物件。</span><span class="sxs-lookup"><span data-stu-id="d211e-105">The solution uses a common technique of using an interface to define the access object to the back-end system.</span></span> <span data-ttu-id="d211e-106">將介面放置在個別的組件中，用戶端組件就可以存取遠端物件，而不需要存取編譯的組件。</span><span class="sxs-lookup"><span data-stu-id="d211e-106">By putting the interface in a separate assembly the client assembly can have access to the remote object without having to have access to the compiled assembly.</span></span>  
  
 <span data-ttu-id="d211e-107">**IOrderHandler**介面會定義與後端訂單系統通訊的方法。</span><span class="sxs-lookup"><span data-stu-id="d211e-107">The **IOrderHandler** interface defines the methods to communicate with the backend order system.</span></span> <span data-ttu-id="d211e-108">介面包含了分析、啟動、取消以及完成訂單的方法。</span><span class="sxs-lookup"><span data-stu-id="d211e-108">The interface includes methods for analyzing, activating, canceling, and completing orders.</span></span> <span data-ttu-id="d211e-109">介面也提供了識別服務類型的方法，這是在取消訂單時必須使用的方法。</span><span class="sxs-lookup"><span data-stu-id="d211e-109">It also provides a method for identifying the service type, a method needed when an order is canceled.</span></span>  
  
 <span data-ttu-id="d211e-110">**CableOrder1**， **CableOrder2**，和附屬協調流程會使用**OrderHandlerWrapper**實作物件**IOrderHandler**.</span><span class="sxs-lookup"><span data-stu-id="d211e-110">The **CableOrder1**, **CableOrder2**, and satellite orchestrations use the **OrderHandlerWrapper** object that implements **IOrderHandler**.</span></span> <span data-ttu-id="d211e-111">**OrderHandlerWrapper**物件，接著，會叫用的遠端執行個體**OrderHandler**所提供物件**CableProvisioningSystemServer**可執行檔。</span><span class="sxs-lookup"><span data-stu-id="d211e-111">The **OrderHandlerWrapper** object, in turn, invokes a remote instance of an **OrderHandler** object provided by the **CableProvisioningSystemServer** executable.</span></span> <span data-ttu-id="d211e-112">使用包裝函式物件不僅符合使用 .NET 遠端處理來與後端訂單系統通訊的商務需求，同時也會啟用例外狀況處理元件的重試功能。</span><span class="sxs-lookup"><span data-stu-id="d211e-112">Using the wrapper object meets the business requirement of using .NET remoting to communicate with the back-end order system while, at the same time, enabling use of the retry features of the exception handling components.</span></span>  
  
 <span data-ttu-id="d211e-113">因為其中一個必須能序列化在協調流程中參考的每個物件**OrderHandlerWrapper**也可以序列化。</span><span class="sxs-lookup"><span data-stu-id="d211e-113">Because one must be able to serialize every object referenced in an orchestration, the **OrderHandlerWrapper** can also be serialized.</span></span> <span data-ttu-id="d211e-114">使用**OrderHandlerWrapper**隔離協調流程的序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="d211e-114">Using the **OrderHandlerWrapper** isolates the serialization code from the orchestrations.</span></span>  
  
 <span data-ttu-id="d211e-115">如果您查看程式碼時，您將 se， **OrderHandlerWrapper**物件會明確實作**ISerializable**介面。</span><span class="sxs-lookup"><span data-stu-id="d211e-115">If you look at the code, you'll se that the **OrderHandlerWrapper** object explicitly implements the **ISerializable** interface.</span></span> <span data-ttu-id="d211e-116">物件必須處理自己的序列化，因為物件使用的非預設的建構函式。</span><span class="sxs-lookup"><span data-stu-id="d211e-116">The object must handle its own serialization because it uses a non-default constructor.</span></span>  
  
 <span data-ttu-id="d211e-117">使用 .NET 遠端處理來與後端系統通訊比使用傳訊更有效率。</span><span class="sxs-lookup"><span data-stu-id="d211e-117">Using .NET remoting to communicate with the backend system is more efficient than using messaging.</span></span> <span data-ttu-id="d211e-118">另外，.NET 遠端處理會將協調流程更緊密地繫結到後端系統，而這是單純的傳訊解決方案無法做到的。</span><span class="sxs-lookup"><span data-stu-id="d211e-118">On the other hand, it binds the orchestrations more tightly to the back-end system than a pure messaging solution might.</span></span> <span data-ttu-id="d211e-119">使用 .NET 遠端處理也可避免解決方案利用內建的 BizTalk Server 功能來重試要求。</span><span class="sxs-lookup"><span data-stu-id="d211e-119">Using .NET remoting also prevents the solution from taking advantage of the built-in BizTalk Server features for retrying requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d211e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d211e-120">See Also</span></span>  
 <span data-ttu-id="d211e-121">[商務程序管理解決方案的實作重點](../core/implementation-highlights-of-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="d211e-121">[Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="d211e-122">程序管理員邏輯</span><span class="sxs-lookup"><span data-stu-id="d211e-122">Process Manager Logic</span></span>](../core/process-manager-logic.md)