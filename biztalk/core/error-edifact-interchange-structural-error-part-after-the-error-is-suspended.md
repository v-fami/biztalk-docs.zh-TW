---
title: 交換有結構的錯誤。 錯誤處於暫停狀態後的部分 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9071825d-7b90-42bf-bcf9-2a15ae36086d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a028608e9843ee40c26bc7e8b158d97552a58163
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241294"
---
# <a name="the-interchange-had-structural-error-the-part-after-the-error-is-being-suspended"></a><span data-ttu-id="afdad-103">交換有結構的錯誤。</span><span class="sxs-lookup"><span data-stu-id="afdad-103">The interchange had structural error.</span></span> <span data-ttu-id="afdad-104">錯誤後的部分正在遭到擱置</span><span class="sxs-lookup"><span data-stu-id="afdad-104">The part after the error is being suspended</span></span>
## <a name="details"></a><span data-ttu-id="afdad-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="afdad-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="afdad-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="afdad-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="afdad-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="afdad-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="afdad-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="afdad-108">Event ID</span></span>|-|  
|<span data-ttu-id="afdad-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="afdad-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="afdad-110">EDI</span><span class="sxs-lookup"><span data-stu-id="afdad-110"> EDI</span></span>|  
|<span data-ttu-id="afdad-111">元件</span><span class="sxs-lookup"><span data-stu-id="afdad-111">Component</span></span>|<span data-ttu-id="afdad-112">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="afdad-112">EDI Engine</span></span>|  
|<span data-ttu-id="afdad-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="afdad-113">Symbolic Name</span></span>|<span data-ttu-id="afdad-114">EfactInterchangeStructuralError</span><span class="sxs-lookup"><span data-stu-id="afdad-114">EfactInterchangeStructuralError</span></span>|  
|<span data-ttu-id="afdad-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="afdad-115">Message Text</span></span>|<span data-ttu-id="afdad-116">交換傳送者識別碼 '{1}' 識別碼為 '{0}'、 接收者識別碼 '{2}' 有結構的錯誤。</span><span class="sxs-lookup"><span data-stu-id="afdad-116">The interchange with id '{0}', with sender id '{1}', receiver id '{2}' had structural error.</span></span> <span data-ttu-id="afdad-117">錯誤後的部分已遭到擱置，請參閱擱置佇列，以取得詳細資料</span><span class="sxs-lookup"><span data-stu-id="afdad-117">The part after the error is being suspended, refer to Suspended Queue for details</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="afdad-118">說明</span><span class="sxs-lookup"><span data-stu-id="afdad-118">Explanation</span></span>  
 <span data-ttu-id="afdad-119">這個錯誤/警告/資訊事件表示接收管線無法處理內送 EDIFACT 交換，因為交換中發生的結構化的錯誤。</span><span class="sxs-lookup"><span data-stu-id="afdad-119">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming EDIFACT interchange, because a structural error occurred in the interchange.</span></span> <span data-ttu-id="afdad-120">這會發生已被保留，與在錯誤時暫停交易集的交換。</span><span class="sxs-lookup"><span data-stu-id="afdad-120">This occurred with an interchange that was being preserved, with transaction sets suspended on the error.</span></span> <span data-ttu-id="afdad-121">這個錯誤，交易集 （或集合） 的結果包含錯誤的暫止，但其餘的交易設定已處理保留批次的一部分。</span><span class="sxs-lookup"><span data-stu-id="afdad-121">As a result of this error, the transaction set (or sets) that included the error was suspended, but the rest of the transaction sets were processed as part of the preserved batch.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="afdad-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="afdad-122">User Action</span></span>  
 <span data-ttu-id="afdad-123">若要解決這個錯誤，將傳送者的交換修正結構的錯誤，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="afdad-123">To resolve this error, have the sender of the interchange fix the structural error, and then resend the interchange.</span></span>