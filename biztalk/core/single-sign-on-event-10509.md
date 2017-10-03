---
title: "單一登入： 事件 10509 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f906823f-db3f-45fc-bf61-cbe6a9566bd7
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4d61cbb7af195aa88c36b64149366334c835b80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10509"></a><span data-ttu-id="dff7c-102">單一登入： 事件 10509</span><span class="sxs-lookup"><span data-stu-id="dff7c-102">Single Sign-On: Event 10509</span></span>
## <a name="details"></a><span data-ttu-id="dff7c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dff7c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dff7c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="dff7c-104">Product Name</span></span>|<span data-ttu-id="dff7c-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="dff7c-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="dff7c-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="dff7c-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="dff7c-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="dff7c-107">Event ID</span></span>|<span data-ttu-id="dff7c-108">10509</span><span class="sxs-lookup"><span data-stu-id="dff7c-108">10509</span></span>|  
|<span data-ttu-id="dff7c-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="dff7c-109">Event Source</span></span>|<span data-ttu-id="dff7c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="dff7c-110">ENTSSO</span></span>|  
|<span data-ttu-id="dff7c-111">元件</span><span class="sxs-lookup"><span data-stu-id="dff7c-111">Component</span></span>|<span data-ttu-id="dff7c-112">N\A</span><span class="sxs-lookup"><span data-stu-id="dff7c-112">N\A</span></span>|  
|<span data-ttu-id="dff7c-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="dff7c-113">Symbolic Name</span></span>|<span data-ttu-id="dff7c-114">SSO_INFO_SERVICE_REMOVE_FAILED</span><span class="sxs-lookup"><span data-stu-id="dff7c-114">SSO_INFO_SERVICE_REMOVE_FAILED</span></span>|  
|<span data-ttu-id="dff7c-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="dff7c-115">Message Text</span></span>|<span data-ttu-id="dff7c-116">無法移除 SSO service.%r</span><span class="sxs-lookup"><span data-stu-id="dff7c-116">Failed to remove the SSO service.%r</span></span><br /><br /> <span data-ttu-id="dff7c-117">錯誤碼： %1</span><span class="sxs-lookup"><span data-stu-id="dff7c-117">Error Code: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dff7c-118">說明</span><span class="sxs-lookup"><span data-stu-id="dff7c-118">Explanation</span></span>  
 <span data-ttu-id="dff7c-119">此事件表示 ENTSSO 服務無法解除安裝。</span><span class="sxs-lookup"><span data-stu-id="dff7c-119">This event indicates that the ENTSSO Service failed to uninstall.</span></span> <span data-ttu-id="dff7c-120">只可以在手動解除安裝的企業單一登入期間會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="dff7c-120">This event can only occur during a manual uninstallation of Enterprise Single Sign-On.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dff7c-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="dff7c-121">User Action</span></span>  
 <span data-ttu-id="dff7c-122">若要解決此事件，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="dff7c-122">To resolve this event, do the following:</span></span>  
  
-   <span data-ttu-id="dff7c-123">請檢查 ENTSSO 或其他服務的相關錯誤的應用程式和系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="dff7c-123">Check both the Application and System event logs for related errors from ENTSSO or other services.</span></span>  
  
 <span data-ttu-id="dff7c-124">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="dff7c-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="dff7c-125">安裝 SSO</span><span class="sxs-lookup"><span data-stu-id="dff7c-125">Installing SSO</span></span>](../core/installing-sso.md)  
  
-   [<span data-ttu-id="dff7c-126">實作企業單一登入</span><span class="sxs-lookup"><span data-stu-id="dff7c-126">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)