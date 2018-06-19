---
title: DistributionList （DistributionListCollection 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DistributionList node [binding file]
ms.assetid: 51864a5c-1697-4804-ac18-8211494f3ff0
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 931443cdca27e5c06767f075298d50ff999545a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239334"
---
# <a name="distributionlist-distributionlistcollection-node"></a><span data-ttu-id="20671-102">DistributionList (DistributionListCollection 節點)</span><span class="sxs-lookup"><span data-stu-id="20671-102">DistributionList (DistributionListCollection Node)</span></span>
<span data-ttu-id="20671-103">繫結檔案的 [DistributionList] 節點包含與該繫結檔案一起匯出之通訊群組清單的特定相關資訊。</span><span class="sxs-lookup"><span data-stu-id="20671-103">The DistributionList node of a binding file contains specific information about a distribution list that is exported with the binding file.</span></span> <span data-ttu-id="20671-104">通訊群組清單在 [BizTalk Server 系統管理員] 中稱為傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="20671-104">A distribution list is referred to as a send port group in the BizTalk Server Administrator.</span></span>  
  
## <a name="nodes-in-the-distributionlist-node"></a><span data-ttu-id="20671-105">DistributionList 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="20671-105">Nodes in the DistributionList node</span></span>  
 <span data-ttu-id="20671-106">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="20671-106">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="20671-107">**名稱**</span><span class="sxs-lookup"><span data-stu-id="20671-107">**Name**</span></span>|<span data-ttu-id="20671-108">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="20671-108">**Node Type**</span></span>|<span data-ttu-id="20671-109">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="20671-109">**Data Type**</span></span>|<span data-ttu-id="20671-110">**說明**</span><span class="sxs-lookup"><span data-stu-id="20671-110">**Description**</span></span>|<span data-ttu-id="20671-111">**限制**</span><span class="sxs-lookup"><span data-stu-id="20671-111">**Restrictions**</span></span>|<span data-ttu-id="20671-112">**註解**</span><span class="sxs-lookup"><span data-stu-id="20671-112">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="20671-113">名稱</span><span class="sxs-lookup"><span data-stu-id="20671-113">Name</span></span>|<span data-ttu-id="20671-114">Attribute</span><span class="sxs-lookup"><span data-stu-id="20671-114">Attribute</span></span>|<span data-ttu-id="20671-115">xs:string</span><span class="sxs-lookup"><span data-stu-id="20671-115">xs:string</span></span>|<span data-ttu-id="20671-116">指定通訊群組清單的名稱。</span><span class="sxs-lookup"><span data-stu-id="20671-116">Specifies the name of the distribution list.</span></span>|<span data-ttu-id="20671-117">不需要</span><span class="sxs-lookup"><span data-stu-id="20671-117">Not required</span></span>|<span data-ttu-id="20671-118">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="20671-118">Default value: empty</span></span>|  
|[<span data-ttu-id="20671-119">傳送埠</span><span class="sxs-lookup"><span data-stu-id="20671-119">SendPorts</span></span>](../core/sendports-distributionlist-node.md)|<span data-ttu-id="20671-120">記錄</span><span class="sxs-lookup"><span data-stu-id="20671-120">Record</span></span>|<span data-ttu-id="20671-121">ArrayOfSendPortRef (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="20671-121">ArrayOfSendPortRef (ComplexType)</span></span>|<span data-ttu-id="20671-122">指定通訊群組清單所包含的一個或多個傳送埠。</span><span class="sxs-lookup"><span data-stu-id="20671-122">Specifies the send port or send ports included in the distribution list.</span></span>|<span data-ttu-id="20671-123">不需要</span><span class="sxs-lookup"><span data-stu-id="20671-123">Not required</span></span>|<span data-ttu-id="20671-124">預設值：無</span><span class="sxs-lookup"><span data-stu-id="20671-124">Default value: none</span></span>|  
|<span data-ttu-id="20671-125">篩選</span><span class="sxs-lookup"><span data-stu-id="20671-125">Filter</span></span>|<span data-ttu-id="20671-126">元素</span><span class="sxs-lookup"><span data-stu-id="20671-126">Element</span></span>|<span data-ttu-id="20671-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="20671-127">xs:string</span></span>|<span data-ttu-id="20671-128">指定在此通訊群組清單使用之選擇性篩選條件運算式的名稱。</span><span class="sxs-lookup"><span data-stu-id="20671-128">Specifies the name of the optional filter expression used on this distribution list.</span></span>|<span data-ttu-id="20671-129">必要項</span><span class="sxs-lookup"><span data-stu-id="20671-129">Required</span></span>|<span data-ttu-id="20671-130">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="20671-130">Default value: empty</span></span>|  
|<span data-ttu-id="20671-131">ApplicationName</span><span class="sxs-lookup"><span data-stu-id="20671-131">ApplicationName</span></span>|<span data-ttu-id="20671-132">元素</span><span class="sxs-lookup"><span data-stu-id="20671-132">Element</span></span>|<span data-ttu-id="20671-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="20671-133">xs:string</span></span>|<span data-ttu-id="20671-134">指定通訊群組清單與其關聯之應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="20671-134">Specifies the name of the application that the distribution list is associated with.</span></span>|<span data-ttu-id="20671-135">必要項</span><span class="sxs-lookup"><span data-stu-id="20671-135">Required</span></span>|<span data-ttu-id="20671-136">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="20671-136">Default value: empty</span></span>|  
|<span data-ttu-id="20671-137">說明</span><span class="sxs-lookup"><span data-stu-id="20671-137">Description</span></span>|<span data-ttu-id="20671-138">元素</span><span class="sxs-lookup"><span data-stu-id="20671-138">Element</span></span>|<span data-ttu-id="20671-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="20671-139">xs:string</span></span>|<span data-ttu-id="20671-140">指定通訊群組清單的描述。</span><span class="sxs-lookup"><span data-stu-id="20671-140">Specifies a description for the distribution list.</span></span>|<span data-ttu-id="20671-141">必要項</span><span class="sxs-lookup"><span data-stu-id="20671-141">Required</span></span>|<span data-ttu-id="20671-142">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="20671-142">Default value: empty</span></span>|