---
title: 單一登入： 事件 10669 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e88a583d-7385-42dd-841e-aa2d2215dd69
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 334180225d47cb9a86577cab75490ea0b6f2225a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271622"
---
# <a name="single-sign-on-event-10669"></a><span data-ttu-id="018d8-102">單一登入： 事件 10669</span><span class="sxs-lookup"><span data-stu-id="018d8-102">Single Sign-On: Event 10669</span></span>
## <a name="details"></a><span data-ttu-id="018d8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="018d8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="018d8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="018d8-104">Product Name</span></span>|<span data-ttu-id="018d8-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="018d8-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="018d8-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="018d8-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="018d8-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="018d8-107">Event ID</span></span>|<span data-ttu-id="018d8-108">10669</span><span class="sxs-lookup"><span data-stu-id="018d8-108">10669</span></span>|  
|<span data-ttu-id="018d8-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="018d8-109">Event Source</span></span>|<span data-ttu-id="018d8-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="018d8-110">ENTSSO</span></span>|  
|<span data-ttu-id="018d8-111">元件</span><span class="sxs-lookup"><span data-stu-id="018d8-111">Component</span></span>|<span data-ttu-id="018d8-112">N\A</span><span class="sxs-lookup"><span data-stu-id="018d8-112">N\A</span></span>|  
|<span data-ttu-id="018d8-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="018d8-113">Symbolic Name</span></span>|<span data-ttu-id="018d8-114">SSO_WARN_CHANGE_WINDOWS_PASSWORD_FAILED</span><span class="sxs-lookup"><span data-stu-id="018d8-114">SSO_WARN_CHANGE_WINDOWS_PASSWORD_FAILED</span></span>|  
|<span data-ttu-id="018d8-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="018d8-115">Message Text</span></span>|<span data-ttu-id="018d8-116">無法變更 Windows password.%r</span><span class="sxs-lookup"><span data-stu-id="018d8-116">Failed to change the Windows password.%r</span></span><br /><br /> <span data-ttu-id="018d8-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="018d8-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="018d8-118">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="018d8-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="018d8-119">Windows 帳戶: %3 %r</span><span class="sxs-lookup"><span data-stu-id="018d8-119">Windows Account: %3%r</span></span><br /><br /> <span data-ttu-id="018d8-120">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="018d8-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="018d8-121">說明</span><span class="sxs-lookup"><span data-stu-id="018d8-121">Explanation</span></span>  
 <span data-ttu-id="018d8-122">這個警告事件表示 SSO 無法變更 Windows 密碼。</span><span class="sxs-lookup"><span data-stu-id="018d8-122">This Warning event indicates that SSO failed to change a Windows password.</span></span> <span data-ttu-id="018d8-123">SSO 會呼叫 Win32 函式 NetUserChangePassword 函式變更對應相關聯的 Windows 密碼。</span><span class="sxs-lookup"><span data-stu-id="018d8-123">SSO calls the Win32 function NetUserChangePassword function to change the Windows password associated with the mapping.</span></span> <span data-ttu-id="018d8-124">如果此函式會失敗這則錯誤訊息就會發出。</span><span class="sxs-lookup"><span data-stu-id="018d8-124">If this function fails this error message is issued.</span></span> <span data-ttu-id="018d8-125">錯誤的程式碼會傳回從 NetUserChangePassword。</span><span class="sxs-lookup"><span data-stu-id="018d8-125">The error code will be the one returned from NetUserChangePassword.</span></span> <span data-ttu-id="018d8-126">請參閱 MSDN 中這個函式，如需詳細資訊的文件。</span><span class="sxs-lookup"><span data-stu-id="018d8-126">See the documentation for this function in MSDN for details.</span></span> <span data-ttu-id="018d8-127">最有可能失敗的原因是舊的密碼不正確，或將新的密碼不符合必要的 Windows 密碼原則。</span><span class="sxs-lookup"><span data-stu-id="018d8-127">Most likely causes of failure are that the old password was incorrect, or that the new password does not meet the required Windows password policy.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="018d8-128">使用者動作</span><span class="sxs-lookup"><span data-stu-id="018d8-128">User Action</span></span>  
 <span data-ttu-id="018d8-129">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="018d8-129">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="018d8-130">驗證舊密碼。</span><span class="sxs-lookup"><span data-stu-id="018d8-130">Verify the old password.</span></span> <span data-ttu-id="018d8-131">如果舊的密碼不正確，則可以設定以手動方式在 SSO 資料庫中使用的命令列工具或管理 MMC。</span><span class="sxs-lookup"><span data-stu-id="018d8-131">If the old password is incorrect then it can be set manually in the SSO database using the command line tools or Admin MMC.</span></span>  
  
-   <span data-ttu-id="018d8-132">確認新密碼符合必要的 Windows 密碼原則。</span><span class="sxs-lookup"><span data-stu-id="018d8-132">Verify the new password meets the required Windows password policy.</span></span> <span data-ttu-id="018d8-133">如果密碼不符合 Windows 密碼原則會再考慮使用密碼篩選器。</span><span class="sxs-lookup"><span data-stu-id="018d8-133">If the password does not meet the Windows password policy then consider using password filters.</span></span>  
  
 <span data-ttu-id="018d8-134">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="018d8-134">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="018d8-135">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="018d8-135">Password Synchronization</span></span>](../core/password-synchronization2.md)