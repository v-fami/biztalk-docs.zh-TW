---
title: 組態錯誤。 對單向 HTTP 要求同步 MDN 的傳送埠 |Microsoft Docs
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
ms.openlocfilehash: 0118789db8e45b096f3852aef3487416d388961d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014143"
---
# <a name="configuration-error-synchronous-mdn-requested-on-one-way-http-send-port"></a><span data-ttu-id="9f52a-103">組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="9f52a-103">Configuration error.</span></span> <span data-ttu-id="9f52a-104">對單向 HTTP 要求同步 MDN 的傳送埠</span><span class="sxs-lookup"><span data-stu-id="9f52a-104">Synchronous MDN requested on one way HTTP send port</span></span>
## <a name="details"></a><span data-ttu-id="9f52a-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9f52a-105">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="9f52a-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9f52a-106">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="9f52a-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="9f52a-107">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="9f52a-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9f52a-108">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="9f52a-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="9f52a-109">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9f52a-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="9f52a-110"> EDI</span></span> |
|    <span data-ttu-id="9f52a-111">元件</span><span class="sxs-lookup"><span data-stu-id="9f52a-111">Component</span></span>    |                                       <span data-ttu-id="9f52a-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="9f52a-112">EDI Engine</span></span>                                       |
|  <span data-ttu-id="9f52a-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9f52a-113">Symbolic Name</span></span>  |                                           -                                            |
|  <span data-ttu-id="9f52a-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9f52a-114">Message Text</span></span>   |       <span data-ttu-id="9f52a-115">組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="9f52a-115">Configuration error.</span></span> <span data-ttu-id="9f52a-116">對單向 HTTP 傳送埠要求同步 MDN。</span><span class="sxs-lookup"><span data-stu-id="9f52a-116">Synchronous MDN requested on one way HTTP send port.</span></span>        |
  
## <a name="explanation"></a><span data-ttu-id="9f52a-117">說明</span><span class="sxs-lookup"><span data-stu-id="9f52a-117">Explanation</span></span>  
 <span data-ttu-id="9f52a-118">這個錯誤/警告/資訊事件表示 BizTalk Server 無法在之後因為 HTTP 傳送埠傳送 AS2 訊息是單向連接埠傳送 AS2 訊息接收同步 MDN。</span><span class="sxs-lookup"><span data-stu-id="9f52a-118">This Error/Warning/Information event indicates that BizTalk Server could not receive a synchronous MDN after sending an AS2 message because the HTTP send port that sent the AS2 message was a one-way port.</span></span> <span data-ttu-id="9f52a-119">雙向請求-回應傳送埠，才能使用連接埠傳送 AS2 訊息的回應傳回同步 MDN 的程序。</span><span class="sxs-lookup"><span data-stu-id="9f52a-119">A two-way solicit-response send port is required to process a synchronous MDN returned in response to an AS2 message sent by the port.</span></span> <span data-ttu-id="9f52a-120">在此情況下，因為在做為 AS2 訊息接收者的合作對象設定中，勾選 [要求 MDN] 屬性，並清除 [要求非同步 MDN] 屬性，必須是以同步方式傳回 MDN。</span><span class="sxs-lookup"><span data-stu-id="9f52a-120">In this case, the MDN must be returned synchronously because in the configuration for the party as an AS2 Message Receiver, the Request MDN property is checked, and the Request asynchronous MDN property is cleared.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9f52a-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9f52a-121">User Action</span></span>  
 <span data-ttu-id="9f52a-122">若要解決這個錯誤，變更傳送埠傳送 AS2 訊息為 靜態請求-回應傳送埠，而不是單向傳送埠。</span><span class="sxs-lookup"><span data-stu-id="9f52a-122">To resolve this error, change the send port that is sending the AS2 message to be a static solicit-response send port, rather than a one-way send port.</span></span> <span data-ttu-id="9f52a-123">請求-回應的接收管線設定為 AS2EdiReceive EDI 交換或 AS2Receive，適用於非 EDI 交換的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="9f52a-123">Set the receive pipeline of the solicit-response send port to be AS2EdiReceive for an EDI interchange or AS2Receive for a non-EDI interchange.</span></span>