---
title: "如何使用選取成品類型對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Select Artifact Type dialog box
- artifacts, Select Artifact Type dialog box
- Orchestration Designer, items
ms.assetid: f0f767f1-4130-4ff0-a898-a089343ee71f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3027971059d99a921bd743ff28aca1617c5d628d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-select-artifact-type-dialog-box"></a><span data-ttu-id="03ae3-102">如何使用選取成品類型對話方塊</span><span class="sxs-lookup"><span data-stu-id="03ae3-102">How to Use the Select Artifact Type Dialog Box</span></span>
<span data-ttu-id="03ae3-103">*項目*用來設定協調流程設計師 」 的協調流程的項目。</span><span class="sxs-lookup"><span data-stu-id="03ae3-103">An *item* is used to configure elements of an orchestration in Orchestration Designer.</span></span> <span data-ttu-id="03ae3-104">項目 (Item) 的範例包括結構描述、對應、管線、連接埠類型以及多部分訊息類型等。</span><span class="sxs-lookup"><span data-stu-id="03ae3-104">Examples of items are schemas, maps, pipelines, port types, and multi-part message types.</span></span> <span data-ttu-id="03ae3-105">在開發協調流程及其組成部分 (例如，連接埠圖形、轉換圖形和訊息) 時，所需參考的項目可能不在目前的協調流程中，但在目前的專案或在其他已編譯入 BizTalk Server 組件的其他專案中。</span><span class="sxs-lookup"><span data-stu-id="03ae3-105">When you develop an orchestration and its constituent parts such as port shapes, transform shapes, and messages, you may need to refer to items that do not reside in the current orchestration, but are in the current project or another project that has been compiled into a BizTalk Server assembly.</span></span> <span data-ttu-id="03ae3-106">您使用**選取成品類型**對話方塊，即可尋找並設定協調流程內的項目時，然後指定項目。</span><span class="sxs-lookup"><span data-stu-id="03ae3-106">You use the **Select Artifact Type** dialog box to locate and then specify items when configuring an element within an orchestration.</span></span>  
  
 <span data-ttu-id="03ae3-107">**選取成品類型** 對話方塊可從許多協調流程設計師中的位置。</span><span class="sxs-lookup"><span data-stu-id="03ae3-107">The **Select Artifact Type** dialog box is available from many locations in Orchestration Designer.</span></span> <span data-ttu-id="03ae3-108">您可以選取\<從參考組件選取 > 下拉式清單中，會顯示組態選項，按一下此文字會開啟**選取成品類型** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="03ae3-108">You can select \<Select from referenced assembly> in a drop-down list that displays configuration options; clicking this text opens the **Select Artifact Type** dialog box.</span></span>  
  
 <span data-ttu-id="03ae3-109">在選取項目 (Item) 之前，必須先選取想要設定的項目 (Element)。</span><span class="sxs-lookup"><span data-stu-id="03ae3-109">Before you can select an item, you must first select the element you want to configure.</span></span>  
  
 <span data-ttu-id="03ae3-110">您可以使用**選取成品類型**用於下列特定用途的對話方塊：</span><span class="sxs-lookup"><span data-stu-id="03ae3-110">You can use the **Select Artifact Type** dialog box for the following specific purposes:</span></span>  
  
