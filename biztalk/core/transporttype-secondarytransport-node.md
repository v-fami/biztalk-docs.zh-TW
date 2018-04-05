---
title: TransportType （SecondaryTransport 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TransportType node [binding file]
ms.assetid: ed66c7ef-32b6-4110-b932-f96a45a29618
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7bb0b9460e6c4689dab169a37a9d6b6c51753598
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transporttype-secondarytransport-node"></a><span data-ttu-id="a4feb-102">TransportType (SecondaryTransport 節點)</span><span class="sxs-lookup"><span data-stu-id="a4feb-102">TransportType (SecondaryTransport Node)</span></span>
<span data-ttu-id="a4feb-103">繫結檔案之 [SecondaryTransport] 節點的 [TransportType] 節點中，包含與隨同繫結檔案所匯出的傳輸關聯之配接器的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="a4feb-103">The TransportType node of the SecondaryTransport node of a binding file contains specific information about the adapter associated with a transport that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transporttype-node"></a><span data-ttu-id="a4feb-104">TransportType 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="a4feb-104">Nodes in the TransportType node</span></span>  
 <span data-ttu-id="a4feb-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="a4feb-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="a4feb-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="a4feb-106">**Name**</span></span>|<span data-ttu-id="a4feb-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="a4feb-107">**Node Type**</span></span>|<span data-ttu-id="a4feb-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="a4feb-108">**Data Type**</span></span>|<span data-ttu-id="a4feb-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="a4feb-109">**Description**</span></span>|<span data-ttu-id="a4feb-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="a4feb-110">**Restrictions**</span></span>|<span data-ttu-id="a4feb-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="a4feb-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="a4feb-112">名稱</span><span class="sxs-lookup"><span data-stu-id="a4feb-112">Name</span></span>|<span data-ttu-id="a4feb-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="a4feb-113">Attribute</span></span>|<span data-ttu-id="a4feb-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="a4feb-114">xs:string</span></span>|<span data-ttu-id="a4feb-115">指定與傳輸關聯之配接器的名稱。</span><span class="sxs-lookup"><span data-stu-id="a4feb-115">Specifies the name of the adapter associated with the transport.</span></span>|<span data-ttu-id="a4feb-116">不需要</span><span class="sxs-lookup"><span data-stu-id="a4feb-116">Not required</span></span>|<span data-ttu-id="a4feb-117">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="a4feb-117">Default value: empty</span></span>|  
|<span data-ttu-id="a4feb-118">Capabilities</span><span class="sxs-lookup"><span data-stu-id="a4feb-118">Capabilities</span></span>|<span data-ttu-id="a4feb-119">Attribute</span><span class="sxs-lookup"><span data-stu-id="a4feb-119">Attribute</span></span>|<span data-ttu-id="a4feb-120">xs:int</span><span class="sxs-lookup"><span data-stu-id="a4feb-120">xs:int</span></span>|<span data-ttu-id="a4feb-121">指定與傳輸關聯之配接器的功能。</span><span class="sxs-lookup"><span data-stu-id="a4feb-121">Specifies the capabilities of the adapter associated with the transport.</span></span>|<span data-ttu-id="a4feb-122">Required</span><span class="sxs-lookup"><span data-stu-id="a4feb-122">Required</span></span>|<span data-ttu-id="a4feb-123">預設值：無</span><span class="sxs-lookup"><span data-stu-id="a4feb-123">Default value: none</span></span><br /><br /> <span data-ttu-id="a4feb-124">可能的值包含 [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) 列舉中可用的值。</span><span class="sxs-lookup"><span data-stu-id="a4feb-124">Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) enumeration.</span></span>|  
|<span data-ttu-id="a4feb-125">ConfigurationClsid</span><span class="sxs-lookup"><span data-stu-id="a4feb-125">ConfigurationClsid</span></span>|<span data-ttu-id="a4feb-126">Attribute</span><span class="sxs-lookup"><span data-stu-id="a4feb-126">Attribute</span></span>|<span data-ttu-id="a4feb-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="a4feb-127">xs:string</span></span>|<span data-ttu-id="a4feb-128">指定與傳輸關聯之配接器的組態 GUID。</span><span class="sxs-lookup"><span data-stu-id="a4feb-128">Specifies the configuration GUID of the adapter associated with the transport.</span></span>|<span data-ttu-id="a4feb-129">不需要</span><span class="sxs-lookup"><span data-stu-id="a4feb-129">Not required</span></span>|<span data-ttu-id="a4feb-130">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="a4feb-130">Default value: empty</span></span>|