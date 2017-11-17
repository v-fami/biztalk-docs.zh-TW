---
title: "在序列化期間發生錯誤。 Edifact 交換其中不包含群組發生下列錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af693139-e4cd-4bcb-922c-79caa148d3b7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72108104b359d4d06233cf9a623097bfd046a0ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-serialization-the-edifact-interchange-which-did-not-contain-a-group-had-the-following-errors"></a><span data-ttu-id="2e9bf-103">在序列化期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2e9bf-103">Error encountered during serialization.</span></span> <span data-ttu-id="2e9bf-104">Edifact 交換其中不包含群組發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="2e9bf-104">The Edifact interchange which did not contain a group had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="2e9bf-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2e9bf-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2e9bf-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2e9bf-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="2e9bf-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="2e9bf-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="2e9bf-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2e9bf-108">Event ID</span></span>|-|  
|<span data-ttu-id="2e9bf-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="2e9bf-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2e9bf-110">EDI</span><span class="sxs-lookup"><span data-stu-id="2e9bf-110"> EDI</span></span>|  
|<span data-ttu-id="2e9bf-111">元件</span><span class="sxs-lookup"><span data-stu-id="2e9bf-111">Component</span></span>|<span data-ttu-id="2e9bf-112">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="2e9bf-112">EDI Engine</span></span>|  
|<span data-ttu-id="2e9bf-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2e9bf-113">Symbolic Name</span></span>|<span data-ttu-id="2e9bf-114">EfactFunctionalGroupSendErrorWithoutGroup</span><span class="sxs-lookup"><span data-stu-id="2e9bf-114">EfactFunctionalGroupSendErrorWithoutGroup</span></span>|  
|<span data-ttu-id="2e9bf-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2e9bf-115">Message Text</span></span>|<span data-ttu-id="2e9bf-116">在序列化期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2e9bf-116">Error encountered during serialization.</span></span> <span data-ttu-id="2e9bf-117">其中不包含群組，交換識別碼為 '{0}'，寄件者識別碼 '{1}'，Edifact 交換接收者識別碼 '{2}' 發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="2e9bf-117">The Edifact interchange which did not contain a group, with interchange id '{0}', with sender id '{1}', receiver id '{2}' had the following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2e9bf-118">說明</span><span class="sxs-lookup"><span data-stu-id="2e9bf-118">Explanation</span></span>  
 <span data-ttu-id="2e9bf-119">這個錯誤/警告/資訊事件表示 EDI 傳送管線在外寄 EDIFACT 交換序列化因為識別的交換與敘述的錯誤時，會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2e9bf-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing EDIFACT interchange because of the stated errors with the identified interchange.</span></span> <span data-ttu-id="2e9bf-120">請注意交換不含群組。</span><span class="sxs-lookup"><span data-stu-id="2e9bf-120">Note that the interchange does not contain a group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2e9bf-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2e9bf-121">User Action</span></span>  
 <span data-ttu-id="2e9bf-122">若要解決這個錯誤，找出交換中的錯誤，，然後決定產品說明中的問題解決方法需要使用錯誤訊息中的資訊。</span><span class="sxs-lookup"><span data-stu-id="2e9bf-122">To resolve this error, use the information in the error message to identify the error in the interchange and then determine the problem resolution in the product help.</span></span>