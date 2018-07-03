---
title: 剖析期間發生的錯誤。 下列的錯誤而擱置的 Edifact 交易集包含在交換 （沒有群組） |Microsoft Docs
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
ms.openlocfilehash: c2e0d8e2b03decf2db806a08f082b7aace276a8e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006415"
---
# <a name="error-encountered-during-parsing-the-edifact-transaction-set-contained-in-interchange-without-group-is-being-suspended-with-following-errors"></a><span data-ttu-id="e2bfc-103">剖析期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e2bfc-103">Error encountered during parsing.</span></span> <span data-ttu-id="e2bfc-104">下列的錯誤是而擱置的 Edifact 交易集包含在交換 （沒有群組）</span><span class="sxs-lookup"><span data-stu-id="e2bfc-104">The Edifact transaction set contained in interchange (without group) is being suspended with following errors</span></span>
## <a name="details"></a><span data-ttu-id="e2bfc-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e2bfc-105">Details</span></span>  
  
|                 |                                                                                                                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="e2bfc-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e2bfc-106">Product Name</span></span>   |                                                                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                   |
| <span data-ttu-id="e2bfc-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="e2bfc-107">Product Version</span></span> |                                                                              [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                               |
|    <span data-ttu-id="e2bfc-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e2bfc-108">Event ID</span></span>     |                                                                                                           -                                                                                                           |
|  <span data-ttu-id="e2bfc-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="e2bfc-109">Event Source</span></span>   |                                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e2bfc-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="e2bfc-110"> EDI</span></span>                                                                 |
|    <span data-ttu-id="e2bfc-111">元件</span><span class="sxs-lookup"><span data-stu-id="e2bfc-111">Component</span></span>    |                                                                                                      <span data-ttu-id="e2bfc-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="e2bfc-112">EDI Engine</span></span>                                                                                                       |
|  <span data-ttu-id="e2bfc-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e2bfc-113">Symbolic Name</span></span>  |                                                                                      <span data-ttu-id="e2bfc-114">EfactTransactionSetReceiveErrorWithoutGroup</span><span class="sxs-lookup"><span data-stu-id="e2bfc-114">EfactTransactionSetReceiveErrorWithoutGroup</span></span>                                                                                      |
|  <span data-ttu-id="e2bfc-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e2bfc-115">Message Text</span></span>   | <span data-ttu-id="e2bfc-116">剖析期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e2bfc-116">Error encountered during parsing.</span></span> <span data-ttu-id="e2bfc-117">Edifact 交易集識別碼為 '{0}'包含在交換 （沒有群組） 識別碼'{1}'，寄件者識別碼為'{2}'，接收者識別碼 '{3}' 而遭到擱置下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="e2bfc-117">The Edifact transaction set with id '{0}' contained in interchange (without group) with id '{1}', with sender id '{2}', receiver id '{3}' is being suspended with following errors:</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="e2bfc-118">說明</span><span class="sxs-lookup"><span data-stu-id="e2bfc-118">Explanation</span></span>  
 <span data-ttu-id="e2bfc-119">這個錯誤/警告/資訊事件表示，由於交換中的已識別交易集發生所述的錯誤，因此 EDI 接收管線在剖析不含群組的內送 EDIFACT 交換時遇到錯誤。</span><span class="sxs-lookup"><span data-stu-id="e2bfc-119">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming EDIFACT interchange without a group because of the stated errors with the identified transaction set in the interchange.</span></span> <span data-ttu-id="e2bfc-120">請注意，交易集不在交換中的群組。</span><span class="sxs-lookup"><span data-stu-id="e2bfc-120">Note that the transaction set is not in a group in the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e2bfc-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e2bfc-121">User Action</span></span>  
 <span data-ttu-id="e2bfc-122">若要解決這個錯誤，錯誤訊息中使用的資訊來識別交易集合中的錯誤訊息，然後決定產品說明中的問題解決方法。</span><span class="sxs-lookup"><span data-stu-id="e2bfc-122">To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution in the product help.</span></span>