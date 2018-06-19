---
title: 單一登入： 事件 11068 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f09a1191-ae67-4156-a8a5-d24e4439fc68
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be824a9205d81aaaeb9fd87129133b94b4f2e379
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277806"
---
# <a name="single-sign-on-event-11068"></a><span data-ttu-id="2478a-102">單一登入： 事件 11068</span><span class="sxs-lookup"><span data-stu-id="2478a-102">Single Sign-On: Event 11068</span></span>
## <a name="details"></a><span data-ttu-id="2478a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2478a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2478a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2478a-104">Product Name</span></span>|<span data-ttu-id="2478a-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="2478a-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="2478a-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="2478a-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="2478a-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2478a-107">Event ID</span></span>|<span data-ttu-id="2478a-108">11068</span><span class="sxs-lookup"><span data-stu-id="2478a-108">11068</span></span>|  
|<span data-ttu-id="2478a-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="2478a-109">Event Source</span></span>|<span data-ttu-id="2478a-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="2478a-110">ENTSSO</span></span>|  
|<span data-ttu-id="2478a-111">元件</span><span class="sxs-lookup"><span data-stu-id="2478a-111">Component</span></span>|<span data-ttu-id="2478a-112">不適用</span><span class="sxs-lookup"><span data-stu-id="2478a-112">N/A</span></span>|  
|<span data-ttu-id="2478a-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2478a-113">Symbolic Name</span></span>|<span data-ttu-id="2478a-114">SSO_ERROR_LOOKUP_CALLBACK_ACCESS_DENIED_NO_REMOTE</span><span class="sxs-lookup"><span data-stu-id="2478a-114">SSO_ERROR_LOOKUP_CALLBACK_ACCESS_DENIED_NO_REMOTE</span></span>|  
|<span data-ttu-id="2478a-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2478a-115">Message Text</span></span>|<span data-ttu-id="2478a-116">拒絕存取尋查伺服器。</span><span class="sxs-lookup"><span data-stu-id="2478a-116">Lookup server access denied.</span></span> <span data-ttu-id="2478a-117">這部 SSO 伺服器目前未設定為允許遠端尋查。</span><span class="sxs-lookup"><span data-stu-id="2478a-117">This SSO server is currently not configured to allow remote lookup.</span></span> <span data-ttu-id="2478a-118">使用 'ssoconfig-remote 尋查 yes' 或 SSO 管理 MMC.%r</span><span class="sxs-lookup"><span data-stu-id="2478a-118">Use 'ssoconfig -remoteLookup yes' or the SSO Administration MMC.%r</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2478a-119">說明</span><span class="sxs-lookup"><span data-stu-id="2478a-119">Explanation</span></span>  
 <span data-ttu-id="2478a-120">存取查閱伺服器被拒因為 ENTSSO 伺服器並未設定為允許遠端尋查。</span><span class="sxs-lookup"><span data-stu-id="2478a-120">Lookup server access has been denied because the ENTSSO server is not configured to allow remote lookup.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2478a-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2478a-121">User Action</span></span>  
 <span data-ttu-id="2478a-122">若要允許遠端尋查，**伺服器嵌入式管理單元**，**進階**索引標籤上，選取**允許遠端尋查**。</span><span class="sxs-lookup"><span data-stu-id="2478a-122">To allow remote lookup, in the **Servers Snap-In**, **Advanced** tab, select **Allow Remote Lookup**.</span></span>  
  
 <span data-ttu-id="2478a-123">如需詳細資訊，請參閱[如何使用伺服器嵌入式管理單元](../core/how-to-use-the-servers-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="2478a-123">For more information, see [How to Use the Servers Snap-in](../core/how-to-use-the-servers-snap-in.md).</span></span>