---
title: 在剖析期間發生錯誤。 在交換的 Edifact 功能群組發生下列錯誤 |Microsoft 文件
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
ms.openlocfilehash: 6af00ae6500419fcb3ed687da89415e7594f1adc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241054"
---
# <a name="error-encountered-during-parsing-the-edifact-functional-group-in-interchange-had-the-following-errors"></a><span data-ttu-id="94034-103">在剖析期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="94034-103">Error encountered during parsing.</span></span> <span data-ttu-id="94034-104">交換中的 Edifact 功能群組發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="94034-104">The Edifact functional group in interchange had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="94034-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="94034-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="94034-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="94034-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="94034-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="94034-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="94034-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="94034-108">Event ID</span></span>|-|  
|<span data-ttu-id="94034-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="94034-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="94034-110">EDI</span><span class="sxs-lookup"><span data-stu-id="94034-110"> EDI</span></span>|  
|<span data-ttu-id="94034-111">元件</span><span class="sxs-lookup"><span data-stu-id="94034-111">Component</span></span>|<span data-ttu-id="94034-112">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="94034-112">EDI Engine</span></span>|  
|<span data-ttu-id="94034-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="94034-113">Symbolic Name</span></span>|<span data-ttu-id="94034-114">EfactFunctionalGroupReceiveError</span><span class="sxs-lookup"><span data-stu-id="94034-114">EfactFunctionalGroupReceiveError</span></span>|  
|<span data-ttu-id="94034-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="94034-115">Message Text</span></span>|<span data-ttu-id="94034-116">在剖析期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="94034-116">Error encountered during parsing.</span></span> <span data-ttu-id="94034-117">Edifact 功能群組識別碼為 '{0}'，識別碼 '{1}' 交換中寄件者識別碼 '{2}'，接收者識別碼 '{3}' 發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="94034-117">The Edifact functional group with id '{0}', in interchange with id '{1}', with sender id '{2}', receiver id '{3}' had the following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="94034-118">說明</span><span class="sxs-lookup"><span data-stu-id="94034-118">Explanation</span></span>  
 <span data-ttu-id="94034-119">這個錯誤/警告/資訊事件表示因為識別的功能群組之敘述的錯誤，EDI 接收管線在剖析內送 EDIFACT 交換時遇到錯誤。</span><span class="sxs-lookup"><span data-stu-id="94034-119">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming EDIFACT interchange because of the stated errors with the identified functional group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="94034-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="94034-120">User Action</span></span>  
 <span data-ttu-id="94034-121">若要解決此錯誤，使用錯誤訊息中的資訊識別群組中的錯誤，然後決定產品說明中的問題解決方法。</span><span class="sxs-lookup"><span data-stu-id="94034-121">To resolve this error, use the information in the error message to identify the error in the group and then determine the problem resolution in the product help.</span></span>