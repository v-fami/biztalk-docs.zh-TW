---
title: "低權限環境 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abdc45d0-b63a-4b6c-80c4-1f8e87644cd9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d43f363bd96dd8e3109a8ce21b9565fb43e5f9bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="low-privilege-environments"></a><span data-ttu-id="c1a81-102">低權限環境</span><span class="sxs-lookup"><span data-stu-id="c1a81-102">Low-Privilege Environments</span></span>
<span data-ttu-id="c1a81-103">所包含的數個工作流程[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件需要提高權限來執行特定動作。</span><span class="sxs-lookup"><span data-stu-id="c1a81-103">Several workflows that are included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack require elevated permissions to perform certain actions.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c1a81-104">管理組件可讓您在低權限環境中執行基本監視功能。</span><span class="sxs-lookup"><span data-stu-id="c1a81-104"> Management Pack enables you to perform basic monitoring functionalities in a low privilege environment.</span></span> <span data-ttu-id="c1a81-105">有兩個系統管理角色： BizTalk Server 系統管理員和 BizTalk Server 操作員。</span><span class="sxs-lookup"><span data-stu-id="c1a81-105">There are two Administrative Roles: the BizTalk Server Administrator, and the BizTalk Server Operator.</span></span> <span data-ttu-id="c1a81-106">BizTalk Server 系統管理員是具有組態和追蹤資料存取權的高權限角色。</span><span class="sxs-lookup"><span data-stu-id="c1a81-106">The BizTalk Server Administrator is a high privilege role with access to configuration and tracking data.</span></span> <span data-ttu-id="c1a81-107">BizTalk Server 系統管理員可以執行所有的主要系統管理工作，這類登錄與啟動成品。</span><span class="sxs-lookup"><span data-stu-id="c1a81-107">The BizTalk Server Administrator can perform all key administrative tasks such enlisting and starting artifacts.</span></span> <span data-ttu-id="c1a81-108">BizTalk Server 操作員則是低權限角色，僅具有用來監控和疑難排解動作的存取權。</span><span class="sxs-lookup"><span data-stu-id="c1a81-108">The BizTalk Server Operator is a low privilege role with access only to monitoring and troubleshooting actions.</span></span> <span data-ttu-id="c1a81-109">如需詳細資訊，請參閱[最低安全性使用者權限](http://technet.microsoft.com/library/aa559845\(BTS.80\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="c1a81-109">For more information, see [Minimum Security User Rights](http://technet.microsoft.com/library/aa559845\(BTS.80\).aspx).</span></span>  
  
 <span data-ttu-id="c1a81-110">使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件：</span><span class="sxs-lookup"><span data-stu-id="c1a81-110">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack:</span></span>  
  
-   <span data-ttu-id="c1a81-111">BizTalk Server 操作員群組的成員可執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c1a81-111">Members of the BizTalk Server Operators group can do the following:</span></span>  
  
    -   <span data-ttu-id="c1a81-112">監控 BizTalk Server 的錯誤，暫停 messages\instances，檢視設定的查詢。</span><span class="sxs-lookup"><span data-stu-id="c1a81-112">Monitor BizTalk Server for errors, query for suspended messages\instances, view configuration.</span></span>  
  
    -   <span data-ttu-id="c1a81-113">監控 BizTalk Server 安裝和成品。</span><span class="sxs-lookup"><span data-stu-id="c1a81-113">Monitor BizTalk Server installations and artifacts.</span></span>  
  
    -   <span data-ttu-id="c1a81-114">檢視服務狀態及訊息流程。</span><span class="sxs-lookup"><span data-stu-id="c1a81-114">View service state and message flow.</span></span>  
  
    -   <span data-ttu-id="c1a81-115">啟動或停止應用程式和成品，例如協調流程、 傳送埠或傳送埠群組中已登錄狀態。</span><span class="sxs-lookup"><span data-stu-id="c1a81-115">Start or stop applications and artifacts such as orchestrations, send ports or send port groups that are in an enlisted state.</span></span>  
  
    -   <span data-ttu-id="c1a81-116">啟用或停用接收位置。</span><span class="sxs-lookup"><span data-stu-id="c1a81-116">Enable or disable receive locations.</span></span> <span data-ttu-id="c1a81-117">在下一個 60 秒 (預設值) 的快取重新整理間隔之前，變更不會生效。</span><span class="sxs-lookup"><span data-stu-id="c1a81-117">The changes do not take effect until the next cache refresh interval of 60 seconds, which is the default.</span></span> <span data-ttu-id="c1a81-118">快取重新整理間隔視在 BizTalk Server 群組層級設定。</span><span class="sxs-lookup"><span data-stu-id="c1a81-118">The cache refresh interval is set at the BizTalk Server group level.</span></span>  
  
-   <span data-ttu-id="c1a81-119">BizTalk Server 操作員群組的成員無法執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c1a81-119">Members of the BizTalk Server Operators group cannot do the following:</span></span>  
  
    -   <span data-ttu-id="c1a81-120">修改 BizTalk Server 的組態。</span><span class="sxs-lookup"><span data-stu-id="c1a81-120">Modify the configuration for BizTalk Server.</span></span>  
  
    -   <span data-ttu-id="c1a81-121">檢視分類為個人識別資訊 (PII) 的訊息內容屬性或訊息內文。</span><span class="sxs-lookup"><span data-stu-id="c1a81-121">View message context properties classified as Personally Identifiable Information (PII) or message bodies.</span></span>  
  
    -   <span data-ttu-id="c1a81-122">修改訊息路由過程，例如移除或新增新的訂閱到執行中的系統，包括將訊息發佈到 BizTalk Server 執行階段。</span><span class="sxs-lookup"><span data-stu-id="c1a81-122">Modify the course of message routing, such as removing or adding new subscriptions to the running system, including the ability to publish messages into the BizTalk Server runtime.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c1a81-123">若要執行所有管理組件，例如，重新啟動 BTSNTSvc.exe 服務所提供的監視工作，您必須是 BizTalk 伺服器上本機 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="c1a81-123">To perform all monitoring tasks provided by the Management Pack such as restarting BTSNTSvc.exe service, you must be a member of the local Administrators group on the BizTalk Servers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1a81-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="c1a81-124">In this section</span></span>  
  
-   [<span data-ttu-id="c1a81-125">監視</span><span class="sxs-lookup"><span data-stu-id="c1a81-125">Monitoring</span></span>](../technical-guides/monitoring.md)  
  
-   [<span data-ttu-id="c1a81-126">探索</span><span class="sxs-lookup"><span data-stu-id="c1a81-126">Discoveries</span></span>](../technical-guides/discoveries.md)