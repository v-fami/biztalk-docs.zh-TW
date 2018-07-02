---
title: 單一登入： 事件 10740 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8e8521e7-32af-4a58-8b1a-66ea1d13f1e1
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9bf7c2cdaae3cffe280035f007cd1b49d2c70c8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970055"
---
# <a name="single-sign-on-event-10740"></a><span data-ttu-id="ac919-102">單一登入： 事件 10740</span><span class="sxs-lookup"><span data-stu-id="ac919-102">Single Sign-On: Event 10740</span></span>
## <a name="details"></a><span data-ttu-id="ac919-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ac919-103">Details</span></span>  

|                 |                                                                                                                                                            |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="ac919-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ac919-104">Product Name</span></span>   |                                                                 <span data-ttu-id="ac919-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="ac919-105">Enterprise Single Sign-On</span></span>                                                                  |
| <span data-ttu-id="ac919-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="ac919-106">Product Version</span></span> |                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                 |
|    <span data-ttu-id="ac919-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ac919-107">Event ID</span></span>     |                                                                           <span data-ttu-id="ac919-108">10740</span><span class="sxs-lookup"><span data-stu-id="ac919-108">10740</span></span>                                                                            |
|  <span data-ttu-id="ac919-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="ac919-109">Event Source</span></span>   |                                                                           <span data-ttu-id="ac919-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ac919-110">ENTSSO</span></span>                                                                           |
|    <span data-ttu-id="ac919-111">元件</span><span class="sxs-lookup"><span data-stu-id="ac919-111">Component</span></span>    |                                                                            <span data-ttu-id="ac919-112">N\A</span><span class="sxs-lookup"><span data-stu-id="ac919-112">N\A</span></span>                                                                             |
|  <span data-ttu-id="ac919-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ac919-113">Symbolic Name</span></span>  |                                                               <span data-ttu-id="ac919-114">SSO_WARN_INVALID_WINDOWS_USER</span><span class="sxs-lookup"><span data-stu-id="ac919-114">SSO_WARN_INVALID_WINDOWS_USER</span></span>                                                                |
|  <span data-ttu-id="ac919-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ac919-115">Message Text</span></span>   | <span data-ttu-id="ac919-116">對應用程式 update.%r 的 Windows 帳戶無效</span><span class="sxs-lookup"><span data-stu-id="ac919-116">The Windows Account is not valid for application update.%r</span></span><br /><br /> <span data-ttu-id="ac919-117">應用程式名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="ac919-117">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="ac919-118">Windows 帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="ac919-118">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="ac919-119">錯誤碼： %3</span><span class="sxs-lookup"><span data-stu-id="ac919-119">Error Code: %3</span></span> |

## <a name="explanation"></a><span data-ttu-id="ac919-120">說明</span><span class="sxs-lookup"><span data-stu-id="ac919-120">Explanation</span></span>  
 <span data-ttu-id="ac919-121">這個警告事件表示 （事件訊息中指定） 的 Windows 帳戶不是有效的應用程式更新。</span><span class="sxs-lookup"><span data-stu-id="ac919-121">This Warning event indicates that the Windows Account (specified in the event message) is not valid for application update.</span></span> <span data-ttu-id="ac919-122">變更主機群組應用程式的 Windows 帳戶時，可能發生這項目。</span><span class="sxs-lookup"><span data-stu-id="ac919-122">This can occur when changing the Windows account for a Host Group application.</span></span> <span data-ttu-id="ac919-123">主機群組應用程式可讓單一登入外部系統的 Windows 系統。</span><span class="sxs-lookup"><span data-stu-id="ac919-123">Host Group applications are used for single sign-on from external systems to Windows systems.</span></span> <span data-ttu-id="ac919-124">它們可以將一組外部的使用者對應至單一的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="ac919-124">They can map a set of external users to a single Windows account.</span></span> <span data-ttu-id="ac919-125">它們會對應至 Windows 帳戶被定義應用程式的 [應用程式使用者] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="ac919-125">The Windows account they are mapped to is defined in the Application Users field of the application.</span></span>  

## <a name="user-action"></a><span data-ttu-id="ac919-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ac919-126">User Action</span></span>  
 <span data-ttu-id="ac919-127">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="ac919-127">To resolve this warning, do the following:</span></span>  

- <span data-ttu-id="ac919-128">檢查 Windows 帳戶已使用無效。</span><span class="sxs-lookup"><span data-stu-id="ac919-128">Check that the Windows account your are using is valid.</span></span>  

- <span data-ttu-id="ac919-129">重新建立具有正確的 Windows 帳戶屬性的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="ac919-129">Recreate the Windows account with the correct Windows account properties.</span></span>  

  <span data-ttu-id="ac919-130">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="ac919-130">For more information, see the following resources:</span></span>  

- [<span data-ttu-id="ac919-131">密碼同步</span><span class="sxs-lookup"><span data-stu-id="ac919-131">Password Synchronization</span></span>](../core/password-synchronization2.md)
