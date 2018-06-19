---
title: 訊息部分遺失元素 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b519315f-d51d-4ca3-a0e6-d08bb920c6c5
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dd5a423a34d8b6ddf8f4689351b0f6dbcef53c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263038"
---
# <a name="message-part-missing-element"></a><span data-ttu-id="45557-102">訊息部分遺失元素</span><span class="sxs-lookup"><span data-stu-id="45557-102">Message part missing element</span></span>
## <a name="details"></a><span data-ttu-id="45557-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="45557-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="45557-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="45557-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="45557-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="45557-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="45557-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="45557-106">Event ID</span></span>|<span data-ttu-id="45557-107">0</span><span class="sxs-lookup"><span data-stu-id="45557-107">0</span></span>|  
|<span data-ttu-id="45557-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="45557-108">Event Source</span></span>|<span data-ttu-id="45557-109">0</span><span class="sxs-lookup"><span data-stu-id="45557-109">0</span></span>|  
|<span data-ttu-id="45557-110">元件</span><span class="sxs-lookup"><span data-stu-id="45557-110">Component</span></span>|<span data-ttu-id="45557-111">0</span><span class="sxs-lookup"><span data-stu-id="45557-111">0</span></span>|  
|<span data-ttu-id="45557-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="45557-112">Symbolic Name</span></span>|<span data-ttu-id="45557-113">0</span><span class="sxs-lookup"><span data-stu-id="45557-113">0</span></span>|  
|<span data-ttu-id="45557-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="45557-114">Message Text</span></span>|<span data-ttu-id="45557-115">訊息部分遺失元素。</span><span class="sxs-lookup"><span data-stu-id="45557-115">Message part missing element.</span></span> <span data-ttu-id="45557-116">更正服務描述"{0}"訊息類型 」 {1} 「 部分 」 {2}"，然後再重新執行精靈</span><span class="sxs-lookup"><span data-stu-id="45557-116">Correct service description "{0}" message type "{1}" part "{2}" and rerun the wizard</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="45557-117">說明</span><span class="sxs-lookup"><span data-stu-id="45557-117">Explanation</span></span>  
 <span data-ttu-id="45557-118">此錯誤表示嘗試從中使用服務不需要識別的訊息類型的項目標記。</span><span class="sxs-lookup"><span data-stu-id="45557-118">This error indicates the service that is trying to be consumed does not have the element tag identifying the type of message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="45557-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="45557-119">User Action</span></span>  
 <span data-ttu-id="45557-120">更正服務與適當的訊息類型，然後再次嘗試使用 （如果您擁有想要使用的 WCF 服務）。</span><span class="sxs-lookup"><span data-stu-id="45557-120">Correct the service with the appropriate message type and try to consume (if you own the WCF services that you are trying to consume).</span></span> <span data-ttu-id="45557-121">否則，請連絡服務提供者。</span><span class="sxs-lookup"><span data-stu-id="45557-121">Otherwise, contact the service provider.</span></span>  
  
 <span data-ttu-id="45557-122">如需有關訊息的詳細資訊，請參閱下列資源中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="45557-122">For additional information on messages, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="45557-123">建構 Web 訊息</span><span class="sxs-lookup"><span data-stu-id="45557-123">Constructing Web Messages</span></span>](../core/constructing-web-messages.md)