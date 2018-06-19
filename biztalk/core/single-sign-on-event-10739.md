---
title: 單一登入： 事件 10739 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1039c832-80ff-4cc2-97b4-2671672b6b12
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8a3dc964d830155a63a5ada8817e8b44aaa4c18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271350"
---
# <a name="single-sign-on-event-10739"></a><span data-ttu-id="5b5d5-102">單一登入： 事件 10739</span><span class="sxs-lookup"><span data-stu-id="5b5d5-102">Single Sign-On: Event 10739</span></span>
## <a name="details"></a><span data-ttu-id="5b5d5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5b5d5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5b5d5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5b5d5-104">Product Name</span></span>|<span data-ttu-id="5b5d5-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="5b5d5-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="5b5d5-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="5b5d5-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="5b5d5-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5b5d5-107">Event ID</span></span>|<span data-ttu-id="5b5d5-108">10739</span><span class="sxs-lookup"><span data-stu-id="5b5d5-108">10739</span></span>|  
|<span data-ttu-id="5b5d5-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="5b5d5-109">Event Source</span></span>|<span data-ttu-id="5b5d5-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="5b5d5-110">ENTSSO</span></span>|  
|<span data-ttu-id="5b5d5-111">元件</span><span class="sxs-lookup"><span data-stu-id="5b5d5-111">Component</span></span>|<span data-ttu-id="5b5d5-112">N\A</span><span class="sxs-lookup"><span data-stu-id="5b5d5-112">N\A</span></span>|  
|<span data-ttu-id="5b5d5-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5b5d5-113">Symbolic Name</span></span>|<span data-ttu-id="5b5d5-114">SSO_WARN_PS_SET_WINDOWS_PASSWORD_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="5b5d5-114">SSO_WARN_PS_SET_WINDOWS_PASSWORD_ADAPTER</span></span>|  
|<span data-ttu-id="5b5d5-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5b5d5-115">Message Text</span></span>|<span data-ttu-id="5b5d5-116">無法更新 SSO 資料庫中的 Windows 密碼。%r</span><span class="sxs-lookup"><span data-stu-id="5b5d5-116">Failed to update the Windows password in the SSO database.%r</span></span><br /><br /> <span data-ttu-id="5b5d5-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="5b5d5-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="5b5d5-118">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="5b5d5-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="5b5d5-119">Windows 帳戶： %3\\%4 %r</span><span class="sxs-lookup"><span data-stu-id="5b5d5-119">Windows Account: %3\\%4%r</span></span><br /><br /> <span data-ttu-id="5b5d5-120">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="5b5d5-120">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5b5d5-121">說明</span><span class="sxs-lookup"><span data-stu-id="5b5d5-121">Explanation</span></span>  
 <span data-ttu-id="5b5d5-122">這個警告事件表示 SSO 無法更新 SSO 資料庫中的 Windows 密碼。</span><span class="sxs-lookup"><span data-stu-id="5b5d5-122">This Warning event indicates that SSO failed to update the Windows password in the SSO database.</span></span> <span data-ttu-id="5b5d5-123">在警告訊息，指出失敗的各種可能的原因有很在某些情況下，此警告可能表示有設定問題，或對應可能遭到刪除，處理密碼變更時。</span><span class="sxs-lookup"><span data-stu-id="5b5d5-123">There are various possible causes of failure indicated in the warning message; in some cases, this warning might indicate a configuration problem, or the mapping may have been deleted while the password change was in process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5b5d5-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5b5d5-124">User Action</span></span>  
 <span data-ttu-id="5b5d5-125">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5b5d5-125">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="5b5d5-126">重試密碼變更。</span><span class="sxs-lookup"><span data-stu-id="5b5d5-126">Retry the password change.</span></span>  
  
-   <span data-ttu-id="5b5d5-127">若其他嘗試繼續失敗，變更密碼以手動方式使用 UI 或命令列工具。</span><span class="sxs-lookup"><span data-stu-id="5b5d5-127">If additional attempts continue to fail, change the password manually using the UI or command line tools.</span></span>  
  
 <span data-ttu-id="5b5d5-128">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="5b5d5-128">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="5b5d5-129">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="5b5d5-129">Password Synchronization</span></span>](../core/password-synchronization2.md)