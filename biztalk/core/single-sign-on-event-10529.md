---
title: 單一登入： 事件 10529 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75ed70e0-8458-4736-883f-a4536f094dc0
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f33c0e475f9b54b5fc0a5d5415736d9717ccdf9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270566"
---
# <a name="single-sign-on-event-10529"></a><span data-ttu-id="e530d-102">單一登入： 事件 10529</span><span class="sxs-lookup"><span data-stu-id="e530d-102">Single Sign-On: Event 10529</span></span>
## <a name="details"></a><span data-ttu-id="e530d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e530d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e530d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e530d-104">Product Name</span></span>|<span data-ttu-id="e530d-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="e530d-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="e530d-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="e530d-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="e530d-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e530d-107">Event ID</span></span>|<span data-ttu-id="e530d-108">10529</span><span class="sxs-lookup"><span data-stu-id="e530d-108">10529</span></span>|  
|<span data-ttu-id="e530d-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="e530d-109">Event Source</span></span>|<span data-ttu-id="e530d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="e530d-110">ENTSSO</span></span>|  
|<span data-ttu-id="e530d-111">元件</span><span class="sxs-lookup"><span data-stu-id="e530d-111">Component</span></span>|<span data-ttu-id="e530d-112">N\A</span><span class="sxs-lookup"><span data-stu-id="e530d-112">N\A</span></span>|  
|<span data-ttu-id="e530d-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e530d-113">Symbolic Name</span></span>|<span data-ttu-id="e530d-114">SSO_INFO_GOT_CURRENT_SECRET</span><span class="sxs-lookup"><span data-stu-id="e530d-114">SSO_INFO_GOT_CURRENT_SECRET</span></span>|  
|<span data-ttu-id="e530d-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e530d-115">Message Text</span></span>|<span data-ttu-id="e530d-116">從主要密碼 server.%r 取得目前的密碼</span><span class="sxs-lookup"><span data-stu-id="e530d-116">Got the current secret from the master secret server.%r</span></span><br /><br /> <span data-ttu-id="e530d-117">密碼伺服器名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="e530d-117">Secret Server Name: %1%r</span></span><br /><br /> <span data-ttu-id="e530d-118">MSID: %2</span><span class="sxs-lookup"><span data-stu-id="e530d-118">MSID: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e530d-119">說明</span><span class="sxs-lookup"><span data-stu-id="e530d-119">Explanation</span></span>  
 <span data-ttu-id="e530d-120">這個資訊事件表示 SSO 具有向主要密碼伺服器要求的主要密碼。</span><span class="sxs-lookup"><span data-stu-id="e530d-120">This Information event indicates that SSO has the requested master secret from the master secret server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e530d-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e530d-121">User Action</span></span>  
  
-   <span data-ttu-id="e530d-122">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="e530d-122">No user action is necessary.</span></span>  
  
 <span data-ttu-id="e530d-123">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="e530d-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="e530d-124">如何產生主要密碼</span><span class="sxs-lookup"><span data-stu-id="e530d-124">How to Generate the Master Secret</span></span>](../core/how-to-generate-the-master-secret.md)  
  
-   [<span data-ttu-id="e530d-125">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="e530d-125">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)