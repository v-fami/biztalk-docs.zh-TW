---
title: Edifact 交易集包含在交換錯誤 |Microsoft Docs
description: 序列化期間發生的錯誤。 下列的錯誤是而擱置的 Edifact 交易集包含在交換 （沒有群組）
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
ms.openlocfilehash: e5fcd7702ce791037d8a7320f647955fca1c9489
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981927"
---
# <a name="edifact-transaction-set-is-suspended-error-and-details"></a><span data-ttu-id="1103a-104">Edifact 交易集時暫停的錯誤和詳細資料</span><span class="sxs-lookup"><span data-stu-id="1103a-104">Edifact transaction set is suspended error and details</span></span>

`Error encountered during serialization. The Edifact transaction set contained in interchange (without group) is being suspended with following errors`

## <a name="details"></a><span data-ttu-id="1103a-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1103a-105">Details</span></span>  
  
|                 |                                                                                                                                                                                                                              |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="1103a-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1103a-106">Product Name</span></span>   |                                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                      |
| <span data-ttu-id="1103a-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="1103a-107">Product Version</span></span> |                                                                                  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                  |
|    <span data-ttu-id="1103a-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1103a-108">Event ID</span></span>     |                                                                                                              -                                                                                                               |
|  <span data-ttu-id="1103a-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="1103a-109">Event Source</span></span>   |                                                                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1103a-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="1103a-110"> EDI</span></span>                                                                    |
|    <span data-ttu-id="1103a-111">元件</span><span class="sxs-lookup"><span data-stu-id="1103a-111">Component</span></span>    |                                                                                                          <span data-ttu-id="1103a-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="1103a-112">EDI Engine</span></span>                                                                                                          |
|  <span data-ttu-id="1103a-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1103a-113">Symbolic Name</span></span>  |                                                                                           <span data-ttu-id="1103a-114">EfactTransactionSetSendErrorWithoutGroup</span><span class="sxs-lookup"><span data-stu-id="1103a-114">EfactTransactionSetSendErrorWithoutGroup</span></span>                                                                                           |
|  <span data-ttu-id="1103a-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1103a-115">Message Text</span></span>   | <span data-ttu-id="1103a-116">序列化期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1103a-116">Error encountered during serialization.</span></span> <span data-ttu-id="1103a-117">Edifact 交易集識別碼為 '{0}'包含在交換 （沒有群組） 識別碼'{1}'，寄件者識別碼為'{2}'，接收者識別碼 '{3}' 而遭到擱置下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="1103a-117">The Edifact transaction set with id '{0}' contained in interchange (without group)  with id '{1}', with sender id '{2}', receiver id '{3}' is being suspended with following errors:</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="1103a-118">說明</span><span class="sxs-lookup"><span data-stu-id="1103a-118">Explanation</span></span>  
 <span data-ttu-id="1103a-119">這個錯誤/警告/資訊事件表示 EDI 傳送管線在序列化傳出的 EDIFACT 交換因為識別的交易集與敘述的錯誤時，會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1103a-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing EDIFACT interchange because of the stated errors with the identified transaction set.</span></span> <span data-ttu-id="1103a-120">請注意，交易集不在交換中的群組。</span><span class="sxs-lookup"><span data-stu-id="1103a-120">Note that the transaction set is not in a group in the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1103a-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1103a-121">User Action</span></span>  
 <span data-ttu-id="1103a-122">若要解決這個錯誤，錯誤訊息中使用的資訊來識別交易集合中的錯誤訊息，並再判斷解決問題。</span><span class="sxs-lookup"><span data-stu-id="1103a-122">To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution.</span></span>