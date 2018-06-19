---
title: 單一登入： 事件 10745 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed630e40-d876-4e90-937e-4d2d54fe9f1a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fe734562b9d8b3564a08f3f5196d53996bf40ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270822"
---
# <a name="single-sign-on-event-10745"></a><span data-ttu-id="2068a-102">單一登入： 事件 10745</span><span class="sxs-lookup"><span data-stu-id="2068a-102">Single Sign-On: Event 10745</span></span>
## <a name="details"></a><span data-ttu-id="2068a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2068a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2068a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2068a-104">Product Name</span></span>|<span data-ttu-id="2068a-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="2068a-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="2068a-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="2068a-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="2068a-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2068a-107">Event ID</span></span>|<span data-ttu-id="2068a-108">10745</span><span class="sxs-lookup"><span data-stu-id="2068a-108">10745</span></span>|  
|<span data-ttu-id="2068a-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="2068a-109">Event Source</span></span>|<span data-ttu-id="2068a-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="2068a-110">ENTSSO</span></span>|  
|<span data-ttu-id="2068a-111">元件</span><span class="sxs-lookup"><span data-stu-id="2068a-111">Component</span></span>|<span data-ttu-id="2068a-112">N\A</span><span class="sxs-lookup"><span data-stu-id="2068a-112">N\A</span></span>|  
|<span data-ttu-id="2068a-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2068a-113">Symbolic Name</span></span>|<span data-ttu-id="2068a-114">SSO_ERROR_ADAPTER_OFFLINE</span><span class="sxs-lookup"><span data-stu-id="2068a-114">SSO_ERROR_ADAPTER_OFFLINE</span></span>|  
|<span data-ttu-id="2068a-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2068a-115">Message Text</span></span>|<span data-ttu-id="2068a-116">配接器已 offline.%r</span><span class="sxs-lookup"><span data-stu-id="2068a-116">The adapter is offline.%r</span></span><br /><br /> <span data-ttu-id="2068a-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="2068a-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="2068a-118">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="2068a-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="2068a-119">錯誤訊息: %3 %r</span><span class="sxs-lookup"><span data-stu-id="2068a-119">Error Message: %3%r</span></span><br /><br /> <span data-ttu-id="2068a-120">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="2068a-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2068a-121">說明</span><span class="sxs-lookup"><span data-stu-id="2068a-121">Explanation</span></span>  
 <span data-ttu-id="2068a-122">這個錯誤事件表示指定的配接器已離線。</span><span class="sxs-lookup"><span data-stu-id="2068a-122">This Error event indicates that the specified adapter is offline.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2068a-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2068a-123">User Action</span></span>  
 <span data-ttu-id="2068a-124">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="2068a-124">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="2068a-125">請檢查系統和應用程式事件日誌中的相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="2068a-125">Check the system and application event logs for associated errors.</span></span>  
  
-   <span data-ttu-id="2068a-126">請檢查有錯誤的外部介面卡。</span><span class="sxs-lookup"><span data-stu-id="2068a-126">Check the external adapter for errors.</span></span>  
  
 <span data-ttu-id="2068a-127">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="2068a-127">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="2068a-128">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="2068a-128">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)