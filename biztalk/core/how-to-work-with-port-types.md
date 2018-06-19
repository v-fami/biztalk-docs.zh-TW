---
title: 如何使用連接埠類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting, port types
- port types, deleting
- port types, Web
- port types, request-response
- orchestrations, ports
- port types, modifier
- port types
- ports, port types
- port types, one-way
ms.assetid: 78ac731e-c330-4888-a9ee-10523fef8ed0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e3b4307cb9d48679ae1b90f7e02dd0288ec2957
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257126"
---
# <a name="how-to-work-with-port-types"></a><span data-ttu-id="8edb2-102">如何使用連接埠類型</span><span class="sxs-lookup"><span data-stu-id="8edb2-102">How to Work with Port Types</span></span>
<span data-ttu-id="8edb2-103">連接埠類型包含通訊模式、一組作業 (要求或回應)，以及可在其上運作這些作業的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="8edb2-103">A port type consists of a communication pattern, a set of operations (requests or responses), and the message types that those operations can work on.</span></span> <span data-ttu-id="8edb2-104">模式可以是單向或要求-回應 (雙向)，且在該連接埠類型上定義的所有作業必須使用相同模式。</span><span class="sxs-lookup"><span data-stu-id="8edb2-104">The pattern can be either one-way or request-response (two-way), and all operations defined on that port type must use the same pattern.</span></span> <span data-ttu-id="8edb2-105">請注意，連接埠類型的方向不特定：方向是在個別連接埠上指定的。</span><span class="sxs-lookup"><span data-stu-id="8edb2-105">Note that port types are direction-agnostic: direction is specified on individual ports.</span></span>  
  
 <span data-ttu-id="8edb2-106">連接埠類型的範圍由所定義**型別修飾詞**屬性。</span><span class="sxs-lookup"><span data-stu-id="8edb2-106">The scope of a port type is defined by the **Type Modifier** property.</span></span> <span data-ttu-id="8edb2-107">連接埠類型可以是公用、專用或內部。</span><span class="sxs-lookup"><span data-stu-id="8edb2-107">A port type can be public, private, or internal.</span></span> <span data-ttu-id="8edb2-108">若為公用，則與協調流程互動的所有使用者皆可看到。</span><span class="sxs-lookup"><span data-stu-id="8edb2-108">If it is public, it is visible to anyone interacting with the orchestration.</span></span> <span data-ttu-id="8edb2-109">若為專用，則在相同專案和命名空間中的其他協調流程可以看到。</span><span class="sxs-lookup"><span data-stu-id="8edb2-109">If it is private, it is visible to other orchestrations within the same project and namespace.</span></span> <span data-ttu-id="8edb2-110">若為內部，則只有在專案內可以看到連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="8edb2-110">If it is internal, the port type is visible only within the project.</span></span> <span data-ttu-id="8edb2-111">由於連接埠類型定義包括訊息類型，因此訊息類型的範圍必須包含使用它的任何連接埠類型之範圍。</span><span class="sxs-lookup"><span data-stu-id="8edb2-111">Since a port type definition includes message types, the scope of the message type must encompass that of any port type that uses it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8edb2-112">連接埠類型可套用至任何數量的連接埠。</span><span class="sxs-lookup"><span data-stu-id="8edb2-112">A port type can be applied to any number of ports.</span></span> <span data-ttu-id="8edb2-113">您可以將連接埠視為連接埠類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8edb2-113">You can think of a port as an instance of a port type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8edb2-114">連接埠類型基本上不具有通訊方向；您要在個別連接埠上設定方向。</span><span class="sxs-lookup"><span data-stu-id="8edb2-114">A port type does not inherently have a communication direction; you set direction on individual ports.</span></span>  
  
### <a name="to-add-a-request-response-port-type"></a><span data-ttu-id="8edb2-115">新增要求-回應連接埠類型</span><span class="sxs-lookup"><span data-stu-id="8edb2-115">To add a request-response port type</span></span>  
  
