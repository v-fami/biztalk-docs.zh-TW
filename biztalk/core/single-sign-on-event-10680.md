---
title: "單一登入： 事件 10680 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88ea12ff-d181-423f-9054-b0c656cc4558
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd7b1804578e1b0880eaa564f68a24f0841280fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10680"></a><span data-ttu-id="93163-102">單一登入： 事件 10680</span><span class="sxs-lookup"><span data-stu-id="93163-102">Single Sign-On: Event 10680</span></span>
## <a name="details"></a><span data-ttu-id="93163-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="93163-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="93163-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="93163-104">Product Name</span></span>|<span data-ttu-id="93163-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="93163-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="93163-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="93163-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="93163-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="93163-107">Event ID</span></span>|<span data-ttu-id="93163-108">10680</span><span class="sxs-lookup"><span data-stu-id="93163-108">10680</span></span>|  
|<span data-ttu-id="93163-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="93163-109">Event Source</span></span>|<span data-ttu-id="93163-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="93163-110">ENTSSO</span></span>|  
|<span data-ttu-id="93163-111">元件</span><span class="sxs-lookup"><span data-stu-id="93163-111">Component</span></span>|<span data-ttu-id="93163-112">N\A</span><span class="sxs-lookup"><span data-stu-id="93163-112">N\A</span></span>|  
|<span data-ttu-id="93163-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="93163-113">Symbolic Name</span></span>|<span data-ttu-id="93163-114">SSO_WARN_PS_GET_CREDS_FAILED</span><span class="sxs-lookup"><span data-stu-id="93163-114">SSO_WARN_PS_GET_CREDS_FAILED</span></span>|  
|<span data-ttu-id="93163-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="93163-115">Message Text</span></span>|<span data-ttu-id="93163-116">外部帳戶的密碼未變更，因為無法從 SSO 資料庫取得現有外部認證。%r</span><span class="sxs-lookup"><span data-stu-id="93163-116">The password was not changed for the external account because the existing external credentials could not be obtained from the SSO database.%r</span></span><br /><br /> <span data-ttu-id="93163-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="93163-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="93163-118">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="93163-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="93163-119">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="93163-119">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="93163-120">外部帳戶: %4 %r</span><span class="sxs-lookup"><span data-stu-id="93163-120">External Account: %4%r</span></span><br /><br /> <span data-ttu-id="93163-121">錯誤碼： %5</span><span class="sxs-lookup"><span data-stu-id="93163-121">Error Code: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="93163-122">說明</span><span class="sxs-lookup"><span data-stu-id="93163-122">Explanation</span></span>  
 <span data-ttu-id="93163-123">這個警告事件表示，密碼未變更外部帳戶因為無法從 SSO 資料庫取得現有外部認證。</span><span class="sxs-lookup"><span data-stu-id="93163-123">This Warning event indicates that the password was not changed for the external account because the existing external credentials could not be obtained from the SSO database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="93163-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="93163-124">User Action</span></span>  
 <span data-ttu-id="93163-125">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="93163-125">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="93163-126">驗證外部認證。</span><span class="sxs-lookup"><span data-stu-id="93163-126">Verify external credentials.</span></span>  
  
-   <span data-ttu-id="93163-127">外部認證不正確，請使用 SSO 管理工具設定此外部帳戶的外部認證。</span><span class="sxs-lookup"><span data-stu-id="93163-127">The external credentials are not valid, use the SSO administration tools to set the external credentials for this external account.</span></span> <span data-ttu-id="93163-128">您必須在所有相關聯的應用程式中設定的外部密碼 （用於指定的帳戶）。</span><span class="sxs-lookup"><span data-stu-id="93163-128">You must set the external password (for the given account) in all associated applications.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="93163-129">其他資訊</span><span class="sxs-lookup"><span data-stu-id="93163-129">More info</span></span>
  
-   [<span data-ttu-id="93163-130">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="93163-130">Password Synchronization</span></span>](../core/password-synchronization2.md)  
  
-   <span data-ttu-id="93163-131">**密碼同步配接器屬性： 選項**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="93163-131">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>