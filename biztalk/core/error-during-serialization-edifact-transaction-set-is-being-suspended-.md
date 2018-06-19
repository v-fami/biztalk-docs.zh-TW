---
title: Edifact 交易集包含在交換錯誤 |Microsoft 文件
description: 在序列化期間發生錯誤。 Edifact 交易集 （不含群組） 的交換中所含處於暫停狀態，錯誤如下
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a0a33ac-d83e-495c-ba75-88c15ad7cfcd
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67f089e49941ffec7d3392b3bc35edcbc4eefec5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241470"
---
# <a name="edifact-transaction-set-is-suspended-error-and-details"></a><span data-ttu-id="ec252-104">Edifact 交易集是已暫停的錯誤和詳細資料</span><span class="sxs-lookup"><span data-stu-id="ec252-104">Edifact transaction set is suspended error and details</span></span>

`Error encountered during serialization. The Edifact transaction set contained in interchange (without group) is being suspended with following errors`

## <a name="details"></a><span data-ttu-id="ec252-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ec252-105">Details</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="ec252-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ec252-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ec252-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="ec252-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ec252-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ec252-108">Event ID</span></span>|-|  
|<span data-ttu-id="ec252-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="ec252-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ec252-110">EDI</span><span class="sxs-lookup"><span data-stu-id="ec252-110"> EDI</span></span>|  
|<span data-ttu-id="ec252-111">元件</span><span class="sxs-lookup"><span data-stu-id="ec252-111">Component</span></span>|<span data-ttu-id="ec252-112">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="ec252-112">EDI Engine</span></span>|  
|<span data-ttu-id="ec252-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ec252-113">Symbolic Name</span></span>|<span data-ttu-id="ec252-114">EfactTransactionSetSendErrorWithoutGroup</span><span class="sxs-lookup"><span data-stu-id="ec252-114">EfactTransactionSetSendErrorWithoutGroup</span></span>|  
|<span data-ttu-id="ec252-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ec252-115">Message Text</span></span>|<span data-ttu-id="ec252-116">在序列化期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ec252-116">Error encountered during serialization.</span></span> <span data-ttu-id="ec252-117">Edifact 交易集識別碼為 '{0}' 中 （不含群組） 的交換 id '{1}'，寄件者識別碼為 '{2}'，與包含收件者 id '{3}' 處於暫停狀態的下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="ec252-117">The Edifact transaction set with id '{0}' contained in interchange (without group)  with id '{1}', with sender id '{2}', receiver id '{3}' is being suspended with following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ec252-118">說明</span><span class="sxs-lookup"><span data-stu-id="ec252-118">Explanation</span></span>  
 <span data-ttu-id="ec252-119">這個錯誤/警告/資訊事件表示 EDI 傳送管線在外寄 EDIFACT 交換序列化因為識別的交易集與敘述的錯誤時，會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ec252-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing EDIFACT interchange because of the stated errors with the identified transaction set.</span></span> <span data-ttu-id="ec252-120">請注意，在交換中的群組不是交易集。</span><span class="sxs-lookup"><span data-stu-id="ec252-120">Note that the transaction set is not in a group in the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ec252-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ec252-121">User Action</span></span>  
 <span data-ttu-id="ec252-122">若要解決這個錯誤，錯誤訊息中使用的資訊來識別交易集的錯誤並再判斷解決問題。</span><span class="sxs-lookup"><span data-stu-id="ec252-122">To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution.</span></span>