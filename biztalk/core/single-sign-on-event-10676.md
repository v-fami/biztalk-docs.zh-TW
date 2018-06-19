---
title: 單一登入： 事件 10676 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec0e86fb-921d-4505-b458-51b565123ea7
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3805e59e5e8984652ec40af9f93db793d5d3b5fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271654"
---
# <a name="single-sign-on-event-10676"></a><span data-ttu-id="a5432-102">單一登入： 事件 10676</span><span class="sxs-lookup"><span data-stu-id="a5432-102">Single Sign-On: Event 10676</span></span>
## <a name="details"></a><span data-ttu-id="a5432-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a5432-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5432-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a5432-104">Product Name</span></span>|<span data-ttu-id="a5432-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a5432-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a5432-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="a5432-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a5432-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a5432-107">Event ID</span></span>|<span data-ttu-id="a5432-108">10676</span><span class="sxs-lookup"><span data-stu-id="a5432-108">10676</span></span>|  
|<span data-ttu-id="a5432-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="a5432-109">Event Source</span></span>|<span data-ttu-id="a5432-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a5432-110">ENTSSO</span></span>|  
|<span data-ttu-id="a5432-111">元件</span><span class="sxs-lookup"><span data-stu-id="a5432-111">Component</span></span>|<span data-ttu-id="a5432-112">N\A</span><span class="sxs-lookup"><span data-stu-id="a5432-112">N\A</span></span>|  
|<span data-ttu-id="a5432-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a5432-113">Symbolic Name</span></span>|<span data-ttu-id="a5432-114">SSO_ERROR_REQUIRE_OLD_PASSWORD</span><span class="sxs-lookup"><span data-stu-id="a5432-114">SSO_ERROR_REQUIRE_OLD_PASSWORD</span></span>|  
|<span data-ttu-id="a5432-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a5432-115">Message Text</span></span>|<span data-ttu-id="a5432-116">外部密碼變更。</span><span class="sxs-lookup"><span data-stu-id="a5432-116">External password change.</span></span> <span data-ttu-id="a5432-117">變更外部帳戶的密碼時，配接器必須提供舊 password.%r</span><span class="sxs-lookup"><span data-stu-id="a5432-117">When changing the password for an external account the adapter must supply the old password.%r</span></span><br /><br /> <span data-ttu-id="a5432-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="a5432-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="a5432-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="a5432-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="a5432-120">外部帳戶： %3</span><span class="sxs-lookup"><span data-stu-id="a5432-120">External Account: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a5432-121">說明</span><span class="sxs-lookup"><span data-stu-id="a5432-121">Explanation</span></span>  
 <span data-ttu-id="a5432-122">這個錯誤事件表示密碼同步配接器已設定為預期來自外部系統中，舊密碼，但未提供舊密碼。</span><span class="sxs-lookup"><span data-stu-id="a5432-122">This Error event indicates that the password sync adapter was configured to expect an old password from the external system, but an old password was not provided.</span></span> <span data-ttu-id="a5432-123">未設定外部系統 （外部密碼同步配接器） 或是如預期般的工作或 「 密碼同步配接器設定不正確。</span><span class="sxs-lookup"><span data-stu-id="a5432-123">Either the external system (the external password sync adapter) is not configured or working as expected or the password sync adapter is incorrectly configured.</span></span> <span data-ttu-id="a5432-124">這項錯誤也可能會傳回錯誤的程式碼的符號名稱 ENTSSO_E_REQUIRE_OLD_PASSWORD。</span><span class="sxs-lookup"><span data-stu-id="a5432-124">This error may also return error code symbolic name ENTSSO_E_REQUIRE_OLD_PASSWORD.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a5432-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a5432-125">User Action</span></span>  
 <span data-ttu-id="a5432-126">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="a5432-126">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="a5432-127">使用者可設定屬性設為使用 SSO 管理工具**驗證舊密碼**密碼同步配接器選項內容 索引標籤上。這個屬性也可以設定時建立配接器透過命令列工具，旗標名稱 (ssops.exe)`verifyOldPassword`和也時建立新的密碼同步配接器使用 「 密碼同步配接器精靈 」。</span><span class="sxs-lookup"><span data-stu-id="a5432-127">Use the SSO administration tools to set the user configurable property **Verify Old Password** on the Password Sync Adapter Options properties tab. This property can also be set when creating adapters via the command line tools (ssops.exe) with the flag name `verifyOldPassword` and also when creating a new password sync adapter using the Password Sync Adapter wizard.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="a5432-128">其他資訊</span><span class="sxs-lookup"><span data-stu-id="a5432-128">More info</span></span>
  
-   [<span data-ttu-id="a5432-129">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="a5432-129">Password Synchronization</span></span>](../core/password-synchronization2.md)  
  
-   <span data-ttu-id="a5432-130">**密碼同步配接器屬性： 選項**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="a5432-130">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>