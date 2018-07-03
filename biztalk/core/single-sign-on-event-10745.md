---
title: 單一登入： 事件 10745 |Microsoft Docs
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
ms.openlocfilehash: 4bb3afa69e4a959b189347ac20b71acfc58208f4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984751"
---
# <a name="single-sign-on-event-10745"></a><span data-ttu-id="ed907-102">單一登入： 事件 10745</span><span class="sxs-lookup"><span data-stu-id="ed907-102">Single Sign-On: Event 10745</span></span>
## <a name="details"></a><span data-ttu-id="ed907-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ed907-103">Details</span></span>  

|                 |                                                                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="ed907-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ed907-104">Product Name</span></span>   |                                                          <span data-ttu-id="ed907-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="ed907-105">Enterprise Single Sign-On</span></span>                                                           |
| <span data-ttu-id="ed907-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="ed907-106">Product Version</span></span> |                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                          |
|    <span data-ttu-id="ed907-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ed907-107">Event ID</span></span>     |                                                                    <span data-ttu-id="ed907-108">10745</span><span class="sxs-lookup"><span data-stu-id="ed907-108">10745</span></span>                                                                     |
|  <span data-ttu-id="ed907-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="ed907-109">Event Source</span></span>   |                                                                    <span data-ttu-id="ed907-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ed907-110">ENTSSO</span></span>                                                                    |
|    <span data-ttu-id="ed907-111">元件</span><span class="sxs-lookup"><span data-stu-id="ed907-111">Component</span></span>    |                                                                     <span data-ttu-id="ed907-112">N\A</span><span class="sxs-lookup"><span data-stu-id="ed907-112">N\A</span></span>                                                                      |
|  <span data-ttu-id="ed907-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ed907-113">Symbolic Name</span></span>  |                                                          <span data-ttu-id="ed907-114">SSO_ERROR_ADAPTER_OFFLINE</span><span class="sxs-lookup"><span data-stu-id="ed907-114">SSO_ERROR_ADAPTER_OFFLINE</span></span>                                                           |
|  <span data-ttu-id="ed907-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ed907-115">Message Text</span></span>   | <span data-ttu-id="ed907-116">配接器已 offline.%r</span><span class="sxs-lookup"><span data-stu-id="ed907-116">The adapter is offline.%r</span></span><br /><br /> <span data-ttu-id="ed907-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="ed907-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="ed907-118">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="ed907-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="ed907-119">錯誤訊息: %3 %r</span><span class="sxs-lookup"><span data-stu-id="ed907-119">Error Message: %3%r</span></span><br /><br /> <span data-ttu-id="ed907-120">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="ed907-120">Error Code: %4</span></span> |

## <a name="explanation"></a><span data-ttu-id="ed907-121">說明</span><span class="sxs-lookup"><span data-stu-id="ed907-121">Explanation</span></span>  
 <span data-ttu-id="ed907-122">這個錯誤事件表示指定的配接器已離線。</span><span class="sxs-lookup"><span data-stu-id="ed907-122">This Error event indicates that the specified adapter is offline.</span></span>  

## <a name="user-action"></a><span data-ttu-id="ed907-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ed907-123">User Action</span></span>  
 <span data-ttu-id="ed907-124">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="ed907-124">To resolve this error, do one or more of the following:</span></span>  

- <span data-ttu-id="ed907-125">請檢查系統和應用程式事件日誌中的相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="ed907-125">Check the system and application event logs for associated errors.</span></span>  

- <span data-ttu-id="ed907-126">請檢查有錯誤的外部介面卡。</span><span class="sxs-lookup"><span data-stu-id="ed907-126">Check the external adapter for errors.</span></span>  

  <span data-ttu-id="ed907-127">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="ed907-127">For more information, see the following resources:</span></span>  

- [<span data-ttu-id="ed907-128">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="ed907-128">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)
