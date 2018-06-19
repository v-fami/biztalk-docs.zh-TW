---
title: 條件式的必要資料元素遺失 |Microsoft 文件
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
ms.openlocfilehash: 0d77a25e60af0d8287515d6fb3a7e2797d5af0b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231958"
---
# <a name="conditional-required-data-element-missing"></a><span data-ttu-id="6c86f-102">遺失條件式的必要資料元素</span><span class="sxs-lookup"><span data-stu-id="6c86f-102">Conditional required data element missing</span></span>
## <a name="details"></a><span data-ttu-id="6c86f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6c86f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6c86f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6c86f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6c86f-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="6c86f-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="6c86f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6c86f-106">Event ID</span></span>|-|  
|<span data-ttu-id="6c86f-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="6c86f-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6c86f-108">EDI</span><span class="sxs-lookup"><span data-stu-id="6c86f-108"> EDI</span></span>|  
|<span data-ttu-id="6c86f-109">元件</span><span class="sxs-lookup"><span data-stu-id="6c86f-109">Component</span></span>|<span data-ttu-id="6c86f-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="6c86f-110">EDI Engine</span></span>|  
|<span data-ttu-id="6c86f-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6c86f-111">Symbolic Name</span></span>|<span data-ttu-id="6c86f-112">X12DeConditionalRequiredDataElementMissingDescription</span><span class="sxs-lookup"><span data-stu-id="6c86f-112">X12DeConditionalRequiredDataElementMissingDescription</span></span>|  
|<span data-ttu-id="6c86f-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6c86f-113">Message Text</span></span>|<span data-ttu-id="6c86f-114">遺失條件式的必要資料元素</span><span class="sxs-lookup"><span data-stu-id="6c86f-114">Conditional required data element missing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6c86f-115">說明</span><span class="sxs-lookup"><span data-stu-id="6c86f-115">Explanation</span></span>  
 <span data-ttu-id="6c86f-116">這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送交換，因為交換中不存在 X12ConditionDesignatorX 規則所需的資料元素。</span><span class="sxs-lookup"><span data-stu-id="6c86f-116">This Error/Warning/Information event indicates that the EDI receive pipeline could not process the incoming interchange because a data element that is required by the X12ConditionDesignatorX rule does not exist in the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6c86f-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6c86f-117">User Action</span></span>  
 <span data-ttu-id="6c86f-118">這個錯誤可能是內送交換，而不設定或 BizTalk server 作業的問題。</span><span class="sxs-lookup"><span data-stu-id="6c86f-118">This error is likely an issue with the incoming interchange, not with the configuration or operation of BizTalk Server.</span></span> <span data-ttu-id="6c86f-119">若要解決這個錯誤，請連絡交換的寄件者，指示他們必須變更交換中使用的字元或識別 UNB1.1 欄位中，使其相符的字元集。</span><span class="sxs-lookup"><span data-stu-id="6c86f-119">To resolve this error, contact the sender of the interchange and indicate that they need to change either the characters used in the interchange or the character set identified in field UNB1.1 so that they match.</span></span>