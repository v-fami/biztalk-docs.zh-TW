---
title: 單一登入： 事件 11023 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: feeb4ede-6045-46bf-9f2b-65062c583faa
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cecf9536babaf2510444abade571149c5fc0e0a2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991535"
---
# <a name="single-sign-on-event-11023"></a><span data-ttu-id="5e59d-102">單一登入： 事件 11023</span><span class="sxs-lookup"><span data-stu-id="5e59d-102">Single Sign-On: Event 11023</span></span>
## <a name="details"></a><span data-ttu-id="5e59d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5e59d-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="5e59d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5e59d-104">Product Name</span></span>   |                                                                                                                                 <span data-ttu-id="5e59d-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="5e59d-105">Enterprise Single Sign-On</span></span>                                                                                                                                  |
| <span data-ttu-id="5e59d-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="5e59d-106">Product Version</span></span> |                                                                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                 |
|    <span data-ttu-id="5e59d-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5e59d-107">Event ID</span></span>     |                                                                                                                                           <span data-ttu-id="5e59d-108">11023</span><span class="sxs-lookup"><span data-stu-id="5e59d-108">11023</span></span>                                                                                                                                            |
|  <span data-ttu-id="5e59d-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="5e59d-109">Event Source</span></span>   |                                                                                                                                           <span data-ttu-id="5e59d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="5e59d-110">ENTSSO</span></span>                                                                                                                                           |
|    <span data-ttu-id="5e59d-111">元件</span><span class="sxs-lookup"><span data-stu-id="5e59d-111">Component</span></span>    |                                                                                                                                            <span data-ttu-id="5e59d-112">不適用</span><span class="sxs-lookup"><span data-stu-id="5e59d-112">N/A</span></span>                                                                                                                                             |
|  <span data-ttu-id="5e59d-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5e59d-113">Symbolic Name</span></span>  |                                                                                                                             <span data-ttu-id="5e59d-114">SSO_WARN_WINDOWS_PASSWORD_DELETED</span><span class="sxs-lookup"><span data-stu-id="5e59d-114">SSO_WARN_WINDOWS_PASSWORD_DELETED</span></span>                                                                                                                              |
|  <span data-ttu-id="5e59d-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5e59d-115">Message Text</span></span>   | <span data-ttu-id="5e59d-116">無效的 Windows 密碼在 SSO 資料庫中已刪除，以防止帳戶 lockout.%r</span><span class="sxs-lookup"><span data-stu-id="5e59d-116">An invalid Windows password in the SSO database was deleted to prevent account lockout.%r</span></span><br /><br /> <span data-ttu-id="5e59d-117">若要設定此 Windows account.%r 的外部認證使用 SSO 管理工具</span><span class="sxs-lookup"><span data-stu-id="5e59d-117">Use the SSO administration tools to set the external credentials for this Windows account.%r</span></span><br /><br /> <span data-ttu-id="5e59d-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="5e59d-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="5e59d-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="5e59d-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="5e59d-120">Windows 帳戶： %3</span><span class="sxs-lookup"><span data-stu-id="5e59d-120">Windows Account: %3</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="5e59d-121">說明</span><span class="sxs-lookup"><span data-stu-id="5e59d-121">Explanation</span></span>  
 <span data-ttu-id="5e59d-122">已刪除無效的 Windows 密碼。</span><span class="sxs-lookup"><span data-stu-id="5e59d-122">An invalid Windows password has been deleted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5e59d-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5e59d-123">User Action</span></span>  
 <span data-ttu-id="5e59d-124">您可以使用 SSO 管理工具來設定此 Windows 帳戶的外部認證。</span><span class="sxs-lookup"><span data-stu-id="5e59d-124">Use the SSO administration tools to set the external credentials for this Windows account.</span></span> <span data-ttu-id="5e59d-125">如需詳細資訊，請參閱 <<c0> [ 使用 SSO](../core/using-sso.md)。</span><span class="sxs-lookup"><span data-stu-id="5e59d-125">For more information, see [Using SSO](../core/using-sso.md).</span></span>