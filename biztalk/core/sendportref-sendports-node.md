---
title: SendPortRef （SendPorts 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SendPortRef node [binding file]
ms.assetid: 6c799b23-a9a4-4686-a04e-0450b4eef889
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9290a535ebcaf0c23097cacbd3412f64c2808f40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sendportref-sendports-node"></a><span data-ttu-id="24a69-102">SendPortRef (SendPorts 節點)</span><span class="sxs-lookup"><span data-stu-id="24a69-102">SendPortRef (SendPorts Node)</span></span>
<span data-ttu-id="24a69-103">繫結檔案之 SendPorts 節點的 SendPortRef 節點會指定通訊群組清單所參考之傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="24a69-103">The SendPortRef node of the SendPorts node of a binding file specifies the name of a send port referenced by a distribution list.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24a69-104">通訊群組清單在 BizTalk 系統管理員中稱為傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="24a69-104">A distribution list is referred to as a send port group in the BizTalk Administrator.</span></span>  
  
## <a name="nodes-in-the-sendportref-node"></a><span data-ttu-id="24a69-105">SendPortRef 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="24a69-105">Nodes in the SendPortRef node</span></span>  
 <span data-ttu-id="24a69-106">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="24a69-106">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="24a69-107">**名稱**</span><span class="sxs-lookup"><span data-stu-id="24a69-107">**Name**</span></span>|<span data-ttu-id="24a69-108">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="24a69-108">**Node Type**</span></span>|<span data-ttu-id="24a69-109">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="24a69-109">**Data Type**</span></span>|<span data-ttu-id="24a69-110">**說明**</span><span class="sxs-lookup"><span data-stu-id="24a69-110">**Description**</span></span>|<span data-ttu-id="24a69-111">**限制**</span><span class="sxs-lookup"><span data-stu-id="24a69-111">**Restrictions**</span></span>|<span data-ttu-id="24a69-112">**註解**</span><span class="sxs-lookup"><span data-stu-id="24a69-112">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="24a69-113">名稱</span><span class="sxs-lookup"><span data-stu-id="24a69-113">Name</span></span>|<span data-ttu-id="24a69-114">Attribute</span><span class="sxs-lookup"><span data-stu-id="24a69-114">Attribute</span></span>|<span data-ttu-id="24a69-115">xs:string</span><span class="sxs-lookup"><span data-stu-id="24a69-115">xs:string</span></span>|<span data-ttu-id="24a69-116">指定通訊群組清單所參考之傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="24a69-116">Specifies the name of the send port referenced by the distribution list.</span></span>|<span data-ttu-id="24a69-117">不需要</span><span class="sxs-lookup"><span data-stu-id="24a69-117">Not required</span></span>|<span data-ttu-id="24a69-118">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="24a69-118">Default value: empty</span></span>|