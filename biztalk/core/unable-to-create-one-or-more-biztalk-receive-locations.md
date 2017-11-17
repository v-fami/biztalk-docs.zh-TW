---
title: "無法建立一或多個 BizTalk 接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b564f87b-34ba-400e-9a71-bd66081fc1b8
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b87f8e4874f2f59f26a58a8c4f40f93e5073207c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-create-one-or-more-biztalk-receive-locations"></a><span data-ttu-id="d5ba5-102">無法建立一或多個 BizTalk 接收位置</span><span class="sxs-lookup"><span data-stu-id="d5ba5-102">Unable to create one or more BizTalk receive locations</span></span>
## <a name="details"></a><span data-ttu-id="d5ba5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d5ba5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d5ba5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d5ba5-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d5ba5-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d5ba5-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="d5ba5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d5ba5-106">Event ID</span></span>|<span data-ttu-id="d5ba5-107">0</span><span class="sxs-lookup"><span data-stu-id="d5ba5-107">0</span></span>|  
|<span data-ttu-id="d5ba5-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="d5ba5-108">Event Source</span></span>|<span data-ttu-id="d5ba5-109">0</span><span class="sxs-lookup"><span data-stu-id="d5ba5-109">0</span></span>|  
|<span data-ttu-id="d5ba5-110">元件</span><span class="sxs-lookup"><span data-stu-id="d5ba5-110">Component</span></span>|<span data-ttu-id="d5ba5-111">0</span><span class="sxs-lookup"><span data-stu-id="d5ba5-111">0</span></span>|  
|<span data-ttu-id="d5ba5-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d5ba5-112">Symbolic Name</span></span>|<span data-ttu-id="d5ba5-113">0</span><span class="sxs-lookup"><span data-stu-id="d5ba5-113">0</span></span>|  
|<span data-ttu-id="d5ba5-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d5ba5-114">Message Text</span></span>|<span data-ttu-id="d5ba5-115">無法建立一或多個 BizTalk 接收位置。</span><span class="sxs-lookup"><span data-stu-id="d5ba5-115">Unable to create one or more BizTalk receive locations.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d5ba5-116">說明</span><span class="sxs-lookup"><span data-stu-id="d5ba5-116">Explanation</span></span>  
 <span data-ttu-id="d5ba5-117">此錯誤表示 BizTalk WCF 發佈精靈無法建立接收位置主控的外掛式的 WCF 配接器。</span><span class="sxs-lookup"><span data-stu-id="d5ba5-117">This error indicates that the BizTalk WCF Publishing Wizard failed to create receive locations hosting an isolated WCF adapter.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d5ba5-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d5ba5-118">User Action</span></span>  
 <span data-ttu-id="d5ba5-119">請確定該 BizTalk 執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="d5ba5-119">Make sure that BizTalk instance is started.</span></span>  
  
 <span data-ttu-id="d5ba5-120">如需有關建立接收位置，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件：</span><span class="sxs-lookup"><span data-stu-id="d5ba5-120">For additional information on creating receive locations, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation:</span></span>  
  
-   [<span data-ttu-id="d5ba5-121">發佈 WCF 服務，利用外掛式 WCF 接收配接器</span><span class="sxs-lookup"><span data-stu-id="d5ba5-121">Publishing WCF Services with the Isolated WCF Receive Adapters</span></span>](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="d5ba5-122">如何設定 Wcf-basichttp 接收位置</span><span class="sxs-lookup"><span data-stu-id="d5ba5-122">How to Configure a WCF-BasicHttp Receive Location</span></span>](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)  
  
-   [<span data-ttu-id="d5ba5-123">如何設定 Wcf-wshttp 接收位置</span><span class="sxs-lookup"><span data-stu-id="d5ba5-123">How to Configure a WCF-WSHttp Receive Location</span></span>](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [<span data-ttu-id="d5ba5-124">如何設定 Wcf-customisolated 接收位置</span><span class="sxs-lookup"><span data-stu-id="d5ba5-124">How to Configure a WCF-CustomIsolated Receive Location</span></span>](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [<span data-ttu-id="d5ba5-125">逐步解說： 使用發佈 WCF 服務 Wcf-basichttp 配接器</span><span class="sxs-lookup"><span data-stu-id="d5ba5-125">Walkthrough: Publishing WCF Services with the WCF-BasicHttp Adapter</span></span>](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)