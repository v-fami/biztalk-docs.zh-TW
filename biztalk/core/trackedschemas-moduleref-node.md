---
title: TrackedSchemas （ModuleRef 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TrackedSchemas node [binding file]
ms.assetid: a2b99fbf-df6b-4a94-97b8-ac5eb819604f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 303aeb1ed17b001583a596d5b550faf63ea1200b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278910"
---
# <a name="trackedschemas-moduleref-node"></a><span data-ttu-id="81642-102">TrackedSchemas (ModuleRef 節點)</span><span class="sxs-lookup"><span data-stu-id="81642-102">TrackedSchemas (ModuleRef Node)</span></span>
<span data-ttu-id="81642-103">繫結檔案之 TrackedSchemas 節點是所有 [結構描述] 節點的父節點，這些節點會描述繫結至隨同繫結檔案一起匯出之服務的結構描述。</span><span class="sxs-lookup"><span data-stu-id="81642-103">The TrackedSchemas node of a binding file is the parent node for all of the Schema nodes which describe the schemas bound to the service that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-trackedschemas-node"></a><span data-ttu-id="81642-104">TrackedSchemas 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="81642-104">Nodes in the TrackedSchemas node</span></span>  
 <span data-ttu-id="81642-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="81642-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="81642-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="81642-106">**Name**</span></span>|<span data-ttu-id="81642-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="81642-107">**Node Type**</span></span>|<span data-ttu-id="81642-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="81642-108">**Data Type**</span></span>|<span data-ttu-id="81642-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="81642-109">**Description**</span></span>|<span data-ttu-id="81642-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="81642-110">**Restrictions**</span></span>|<span data-ttu-id="81642-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="81642-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="81642-112">結構描述</span><span class="sxs-lookup"><span data-stu-id="81642-112">Schema</span></span>](../core/schema-trackedschemas-node.md)|<span data-ttu-id="81642-113">記錄</span><span class="sxs-lookup"><span data-stu-id="81642-113">Record</span></span>|<span data-ttu-id="81642-114">ArrayOfSchema (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="81642-114">ArrayOfSchema (ComplexType)</span></span>|<span data-ttu-id="81642-115">繫結至隨同繫結檔案一起匯出之服務的結構描述之容器節點。</span><span class="sxs-lookup"><span data-stu-id="81642-115">Container node for the schemas that are bound to the service that is exported with the binding file.</span></span>|<span data-ttu-id="81642-116">不需要</span><span class="sxs-lookup"><span data-stu-id="81642-116">Not required</span></span>|<span data-ttu-id="81642-117">預設值：無</span><span class="sxs-lookup"><span data-stu-id="81642-117">Default value: none</span></span>|