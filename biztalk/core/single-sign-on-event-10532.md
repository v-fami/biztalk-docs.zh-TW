---
title: "單一登入： 事件 10532 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae2112bc-b53c-4d99-9dc1-a2f55dda4665
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7a9d477ec54a3c959f2afdf4c687c65b88523ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10532"></a><span data-ttu-id="906cc-102">單一登入： 事件 10532</span><span class="sxs-lookup"><span data-stu-id="906cc-102">Single Sign-On: Event 10532</span></span>
## <a name="details"></a><span data-ttu-id="906cc-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="906cc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="906cc-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="906cc-104">Product Name</span></span>|<span data-ttu-id="906cc-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="906cc-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="906cc-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="906cc-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="906cc-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="906cc-107">Event ID</span></span>|<span data-ttu-id="906cc-108">10532</span><span class="sxs-lookup"><span data-stu-id="906cc-108">10532</span></span>|  
|<span data-ttu-id="906cc-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="906cc-109">Event Source</span></span>|<span data-ttu-id="906cc-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="906cc-110">ENTSSO</span></span>|  
|<span data-ttu-id="906cc-111">元件</span><span class="sxs-lookup"><span data-stu-id="906cc-111">Component</span></span>|<span data-ttu-id="906cc-112">CO</span><span class="sxs-lookup"><span data-stu-id="906cc-112">CO</span></span>|  
|<span data-ttu-id="906cc-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="906cc-113">Symbolic Name</span></span>|<span data-ttu-id="906cc-114">SSO_WARN_LOST_SECRET_SERVER</span><span class="sxs-lookup"><span data-stu-id="906cc-114">SSO_WARN_LOST_SECRET_SERVER</span></span>|  
|<span data-ttu-id="906cc-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="906cc-115">Message Text</span></span>|<span data-ttu-id="906cc-116">無法擷取主要密碼。</span><span class="sxs-lookup"><span data-stu-id="906cc-116">Failed to retrieve master secrets.</span></span> <span data-ttu-id="906cc-117">確認主要密碼伺服器名稱是否正確以及是否可用。%r</span><span class="sxs-lookup"><span data-stu-id="906cc-117">Verify that the master secret server name is correct and that it is available.%r</span></span><br /><br /> <span data-ttu-id="906cc-118">密碼伺服器名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="906cc-118">Secret Server Name: %1%r</span></span><br /><br /> <span data-ttu-id="906cc-119">錯誤碼： %2</span><span class="sxs-lookup"><span data-stu-id="906cc-119">Error Code: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="906cc-120">說明</span><span class="sxs-lookup"><span data-stu-id="906cc-120">Explanation</span></span>  
 <span data-ttu-id="906cc-121">這個警告事件表示取得主要密碼的要求已經失敗。</span><span class="sxs-lookup"><span data-stu-id="906cc-121">This Warning event indicates that a request to get the master secret has failed.</span></span> <span data-ttu-id="906cc-122">這可能是因為「企業單一登入」服務未在伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="906cc-122">This might be because the Enterprise Single Sign-On service is not running on the server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="906cc-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="906cc-123">User Action</span></span>  
 <span data-ttu-id="906cc-124">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="906cc-124">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="906cc-125">請檢查應用程式事件記錄檔，取得相關聯的事件或錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="906cc-125">Check the Application event log for associated events or errors.</span></span>  
  
-   <span data-ttu-id="906cc-126">請確認主要密碼伺服器名稱是正確的。</span><span class="sxs-lookup"><span data-stu-id="906cc-126">Verify the master secret server name is correct.</span></span>  
  
-   <span data-ttu-id="906cc-127">請確認主要密碼伺服器連線且「企業單一登入」服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="906cc-127">Verify the master secret server is online and that the Enterprise Single Sign-On service is running.</span></span>  
  
 <span data-ttu-id="906cc-128">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="906cc-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="906cc-129">如何產生主要密碼</span><span class="sxs-lookup"><span data-stu-id="906cc-129">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  
  
-   [<span data-ttu-id="906cc-130">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="906cc-130">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)