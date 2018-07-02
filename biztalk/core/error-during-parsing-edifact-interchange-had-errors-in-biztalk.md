---
title: 剖析期間發生的錯誤。 Edifact 交換發生下列錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2fa8f9d5-5b7c-47c9-96d3-77be280b78e9
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86d891abe7ca75dbbe9052f221970e235b390269
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988207"
---
# <a name="error-encountered-during-parsing-the-edifact-interchange-had-the-following-errors"></a><span data-ttu-id="13926-103">剖析期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="13926-103">Error encountered during parsing.</span></span> <span data-ttu-id="13926-104">Edifact 交換發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="13926-104">The Edifact interchange had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="13926-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="13926-105">Details</span></span>  
  
|                 |                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="13926-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="13926-106">Product Name</span></span>   |                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                             |
| <span data-ttu-id="13926-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="13926-107">Product Version</span></span> |                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                         |
|    <span data-ttu-id="13926-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="13926-108">Event ID</span></span>     |                                                                     -                                                                      |
|  <span data-ttu-id="13926-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="13926-109">Event Source</span></span>   |                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="13926-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="13926-110"> EDI</span></span>                           |
|    <span data-ttu-id="13926-111">元件</span><span class="sxs-lookup"><span data-stu-id="13926-111">Component</span></span>    |                                                                 <span data-ttu-id="13926-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="13926-112">EDI Engine</span></span>                                                                 |
|  <span data-ttu-id="13926-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="13926-113">Symbolic Name</span></span>  |                                                        <span data-ttu-id="13926-114">EfactInterchangeReceiveError</span><span class="sxs-lookup"><span data-stu-id="13926-114">EfactInterchangeReceiveError</span></span>                                                        |
|  <span data-ttu-id="13926-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="13926-115">Message Text</span></span>   | <span data-ttu-id="13926-116">剖析期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="13926-116">Error encountered during parsing.</span></span> <span data-ttu-id="13926-117">Edifact 交換識別碼 '{0}'，寄件者識別碼為'{1}'，接收者識別碼 '{2}' 發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="13926-117">The Edifact interchange with id '{0}', with sender id '{1}', receiver id '{2}' had the following errors:</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="13926-118">說明</span><span class="sxs-lookup"><span data-stu-id="13926-118">Explanation</span></span>  
 <span data-ttu-id="13926-119">這個錯誤/警告/資訊事件表示 EDI 接收管線在剖析內送 EDIFACT 交換因為交換中敘述的錯誤時遇到錯誤。</span><span class="sxs-lookup"><span data-stu-id="13926-119">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming EDIFACT interchange because of the stated errors in the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="13926-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="13926-120">User Action</span></span>  
 <span data-ttu-id="13926-121">若要解決這個錯誤，找出交換中的錯誤訊息，並接著決定產品說明中的問題解決方法需要使用錯誤訊息中的資訊。</span><span class="sxs-lookup"><span data-stu-id="13926-121">To resolve this error, use the information in the error message to identify the error in the interchange and then determine the problem resolution in the product help.</span></span>