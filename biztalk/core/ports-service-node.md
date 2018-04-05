---
title: 連接埠 （服務節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Ports node [binding file]
ms.assetid: 498d4310-4e9e-4e74-bc3d-5cbf1319c4ff
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31e09470b9f3287cce5ce15c2941d2165157ec48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ports-service-node"></a><span data-ttu-id="ca239-102">連接埠 (服務節點)</span><span class="sxs-lookup"><span data-stu-id="ca239-102">Ports (Service Node)</span></span>
<span data-ttu-id="ca239-103">繫結檔案的 [連接埠] 節點是所有 [連接埠] 節點的父節點，這些 [連接埠] 節點包含隨同繫結檔案一起匯出之繫結至服務的連接埠的特定相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ca239-103">The Ports node of a binding file is the parent node for all of the Port nodes which contain specific information about ports bound to a service that is exported with the binding file.</span></span>  
  
## <a name="node-in-the-ports-node"></a><span data-ttu-id="ca239-104">連接埠節點中的節點</span><span class="sxs-lookup"><span data-stu-id="ca239-104">Node in the Ports node</span></span>  
 <span data-ttu-id="ca239-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="ca239-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="ca239-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="ca239-106">**Name**</span></span>|<span data-ttu-id="ca239-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="ca239-107">**Node Type**</span></span>|<span data-ttu-id="ca239-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="ca239-108">**Data Type**</span></span>|<span data-ttu-id="ca239-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="ca239-109">**Description**</span></span>|<span data-ttu-id="ca239-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="ca239-110">**Restrictions**</span></span>|<span data-ttu-id="ca239-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="ca239-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="ca239-112">[[通訊埠]](../core/port-ports-node.md)</span><span class="sxs-lookup"><span data-stu-id="ca239-112">[Port](../core/port-ports-node.md)</span></span>|<span data-ttu-id="ca239-113">記錄</span><span class="sxs-lookup"><span data-stu-id="ca239-113">Record</span></span>|<span data-ttu-id="ca239-114">ServicePortRef (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="ca239-114">ServicePortRef (ComplexType)</span></span>|<span data-ttu-id="ca239-115">指定繫結至隨同繫結檔案匯出之服務的連接埠特定資訊。</span><span class="sxs-lookup"><span data-stu-id="ca239-115">Specifies information about a port that is bound to a service that is exported with the binding file.</span></span>|<span data-ttu-id="ca239-116">不需要</span><span class="sxs-lookup"><span data-stu-id="ca239-116">Not required</span></span>|<span data-ttu-id="ca239-117">預設值：無</span><span class="sxs-lookup"><span data-stu-id="ca239-117">Default value: none</span></span>|