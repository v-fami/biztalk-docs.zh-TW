---
title: 單一登入： 事件 11068 |Microsoft Docs
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
ms.openlocfilehash: 218da642493981211de4a0e10b504ea8f434945f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020492"
---
# <a name="single-sign-on-event-11068"></a><span data-ttu-id="862a2-102">單一登入： 事件 11068</span><span class="sxs-lookup"><span data-stu-id="862a2-102">Single Sign-On: Event 11068</span></span>
## <a name="details"></a><span data-ttu-id="862a2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="862a2-103">Details</span></span>  
  
|                 |                                                                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="862a2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="862a2-104">Product Name</span></span>   |                                                                      <span data-ttu-id="862a2-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="862a2-105">Enterprise Single Sign-On</span></span>                                                                      |
| <span data-ttu-id="862a2-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="862a2-106">Product Version</span></span> |                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                      |
|    <span data-ttu-id="862a2-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="862a2-107">Event ID</span></span>     |                                                                                <span data-ttu-id="862a2-108">11068</span><span class="sxs-lookup"><span data-stu-id="862a2-108">11068</span></span>                                                                                |
|  <span data-ttu-id="862a2-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="862a2-109">Event Source</span></span>   |                                                                               <span data-ttu-id="862a2-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="862a2-110">ENTSSO</span></span>                                                                                |
|    <span data-ttu-id="862a2-111">元件</span><span class="sxs-lookup"><span data-stu-id="862a2-111">Component</span></span>    |                                                                                 <span data-ttu-id="862a2-112">不適用</span><span class="sxs-lookup"><span data-stu-id="862a2-112">N/A</span></span>                                                                                 |
|  <span data-ttu-id="862a2-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="862a2-113">Symbolic Name</span></span>  |                                                          <span data-ttu-id="862a2-114">SSO_ERROR_LOOKUP_CALLBACK_ACCESS_DENIED_NO_REMOTE</span><span class="sxs-lookup"><span data-stu-id="862a2-114">SSO_ERROR_LOOKUP_CALLBACK_ACCESS_DENIED_NO_REMOTE</span></span>                                                          |
|  <span data-ttu-id="862a2-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="862a2-115">Message Text</span></span>   | <span data-ttu-id="862a2-116">拒絕存取查閱伺服器。</span><span class="sxs-lookup"><span data-stu-id="862a2-116">Lookup server access denied.</span></span> <span data-ttu-id="862a2-117">這部 SSO 伺服器目前未設定為允許遠端尋查。</span><span class="sxs-lookup"><span data-stu-id="862a2-117">This SSO server is currently not configured to allow remote lookup.</span></span> <span data-ttu-id="862a2-118">使用 'ssoconfig-remote 尋查 yes' 或 SSO 管理 MMC.%r</span><span class="sxs-lookup"><span data-stu-id="862a2-118">Use 'ssoconfig -remoteLookup yes' or the SSO Administration MMC.%r</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="862a2-119">說明</span><span class="sxs-lookup"><span data-stu-id="862a2-119">Explanation</span></span>  
 <span data-ttu-id="862a2-120">存取查閱伺服器被拒因為 ENTSSO 伺服器未設定為允許遠端尋查。</span><span class="sxs-lookup"><span data-stu-id="862a2-120">Lookup server access has been denied because the ENTSSO server is not configured to allow remote lookup.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="862a2-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="862a2-121">User Action</span></span>  
 <span data-ttu-id="862a2-122">若要允許遠端尋查中,**伺服器嵌入式管理單元**，**進階**索引標籤上，選取**允許遠端尋查**。</span><span class="sxs-lookup"><span data-stu-id="862a2-122">To allow remote lookup, in the **Servers Snap-In**, **Advanced** tab, select **Allow Remote Lookup**.</span></span>  
  
 <span data-ttu-id="862a2-123">如需詳細資訊，請參閱 <<c0> [ 如何使用伺服器嵌入式管理單元](../core/how-to-use-the-servers-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="862a2-123">For more information, see [How to Use the Servers Snap-in](../core/how-to-use-the-servers-snap-in.md).</span></span>