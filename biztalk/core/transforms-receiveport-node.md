---
title: 轉換 （ReceivePort 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Transforms node [binding file]
ms.assetid: cd32f2fe-b70a-4153-86ec-bb1aa9bad0e4
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7d039d95a1f28afa468078ff7547e9f298633bb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279238"
---
# <a name="transforms-receiveport-node"></a><span data-ttu-id="0c435-102">轉換 (ReceivePort 節點)</span><span class="sxs-lookup"><span data-stu-id="0c435-102">Transforms (ReceivePort Node)</span></span>
<span data-ttu-id="0c435-103">繫結檔案之 [ReceivePort] 節點的 [轉換] 節點包含隨同該繫結檔案一起匯出之單向接收埠的輸入轉換集合。</span><span class="sxs-lookup"><span data-stu-id="0c435-103">The Transforms node of the ReceivePort node of a binding file contains the collection of inbound transforms of a one way receive port that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transforms-node"></a><span data-ttu-id="0c435-104">轉換節點中的節點</span><span class="sxs-lookup"><span data-stu-id="0c435-104">Nodes in the Transforms node</span></span>  
 <span data-ttu-id="0c435-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="0c435-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="0c435-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="0c435-106">**Name**</span></span>|<span data-ttu-id="0c435-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="0c435-107">**Node Type**</span></span>|<span data-ttu-id="0c435-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="0c435-108">**Data Type**</span></span>|<span data-ttu-id="0c435-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="0c435-109">**Description**</span></span>|<span data-ttu-id="0c435-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="0c435-110">**Restrictions**</span></span>|<span data-ttu-id="0c435-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="0c435-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="0c435-112">轉換 （轉換節點）</span><span class="sxs-lookup"><span data-stu-id="0c435-112">Transform (Transforms Node)</span></span>](../core/transform-transforms-node.md)|<span data-ttu-id="0c435-113">記錄</span><span class="sxs-lookup"><span data-stu-id="0c435-113">Record</span></span>|<span data-ttu-id="0c435-114">Transform (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="0c435-114">Transform (ComplexType)</span></span>|<span data-ttu-id="0c435-115">指定 BizTalk Server 對應 (或轉換)，這個項目代表來源結構描述和目的結構描述之間的對應。</span><span class="sxs-lookup"><span data-stu-id="0c435-115">Specifies a BizTalk Server map, or transform, which is an item that represents the mapping between a source schema and destination schema.</span></span>|<span data-ttu-id="0c435-116">不需要</span><span class="sxs-lookup"><span data-stu-id="0c435-116">Not required</span></span>|<span data-ttu-id="0c435-117">預設值：無</span><span class="sxs-lookup"><span data-stu-id="0c435-117">Default value: none</span></span>|