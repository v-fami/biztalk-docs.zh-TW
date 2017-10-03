---
title: "單一登入： 事件 10511 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98371982-0db5-4ae0-9f92-f05a58e23b83
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c080812d70dc78a0fe2a9b217833f961da951401
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10511"></a><span data-ttu-id="ceb22-102">單一登入： 事件 10511</span><span class="sxs-lookup"><span data-stu-id="ceb22-102">Single Sign-On: Event 10511</span></span>
## <a name="details"></a><span data-ttu-id="ceb22-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ceb22-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ceb22-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ceb22-104">Product Name</span></span>|<span data-ttu-id="ceb22-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="ceb22-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="ceb22-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="ceb22-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="ceb22-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ceb22-107">Event ID</span></span>|<span data-ttu-id="ceb22-108">10511</span><span class="sxs-lookup"><span data-stu-id="ceb22-108">10511</span></span>|  
|<span data-ttu-id="ceb22-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="ceb22-109">Event Source</span></span>|<span data-ttu-id="ceb22-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ceb22-110">ENTSSO</span></span>|  
|<span data-ttu-id="ceb22-111">元件</span><span class="sxs-lookup"><span data-stu-id="ceb22-111">Component</span></span>|<span data-ttu-id="ceb22-112">N\A</span><span class="sxs-lookup"><span data-stu-id="ceb22-112">N\A</span></span>|  
|<span data-ttu-id="ceb22-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ceb22-113">Symbolic Name</span></span>|<span data-ttu-id="ceb22-114">SSO_ERROR_NO_DSN</span><span class="sxs-lookup"><span data-stu-id="ceb22-114">SSO_ERROR_NO_DSN</span></span>|  
|<span data-ttu-id="ceb22-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ceb22-115">Message Text</span></span>|<span data-ttu-id="ceb22-116">在登錄中找不到 SQL Server 與 SSO 資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ceb22-116">The SQL Server and SSO database names were not found in the registry.</span></span> <span data-ttu-id="ceb22-117">您可以使用 SSO 管理工具來設定這些值。</span><span class="sxs-lookup"><span data-stu-id="ceb22-117">Use the SSO administration tools to configure these values.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ceb22-118">說明</span><span class="sxs-lookup"><span data-stu-id="ceb22-118">Explanation</span></span>  
 <span data-ttu-id="ceb22-119">這個錯誤事件表示 SQL Server 與 SSO 資料庫名稱不登錄中找到。</span><span class="sxs-lookup"><span data-stu-id="ceb22-119">This Error event indicates that the SQL Server and SSO database names were not found in the registry.</span></span> <span data-ttu-id="ceb22-120">SSO 服務需要這項資訊，讓它可以連接到 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ceb22-120">The SSO service requires this information so it can connect to the SSO database.</span></span> <span data-ttu-id="ceb22-121">這項資訊是在設定期間設定登錄。</span><span class="sxs-lookup"><span data-stu-id="ceb22-121">This information is set in the registry during configuration.</span></span> <span data-ttu-id="ceb22-122">這可能表示設定未正確完成，或已完成設定後，已刪除的登錄項目。</span><span class="sxs-lookup"><span data-stu-id="ceb22-122">This may indicate that configuration did not complete correctly or that the registry entries have been deleted after configuration was completed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ceb22-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ceb22-123">User Action</span></span>  
 <span data-ttu-id="ceb22-124">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="ceb22-124">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="ceb22-125">如果您懷疑較寬的組態失敗，取消設定產品，然後重新設定使用 「 組態 」 程式。</span><span class="sxs-lookup"><span data-stu-id="ceb22-125">If you suspect a wider configuration failure, unconfigure the product and then reconfigure using the configuration program.</span></span>  
  
-   <span data-ttu-id="ceb22-126">或者您可以使用 SSO 命令列工具位於 SSO 安裝目錄，通常是 C:\Program Files\Common Files\Enterprise Single Sign-on ssoconfig.exe 來設定這些特定的遺漏登錄項目。</span><span class="sxs-lookup"><span data-stu-id="ceb22-126">Alternatively these specific missing registry entries can be set using the SSO command line tool, ssoconfig.exe located in the SSO installation directory, typically C:\Program Files\Common Files\Enterprise Single Sign-On.</span></span> <span data-ttu-id="ceb22-127">您的 SSO 安裝目錄可能會不同。</span><span class="sxs-lookup"><span data-stu-id="ceb22-127">Your SSO installation directory may be different.</span></span> <span data-ttu-id="ceb22-128">使用**-setDB**選項可用來設定必要的 SQL Server 與 SSO 資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ceb22-128">Use the **-setDB** option to set the required SQL Server and SSO database names.</span></span>  
  
 <span data-ttu-id="ceb22-129">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="ceb22-129">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="ceb22-130">實作企業單一登入</span><span class="sxs-lookup"><span data-stu-id="ceb22-130">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)