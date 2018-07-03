---
title: 訊息部分遺失元素 |Microsoft Docs
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
ms.openlocfilehash: 412b25d2f7ea027de53818b032b50562faab9865
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009439"
---
# <a name="message-part-missing-element"></a><span data-ttu-id="55534-102">訊息部分遺失元素</span><span class="sxs-lookup"><span data-stu-id="55534-102">Message part missing element</span></span>
## <a name="details"></a><span data-ttu-id="55534-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="55534-103">Details</span></span>  
  
|                 |                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="55534-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="55534-104">Product Name</span></span>   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                 |
| <span data-ttu-id="55534-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="55534-105">Product Version</span></span> |                             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                             |
|    <span data-ttu-id="55534-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="55534-106">Event ID</span></span>     |                                                         <span data-ttu-id="55534-107">0</span><span class="sxs-lookup"><span data-stu-id="55534-107">0</span></span>                                                          |
|  <span data-ttu-id="55534-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="55534-108">Event Source</span></span>   |                                                         <span data-ttu-id="55534-109">0</span><span class="sxs-lookup"><span data-stu-id="55534-109">0</span></span>                                                          |
|    <span data-ttu-id="55534-110">元件</span><span class="sxs-lookup"><span data-stu-id="55534-110">Component</span></span>    |                                                         <span data-ttu-id="55534-111">0</span><span class="sxs-lookup"><span data-stu-id="55534-111">0</span></span>                                                          |
|  <span data-ttu-id="55534-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="55534-112">Symbolic Name</span></span>  |                                                         <span data-ttu-id="55534-113">0</span><span class="sxs-lookup"><span data-stu-id="55534-113">0</span></span>                                                          |
|  <span data-ttu-id="55534-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="55534-114">Message Text</span></span>   | <span data-ttu-id="55534-115">訊息部分遺失元素。</span><span class="sxs-lookup"><span data-stu-id="55534-115">Message part missing element.</span></span> <span data-ttu-id="55534-116">更正服務描述"{0}」 訊息類型 」{1}「 部分 」{2}"，然後重新執行精靈</span><span class="sxs-lookup"><span data-stu-id="55534-116">Correct service description "{0}" message type "{1}" part "{2}" and rerun the wizard</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="55534-117">說明</span><span class="sxs-lookup"><span data-stu-id="55534-117">Explanation</span></span>  
 <span data-ttu-id="55534-118">此錯誤表示嘗試從中使用的服務並沒有用來識別訊息類型的元素標記。</span><span class="sxs-lookup"><span data-stu-id="55534-118">This error indicates the service that is trying to be consumed does not have the element tag identifying the type of message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="55534-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="55534-119">User Action</span></span>  
 <span data-ttu-id="55534-120">更正服務與適當的訊息類型，然後再次嘗試使用 （如果您擁有想要使用的 WCF 服務時）。</span><span class="sxs-lookup"><span data-stu-id="55534-120">Correct the service with the appropriate message type and try to consume (if you own the WCF services that you are trying to consume).</span></span> <span data-ttu-id="55534-121">否則，請連絡服務提供者。</span><span class="sxs-lookup"><span data-stu-id="55534-121">Otherwise, contact the service provider.</span></span>  
  
 <span data-ttu-id="55534-122">如需其他有關訊息的詳細資訊，請參閱下列資源中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="55534-122">For additional information on messages, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="55534-123">建構 Web 訊息</span><span class="sxs-lookup"><span data-stu-id="55534-123">Constructing Web Messages</span></span>](../core/constructing-web-messages.md)