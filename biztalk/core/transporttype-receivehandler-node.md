---
title: TransportType （ReceiveHandler 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TransportType node [binding file]
ms.assetid: d893b3ac-8e2c-41fb-926c-cea23f6f93b3
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df0e041a322b8bb9a144b9ea2bdab5ebb58ac01e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transporttype-receivehandler-node"></a><span data-ttu-id="6ca52-102">TransportType (ReceiveHandler 節點)</span><span class="sxs-lookup"><span data-stu-id="6ca52-102">TransportType (ReceiveHandler Node)</span></span>
<span data-ttu-id="6ca52-103">繫結檔案之 [ReceiveHandler] 節點的 [TransportType] 節點中，包含與隨同繫結檔案一起匯出的接收處理常式有關聯之配接器的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="6ca52-103">The TransportType node of the ReceiveHandler node of a binding file contains specific information about the adapter associated with a receive handler that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transporttype-node"></a><span data-ttu-id="6ca52-104">TransportType 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="6ca52-104">Nodes in the TransportType node</span></span>  
 <span data-ttu-id="6ca52-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="6ca52-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="6ca52-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="6ca52-106">**Name**</span></span>|<span data-ttu-id="6ca52-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="6ca52-107">**Node Type**</span></span>|<span data-ttu-id="6ca52-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="6ca52-108">**Data Type**</span></span>|<span data-ttu-id="6ca52-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="6ca52-109">**Description**</span></span>|<span data-ttu-id="6ca52-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="6ca52-110">**Restrictions**</span></span>|<span data-ttu-id="6ca52-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="6ca52-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="6ca52-112">名稱</span><span class="sxs-lookup"><span data-stu-id="6ca52-112">Name</span></span>|<span data-ttu-id="6ca52-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="6ca52-113">Attribute</span></span>|<span data-ttu-id="6ca52-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="6ca52-114">xs:string</span></span>|<span data-ttu-id="6ca52-115">指定與接收處理常式關聯之配接器的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ca52-115">Specifies the name of the adapter associated with the receive handler.</span></span>|<span data-ttu-id="6ca52-116">非必要</span><span class="sxs-lookup"><span data-stu-id="6ca52-116">Not Required</span></span>|<span data-ttu-id="6ca52-117">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="6ca52-117">Default value: empty</span></span>|  
|<span data-ttu-id="6ca52-118">Capabilities</span><span class="sxs-lookup"><span data-stu-id="6ca52-118">Capabilities</span></span>|<span data-ttu-id="6ca52-119">Attribute</span><span class="sxs-lookup"><span data-stu-id="6ca52-119">Attribute</span></span>|<span data-ttu-id="6ca52-120">xs:int</span><span class="sxs-lookup"><span data-stu-id="6ca52-120">xs:int</span></span>|<span data-ttu-id="6ca52-121">指定與接收處理常式關聯之配接器的功能。</span><span class="sxs-lookup"><span data-stu-id="6ca52-121">Specifies the capabilities of the adapter associated with the receive handler.</span></span>|<span data-ttu-id="6ca52-122">Required</span><span class="sxs-lookup"><span data-stu-id="6ca52-122">Required</span></span>|<span data-ttu-id="6ca52-123">預設值：無</span><span class="sxs-lookup"><span data-stu-id="6ca52-123">Default value: none</span></span><br /><br /> <span data-ttu-id="6ca52-124">可能的值包含 [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) 列舉中可用的值。</span><span class="sxs-lookup"><span data-stu-id="6ca52-124">Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) enumeration.</span></span>|  
|<span data-ttu-id="6ca52-125">ConfigurationClsid</span><span class="sxs-lookup"><span data-stu-id="6ca52-125">ConfigurationClsid</span></span>|<span data-ttu-id="6ca52-126">Attribute</span><span class="sxs-lookup"><span data-stu-id="6ca52-126">Attribute</span></span>|<span data-ttu-id="6ca52-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="6ca52-127">xs:string</span></span>|<span data-ttu-id="6ca52-128">指定與接收處理常式關聯之配接器的組態 GUID。</span><span class="sxs-lookup"><span data-stu-id="6ca52-128">Specifies the configuration GUID of the adapter associated with the receive handler.</span></span>|<span data-ttu-id="6ca52-129">非必要</span><span class="sxs-lookup"><span data-stu-id="6ca52-129">Not Required</span></span>|<span data-ttu-id="6ca52-130">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="6ca52-130">Default value: empty</span></span>|