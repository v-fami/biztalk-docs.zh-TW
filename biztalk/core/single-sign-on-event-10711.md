---
title: 單一登入： 事件 10711 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 40722fe1-4be9-40d3-b5c5-a740a4b59f45
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9966cd2f588d34c3be60282bc7acfa54cd1f42b3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982575"
---
# <a name="single-sign-on-event-10711"></a><span data-ttu-id="cd9cb-102">單一登入： 事件 10711</span><span class="sxs-lookup"><span data-stu-id="cd9cb-102">Single Sign-On: Event 10711</span></span>
## <a name="details"></a><span data-ttu-id="cd9cb-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cd9cb-103">Details</span></span>  

|                 |                                                                                                                                                                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="cd9cb-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cd9cb-104">Product Name</span></span>   |                                                                                                             <span data-ttu-id="cd9cb-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="cd9cb-105">Enterprise Single Sign-On</span></span>                                                                                                             |
| <span data-ttu-id="cd9cb-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="cd9cb-106">Product Version</span></span> |                                                                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                             |
|    <span data-ttu-id="cd9cb-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cd9cb-107">Event ID</span></span>     |                                                                                                                       <span data-ttu-id="cd9cb-108">10711</span><span class="sxs-lookup"><span data-stu-id="cd9cb-108">10711</span></span>                                                                                                                       |
|  <span data-ttu-id="cd9cb-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="cd9cb-109">Event Source</span></span>   |                                                                                                                      <span data-ttu-id="cd9cb-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="cd9cb-110">ENTSSO</span></span>                                                                                                                       |
|    <span data-ttu-id="cd9cb-111">元件</span><span class="sxs-lookup"><span data-stu-id="cd9cb-111">Component</span></span>    |                                                                                                                        <span data-ttu-id="cd9cb-112">N\A</span><span class="sxs-lookup"><span data-stu-id="cd9cb-112">N\A</span></span>                                                                                                                        |
|  <span data-ttu-id="cd9cb-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cd9cb-113">Symbolic Name</span></span>  |                                                                                                         <span data-ttu-id="cd9cb-114">SSO_WARN_PS_MISSING_INITIAL_CREDS</span><span class="sxs-lookup"><span data-stu-id="cd9cb-114">SSO_WARN_PS_MISSING_INITIAL_CREDS</span></span>                                                                                                         |
|  <span data-ttu-id="cd9cb-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cd9cb-115">Message Text</span></span>   | <span data-ttu-id="cd9cb-116">外部密碼變更。</span><span class="sxs-lookup"><span data-stu-id="cd9cb-116">External password change.</span></span> <span data-ttu-id="cd9cb-117">這種對應的部分遺失外部認證欄位已設為預設值。%r</span><span class="sxs-lookup"><span data-stu-id="cd9cb-117">Some missing external credential fields for this mapping have been set to default values.%r</span></span><br /><br /> <span data-ttu-id="cd9cb-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="cd9cb-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="cd9cb-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="cd9cb-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="cd9cb-120">應用程式名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="cd9cb-120">Application Name: %3%r</span></span><br /><br /> <span data-ttu-id="cd9cb-121">外部帳戶： %4</span><span class="sxs-lookup"><span data-stu-id="cd9cb-121">External Account: %4</span></span> |

## <a name="explanation"></a><span data-ttu-id="cd9cb-122">說明</span><span class="sxs-lookup"><span data-stu-id="cd9cb-122">Explanation</span></span>  
 <span data-ttu-id="cd9cb-123">這個警告事件表示已收到外部密碼變更但是有認證遺失。</span><span class="sxs-lookup"><span data-stu-id="cd9cb-123">This Warning event indicates that an external password change was received with missing credentials.</span></span> <span data-ttu-id="cd9cb-124">在這些欄位中使用預設值。</span><span class="sxs-lookup"><span data-stu-id="cd9cb-124">Default values were used in those fields.</span></span>  

## <a name="user-action"></a><span data-ttu-id="cd9cb-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cd9cb-125">User Action</span></span>  
 <span data-ttu-id="cd9cb-126">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="cd9cb-126">To resolve this warning, do the following:</span></span>  

- <span data-ttu-id="cd9cb-127">如有必要，設定要比對的認證。</span><span class="sxs-lookup"><span data-stu-id="cd9cb-127">If necessary, set the credentials to match.</span></span>  

  <span data-ttu-id="cd9cb-128">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="cd9cb-128">For more information, see the following resources:</span></span>  

- [<span data-ttu-id="cd9cb-129">SSO 分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="cd9cb-129">SSO Affiliate Applications</span></span>](../core/sso-affiliate-applications.md)  

- [<span data-ttu-id="cd9cb-130">密碼同步</span><span class="sxs-lookup"><span data-stu-id="cd9cb-130">Password Synchronization</span></span>](../core/password-synchronization2.md)
