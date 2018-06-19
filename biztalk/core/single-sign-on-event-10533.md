---
title: 單一登入： 事件 10533 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31abd828-5f10-43f7-b99e-f3195250130c
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 661c2eb91e0b8886f200319e9595f9d25c7023f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270878"
---
# <a name="single-sign-on-event-10533"></a><span data-ttu-id="7909d-102">單一登入： 事件 10533</span><span class="sxs-lookup"><span data-stu-id="7909d-102">Single Sign-On: Event 10533</span></span>
## <a name="details"></a><span data-ttu-id="7909d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7909d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7909d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7909d-104">Product Name</span></span>|<span data-ttu-id="7909d-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="7909d-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="7909d-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="7909d-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="7909d-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7909d-107">Event ID</span></span>|<span data-ttu-id="7909d-108">10533</span><span class="sxs-lookup"><span data-stu-id="7909d-108">10533</span></span>|  
|<span data-ttu-id="7909d-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="7909d-109">Event Source</span></span>|<span data-ttu-id="7909d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="7909d-110">ENTSSO</span></span>|  
|<span data-ttu-id="7909d-111">元件</span><span class="sxs-lookup"><span data-stu-id="7909d-111">Component</span></span>|<span data-ttu-id="7909d-112">N\A</span><span class="sxs-lookup"><span data-stu-id="7909d-112">N\A</span></span>|  
|<span data-ttu-id="7909d-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7909d-113">Symbolic Name</span></span>|<span data-ttu-id="7909d-114">SSO_INFO_GOT_CURRENT_SECRET</span><span class="sxs-lookup"><span data-stu-id="7909d-114">SSO_INFO_GOT_CURRENT_SECRET</span></span>|  
|<span data-ttu-id="7909d-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7909d-115">Message Text</span></span>|<span data-ttu-id="7909d-116">從主要密碼 server.%r 取得目前的密碼</span><span class="sxs-lookup"><span data-stu-id="7909d-116">Got the current secret from the master secret server.%r</span></span><br /><br /> <span data-ttu-id="7909d-117">密碼伺服器名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="7909d-117">Secret Server Name: %1%r</span></span><br /><br /> <span data-ttu-id="7909d-118">MSID: %2</span><span class="sxs-lookup"><span data-stu-id="7909d-118">MSID: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7909d-119">說明</span><span class="sxs-lookup"><span data-stu-id="7909d-119">Explanation</span></span>  
 <span data-ttu-id="7909d-120">這個資訊事件表示 SSO 具有目前的主要密碼。</span><span class="sxs-lookup"><span data-stu-id="7909d-120">This Information event indicates that SSO has the current master secret.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7909d-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7909d-121">User Action</span></span>  
  
-   <span data-ttu-id="7909d-122">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="7909d-122">No user action is necessary.</span></span>  
  
 <span data-ttu-id="7909d-123">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="7909d-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="7909d-124">如何產生主要密碼</span><span class="sxs-lookup"><span data-stu-id="7909d-124">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  
  
-   [<span data-ttu-id="7909d-125">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="7909d-125">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)