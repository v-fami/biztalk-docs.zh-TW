---
title: 角色 （角色節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Role node [binding file]
ms.assetid: dfe2a579-7090-4d85-87e5-d627598c4ee8
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d70e99568db262ef5abd5b0885cb814c722347f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268694"
---
# <a name="role-roles-node"></a><span data-ttu-id="721c5-102">角色 (角色節點)</span><span class="sxs-lookup"><span data-stu-id="721c5-102">Role (Roles Node)</span></span>
<span data-ttu-id="721c5-103">繫結檔案之 [角色] 節點的 [角色] 節點，指定有關該繫結檔案所匯出服務繫結到之角色的資訊。</span><span class="sxs-lookup"><span data-stu-id="721c5-103">The Role node of the Roles node of a binding file specifies information about a role that is bound to a service that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-role-node"></a><span data-ttu-id="721c5-104">角色節點中的節點</span><span class="sxs-lookup"><span data-stu-id="721c5-104">Nodes in the Role node</span></span>  
 <span data-ttu-id="721c5-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="721c5-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="721c5-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="721c5-106">**Name**</span></span>|<span data-ttu-id="721c5-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="721c5-107">**Node Type**</span></span>|<span data-ttu-id="721c5-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="721c5-108">**Data Type**</span></span>|<span data-ttu-id="721c5-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="721c5-109">**Description**</span></span>|<span data-ttu-id="721c5-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="721c5-110">**Restrictions**</span></span>|<span data-ttu-id="721c5-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="721c5-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="721c5-112">名稱</span><span class="sxs-lookup"><span data-stu-id="721c5-112">Name</span></span>|<span data-ttu-id="721c5-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="721c5-113">Attribute</span></span>|<span data-ttu-id="721c5-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="721c5-114">xs:string</span></span>|<span data-ttu-id="721c5-115">指定角色的名稱。</span><span class="sxs-lookup"><span data-stu-id="721c5-115">Specifies the name of the role.</span></span>|<span data-ttu-id="721c5-116">不需要</span><span class="sxs-lookup"><span data-stu-id="721c5-116">Not required</span></span>|<span data-ttu-id="721c5-117">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="721c5-117">Default value: empty</span></span>|  
|<span data-ttu-id="721c5-118">RoleLinkTypeName</span><span class="sxs-lookup"><span data-stu-id="721c5-118">RoleLinkTypeName</span></span>|<span data-ttu-id="721c5-119">Attribute</span><span class="sxs-lookup"><span data-stu-id="721c5-119">Attribute</span></span>|<span data-ttu-id="721c5-120">xs:string</span><span class="sxs-lookup"><span data-stu-id="721c5-120">xs:string</span></span>|<span data-ttu-id="721c5-121">指定與角色關聯之角色連結類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="721c5-121">Specifies the name of the role link type associated with the role</span></span>|<span data-ttu-id="721c5-122">不需要</span><span class="sxs-lookup"><span data-stu-id="721c5-122">Not required</span></span>|<span data-ttu-id="721c5-123">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="721c5-123">Default value: empty</span></span>|  
|<span data-ttu-id="721c5-124">RoleType</span><span class="sxs-lookup"><span data-stu-id="721c5-124">RoleType</span></span>|<span data-ttu-id="721c5-125">Attribute</span><span class="sxs-lookup"><span data-stu-id="721c5-125">Attribute</span></span>|<span data-ttu-id="721c5-126">RoleRefType (SimpleType)</span><span class="sxs-lookup"><span data-stu-id="721c5-126">RoleRefType (SimpleType)</span></span>|<span data-ttu-id="721c5-127">指定與角色關聯之角色類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="721c5-127">Specifies the role type associated with the role.</span></span>|<span data-ttu-id="721c5-128">Required</span><span class="sxs-lookup"><span data-stu-id="721c5-128">Required</span></span>|<span data-ttu-id="721c5-129">預設值：無</span><span class="sxs-lookup"><span data-stu-id="721c5-129">Default value: none</span></span><br /><br /> <span data-ttu-id="721c5-130">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="721c5-130">Possible values include:</span></span><br /><br /> <span data-ttu-id="721c5-131">-不明</span><span class="sxs-lookup"><span data-stu-id="721c5-131">-   Unknown</span></span><br /><span data-ttu-id="721c5-132">-實作</span><span class="sxs-lookup"><span data-stu-id="721c5-132">-   Implements</span></span><br /><span data-ttu-id="721c5-133">-使用</span><span class="sxs-lookup"><span data-stu-id="721c5-133">-   Uses</span></span>|  
|[<span data-ttu-id="721c5-134">已登錄合作對象</span><span class="sxs-lookup"><span data-stu-id="721c5-134">Enlisted Parties</span></span>](../core/enlisted-parties-role-node.md)|<span data-ttu-id="721c5-135">記錄</span><span class="sxs-lookup"><span data-stu-id="721c5-135">Record</span></span>|<span data-ttu-id="721c5-136">ArrayOfEnlistedParty (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="721c5-136">ArrayOfEnlistedParty (ComplexType)</span></span>|<span data-ttu-id="721c5-137">繫結到此角色之已登錄合作對象的容器節點</span><span class="sxs-lookup"><span data-stu-id="721c5-137">Container node for the enlisted parties bound to this role.</span></span>|<span data-ttu-id="721c5-138">不需要</span><span class="sxs-lookup"><span data-stu-id="721c5-138">Not required</span></span>|<span data-ttu-id="721c5-139">預設值：無</span><span class="sxs-lookup"><span data-stu-id="721c5-139">Default value: none</span></span>|