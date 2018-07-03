---
title: 單一登入： 事件 10526 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f72d466-8b63-453c-b608-f9d64f635f65
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 433190146391c494ff3b890c8332cc15fb947753
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024452"
---
# <a name="single-sign-on-event-10526"></a><span data-ttu-id="f29bf-102">單一登入： 事件 10526</span><span class="sxs-lookup"><span data-stu-id="f29bf-102">Single Sign-On: Event 10526</span></span>
## <a name="details"></a><span data-ttu-id="f29bf-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f29bf-103">Details</span></span>  

|                 |                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="f29bf-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f29bf-104">Product Name</span></span>   |                                                                     <span data-ttu-id="f29bf-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="f29bf-105">Enterprise Single Sign-On</span></span>                                                                     |
| <span data-ttu-id="f29bf-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="f29bf-106">Product Version</span></span> |                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                     |
|    <span data-ttu-id="f29bf-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f29bf-107">Event ID</span></span>     |                                                                               <span data-ttu-id="f29bf-108">10526</span><span class="sxs-lookup"><span data-stu-id="f29bf-108">10526</span></span>                                                                               |
|  <span data-ttu-id="f29bf-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="f29bf-109">Event Source</span></span>   |                                                                              <span data-ttu-id="f29bf-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f29bf-110">ENTSSO</span></span>                                                                               |
|    <span data-ttu-id="f29bf-111">元件</span><span class="sxs-lookup"><span data-stu-id="f29bf-111">Component</span></span>    |                                                                                <span data-ttu-id="f29bf-112">N\A</span><span class="sxs-lookup"><span data-stu-id="f29bf-112">N\A</span></span>                                                                                |
|  <span data-ttu-id="f29bf-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f29bf-113">Symbolic Name</span></span>  |                                                                 <span data-ttu-id="f29bf-114">SSO_ERROR_GENERATE_SECRET_FAILED</span><span class="sxs-lookup"><span data-stu-id="f29bf-114">SSO_ERROR_GENERATE_SECRET_FAILED</span></span>                                                                  |
|  <span data-ttu-id="f29bf-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f29bf-115">Message Text</span></span>   | <span data-ttu-id="f29bf-116">無法產生新的主要密碼。%r</span><span class="sxs-lookup"><span data-stu-id="f29bf-116">Failed to generate a new master secret.%r</span></span><br /><br /> <span data-ttu-id="f29bf-117">用戶端使用者: %1 %r</span><span class="sxs-lookup"><span data-stu-id="f29bf-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="f29bf-118">用戶端電腦：%2%r</span><span class="sxs-lookup"><span data-stu-id="f29bf-118">Client Computer:%2%r</span></span><br /><br /> <span data-ttu-id="f29bf-119">追蹤識別碼: %3 %r</span><span class="sxs-lookup"><span data-stu-id="f29bf-119">Tracking ID: %3%r</span></span><br /><br /> <span data-ttu-id="f29bf-120">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="f29bf-120">Error Code: %4</span></span> |

## <a name="explanation"></a><span data-ttu-id="f29bf-121">說明</span><span class="sxs-lookup"><span data-stu-id="f29bf-121">Explanation</span></span>  
 <span data-ttu-id="f29bf-122">這個錯誤事件表示使用者嘗試產生新的主要祕密失敗。</span><span class="sxs-lookup"><span data-stu-id="f29bf-122">This Error event indicates that a user attempt to generate a new master secret has failed.</span></span> <span data-ttu-id="f29bf-123">這可能是因為權限 （您必須是 SSO 系統管理員，以產生主要祕密） 的問題，或可能有寫入備份檔案中的主要密碼的問題。</span><span class="sxs-lookup"><span data-stu-id="f29bf-123">This might be due to permissions issues (you must be an SSO Administrator to generate the master secret) or possibly there were problems writing the master secret to the backup file.</span></span> <span data-ttu-id="f29bf-124">在這些情況下應該有相關的郵件應用程式事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="f29bf-124">In these cases there should be related messages in the Application event log.</span></span>  

## <a name="user-action"></a><span data-ttu-id="f29bf-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f29bf-125">User Action</span></span>  
 <span data-ttu-id="f29bf-126">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="f29bf-126">To resolve this error, do one or more of the following:</span></span>  

- <span data-ttu-id="f29bf-127">檢查應用程式事件記錄檔相關聯的事件或錯誤。</span><span class="sxs-lookup"><span data-stu-id="f29bf-127">Check the Application event log for associated events or errors.</span></span>  

- <span data-ttu-id="f29bf-128">檢查您具備適當的 SSO 系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="f29bf-128">Check that you have the appropriate SSO Administrator permissions.</span></span>  

  <span data-ttu-id="f29bf-129">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="f29bf-129">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="f29bf-130">如何產生主要密碼</span><span class="sxs-lookup"><span data-stu-id="f29bf-130">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  

- [<span data-ttu-id="f29bf-131">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="f29bf-131">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)
