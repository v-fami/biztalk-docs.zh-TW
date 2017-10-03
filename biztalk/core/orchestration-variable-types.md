---
title: "協調流程變數類型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: orchestrations, variables
ms.assetid: 34990be2-35b6-40ec-b107-42a1c7b45aca
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f388cf112a84d1e6ace00d3930cd6d815d728d89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="orchestration-variable-types"></a><span data-ttu-id="39df9-102">協調流程變數類型</span><span class="sxs-lookup"><span data-stu-id="39df9-102">Orchestration Variable Types</span></span>
<span data-ttu-id="39df9-103">您可以宣告下列預先定義型別的變數：</span><span class="sxs-lookup"><span data-stu-id="39df9-103">You can declare variables of the following predefined types:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="39df9-104">boolean</span><span class="sxs-lookup"><span data-stu-id="39df9-104">boolean</span></span>|<span data-ttu-id="39df9-105">byte</span><span class="sxs-lookup"><span data-stu-id="39df9-105">byte</span></span>|<span data-ttu-id="39df9-106">char</span><span class="sxs-lookup"><span data-stu-id="39df9-106">char</span></span>|<span data-ttu-id="39df9-107">datetime</span><span class="sxs-lookup"><span data-stu-id="39df9-107">datetime</span></span>|  
|<span data-ttu-id="39df9-108">decimal</span><span class="sxs-lookup"><span data-stu-id="39df9-108">decimal</span></span>|<span data-ttu-id="39df9-109">double</span><span class="sxs-lookup"><span data-stu-id="39df9-109">double</span></span>|<span data-ttu-id="39df9-110">int16</span><span class="sxs-lookup"><span data-stu-id="39df9-110">int16</span></span>|<span data-ttu-id="39df9-111">int32</span><span class="sxs-lookup"><span data-stu-id="39df9-111">int32</span></span>|  
|<span data-ttu-id="39df9-112">int64</span><span class="sxs-lookup"><span data-stu-id="39df9-112">int64</span></span>|<span data-ttu-id="39df9-113">long</span><span class="sxs-lookup"><span data-stu-id="39df9-113">long</span></span>|<span data-ttu-id="39df9-114">sbyte</span><span class="sxs-lookup"><span data-stu-id="39df9-114">sbyte</span></span>|<span data-ttu-id="39df9-115">single</span><span class="sxs-lookup"><span data-stu-id="39df9-115">single</span></span>|  
|<span data-ttu-id="39df9-116">string</span><span class="sxs-lookup"><span data-stu-id="39df9-116">string</span></span>|<span data-ttu-id="39df9-117">timespan</span><span class="sxs-lookup"><span data-stu-id="39df9-117">timespan</span></span>|<span data-ttu-id="39df9-118">uint16</span><span class="sxs-lookup"><span data-stu-id="39df9-118">uint16</span></span>|<span data-ttu-id="39df9-119">uint32</span><span class="sxs-lookup"><span data-stu-id="39df9-119">uint32</span></span>|  
|<span data-ttu-id="39df9-120">uint64</span><span class="sxs-lookup"><span data-stu-id="39df9-120">uint64</span></span>||||  
  
 <span data-ttu-id="39df9-121">您也可以宣告在專案中參考之任何 NET 架構型別的變數。</span><span class="sxs-lookup"><span data-stu-id="39df9-121">You can also declare variables of any .NET-based types that are referenced in your project.</span></span>  
  
## <a name="considerations-for-declare-orchestration-variables"></a><span data-ttu-id="39df9-122">宣告協調流程變數的考量</span><span class="sxs-lookup"><span data-stu-id="39df9-122">Considerations for Declare Orchestration Variables</span></span>  
 <span data-ttu-id="39df9-123">在宣告協調流程變數時，請考慮下列項目：</span><span class="sxs-lookup"><span data-stu-id="39df9-123">When declare orchestration variables, consider the following:</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="39df9-124"> 對某些以內容為基礎的路由案例支援多值內容屬性，不過您無法在協調流程中使用這類屬性。</span><span class="sxs-lookup"><span data-stu-id="39df9-124"> supports multivalued context properties for certain content-based routing scenarios, but you cannot use such properties in orchestrations.</span></span>  
  
-   <span data-ttu-id="39df9-125">為了支援協調流程的擱置和解除凍結，所有的協調流程變數都必須能夠使其狀態持續。</span><span class="sxs-lookup"><span data-stu-id="39df9-125">In order to support suspension and re-hydration of orchestrations, all orchestration variables must be capable of having their state persisted.</span></span>  <span data-ttu-id="39df9-126">通常，這點會由變數型別或類別的可序列化或可資料流化來達成。</span><span class="sxs-lookup"><span data-stu-id="39df9-126">Typically, this is accomplished by the variable's type or class being serializable or streamable.</span></span>  
  
-   <span data-ttu-id="39df9-127">這些 .NET 架構的型別 (類別) 必須是可序列化的類別。</span><span class="sxs-lookup"><span data-stu-id="39df9-127">These .NET-based types (classes) must be serializable classes.</span></span>  <span data-ttu-id="39df9-128">它們可能會以 "[Serializable]” 屬性宣告，或是明確實作 ISerializable .NET 介面 (在 System.Runtime.Serialization 命名空間中)，以便進行實作。</span><span class="sxs-lookup"><span data-stu-id="39df9-128">They may either implement this by being declared with the "[Serializable]” attribute or by explicitly implementing the ISerializable .NET interface (in the System.Runtime.Serialization namespace).</span></span>  
  
-   <span data-ttu-id="39df9-129">如果 .NET 架構型別實際上是基礎 COM 元件的執行階段可呼叫包裝函式 (RCW)，則該 COM 元件就必須實作 RCW 所需要的介面，以便成為可序列化的 .NET 類別 (例如，IpersistStream、IPersistStreamInit)。</span><span class="sxs-lookup"><span data-stu-id="39df9-129">If the .NET-based type is actually a runtime callable wrapper (RCW) of an underlying COM component, then that COM component must implement the interface(s) required for the RCW to be a serializable .NET class (e.g. IPersistStream, IPersistStreamInit).</span></span>  
  
-   <span data-ttu-id="39df9-130">由於任何 .NET 架構 (或基礎 COM) 型別都是在協調流程的流程內執行，這些型別的方法都不能延遲協調流程的執行 (例如，透過資源的爭用等等)。</span><span class="sxs-lookup"><span data-stu-id="39df9-130">Because any .NET-based (or underlying COM) types are executing within the flow of an orchestration, methods in these types must not delay execution of the orchestration (e.g. through contention for resources, etc.).</span></span>  <span data-ttu-id="39df9-131">而且這些型別實作的任何資源消耗，都會影響到呼叫之協調流程在其中執行的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="39df9-131">And any consumption of resources by these type implementations will affect the host instance in which the calling orchestration runs.</span></span>