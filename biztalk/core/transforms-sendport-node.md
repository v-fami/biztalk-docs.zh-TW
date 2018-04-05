---
title: Transforms （SendPort 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Transforms node [binding file]
ms.assetid: b405397b-e394-44fa-b507-93896f800f66
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1571a38841f6567279a27c58770f4198ba3eb56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transforms-sendport-node"></a><span data-ttu-id="7899a-102">Transforms (SendPort 節點)</span><span class="sxs-lookup"><span data-stu-id="7899a-102">Transforms (SendPort Node)</span></span>
<span data-ttu-id="7899a-103">繫結檔案之 [SendPort] 節點的 [Transforms] 節點包含與該繫結檔案一起匯出之單向傳送埠的輸出轉換集合。</span><span class="sxs-lookup"><span data-stu-id="7899a-103">The Transforms node of the SendPort node of a binding file contains the collection of outbound transforms of a one way send port that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transforms-node"></a><span data-ttu-id="7899a-104">轉換節點中的節點</span><span class="sxs-lookup"><span data-stu-id="7899a-104">Nodes in the Transforms node</span></span>  
 <span data-ttu-id="7899a-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="7899a-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="7899a-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="7899a-106">**Name**</span></span>|<span data-ttu-id="7899a-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="7899a-107">**Node Type**</span></span>|<span data-ttu-id="7899a-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="7899a-108">**Data Type**</span></span>|<span data-ttu-id="7899a-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="7899a-109">**Description**</span></span>|<span data-ttu-id="7899a-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="7899a-110">**Restrictions**</span></span>|<span data-ttu-id="7899a-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="7899a-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="7899a-112">轉換 （傳送埠轉換節點）</span><span class="sxs-lookup"><span data-stu-id="7899a-112">Transform (SendPort-Transforms Node)</span></span>](../core/transform-sendport-transforms-node.md)|<span data-ttu-id="7899a-113">記錄</span><span class="sxs-lookup"><span data-stu-id="7899a-113">Record</span></span>|<span data-ttu-id="7899a-114">Transform (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="7899a-114">Transform (ComplexType)</span></span>|<span data-ttu-id="7899a-115">指定 BizTalk Server 對應 (或轉換)，這個項目代表來源結構描述和目的結構描述之間的對應。</span><span class="sxs-lookup"><span data-stu-id="7899a-115">Specifies a BizTalk Server map, or transform, which is an item that represents the mapping between a source schema and destination schema.</span></span>|<span data-ttu-id="7899a-116">不需要</span><span class="sxs-lookup"><span data-stu-id="7899a-116">Not required</span></span>|<span data-ttu-id="7899a-117">預設值：無</span><span class="sxs-lookup"><span data-stu-id="7899a-117">Default value: none</span></span>|