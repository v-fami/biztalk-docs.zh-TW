---
title: 主機 （服務節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Host node [binding file]
ms.assetid: 597522db-0336-43b1-b464-d17cffbf25be
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9c70c23105a8d2f2ebe389b22ddf910b4166994
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246558"
---
# <a name="host-service-node"></a><span data-ttu-id="17926-102">主控件 (服務節點)</span><span class="sxs-lookup"><span data-stu-id="17926-102">Host (Service Node)</span></span>
<span data-ttu-id="17926-103">繫結檔案之 [服務] 節點的 [主控件] 節點，說明與該繫結檔案匯出之服務關聯的主控件。</span><span class="sxs-lookup"><span data-stu-id="17926-103">The Host node of the Service node of a binding file describes the host associated with the service that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-host-node"></a><span data-ttu-id="17926-104">主控件節點中的節點</span><span class="sxs-lookup"><span data-stu-id="17926-104">Nodes in the Host node</span></span>  
 <span data-ttu-id="17926-105">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="17926-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="17926-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="17926-106">**Name**</span></span>|<span data-ttu-id="17926-107">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="17926-107">**Node Type**</span></span>|<span data-ttu-id="17926-108">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="17926-108">**Data Type**</span></span>|<span data-ttu-id="17926-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="17926-109">**Description**</span></span>|<span data-ttu-id="17926-110">**限制**</span><span class="sxs-lookup"><span data-stu-id="17926-110">**Restrictions**</span></span>|<span data-ttu-id="17926-111">**註解**</span><span class="sxs-lookup"><span data-stu-id="17926-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="17926-112">名稱</span><span class="sxs-lookup"><span data-stu-id="17926-112">Name</span></span>|<span data-ttu-id="17926-113">Attribute</span><span class="sxs-lookup"><span data-stu-id="17926-113">Attribute</span></span>|<span data-ttu-id="17926-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="17926-114">xs:string</span></span>|<span data-ttu-id="17926-115">指定主控件的名稱。</span><span class="sxs-lookup"><span data-stu-id="17926-115">Specifies the name of the host.</span></span>|<span data-ttu-id="17926-116">不需要</span><span class="sxs-lookup"><span data-stu-id="17926-116">Not required</span></span>|<span data-ttu-id="17926-117">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="17926-117">Default value: empty</span></span>|  
|<span data-ttu-id="17926-118">NTGroupName</span><span class="sxs-lookup"><span data-stu-id="17926-118">NTGroupName</span></span>|<span data-ttu-id="17926-119">Attribute</span><span class="sxs-lookup"><span data-stu-id="17926-119">Attribute</span></span>|<span data-ttu-id="17926-120">xs:string</span><span class="sxs-lookup"><span data-stu-id="17926-120">xs:string</span></span>|<span data-ttu-id="17926-121">指定與主控件關聯的 Windows NT 群組名稱。</span><span class="sxs-lookup"><span data-stu-id="17926-121">Specifies the Windows NT Group name associated with the host.</span></span>|<span data-ttu-id="17926-122">不需要</span><span class="sxs-lookup"><span data-stu-id="17926-122">Not required</span></span>|<span data-ttu-id="17926-123">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="17926-123">Default value: empty</span></span>|  
|<span data-ttu-id="17926-124">類型</span><span class="sxs-lookup"><span data-stu-id="17926-124">Type</span></span>|<span data-ttu-id="17926-125">Attribute</span><span class="sxs-lookup"><span data-stu-id="17926-125">Attribute</span></span>|<span data-ttu-id="17926-126">xs:int</span><span class="sxs-lookup"><span data-stu-id="17926-126">xs:int</span></span>|<span data-ttu-id="17926-127">指定主控件類型為「內含式」或「外掛式」。</span><span class="sxs-lookup"><span data-stu-id="17926-127">Specifies the host type as in process or isolated.</span></span>|<span data-ttu-id="17926-128">Required</span><span class="sxs-lookup"><span data-stu-id="17926-128">Required</span></span>|<span data-ttu-id="17926-129">預設值：無</span><span class="sxs-lookup"><span data-stu-id="17926-129">Default value: none</span></span><br /><br /> <span data-ttu-id="17926-130">可能的值所述[Microsoft.BizTalk.ExplorerOM.HostType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.hosttype.aspx)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="17926-130">Possible values are described in the [Microsoft.BizTalk.ExplorerOM.HostType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.hosttype.aspx) enumeration.</span></span>|  
|<span data-ttu-id="17926-131">Trusted</span><span class="sxs-lookup"><span data-stu-id="17926-131">Trusted</span></span>|<span data-ttu-id="17926-132">Attribute</span><span class="sxs-lookup"><span data-stu-id="17926-132">Attribute</span></span>|<span data-ttu-id="17926-133">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="17926-133">xs:boolean</span></span>|<span data-ttu-id="17926-134">指定是否可以信任 BizTalk 主控件進行驗證資訊的收集。</span><span class="sxs-lookup"><span data-stu-id="17926-134">Specifies whether the BizTalk host can be trusted to collect authentication information.</span></span>|<span data-ttu-id="17926-135">Required</span><span class="sxs-lookup"><span data-stu-id="17926-135">Required</span></span>|<span data-ttu-id="17926-136">預設值：無</span><span class="sxs-lookup"><span data-stu-id="17926-136">Default value: none</span></span><br /><br /> <span data-ttu-id="17926-137">設定為**true**主機是受信任的否則設為**false**。</span><span class="sxs-lookup"><span data-stu-id="17926-137">Set to **true** if the host is trusted, otherwise set to **false**.</span></span>|