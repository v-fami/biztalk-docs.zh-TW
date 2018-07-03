---
title: 組態錯誤。 對單向 HTTP 要求同步 MDN 的接收埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f140c7a4-46bf-4557-9679-cdaf2fbe66f4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1d0d6e78830c06c11c4c6f54789ba522cfaf366
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004727"
---
# <a name="configuration-error-synchronous-mdn-requested-on-a-one-way-http-receive-port"></a><span data-ttu-id="a7b2b-103">組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="a7b2b-103">Configuration error.</span></span> <span data-ttu-id="a7b2b-104">對單向 HTTP 接收埠要求同步 MDN</span><span class="sxs-lookup"><span data-stu-id="a7b2b-104">Synchronous MDN requested on a one way HTTP receive Port</span></span>
## <a name="details"></a><span data-ttu-id="a7b2b-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a7b2b-105">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="a7b2b-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a7b2b-106">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="a7b2b-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="a7b2b-107">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="a7b2b-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a7b2b-108">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="a7b2b-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="a7b2b-109">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a7b2b-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="a7b2b-110"> EDI</span></span> |
|    <span data-ttu-id="a7b2b-111">元件</span><span class="sxs-lookup"><span data-stu-id="a7b2b-111">Component</span></span>    |                                       <span data-ttu-id="a7b2b-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="a7b2b-112">EDI Engine</span></span>                                       |
|  <span data-ttu-id="a7b2b-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a7b2b-113">Symbolic Name</span></span>  |                                           -                                            |
|  <span data-ttu-id="a7b2b-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a7b2b-114">Message Text</span></span>   |       <span data-ttu-id="a7b2b-115">組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="a7b2b-115">Configuration error.</span></span> <span data-ttu-id="a7b2b-116">對單向 HTTP 傳送埠要求同步 MDN。</span><span class="sxs-lookup"><span data-stu-id="a7b2b-116">Synchronous MDN requested on one way HTTP send port.</span></span>        |
  
## <a name="explanation"></a><span data-ttu-id="a7b2b-117">說明</span><span class="sxs-lookup"><span data-stu-id="a7b2b-117">Explanation</span></span>  
 <span data-ttu-id="a7b2b-118">這個錯誤/警告/資訊事件表示 BizTalk Server 無法在接收 AS2 訊息之後傳回同步的 MDN，因為處理內送 AS2 訊息的 HTTP 接收埠是單向連接埠。</span><span class="sxs-lookup"><span data-stu-id="a7b2b-118">This Error/Warning/Information event indicates that BizTalk Server could not return a synchronous MDN after receiving an AS2 message because the HTTP receive port that processed the incoming AS2 message was a one-way port.</span></span> <span data-ttu-id="a7b2b-119">雙向要求-回應接收埠，才能傳回同步 MDN 以回應內送 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="a7b2b-119">A two-way request-response receive port is required to return a synchronous MDN in response to an incoming AS2 message.</span></span> <span data-ttu-id="a7b2b-120">在此情況下，MDN 就必須傳回同步因為 AS2 訊息包含配置通知至 標頭或合作對象當做 AS2 訊息傳送者，會檢查傳入的訊息內容屬性的覆寫，產生的組態勾選 MDN 屬性，以及傳輸 MDN 屬性是以非同步方式清除。</span><span class="sxs-lookup"><span data-stu-id="a7b2b-120">In this case, the MDN must be returned synchronously because the AS2 message includes the Disposition-Notification-To header, or in the configuration for the party as an AS2 Message Sender, the Override inbound message properties property is checked, the Generate MDN property is checked, and the Transmit MDN asynchronously property is cleared.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a7b2b-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a7b2b-121">User Action</span></span>  
 <span data-ttu-id="a7b2b-122">若要解決這個錯誤，變更會接收 AS2 訊息是要求回應接收埠，接收埠，而不是單向接收埠。</span><span class="sxs-lookup"><span data-stu-id="a7b2b-122">To resolve this error, change the receive port that is receiving the AS2 message to be a request response receive port, rather than a one-way receive port.</span></span> <span data-ttu-id="a7b2b-123">設定傳送管線的要求回應接收非 EDI 交換是 AS2EdiSend EDI 交換或 AS2Send 的位置。</span><span class="sxs-lookup"><span data-stu-id="a7b2b-123">Set the send pipeline of the request response receive location to be AS2EdiSend for an EDI interchange or AS2Send for a non-EDI interchange.</span></span>