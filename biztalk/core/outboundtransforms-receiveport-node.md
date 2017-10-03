---
title: "OutboundTransforms （ReceivePort 節點） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: OutboundTransforms node [binding file]
ms.assetid: 6deea062-4eb0-47ed-869c-ed6ec9290ea7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc6fa0bc804fad0d0ddea79614c392769452f1c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="outboundtransforms-receiveport-node"></a><span data-ttu-id="c22fd-102">OutboundTransforms (ReceivePort 節點)</span><span class="sxs-lookup"><span data-stu-id="c22fd-102">OutboundTransforms (ReceivePort Node)</span></span>
<span data-ttu-id="c22fd-103">繫結檔案之 ReceivePort 節點的 OutboundTransforms 節點，包含與該繫結檔案一起匯出之雙向接收埠輸出轉換的集合。</span><span class="sxs-lookup"><span data-stu-id="c22fd-103">The OutboundTransforms node of the ReceivePort node of a binding file contains the collection of outbound transforms of a two-way receive port that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-outboundtransforms-node"></a><span data-ttu-id="c22fd-104">OutboundTransforms 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="c22fd-104">Nodes in the OutboundTransforms node</span></span>  
 <span data-ttu-id="c22fd-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="c22fd-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="c22fd-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="c22fd-106">**Name**</span></span>|<span data-ttu-id="c22fd-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="c22fd-107">**Node Type**</span></span>|<span data-ttu-id="c22fd-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="c22fd-108">**Data Type**</span></span>|<span data-ttu-id="c22fd-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="c22fd-109">**Description**</span></span>|<span data-ttu-id="c22fd-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="c22fd-110">**Restrictions**</span></span>|<span data-ttu-id="c22fd-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="c22fd-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="c22fd-112">轉換 （OutboundTransforms 節點）</span><span class="sxs-lookup"><span data-stu-id="c22fd-112">Transform (OutboundTransforms Node)</span></span>](../core/transform-outboundtransforms-node.md)|<span data-ttu-id="c22fd-113">記錄</span><span class="sxs-lookup"><span data-stu-id="c22fd-113">Record</span></span>|<span data-ttu-id="c22fd-114">Transform (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="c22fd-114">Transform (ComplexType)</span></span>|<span data-ttu-id="c22fd-115">指定 BizTalk Server 對應 (或轉換)，這個項目代表來源結構描述和目的結構描述之間的對應。</span><span class="sxs-lookup"><span data-stu-id="c22fd-115">Specifies a BizTalk Server map, or transform, which is an item that represents the mapping between a source schema and destination schema.</span></span>|<span data-ttu-id="c22fd-116">不需要</span><span class="sxs-lookup"><span data-stu-id="c22fd-116">Not required</span></span>|<span data-ttu-id="c22fd-117">預設值：無</span><span class="sxs-lookup"><span data-stu-id="c22fd-117">Default value: none</span></span>|