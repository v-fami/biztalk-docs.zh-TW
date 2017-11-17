---
title: "排程器無法排程批次 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ac6d79c-c995-4c95-a4da-ee2f50b9a13a
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bef1df18d88f8497fde440383d63bc64eefdd69a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scheduler-was-unable-to-schedule-the-batch"></a><span data-ttu-id="d9cc5-102">排程器無法排程批次</span><span class="sxs-lookup"><span data-stu-id="d9cc5-102">Scheduler was unable to schedule the batch</span></span>
## <a name="details"></a><span data-ttu-id="d9cc5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d9cc5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d9cc5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d9cc5-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d9cc5-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d9cc5-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d9cc5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d9cc5-106">Event ID</span></span>|-|  
|<span data-ttu-id="d9cc5-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d9cc5-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d9cc5-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d9cc5-108"> EDI</span></span>|  
|<span data-ttu-id="d9cc5-109">元件</span><span class="sxs-lookup"><span data-stu-id="d9cc5-109">Component</span></span>|<span data-ttu-id="d9cc5-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="d9cc5-110">Batching Engine</span></span>|  
|<span data-ttu-id="d9cc5-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d9cc5-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="d9cc5-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d9cc5-112">Message Text</span></span>|<span data-ttu-id="d9cc5-113">排程器無法排程批次</span><span class="sxs-lookup"><span data-stu-id="d9cc5-113">Scheduler was unable to schedule the batch</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d9cc5-114">說明</span><span class="sxs-lookup"><span data-stu-id="d9cc5-114">Explanation</span></span>  
 <span data-ttu-id="d9cc5-115">此錯誤表示排程器無法判斷下一個出現的批次釋放。</span><span class="sxs-lookup"><span data-stu-id="d9cc5-115">This error indicates the scheduler could not determine the next occurrence of a batch release.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d9cc5-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d9cc5-116">User Action</span></span>  
 <span data-ttu-id="d9cc5-117">若要解決這個錯誤，請確定排定的批次釋放是有效的：</span><span class="sxs-lookup"><span data-stu-id="d9cc5-117">To resolve this error, make sure the batch release schedule is valid:</span></span>  
  
1.  <span data-ttu-id="d9cc5-118">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="d9cc5-118">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="d9cc5-119">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="d9cc5-119">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and click **Parties**.</span></span>  
  
3.  <span data-ttu-id="d9cc5-120">以滑鼠右鍵按一下正確的合作對象。</span><span class="sxs-lookup"><span data-stu-id="d9cc5-120">Right-click the correct party.</span></span>  
  
4.  <span data-ttu-id="d9cc5-121">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="d9cc5-121">Click **Properties**.</span></span>  
  
5.  <span data-ttu-id="d9cc5-122">在 [*合作對象名稱*]**合作對象屬性**] 對話方塊的左窗格中，按一下 [**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="d9cc5-122">In the [*party name*] **Party Properties** dialog box, in the left pane, click **Send Ports**.</span></span>  
  
6.  <span data-ttu-id="d9cc5-123">輸入傳送埠名稱，在**傳送埠**清單。</span><span class="sxs-lookup"><span data-stu-id="d9cc5-123">Enter the Send port name in the **Send Ports** list.</span></span>  
  
7.  <span data-ttu-id="d9cc5-124">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d9cc5-124">Click **OK**.</span></span>