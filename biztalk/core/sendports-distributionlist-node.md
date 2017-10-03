---
title: "SendPorts （DistributionList 節點） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SendPorts node [binding file]
ms.assetid: 9cb645fa-cb9c-44eb-9f98-2fc507b2be67
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9eaf692bd61913e604731fc2e2cea373fd31f48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sendports-distributionlist-node"></a><span data-ttu-id="e610f-102">SendPorts (DistributionList 節點)</span><span class="sxs-lookup"><span data-stu-id="e610f-102">SendPorts (DistributionList Node)</span></span>
<span data-ttu-id="e610f-103">繫結檔案之 DistributionList 節點的 SendPorts 節點是通訊群組清單中傳送埠參考的容器節點。</span><span class="sxs-lookup"><span data-stu-id="e610f-103">The SendPorts node of the DistributionList node of a binding file is the container node for the send port references in the distribution list.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e610f-104">通訊群組清單在 BizTalk 系統管理員中稱為傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="e610f-104">A distribution list is referred to as a send port group in the BizTalk Administrator.</span></span>  
  
## <a name="nodes-in-the-sendports-node"></a><span data-ttu-id="e610f-105">SendPorts 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="e610f-105">Nodes in the SendPorts node</span></span>  
 <span data-ttu-id="e610f-106">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="e610f-106">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="e610f-107">**名稱**</span><span class="sxs-lookup"><span data-stu-id="e610f-107">**Name**</span></span>|<span data-ttu-id="e610f-108">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="e610f-108">**Node Type**</span></span>|<span data-ttu-id="e610f-109">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="e610f-109">**Data Type**</span></span>|<span data-ttu-id="e610f-110">**說明**</span><span class="sxs-lookup"><span data-stu-id="e610f-110">**Description**</span></span>|<span data-ttu-id="e610f-111">**限制**</span><span class="sxs-lookup"><span data-stu-id="e610f-111">**Restrictions**</span></span>|<span data-ttu-id="e610f-112">**註解**</span><span class="sxs-lookup"><span data-stu-id="e610f-112">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="e610f-113">SendPortRef</span><span class="sxs-lookup"><span data-stu-id="e610f-113">SendPortRef</span></span>](../core/sendportref-sendports-node.md)|<span data-ttu-id="e610f-114">記錄</span><span class="sxs-lookup"><span data-stu-id="e610f-114">Record</span></span>|<span data-ttu-id="e610f-115">SendPortRef (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="e610f-115">SendPortRef (ComplexType)</span></span>|<span data-ttu-id="e610f-116">傳送埠參考的容器節點 (此傳送埠為通訊群組清單所產生)。</span><span class="sxs-lookup"><span data-stu-id="e610f-116">Container node for a reference to a send port made by the distribution list.</span></span>|<span data-ttu-id="e610f-117">不需要</span><span class="sxs-lookup"><span data-stu-id="e610f-117">Not required</span></span>|<span data-ttu-id="e610f-118">預設值：無</span><span class="sxs-lookup"><span data-stu-id="e610f-118">Default value: none</span></span>|