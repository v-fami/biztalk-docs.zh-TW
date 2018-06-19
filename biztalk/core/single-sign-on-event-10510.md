---
title: 單一登入： 事件 10510 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4553ad4c-9553-4b8b-b3a3-72aed2a61202
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 053f75541597e3b2e721c53714aaaf8517c3c49f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271254"
---
# <a name="single-sign-on-event-10510"></a><span data-ttu-id="9de73-102">單一登入： 事件 10510</span><span class="sxs-lookup"><span data-stu-id="9de73-102">Single Sign-On: Event 10510</span></span>
## <a name="details"></a><span data-ttu-id="9de73-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9de73-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9de73-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9de73-104">Product Name</span></span>|<span data-ttu-id="9de73-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="9de73-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="9de73-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="9de73-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="9de73-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9de73-107">Event ID</span></span>|<span data-ttu-id="9de73-108">10510</span><span class="sxs-lookup"><span data-stu-id="9de73-108">10510</span></span>|  
|<span data-ttu-id="9de73-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="9de73-109">Event Source</span></span>|<span data-ttu-id="9de73-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="9de73-110">ENTSSO</span></span>|  
|<span data-ttu-id="9de73-111">元件</span><span class="sxs-lookup"><span data-stu-id="9de73-111">Component</span></span>|<span data-ttu-id="9de73-112">N\A</span><span class="sxs-lookup"><span data-stu-id="9de73-112">N\A</span></span>|  
|<span data-ttu-id="9de73-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9de73-113">Symbolic Name</span></span>|<span data-ttu-id="9de73-114">SSO_INFO_DLL_LOAD_FAILED</span><span class="sxs-lookup"><span data-stu-id="9de73-114">SSO_INFO_DLL_LOAD_FAILED</span></span>|  
|<span data-ttu-id="9de73-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9de73-115">Message Text</span></span>|<span data-ttu-id="9de73-116">無法載入 %1。</span><span class="sxs-lookup"><span data-stu-id="9de73-116">Failed to load %1.</span></span> <span data-ttu-id="9de73-117">請檢查此檔案可用。</span><span class="sxs-lookup"><span data-stu-id="9de73-117">Check that this file is available.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9de73-118">說明</span><span class="sxs-lookup"><span data-stu-id="9de73-118">Explanation</span></span>  
 <span data-ttu-id="9de73-119">這個資訊事件表示 SSO 服務已無法載入的 DLL。</span><span class="sxs-lookup"><span data-stu-id="9de73-119">This Information event indicates that the SSO service has failed to load the DLL.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9de73-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9de73-120">User Action</span></span>  
 <span data-ttu-id="9de73-121">若要解決此事件，執行下列一或多個項目：</span><span class="sxs-lookup"><span data-stu-id="9de73-121">To resolve this event, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="9de73-122">請確認 DLL 位於 SSO 安裝目錄中，通常是 C:\Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="9de73-122">Verify the DLL is located in the SSO installation directory, typically C:\Program Files\Common Files\Enterprise Single Sign-On.</span></span> <span data-ttu-id="9de73-123">您的 SSO 安裝目錄可能會不同。</span><span class="sxs-lookup"><span data-stu-id="9de73-123">Your SSO installation directory may be different.</span></span>  
  
-   <span data-ttu-id="9de73-124">如果單一 DLL 遺失或損毀，嘗試取代它，然後重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="9de73-124">If the single DLL is missing or corrupted, attempt to replace it and then restart the service.</span></span>  
  
 <span data-ttu-id="9de73-125">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="9de73-125">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="9de73-126">實作企業單一登入</span><span class="sxs-lookup"><span data-stu-id="9de73-126">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)