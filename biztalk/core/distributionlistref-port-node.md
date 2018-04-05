---
title: DistributionListRef （連接埠節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DistributionListRef node [binding file]
ms.assetid: 5d0d0121-1bcc-4c26-a1a3-8937ac7c282a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 665b8c2115c5c4681f7cff057481b6ce7da320ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="distributionlistref-port-node"></a><span data-ttu-id="20db9-102">DistributionListRef (連接埠節點)</span><span class="sxs-lookup"><span data-stu-id="20db9-102">DistributionListRef (Port Node)</span></span>
<span data-ttu-id="20db9-103">繫結檔案之 [連接埠] 節點的 [DistributionListRef] 節點包含由服務所參考之通訊群組清單的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="20db9-103">The DistributionListRef node of the Port node of a binding file contains information about a distribution list that is referenced by a service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20db9-104">通訊群組清單在 BizTalk Server「管理主控台」中也稱為傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="20db9-104">Distribution lists are referred to as send port groups in the BizTalk Server Administration Console.</span></span>  
  
## <a name="nodes-in-the-distributionlistref-node"></a><span data-ttu-id="20db9-105">DistributionListRef 節點中的節點</span><span class="sxs-lookup"><span data-stu-id="20db9-105">Nodes in the DistributionListRef node</span></span>  
 <span data-ttu-id="20db9-106">下表列出可以為繫結檔案中的這個節點設定的屬性：</span><span class="sxs-lookup"><span data-stu-id="20db9-106">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="20db9-107">**名稱**</span><span class="sxs-lookup"><span data-stu-id="20db9-107">**Name**</span></span>|<span data-ttu-id="20db9-108">**節點類型**</span><span class="sxs-lookup"><span data-stu-id="20db9-108">**Node Type**</span></span>|<span data-ttu-id="20db9-109">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="20db9-109">**Data Type**</span></span>|<span data-ttu-id="20db9-110">**說明**</span><span class="sxs-lookup"><span data-stu-id="20db9-110">**Description**</span></span>|<span data-ttu-id="20db9-111">**限制**</span><span class="sxs-lookup"><span data-stu-id="20db9-111">**Restrictions**</span></span>|<span data-ttu-id="20db9-112">**註解**</span><span class="sxs-lookup"><span data-stu-id="20db9-112">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="20db9-113">名稱</span><span class="sxs-lookup"><span data-stu-id="20db9-113">Name</span></span>|<span data-ttu-id="20db9-114">Attribute</span><span class="sxs-lookup"><span data-stu-id="20db9-114">Attribute</span></span>|<span data-ttu-id="20db9-115">xs:string</span><span class="sxs-lookup"><span data-stu-id="20db9-115">xs:string</span></span>|<span data-ttu-id="20db9-116">指定由服務所參考的通訊群組清單名稱。</span><span class="sxs-lookup"><span data-stu-id="20db9-116">Specifies the name of a distribution list that is referenced by a service.</span></span>|<span data-ttu-id="20db9-117">不需要</span><span class="sxs-lookup"><span data-stu-id="20db9-117">Not required</span></span>|<span data-ttu-id="20db9-118">預設值：空白</span><span class="sxs-lookup"><span data-stu-id="20db9-118">Default value: empty</span></span>|