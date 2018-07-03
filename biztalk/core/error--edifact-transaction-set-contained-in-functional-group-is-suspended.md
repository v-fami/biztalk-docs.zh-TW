---
title: 剖析期間發生的錯誤。 正在暫停的 Edifact 交易集包含在功能群組發生下列錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 986a7220-d35a-4047-8996-7d44c7d2b823
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b7e5dd86c995b78eb07aa9c7516274b748ee99b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014095"
---
# <a name="error-encountered-during-parsing-the-edifact-transaction-set-contained-in-functional-group-is-being-suspended-with-following-errors"></a><span data-ttu-id="7fd73-103">剖析期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="7fd73-103">Error encountered during parsing.</span></span> <span data-ttu-id="7fd73-104">下列錯誤而遭到擱置包含在功能群組的 Edifact 交易集</span><span class="sxs-lookup"><span data-stu-id="7fd73-104">The Edifact transaction set contained in functional group is being suspended with following errors</span></span>
## <a name="details"></a><span data-ttu-id="7fd73-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7fd73-105">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                          |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="7fd73-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7fd73-106">Product Name</span></span>   |                                                                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                            |
| <span data-ttu-id="7fd73-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="7fd73-107">Product Version</span></span> |                                                                                        [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                        |
|    <span data-ttu-id="7fd73-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7fd73-108">Event ID</span></span>     |                                                                                                                    -                                                                                                                     |
|  <span data-ttu-id="7fd73-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="7fd73-109">Event Source</span></span>   |                                                                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7fd73-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="7fd73-110"> EDI</span></span>                                                                          |
|    <span data-ttu-id="7fd73-111">元件</span><span class="sxs-lookup"><span data-stu-id="7fd73-111">Component</span></span>    |                                                                                                                <span data-ttu-id="7fd73-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="7fd73-112">EDI Engine</span></span>                                                                                                                |
|  <span data-ttu-id="7fd73-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7fd73-113">Symbolic Name</span></span>  |                                                                                                     <span data-ttu-id="7fd73-114">EfactTransactionSetReceiveError</span><span class="sxs-lookup"><span data-stu-id="7fd73-114">EfactTransactionSetReceiveError</span></span>                                                                                                      |
|  <span data-ttu-id="7fd73-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7fd73-115">Message Text</span></span>   | <span data-ttu-id="7fd73-116">剖析期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="7fd73-116">Error encountered during parsing.</span></span> <span data-ttu-id="7fd73-117">Edifact 交易集識別碼為 '{0}'包含在功能群組識別碼'{1}'，在交換識別碼'{2}'，寄件者識別碼為 '{3}'，接收者識別碼'{4}' 而遭到擱置下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="7fd73-117">The Edifact transaction set with id '{0}' contained in functional group with id '{1}', in interchange with id '{2}', with sender id '{3}', receiver id '{4}' is being suspended with following errors:</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="7fd73-118">說明</span><span class="sxs-lookup"><span data-stu-id="7fd73-118">Explanation</span></span>  
 <span data-ttu-id="7fd73-119">這個錯誤/警告/資訊事件表示 EDI 接收管線無法剖析內送 EDIFACT 交換和群組，因為識別的交易集與敘述的錯誤。</span><span class="sxs-lookup"><span data-stu-id="7fd73-119">This Error/Warning/Information event indicates that the EDI receive pipeline could not parse an incoming EDIFACT interchange with a group because of the stated errors with the identified transaction set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7fd73-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7fd73-120">User Action</span></span>  
 <span data-ttu-id="7fd73-121">若要解決這個錯誤，錯誤訊息中使用的資訊來識別交易集合中的錯誤訊息，然後判斷 文件中的問題解決方法。</span><span class="sxs-lookup"><span data-stu-id="7fd73-121">To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution in the documentation.</span></span>