---
title: 條件式的必要資料元素遺失 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5105c03-fa26-4c38-a276-c656f3076d5f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f43ebf2ba593ad5133b93400bf0e9cb1151dc45b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978439"
---
# <a name="conditional-required-data-element-missing"></a><span data-ttu-id="4e89c-102">遺失條件式的必要資料元素</span><span class="sxs-lookup"><span data-stu-id="4e89c-102">Conditional required data element missing</span></span>
## <a name="details"></a><span data-ttu-id="4e89c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4e89c-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="4e89c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4e89c-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="4e89c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="4e89c-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="4e89c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4e89c-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="4e89c-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="4e89c-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4e89c-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="4e89c-108"> EDI</span></span> |
|    <span data-ttu-id="4e89c-109">元件</span><span class="sxs-lookup"><span data-stu-id="4e89c-109">Component</span></span>    |                                       <span data-ttu-id="4e89c-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="4e89c-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="4e89c-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4e89c-111">Symbolic Name</span></span>  |                 <span data-ttu-id="4e89c-112">X12DeConditionalRequiredDataElementMissingDescription</span><span class="sxs-lookup"><span data-stu-id="4e89c-112">X12DeConditionalRequiredDataElementMissingDescription</span></span>                  |
|  <span data-ttu-id="4e89c-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4e89c-113">Message Text</span></span>   |                       <span data-ttu-id="4e89c-114">遺失條件式的必要資料元素</span><span class="sxs-lookup"><span data-stu-id="4e89c-114">Conditional required data element missing</span></span>                        |
  
## <a name="explanation"></a><span data-ttu-id="4e89c-115">說明</span><span class="sxs-lookup"><span data-stu-id="4e89c-115">Explanation</span></span>  
 <span data-ttu-id="4e89c-116">這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送交換，因為不存在 X12ConditionDesignatorX 規則所需的資料元素，這是在交換中。</span><span class="sxs-lookup"><span data-stu-id="4e89c-116">This Error/Warning/Information event indicates that the EDI receive pipeline could not process the incoming interchange because a data element that is required by the X12ConditionDesignatorX rule does not exist in the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4e89c-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4e89c-117">User Action</span></span>  
 <span data-ttu-id="4e89c-118">此錯誤可能是使用內送交換，而非與組態或 BizTalk server 作業的問題。</span><span class="sxs-lookup"><span data-stu-id="4e89c-118">This error is likely an issue with the incoming interchange, not with the configuration or operation of BizTalk Server.</span></span> <span data-ttu-id="4e89c-119">若要解決這個錯誤，請連絡交換的寄件者，並指出它們需要變更在交換中使用的字元或使其符合，UNB1.1 欄位中所識別的字元集。</span><span class="sxs-lookup"><span data-stu-id="4e89c-119">To resolve this error, contact the sender of the interchange and indicate that they need to change either the characters used in the interchange or the character set identified in field UNB1.1 so that they match.</span></span>