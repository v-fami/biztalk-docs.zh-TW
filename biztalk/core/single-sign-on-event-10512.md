---
title: 單一登入： 事件 10512 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4edf0512-112d-40b8-9e29-7dd67f999b6d
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a586af2b280e9d968b87a7cb3e7680a17457ca0a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270774"
---
# <a name="single-sign-on-event-10512"></a><span data-ttu-id="c6351-102">單一登入： 事件 10512</span><span class="sxs-lookup"><span data-stu-id="c6351-102">Single Sign-On: Event 10512</span></span>
## <a name="details"></a><span data-ttu-id="c6351-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c6351-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6351-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c6351-104">Product Name</span></span>|<span data-ttu-id="c6351-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="c6351-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c6351-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="c6351-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c6351-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c6351-107">Event ID</span></span>|<span data-ttu-id="c6351-108">10512</span><span class="sxs-lookup"><span data-stu-id="c6351-108">10512</span></span>|  
|<span data-ttu-id="c6351-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="c6351-109">Event Source</span></span>|<span data-ttu-id="c6351-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c6351-110">ENTSSO</span></span>|  
|<span data-ttu-id="c6351-111">元件</span><span class="sxs-lookup"><span data-stu-id="c6351-111">Component</span></span>|<span data-ttu-id="c6351-112">N\A</span><span class="sxs-lookup"><span data-stu-id="c6351-112">N\A</span></span>|  
|<span data-ttu-id="c6351-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c6351-113">Symbolic Name</span></span>|<span data-ttu-id="c6351-114">SSO_ERROR_LOADLIBRARY</span><span class="sxs-lookup"><span data-stu-id="c6351-114">SSO_ERROR_LOADLIBRARY</span></span>|  
|<span data-ttu-id="c6351-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c6351-115">Message Text</span></span>|<span data-ttu-id="c6351-116">無法載入 %1%r</span><span class="sxs-lookup"><span data-stu-id="c6351-116">Failed to load %1%r</span></span><br /><br /> <span data-ttu-id="c6351-117">錯誤碼: %2。</span><span class="sxs-lookup"><span data-stu-id="c6351-117">Error code: %2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c6351-118">說明</span><span class="sxs-lookup"><span data-stu-id="c6351-118">Explanation</span></span>  
 <span data-ttu-id="c6351-119">這個錯誤事件表示指定的動態連結程式庫 (DLL) 無法載入至 SSO 伺服器處理程序。</span><span class="sxs-lookup"><span data-stu-id="c6351-119">This Error event indicates that the specified Dynamic Link Library (DLL) could not be loaded into the SSO server process.</span></span> <span data-ttu-id="c6351-120">如果 DLL 遺失在 SSO 安裝目錄中，通常是 C:\Program Files\Common Files\Enterprise Single Sign-on，它可能未正確地完成安裝程式，或安裝後已刪除的 DLL 完成。</span><span class="sxs-lookup"><span data-stu-id="c6351-120">If the DLL is missing in the SSO installation directory, typically C:\Program Files\Common Files\Enterprise Single Sign-On, it may indicate that setup was not completed correctly, or that the DLL was deleted after setup was completed.</span></span> <span data-ttu-id="c6351-121">如果 DLL 存在，則解析 DLL 正確路徑的 SSO 服務可能有問題。</span><span class="sxs-lookup"><span data-stu-id="c6351-121">If the DLL is present, then there could be a problem with the SSO service resolving the correct path to the DLL.</span></span> <span data-ttu-id="c6351-122">此外，DLL 本身可能已損毀。</span><span class="sxs-lookup"><span data-stu-id="c6351-122">Additionally, the DLL itself could be corrupted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c6351-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c6351-123">User Action</span></span>  
 <span data-ttu-id="c6351-124">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="c6351-124">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="c6351-125">如果懷疑有更多設定失敗，可能需要解除安裝然後重新安裝產品。</span><span class="sxs-lookup"><span data-stu-id="c6351-125">If a wider failure of setup is suspected it may be necessary to uninstall and reinstall the product.</span></span>  
  
-   <span data-ttu-id="c6351-126">如果單一 DLL 遺失或損毀，嘗試取代它，然後重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="c6351-126">If the single DLL is missing or corrupted, attempt to replace it and then restart the service.</span></span>  
  
 <span data-ttu-id="c6351-127">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="c6351-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="c6351-128">實作企業單一登入</span><span class="sxs-lookup"><span data-stu-id="c6351-128">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)