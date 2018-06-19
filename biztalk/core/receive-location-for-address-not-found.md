---
title: 接收位置位址找不到 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 637f3925-06ff-47b2-99db-f85e829ee318
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1242ffc77976fb2ffcc469752d13a6f6366d7a1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268766"
---
# <a name="receive-location-for-address-not-found"></a><span data-ttu-id="d9e9c-102">接收位置位址找不到</span><span class="sxs-lookup"><span data-stu-id="d9e9c-102">Receive location for address not found</span></span>
## <a name="details"></a><span data-ttu-id="d9e9c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d9e9c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d9e9c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d9e9c-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d9e9c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d9e9c-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="d9e9c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d9e9c-106">Event ID</span></span>|<span data-ttu-id="d9e9c-107">0</span><span class="sxs-lookup"><span data-stu-id="d9e9c-107">0</span></span>|  
|<span data-ttu-id="d9e9c-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="d9e9c-108">Event Source</span></span>|<span data-ttu-id="d9e9c-109">0</span><span class="sxs-lookup"><span data-stu-id="d9e9c-109">0</span></span>|  
|<span data-ttu-id="d9e9c-110">元件</span><span class="sxs-lookup"><span data-stu-id="d9e9c-110">Component</span></span>|<span data-ttu-id="d9e9c-111">0</span><span class="sxs-lookup"><span data-stu-id="d9e9c-111">0</span></span>|  
|<span data-ttu-id="d9e9c-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d9e9c-112">Symbolic Name</span></span>|<span data-ttu-id="d9e9c-113">0</span><span class="sxs-lookup"><span data-stu-id="d9e9c-113">0</span></span>|  
|<span data-ttu-id="d9e9c-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d9e9c-114">Message Text</span></span>|<span data-ttu-id="d9e9c-115">接收位置位址"{0}"找不到。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-115">Receive location for address "{0}" not found.</span></span> <span data-ttu-id="d9e9c-116">(BizTalk 接收位置可能會停用。)</span><span class="sxs-lookup"><span data-stu-id="d9e9c-116">(The BizTalk receive location may be disabled.)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d9e9c-117">說明</span><span class="sxs-lookup"><span data-stu-id="d9e9c-117">Explanation</span></span>  
 <span data-ttu-id="d9e9c-118">此錯誤表示已發行的外掛式的 WCF 接收位置找不到對應的接收位置。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-118">This error indicates that a published isolated WCF receive location could not find the corresponding receive location.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d9e9c-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d9e9c-119">User Action</span></span>  
 <span data-ttu-id="d9e9c-120">若要解決這個錯誤，執行下列動作： 在 BizTalk 管理主控台中，確定該接收位置屬性所指定 receiveLocationName Web.config 檔案中 BizTalk WCF 發佈精靈產生存在且已啟動。</span><span class="sxs-lookup"><span data-stu-id="d9e9c-120">To resolve this error, do the following: In the BizTalk Administration console, make sure that the receive location specified by the receiveLocationName attribute in the Web.config file that the BizTalk WCF Publishing Wizard generated exists and is started.</span></span>  
  
 <span data-ttu-id="d9e9c-121">如需有關建立接收位置，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="d9e9c-121">For additional information on creating receive locations, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="d9e9c-122">發佈 WCF 服務，利用外掛式 WCF 接收配接器</span><span class="sxs-lookup"><span data-stu-id="d9e9c-122">Publishing WCF Services with the Isolated WCF Receive Adapters</span></span>](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="d9e9c-123">如何設定 Wcf-basichttp 接收位置</span><span class="sxs-lookup"><span data-stu-id="d9e9c-123">How to Configure a WCF-BasicHttp Receive Location</span></span>](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)  
  
-   [<span data-ttu-id="d9e9c-124">如何設定 Wcf-wshttp 接收位置</span><span class="sxs-lookup"><span data-stu-id="d9e9c-124">How to Configure a WCF-WSHttp Receive Location</span></span>](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [<span data-ttu-id="d9e9c-125">如何設定 Wcf-customisolated 接收位置</span><span class="sxs-lookup"><span data-stu-id="d9e9c-125">How to Configure a WCF-CustomIsolated Receive Location</span></span>](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [<span data-ttu-id="d9e9c-126">逐步解說： 使用發佈 WCF 服務 Wcf-basichttp 配接器</span><span class="sxs-lookup"><span data-stu-id="d9e9c-126">Walkthrough: Publishing WCF Services with the WCF-BasicHttp Adapter</span></span>](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)