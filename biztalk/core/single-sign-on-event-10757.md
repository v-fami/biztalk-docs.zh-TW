---
title: "單一登入： 事件 10757 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24765a25-560b-4391-9839-a325894c679f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5887694e8fd307c0738fc7596c52354925bfbc7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10757"></a><span data-ttu-id="a5533-102">單一登入： 事件 10757</span><span class="sxs-lookup"><span data-stu-id="a5533-102">Single Sign-On: Event 10757</span></span>
## <a name="details"></a><span data-ttu-id="a5533-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a5533-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5533-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a5533-104">Product Name</span></span>|<span data-ttu-id="a5533-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a5533-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a5533-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="a5533-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a5533-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a5533-107">Event ID</span></span>|<span data-ttu-id="a5533-108">10757</span><span class="sxs-lookup"><span data-stu-id="a5533-108">10757</span></span>|  
|<span data-ttu-id="a5533-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="a5533-109">Event Source</span></span>|<span data-ttu-id="a5533-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a5533-110">ENTSSO</span></span>|  
|<span data-ttu-id="a5533-111">元件</span><span class="sxs-lookup"><span data-stu-id="a5533-111">Component</span></span>|<span data-ttu-id="a5533-112">不適用</span><span class="sxs-lookup"><span data-stu-id="a5533-112">N/A</span></span>|  
|<span data-ttu-id="a5533-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a5533-113">Symbolic Name</span></span>|<span data-ttu-id="a5533-114">ENTSSO_E_NO_MAPPING</span><span class="sxs-lookup"><span data-stu-id="a5533-114">ENTSSO_E_NO_MAPPING</span></span>|  
|<span data-ttu-id="a5533-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a5533-115">Message Text</span></span>|<span data-ttu-id="a5533-116">對應不存在。</span><span class="sxs-lookup"><span data-stu-id="a5533-116">The mapping does not exist.</span></span> <span data-ttu-id="a5533-117">針對組態存放區應用程式，尚未設定組態資訊。</span><span class="sxs-lookup"><span data-stu-id="a5533-117">For Config Store applications, the config info has not been set.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a5533-118">說明</span><span class="sxs-lookup"><span data-stu-id="a5533-118">Explanation</span></span>  
 <span data-ttu-id="a5533-119">如果這是個人或群組類型應用程式，然後對應不存在。</span><span class="sxs-lookup"><span data-stu-id="a5533-119">If this is an Individual or Group type application, then the mapping does not exist.</span></span>  
  
 <span data-ttu-id="a5533-120">如果這是組態存放區應用程式，然後將組態資料尚未設定。</span><span class="sxs-lookup"><span data-stu-id="a5533-120">If this is a Config Store application, then the configuration data has not been set.</span></span> <span data-ttu-id="a5533-121">發生這個問題，已經重新初始化的 SSO 資料庫，但 「 BizTalk 管理 」 資料庫，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="a5533-121">This can occur when the SSO database has been reinitialized but the BizTalk Management database has not, or vice versa.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a5533-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a5533-122">User Action</span></span>  
 <span data-ttu-id="a5533-123">如果這是個人或群組類型應用程式，建立所需的對應。</span><span class="sxs-lookup"><span data-stu-id="a5533-123">If this is an Individual or Group type application, create the desired mapping.</span></span> <span data-ttu-id="a5533-124">如需詳細資訊，請參閱[如何建立使用者對應](../core/how-to-create-user-mappings.md)。</span><span class="sxs-lookup"><span data-stu-id="a5533-124">For more information, see [How to Create User Mappings](../core/how-to-create-user-mappings.md).</span></span>