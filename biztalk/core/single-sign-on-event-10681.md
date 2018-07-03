---
title: 單一登入： 事件 10681 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87ce2e50-cf54-4b23-b247-f137ce64ba1d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d2b400db062dc76b32d071032ee75c55ef48046
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011663"
---
# <a name="single-sign-on-event-10681"></a><span data-ttu-id="8bf76-102">單一登入： 事件 10681</span><span class="sxs-lookup"><span data-stu-id="8bf76-102">Single Sign-On: Event 10681</span></span>
## <a name="details"></a><span data-ttu-id="8bf76-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8bf76-103">Details</span></span>  

|                 |                                                                                                                                                                                                                      |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="8bf76-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8bf76-104">Product Name</span></span>   |                                                                                              <span data-ttu-id="8bf76-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="8bf76-105">Enterprise Single Sign-On</span></span>                                                                                               |
| <span data-ttu-id="8bf76-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="8bf76-106">Product Version</span></span> |                                                                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                              |
|    <span data-ttu-id="8bf76-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8bf76-107">Event ID</span></span>     |                                                                                                        <span data-ttu-id="8bf76-108">10681</span><span class="sxs-lookup"><span data-stu-id="8bf76-108">10681</span></span>                                                                                                         |
|  <span data-ttu-id="8bf76-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="8bf76-109">Event Source</span></span>   |                                                                                                        <span data-ttu-id="8bf76-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="8bf76-110">ENTSSO</span></span>                                                                                                        |
|    <span data-ttu-id="8bf76-111">元件</span><span class="sxs-lookup"><span data-stu-id="8bf76-111">Component</span></span>    |                                                                                                         <span data-ttu-id="8bf76-112">N\A</span><span class="sxs-lookup"><span data-stu-id="8bf76-112">N\A</span></span>                                                                                                          |
|  <span data-ttu-id="8bf76-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8bf76-113">Symbolic Name</span></span>  |                                                                                         <span data-ttu-id="8bf76-114">SSO_WARN_NO_WINDOWS_PASSWORD_CHANGE</span><span class="sxs-lookup"><span data-stu-id="8bf76-114">SSO_WARN_NO_WINDOWS_PASSWORD_CHANGE</span></span>                                                                                          |
|  <span data-ttu-id="8bf76-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8bf76-115">Message Text</span></span>   | <span data-ttu-id="8bf76-116">外部密碼變更。</span><span class="sxs-lookup"><span data-stu-id="8bf76-116">External password change.</span></span> <span data-ttu-id="8bf76-117">無法變更 Windows 密碼，因為一個或多個外部帳戶變更 failed.%r</span><span class="sxs-lookup"><span data-stu-id="8bf76-117">The Windows password was not changed because one or more of the external account changes failed.%r</span></span><br /><br /> <span data-ttu-id="8bf76-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="8bf76-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="8bf76-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="8bf76-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="8bf76-120">Windows 帳戶： %3</span><span class="sxs-lookup"><span data-stu-id="8bf76-120">Windows Account: %3</span></span> |

## <a name="explanation"></a><span data-ttu-id="8bf76-121">說明</span><span class="sxs-lookup"><span data-stu-id="8bf76-121">Explanation</span></span>  
 <span data-ttu-id="8bf76-122">這個警告事件表示因為一個或多個外部帳戶變更失敗，已不會變更 Windows 密碼。</span><span class="sxs-lookup"><span data-stu-id="8bf76-122">This Warning event indicates that the Windows password was not changed because one or more of the external account changes failed.</span></span>  

## <a name="user-action"></a><span data-ttu-id="8bf76-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8bf76-123">User Action</span></span>  
 <span data-ttu-id="8bf76-124">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="8bf76-124">To resolve this warning, do one or more of the following:</span></span>  

-   <span data-ttu-id="8bf76-125">請檢查關聯事件的系統和應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="8bf76-125">Check the System and Application Event logs for associated events.</span></span>  

-   <span data-ttu-id="8bf76-126">確認配接器使用 SSO 管理工具的組態。</span><span class="sxs-lookup"><span data-stu-id="8bf76-126">Verify adapter configuration using the SSO administration tools.</span></span>  

-   <span data-ttu-id="8bf76-127">確認外部系統。</span><span class="sxs-lookup"><span data-stu-id="8bf76-127">Verify external systems.</span></span>  

## <a name="more-info"></a><span data-ttu-id="8bf76-128">其他資訊</span><span class="sxs-lookup"><span data-stu-id="8bf76-128">More info</span></span>

- [<span data-ttu-id="8bf76-129">密碼同步</span><span class="sxs-lookup"><span data-stu-id="8bf76-129">Password Synchronization</span></span>](../core/password-synchronization2.md)  

- <span data-ttu-id="8bf76-130">**密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="8bf76-130">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
