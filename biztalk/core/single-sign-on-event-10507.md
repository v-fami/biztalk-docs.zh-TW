---
title: 單一登入： 事件 10507 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b02d8dfa-7655-471e-84af-e58d08c3cefd
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6df0c2d898fd715cbbdebf6fe5d11b780f0fa037
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974831"
---
# <a name="single-sign-on-event-10507"></a><span data-ttu-id="fad94-102">單一登入： 事件 10507</span><span class="sxs-lookup"><span data-stu-id="fad94-102">Single Sign-On: Event 10507</span></span>
## <a name="details"></a><span data-ttu-id="fad94-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fad94-103">Details</span></span>  

|                 |                                                                 |
|-----------------|-----------------------------------------------------------------|
|  <span data-ttu-id="fad94-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fad94-104">Product Name</span></span>   |                    <span data-ttu-id="fad94-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="fad94-105">Enterprise Single Sign-On</span></span>                    |
| <span data-ttu-id="fad94-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="fad94-106">Product Version</span></span> |   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]    |
|    <span data-ttu-id="fad94-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fad94-107">Event ID</span></span>     |                              <span data-ttu-id="fad94-108">10504</span><span class="sxs-lookup"><span data-stu-id="fad94-108">10504</span></span>                              |
|  <span data-ttu-id="fad94-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="fad94-109">Event Source</span></span>   |                             <span data-ttu-id="fad94-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="fad94-110">ENTSSO</span></span>                              |
|    <span data-ttu-id="fad94-111">元件</span><span class="sxs-lookup"><span data-stu-id="fad94-111">Component</span></span>    |                               <span data-ttu-id="fad94-112">N\A</span><span class="sxs-lookup"><span data-stu-id="fad94-112">N\A</span></span>                               |
|  <span data-ttu-id="fad94-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fad94-113">Symbolic Name</span></span>  |                 <span data-ttu-id="fad94-114">SSO_INFO_SERVICE_INSTALL_FAILED</span><span class="sxs-lookup"><span data-stu-id="fad94-114">SSO_INFO_SERVICE_INSTALL_FAILED</span></span>                 |
|  <span data-ttu-id="fad94-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fad94-115">Message Text</span></span>   | <span data-ttu-id="fad94-116">無法安裝 SSO service.%r</span><span class="sxs-lookup"><span data-stu-id="fad94-116">Failed to install the SSO service.%r</span></span><br /><br /> <span data-ttu-id="fad94-117">錯誤碼： %1</span><span class="sxs-lookup"><span data-stu-id="fad94-117">Error Code: %1</span></span> |

## <a name="explanation"></a><span data-ttu-id="fad94-118">說明</span><span class="sxs-lookup"><span data-stu-id="fad94-118">Explanation</span></span>  
 <span data-ttu-id="fad94-119">這個事件表示 ENTSSO 服務無法安裝。</span><span class="sxs-lookup"><span data-stu-id="fad94-119">This event indicates that the ENTSSO Service failed to install.</span></span> <span data-ttu-id="fad94-120">手動安裝的企業單一登入期間，只可以發生此事件。</span><span class="sxs-lookup"><span data-stu-id="fad94-120">This event can only occur during a manual installation of Enterprise Single Sign-On.</span></span>  

## <a name="user-action"></a><span data-ttu-id="fad94-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fad94-121">User Action</span></span>  
 <span data-ttu-id="fad94-122">若要解決此事件，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="fad94-122">To resolve this event, do the following:</span></span>  

- <span data-ttu-id="fad94-123">請檢查 ENTSSO 或其他服務的相關錯誤的應用程式和系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="fad94-123">Check both the Application and System event logs for related errors from ENTSSO or other services.</span></span>  

  <span data-ttu-id="fad94-124">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="fad94-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="fad94-125">安裝 SSO</span><span class="sxs-lookup"><span data-stu-id="fad94-125">Installing SSO</span></span>](../core/installing-sso.md)  

- [<span data-ttu-id="fad94-126">實作企業單一登入</span><span class="sxs-lookup"><span data-stu-id="fad94-126">Implementing Enterprise Single Sign-On</span></span>](../core/implementing-enterprise-single-sign-on.md)
