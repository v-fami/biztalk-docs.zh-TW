---
title: InboundTransforms （SendPort 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- InboundTransforms node [binding file]
ms.assetid: 5ed239b9-13d8-4099-b779-08f589a722e9
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03567b5ea6095e38370260e1f17055ab40da4d6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="inboundtransforms-sendport-node"></a><span data-ttu-id="51ec8-102">InboundTransforms (SendPort 節點)</span><span class="sxs-lookup"><span data-stu-id="51ec8-102">InboundTransforms (SendPort Node)</span></span>
<span data-ttu-id="51ec8-103">繫結檔案之 [SendPort] 節點的 [InboundTransforms ] 節點包含與該繫結檔案匯出之雙向傳送埠關聯的輸入轉換集合。</span><span class="sxs-lookup"><span data-stu-id="51ec8-103">The InboundTransforms node of the SendPort node of a binding file contains the collection of inbound transforms of a two-way send port that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-inboundtransforms-node"></a><span data-ttu-id="51ec8-104">InboundTransforms 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="51ec8-104">Nodes in the InboundTransforms node</span></span>  
 <span data-ttu-id="51ec8-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="51ec8-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="51ec8-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="51ec8-106">**Name**</span></span>|<span data-ttu-id="51ec8-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="51ec8-107">**Node Type**</span></span>|<span data-ttu-id="51ec8-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="51ec8-108">**Data Type**</span></span>|<span data-ttu-id="51ec8-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="51ec8-109">**Description**</span></span>|<span data-ttu-id="51ec8-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="51ec8-110">**Restrictions**</span></span>|<span data-ttu-id="51ec8-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="51ec8-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="51ec8-112">轉換 （InboundTransforms 節點）</span><span class="sxs-lookup"><span data-stu-id="51ec8-112">Transform (InboundTransforms Node)</span></span>](../core/transform-inboundtransforms-node.md)|<span data-ttu-id="51ec8-113">記錄</span><span class="sxs-lookup"><span data-stu-id="51ec8-113">Record</span></span>|<span data-ttu-id="51ec8-114">Transform (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="51ec8-114">Transform (ComplexType)</span></span>|<span data-ttu-id="51ec8-115">指定 BizTalk Server 對應 (或轉換)，這個項目代表來源結構描述和目的結構描述之間的對應。</span><span class="sxs-lookup"><span data-stu-id="51ec8-115">Specifies a BizTalk Server map, or transform, which is an item that represents the mapping between a source schema and destination schema.</span></span>|<span data-ttu-id="51ec8-116">不需要</span><span class="sxs-lookup"><span data-stu-id="51ec8-116">Not required</span></span>|<span data-ttu-id="51ec8-117">預設值：無</span><span class="sxs-lookup"><span data-stu-id="51ec8-117">Default value: none</span></span>|