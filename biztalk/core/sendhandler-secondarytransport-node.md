---
title: SendHandler （SecondaryTransport 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SendHandler node [binding file]
ms.assetid: 32eb3e87-25ac-461e-9c09-3d6d9bcba3b2
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f5ecdbb1860c9132133835b8928f85b1e0e1cfb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270830"
---
# <a name="sendhandler-secondarytransport-node"></a><span data-ttu-id="0f973-102">SendHandler (SecondaryTransport 節點)</span><span class="sxs-lookup"><span data-stu-id="0f973-102">SendHandler (SecondaryTransport Node)</span></span>
<span data-ttu-id="0f973-103">繫結檔案之 [SecondaryTransport] 節點的 [SendHandler] 節點中，包含與隨同繫結檔案所匯出的傳輸關聯之傳送處理常式的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="0f973-103">The SendHandler node of the SecondaryTransport node of a binding file contains specific information about the send handler associated with a transport that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-sendhandler-node"></a><span data-ttu-id="0f973-104">SendHandler 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="0f973-104">Nodes in the SendHandler node</span></span>  
 <span data-ttu-id="0f973-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="0f973-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="0f973-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="0f973-106">**Name**</span></span>|<span data-ttu-id="0f973-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="0f973-107">**Node Type**</span></span>|<span data-ttu-id="0f973-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="0f973-108">**Data Type**</span></span>|<span data-ttu-id="0f973-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="0f973-109">**Description**</span></span>|<span data-ttu-id="0f973-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="0f973-110">**Restrictions**</span></span>|<span data-ttu-id="0f973-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="0f973-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="0f973-112">名稱</span><span class="sxs-lookup"><span data-stu-id="0f973-112">Name</span></span>|<span data-ttu-id="0f973-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="0f973-113">Attribute</span></span>|<span data-ttu-id="0f973-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="0f973-114">xs:string</span></span>|<span data-ttu-id="0f973-115">指定與傳輸關聯之傳送處理常式的名稱。</span><span class="sxs-lookup"><span data-stu-id="0f973-115">Specifies the name of the send handler associated with the transport.</span></span>|<span data-ttu-id="0f973-116">不需要</span><span class="sxs-lookup"><span data-stu-id="0f973-116">Not required</span></span>|<span data-ttu-id="0f973-117">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="0f973-117">Default value: empty</span></span>|  
|<span data-ttu-id="0f973-118">HostTrusted</span><span class="sxs-lookup"><span data-stu-id="0f973-118">HostTrusted</span></span>|<span data-ttu-id="0f973-119">Attribute</span><span class="sxs-lookup"><span data-stu-id="0f973-119">Attribute</span></span>|<span data-ttu-id="0f973-120">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="0f973-120">xs:boolean</span></span>|<span data-ttu-id="0f973-121">指定與傳送處理常式關聯的主控件是否受到信任。</span><span class="sxs-lookup"><span data-stu-id="0f973-121">Specifies whether the host associated with the send handler is trusted.</span></span>|<span data-ttu-id="0f973-122">Required</span><span class="sxs-lookup"><span data-stu-id="0f973-122">Required</span></span>|<span data-ttu-id="0f973-123">預設值：無</span><span class="sxs-lookup"><span data-stu-id="0f973-123">Default value: none</span></span><br /><br /> <span data-ttu-id="0f973-124">設定為**true**主控件受到信任，否則設為**false**。</span><span class="sxs-lookup"><span data-stu-id="0f973-124">Set to **true** if host is trusted, otherwise set to **false**.</span></span>|  
|[<span data-ttu-id="0f973-125">TransportType （SendHandler 節點）</span><span class="sxs-lookup"><span data-stu-id="0f973-125">TransportType (SendHandler Node)</span></span>](../core/transporttype-sendhandler-node.md)|<span data-ttu-id="0f973-126">記錄</span><span class="sxs-lookup"><span data-stu-id="0f973-126">Record</span></span>|<span data-ttu-id="0f973-127">ProtocolType (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="0f973-127">ProtocolType (ComplexType)</span></span>|<span data-ttu-id="0f973-128">指定傳輸類型，這也是用於此傳送處理常式的配接器名稱。</span><span class="sxs-lookup"><span data-stu-id="0f973-128">Specifies the transport type, which is also the name of the adapter used with this send handler.</span></span>|<span data-ttu-id="0f973-129">Required</span><span class="sxs-lookup"><span data-stu-id="0f973-129">Required</span></span>|<span data-ttu-id="0f973-130">預設值：無</span><span class="sxs-lookup"><span data-stu-id="0f973-130">Default value: none</span></span>|