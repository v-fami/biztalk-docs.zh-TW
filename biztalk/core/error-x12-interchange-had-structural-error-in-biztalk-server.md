---
title: '交換有結構的錯誤。 最後一個結構上有效的功能群組識別碼為: |Microsoft 文件'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd62855b-ecc6-4cfd-be9c-0025348eb841
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 565a4865455cabef3cd53988d601a89ecf1549e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241406"
---
# <a name="the-interchange-had-structural-error-last-structurally-valid-functional-group-id-was"></a><span data-ttu-id="ba8a1-103">交換有結構的錯誤。</span><span class="sxs-lookup"><span data-stu-id="ba8a1-103">The interchange had structural error.</span></span> <span data-ttu-id="ba8a1-104">最後一個結構有效的功能群組識別碼是：</span><span class="sxs-lookup"><span data-stu-id="ba8a1-104">Last structurally valid functional group ID was:</span></span>
## <a name="details"></a><span data-ttu-id="ba8a1-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ba8a1-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ba8a1-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ba8a1-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ba8a1-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="ba8a1-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ba8a1-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ba8a1-108">Event ID</span></span>|-|  
|<span data-ttu-id="ba8a1-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="ba8a1-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ba8a1-110">EDI</span><span class="sxs-lookup"><span data-stu-id="ba8a1-110"> EDI</span></span>|  
|<span data-ttu-id="ba8a1-111">元件</span><span class="sxs-lookup"><span data-stu-id="ba8a1-111">Component</span></span>|<span data-ttu-id="ba8a1-112">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="ba8a1-112">EDI Engine</span></span>|  
|<span data-ttu-id="ba8a1-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ba8a1-113">Symbolic Name</span></span>|<span data-ttu-id="ba8a1-114">X12InterchangeStructuralErrorAfter1stGroup</span><span class="sxs-lookup"><span data-stu-id="ba8a1-114">X12InterchangeStructuralErrorAfter1stGroup</span></span>|  
|<span data-ttu-id="ba8a1-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ba8a1-115">Message Text</span></span>|<span data-ttu-id="ba8a1-116">交換傳送者識別碼 '{1}' 識別碼為 '{0}'、 接收者識別碼 '{2}' 有結構的錯誤。</span><span class="sxs-lookup"><span data-stu-id="ba8a1-116">The interchange with id '{0}', with sender id '{1}', receiver id '{2}' had structural error.</span></span> <span data-ttu-id="ba8a1-117">上次結構上有效的功能群組識別碼為 '{3}'</span><span class="sxs-lookup"><span data-stu-id="ba8a1-117">Last structurally valid functional group ID was '{3}'</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ba8a1-118">說明</span><span class="sxs-lookup"><span data-stu-id="ba8a1-118">Explanation</span></span>  
 <span data-ttu-id="ba8a1-119">這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換，因為指定的功能群組後發生交換中的結構化的錯誤。</span><span class="sxs-lookup"><span data-stu-id="ba8a1-119">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange, because a structural error occurred in the interchange after the indicated functional group.</span></span> <span data-ttu-id="ba8a1-120">這可能會發生已被保留，與在錯誤時暫停交易集的交換。</span><span class="sxs-lookup"><span data-stu-id="ba8a1-120">This may have occurred with an interchange that was being preserved, with transaction sets suspended on the error.</span></span> <span data-ttu-id="ba8a1-121">這個錯誤，交易集 （或集合） 的結果包含錯誤的暫止，但其餘的交易設定已處理保留批次的一部分。</span><span class="sxs-lookup"><span data-stu-id="ba8a1-121">As a result of this error, the transaction set (or sets) that included the error was suspended, but the rest of the transaction sets were processed as part of the preserved batch.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ba8a1-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ba8a1-122">User Action</span></span>  
 <span data-ttu-id="ba8a1-123">若要解決這個錯誤，將傳送者的交換修正結構的錯誤，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="ba8a1-123">To resolve this error, have the sender of the interchange fix the structural error, and then resend the interchange.</span></span>