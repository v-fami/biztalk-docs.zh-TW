---
title: "在序列化期間發生錯誤。 X12 交換發生下列錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9ca3314-6c66-4400-816a-f9c7c7915122
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b27c08632901fed3d0fc9a9d43646034b044c626
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-serialization-the-x12-interchange-had-the-following-errors"></a><span data-ttu-id="76096-103">在序列化期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="76096-103">Error encountered during serialization.</span></span> <span data-ttu-id="76096-104">X12 交換發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="76096-104">The X12 interchange had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="76096-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="76096-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="76096-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="76096-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="76096-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="76096-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="76096-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="76096-108">Event ID</span></span>|-|  
|<span data-ttu-id="76096-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="76096-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="76096-110">EDI</span><span class="sxs-lookup"><span data-stu-id="76096-110"> EDI</span></span>|  
|<span data-ttu-id="76096-111">元件</span><span class="sxs-lookup"><span data-stu-id="76096-111">Component</span></span>|<span data-ttu-id="76096-112">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="76096-112">EDI Engine</span></span>|  
|<span data-ttu-id="76096-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="76096-113">Symbolic Name</span></span>|<span data-ttu-id="76096-114">X12InterchangeSendError</span><span class="sxs-lookup"><span data-stu-id="76096-114">X12InterchangeSendError</span></span>|  
|<span data-ttu-id="76096-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="76096-115">Message Text</span></span>|<span data-ttu-id="76096-116">在序列化期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="76096-116">Error encountered during serialization.</span></span> <span data-ttu-id="76096-117">X12 交換傳送者識別碼 '{1}'，接收者識別碼 '{2}' 識別碼為 '{0}'，發生下列錯誤</span><span class="sxs-lookup"><span data-stu-id="76096-117">The X12 interchange with id '{0}', with sender id '{1}', receiver id '{2}' had the following errors</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="76096-118">說明</span><span class="sxs-lookup"><span data-stu-id="76096-118">Explanation</span></span>  
 <span data-ttu-id="76096-119">這個錯誤/警告/資訊事件表示 EDI 傳送管線發生錯誤，當序列化 X12 外寄交換，因為敘述的錯誤。</span><span class="sxs-lookup"><span data-stu-id="76096-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing X12 interchange because of the stated errors.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="76096-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="76096-120">User Action</span></span>  
 <span data-ttu-id="76096-121">若要解決這個錯誤，找出交換中的錯誤，，然後決定產品說明中的問題解決方法需要使用錯誤訊息中的資訊。</span><span class="sxs-lookup"><span data-stu-id="76096-121">To resolve this error, use the information in the error message to identify the error in the interchange and then determine the problem resolution in the product help.</span></span>