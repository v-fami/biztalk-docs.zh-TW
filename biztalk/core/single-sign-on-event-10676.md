---
title: 單一登入： 事件 10676 |Microsoft Docs
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
ms.openlocfilehash: 63228e82546e100c81bf01c301d7d9507f147671
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991927"
---
# <a name="single-sign-on-event-10676"></a><span data-ttu-id="3eec7-102">單一登入： 事件 10676</span><span class="sxs-lookup"><span data-stu-id="3eec7-102">Single Sign-On: Event 10676</span></span>
## <a name="details"></a><span data-ttu-id="3eec7-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3eec7-103">Details</span></span>  

|                 |                                                                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="3eec7-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3eec7-104">Product Name</span></span>   |                                                                                             <span data-ttu-id="3eec7-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="3eec7-105">Enterprise Single Sign-On</span></span>                                                                                             |
| <span data-ttu-id="3eec7-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="3eec7-106">Product Version</span></span> |                                                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                             |
|    <span data-ttu-id="3eec7-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3eec7-107">Event ID</span></span>     |                                                                                                       <span data-ttu-id="3eec7-108">10676</span><span class="sxs-lookup"><span data-stu-id="3eec7-108">10676</span></span>                                                                                                       |
|  <span data-ttu-id="3eec7-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="3eec7-109">Event Source</span></span>   |                                                                                                      <span data-ttu-id="3eec7-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="3eec7-110">ENTSSO</span></span>                                                                                                       |
|    <span data-ttu-id="3eec7-111">元件</span><span class="sxs-lookup"><span data-stu-id="3eec7-111">Component</span></span>    |                                                                                                        <span data-ttu-id="3eec7-112">N\A</span><span class="sxs-lookup"><span data-stu-id="3eec7-112">N\A</span></span>                                                                                                        |
|  <span data-ttu-id="3eec7-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3eec7-113">Symbolic Name</span></span>  |                                                                                          <span data-ttu-id="3eec7-114">SSO_ERROR_REQUIRE_OLD_PASSWORD</span><span class="sxs-lookup"><span data-stu-id="3eec7-114">SSO_ERROR_REQUIRE_OLD_PASSWORD</span></span>                                                                                           |
|  <span data-ttu-id="3eec7-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3eec7-115">Message Text</span></span>   | <span data-ttu-id="3eec7-116">外部密碼變更。</span><span class="sxs-lookup"><span data-stu-id="3eec7-116">External password change.</span></span> <span data-ttu-id="3eec7-117">變更外部帳戶的密碼時，配接器必須提供舊 password.%r</span><span class="sxs-lookup"><span data-stu-id="3eec7-117">When changing the password for an external account the adapter must supply the old password.%r</span></span><br /><br /> <span data-ttu-id="3eec7-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="3eec7-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="3eec7-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="3eec7-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="3eec7-120">外部帳戶： %3</span><span class="sxs-lookup"><span data-stu-id="3eec7-120">External Account: %3</span></span> |

## <a name="explanation"></a><span data-ttu-id="3eec7-121">說明</span><span class="sxs-lookup"><span data-stu-id="3eec7-121">Explanation</span></span>  
 <span data-ttu-id="3eec7-122">這個錯誤事件表示 「 密碼同步配接器已設定為預期收到來自外部系統中，舊的密碼，但未提供舊密碼。</span><span class="sxs-lookup"><span data-stu-id="3eec7-122">This Error event indicates that the password sync adapter was configured to expect an old password from the external system, but an old password was not provided.</span></span> <span data-ttu-id="3eec7-123">可能是未設定外部系統 （外部密碼同步配接器），或如預期般運作或密碼同步配接器設定不正確。</span><span class="sxs-lookup"><span data-stu-id="3eec7-123">Either the external system (the external password sync adapter) is not configured or working as expected or the password sync adapter is incorrectly configured.</span></span> <span data-ttu-id="3eec7-124">這項錯誤也可能會傳回錯誤的程式碼符號名稱 ENTSSO_E_REQUIRE_OLD_PASSWORD。</span><span class="sxs-lookup"><span data-stu-id="3eec7-124">This error may also return error code symbolic name ENTSSO_E_REQUIRE_OLD_PASSWORD.</span></span>  

## <a name="user-action"></a><span data-ttu-id="3eec7-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3eec7-125">User Action</span></span>  
 <span data-ttu-id="3eec7-126">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="3eec7-126">To resolve this error, do the following:</span></span>  

-   <span data-ttu-id="3eec7-127">若要設定使用者可設定的屬性使用 SSO 管理工具**驗證舊密碼**密碼同步配接器選項內容 索引標籤上。這個屬性也可以設定建立配接器，透過命令列工具 (ssops.exe) 旗標名稱`verifyOldPassword`和也當建立新的密碼同步配接器使用 「 密碼同步配接器精靈 」。</span><span class="sxs-lookup"><span data-stu-id="3eec7-127">Use the SSO administration tools to set the user configurable property **Verify Old Password** on the Password Sync Adapter Options properties tab. This property can also be set when creating adapters via the command line tools (ssops.exe) with the flag name `verifyOldPassword` and also when creating a new password sync adapter using the Password Sync Adapter wizard.</span></span>  

## <a name="more-info"></a><span data-ttu-id="3eec7-128">其他資訊</span><span class="sxs-lookup"><span data-stu-id="3eec7-128">More info</span></span>

- [<span data-ttu-id="3eec7-129">密碼同步</span><span class="sxs-lookup"><span data-stu-id="3eec7-129">Password Synchronization</span></span>](../core/password-synchronization2.md)  

- <span data-ttu-id="3eec7-130">**密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="3eec7-130">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
