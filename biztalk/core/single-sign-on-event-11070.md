---
title: "單一登入： 事件 11070 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb669df9-710a-4792-bdd4-cca0c03fcda2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb0d2a868d5c8bf47cbcb5389bf2d16dadf4010a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11070"></a><span data-ttu-id="b0838-102">單一登入： 事件 11070</span><span class="sxs-lookup"><span data-stu-id="b0838-102">Single Sign-On: Event 11070</span></span>
## <a name="details"></a><span data-ttu-id="b0838-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b0838-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b0838-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b0838-104">Product Name</span></span>|<span data-ttu-id="b0838-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="b0838-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="b0838-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="b0838-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="b0838-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b0838-107">Event ID</span></span>|<span data-ttu-id="b0838-108">11070</span><span class="sxs-lookup"><span data-stu-id="b0838-108">11070</span></span>|  
|<span data-ttu-id="b0838-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="b0838-109">Event Source</span></span>|<span data-ttu-id="b0838-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="b0838-110">ENTSSO</span></span>|  
|<span data-ttu-id="b0838-111">元件</span><span class="sxs-lookup"><span data-stu-id="b0838-111">Component</span></span>|<span data-ttu-id="b0838-112">不適用</span><span class="sxs-lookup"><span data-stu-id="b0838-112">N/A</span></span>|  
|<span data-ttu-id="b0838-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b0838-113">Symbolic Name</span></span>|<span data-ttu-id="b0838-114">SSO_WARN_PS_MIIS_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="b0838-114">SSO_WARN_PS_MIIS_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="b0838-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b0838-115">Message Text</span></span>|<span data-ttu-id="b0838-116">這部 SSO 伺服器目前未設定為允許來自 MIIS 的 Windows 密碼變更。</span><span class="sxs-lookup"><span data-stu-id="b0838-116">This SSO server is currently not configured to allow Windows password changes from MIIS.</span></span> <span data-ttu-id="b0838-117">使用 'ssoconfig-allowPS MIIS yes' 或 SSO 管理 MMC.%r</span><span class="sxs-lookup"><span data-stu-id="b0838-117">Use 'ssoconfig -allowPS MIIS yes' or the SSO Administration MMC.%r</span></span><br /><br /> <span data-ttu-id="b0838-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="b0838-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="b0838-119">用戶端使用者： %2</span><span class="sxs-lookup"><span data-stu-id="b0838-119">Client User: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b0838-120">說明</span><span class="sxs-lookup"><span data-stu-id="b0838-120">Explanation</span></span>  
 <span data-ttu-id="b0838-121">這部 SSO 伺服器目前未設定為允許來自 MIIS 的 Windows 密碼變更。</span><span class="sxs-lookup"><span data-stu-id="b0838-121">This SSO server is currently not configured to allow Windows password changes from MIIS.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b0838-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b0838-122">User Action</span></span>  
 <span data-ttu-id="b0838-123">若要允許的 Windows 密碼變更從 MIIS，**伺服器嵌入式管理單元**，**密碼同步屬性**索引標籤上，選取**允許從 MIIS 進行密碼同步。**</span><span class="sxs-lookup"><span data-stu-id="b0838-123">To allow Windows password changes from MIIS, in the **Servers Snap-In**, **Password Sync Properties** tab, select **Allow Password Sync from MIIS.**</span></span>  
  
 <span data-ttu-id="b0838-124">如需詳細資訊，請參閱[如何使用伺服器嵌入式管理單元](../core/how-to-use-the-servers-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="b0838-124">For more information, see [How to Use the Servers Snap-in](../core/how-to-use-the-servers-snap-in.md).</span></span>