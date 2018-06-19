---
title: 在序列化期間發生錯誤。 Edifact 交換發生下列錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc933ac-161a-41e5-b67d-9f15e569d5c9
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4a84c70ee5db36c5482cac34c73ef0c9cad4620
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240006"
---
# <a name="error-encountered-during-serialization-the-edifact-interchange-had-the-following-errors"></a><span data-ttu-id="7fe60-103">在序列化期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7fe60-103">Error encountered during serialization.</span></span> <span data-ttu-id="7fe60-104">Edifact 交換發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="7fe60-104">The Edifact interchange had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="7fe60-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7fe60-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7fe60-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7fe60-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7fe60-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="7fe60-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="7fe60-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7fe60-108">Event ID</span></span>|-|  
|<span data-ttu-id="7fe60-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="7fe60-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7fe60-110">EDI</span><span class="sxs-lookup"><span data-stu-id="7fe60-110"> EDI</span></span>|  
|<span data-ttu-id="7fe60-111">元件</span><span class="sxs-lookup"><span data-stu-id="7fe60-111">Component</span></span>|<span data-ttu-id="7fe60-112">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="7fe60-112">EDI Engine</span></span>|  
|<span data-ttu-id="7fe60-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7fe60-113">Symbolic Name</span></span>|<span data-ttu-id="7fe60-114">EfactInterchangeSendError</span><span class="sxs-lookup"><span data-stu-id="7fe60-114">EfactInterchangeSendError</span></span>|  
|<span data-ttu-id="7fe60-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7fe60-115">Message Text</span></span>|<span data-ttu-id="7fe60-116">在序列化期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7fe60-116">Error encountered during serialization.</span></span> <span data-ttu-id="7fe60-117">寄件者識別碼 '{1}' 識別碼為 '{0}'，Edifact 交換接收者識別碼 '{2}' 發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="7fe60-117">The Edifact interchange with id '{0}', with sender id '{1}', receiver id '{2}' had the following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7fe60-118">說明</span><span class="sxs-lookup"><span data-stu-id="7fe60-118">Explanation</span></span>  
 <span data-ttu-id="7fe60-119">這個錯誤/警告/資訊事件表示 EDI 傳送管線在外寄 EDIFACT 交換序列化因為識別的交換與敘述的錯誤時，會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7fe60-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing EDIFACT interchange because of the stated errors with the identified interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7fe60-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7fe60-120">User Action</span></span>  
 <span data-ttu-id="7fe60-121">若要解決這個錯誤，找出交換中的錯誤，，然後決定產品說明中的問題解決方法需要使用錯誤訊息中的資訊。</span><span class="sxs-lookup"><span data-stu-id="7fe60-121">To resolve this error, use the information in the error message to identify the error in the interchange and then determine the problem resolution in the product help.</span></span>