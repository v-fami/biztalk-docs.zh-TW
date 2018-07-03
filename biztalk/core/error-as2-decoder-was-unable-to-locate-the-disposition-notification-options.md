---
title: AS2 解碼器找不到配置通知選項 HTTP 標頭 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6de4b9a6-17b2-4455-9dbd-a6bb69fac1d5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 230f0a03e1274fec7ef196ce12cc3be33ff2702b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004559"
---
# <a name="the-as2-decoder-was-unable-to-locate-the-disposition-notification-options-http-header"></a><span data-ttu-id="13c81-102">AS2 解碼器找不到配置通知選項 HTTP 標頭</span><span class="sxs-lookup"><span data-stu-id="13c81-102">The AS2 Decoder was unable to locate the Disposition-Notification-Options HTTP header</span></span>
## <a name="details"></a><span data-ttu-id="13c81-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="13c81-103">Details</span></span>  
  
|                 |                                                                                                                             |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="13c81-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="13c81-104">Product Name</span></span>   |                     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                      |
| <span data-ttu-id="13c81-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="13c81-105">Product Version</span></span> |                                 [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                  |
|    <span data-ttu-id="13c81-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="13c81-106">Event ID</span></span>     |                                                              -                                                              |
|  <span data-ttu-id="13c81-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="13c81-107">Event Source</span></span>   |                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="13c81-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="13c81-108"> EDI</span></span>                    |
|    <span data-ttu-id="13c81-109">元件</span><span class="sxs-lookup"><span data-stu-id="13c81-109">Component</span></span>    |                                                         <span data-ttu-id="13c81-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="13c81-110">AS2 Engine</span></span>                                                          |
|  <span data-ttu-id="13c81-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="13c81-111">Symbolic Name</span></span>  |                               <span data-ttu-id="13c81-112">AS2DecoderMissingDispositionNotificationOptionsHTTPHeaderError</span><span class="sxs-lookup"><span data-stu-id="13c81-112">AS2DecoderMissingDispositionNotificationOptionsHTTPHeaderError</span></span>                                |
|  <span data-ttu-id="13c81-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="13c81-113">Message Text</span></span>   | <span data-ttu-id="13c81-114">AS2 解碼器找不到產生 MDN 所需的 Disposition-Notification-Options HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="13c81-114">The AS2 Decoder was unable to locate the Disposition-Notification-Options HTTP header which is required for MDN generation.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="13c81-115">說明</span><span class="sxs-lookup"><span data-stu-id="13c81-115">Explanation</span></span>  
 <span data-ttu-id="13c81-116">這個錯誤/警告/資訊事件表示，接收管線無法產生 MDN 因為內送 AS2 訊息未包含配置通知選項標頭，指出是否必須簽署 MDN 的 MIC 和必須使用演算法。</span><span class="sxs-lookup"><span data-stu-id="13c81-116">This Error/Warning/Information event indicates that the receive pipeline could not generate the MDN because the incoming AS2 message did not include the Disposition-Notification-Options header that indicates whether the MDN must be signed and which MIC algorithm must be used.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="13c81-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="13c81-117">User Action</span></span>  
 <span data-ttu-id="13c81-118">若要解決這個錯誤，有 寄件者的 AS2 訊息處置通知選項標頭包含在訊息，然後再重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="13c81-118">To resolve this error, have the sender of the AS2 message include the Disposition-Notification-Options header in the message and then resend the message.</span></span>