---
title: ReceiveHandler （ReceiveLocation 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ReceiveHandler node [binding file]
ms.assetid: dd105052-ec71-4762-aa74-e8cdb806a6bf
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e865886624731414f979c77f3f2e898e417c8b11
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receivehandler-receivelocation-node"></a><span data-ttu-id="95556-102">ReceiveHandler (接收位置節點)</span><span class="sxs-lookup"><span data-stu-id="95556-102">ReceiveHandler (ReceiveLocation Node)</span></span>
<span data-ttu-id="95556-103">繫結檔案的 [接收位置] 節點的 [ReceiveHandler] 節點中，包含與隨同繫結檔案所匯出的傳輸關聯之接收處理函式的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="95556-103">The ReceiveHandler node of the ReceiveLocation node of a binding file contains specific information about the receive handler associated with a transport that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-receivehandler-node"></a><span data-ttu-id="95556-104">ReceiveHandler 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="95556-104">Nodes in the ReceiveHandler node</span></span>  
 <span data-ttu-id="95556-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="95556-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="95556-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="95556-106">**Name**</span></span>|<span data-ttu-id="95556-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="95556-107">**Node Type**</span></span>|<span data-ttu-id="95556-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="95556-108">**Data Type**</span></span>|<span data-ttu-id="95556-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="95556-109">**Description**</span></span>|<span data-ttu-id="95556-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="95556-110">**Restrictions**</span></span>|<span data-ttu-id="95556-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="95556-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="95556-112">名稱</span><span class="sxs-lookup"><span data-stu-id="95556-112">Name</span></span>|<span data-ttu-id="95556-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="95556-113">Attribute</span></span>|<span data-ttu-id="95556-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="95556-114">xs:string</span></span>|<span data-ttu-id="95556-115">指定與傳輸關聯之接收處理常式的名稱。</span><span class="sxs-lookup"><span data-stu-id="95556-115">Specifies the name of the receive handler associated with the transport.</span></span>|<span data-ttu-id="95556-116">不需要</span><span class="sxs-lookup"><span data-stu-id="95556-116">Not required</span></span>|<span data-ttu-id="95556-117">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="95556-117">Default value: empty</span></span>|  
|<span data-ttu-id="95556-118">HostTrusted</span><span class="sxs-lookup"><span data-stu-id="95556-118">HostTrusted</span></span>|<span data-ttu-id="95556-119">Attribute</span><span class="sxs-lookup"><span data-stu-id="95556-119">Attribute</span></span>|<span data-ttu-id="95556-120">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="95556-120">xs:boolean</span></span>|<span data-ttu-id="95556-121">指定與接收處理常式關聯的主控件是否受到信任。</span><span class="sxs-lookup"><span data-stu-id="95556-121">Specifies whether the host associated with the receive handler is trusted.</span></span>|<span data-ttu-id="95556-122">Required</span><span class="sxs-lookup"><span data-stu-id="95556-122">Required</span></span>|<span data-ttu-id="95556-123">預設值：無</span><span class="sxs-lookup"><span data-stu-id="95556-123">Default value: none</span></span><br /><br /> <span data-ttu-id="95556-124">設定為**true**主控件受到信任，否則設為**false**。</span><span class="sxs-lookup"><span data-stu-id="95556-124">Set to **true** if host is trusted, otherwise set to **false**.</span></span>|  
|[<span data-ttu-id="95556-125">TransportType （ReceiveHandler 節點）</span><span class="sxs-lookup"><span data-stu-id="95556-125">TransportType (ReceiveHandler Node)</span></span>](../core/transporttype-receivehandler-node.md)|<span data-ttu-id="95556-126">記錄</span><span class="sxs-lookup"><span data-stu-id="95556-126">Record</span></span>|<span data-ttu-id="95556-127">ProtocolType (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="95556-127">ProtocolType (ComplexType)</span></span>|<span data-ttu-id="95556-128">指定傳輸類型，這也是用於此接收處理常式的配接器名稱。</span><span class="sxs-lookup"><span data-stu-id="95556-128">Specifies the transport type, which is also the name of the adapter used with this receive handler.</span></span>|<span data-ttu-id="95556-129">Required</span><span class="sxs-lookup"><span data-stu-id="95556-129">Required</span></span>|<span data-ttu-id="95556-130">預設值：無</span><span class="sxs-lookup"><span data-stu-id="95556-130">Default value: none</span></span>|