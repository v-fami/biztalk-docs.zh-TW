---
title: 單一登入： 事件 10668 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0eb3dd4d-04b5-4713-93c1-76af012d6920
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 006855842ea2d789290200d5c5a9692b6e046e8a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271438"
---
# <a name="single-sign-on-event-10668"></a><span data-ttu-id="63eaa-102">單一登入： 事件 10668</span><span class="sxs-lookup"><span data-stu-id="63eaa-102">Single Sign-On: Event 10668</span></span>
## <a name="details"></a><span data-ttu-id="63eaa-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="63eaa-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="63eaa-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="63eaa-104">Product Name</span></span>|<span data-ttu-id="63eaa-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="63eaa-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="63eaa-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="63eaa-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="63eaa-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="63eaa-107">Event ID</span></span>|<span data-ttu-id="63eaa-108">10668</span><span class="sxs-lookup"><span data-stu-id="63eaa-108">10668</span></span>|  
|<span data-ttu-id="63eaa-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="63eaa-109">Event Source</span></span>|<span data-ttu-id="63eaa-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="63eaa-110">ENTSSO</span></span>|  
|<span data-ttu-id="63eaa-111">元件</span><span class="sxs-lookup"><span data-stu-id="63eaa-111">Component</span></span>|<span data-ttu-id="63eaa-112">N\A</span><span class="sxs-lookup"><span data-stu-id="63eaa-112">N\A</span></span>|  
|<span data-ttu-id="63eaa-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="63eaa-113">Symbolic Name</span></span>|<span data-ttu-id="63eaa-114">SSO_WARN_NO_OLD_WINDOWS_PASSWORD</span><span class="sxs-lookup"><span data-stu-id="63eaa-114">SSO_WARN_NO_OLD_WINDOWS_PASSWORD</span></span>|  
|<span data-ttu-id="63eaa-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="63eaa-115">Message Text</span></span>|<span data-ttu-id="63eaa-116">無法變更 Windows 密碼，因為此帳戶的舊 Windows 密碼無法使用 SSO database.%r 中</span><span class="sxs-lookup"><span data-stu-id="63eaa-116">Cannot change the Windows password because the old Windows password for this account is not available in the SSO database.%r</span></span><br /><br /> <span data-ttu-id="63eaa-117">若要設定此 Windows account.%r 的外部認證使用 SSO 管理工具</span><span class="sxs-lookup"><span data-stu-id="63eaa-117">Use the SSO administration tools to set the external credentials for this Windows account.%r</span></span><br /><br /> <span data-ttu-id="63eaa-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="63eaa-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="63eaa-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="63eaa-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="63eaa-120">Windows 帳戶： %3</span><span class="sxs-lookup"><span data-stu-id="63eaa-120">Windows Account: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="63eaa-121">說明</span><span class="sxs-lookup"><span data-stu-id="63eaa-121">Explanation</span></span>  
 <span data-ttu-id="63eaa-122">這個警告事件表示密碼同步無法變更 Windows 密碼，因為在 SSO 資料庫中沒有此帳戶的舊 Windows 密碼。</span><span class="sxs-lookup"><span data-stu-id="63eaa-122">This Warning event indicates that Password Sync cannot change the Windows password because the old Windows password for this account is not available in the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="63eaa-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="63eaa-123">User Action</span></span>  
 <span data-ttu-id="63eaa-124">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="63eaa-124">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="63eaa-125">判斷哪些應用程式已指派給此配接器 （在事件記錄檔訊息中的名稱），然後使用 SSO 管理工具來設定此 Windows 帳戶的外部認證。</span><span class="sxs-lookup"><span data-stu-id="63eaa-125">Determine which Applications were assigned to this Adapter (name in event log message) and then use the SSO administration tools to set the external credentials for this Windows account.</span></span> <span data-ttu-id="63eaa-126">您必須在所有這些應用程式設定 （適用於指定的 Windows 帳戶） 的外部密碼。</span><span class="sxs-lookup"><span data-stu-id="63eaa-126">You must set the external password (for the given Windows Account) in all of those Applications.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="63eaa-127">其他資訊</span><span class="sxs-lookup"><span data-stu-id="63eaa-127">More info</span></span>
  
-   [<span data-ttu-id="63eaa-128">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="63eaa-128">Password Synchronization</span></span>](../core/password-synchronization2.md)  
  
-   <span data-ttu-id="63eaa-129">**密碼同步配接器屬性： 選項**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="63eaa-129">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>