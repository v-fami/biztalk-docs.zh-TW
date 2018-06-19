---
title: 單一登入： 事件 10715 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f63c98d2-988e-466f-be40-171b13a34732
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24bf65f00d9ef915d585c91aa06900b96d4b44d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270846"
---
# <a name="single-sign-on-event-10715"></a><span data-ttu-id="f951b-102">單一登入： 事件 10715</span><span class="sxs-lookup"><span data-stu-id="f951b-102">Single Sign-On: Event 10715</span></span>
## <a name="details"></a><span data-ttu-id="f951b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f951b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f951b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f951b-104">Product Name</span></span>|<span data-ttu-id="f951b-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="f951b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="f951b-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="f951b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="f951b-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f951b-107">Event ID</span></span>|<span data-ttu-id="f951b-108">10715</span><span class="sxs-lookup"><span data-stu-id="f951b-108">10715</span></span>|  
|<span data-ttu-id="f951b-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="f951b-109">Event Source</span></span>|<span data-ttu-id="f951b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f951b-110">ENTSSO</span></span>|  
|<span data-ttu-id="f951b-111">元件</span><span class="sxs-lookup"><span data-stu-id="f951b-111">Component</span></span>|<span data-ttu-id="f951b-112">N\A</span><span class="sxs-lookup"><span data-stu-id="f951b-112">N\A</span></span>|  
|<span data-ttu-id="f951b-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f951b-113">Symbolic Name</span></span>|<span data-ttu-id="f951b-114">SSO_WARN_NO_CREATE_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="f951b-114">SSO_WARN_NO_CREATE_ADAPTER</span></span>|  
|<span data-ttu-id="f951b-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f951b-115">Message Text</span></span>|<span data-ttu-id="f951b-116">用戶端使用者必須是 SSO 系統管理員帳戶的成員，才能建立配接器。%r</span><span class="sxs-lookup"><span data-stu-id="f951b-116">The client user must be a member of the SSO Administrators account to create adapters.%r</span></span><br /><br /> <span data-ttu-id="f951b-117">用戶端使用者: %1 %r</span><span class="sxs-lookup"><span data-stu-id="f951b-117">Client User: %1%r</span></span><br /><br /> <span data-ttu-id="f951b-118">SSO 系統管理員: %2 %r</span><span class="sxs-lookup"><span data-stu-id="f951b-118">SSO Administrators: %2%r</span></span><br /><br /> <span data-ttu-id="f951b-119">配接器: %3 %r</span><span class="sxs-lookup"><span data-stu-id="f951b-119">Adapter: %3%r</span></span><br /><br /> <span data-ttu-id="f951b-120">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="f951b-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f951b-121">說明</span><span class="sxs-lookup"><span data-stu-id="f951b-121">Explanation</span></span>  
 <span data-ttu-id="f951b-122">這個警告事件表示用戶端使用者必須是 SSO 系統管理員帳戶的成員，才能建立配接器。</span><span class="sxs-lookup"><span data-stu-id="f951b-122">This Warning event indicates that the client user must be a member of the SSO Administrators account to create adapters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f951b-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f951b-123">User Action</span></span>  
 <span data-ttu-id="f951b-124">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f951b-124">To resolve this warning, do the following:</span></span>  
  
-   <span data-ttu-id="f951b-125">使用屬於 SSO 系統管理員群組的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="f951b-125">Logon with an account that belongs to the SSO Administrators group.</span></span>  
  
 <span data-ttu-id="f951b-126">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="f951b-126">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="f951b-127">SSO 使用者群組</span><span class="sxs-lookup"><span data-stu-id="f951b-127">SSO User Groups</span></span>](../core/sso-user-groups.md)