|<span data-ttu-id="03ae3-111">動作</span><span class="sxs-lookup"><span data-stu-id="03ae3-111">Action</span></span>|<span data-ttu-id="03ae3-112">目的</span><span class="sxs-lookup"><span data-stu-id="03ae3-112">Purpose</span></span>|  
|------------|-------------|  
|<span data-ttu-id="03ae3-113">選取管線</span><span class="sxs-lookup"><span data-stu-id="03ae3-113">Select a pipeline</span></span>|<span data-ttu-id="03ae3-114">在設定直接 (早期) 繫結的連接埠時，選取管線屬性的管線。</span><span class="sxs-lookup"><span data-stu-id="03ae3-114">Select a pipeline for the pipeline property when configuring a port for direct (early) binding.</span></span>|  
|<span data-ttu-id="03ae3-115">選取對應</span><span class="sxs-lookup"><span data-stu-id="03ae3-115">Select a map</span></span>|<span data-ttu-id="03ae3-116">選取要用於對應**轉換**圖形。</span><span class="sxs-lookup"><span data-stu-id="03ae3-116">Select a map to use with a **Transform** shape.</span></span>|  
|<span data-ttu-id="03ae3-117">選取結構描述</span><span class="sxs-lookup"><span data-stu-id="03ae3-117">Select a schema</span></span>|<span data-ttu-id="03ae3-118">在建立多部分訊息類型時選取專案中的結構描述。</span><span class="sxs-lookup"><span data-stu-id="03ae3-118">Select schemas in the project when creating multi-part message types.</span></span>|  
|<span data-ttu-id="03ae3-119">選取連接埠類型</span><span class="sxs-lookup"><span data-stu-id="03ae3-119">Select a port type</span></span>|<span data-ttu-id="03ae3-120">在建立連接埠時參考現有的連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="03ae3-120">Refer to existing port types when creating a port.</span></span>|  
|<span data-ttu-id="03ae3-121">選取多部分訊息類型</span><span class="sxs-lookup"><span data-stu-id="03ae3-121">Select a multi-part message type</span></span>|<span data-ttu-id="03ae3-122">在建立訊息時參考現有的多部分類型。</span><span class="sxs-lookup"><span data-stu-id="03ae3-122">Refer to existing multipart types when creating messages.</span></span>|  
|<span data-ttu-id="03ae3-123">選取 .NET 類型</span><span class="sxs-lookup"><span data-stu-id="03ae3-123">Select a .NET type</span></span>|<span data-ttu-id="03ae3-124">在建立變數或訊息時參考現有的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="03ae3-124">Refer to existing .NET types when creating variables or messages.</span></span>|  
  
 <span data-ttu-id="03ae3-125">**參考窗格**</span><span class="sxs-lookup"><span data-stu-id="03ae3-125">**Reference pane**</span></span>  
  
 <span data-ttu-id="03ae3-126">參考窗格**選取成品類型**對話方塊會顯示參考目前專案中，以及其他可用的組件中。</span><span class="sxs-lookup"><span data-stu-id="03ae3-126">The reference pane of the **Select Artifact Type** dialog box displays references in the current project and in other available assemblies.</span></span> <span data-ttu-id="03ae3-127">若要選取此窗格中的參考，請在該參考上按一下。</span><span class="sxs-lookup"><span data-stu-id="03ae3-127">To select a reference in this pane, click it.</span></span> <span data-ttu-id="03ae3-128">若要展開此窗格中的容器 (例如**組件**容器)，按一下旁邊的加號 （+）。</span><span class="sxs-lookup"><span data-stu-id="03ae3-128">To expand a container in this pane (such as the **Assemblies** container), click the plus sign (+) beside it.</span></span>  
  
 <span data-ttu-id="03ae3-129">**項目 窗格**</span><span class="sxs-lookup"><span data-stu-id="03ae3-129">**Item pane**</span></span>  
  
 <span data-ttu-id="03ae3-130">項目窗格**選取成品類型**對話方塊會顯示目前在 [參考] 窗格中選取參考中包含的項目。</span><span class="sxs-lookup"><span data-stu-id="03ae3-130">The item pane of the **Select Artifact Type** dialog box displays the items contained in the reference currently selected in the reference pane.</span></span> <span data-ttu-id="03ae3-131">項目 窗格有兩個資料行，**項目**和**限定名稱**，其中顯示目前參考中的項目的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="03ae3-131">The item pane has two columns, **Item** and **Qualified Name**, which display information about the items in the current reference.</span></span>  
  
