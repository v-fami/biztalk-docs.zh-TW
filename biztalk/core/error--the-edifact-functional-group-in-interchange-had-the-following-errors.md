---
title: 剖析期間發生的錯誤。 交換中的 Edifact 功能群組發生下列錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77ca78b3-8a1f-4da5-9c15-524ab6802457
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5be4d7270aeac605c1e476db4089ea3089296bf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004495"
---
# <a name="error-encountered-during-parsing-the-edifact-functional-group-in-interchange-had-the-following-errors"></a><span data-ttu-id="c5197-103">剖析期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c5197-103">Error encountered during parsing.</span></span> <span data-ttu-id="c5197-104">交換中的 Edifact 功能群組發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="c5197-104">The Edifact functional group in interchange had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="c5197-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c5197-105">Details</span></span>  
  
|                 |                                                                                                                                                                               |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="c5197-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c5197-106">Product Name</span></span>   |                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                               |
| <span data-ttu-id="c5197-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="c5197-107">Product Version</span></span> |                                                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                           |
|    <span data-ttu-id="c5197-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c5197-108">Event ID</span></span>     |                                                                                       -                                                                                       |
|  <span data-ttu-id="c5197-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="c5197-109">Event Source</span></span>   |                                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c5197-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="c5197-110"> EDI</span></span>                                             |
|    <span data-ttu-id="c5197-111">元件</span><span class="sxs-lookup"><span data-stu-id="c5197-111">Component</span></span>    |                                                                                  <span data-ttu-id="c5197-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="c5197-112">EDI Engine</span></span>                                                                                   |
|  <span data-ttu-id="c5197-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c5197-113">Symbolic Name</span></span>  |                                                                       <span data-ttu-id="c5197-114">EfactFunctionalGroupReceiveError</span><span class="sxs-lookup"><span data-stu-id="c5197-114">EfactFunctionalGroupReceiveError</span></span>                                                                        |
|  <span data-ttu-id="c5197-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c5197-115">Message Text</span></span>   | <span data-ttu-id="c5197-116">剖析期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c5197-116">Error encountered during parsing.</span></span> <span data-ttu-id="c5197-117">Edifact 功能群組識別碼 '{0}'，在交換識別碼'{1}'，寄件者識別碼為 '{2}'，接收者識別碼'{3}' 發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="c5197-117">The Edifact functional group with id '{0}', in interchange with id '{1}', with sender id '{2}', receiver id '{3}' had the following errors:</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="c5197-118">說明</span><span class="sxs-lookup"><span data-stu-id="c5197-118">Explanation</span></span>  
 <span data-ttu-id="c5197-119">這個錯誤/警告/資訊事件表示因為識別的功能群組之敘述的錯誤，EDI 接收管線在剖析內送 EDIFACT 交換時遇到錯誤。</span><span class="sxs-lookup"><span data-stu-id="c5197-119">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming EDIFACT interchange because of the stated errors with the identified functional group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c5197-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c5197-120">User Action</span></span>  
 <span data-ttu-id="c5197-121">若要解決此錯誤，使用錯誤訊息中的資訊識別群組中的錯誤，然後決定產品說明中的問題解決方法。</span><span class="sxs-lookup"><span data-stu-id="c5197-121">To resolve this error, use the information in the error message to identify the error in the group and then determine the problem resolution in the product help.</span></span>