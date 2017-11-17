---
title: "已登錄合作對象 （已登錄合作對象節點） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Enlisted Parties node [binding file]
ms.assetid: 2ff7b563-17c5-48e9-b33e-62c821188448
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 624f74d3b49b80e8000723c3f7451c52b37c8d3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="enlisted-party-enlisted-parties-node"></a><span data-ttu-id="1dd34-102">已登錄的合作對象 (已登錄的合作對象節點)</span><span class="sxs-lookup"><span data-stu-id="1dd34-102">Enlisted Party (Enlisted Parties Node)</span></span>
<span data-ttu-id="1dd34-103">繫結檔案的 [已登錄的合作對象] 節點包含與隨著繫結檔案匯出之角色關聯的已登錄之合作對象的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="1dd34-103">The Enlisted Party node of a binding file contains specific information about an enlisted party associated with a role that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-enlisted-party-node"></a><span data-ttu-id="1dd34-104">已登錄的合作對象節點中的節點</span><span class="sxs-lookup"><span data-stu-id="1dd34-104">Nodes in the Enlisted Party node</span></span>  
 <span data-ttu-id="1dd34-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="1dd34-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="1dd34-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="1dd34-106">**Name**</span></span>|<span data-ttu-id="1dd34-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="1dd34-107">**Node Type**</span></span>|<span data-ttu-id="1dd34-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="1dd34-108">**Data Type**</span></span>|<span data-ttu-id="1dd34-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="1dd34-109">**Description**</span></span>|<span data-ttu-id="1dd34-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="1dd34-110">**Restrictions**</span></span>|<span data-ttu-id="1dd34-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="1dd34-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="1dd34-112">名稱</span><span class="sxs-lookup"><span data-stu-id="1dd34-112">Name</span></span>|<span data-ttu-id="1dd34-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="1dd34-113">Attribute</span></span>|<span data-ttu-id="1dd34-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="1dd34-114">xs:string</span></span>|<span data-ttu-id="1dd34-115">指定已登錄的合作對象的名稱</span><span class="sxs-lookup"><span data-stu-id="1dd34-115">Specifies the name of the enlisted party</span></span>|<span data-ttu-id="1dd34-116">不需要</span><span class="sxs-lookup"><span data-stu-id="1dd34-116">Not required</span></span>|<span data-ttu-id="1dd34-117">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="1dd34-117">Default value: empty</span></span>|  
|[<span data-ttu-id="1dd34-118">對應</span><span class="sxs-lookup"><span data-stu-id="1dd34-118">Mappings</span></span>](../core/mappings-enlisted-party-node.md)|<span data-ttu-id="1dd34-119">記錄</span><span class="sxs-lookup"><span data-stu-id="1dd34-119">Record</span></span>|<span data-ttu-id="1dd34-120">ArrayOfEnlistedPartyMapping (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="1dd34-120">ArrayOfEnlistedPartyMapping (ComplexType)</span></span>|<span data-ttu-id="1dd34-121">合作對象連接埠與角色連接埠類型作業間之對應的容器節點。</span><span class="sxs-lookup"><span data-stu-id="1dd34-121">Container node for the mappings between party ports and role port type operations.</span></span>|<span data-ttu-id="1dd34-122">不需要</span><span class="sxs-lookup"><span data-stu-id="1dd34-122">Not required</span></span>|<span data-ttu-id="1dd34-123">預設值：無</span><span class="sxs-lookup"><span data-stu-id="1dd34-123">Default value: none</span></span>|