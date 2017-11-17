---
title: "無效的引號遇到的 HTTP 標頭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb530ee6-ec6a-4791-ae99-b9db426c0896
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e154e3bacf34025edd837516a15dca6f2caa174
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="an-invalid-quoted-http-header-encountered"></a><span data-ttu-id="d40d1-102">無效的引號遇到的 HTTP 標頭</span><span class="sxs-lookup"><span data-stu-id="d40d1-102">An invalid quoted HTTP header encountered</span></span>
## <a name="details"></a><span data-ttu-id="d40d1-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d40d1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d40d1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d40d1-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d40d1-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d40d1-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d40d1-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d40d1-106">Event ID</span></span>|-|  
|<span data-ttu-id="d40d1-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d40d1-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d40d1-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d40d1-108"> EDI</span></span>|  
|<span data-ttu-id="d40d1-109">元件</span><span class="sxs-lookup"><span data-stu-id="d40d1-109">Component</span></span>|<span data-ttu-id="d40d1-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="d40d1-110">AS2 Engine</span></span>|  
|<span data-ttu-id="d40d1-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d40d1-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="d40d1-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d40d1-112">Message Text</span></span>|<span data-ttu-id="d40d1-113">發現無效且具引號的 HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="d40d1-113">An invalid quoted HTTP header encountered.</span></span>  <span data-ttu-id="d40d1-114">詳細資料如下： 標頭名稱:"{0}"標頭值:"{1}"</span><span class="sxs-lookup"><span data-stu-id="d40d1-114">Details are as follows:  Header Name: "{0}"  Header Value: "{1}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d40d1-115">說明</span><span class="sxs-lookup"><span data-stu-id="d40d1-115">Explanation</span></span>  
 <span data-ttu-id="d40d1-116">這個錯誤/警告/資訊事件表示 AS2 接收管線或 AS2 傳送管線無法處理 AS2 訊息，因為 AS2 的名稱-從或 AS2 的訊息到 HTTP 標頭不正確地括住。</span><span class="sxs-lookup"><span data-stu-id="d40d1-116">This Error/Warning/Information event indicates that the AS2 receive pipeline or the AS2 send pipeline could not process the AS2 message because the name of the AS2-From or AS2-To HTTP header in the message was not quoted correctly.</span></span> <span data-ttu-id="d40d1-117">標頭名稱會以容納空格、 反斜線或在名稱中的雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="d40d1-117">The header name is quoted in order to accommodate a space, backslash, or double quotes within the name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d40d1-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d40d1-118">User Action</span></span>  
 <span data-ttu-id="d40d1-119">若要解決這個錯誤，引號標頭名稱符合規則的 AS2 訊息中一節所述 6.2，「 AS2 系統識別碼 」，RFC 4130 「 以 MIME 為基礎安全端對端商務資料交換使用 HTTP，Applicability Statement 2 (AS2) 」。</span><span class="sxs-lookup"><span data-stu-id="d40d1-119">To resolve this error, quote the header name in the AS2 message in accordance with the rules stated in section 6.2, "AS2 System Identifiers", in RFC 4130, "MIME-Based Secure Peer-to-Peer Business Data Interchange Using HTTP, Applicability Statement 2 (AS2)".</span></span>