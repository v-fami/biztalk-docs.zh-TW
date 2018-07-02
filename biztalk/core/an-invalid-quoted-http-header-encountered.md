---
title: 無效且具引號的 HTTP 標頭發生 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb530ee6-ec6a-4791-ae99-b9db426c0896
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ca0d7463f4604e8a159c12fab690e494a13fb60
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971007"
---
# <a name="an-invalid-quoted-http-header-encountered"></a><span data-ttu-id="07fb4-102">無效且具引號的 HTTP 標頭發生</span><span class="sxs-lookup"><span data-stu-id="07fb4-102">An invalid quoted HTTP header encountered</span></span>
## <a name="details"></a><span data-ttu-id="07fb4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="07fb4-103">Details</span></span>  
  
|                 |                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="07fb4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="07fb4-104">Product Name</span></span>   |              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]              |
| <span data-ttu-id="07fb4-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="07fb4-105">Product Version</span></span> |                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                          |
|    <span data-ttu-id="07fb4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="07fb4-106">Event ID</span></span>     |                                                      -                                                       |
|  <span data-ttu-id="07fb4-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="07fb4-107">Event Source</span></span>   |            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="07fb4-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="07fb4-108"> EDI</span></span>            |
|    <span data-ttu-id="07fb4-109">元件</span><span class="sxs-lookup"><span data-stu-id="07fb4-109">Component</span></span>    |                                                  <span data-ttu-id="07fb4-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="07fb4-110">AS2 Engine</span></span>                                                  |
|  <span data-ttu-id="07fb4-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="07fb4-111">Symbolic Name</span></span>  |                                                      -                                                       |
|  <span data-ttu-id="07fb4-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="07fb4-112">Message Text</span></span>   | <span data-ttu-id="07fb4-113">發現無效且具引號的 HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="07fb4-113">An invalid quoted HTTP header encountered.</span></span>  <span data-ttu-id="07fb4-114">詳細資料如下： 標頭名稱:"{0}"標頭值:"{1}」</span><span class="sxs-lookup"><span data-stu-id="07fb4-114">Details are as follows:  Header Name: "{0}"  Header Value: "{1}"</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="07fb4-115">說明</span><span class="sxs-lookup"><span data-stu-id="07fb4-115">Explanation</span></span>  
 <span data-ttu-id="07fb4-116">這個錯誤/警告/資訊事件表示，AS2 接收管線或 AS2 傳送管線無法處理 AS2 訊息，因為 AS2 的名稱-從或 AS2-以 HTTP 標頭，訊息中的不正確地括住。</span><span class="sxs-lookup"><span data-stu-id="07fb4-116">This Error/Warning/Information event indicates that the AS2 receive pipeline or the AS2 send pipeline could not process the AS2 message because the name of the AS2-From or AS2-To HTTP header in the message was not quoted correctly.</span></span> <span data-ttu-id="07fb4-117">標頭名稱已加上引號，以容納空間、 反斜線或雙引號括住名稱。</span><span class="sxs-lookup"><span data-stu-id="07fb4-117">The header name is quoted in order to accommodate a space, backslash, or double quotes within the name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="07fb4-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="07fb4-118">User Action</span></span>  
 <span data-ttu-id="07fb4-119">若要解決這個錯誤，引號 AS2 訊息，根據規則中的標頭名稱一節所述 6.2，「 AS2 系統識別碼 」，RFC 4130 「 以 MIME 為基礎安全端對端商務資料交換使用 HTTP，Applicability Statement 2 (AS2) 」。</span><span class="sxs-lookup"><span data-stu-id="07fb4-119">To resolve this error, quote the header name in the AS2 message in accordance with the rules stated in section 6.2, "AS2 System Identifiers", in RFC 4130, "MIME-Based Secure Peer-to-Peer Business Data Interchange Using HTTP, Applicability Statement 2 (AS2)".</span></span>