1.  <span data-ttu-id="8edb2-116">在協調流程檢視] 視窗中，以滑鼠右鍵按一下**連接埠類型**，然後按一下 [**新增要求-回應連接埠類型**。</span><span class="sxs-lookup"><span data-stu-id="8edb2-116">In the Orchestration View window, right-click **Port Types** and then click **New Request-response Port Type**.</span></span>  
  
     <span data-ttu-id="8edb2-117">**連接埠類型**節點，則會展開摺疊，並使用一個預設作業新增新的要求-回應連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="8edb2-117">The **Port Types** node expands, if collapsed, and a new request-response port type is added with one default operation.</span></span>  
  
2.  <span data-ttu-id="8edb2-118">指定連接埠類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="8edb2-118">Specify a name for the port type.</span></span>  
  
3.  <span data-ttu-id="8edb2-119">定義一或多個連接埠作業。</span><span class="sxs-lookup"><span data-stu-id="8edb2-119">Define one or more port operations.</span></span>  
  
     <span data-ttu-id="8edb2-120">您可以命名您的連接埠作業，不過，當您從其他專案選取連接埠作業時，只會看到它們顯示為「要求」和「回應」。</span><span class="sxs-lookup"><span data-stu-id="8edb2-120">You can name your port operations, but when you are selecting them from another project, you will see them only as "Request" and "Response."</span></span> <span data-ttu-id="8edb2-121">若您從其他專案選取連接埠作業，請確認其訊息類型正確。</span><span class="sxs-lookup"><span data-stu-id="8edb2-121">If you select a port operation from another project, verify that it has the correct message type.</span></span>  
  
### <a name="to-add-a-one-way-port-type"></a><span data-ttu-id="8edb2-122">新增單向連接埠類型</span><span class="sxs-lookup"><span data-stu-id="8edb2-122">To add a one-way port type</span></span>  
  
1.  <span data-ttu-id="8edb2-123">在協調流程檢視] 視窗中，以滑鼠右鍵按一下**連接埠類型**，然後按一下 [**新單向連接埠類型**。</span><span class="sxs-lookup"><span data-stu-id="8edb2-123">In the Orchestration View window, right-click **Port Types** and then click **New One-way Port Type**.</span></span>  
  
     <span data-ttu-id="8edb2-124">**連接埠類型**節點，則會展開摺疊，並使用一個預設作業新增新的單向連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="8edb2-124">The **Port Types** node expands, if collapsed, and a new one-way port type is added with one default operation.</span></span>  
  
2.  <span data-ttu-id="8edb2-125">指定連接埠類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="8edb2-125">Specify a name for the port type.</span></span>  
  
3.  <span data-ttu-id="8edb2-126">定義一或多個連接埠作業。</span><span class="sxs-lookup"><span data-stu-id="8edb2-126">Define one or more port operations.</span></span>  
  
### <a name="to-add-a-web-port-type"></a><span data-ttu-id="8edb2-127">新增 Web 連接埠類型</span><span class="sxs-lookup"><span data-stu-id="8edb2-127">To add a Web port type</span></span>  
  
-   <span data-ttu-id="8edb2-128">新增專案參考至包含 Web 服務的 Proxy 類別之組件。</span><span class="sxs-lookup"><span data-stu-id="8edb2-128">Add a project reference to an assembly containing a proxy class for a Web service.</span></span> <span data-ttu-id="8edb2-129">如需詳細資訊，請參閱[建立 Web 連接埠](../core/creating-web-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="8edb2-129">For more information, see [Creating Web Ports](../core/creating-web-ports.md).</span></span>  
  
### <a name="to-remove-a-port-type"></a><span data-ttu-id="8edb2-130">移除連接埠類型</span><span class="sxs-lookup"><span data-stu-id="8edb2-130">To remove a port type</span></span>  
  
-   <span data-ttu-id="8edb2-131">在協調流程檢視] 視窗中，以滑鼠右鍵按一下要刪除，然後按一下 [連接埠類型**刪除**。</span><span class="sxs-lookup"><span data-stu-id="8edb2-131">In the Orchestration View window, right-click the port type to delete, and then click **Delete**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8edb2-132">若連接埠類型正在使用中，刪除該連接埠類型會影響設定為使用它的所有連接埠之組態。</span><span class="sxs-lookup"><span data-stu-id="8edb2-132">If the port type is in use, deleting it will impact the configuration of any ports that are configured to use it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8edb2-133">顯示為唯讀的項目定義在另一個協調流程中。</span><span class="sxs-lookup"><span data-stu-id="8edb2-133">Items that appear as read-only are defined in another orchestration.</span></span>  
  
### <a name="to-set-the-type-modifier-for-a-port-type"></a><span data-ttu-id="8edb2-134">設定連接埠類型的型別修飾詞</span><span class="sxs-lookup"><span data-stu-id="8edb2-134">To set the type modifier for a port type</span></span>  
  
-   <span data-ttu-id="8edb2-135">在 [屬性] 視窗中，設定以下屬性：</span><span class="sxs-lookup"><span data-stu-id="8edb2-135">In the Properties window, set the following property:</span></span>  
  
    |<span data-ttu-id="8edb2-136">屬性</span><span class="sxs-lookup"><span data-stu-id="8edb2-136">Property</span></span>|<span data-ttu-id="8edb2-137">Description</span><span class="sxs-lookup"><span data-stu-id="8edb2-137">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="8edb2-138">型別修飾詞</span><span class="sxs-lookup"><span data-stu-id="8edb2-138">Type Modifier</span></span>|<span data-ttu-id="8edb2-139">決定連接埠類型的範圍：</span><span class="sxs-lookup"><span data-stu-id="8edb2-139">Determines the scope of the port type:</span></span><br /><br /> <span data-ttu-id="8edb2-140">專用—存取此連接埠類型限於包含的模組。</span><span class="sxs-lookup"><span data-stu-id="8edb2-140">Private—Access to this port type is limited to the containing module.</span></span><br /><br /> <span data-ttu-id="8edb2-141">公用—存取此連接埠類型不受任何限制。</span><span class="sxs-lookup"><span data-stu-id="8edb2-141">Public—Access to this port type is not limited.</span></span><br /><br /> <span data-ttu-id="8edb2-142">內部—存取此連接埠類型限於相同專案中的模組。</span><span class="sxs-lookup"><span data-stu-id="8edb2-142">Internal—Access to this port type is limited to modules within the same project.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8edb2-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8edb2-143">See Also</span></span>  
 <span data-ttu-id="8edb2-144">[通訊模式](../core/communication-pattern.md) </span><span class="sxs-lookup"><span data-stu-id="8edb2-144">[Communication Pattern](../core/communication-pattern.md) </span></span>  
 <span data-ttu-id="8edb2-145">[如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="8edb2-145">[How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md) </span></span>  
 [<span data-ttu-id="8edb2-146">協調流程中使用連接埠</span><span class="sxs-lookup"><span data-stu-id="8edb2-146">Using Ports in Orchestrations</span></span>](../core/using-ports-in-orchestrations.md)