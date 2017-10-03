---
title: "訊息類型，而不支援部分 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0bfb042-feda-4282-a7fa-c13be4ff6254
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e3e6cc0f5d4a2ae18ff6bcb5fa0dc8ef605d730
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-types-without-parts-are-not-supported"></a><span data-ttu-id="63ad6-102">不支援沒有部分訊息類型</span><span class="sxs-lookup"><span data-stu-id="63ad6-102">Message types without parts are not supported</span></span>
## <a name="details"></a><span data-ttu-id="63ad6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="63ad6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="63ad6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="63ad6-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="63ad6-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="63ad6-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="63ad6-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="63ad6-106">Event ID</span></span>|<span data-ttu-id="63ad6-107">0</span><span class="sxs-lookup"><span data-stu-id="63ad6-107">0</span></span>|  
|<span data-ttu-id="63ad6-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="63ad6-108">Event Source</span></span>|<span data-ttu-id="63ad6-109">0</span><span class="sxs-lookup"><span data-stu-id="63ad6-109">0</span></span>|  
|<span data-ttu-id="63ad6-110">元件</span><span class="sxs-lookup"><span data-stu-id="63ad6-110">Component</span></span>|<span data-ttu-id="63ad6-111">0</span><span class="sxs-lookup"><span data-stu-id="63ad6-111">0</span></span>|  
|<span data-ttu-id="63ad6-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="63ad6-112">Symbolic Name</span></span>|<span data-ttu-id="63ad6-113">0</span><span class="sxs-lookup"><span data-stu-id="63ad6-113">0</span></span>|  
|<span data-ttu-id="63ad6-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="63ad6-114">Message Text</span></span>|<span data-ttu-id="63ad6-115">不支援部分訊息類型。</span><span class="sxs-lookup"><span data-stu-id="63ad6-115">Message types without parts are not supported.</span></span> <span data-ttu-id="63ad6-116">更正服務描述"{0}"訊息類型 」 {1}"，然後再重新執行精靈。</span><span class="sxs-lookup"><span data-stu-id="63ad6-116">Correct service description "{0}" message type "{1}" and rerun the wizard.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="63ad6-117">說明</span><span class="sxs-lookup"><span data-stu-id="63ad6-117">Explanation</span></span>  
 <span data-ttu-id="63ad6-118">此錯誤表示嘗試從中使用的服務並沒有定義的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="63ad6-118">This error indicates the service that is trying to be consumed does not have a message type defined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="63ad6-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="63ad6-119">User Action</span></span>  
 <span data-ttu-id="63ad6-120">更正服務與適當的訊息類型，然後再次嘗試使用 （如果您擁有想要使用的 WCF 服務）。</span><span class="sxs-lookup"><span data-stu-id="63ad6-120">Correct the service with the appropriate message type and try to consume (if you own the WCF services that you are trying to consume).</span></span> <span data-ttu-id="63ad6-121">否則，請連絡服務提供者。</span><span class="sxs-lookup"><span data-stu-id="63ad6-121">Otherwise, contact the serviced provider.</span></span>  <span data-ttu-id="63ad6-122">如需有關訊息的詳細資訊，請參閱下列資源中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="63ad6-122">For additional information on messages, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Help:</span></span>  
  
-   [<span data-ttu-id="63ad6-123">建構 Web 訊息</span><span class="sxs-lookup"><span data-stu-id="63ad6-123">Constructing Web Messages</span></span>](../core/constructing-web-messages.md)