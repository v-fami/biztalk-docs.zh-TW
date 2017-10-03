---
title: "無法註冊外掛式的接收器位址 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 313b436a-d7c5-4b46-bfe3-bbad0d8efe42
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: edd55360a1638128ed687cf83f2e05bf52ad9dfe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="failed-to-register-isolated-receiver-for-address"></a><span data-ttu-id="10d3d-102">無法註冊外掛式的接收器位址</span><span class="sxs-lookup"><span data-stu-id="10d3d-102">Failed to register isolated receiver for address</span></span>
## <a name="details"></a><span data-ttu-id="10d3d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="10d3d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="10d3d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="10d3d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="10d3d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="10d3d-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="10d3d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="10d3d-106">Event ID</span></span>|<span data-ttu-id="10d3d-107">0</span><span class="sxs-lookup"><span data-stu-id="10d3d-107">0</span></span>|  
|<span data-ttu-id="10d3d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="10d3d-108">Event Source</span></span>|<span data-ttu-id="10d3d-109">0</span><span class="sxs-lookup"><span data-stu-id="10d3d-109">0</span></span>|  
|<span data-ttu-id="10d3d-110">元件</span><span class="sxs-lookup"><span data-stu-id="10d3d-110">Component</span></span>|<span data-ttu-id="10d3d-111">0</span><span class="sxs-lookup"><span data-stu-id="10d3d-111">0</span></span>|  
|<span data-ttu-id="10d3d-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="10d3d-112">Symbolic Name</span></span>|<span data-ttu-id="10d3d-113">0</span><span class="sxs-lookup"><span data-stu-id="10d3d-113">0</span></span>|  
|<span data-ttu-id="10d3d-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="10d3d-114">Message Text</span></span>|<span data-ttu-id="10d3d-115">無法註冊外掛式的接收器位址"{0}"。接收位置不存在或已停用。</span><span class="sxs-lookup"><span data-stu-id="10d3d-115">Failed to register isolated receiver for address "{0}"; receive location does not exist or is disabled.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="10d3d-116">說明</span><span class="sxs-lookup"><span data-stu-id="10d3d-116">Explanation</span></span>  
 <span data-ttu-id="10d3d-117">此錯誤表示已發行的外掛式的 WCF 接收位置找不到對應的接收位置。</span><span class="sxs-lookup"><span data-stu-id="10d3d-117">This error indicates that a published isolated WCF receive location could not find the corresponding receive location.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="10d3d-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="10d3d-118">User Action</span></span>  
 <span data-ttu-id="10d3d-119">若要解決這個錯誤，執行下列動作： 在 BizTalk 管理主控台中，確定該接收位置屬性所指定 receiveLocationName Web.config 檔案中 BizTalk WCF 服務發佈精靈產生存在，而且是已啟動。</span><span class="sxs-lookup"><span data-stu-id="10d3d-119">To resolve this error, do the following: In the BizTalk Administration console, make sure that the receive location specified by the receiveLocationName attribute in the Web.config file that the BizTalk WCF Services Publishing Wizard generated exists and is started.</span></span>  
  
 <span data-ttu-id="10d3d-120">如需有關建立接收位置，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="10d3d-120">For additional information on creating receive locations, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="10d3d-121">發佈 WCF 服務，利用外掛式 WCF 接收配接器</span><span class="sxs-lookup"><span data-stu-id="10d3d-121">Publishing WCF Services with the Isolated WCF Receive Adapters</span></span>](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="10d3d-122">如何設定 Wcf-basichttp 接收位置</span><span class="sxs-lookup"><span data-stu-id="10d3d-122">How to Configure a WCF-BasicHttp Receive Location</span></span>](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)  
  
-   [<span data-ttu-id="10d3d-123">如何設定 Wcf-wshttp 接收位置</span><span class="sxs-lookup"><span data-stu-id="10d3d-123">How to Configure a WCF-WSHttp Receive Location</span></span>](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [<span data-ttu-id="10d3d-124">如何設定 Wcf-customisolated 接收位置</span><span class="sxs-lookup"><span data-stu-id="10d3d-124">How to Configure a WCF-CustomIsolated Receive Location</span></span>](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [<span data-ttu-id="10d3d-125">逐步解說： 使用發佈 WCF 服務 Wcf-basichttp 配接器</span><span class="sxs-lookup"><span data-stu-id="10d3d-125">Walkthrough: Publishing WCF Services with the WCF-BasicHttp Adapter</span></span>](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)