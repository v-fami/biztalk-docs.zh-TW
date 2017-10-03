---
title: "找不到對應至批次的商務識別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9baf11-e9c6-482d-a47d-aa99852939bf
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f1027186e5b001d21e08bbabcfc100400a02d5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="could-not-find-business-identities-corresponding-to-batch"></a><span data-ttu-id="70974-102">找不到和批次對應的商務識別</span><span class="sxs-lookup"><span data-stu-id="70974-102">Could not find Business Identities corresponding to batch</span></span>
## <a name="details"></a><span data-ttu-id="70974-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="70974-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="70974-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="70974-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="70974-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="70974-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="70974-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="70974-106">Event ID</span></span>|-|  
|<span data-ttu-id="70974-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="70974-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="70974-108">EDI</span><span class="sxs-lookup"><span data-stu-id="70974-108"> EDI</span></span>|  
|<span data-ttu-id="70974-109">元件</span><span class="sxs-lookup"><span data-stu-id="70974-109">Component</span></span>|<span data-ttu-id="70974-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="70974-110">EDI Engine</span></span>|  
|<span data-ttu-id="70974-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="70974-111">Symbolic Name</span></span>|<span data-ttu-id="70974-112">IdentitiesNotFoundForBatch</span><span class="sxs-lookup"><span data-stu-id="70974-112">IdentitiesNotFoundForBatch</span></span>|  
|<span data-ttu-id="70974-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="70974-113">Message Text</span></span>|<span data-ttu-id="70974-114">找不到和批次 {0} 對應的商務識別。</span><span class="sxs-lookup"><span data-stu-id="70974-114">Could not find Business Identities corresponding to batch {0}.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="70974-115">說明</span><span class="sxs-lookup"><span data-stu-id="70974-115">Explanation</span></span>  
 <span data-ttu-id="70974-116">這個錯誤/警告/資訊事件表示，由於資料不足，因此 BizTalk Server 無法處理批次訊息。</span><span class="sxs-lookup"><span data-stu-id="70974-116">This Error/Warning/Information event indicates BizTalk Server was not able to process a batch message because of insufficient data.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="70974-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="70974-117">User Action</span></span>  
 <span data-ttu-id="70974-118">若要解決這個錯誤，請確認含指定識別碼的批次存在內含協議的 [協議] 屬性中，同時也已為協議指定合適的商務識別。</span><span class="sxs-lookup"><span data-stu-id="70974-118">To resolve this error, ensure that a batch with the given Id is present in the Agreement properties of the containing Agreement and proper business identities are specified for the agreement.</span></span>