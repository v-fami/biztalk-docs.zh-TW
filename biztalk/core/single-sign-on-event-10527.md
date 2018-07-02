---
title: 單一登入： 事件 10527 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 40995ad8-9f74-4e96-863d-427e23025ba1
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac787d375e8ccc4c578c2450b7cc6128dd427483
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972991"
---
# <a name="single-sign-on-event-10527"></a><span data-ttu-id="8902f-102">單一登入： 事件 10527</span><span class="sxs-lookup"><span data-stu-id="8902f-102">Single Sign-On: Event 10527</span></span>
## <a name="details"></a><span data-ttu-id="8902f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8902f-103">Details</span></span>  

|                 |                                                                                                                                                                                                     |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="8902f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8902f-104">Product Name</span></span>   |                                                                                      <span data-ttu-id="8902f-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="8902f-105">Enterprise Single Sign-On</span></span>                                                                                      |
| <span data-ttu-id="8902f-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="8902f-106">Product Version</span></span> |                                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                      |
|    <span data-ttu-id="8902f-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8902f-107">Event ID</span></span>     |                                                                                                <span data-ttu-id="8902f-108">10527</span><span class="sxs-lookup"><span data-stu-id="8902f-108">10527</span></span>                                                                                                |
|  <span data-ttu-id="8902f-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="8902f-109">Event Source</span></span>   |                                                                                               <span data-ttu-id="8902f-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="8902f-110">ENTSSO</span></span>                                                                                                |
|    <span data-ttu-id="8902f-111">元件</span><span class="sxs-lookup"><span data-stu-id="8902f-111">Component</span></span>    |                                                                                                  <span data-ttu-id="8902f-112">0</span><span class="sxs-lookup"><span data-stu-id="8902f-112">0</span></span>                                                                                                  |
|  <span data-ttu-id="8902f-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8902f-113">Symbolic Name</span></span>  |                                                                                     <span data-ttu-id="8902f-114">SSO_ERROR_GET_SECRET_FAILED</span><span class="sxs-lookup"><span data-stu-id="8902f-114">SSO_ERROR_GET_SECRET_FAILED</span></span>                                                                                     |
|  <span data-ttu-id="8902f-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8902f-115">Message Text</span></span>   | <span data-ttu-id="8902f-116">取得主要祕密 failed.%r 的要求</span><span class="sxs-lookup"><span data-stu-id="8902f-116">A request to get a master secret failed.%r</span></span><br /><br /> <span data-ttu-id="8902f-117">祕密號碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="8902f-117">Secret Number: %1%r</span></span><br /><br /> <span data-ttu-id="8902f-118">用戶端使用者: %2 %r</span><span class="sxs-lookup"><span data-stu-id="8902f-118">Client User: %2%r</span></span><br /><br /> <span data-ttu-id="8902f-119">用戶端電腦: %3 %r</span><span class="sxs-lookup"><span data-stu-id="8902f-119">Client Computer: %3%r</span></span><br /><br /> <span data-ttu-id="8902f-120">追蹤識別碼: %4 %r</span><span class="sxs-lookup"><span data-stu-id="8902f-120">Tracking ID: %4%r</span></span><br /><br /> <span data-ttu-id="8902f-121">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="8902f-121">Error Code: %5</span></span> |

## <a name="explanation"></a><span data-ttu-id="8902f-122">說明</span><span class="sxs-lookup"><span data-stu-id="8902f-122">Explanation</span></span>  
 <span data-ttu-id="8902f-123">這個錯誤事件表示取得主要祕密的要求已失敗。</span><span class="sxs-lookup"><span data-stu-id="8902f-123">This Error event indicates that a request to get the master secret has failed.</span></span> <span data-ttu-id="8902f-124">在這些情況下應該有相關的郵件應用程式事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="8902f-124">In these cases there should be related messages in the Application event log.</span></span>  

## <a name="user-action"></a><span data-ttu-id="8902f-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8902f-125">User Action</span></span>  
 <span data-ttu-id="8902f-126">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="8902f-126">To resolve this error, do the following:</span></span>  

- <span data-ttu-id="8902f-127">檢查應用程式事件記錄檔相關聯的事件或錯誤。</span><span class="sxs-lookup"><span data-stu-id="8902f-127">Check the Application event log for associated events or errors.</span></span>  

  <span data-ttu-id="8902f-128">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="8902f-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="8902f-129">如何產生主要密碼</span><span class="sxs-lookup"><span data-stu-id="8902f-129">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  

- [<span data-ttu-id="8902f-130">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="8902f-130">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)
