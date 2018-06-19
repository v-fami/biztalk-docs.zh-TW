---
title: 對應 （對應節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Mapping node [binding file]
ms.assetid: bc54c476-505c-4020-b7df-1d19f86329aa
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2c62d46e4d5c2b73eee5094ecda0e20c039798a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262518"
---
# <a name="mapping-mappings-node"></a><span data-ttu-id="6773f-102">對應 (對應節點)</span><span class="sxs-lookup"><span data-stu-id="6773f-102">Mapping (Mappings Node)</span></span>
<span data-ttu-id="6773f-103">繫結檔案的 [對應] 節點描述已登錄合作對象之合作對象連接埠和角色連接埠類型作業之間的對應。</span><span class="sxs-lookup"><span data-stu-id="6773f-103">The Mapping node of a binding file describes the mapping between a party port and role port type operation for the enlisted party.</span></span>  
  
## <a name="nodes-in-the-mapping-node"></a><span data-ttu-id="6773f-104">對應節點中的節點</span><span class="sxs-lookup"><span data-stu-id="6773f-104">Nodes in the Mapping node</span></span>  
 <span data-ttu-id="6773f-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="6773f-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="6773f-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="6773f-106">**Name**</span></span>|<span data-ttu-id="6773f-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="6773f-107">**Node Type**</span></span>|<span data-ttu-id="6773f-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="6773f-108">**Data Type**</span></span>|<span data-ttu-id="6773f-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="6773f-109">**Description**</span></span>|<span data-ttu-id="6773f-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="6773f-110">**Restrictions**</span></span>|<span data-ttu-id="6773f-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="6773f-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="6773f-112">PortTypeName</span><span class="sxs-lookup"><span data-stu-id="6773f-112">PortTypeName</span></span>|<span data-ttu-id="6773f-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="6773f-113">Attribute</span></span>|<span data-ttu-id="6773f-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="6773f-114">xs:string</span></span>|<span data-ttu-id="6773f-115">指定連接埠類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="6773f-115">Specifies the name of the port type.</span></span>|<span data-ttu-id="6773f-116">不需要</span><span class="sxs-lookup"><span data-stu-id="6773f-116">Not required</span></span>|<span data-ttu-id="6773f-117">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="6773f-117">Default value: empty</span></span>|  
|<span data-ttu-id="6773f-118">OperationName</span><span class="sxs-lookup"><span data-stu-id="6773f-118">OperationName</span></span>|<span data-ttu-id="6773f-119">Attribute</span><span class="sxs-lookup"><span data-stu-id="6773f-119">Attribute</span></span>|<span data-ttu-id="6773f-120">xs:string</span><span class="sxs-lookup"><span data-stu-id="6773f-120">xs:string</span></span>|<span data-ttu-id="6773f-121">指定屬於此連接埠類型的作業。</span><span class="sxs-lookup"><span data-stu-id="6773f-121">Specifies the operation belonging to this port type.</span></span>|<span data-ttu-id="6773f-122">不需要</span><span class="sxs-lookup"><span data-stu-id="6773f-122">Not required</span></span>|<span data-ttu-id="6773f-123">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="6773f-123">Default value: empty</span></span>|  
|[<span data-ttu-id="6773f-124">SendPortRef</span><span class="sxs-lookup"><span data-stu-id="6773f-124">SendPortRef</span></span>](../core/sendportref-mapping-node.md)|<span data-ttu-id="6773f-125">記錄</span><span class="sxs-lookup"><span data-stu-id="6773f-125">Record</span></span>|<span data-ttu-id="6773f-126">SendPortRef (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="6773f-126">SendPortRef (ComplexType)</span></span>|<span data-ttu-id="6773f-127">與對應有關之傳送埠清單的容器節點。</span><span class="sxs-lookup"><span data-stu-id="6773f-127">Container node for the list of send ports associated with a mapping.</span></span>|<span data-ttu-id="6773f-128">不需要</span><span class="sxs-lookup"><span data-stu-id="6773f-128">Not required</span></span>|<span data-ttu-id="6773f-129">預設值：無</span><span class="sxs-lookup"><span data-stu-id="6773f-129">Default value: none</span></span>|