---
title: 轉換 （OutboundTransforms 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Transform node [binding file]
ms.assetid: 928a93cd-7a26-4148-b1af-dc0bc316f8c1
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b44dc5ffd444ebaee8f1f3007f27343c389c5e5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transform-outboundtransforms-node"></a><span data-ttu-id="119da-102">轉換 (OutboundTransforms 節點)</span><span class="sxs-lookup"><span data-stu-id="119da-102">Transform (OutboundTransforms Node)</span></span>
<span data-ttu-id="119da-103">繫結檔案之 [OutboundTransforms] 節點的 [轉換] 節點，包含與該繫結檔案一起匯出之 BizTalk Server 對應有關的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="119da-103">The Transform node of the OutboundTransforms node of a binding file contains specific information about a BizTalk Server map that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transform-node"></a><span data-ttu-id="119da-104">轉換節點中的節點</span><span class="sxs-lookup"><span data-stu-id="119da-104">Nodes in the Transform node</span></span>  
 <span data-ttu-id="119da-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="119da-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="119da-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="119da-106">**Name**</span></span>|<span data-ttu-id="119da-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="119da-107">**Node Type**</span></span>|<span data-ttu-id="119da-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="119da-108">**Data Type**</span></span>|<span data-ttu-id="119da-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="119da-109">**Description**</span></span>|<span data-ttu-id="119da-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="119da-110">**Restrictions**</span></span>|<span data-ttu-id="119da-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="119da-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="119da-112">FullName</span><span class="sxs-lookup"><span data-stu-id="119da-112">FullName</span></span>|<span data-ttu-id="119da-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="119da-113">Attribute</span></span>|<span data-ttu-id="119da-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="119da-114">xs:string</span></span>|<span data-ttu-id="119da-115">指定對應的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="119da-115">Specifies the full name of the map.</span></span>|<span data-ttu-id="119da-116">不需要</span><span class="sxs-lookup"><span data-stu-id="119da-116">Not required</span></span>|<span data-ttu-id="119da-117">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="119da-117">Default value: empty</span></span>|  
|<span data-ttu-id="119da-118">AssemblyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="119da-118">AssemblyQualifiedName</span></span>|<span data-ttu-id="119da-119">Attribute</span><span class="sxs-lookup"><span data-stu-id="119da-119">Attribute</span></span>|<span data-ttu-id="119da-120">xs:string</span><span class="sxs-lookup"><span data-stu-id="119da-120">xs:string</span></span>|<span data-ttu-id="119da-121">指定對應的組件限定名稱。</span><span class="sxs-lookup"><span data-stu-id="119da-121">Specifies the assembly qualified name of the map.</span></span>|<span data-ttu-id="119da-122">不需要</span><span class="sxs-lookup"><span data-stu-id="119da-122">Not required</span></span>|<span data-ttu-id="119da-123">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="119da-123">Default value: empty</span></span>|