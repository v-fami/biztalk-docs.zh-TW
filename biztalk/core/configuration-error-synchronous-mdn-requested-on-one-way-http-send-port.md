---
title: 組態錯誤。 對單向 HTTP 要求同步 MDN 的傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bd38eb3-321f-4738-b35e-390f4f54673e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a0a240593aa21b102c401a2a6886ea24baa42c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231894"
---
# <a name="configuration-error-synchronous-mdn-requested-on-one-way-http-send-port"></a><span data-ttu-id="74335-103">組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="74335-103">Configuration error.</span></span> <span data-ttu-id="74335-104">對單向 HTTP 要求同步 MDN 的傳送埠</span><span class="sxs-lookup"><span data-stu-id="74335-104">Synchronous MDN requested on one way HTTP send port</span></span>
## <a name="details"></a><span data-ttu-id="74335-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="74335-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74335-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="74335-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="74335-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="74335-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="74335-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="74335-108">Event ID</span></span>|-|  
|<span data-ttu-id="74335-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="74335-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="74335-110">EDI</span><span class="sxs-lookup"><span data-stu-id="74335-110"> EDI</span></span>|  
|<span data-ttu-id="74335-111">元件</span><span class="sxs-lookup"><span data-stu-id="74335-111">Component</span></span>|<span data-ttu-id="74335-112">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="74335-112">EDI Engine</span></span>|  
|<span data-ttu-id="74335-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="74335-113">Symbolic Name</span></span>|-|  
|<span data-ttu-id="74335-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="74335-114">Message Text</span></span>|<span data-ttu-id="74335-115">組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="74335-115">Configuration error.</span></span> <span data-ttu-id="74335-116">對單向 HTTP 傳送埠要求同步 MDN。</span><span class="sxs-lookup"><span data-stu-id="74335-116">Synchronous MDN requested on one way HTTP send port.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="74335-117">說明</span><span class="sxs-lookup"><span data-stu-id="74335-117">Explanation</span></span>  
 <span data-ttu-id="74335-118">這個錯誤/警告/資訊事件表示 BizTalk Server 無法接收同步 MDN 傳送 AS2 訊息，因為 HTTP 傳送埠傳送 AS2 訊息是單向連接埠之後。</span><span class="sxs-lookup"><span data-stu-id="74335-118">This Error/Warning/Information event indicates that BizTalk Server could not receive a synchronous MDN after sending an AS2 message because the HTTP send port that sent the AS2 message was a one-way port.</span></span> <span data-ttu-id="74335-119">雙向請求-回應傳送埠，才能由連接埠傳送 AS2 訊息的回應傳回同步 MDN 的程序。</span><span class="sxs-lookup"><span data-stu-id="74335-119">A two-way solicit-response send port is required to process a synchronous MDN returned in response to an AS2 message sent by the port.</span></span> <span data-ttu-id="74335-120">在此情況下，因為在做為 AS2 訊息接收者的合作對象設定中，勾選 [要求 MDN] 屬性，並清除 [要求非同步 MDN] 屬性，必須是以同步方式傳回 MDN。</span><span class="sxs-lookup"><span data-stu-id="74335-120">In this case, the MDN must be returned synchronously because in the configuration for the party as an AS2 Message Receiver, the Request MDN property is checked, and the Request asynchronous MDN property is cleared.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="74335-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="74335-121">User Action</span></span>  
 <span data-ttu-id="74335-122">若要解決這個錯誤，變更傳送埠傳送 AS2 訊息靜態請求-回應傳送埠，而非單向傳送埠。</span><span class="sxs-lookup"><span data-stu-id="74335-122">To resolve this error, change the send port that is sending the AS2 message to be a static solicit-response send port, rather than a one-way send port.</span></span> <span data-ttu-id="74335-123">設定接收管線的請求-回應傳送埠的非 EDI 交換的是 AS2EdiReceive EDI 交換或 AS2Receive。</span><span class="sxs-lookup"><span data-stu-id="74335-123">Set the receive pipeline of the solicit-response send port to be AS2EdiReceive for an EDI interchange or AS2Receive for a non-EDI interchange.</span></span>