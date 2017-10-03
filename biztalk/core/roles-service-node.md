---
title: "角色 （服務節點） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Roles node [binding file]
ms.assetid: 847755c9-1697-41a0-b870-f9e795a1a2a6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b47f5ae94326b0555c0c9cd84752cb9f1c409daa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="roles-service-node"></a><span data-ttu-id="2c302-102">角色 (服務節點)</span><span class="sxs-lookup"><span data-stu-id="2c302-102">Roles (Service Node)</span></span>
<span data-ttu-id="2c302-103">繫結檔案的 [角色] 節點是所有 [角色] 節點的父節點，這些節點提供與繫結檔案一起匯出之服務所繫結每個角色的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="2c302-103">The Roles node of a binding file is the parent node for all of the Role nodes which provide specific information about each role bound to a service that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-roles-node"></a><span data-ttu-id="2c302-104">角色節點中的節點</span><span class="sxs-lookup"><span data-stu-id="2c302-104">Nodes in the Roles node</span></span>  
 <span data-ttu-id="2c302-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="2c302-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="2c302-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="2c302-106">**Name**</span></span>|<span data-ttu-id="2c302-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="2c302-107">**Node Type**</span></span>|<span data-ttu-id="2c302-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="2c302-108">**Data Type**</span></span>|<span data-ttu-id="2c302-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="2c302-109">**Description**</span></span>|<span data-ttu-id="2c302-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="2c302-110">**Restrictions**</span></span>|<span data-ttu-id="2c302-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="2c302-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="2c302-112">角色</span><span class="sxs-lookup"><span data-stu-id="2c302-112">Role</span></span>](../core/role-roles-node.md)|<span data-ttu-id="2c302-113">記錄</span><span class="sxs-lookup"><span data-stu-id="2c302-113">Record</span></span>|<span data-ttu-id="2c302-114">RoleRef (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="2c302-114">RoleRef (ComplexType)</span></span>|<span data-ttu-id="2c302-115">指定與繫結檔案一起匯出之服務所繫結角色的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2c302-115">Specifies information about a role that is bound to a service that is exported with the binding file.</span></span>|<span data-ttu-id="2c302-116">不需要</span><span class="sxs-lookup"><span data-stu-id="2c302-116">Not required</span></span>|<span data-ttu-id="2c302-117">預設值：無</span><span class="sxs-lookup"><span data-stu-id="2c302-117">Default value: none</span></span>|