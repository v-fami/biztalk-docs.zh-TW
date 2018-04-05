---
title: 轉換 （傳送埠轉換節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Transform node [binding file]
ms.assetid: db9a82b2-9bc1-4bd8-8d98-a708a8d25b35
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a54ed1f25b762d12f598bca84da9b9c3ddd26a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transform-sendport-transforms-node"></a><span data-ttu-id="34a21-102">轉換 （傳送埠轉換節點）</span><span class="sxs-lookup"><span data-stu-id="34a21-102">Transform (SendPort-Transforms Node)</span></span>
<span data-ttu-id="34a21-103">繫結檔案之 [轉換] 節點的 [轉換] 節點，包含與該繫結檔案匯出之 BizTalk Server 對應有關的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="34a21-103">The Transform node of the Transforms node of a binding file contains specific information about a BizTalk Server map that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transform-node"></a><span data-ttu-id="34a21-104">轉換節點中的節點</span><span class="sxs-lookup"><span data-stu-id="34a21-104">Nodes in the Transform node</span></span>  
 <span data-ttu-id="34a21-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="34a21-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="34a21-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="34a21-106">**Name**</span></span>|<span data-ttu-id="34a21-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="34a21-107">**Node Type**</span></span>|<span data-ttu-id="34a21-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="34a21-108">**Data Type**</span></span>|<span data-ttu-id="34a21-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="34a21-109">**Description**</span></span>|<span data-ttu-id="34a21-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="34a21-110">**Restrictions**</span></span>|<span data-ttu-id="34a21-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="34a21-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="34a21-112">FullName</span><span class="sxs-lookup"><span data-stu-id="34a21-112">FullName</span></span>|<span data-ttu-id="34a21-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="34a21-113">Attribute</span></span>|<span data-ttu-id="34a21-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="34a21-114">xs:string</span></span>|<span data-ttu-id="34a21-115">指定對應的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="34a21-115">Specifies the full name of the map.</span></span>|<span data-ttu-id="34a21-116">不需要</span><span class="sxs-lookup"><span data-stu-id="34a21-116">Not required</span></span>|<span data-ttu-id="34a21-117">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="34a21-117">Default value: empty</span></span>|  
|<span data-ttu-id="34a21-118">AssemblyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="34a21-118">AssemblyQualifiedName</span></span>|<span data-ttu-id="34a21-119">Attribute</span><span class="sxs-lookup"><span data-stu-id="34a21-119">Attribute</span></span>|<span data-ttu-id="34a21-120">xs:string</span><span class="sxs-lookup"><span data-stu-id="34a21-120">xs:string</span></span>|<span data-ttu-id="34a21-121">指定對應的組件限定名稱。</span><span class="sxs-lookup"><span data-stu-id="34a21-121">Specifies the assembly qualified name of the map.</span></span>|<span data-ttu-id="34a21-122">不需要</span><span class="sxs-lookup"><span data-stu-id="34a21-122">Not required</span></span>|<span data-ttu-id="34a21-123">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="34a21-123">Default value: empty</span></span>|