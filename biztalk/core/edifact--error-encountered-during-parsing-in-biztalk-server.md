---
title: "在剖析期間發生錯誤。 Edifact 交換其中不包含群組發生下列錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6b324fd-f365-41b9-81aa-b6c5c5d3f673
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 550e5ca207bef7fdcb42ffcbd52e114ad3dc95ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-parsing-the-edifact-interchange-which-did-not-contain-a-group-had-the-following-errors"></a><span data-ttu-id="ebe29-103">在剖析期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ebe29-103">Error encountered during parsing.</span></span> <span data-ttu-id="ebe29-104">Edifact 交換其中不包含群組發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="ebe29-104">The Edifact interchange which did not contain a group had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="ebe29-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ebe29-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ebe29-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ebe29-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ebe29-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="ebe29-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ebe29-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ebe29-108">Event ID</span></span>|-|  
|<span data-ttu-id="ebe29-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="ebe29-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ebe29-110">EDI</span><span class="sxs-lookup"><span data-stu-id="ebe29-110"> EDI</span></span>|  
|<span data-ttu-id="ebe29-111">元件</span><span class="sxs-lookup"><span data-stu-id="ebe29-111">Component</span></span>|<span data-ttu-id="ebe29-112">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="ebe29-112">EDI Engine</span></span>|  
|<span data-ttu-id="ebe29-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ebe29-113">Symbolic Name</span></span>|<span data-ttu-id="ebe29-114">EfactFunctionalGroupReceiveErrorWithoutGroup</span><span class="sxs-lookup"><span data-stu-id="ebe29-114">EfactFunctionalGroupReceiveErrorWithoutGroup</span></span>|  
|<span data-ttu-id="ebe29-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ebe29-115">Message Text</span></span>|<span data-ttu-id="ebe29-116">在剖析期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ebe29-116">Error encountered during parsing.</span></span> <span data-ttu-id="ebe29-117">其中不包含群組，交換識別碼為 '{0}'，寄件者識別碼 '{1}'，Edifact 交換接收者識別碼 '{2}' 發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="ebe29-117">The Edifact interchange which did not contain a group, with interchange id '{0}', with sender id '{1}', receiver id '{2}' had the following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ebe29-118">說明</span><span class="sxs-lookup"><span data-stu-id="ebe29-118">Explanation</span></span>  
 <span data-ttu-id="ebe29-119">這個錯誤/警告/資訊事件表示 EDI 接收管線在剖析內送 EDIFACT 交換因為敘述的錯誤不包含群組時，發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ebe29-119">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming EDIFACT interchange that did not contain a group because of the stated errors.</span></span> <span data-ttu-id="ebe29-120">請注意，群組是 EDIFACT 交換的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="ebe29-120">Note that groups are optional in EDIFACT interchanges.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ebe29-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ebe29-121">User Action</span></span>  
 <span data-ttu-id="ebe29-122">若要解決這個錯誤，錯誤訊息中使用的資訊來識別錯誤，然後決定產品說明中的問題解決方法。</span><span class="sxs-lookup"><span data-stu-id="ebe29-122">To resolve this error, use the information in the error message to identify the error and then determine the problem resolution in the product help.</span></span>