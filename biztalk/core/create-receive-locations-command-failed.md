---
title: "建立接收位置命令失敗 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f73ff211-af7f-40be-ad7e-7bde7bf75a2d
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a6ad1c7992bb696eb05223e9830a7114d8a0fd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="create-receive-locations-command-failed"></a><span data-ttu-id="7d3d9-102">建立接收位置命令失敗</span><span class="sxs-lookup"><span data-stu-id="7d3d9-102">Create receive locations command failed</span></span>
## <a name="details"></a><span data-ttu-id="7d3d9-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7d3d9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d3d9-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7d3d9-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7d3d9-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="7d3d9-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="7d3d9-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7d3d9-106">Event ID</span></span>|<span data-ttu-id="7d3d9-107">0</span><span class="sxs-lookup"><span data-stu-id="7d3d9-107">0</span></span>|  
|<span data-ttu-id="7d3d9-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="7d3d9-108">Event Source</span></span>|<span data-ttu-id="7d3d9-109">0</span><span class="sxs-lookup"><span data-stu-id="7d3d9-109">0</span></span>|  
|<span data-ttu-id="7d3d9-110">元件</span><span class="sxs-lookup"><span data-stu-id="7d3d9-110">Component</span></span>|<span data-ttu-id="7d3d9-111">0</span><span class="sxs-lookup"><span data-stu-id="7d3d9-111">0</span></span>|  
|<span data-ttu-id="7d3d9-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7d3d9-112">Symbolic Name</span></span>|<span data-ttu-id="7d3d9-113">0</span><span class="sxs-lookup"><span data-stu-id="7d3d9-113">0</span></span>|  
|<span data-ttu-id="7d3d9-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7d3d9-114">Message Text</span></span>|<span data-ttu-id="7d3d9-115">建立接收位置命令失敗： 檔案名稱 = {0} 引數 = \ {1 \} ExitCode = \ {2 \}</span><span class="sxs-lookup"><span data-stu-id="7d3d9-115">Create receive locations command failed: FileName={0} Arguments={1} ExitCode={2}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7d3d9-116">說明</span><span class="sxs-lookup"><span data-stu-id="7d3d9-116">Explanation</span></span>  
 <span data-ttu-id="7d3d9-117">發佈精靈無法建立接收位置。</span><span class="sxs-lookup"><span data-stu-id="7d3d9-117">The publishing wizard failed to create a receive location.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7d3d9-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7d3d9-118">User Action</span></span>  
 <span data-ttu-id="7d3d9-119">若要解決這個錯誤，執行下列動作： 在 BizTalk 管理主控台中，確定該接收位置屬性所指定 receiveLocationName Web.config 檔案中 BizTalk WCF 發佈精靈產生存在且已啟動。</span><span class="sxs-lookup"><span data-stu-id="7d3d9-119">To resolve this error, do the following: In the BizTalk Administration console, make sure that the receive location specified by the receiveLocationName attribute in the Web.config file that the BizTalk WCF Publishing Wizard generated exists and is started.</span></span>  
  
 <span data-ttu-id="7d3d9-120">如需有關建立接收位置，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="7d3d9-120">For additional information on creating receive locations, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="7d3d9-121">發佈 WCF 服務，利用外掛式 WCF 接收配接器</span><span class="sxs-lookup"><span data-stu-id="7d3d9-121">Publishing WCF Services with the Isolated WCF Receive Adapters</span></span>](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="7d3d9-122">如何設定 Wcf-basichttp 接收位置</span><span class="sxs-lookup"><span data-stu-id="7d3d9-122">How to Configure a WCF-BasicHttp Receive Location</span></span>](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)  
  
-   [<span data-ttu-id="7d3d9-123">如何設定 Wcf-wshttp 接收位置</span><span class="sxs-lookup"><span data-stu-id="7d3d9-123">How to Configure a WCF-WSHttp Receive Location</span></span>](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [<span data-ttu-id="7d3d9-124">如何設定 Wcf-customisolated 接收位置</span><span class="sxs-lookup"><span data-stu-id="7d3d9-124">How to Configure a WCF-CustomIsolated Receive Location</span></span>](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [<span data-ttu-id="7d3d9-125">逐步解說： 使用發佈 WCF 服務 Wcf-basichttp 配接器</span><span class="sxs-lookup"><span data-stu-id="7d3d9-125">Walkthrough: Publishing WCF Services with the WCF-BasicHttp Adapter</span></span>](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)