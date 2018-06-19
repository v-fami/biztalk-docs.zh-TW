---
title: ModuleRefCollection 節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ModuleRefCollection node [binding file]
ms.assetid: fa8593bf-6548-4615-9f98-1e0eadde9aa4
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 039cabd380195f840e9ffb99de5071026b3810c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262678"
---
# <a name="modulerefcollection-node"></a><span data-ttu-id="28fe2-102">ModuleRefCollection 節點</span><span class="sxs-lookup"><span data-stu-id="28fe2-102">ModuleRefCollection Node</span></span>
<span data-ttu-id="28fe2-103">繫結檔案的 ModuleRefCollection 區段是所有 ModuleRef 節點的父節點，這些節點包含隨同繫結檔案一起匯出之 .NET 組件的特定相關資訊。</span><span class="sxs-lookup"><span data-stu-id="28fe2-103">The ModuleRefCollection section of a binding file is the parent node for all of the ModuleRef nodes which contain specific information about .NET assemblies exported with the binding file.</span></span>  
  
## <a name="entries-in-the-modulerefcollection-section"></a><span data-ttu-id="28fe2-104">ModuleRefCollection 區段中的項目</span><span class="sxs-lookup"><span data-stu-id="28fe2-104">Entries in the ModuleRefCollection section</span></span>  
 <span data-ttu-id="28fe2-105">下表列出可以為繫結檔案中這個區段的節點設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="28fe2-105">The following table lists the properties that can be set for the nodes in this section of a binding file:</span></span>  
  
|<span data-ttu-id="28fe2-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="28fe2-106">**Name**</span></span>|<span data-ttu-id="28fe2-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="28fe2-107">**Node Type**</span></span>|<span data-ttu-id="28fe2-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="28fe2-108">**Data Type**</span></span>|<span data-ttu-id="28fe2-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="28fe2-109">**Description**</span></span>|<span data-ttu-id="28fe2-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="28fe2-110">**Restrictions**</span></span>|<span data-ttu-id="28fe2-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="28fe2-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="28fe2-112">ModuleRef</span><span class="sxs-lookup"><span data-stu-id="28fe2-112">ModuleRef</span></span>](../core/moduleref-modulerefcollection-node.md)|<span data-ttu-id="28fe2-113">記錄</span><span class="sxs-lookup"><span data-stu-id="28fe2-113">Record</span></span>|<span data-ttu-id="28fe2-114">ModuleRef (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="28fe2-114">ModuleRef (ComplexType)</span></span>|<span data-ttu-id="28fe2-115">.NET 組件模組 (由繫結檔案所匯出) 的容器節點。</span><span class="sxs-lookup"><span data-stu-id="28fe2-115">Container node for a .NET assembly module exported with the binding file.</span></span>|<span data-ttu-id="28fe2-116">不需要</span><span class="sxs-lookup"><span data-stu-id="28fe2-116">Not required</span></span>|<span data-ttu-id="28fe2-117">預設值：無</span><span class="sxs-lookup"><span data-stu-id="28fe2-117">Default value: None</span></span>|