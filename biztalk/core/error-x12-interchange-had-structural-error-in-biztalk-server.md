---
title: '交換發生結構錯誤。 最後一個結構有效的功能群組識別碼為: |Microsoft Docs'
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
ms.openlocfilehash: a3da8a701e543fe5bfb9453af3cfa2514414f5c2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988094"
---
# <a name="the-interchange-had-structural-error-last-structurally-valid-functional-group-id-was"></a><span data-ttu-id="88101-103">交換發生結構錯誤。</span><span class="sxs-lookup"><span data-stu-id="88101-103">The interchange had structural error.</span></span> <span data-ttu-id="88101-104">最後一個結構有效的功能群組識別碼是：</span><span class="sxs-lookup"><span data-stu-id="88101-104">Last structurally valid functional group ID was:</span></span>
## <a name="details"></a><span data-ttu-id="88101-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="88101-105">Details</span></span>  
  
|                 |                                                                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="88101-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="88101-106">Product Name</span></span>   |                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                 |
| <span data-ttu-id="88101-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="88101-107">Product Version</span></span> |                                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                             |
|    <span data-ttu-id="88101-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="88101-108">Event ID</span></span>     |                                                                         -                                                                          |
|  <span data-ttu-id="88101-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="88101-109">Event Source</span></span>   |                               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="88101-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="88101-110"> EDI</span></span>                               |
|    <span data-ttu-id="88101-111">元件</span><span class="sxs-lookup"><span data-stu-id="88101-111">Component</span></span>    |                                                                     <span data-ttu-id="88101-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="88101-112">EDI Engine</span></span>                                                                     |
|  <span data-ttu-id="88101-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="88101-113">Symbolic Name</span></span>  |                                                     <span data-ttu-id="88101-114">X12InterchangeStructuralErrorAfter1stGroup</span><span class="sxs-lookup"><span data-stu-id="88101-114">X12InterchangeStructuralErrorAfter1stGroup</span></span>                                                     |
|  <span data-ttu-id="88101-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="88101-115">Message Text</span></span>   | <span data-ttu-id="88101-116">交換識別碼 '{0}'，寄件者識別碼為'{1}'，接收者識別碼 '{2}' 發生結構錯誤。</span><span class="sxs-lookup"><span data-stu-id="88101-116">The interchange with id '{0}', with sender id '{1}', receiver id '{2}' had structural error.</span></span> <span data-ttu-id="88101-117">最後一個結構有效的功能群組識別碼為 '{3}'</span><span class="sxs-lookup"><span data-stu-id="88101-117">Last structurally valid functional group ID was '{3}'</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="88101-118">說明</span><span class="sxs-lookup"><span data-stu-id="88101-118">Explanation</span></span>  
 <span data-ttu-id="88101-119">這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換，因為指定的功能群組後，所發生交換中的結構化的錯誤。</span><span class="sxs-lookup"><span data-stu-id="88101-119">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange, because a structural error occurred in the interchange after the indicated functional group.</span></span> <span data-ttu-id="88101-120">發生此狀況可能是使用已被保留，與在錯誤時暫停交易集的交換。</span><span class="sxs-lookup"><span data-stu-id="88101-120">This may have occurred with an interchange that was being preserved, with transaction sets suspended on the error.</span></span> <span data-ttu-id="88101-121">此錯誤，交易集 （或集合） 包含錯誤的結果暫止，但其餘的交易設定已處理保留批次的一部分。</span><span class="sxs-lookup"><span data-stu-id="88101-121">As a result of this error, the transaction set (or sets) that included the error was suspended, but the rest of the transaction sets were processed as part of the preserved batch.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="88101-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="88101-122">User Action</span></span>  
 <span data-ttu-id="88101-123">若要解決這個錯誤，交換修正程式結構的錯誤，將傳送者與然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="88101-123">To resolve this error, have the sender of the interchange fix the structural error, and then resend the interchange.</span></span>