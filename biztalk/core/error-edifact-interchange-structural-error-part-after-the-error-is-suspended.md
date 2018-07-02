---
title: 交換發生結構錯誤。 正在暫止錯誤後的部分 |Microsoft Docs
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
ms.openlocfilehash: e77100200a4fb2eacb24c6745fcd17011231b991
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967303"
---
# <a name="the-interchange-had-structural-error-the-part-after-the-error-is-being-suspended"></a><span data-ttu-id="e1e60-103">交換發生結構錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e60-103">The interchange had structural error.</span></span> <span data-ttu-id="e1e60-104">錯誤後的部分正在遭到擱置</span><span class="sxs-lookup"><span data-stu-id="e1e60-104">The part after the error is being suspended</span></span>
## <a name="details"></a><span data-ttu-id="e1e60-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e1e60-105">Details</span></span>  
  
|                 |                                                                                                                                                                                |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="e1e60-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e1e60-106">Product Name</span></span>   |                                               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                               |
| <span data-ttu-id="e1e60-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="e1e60-107">Product Version</span></span> |                                                           [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                           |
|    <span data-ttu-id="e1e60-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e1e60-108">Event ID</span></span>     |                                                                                       -                                                                                        |
|  <span data-ttu-id="e1e60-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="e1e60-109">Event Source</span></span>   |                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e1e60-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="e1e60-110"> EDI</span></span>                                             |
|    <span data-ttu-id="e1e60-111">元件</span><span class="sxs-lookup"><span data-stu-id="e1e60-111">Component</span></span>    |                                                                                   <span data-ttu-id="e1e60-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="e1e60-112">EDI Engine</span></span>                                                                                   |
|  <span data-ttu-id="e1e60-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e1e60-113">Symbolic Name</span></span>  |                                                                        <span data-ttu-id="e1e60-114">EfactInterchangeStructuralError</span><span class="sxs-lookup"><span data-stu-id="e1e60-114">EfactInterchangeStructuralError</span></span>                                                                         |
|  <span data-ttu-id="e1e60-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e1e60-115">Message Text</span></span>   | <span data-ttu-id="e1e60-116">交換識別碼 '{0}'，寄件者識別碼為'{1}'，接收者識別碼 '{2}' 發生結構錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e60-116">The interchange with id '{0}', with sender id '{1}', receiver id '{2}' had structural error.</span></span> <span data-ttu-id="e1e60-117">錯誤後的部分已遭到擱置，請參閱擱置佇列，以取得詳細資料</span><span class="sxs-lookup"><span data-stu-id="e1e60-117">The part after the error is being suspended, refer to Suspended Queue for details</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="e1e60-118">說明</span><span class="sxs-lookup"><span data-stu-id="e1e60-118">Explanation</span></span>  
 <span data-ttu-id="e1e60-119">這個錯誤/警告/資訊事件表示接收管線無法處理內送 EDIFACT 交換，因為交換中發生結構錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1e60-119">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming EDIFACT interchange, because a structural error occurred in the interchange.</span></span> <span data-ttu-id="e1e60-120">這發生已被保留，與在錯誤時暫停交易集的交換。</span><span class="sxs-lookup"><span data-stu-id="e1e60-120">This occurred with an interchange that was being preserved, with transaction sets suspended on the error.</span></span> <span data-ttu-id="e1e60-121">此錯誤，交易集 （或集合） 包含錯誤的結果暫止，但其餘的交易設定已處理保留批次的一部分。</span><span class="sxs-lookup"><span data-stu-id="e1e60-121">As a result of this error, the transaction set (or sets) that included the error was suspended, but the rest of the transaction sets were processed as part of the preserved batch.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e1e60-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e1e60-122">User Action</span></span>  
 <span data-ttu-id="e1e60-123">若要解決這個錯誤，交換修正程式結構的錯誤，將傳送者與然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="e1e60-123">To resolve this error, have the sender of the interchange fix the structural error, and then resend the interchange.</span></span>