---
title: 在協調流程中的持續性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, persistence
- persistence
- BizTalk Server Orchestration Engine
ms.assetid: 2f79d294-f7df-4d84-ba76-50618506b6c6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 184b4a7dde452902f404a5d6ed5dca5ee611e1e0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008911"
---
# <a name="persistence-in-orchestrations"></a><span data-ttu-id="539ca-102">協調流程持續性</span><span class="sxs-lookup"><span data-stu-id="539ca-102">Persistence in Orchestrations</span></span>
<span data-ttu-id="539ca-103">協調流程引擎會在不同的持續點儲存協調流程執行個體的整個狀態，讓協調流程執行個體能夠解除凍結。</span><span class="sxs-lookup"><span data-stu-id="539ca-103">The orchestration engine saves the entire state of an orchestration instance at various persistence points to allow rehydration of the orchestration instance.</span></span> <span data-ttu-id="539ca-104">除了訊息和變數以外，狀態還包括可能在協調流程中使用的任何 .NET 架構元件。</span><span class="sxs-lookup"><span data-stu-id="539ca-104">The state includes any .NET-based components that may be used in the orchestration, in addition to messages and variables.</span></span> <span data-ttu-id="539ca-105">引擎將狀態存放在下列持續點：</span><span class="sxs-lookup"><span data-stu-id="539ca-105">The engine stores state at the following persistence points:</span></span>  
  
- <span data-ttu-id="539ca-106">交易式範圍的結尾 (不可部分完成或長執行)。</span><span class="sxs-lookup"><span data-stu-id="539ca-106">End of a transactional scope (atomic or long running)</span></span>  
  
- <span data-ttu-id="539ca-107">在偵錯中斷點</span><span class="sxs-lookup"><span data-stu-id="539ca-107">At debugging breakpoints</span></span>  
  
- <span data-ttu-id="539ca-108">在透過「啟動協調流程」圖形執行其他協調流程時</span><span class="sxs-lookup"><span data-stu-id="539ca-108">At the execution of other orchestrations through the Start Orchestration shape</span></span>  
  
- <span data-ttu-id="539ca-109">在「傳送」圖形 (不可部分完成的交易除外)</span><span class="sxs-lookup"><span data-stu-id="539ca-109">At the Send shape (except in an atomic transaction)</span></span>  
  
- <span data-ttu-id="539ca-110">當協調流程執行個體被擱置時</span><span class="sxs-lookup"><span data-stu-id="539ca-110">When an Orchestration Instance is suspended</span></span>  
  
- <span data-ttu-id="539ca-111">當系統在控制的情況下關機時</span><span class="sxs-lookup"><span data-stu-id="539ca-111">When the system shutdowns in a controlled manner</span></span>  
  
- <span data-ttu-id="539ca-112">當引擎決定要凍結時</span><span class="sxs-lookup"><span data-stu-id="539ca-112">When the engine determines it wants to dehydrate</span></span>  
  
