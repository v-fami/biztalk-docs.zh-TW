---
title: 訊息類型不支援組件沒有 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0bfb042-feda-4282-a7fa-c13be4ff6254
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60bb78e2bbf06ff80315bd9bbc2b33346ed18d5d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024164"
---
# <a name="message-types-without-parts-are-not-supported"></a><span data-ttu-id="d37fd-102">不支援沒有部分的訊息類型</span><span class="sxs-lookup"><span data-stu-id="d37fd-102">Message types without parts are not supported</span></span>
## <a name="details"></a><span data-ttu-id="d37fd-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d37fd-103">Details</span></span>  
  
|                 |                                                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="d37fd-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d37fd-104">Product Name</span></span>   |                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                     |
| <span data-ttu-id="d37fd-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d37fd-105">Product Version</span></span> |                                [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                 |
|    <span data-ttu-id="d37fd-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d37fd-106">Event ID</span></span>     |                                                             <span data-ttu-id="d37fd-107">0</span><span class="sxs-lookup"><span data-stu-id="d37fd-107">0</span></span>                                                             |
|  <span data-ttu-id="d37fd-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="d37fd-108">Event Source</span></span>   |                                                             <span data-ttu-id="d37fd-109">0</span><span class="sxs-lookup"><span data-stu-id="d37fd-109">0</span></span>                                                             |
|    <span data-ttu-id="d37fd-110">元件</span><span class="sxs-lookup"><span data-stu-id="d37fd-110">Component</span></span>    |                                                             <span data-ttu-id="d37fd-111">0</span><span class="sxs-lookup"><span data-stu-id="d37fd-111">0</span></span>                                                             |
|  <span data-ttu-id="d37fd-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d37fd-112">Symbolic Name</span></span>  |                                                             <span data-ttu-id="d37fd-113">0</span><span class="sxs-lookup"><span data-stu-id="d37fd-113">0</span></span>                                                             |
|  <span data-ttu-id="d37fd-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d37fd-114">Message Text</span></span>   | <span data-ttu-id="d37fd-115">不支援沒有部分的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="d37fd-115">Message types without parts are not supported.</span></span> <span data-ttu-id="d37fd-116">更正服務描述"{0}」 訊息類型"{1}」 並返回精靈。</span><span class="sxs-lookup"><span data-stu-id="d37fd-116">Correct service description "{0}" message type "{1}" and rerun the wizard.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="d37fd-117">說明</span><span class="sxs-lookup"><span data-stu-id="d37fd-117">Explanation</span></span>  
 <span data-ttu-id="d37fd-118">此錯誤表示嘗試從中使用的服務並沒有定義的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="d37fd-118">This error indicates the service that is trying to be consumed does not have a message type defined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d37fd-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d37fd-119">User Action</span></span>  
 <span data-ttu-id="d37fd-120">更正服務與適當的訊息類型，然後再次嘗試使用 （如果您擁有想要使用的 WCF 服務時）。</span><span class="sxs-lookup"><span data-stu-id="d37fd-120">Correct the service with the appropriate message type and try to consume (if you own the WCF services that you are trying to consume).</span></span> <span data-ttu-id="d37fd-121">否則，請連絡服務提供者。</span><span class="sxs-lookup"><span data-stu-id="d37fd-121">Otherwise, contact the serviced provider.</span></span>  <span data-ttu-id="d37fd-122">如需其他有關訊息的詳細資訊，請參閱下列資源中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="d37fd-122">For additional information on messages, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Help:</span></span>  
  
-   [<span data-ttu-id="d37fd-123">建構 Web 訊息</span><span class="sxs-lookup"><span data-stu-id="d37fd-123">Constructing Web Messages</span></span>](../core/constructing-web-messages.md)