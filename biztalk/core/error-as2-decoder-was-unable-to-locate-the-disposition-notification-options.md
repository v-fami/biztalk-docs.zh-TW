---
title: AS2 解碼器找不到配置通知選項 HTTP 標頭 |Microsoft 文件
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
ms.openlocfilehash: 966860c7f2b7b47187b861ed6b81fb14a4753872
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240014"
---
# <a name="the-as2-decoder-was-unable-to-locate-the-disposition-notification-options-http-header"></a><span data-ttu-id="bda2d-102">AS2 解碼器找不到配置通知選項 HTTP 標頭</span><span class="sxs-lookup"><span data-stu-id="bda2d-102">The AS2 Decoder was unable to locate the Disposition-Notification-Options HTTP header</span></span>
## <a name="details"></a><span data-ttu-id="bda2d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bda2d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bda2d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bda2d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="bda2d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="bda2d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="bda2d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bda2d-106">Event ID</span></span>|-|  
|<span data-ttu-id="bda2d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="bda2d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="bda2d-108">EDI</span><span class="sxs-lookup"><span data-stu-id="bda2d-108"> EDI</span></span>|  
|<span data-ttu-id="bda2d-109">元件</span><span class="sxs-lookup"><span data-stu-id="bda2d-109">Component</span></span>|<span data-ttu-id="bda2d-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="bda2d-110">AS2 Engine</span></span>|  
|<span data-ttu-id="bda2d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bda2d-111">Symbolic Name</span></span>|<span data-ttu-id="bda2d-112">AS2DecoderMissingDispositionNotificationOptionsHTTPHeaderError</span><span class="sxs-lookup"><span data-stu-id="bda2d-112">AS2DecoderMissingDispositionNotificationOptionsHTTPHeaderError</span></span>|  
|<span data-ttu-id="bda2d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bda2d-113">Message Text</span></span>|<span data-ttu-id="bda2d-114">AS2 解碼器找不到產生 MDN 所需的 Disposition-Notification-Options HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="bda2d-114">The AS2 Decoder was unable to locate the Disposition-Notification-Options HTTP header which is required for MDN generation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bda2d-115">說明</span><span class="sxs-lookup"><span data-stu-id="bda2d-115">Explanation</span></span>  
 <span data-ttu-id="bda2d-116">這個錯誤/警告/資訊事件表示，接收管線無法產生 MDN 因為內送 AS2 訊息不含配置通知選項標頭，指出是否必須簽署 MDN 的 MIC 和必須使用演算法。</span><span class="sxs-lookup"><span data-stu-id="bda2d-116">This Error/Warning/Information event indicates that the receive pipeline could not generate the MDN because the incoming AS2 message did not include the Disposition-Notification-Options header that indicates whether the MDN must be signed and which MIC algorithm must be used.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bda2d-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bda2d-117">User Action</span></span>  
 <span data-ttu-id="bda2d-118">若要解決這個錯誤，讓傳送者的 AS2 訊息的訊息中包含配置通知選項標頭，然後再重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="bda2d-118">To resolve this error, have the sender of the AS2 message include the Disposition-Notification-Options header in the message and then resend the message.</span></span>