### <a name="to-use-the-select-artifact-type-dialog-box"></a><span data-ttu-id="03ae3-132">使用選取成品類型對話方塊</span><span class="sxs-lookup"><span data-stu-id="03ae3-132">To use the Select Artifact Type dialog box</span></span>  
  
1.  <span data-ttu-id="03ae3-133">展開**參考**的左窗格中的節點。</span><span class="sxs-lookup"><span data-stu-id="03ae3-133">Expand the **References** node in the left pane.</span></span> <span data-ttu-id="03ae3-134">此窗格會顯示可用的專案和組件。</span><span class="sxs-lookup"><span data-stu-id="03ae3-134">The pane displays available projects and assemblies.</span></span>  
  
2.  <span data-ttu-id="03ae3-135">展開**組件**節點。</span><span class="sxs-lookup"><span data-stu-id="03ae3-135">Expand the **Assemblies** node.</span></span> <span data-ttu-id="03ae3-136">將列出一或多個組件，例如 SYSTEM.DLL 和 MICROSOFT.BIZTALK.PIPELINES.DLL。</span><span class="sxs-lookup"><span data-stu-id="03ae3-136">One or more assemblies are listed, such as SYSTEM.DLL and MICROSOFT.BIZTALK.PIPELINES.DLL.</span></span>  
  
3.  <span data-ttu-id="03ae3-137">按一下組件。</span><span class="sxs-lookup"><span data-stu-id="03ae3-137">Click an assembly.</span></span> <span data-ttu-id="03ae3-138">如果組件包含項目，則這些項目會顯示在右窗格中。</span><span class="sxs-lookup"><span data-stu-id="03ae3-138">If the assembly contains items, they are displayed in the right pane.</span></span> <span data-ttu-id="03ae3-139">項目的完整格式名稱會顯示在右窗格的右方欄位中。</span><span class="sxs-lookup"><span data-stu-id="03ae3-139">The qualified name of an item is displayed in the right column of the right pane.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="03ae3-140">如果目前的專案含有項目，可以按一下該專案來檢視其項目並進行選擇。</span><span class="sxs-lookup"><span data-stu-id="03ae3-140">If the current project contains items, you can click it to view its items and select one.</span></span>  
  
4.  <span data-ttu-id="03ae3-141">在右窗格中選取的項目，按一下它，然後按一下 [**確定**結束**選取成品類型**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="03ae3-141">To select an item in the right pane, click it and then click **OK** to exit the **Select Artifact Type** dialog box.</span></span> <span data-ttu-id="03ae3-142">這會將該項目 (Item) 指定為已選取項目 (Element) 的類型。</span><span class="sxs-lookup"><span data-stu-id="03ae3-142">This assigns that item as the type for the selected element.</span></span> <span data-ttu-id="03ae3-143">若要關閉**選取成品類型**對話方塊，而不選取，然後指派一個項目，按一下**取消**。</span><span class="sxs-lookup"><span data-stu-id="03ae3-143">To close the **Select Artifact Type** dialog box without selecting and assigning an item, click **Cancel**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03ae3-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03ae3-144">See Also</span></span>  
 <span data-ttu-id="03ae3-145">[協調流程圖形](../core/orchestration-shapes.md) </span><span class="sxs-lookup"><span data-stu-id="03ae3-145">[Orchestration Shapes](../core/orchestration-shapes.md) </span></span>  
 <span data-ttu-id="03ae3-146">[如何新增圖形至協調流程](../core/how-to-add-shapes-to-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="03ae3-146">[How to Add Shapes to Orchestrations](../core/how-to-add-shapes-to-orchestrations.md) </span></span>  
 [<span data-ttu-id="03ae3-147">如何新增參數至協調流程</span><span class="sxs-lookup"><span data-stu-id="03ae3-147">How to Add Parameters to Orchestrations</span></span>](../core/how-to-add-parameters-to-orchestrations.md)