- <span data-ttu-id="539ca-113">當協調流程執行個體完成時</span><span class="sxs-lookup"><span data-stu-id="539ca-113">When an orchestration instance is finished</span></span>  
  
  <span data-ttu-id="539ca-114">引擎會最佳化持續點的數目，因為這些會耗費許多資源，在處理大的訊息大小時尤其如此。</span><span class="sxs-lookup"><span data-stu-id="539ca-114">The engine optimizes the number of persistence points as they are expensive, especially when dealing with large message sizes.</span></span> <span data-ttu-id="539ca-115">如以下兩個協調流程執行個體所示，在將「傳送圖形」置於不可部分完成範圍的協調流程中，引擎會決定在交易式範圍結尾與協調流程結尾之間具有單一的持續點。</span><span class="sxs-lookup"><span data-stu-id="539ca-115">As shown in the two orchestration instances below, in the orchestration with the Send Shapes in an atomic scope, the engine determines a single persistence point between the end of the transaction scope and the end of the orchestration.</span></span> <span data-ttu-id="539ca-116">在另一個協調流程中，則會有兩個持續點，一個用於第一個「傳送」圖形，第二個則用於「傳送」圖形加上協調流程的結尾。</span><span class="sxs-lookup"><span data-stu-id="539ca-116">In the other orchestration, there will be two persistence points, one for the first Send shape and the second for the Send shape plus end of the orchestration.</span></span>  
  
  <span data-ttu-id="539ca-117">**協調流程持續性**</span><span class="sxs-lookup"><span data-stu-id="539ca-117">**Orchestration persistence**</span></span>  
  
  <span data-ttu-id="539ca-118">![協調流程持續性](../core/media/bts-trans-orch-fig2.gif "BTS_Trans_Orch_Fig2")</span><span class="sxs-lookup"><span data-stu-id="539ca-118">![Orchestration persistence](../core/media/bts-trans-orch-fig2.gif "BTS_Trans_Orch_Fig2")</span></span>  
  
  <span data-ttu-id="539ca-119">您在協調流程中使用的任何 .NET 架構物件，除非是在不可部分完成範圍中叫用，或是物件沒有狀態而且只能透過靜態方法叫用，否則無論是直接或是間接，都必須標記為可序列化。</span><span class="sxs-lookup"><span data-stu-id="539ca-119">Any .NET-based objects you use in orchestrations, either directly or indirectly, must be marked as serializable unless they are invoked in atomic scopes, or if the objects are stateless and are invoked only through static methods.</span></span> <span data-ttu-id="539ca-120">**System.Xml.XmlDocument**是特殊案例，而且不需要標記為可序列化，不論針對某範圍的交易屬性。</span><span class="sxs-lookup"><span data-stu-id="539ca-120">**System.Xml.XmlDocument** is a special case and does not need to be marked as serializable regardless of the transaction property for a scope.</span></span>  
  
  <span data-ttu-id="539ca-121">如何執行特殊處理， **System.Xml.XmlDocument**運作：</span><span class="sxs-lookup"><span data-stu-id="539ca-121">How does the special handling for **System.Xml.XmlDocument** work:</span></span>  
  
  <span data-ttu-id="539ca-122">當使用者定義變數**X**型別的**T**，其中**T**是**System.Xml.XmlDocument**或衍生自類別**System.Xml.XmlDocument**則會將編譯器**X**為可序列化的物件。</span><span class="sxs-lookup"><span data-stu-id="539ca-122">When the user defines a variable **X** of type **T**, where **T** is **System.Xml.XmlDocument** or a class derived from **System.Xml.XmlDocument** then the compiler will treat **X** as a serializable object.</span></span>  
  
  <span data-ttu-id="539ca-123">當序列化**X**，執行階段會保留下列幾項資訊: （a） 的實際型別**Tr**物件的**X**指 （b) **OuterXml**文件的字串。</span><span class="sxs-lookup"><span data-stu-id="539ca-123">When serializing **X**, the runtime will keep the following pieces of information: (a) the actual type **Tr** of the object **X** is referring to (b) the **OuterXml** string of the document.</span></span>  
  
  <span data-ttu-id="539ca-124">在還原序列化**X**，執行階段會建立的執行個體**Tr** （這假設不採用任何參數的建構函式），並將呼叫**LoadXml**提供將儲存的執行個體**OuterXml。X**則會設為指向新建立的執行個體**Tr**。</span><span class="sxs-lookup"><span data-stu-id="539ca-124">When de-serializing **X**, the runtime will create an instance of **Tr** (this assumes a constructor that does not take any parameters) and will call **LoadXml** providing the instance with the saved **OuterXml.  X** will then be set to point to the newly created instance of **Tr**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="539ca-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="539ca-125">See Also</span></span>  
 [<span data-ttu-id="539ca-126">Transactions</span><span class="sxs-lookup"><span data-stu-id="539ca-126">Transactions</span></span>](../core/transactions.md)