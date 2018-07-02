---
title: 單一登入： 事件 10512 |Microsoft Docs
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
ms.openlocfilehash: 54ba5a340a1a7590dae72016a3e747726ea68125
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980959"
---
# <a name="single-sign-on-event-10512"></a><span data-ttu-id="f327d-102">單一登入： 事件 10512</span><span class="sxs-lookup"><span data-stu-id="f327d-102">Single Sign-On: Event 10512</span></span>
## <a name="details"></a><span data-ttu-id="f327d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f327d-103">Details</span></span>  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  <span data-ttu-id="f327d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f327d-104">Product Name</span></span>   |                 <span data-ttu-id="f327d-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="f327d-105">Enterprise Single Sign-On</span></span>                  |
| <span data-ttu-id="f327d-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="f327d-106">Product Version</span></span> | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    <span data-ttu-id="f327d-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f327d-107">Event ID</span></span>     |                           <span data-ttu-id="f327d-108">10512</span><span class="sxs-lookup"><span data-stu-id="f327d-108">10512</span></span>                            |
|  <span data-ttu-id="f327d-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="f327d-109">Event Source</span></span>   |                           <span data-ttu-id="f327d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f327d-110">ENTSSO</span></span>                           |
|    <span data-ttu-id="f327d-111">元件</span><span class="sxs-lookup"><span data-stu-id="f327d-111">Component</span></span>    |                            <span data-ttu-id="f327d-112">N\A</span><span class="sxs-lookup"><span data-stu-id="f327d-112">N\A</span></span>                             |
|  <span data-ttu-id="f327d-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f327d-113">Symbolic Name</span></span>  |                   <span data-ttu-id="f327d-114">SSO_ERROR_LOADLIBRARY</span><span class="sxs-lookup"><span data-stu-id="f327d-114">SSO_ERROR_LOADLIBRARY</span></span>                    |
|  <span data-ttu-id="f327d-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f327d-115">Message Text</span></span>   |      <span data-ttu-id="f327d-116">無法載入 %1%r</span><span class="sxs-lookup"><span data-stu-id="f327d-116">Failed to load %1%r</span></span><br /><br /> <span data-ttu-id="f327d-117">錯誤碼: %2。</span><span class="sxs-lookup"><span data-stu-id="f327d-117">Error code: %2.</span></span>       |

## <a name="explanation"></a><span data-ttu-id="f327d-118">說明</span><span class="sxs-lookup"><span data-stu-id="f327d-118">Explanation</span></span>  
 <span data-ttu-id="f327d-119">這個錯誤事件表示指定的動態連結程式庫 (DLL) 無法載入至 SSO 伺服器處理程序。</span><span class="sxs-lookup"><span data-stu-id="f327d-119">This Error event indicates that the specified Dynamic Link Library (DLL) could not be loaded into the SSO server process.</span></span> <span data-ttu-id="f327d-120">如果 DLL 遺失在 SSO 安裝目錄中，通常是 C:\Program Files\Common Files\Enterprise Single Sign-on，它可能表示未正確地完成安裝程式或 DLL 已刪除之後的安裝已完成。</span><span class="sxs-lookup"><span data-stu-id="f327d-120">If the DLL is missing in the SSO installation directory, typically C:\Program Files\Common Files\Enterprise Single Sign-On, it may indicate that setup was not completed correctly, or that the DLL was deleted after setup was completed.</span></span> <span data-ttu-id="f327d-121">如果 DLL 存在，則解析 DLL 正確路徑的 SSO 服務可能有問題。</span><span class="sxs-lookup"><span data-stu-id="f327d-121">If the DLL is present, then there could be a problem with the SSO service resolving the correct path to the DLL.</span></span> <span data-ttu-id="f327d-122">此外，DLL 本身可能已損毀。</span><span class="sxs-lookup"><span data-stu-id="f327d-122">Additionally, the DLL itself could be corrupted.</span></span>  

## <a name="user-action"></a><span data-ttu-id="f327d-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f327d-123">User Action</span></span>  
 <span data-ttu-id="f327d-124">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="f327d-124">To resolve this error, do one or more of the following:</span></span>  

- <span data-ttu-id="f327d-125">如果懷疑有更多設定失敗，可能需要解除安裝然後重新安裝產品。</span><span class="sxs-lookup"><span data-stu-id="f327d-125">If a wider failure of setup is suspected it may be necessary to uninstall and reinstall the product.</span></span>  

- <span data-ttu-id="f327d-126">如果單一 DLL 遺失或損毀，則會嘗試取代它，然後重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="f327d-126">If the single DLL is missing or corrupted, attempt to replace it and then restart the service.</span></span>  

  <span data-ttu-id="f327d-127">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="f327d-127">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="f327d-128">實作企業單一登入</span><span class="sxs-lookup"><span data-stu-id="f327d-128">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)
