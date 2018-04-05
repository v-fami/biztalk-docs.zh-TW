---
title: 如何讀取管線元件屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components, properties
ms.assetid: 10b1c59c-7ba4-453f-9aaa-1ce9ecf31fac
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19a6ccbcbe7588a0a75b4dbe6bf821a19fab965c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-read-pipeline-component-properties"></a><span data-ttu-id="43311-102">如何讀取管線元件屬性</span><span class="sxs-lookup"><span data-stu-id="43311-102">How to Read Pipeline Component Properties</span></span>
<span data-ttu-id="43311-103">元件的 [屬性] 視窗包含兩個部分：一般屬性和元件屬性。</span><span class="sxs-lookup"><span data-stu-id="43311-103">The Properties window contains two sections for components: general properties and component properties.</span></span> <span data-ttu-id="43311-104">一般屬性為所有元件通用，不過，其值則依元件的不同各異。</span><span class="sxs-lookup"><span data-stu-id="43311-104">General properties are common to all components, though their values change between components.</span></span>  
  
### <a name="to-read-the-general-properties-for-a-pipeline-component"></a><span data-ttu-id="43311-105">讀取管線元件的一般屬性</span><span class="sxs-lookup"><span data-stu-id="43311-105">To read the general properties for a pipeline component</span></span>  
  
1.  <span data-ttu-id="43311-106">將管線元件拖曳至管線的某個階段中，或選取管線中已經存在的元件。</span><span class="sxs-lookup"><span data-stu-id="43311-106">Drag the pipeline component into a stage of the pipeline, or select a component if it already exists in the pipeline.</span></span>  
  
2.  <span data-ttu-id="43311-107">在 [屬性] 視窗中**一般**區段中，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="43311-107">In the Properties window, in the **General** section, do the following.</span></span>  
  
    |<span data-ttu-id="43311-108">使用</span><span class="sxs-lookup"><span data-stu-id="43311-108">Use this</span></span>|<span data-ttu-id="43311-109">動作</span><span class="sxs-lookup"><span data-stu-id="43311-109">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="43311-110">**名稱**</span><span class="sxs-lookup"><span data-stu-id="43311-110">**Name**</span></span>|<span data-ttu-id="43311-111">指示元件名稱。</span><span class="sxs-lookup"><span data-stu-id="43311-111">Indicates the component name.</span></span>|  
    |<span data-ttu-id="43311-112">**組件**</span><span class="sxs-lookup"><span data-stu-id="43311-112">**Assembly**</span></span>|<span data-ttu-id="43311-113">指示元件的組件與關聯的 .NET 資訊。</span><span class="sxs-lookup"><span data-stu-id="43311-113">Indicates the assembly and associated .NET information for the component.</span></span>|  
    |<span data-ttu-id="43311-114">**說明**</span><span class="sxs-lookup"><span data-stu-id="43311-114">**Description**</span></span>|<span data-ttu-id="43311-115">指示管線元件的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="43311-115">Indicates the friendly name of the pipeline component.</span></span>|  
    |<span data-ttu-id="43311-116">**受管理**</span><span class="sxs-lookup"><span data-stu-id="43311-116">**Managed**</span></span>|<span data-ttu-id="43311-117">指示管線元件是否受管理。</span><span class="sxs-lookup"><span data-stu-id="43311-117">Indicates whether the pipeline component is managed.</span></span> <span data-ttu-id="43311-118">**[是]**如果元件為.NET 受管理的元件。**否**如果管線元件是 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="43311-118">**Yes** if the component is a .NET managed component; **No** if the pipeline component is a COM component.</span></span>|  
    |<span data-ttu-id="43311-119">**路徑**</span><span class="sxs-lookup"><span data-stu-id="43311-119">**Path**</span></span>|<span data-ttu-id="43311-120">指示 .NET 元件的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="43311-120">Indicates the fully qualified path to the .NET component.</span></span>|  
    |<span data-ttu-id="43311-121">**型別**</span><span class="sxs-lookup"><span data-stu-id="43311-121">**Type**</span></span>|<span data-ttu-id="43311-122">指示元件的元件類型、組件以及關聯的 .NET 資訊。</span><span class="sxs-lookup"><span data-stu-id="43311-122">Indicates the component type, the assembly, and the associated .NET information for the component.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43311-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43311-123">See Also</span></span>  
 <span data-ttu-id="43311-124">[設定原生管線元件](../core/configuring-native-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="43311-124">[Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md) </span></span>  
 [<span data-ttu-id="43311-125">使用管線設計師建立管線</span><span class="sxs-lookup"><span data-stu-id="43311-125">Creating Pipelines with Pipeline Designer</span></span>](../core/creating-pipelines-with-pipeline-designer.md)