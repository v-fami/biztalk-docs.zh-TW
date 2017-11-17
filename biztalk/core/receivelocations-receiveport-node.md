---
title: "ReceiveLocations （ReceivePort 節點） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ReceiveLocations node [binding file]
ms.assetid: c12acc1b-f8fe-4a27-8386-d9f4f4455e3f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c9fb5b64466e32ae27d53852b3383eb79531d60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receivelocations-receiveport-node"></a><span data-ttu-id="663c7-102">ReceiveLocations (ReceivePort 節點)</span><span class="sxs-lookup"><span data-stu-id="663c7-102">ReceiveLocations (ReceivePort Node)</span></span>
<span data-ttu-id="663c7-103">繫結檔案之 [ReceivePort] 節點的 [ ReceiveLocations] 節點是所有 [ReceiveLocation] 節點的父節點，這些節點包含隨同繫結檔案一起匯出之接收位置的特定相關資訊。</span><span class="sxs-lookup"><span data-stu-id="663c7-103">The ReceiveLocations node of the ReceivePort node of a binding file is the parent node for all of the ReceiveLocation nodes which contain specific information about the receive locations that are exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-receivelocations-node"></a><span data-ttu-id="663c7-104">ReceiveLocations 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="663c7-104">Nodes in the ReceiveLocations node</span></span>  
 <span data-ttu-id="663c7-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="663c7-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="663c7-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="663c7-106">**Name**</span></span>|<span data-ttu-id="663c7-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="663c7-107">**Node Type**</span></span>|<span data-ttu-id="663c7-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="663c7-108">**Data Type**</span></span>|<span data-ttu-id="663c7-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="663c7-109">**Description**</span></span>|<span data-ttu-id="663c7-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="663c7-110">**Restrictions**</span></span>|<span data-ttu-id="663c7-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="663c7-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="663c7-112">ReceiveLocation</span><span class="sxs-lookup"><span data-stu-id="663c7-112">ReceiveLocation</span></span>](../core/receivelocation-receivelocations-node.md)|<span data-ttu-id="663c7-113">記錄</span><span class="sxs-lookup"><span data-stu-id="663c7-113">Record</span></span>|<span data-ttu-id="663c7-114">ReceiveLocation (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="663c7-114">ReceiveLocation (ComplexType)</span></span>|<span data-ttu-id="663c7-115">指定隨同繫結檔案一起匯出之接收位置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="663c7-115">Specifies information about a receive location that is exported with the binding file.</span></span>|<span data-ttu-id="663c7-116">不需要</span><span class="sxs-lookup"><span data-stu-id="663c7-116">Not required</span></span>|<span data-ttu-id="663c7-117">預設值：無</span><span class="sxs-lookup"><span data-stu-id="663c7-117">Default value: none</span></span>|