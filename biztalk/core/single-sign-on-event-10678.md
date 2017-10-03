---
title: "單一登入： 事件 10678 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6af92ce1-fdac-432f-be6b-cf8958aee776
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: daa6639e361abf364e012ec9a4f19f049bbcd08f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10678"></a><span data-ttu-id="8b45e-102">單一登入： 事件 10678</span><span class="sxs-lookup"><span data-stu-id="8b45e-102">Single Sign-On: Event 10678</span></span>
## <a name="details"></a><span data-ttu-id="8b45e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8b45e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b45e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8b45e-104">Product Name</span></span>|<span data-ttu-id="8b45e-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="8b45e-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="8b45e-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="8b45e-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="8b45e-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8b45e-107">Event ID</span></span>|<span data-ttu-id="8b45e-108">10678</span><span class="sxs-lookup"><span data-stu-id="8b45e-108">10678</span></span>|  
|<span data-ttu-id="8b45e-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="8b45e-109">Event Source</span></span>|<span data-ttu-id="8b45e-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="8b45e-110">ENTSSO</span></span>|  
|<span data-ttu-id="8b45e-111">元件</span><span class="sxs-lookup"><span data-stu-id="8b45e-111">Component</span></span>|<span data-ttu-id="8b45e-112">N\A</span><span class="sxs-lookup"><span data-stu-id="8b45e-112">N\A</span></span>|  
|<span data-ttu-id="8b45e-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8b45e-113">Symbolic Name</span></span>|<span data-ttu-id="8b45e-114">SSO_WARN_PASSWORD_MISMATCH</span><span class="sxs-lookup"><span data-stu-id="8b45e-114">SSO_WARN_PASSWORD_MISMATCH</span></span>|  
|<span data-ttu-id="8b45e-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8b45e-115">Message Text</span></span>|<span data-ttu-id="8b45e-116">外部密碼變更。</span><span class="sxs-lookup"><span data-stu-id="8b45e-116">External password change.</span></span> <span data-ttu-id="8b45e-117">配接器所提供的舊密碼不符合現有的密碼和外部 account.%r</span><span class="sxs-lookup"><span data-stu-id="8b45e-117">The old password supplied by the adapter does not match the existing password for the external account.%r</span></span><br /><br /> <span data-ttu-id="8b45e-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="8b45e-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="8b45e-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="8b45e-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="8b45e-120">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="8b45e-120">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="8b45e-121">外部帳戶： %4</span><span class="sxs-lookup"><span data-stu-id="8b45e-121">External Account: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8b45e-122">說明</span><span class="sxs-lookup"><span data-stu-id="8b45e-122">Explanation</span></span>  
 <span data-ttu-id="8b45e-123">這個警告事件表示配接器所提供的舊密碼不符合現有外部帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="8b45e-123">This Warning event indicates that the old password supplied by the adapter does not match the existing password for the external account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8b45e-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8b45e-124">User Action</span></span>  
 <span data-ttu-id="8b45e-125">若要解決這個警告，請執行下列：</span><span class="sxs-lookup"><span data-stu-id="8b45e-125">To resolve this warning do the following:</span></span>  
  
-   <span data-ttu-id="8b45e-126">判斷哪些應用程式已指派給此配接器 （在事件記錄檔訊息中的名稱），然後使用 SSO 管理工具來設定這個外部帳戶的外部認證。</span><span class="sxs-lookup"><span data-stu-id="8b45e-126">Determine which Applications were assigned to this Adapter (name in event log message) and then use the SSO administration tools to set the external credentials for this external account.</span></span> <span data-ttu-id="8b45e-127">您必須在所有這些應用程式設定 （適用於指定的帳戶） 的外部密碼。</span><span class="sxs-lookup"><span data-stu-id="8b45e-127">You must set the external password (for the given account) in all of those Applications.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="8b45e-128">其他資訊</span><span class="sxs-lookup"><span data-stu-id="8b45e-128">More info</span></span>
  
-   [<span data-ttu-id="8b45e-129">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="8b45e-129">Password Synchronization</span></span>](../core/password-synchronization2.md)  
  
-   <span data-ttu-id="8b45e-130">**密碼同步配接器屬性： 選項**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="8b45e-130">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>