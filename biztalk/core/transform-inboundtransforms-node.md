---
title: 轉換 （InboundTransforms 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Transform node [binding file]
ms.assetid: c1bad23e-78a4-4fd4-95ef-30601393d53c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 705b1b04b8305330ab1d5ff705c5025f24b0685c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279110"
---
# <a name="transform-inboundtransforms-node"></a><span data-ttu-id="620b9-102">轉換 (InboundTransforms 節點)</span><span class="sxs-lookup"><span data-stu-id="620b9-102">Transform (InboundTransforms Node)</span></span>
<span data-ttu-id="620b9-103">繫結檔案之 [InboundTransforms] 節點的 [轉換] 節點中，包含隨同該繫結檔案一起匯出之 BizTalk Server 對應的特定相關資訊。</span><span class="sxs-lookup"><span data-stu-id="620b9-103">The Transform node of the InboundTransforms node of a binding file contains specific information about a BizTalk Server map that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transform-node"></a><span data-ttu-id="620b9-104">轉換節點中的節點</span><span class="sxs-lookup"><span data-stu-id="620b9-104">Nodes in the Transform node</span></span>  
 <span data-ttu-id="620b9-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="620b9-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="620b9-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="620b9-106">**Name**</span></span>|<span data-ttu-id="620b9-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="620b9-107">**Node Type**</span></span>|<span data-ttu-id="620b9-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="620b9-108">**Data Type**</span></span>|<span data-ttu-id="620b9-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="620b9-109">**Description**</span></span>|<span data-ttu-id="620b9-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="620b9-110">**Restrictions**</span></span>|<span data-ttu-id="620b9-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="620b9-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="620b9-112">FullName</span><span class="sxs-lookup"><span data-stu-id="620b9-112">FullName</span></span>|<span data-ttu-id="620b9-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="620b9-113">Attribute</span></span>|<span data-ttu-id="620b9-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="620b9-114">xs:string</span></span>|<span data-ttu-id="620b9-115">指定對應的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="620b9-115">Specifies the full name of the map.</span></span>|<span data-ttu-id="620b9-116">不需要</span><span class="sxs-lookup"><span data-stu-id="620b9-116">Not required</span></span>|<span data-ttu-id="620b9-117">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="620b9-117">Default value: empty</span></span>|  
|<span data-ttu-id="620b9-118">AssemblyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="620b9-118">AssemblyQualifiedName</span></span>|<span data-ttu-id="620b9-119">Attribute</span><span class="sxs-lookup"><span data-stu-id="620b9-119">Attribute</span></span>|<span data-ttu-id="620b9-120">xs:string</span><span class="sxs-lookup"><span data-stu-id="620b9-120">xs:string</span></span>|<span data-ttu-id="620b9-121">指定對應的組件限定名稱。</span><span class="sxs-lookup"><span data-stu-id="620b9-121">Specifies the assembly qualified name of the map.</span></span>|<span data-ttu-id="620b9-122">不需要</span><span class="sxs-lookup"><span data-stu-id="620b9-122">Not required</span></span>|<span data-ttu-id="620b9-123">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="620b9-123">Default value: empty</span></span>|