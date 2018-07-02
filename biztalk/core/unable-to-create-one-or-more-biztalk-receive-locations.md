---
title: 無法建立一或多個 BizTalk 接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b564f87b-34ba-400e-9a71-bd66081fc1b8
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0dfc81876cba51b4dad03a01c2feb935b4fc959
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986399"
---
# <a name="unable-to-create-one-or-more-biztalk-receive-locations"></a><span data-ttu-id="f6916-102">無法建立一或多個 BizTalk 接收位置</span><span class="sxs-lookup"><span data-stu-id="f6916-102">Unable to create one or more BizTalk receive locations</span></span>
## <a name="details"></a><span data-ttu-id="f6916-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f6916-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="f6916-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f6916-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="f6916-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f6916-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="f6916-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f6916-106">Event ID</span></span>     |                                         <span data-ttu-id="f6916-107">0</span><span class="sxs-lookup"><span data-stu-id="f6916-107">0</span></span>                                          |
|  <span data-ttu-id="f6916-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="f6916-108">Event Source</span></span>   |                                         <span data-ttu-id="f6916-109">0</span><span class="sxs-lookup"><span data-stu-id="f6916-109">0</span></span>                                          |
|    <span data-ttu-id="f6916-110">元件</span><span class="sxs-lookup"><span data-stu-id="f6916-110">Component</span></span>    |                                         <span data-ttu-id="f6916-111">0</span><span class="sxs-lookup"><span data-stu-id="f6916-111">0</span></span>                                          |
|  <span data-ttu-id="f6916-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f6916-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="f6916-113">0</span><span class="sxs-lookup"><span data-stu-id="f6916-113">0</span></span>                                          |
|  <span data-ttu-id="f6916-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f6916-114">Message Text</span></span>   |              <span data-ttu-id="f6916-115">無法建立一或多個 BizTalk 接收位置。</span><span class="sxs-lookup"><span data-stu-id="f6916-115">Unable to create one or more BizTalk receive locations.</span></span>               |
  
## <a name="explanation"></a><span data-ttu-id="f6916-116">說明</span><span class="sxs-lookup"><span data-stu-id="f6916-116">Explanation</span></span>  
 <span data-ttu-id="f6916-117">此錯誤表示 BizTalk WCF 發佈精靈 無法建立接收位置裝載的外掛式的 WCF 配接器。</span><span class="sxs-lookup"><span data-stu-id="f6916-117">This error indicates that the BizTalk WCF Publishing Wizard failed to create receive locations hosting an isolated WCF adapter.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f6916-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f6916-118">User Action</span></span>  
 <span data-ttu-id="f6916-119">請確定該 BizTalk 執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="f6916-119">Make sure that BizTalk instance is started.</span></span>  
  
 <span data-ttu-id="f6916-120">如需有關建立接收位置，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件：</span><span class="sxs-lookup"><span data-stu-id="f6916-120">For additional information on creating receive locations, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation:</span></span>  
  
-   [<span data-ttu-id="f6916-121">利用外掛式 WCF 接收配接器發佈 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="f6916-121">Publishing WCF Services with the Isolated WCF Receive Adapters</span></span>](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="f6916-122">如何設定 Wcf-basichttp 接收位置</span><span class="sxs-lookup"><span data-stu-id="f6916-122">How to Configure a WCF-BasicHttp Receive Location</span></span>](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)  
  
-   [<span data-ttu-id="f6916-123">如何設定 Wcf-wshttp 接收位置</span><span class="sxs-lookup"><span data-stu-id="f6916-123">How to Configure a WCF-WSHttp Receive Location</span></span>](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [<span data-ttu-id="f6916-124">如何設定 Wcf-customisolated 接收位置</span><span class="sxs-lookup"><span data-stu-id="f6916-124">How to Configure a WCF-CustomIsolated Receive Location</span></span>](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [<span data-ttu-id="f6916-125">逐步解說：使用 WCF-BasicHttp 配接器發佈 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="f6916-125">Walkthrough: Publishing WCF Services with the WCF-BasicHttp Adapter</span></span>](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)