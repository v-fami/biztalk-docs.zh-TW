---
title: 單一登入： 事件 10503 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 04292ae8-8daf-4f5a-837e-fe5dfcd02b10
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 53c02388304fa9fab0b518517ba51b2db94412f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271110"
---
# <a name="single-sign-on-event-10503"></a><span data-ttu-id="6e181-102">單一登入： 事件 10503</span><span class="sxs-lookup"><span data-stu-id="6e181-102">Single Sign-On: Event 10503</span></span>
## <a name="details"></a><span data-ttu-id="6e181-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6e181-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e181-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6e181-104">Product Name</span></span>|<span data-ttu-id="6e181-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="6e181-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="6e181-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="6e181-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="6e181-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6e181-107">Event ID</span></span>|<span data-ttu-id="6e181-108">10503</span><span class="sxs-lookup"><span data-stu-id="6e181-108">10503</span></span>|  
|<span data-ttu-id="6e181-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="6e181-109">Event Source</span></span>|<span data-ttu-id="6e181-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="6e181-110">ENTSSO</span></span>|  
|<span data-ttu-id="6e181-111">元件</span><span class="sxs-lookup"><span data-stu-id="6e181-111">Component</span></span>|<span data-ttu-id="6e181-112">N\A</span><span class="sxs-lookup"><span data-stu-id="6e181-112">N\A</span></span>|  
|<span data-ttu-id="6e181-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6e181-113">Symbolic Name</span></span>|<span data-ttu-id="6e181-114">SSO_ERROR_SERVICE_START_FAILED</span><span class="sxs-lookup"><span data-stu-id="6e181-114">SSO_ERROR_SERVICE_START_FAILED</span></span>|  
|<span data-ttu-id="6e181-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6e181-115">Message Text</span></span>|<span data-ttu-id="6e181-116">SSO 服務無法啟動。%r</span><span class="sxs-lookup"><span data-stu-id="6e181-116">The SSO service failed to start.%r</span></span><br /><br /> <span data-ttu-id="6e181-117">錯誤碼： %1</span><span class="sxs-lookup"><span data-stu-id="6e181-117">Error Code: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6e181-118">說明</span><span class="sxs-lookup"><span data-stu-id="6e181-118">Explanation</span></span>  
 <span data-ttu-id="6e181-119">此錯誤事件表示 ENTSSO 服務因為例外狀況所以無法啟動。</span><span class="sxs-lookup"><span data-stu-id="6e181-119">This Error event indicates that the ENTSSO Service could not start due to an exception.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6e181-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6e181-120">User Action</span></span>  
 <span data-ttu-id="6e181-121">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="6e181-121">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="6e181-122">請檢查 ENTSSO 或其他服務的相關錯誤的應用程式和系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="6e181-122">Check both the Application and System event logs for related errors from ENTSSO or other services.</span></span>  
  
 <span data-ttu-id="6e181-123">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="6e181-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="6e181-124">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="6e181-124">Using SSO</span></span>](../core/using-sso.md)