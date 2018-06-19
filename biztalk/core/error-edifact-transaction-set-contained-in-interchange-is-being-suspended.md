---
title: 在剖析期間發生錯誤。 Edifact 交易集 （不含群組） 的交換中所含處於暫停狀態，錯誤如下 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 901fef68-4649-480a-997c-b061d7d069d6
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2dc5633917c708f457f11fc824997fa7eb6d4c59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240230"
---
# <a name="error-encountered-during-parsing-the-edifact-transaction-set-contained-in-interchange-without-group-is-being-suspended-with-following-errors"></a><span data-ttu-id="77c3b-103">在剖析期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="77c3b-103">Error encountered during parsing.</span></span> <span data-ttu-id="77c3b-104">Edifact 交易集 （不含群組） 的交換中所含處於暫停狀態，錯誤如下</span><span class="sxs-lookup"><span data-stu-id="77c3b-104">The Edifact transaction set contained in interchange (without group) is being suspended with following errors</span></span>
## <a name="details"></a><span data-ttu-id="77c3b-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="77c3b-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77c3b-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="77c3b-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="77c3b-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="77c3b-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="77c3b-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="77c3b-108">Event ID</span></span>|-|  
|<span data-ttu-id="77c3b-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="77c3b-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="77c3b-110">EDI</span><span class="sxs-lookup"><span data-stu-id="77c3b-110"> EDI</span></span>|  
|<span data-ttu-id="77c3b-111">元件</span><span class="sxs-lookup"><span data-stu-id="77c3b-111">Component</span></span>|<span data-ttu-id="77c3b-112">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="77c3b-112">EDI Engine</span></span>|  
|<span data-ttu-id="77c3b-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="77c3b-113">Symbolic Name</span></span>|<span data-ttu-id="77c3b-114">EfactTransactionSetReceiveErrorWithoutGroup</span><span class="sxs-lookup"><span data-stu-id="77c3b-114">EfactTransactionSetReceiveErrorWithoutGroup</span></span>|  
|<span data-ttu-id="77c3b-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="77c3b-115">Message Text</span></span>|<span data-ttu-id="77c3b-116">在剖析期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="77c3b-116">Error encountered during parsing.</span></span> <span data-ttu-id="77c3b-117">Edifact 交易集識別碼為 '{0}' 中 （不含群組） 的交換 id '{1}'，寄件者識別碼為 '{2}'，與包含收件者 id '{3}' 處於暫停狀態的下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="77c3b-117">The Edifact transaction set with id '{0}' contained in interchange (without group) with id '{1}', with sender id '{2}', receiver id '{3}' is being suspended with following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="77c3b-118">說明</span><span class="sxs-lookup"><span data-stu-id="77c3b-118">Explanation</span></span>  
 <span data-ttu-id="77c3b-119">這個錯誤/警告/資訊事件表示，由於交換中的已識別交易集發生所述的錯誤，因此 EDI 接收管線在剖析不含群組的內送 EDIFACT 交換時遇到錯誤。</span><span class="sxs-lookup"><span data-stu-id="77c3b-119">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming EDIFACT interchange without a group because of the stated errors with the identified transaction set in the interchange.</span></span> <span data-ttu-id="77c3b-120">請注意，在交換中的群組不是交易集。</span><span class="sxs-lookup"><span data-stu-id="77c3b-120">Note that the transaction set is not in a group in the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="77c3b-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="77c3b-121">User Action</span></span>  
 <span data-ttu-id="77c3b-122">若要解決這個錯誤，錯誤訊息中使用的資訊中的交易集識別錯誤，，然後決定產品說明中的問題解決方法。</span><span class="sxs-lookup"><span data-stu-id="77c3b-122">To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution in the product help.</span></span>