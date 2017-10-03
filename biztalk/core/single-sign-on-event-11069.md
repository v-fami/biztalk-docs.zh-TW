---
title: "單一登入： 事件 11069 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1accfe68-000c-4b5e-909c-244e18eba110
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66f89a1d273b0ed621cd3b59526714d9cb167bfb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11069"></a><span data-ttu-id="2654d-102">單一登入： 事件 11069</span><span class="sxs-lookup"><span data-stu-id="2654d-102">Single Sign-On: Event 11069</span></span>
## <a name="details"></a><span data-ttu-id="2654d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2654d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2654d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2654d-104">Product Name</span></span>|<span data-ttu-id="2654d-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="2654d-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="2654d-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="2654d-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="2654d-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2654d-107">Event ID</span></span>|<span data-ttu-id="2654d-108">11069</span><span class="sxs-lookup"><span data-stu-id="2654d-108">11069</span></span>|  
|<span data-ttu-id="2654d-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="2654d-109">Event Source</span></span>|<span data-ttu-id="2654d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="2654d-110">ENTSSO</span></span>|  
|<span data-ttu-id="2654d-111">元件</span><span class="sxs-lookup"><span data-stu-id="2654d-111">Component</span></span>|<span data-ttu-id="2654d-112">不適用</span><span class="sxs-lookup"><span data-stu-id="2654d-112">N/A</span></span>|  
|<span data-ttu-id="2654d-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2654d-113">Symbolic Name</span></span>|<span data-ttu-id="2654d-114">SSO_WARN_PS_PCNS_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="2654d-114">SSO_WARN_PS_PCNS_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="2654d-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2654d-115">Message Text</span></span>|<span data-ttu-id="2654d-116">此 SSO 伺服器目前未設定為允許從 PCNS 進行 Windows 密碼變更。</span><span class="sxs-lookup"><span data-stu-id="2654d-116">This SSO server is currently not configured to allow Windows password changes from PCNS.</span></span> <span data-ttu-id="2654d-117">使用 'ssoconfig-allowPS PCNS yes' 或 SSO 管理 MMC.%r</span><span class="sxs-lookup"><span data-stu-id="2654d-117">Use 'ssoconfig -allowPS PCNS yes' or the SSO Administration MMC.%r</span></span><br /><br /> <span data-ttu-id="2654d-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="2654d-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="2654d-119">用戶端使用者： %2</span><span class="sxs-lookup"><span data-stu-id="2654d-119">Client User: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2654d-120">說明</span><span class="sxs-lookup"><span data-stu-id="2654d-120">Explanation</span></span>  
 <span data-ttu-id="2654d-121">此 SSO 伺服器目前未設定為允許從 PCNS 進行 Windows 密碼變更。</span><span class="sxs-lookup"><span data-stu-id="2654d-121">This SSO server is currently not configured to allow Windows password changes from PCNS.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2654d-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2654d-122">User Action</span></span>  
 <span data-ttu-id="2654d-123">若要允許來自 PCNS 的 Windows 密碼變更，在**伺服器嵌入式管理單元**，**密碼同步屬性**索引標籤上，選取**允許從 PCNS 進行密碼同步。**</span><span class="sxs-lookup"><span data-stu-id="2654d-123">To allow Windows password changes from PCNS, in the **Servers Snap-In**, **Password Sync Properties** tab, select **Allow Password Sync from PCNS.**</span></span>  
  
 <span data-ttu-id="2654d-124">如需詳細資訊，請參閱[如何使用伺服器嵌入式管理單元](../core/how-to-use-the-servers-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="2654d-124">For more information, see [How to Use the Servers Snap-in](../core/how-to-use-the-servers-snap-in.md).</span></span>