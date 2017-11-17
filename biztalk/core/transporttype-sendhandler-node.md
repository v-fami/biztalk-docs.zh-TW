---
title: "TransportType （SendHandler 節點） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TransportType node [binding file]
ms.assetid: ee87a409-33dd-4111-ba6a-ead3bacc80aa
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3525b78fa9812c1e4fa8690a622f9b8cccce8d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transporttype-sendhandler-node"></a><span data-ttu-id="0d821-102">TransportType (SendHandler 節點)</span><span class="sxs-lookup"><span data-stu-id="0d821-102">TransportType (SendHandler Node)</span></span>
<span data-ttu-id="0d821-103">繫結檔案之 SendHandler 節點的 TransportType 節點，包含與該繫結檔案一起匯出之傳輸有關之配接器的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="0d821-103">The TransportType node of the SendHandler node of a binding file contains specific information about the adapter associated with a send handler that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transporttype-node"></a><span data-ttu-id="0d821-104">TransportType 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="0d821-104">Nodes in the TransportType node</span></span>  
 <span data-ttu-id="0d821-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="0d821-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="0d821-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="0d821-106">**Name**</span></span>|<span data-ttu-id="0d821-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="0d821-107">**Node Type**</span></span>|<span data-ttu-id="0d821-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="0d821-108">**Data Type**</span></span>|<span data-ttu-id="0d821-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="0d821-109">**Description**</span></span>|<span data-ttu-id="0d821-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="0d821-110">**Restrictions**</span></span>|<span data-ttu-id="0d821-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="0d821-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="0d821-112">名稱</span><span class="sxs-lookup"><span data-stu-id="0d821-112">Name</span></span>|<span data-ttu-id="0d821-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="0d821-113">Attribute</span></span>|<span data-ttu-id="0d821-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="0d821-114">xs:string</span></span>|<span data-ttu-id="0d821-115">指定與傳送處理常式關聯之配接器的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d821-115">Specifies the name of the adapter associated with the send handler.</span></span>|<span data-ttu-id="0d821-116">不需要</span><span class="sxs-lookup"><span data-stu-id="0d821-116">Not required</span></span>|<span data-ttu-id="0d821-117">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="0d821-117">Default value: empty</span></span>|  
|<span data-ttu-id="0d821-118">Capabilities</span><span class="sxs-lookup"><span data-stu-id="0d821-118">Capabilities</span></span>|<span data-ttu-id="0d821-119">Attribute</span><span class="sxs-lookup"><span data-stu-id="0d821-119">Attribute</span></span>|<span data-ttu-id="0d821-120">xs:int</span><span class="sxs-lookup"><span data-stu-id="0d821-120">xs:int</span></span>|<span data-ttu-id="0d821-121">指定與傳送處理常式關聯之配接器的功能。</span><span class="sxs-lookup"><span data-stu-id="0d821-121">Specifies the capabilities of the adapter associated with the send handler.</span></span>|<span data-ttu-id="0d821-122">Required</span><span class="sxs-lookup"><span data-stu-id="0d821-122">Required</span></span>|<span data-ttu-id="0d821-123">預設值：無</span><span class="sxs-lookup"><span data-stu-id="0d821-123">Default value: none</span></span><br /><br /> <span data-ttu-id="0d821-124">可能的值包含 [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) 列舉中可用的值。</span><span class="sxs-lookup"><span data-stu-id="0d821-124">Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) enumeration.</span></span>|  
|<span data-ttu-id="0d821-125">ConfigurationClsid</span><span class="sxs-lookup"><span data-stu-id="0d821-125">ConfigurationClsid</span></span>|<span data-ttu-id="0d821-126">Attribute</span><span class="sxs-lookup"><span data-stu-id="0d821-126">Attribute</span></span>|<span data-ttu-id="0d821-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="0d821-127">xs:string</span></span>|<span data-ttu-id="0d821-128">指定與傳送處理常式關聯之配接器的組態 GUID。</span><span class="sxs-lookup"><span data-stu-id="0d821-128">Specifies the configuration GUID of the adapter associated with the send handler.</span></span>|<span data-ttu-id="0d821-129">不需要</span><span class="sxs-lookup"><span data-stu-id="0d821-129">Not required</span></span>|<span data-ttu-id="0d821-130">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="0d821-130">Default value: empty</span></span>|