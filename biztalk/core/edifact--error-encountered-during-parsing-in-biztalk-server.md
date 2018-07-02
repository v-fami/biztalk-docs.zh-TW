---
title: 剖析期間發生的錯誤。 不包含群組的 Edifact 交換發生下列錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6b324fd-f365-41b9-81aa-b6c5c5d3f673
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c3ef771093a376349ee6656709f90d2ca7ece7e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015310"
---
# <a name="error-encountered-during-parsing-the-edifact-interchange-which-did-not-contain-a-group-had-the-following-errors"></a><span data-ttu-id="8890a-103">剖析期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8890a-103">Error encountered during parsing.</span></span> <span data-ttu-id="8890a-104">不包含群組的 Edifact 交換發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="8890a-104">The Edifact interchange which did not contain a group had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="8890a-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8890a-105">Details</span></span>  
  
|                 |                                                                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="8890a-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8890a-106">Product Name</span></span>   |                                                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                   |
| <span data-ttu-id="8890a-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="8890a-107">Product Version</span></span> |                                                              [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                               |
|    <span data-ttu-id="8890a-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8890a-108">Event ID</span></span>     |                                                                                           -                                                                                           |
|  <span data-ttu-id="8890a-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="8890a-109">Event Source</span></span>   |                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8890a-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="8890a-110"> EDI</span></span>                                                 |
|    <span data-ttu-id="8890a-111">元件</span><span class="sxs-lookup"><span data-stu-id="8890a-111">Component</span></span>    |                                                                                      <span data-ttu-id="8890a-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="8890a-112">EDI Engine</span></span>                                                                                       |
|  <span data-ttu-id="8890a-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8890a-113">Symbolic Name</span></span>  |                                                                     <span data-ttu-id="8890a-114">EfactFunctionalGroupReceiveErrorWithoutGroup</span><span class="sxs-lookup"><span data-stu-id="8890a-114">EfactFunctionalGroupReceiveErrorWithoutGroup</span></span>                                                                      |
|  <span data-ttu-id="8890a-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8890a-115">Message Text</span></span>   | <span data-ttu-id="8890a-116">剖析期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8890a-116">Error encountered during parsing.</span></span> <span data-ttu-id="8890a-117">Edifact 交換不包含群組的交換識別碼為 '{0}'，寄件者識別碼為'{1}'，接收者識別碼 '{2}' 發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="8890a-117">The Edifact interchange which did not contain a group, with interchange id '{0}', with sender id '{1}', receiver id '{2}' had the following errors:</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="8890a-118">說明</span><span class="sxs-lookup"><span data-stu-id="8890a-118">Explanation</span></span>  
 <span data-ttu-id="8890a-119">這個錯誤/警告/資訊事件表示 EDI 接收管線在剖析內送 EDIFACT 交換因為敘述的錯誤不包含群組時遇到錯誤。</span><span class="sxs-lookup"><span data-stu-id="8890a-119">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming EDIFACT interchange that did not contain a group because of the stated errors.</span></span> <span data-ttu-id="8890a-120">請注意，群組是 EDIFACT 交換中的選擇項。</span><span class="sxs-lookup"><span data-stu-id="8890a-120">Note that groups are optional in EDIFACT interchanges.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8890a-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8890a-121">User Action</span></span>  
 <span data-ttu-id="8890a-122">若要解決這個錯誤，找出錯誤並再決定產品說明中的問題解決方法需要使用錯誤訊息中的資訊。</span><span class="sxs-lookup"><span data-stu-id="8890a-122">To resolve this error, use the information in the error message to identify the error and then determine the problem resolution in the product help.</span></span>