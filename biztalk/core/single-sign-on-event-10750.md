---
title: 單一登入： 事件 10750 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a0fdaf2-d429-40b9-adc3-eb134687fb1a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b32b8c29159edc0cf6fa7281b5a717af509e3a63
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276326"
---
# <a name="single-sign-on-event-10750"></a><span data-ttu-id="c1a90-102">單一登入： 事件 10750</span><span class="sxs-lookup"><span data-stu-id="c1a90-102">Single Sign-On: Event 10750</span></span>
## <a name="details"></a><span data-ttu-id="c1a90-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c1a90-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c1a90-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c1a90-104">Product Name</span></span>|<span data-ttu-id="c1a90-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="c1a90-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c1a90-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="c1a90-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c1a90-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c1a90-107">Event ID</span></span>|<span data-ttu-id="c1a90-108">10750</span><span class="sxs-lookup"><span data-stu-id="c1a90-108">10750</span></span>|  
|<span data-ttu-id="c1a90-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="c1a90-109">Event Source</span></span>|<span data-ttu-id="c1a90-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c1a90-110">ENTSSO</span></span>|  
|<span data-ttu-id="c1a90-111">元件</span><span class="sxs-lookup"><span data-stu-id="c1a90-111">Component</span></span>|<span data-ttu-id="c1a90-112">N\A</span><span class="sxs-lookup"><span data-stu-id="c1a90-112">N\A</span></span>|  
|<span data-ttu-id="c1a90-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c1a90-113">Symbolic Name</span></span>|<span data-ttu-id="c1a90-114">SSO_ERROR_PS_WRONG_USER_NAME_TYPE</span><span class="sxs-lookup"><span data-stu-id="c1a90-114">SSO_ERROR_PS_WRONG_USER_NAME_TYPE</span></span>|  
|<span data-ttu-id="c1a90-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c1a90-115">Message Text</span></span>|<span data-ttu-id="c1a90-116">PasswordChangeNotify： 不正確的使用者名稱類型。</span><span class="sxs-lookup"><span data-stu-id="c1a90-116">PasswordChangeNotify: Incorrect User Name Type.</span></span> <span data-ttu-id="c1a90-117">接受的值只有 USER_NAME_TYPE_NT4。</span><span class="sxs-lookup"><span data-stu-id="c1a90-117">The only accepted value is USER_NAME_TYPE_NT4.</span></span><br /><br /> <span data-ttu-id="c1a90-118">設定目標 Active Directory.%r 中，不正確</span><span class="sxs-lookup"><span data-stu-id="c1a90-118">The target is incorrectly configured in Active Directory.%r</span></span><br /><br /> <span data-ttu-id="c1a90-119">使用者名稱類型: %1 %r</span><span class="sxs-lookup"><span data-stu-id="c1a90-119">User Name Type: %1%r</span></span><br /><br /> <span data-ttu-id="c1a90-120">用戶端使用者: %2 %r</span><span class="sxs-lookup"><span data-stu-id="c1a90-120">Client User: %2%r</span></span><br /><br /> <span data-ttu-id="c1a90-121">錯誤碼： %3</span><span class="sxs-lookup"><span data-stu-id="c1a90-121">Error Code: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c1a90-122">說明</span><span class="sxs-lookup"><span data-stu-id="c1a90-122">Explanation</span></span>  
 <span data-ttu-id="c1a90-123">這個錯誤事件表示密碼同步接收密碼變更從密碼變更通知服務 (PCNS)，但密碼變更是格式錯誤。</span><span class="sxs-lookup"><span data-stu-id="c1a90-123">This Error event indicates that Password Sync received a password change from the Password Change Notification Service (PCNS), but the password change was in the wrong format.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c1a90-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c1a90-124">User Action</span></span>  
 <span data-ttu-id="c1a90-125">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c1a90-125">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="c1a90-126">請檢查 PCNS 組態。</span><span class="sxs-lookup"><span data-stu-id="c1a90-126">Check the PCNS configuration.</span></span> <span data-ttu-id="c1a90-127">PCNS 可以只在網域控制站上執行。</span><span class="sxs-lookup"><span data-stu-id="c1a90-127">PCNS can run only on a domain controller.</span></span>  
  
-   <span data-ttu-id="c1a90-128">設定 Active Directory 中的使用者名稱類型 USER_NAME_TYPE_NT4。</span><span class="sxs-lookup"><span data-stu-id="c1a90-128">Configure User Name Type to USER_NAME_TYPE_NT4 in Active Directory.</span></span>  
  
 <span data-ttu-id="c1a90-129">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="c1a90-129">For more information, see the following resources:</span></span>  
  
-   <span data-ttu-id="c1a90-130">請參閱 Active Directory 文件，如需有關如何指定使用者名稱類型資訊。</span><span class="sxs-lookup"><span data-stu-id="c1a90-130">Refer to Active Directory documentation for information on how to specify User Name Type.</span></span>  
  
-   [<span data-ttu-id="c1a90-131">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="c1a90-131">Password Synchronization</span></span>](../core/password-synchronization2.md)