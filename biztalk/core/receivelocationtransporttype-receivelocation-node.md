---
title: "ReceiveLocationTransportType （ReceiveLocation 節點） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ReceiveLocationTransportType node [binding file]
ms.assetid: 375076c3-d5e6-4c25-b054-b452e29717e0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d0eae3e2c4fd9f5f668cb12ffd630640b1b63c74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receivelocationtransporttype-receivelocation-node"></a><span data-ttu-id="d934f-102">ReceiveLocationTransportType (ReceiveLocation 節點)</span><span class="sxs-lookup"><span data-stu-id="d934f-102">ReceiveLocationTransportType (ReceiveLocation Node)</span></span>
<span data-ttu-id="d934f-103">繫結檔案的 [ReceiveLocation] 節點的 [ReceiveLocationTransportType] 節點中，包含與隨同繫結檔案所匯出的傳輸關聯之配接器的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="d934f-103">The ReceiveLocationTransportType node of the ReceiveLocation node of a binding file contains specific information about the adapter associated with a transport that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-receivelocationtransporttype-node"></a><span data-ttu-id="d934f-104">ReceiveLocationTransportType 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="d934f-104">Nodes in the ReceiveLocationTransportType node</span></span>  
 <span data-ttu-id="d934f-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="d934f-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="d934f-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d934f-106">**Name**</span></span>|<span data-ttu-id="d934f-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="d934f-107">**Node Type**</span></span>|<span data-ttu-id="d934f-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="d934f-108">**Data Type**</span></span>|<span data-ttu-id="d934f-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="d934f-109">**Description**</span></span>|<span data-ttu-id="d934f-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="d934f-110">**Restrictions**</span></span>|<span data-ttu-id="d934f-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="d934f-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="d934f-112">名稱</span><span class="sxs-lookup"><span data-stu-id="d934f-112">Name</span></span>|<span data-ttu-id="d934f-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="d934f-113">Attribute</span></span>|<span data-ttu-id="d934f-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="d934f-114">xs:string</span></span>|<span data-ttu-id="d934f-115">指定與傳輸關聯之配接器的名稱。</span><span class="sxs-lookup"><span data-stu-id="d934f-115">Specifies the name of the adapter associated with the transport.</span></span>|<span data-ttu-id="d934f-116">不需要</span><span class="sxs-lookup"><span data-stu-id="d934f-116">Not required</span></span>|<span data-ttu-id="d934f-117">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="d934f-117">Default value: empty</span></span>|  
|<span data-ttu-id="d934f-118">Capabilities</span><span class="sxs-lookup"><span data-stu-id="d934f-118">Capabilities</span></span>|<span data-ttu-id="d934f-119">Attribute</span><span class="sxs-lookup"><span data-stu-id="d934f-119">Attribute</span></span>|<span data-ttu-id="d934f-120">xs:int</span><span class="sxs-lookup"><span data-stu-id="d934f-120">xs:int</span></span>|<span data-ttu-id="d934f-121">指定與傳輸關聯之配接器的功能。</span><span class="sxs-lookup"><span data-stu-id="d934f-121">Specifies the capabilities of the adapter associated with the transport.</span></span>|<span data-ttu-id="d934f-122">Required</span><span class="sxs-lookup"><span data-stu-id="d934f-122">Required</span></span>|<span data-ttu-id="d934f-123">預設值：無</span><span class="sxs-lookup"><span data-stu-id="d934f-123">Default value: none</span></span><br /><br /> <span data-ttu-id="d934f-124">可能的值包含 [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) 列舉中可用的值。</span><span class="sxs-lookup"><span data-stu-id="d934f-124">Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) enumeration.</span></span>|  
|<span data-ttu-id="d934f-125">ConfigurationClsid</span><span class="sxs-lookup"><span data-stu-id="d934f-125">ConfigurationClsid</span></span>|<span data-ttu-id="d934f-126">Attribute</span><span class="sxs-lookup"><span data-stu-id="d934f-126">Attribute</span></span>|<span data-ttu-id="d934f-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="d934f-127">xs:string</span></span>|<span data-ttu-id="d934f-128">指定與傳輸關聯之配接器的組態 GUID。</span><span class="sxs-lookup"><span data-stu-id="d934f-128">Specifies the configuration GUID of the adapter associated with the transport.</span></span>|<span data-ttu-id="d934f-129">不需要</span><span class="sxs-lookup"><span data-stu-id="d934f-129">Not required</span></span>|<span data-ttu-id="d934f-130">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="d934f-130">Default value: empty</span></span>|