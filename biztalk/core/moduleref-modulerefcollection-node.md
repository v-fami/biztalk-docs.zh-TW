---
title: ModuleRef （ModuleRefCollection 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ModuleRef node [binding file]
ms.assetid: 61787779-33bd-499a-a5c1-c1e0bd306b48
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ed580b022e9896ade824c8cf8eccc2458c7ddce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="moduleref-modulerefcollection-node"></a><span data-ttu-id="b7898-102">ModuleRef (ModuleRefCollection 節點)</span><span class="sxs-lookup"><span data-stu-id="b7898-102">ModuleRef (ModuleRefCollection Node)</span></span>
<span data-ttu-id="b7898-103">繫結檔案的 [ModuleRef] 節點包含與該繫結檔案一起匯出之 .NET 組件有關的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="b7898-103">The ModuleRef node of a binding file contains specific information about a .NET assembly that was exported with the binding file.</span></span> <span data-ttu-id="b7898-104">ModuleRef 節點包含 (但不限於) 有自訂程式碼、結構描述和協調流程之組件的說明。</span><span class="sxs-lookup"><span data-stu-id="b7898-104">A ModuleRef node can include but is not limited to descriptions of assemblies that contain custom code, schemas, and orchestrations.</span></span>  
  
## <a name="nodes-in-the-moduleref-node"></a><span data-ttu-id="b7898-105">ModuleRef 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="b7898-105">Nodes in the ModuleRef node</span></span>  
 <span data-ttu-id="b7898-106">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="b7898-106">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="b7898-107">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b7898-107">**Name**</span></span>|<span data-ttu-id="b7898-108">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="b7898-108">**Node Type**</span></span>|<span data-ttu-id="b7898-109">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="b7898-109">**Data Type**</span></span>|<span data-ttu-id="b7898-110">**說明**</span><span class="sxs-lookup"><span data-stu-id="b7898-110">**Description**</span></span>|<span data-ttu-id="b7898-111">**限制**</span><span class="sxs-lookup"><span data-stu-id="b7898-111">**Restrictions**</span></span>|<span data-ttu-id="b7898-112">**註解**</span><span class="sxs-lookup"><span data-stu-id="b7898-112">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="b7898-113">服務</span><span class="sxs-lookup"><span data-stu-id="b7898-113">Services</span></span>](../core/services-moduleref-node.md)|<span data-ttu-id="b7898-114">記錄</span><span class="sxs-lookup"><span data-stu-id="b7898-114">Record</span></span>|<span data-ttu-id="b7898-115">ArrayOfServiceRef (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="b7898-115">ArrayOfServiceRef (ComplexType)</span></span>|<span data-ttu-id="b7898-116">與此 .NET 組件相關聯之服務的容器節點。</span><span class="sxs-lookup"><span data-stu-id="b7898-116">Container node for services associated with this .NET assembly.</span></span>|<span data-ttu-id="b7898-117">不需要</span><span class="sxs-lookup"><span data-stu-id="b7898-117">Not required</span></span>|<span data-ttu-id="b7898-118">預設值：無</span><span class="sxs-lookup"><span data-stu-id="b7898-118">Default value: none</span></span>|  
|[<span data-ttu-id="b7898-119">TrackedSchemas （ModuleRef 節點）</span><span class="sxs-lookup"><span data-stu-id="b7898-119">TrackedSchemas (ModuleRef Node)</span></span>](../core/trackedschemas-moduleref-node.md)|<span data-ttu-id="b7898-120">記錄</span><span class="sxs-lookup"><span data-stu-id="b7898-120">Record</span></span>|<span data-ttu-id="b7898-121">ArrayOfSchema (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="b7898-121">ArrayOfSchema (ComplexType)</span></span>|<span data-ttu-id="b7898-122">與此 .NET 組件相關聯之結構描述的容器節點。</span><span class="sxs-lookup"><span data-stu-id="b7898-122">Container node for schemas associated with this .NET assembly</span></span>|<span data-ttu-id="b7898-123">不需要</span><span class="sxs-lookup"><span data-stu-id="b7898-123">Not required</span></span>|<span data-ttu-id="b7898-124">預設值：無</span><span class="sxs-lookup"><span data-stu-id="b7898-124">Default value: none</span></span>|