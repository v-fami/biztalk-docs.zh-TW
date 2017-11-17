---
title: "如何登錄協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [orchestrations], enlisting
- orchestrations, enlisting
- enlisting, orchestrations
ms.assetid: b21a398b-8c9a-42ae-aac0-de35dbfd8176
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f58cb697e270052f8f42229997b1125e808816b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enlist-an-orchestration"></a><span data-ttu-id="5dae8-102">如何登錄協調流程。</span><span class="sxs-lookup"><span data-stu-id="5dae8-102">How to Enlist an Orchestration</span></span>
<span data-ttu-id="5dae8-103">這個主題說明如何使用 BizTalk Server 管理主控台，將協調流程登錄到主控件中。</span><span class="sxs-lookup"><span data-stu-id="5dae8-103">This topic describes how to use the BizTalk Server Administration console to enlist an orchestration into a host.</span></span> <span data-ttu-id="5dae8-104">您必須登錄協調流程，才能將它啟動。</span><span class="sxs-lookup"><span data-stu-id="5dae8-104">The orchestration must be enlisted before you can start it.</span></span>  
  
 <span data-ttu-id="5dae8-105">登錄協調流程時，請記住下列要點：</span><span class="sxs-lookup"><span data-stu-id="5dae8-105">When enlisting an orchestration, bear in mind the following points:</span></span>  
  
-   <span data-ttu-id="5dae8-106">**協調流程必須繫結，然後您可以將它登錄。**</span><span class="sxs-lookup"><span data-stu-id="5dae8-106">**The orchestration must be bound before you can enlist it.**</span></span> <span data-ttu-id="5dae8-107">如需設定的協調流程繫結的指示，請參閱[如何設定協調流程繫結](../core/how-to-configure-bindings-for-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="5dae8-107">For instructions on configuring bindings for orchestrations, see [How to Configure Bindings for an Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).</span></span>  
  
-   <span data-ttu-id="5dae8-108">**訂用帳戶會自動建立。**</span><span class="sxs-lookup"><span data-stu-id="5dae8-108">**Subscriptions are automatically created.**</span></span> <span data-ttu-id="5dae8-109">協調流程登錄程序會在 MessageBox 資料庫中建立必要的訂閱。</span><span class="sxs-lookup"><span data-stu-id="5dae8-109">The orchestration enlistment process creates the necessary subscriptions in the MessageBox database.</span></span>  
  
-   <span data-ttu-id="5dae8-110">**您必須安裝應用程式。**</span><span class="sxs-lookup"><span data-stu-id="5dae8-110">**You must install the application.**</span></span> <span data-ttu-id="5dae8-111">您必須在所有要執行協調流程的電腦上安裝包含協調流程的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5dae8-111">You must install the application containing the orchestration on all of computers where the orchestration will run.</span></span> <span data-ttu-id="5dae8-112">如需詳細資訊，請參閱[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="5dae8-112">For more information, see [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md).</span></span>  
  
-   <span data-ttu-id="5dae8-113">**呼叫的協調流程必須繫結呼叫的協調流程相同的主控件。**</span><span class="sxs-lookup"><span data-stu-id="5dae8-113">**A calling orchestration must be bound to the same host as the called orchestration.**</span></span> <span data-ttu-id="5dae8-114">任何由其他協調流程所呼叫的協調流程必須繫結至與發出呼叫的協調流程相同的主控件。</span><span class="sxs-lookup"><span data-stu-id="5dae8-114">Any orchestration that is called by another orchestration must be bound to the same host as the calling orchestration.</span></span>  
  
-   <span data-ttu-id="5dae8-115">**您也應該登錄依存的協調流程。**</span><span class="sxs-lookup"><span data-stu-id="5dae8-115">**You should also enlist dependent orchestrations.**</span></span> <span data-ttu-id="5dae8-116">如果您登錄協調流程，但沒有登錄任何依存的協調流程，則依存的協調流程將不會有任何訂閱。</span><span class="sxs-lookup"><span data-stu-id="5dae8-116">If you enlist an orchestration but do not enlist any dependent orchestrations, the dependent orchestrations will not have any subscriptions.</span></span> <span data-ttu-id="5dae8-117">沒有訂閱的依存協調流程可能會因為沒有符合訊息的訂閱而捨棄或擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="5dae8-117">A dependent orchestration without subscriptions may drop or suspend messages because there is no subscription for the messages to match.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5dae8-118">應用程式開發人員可以使用此主題中的程序，在開發程序中登錄協調流程以測試其功能。</span><span class="sxs-lookup"><span data-stu-id="5dae8-118">The application developer can enlist an orchestration to test its functionality during the development process  by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5dae8-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="5dae8-119">Prerequisites</span></span>  
 <span data-ttu-id="5dae8-120">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="5dae8-120">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="5dae8-121">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="5dae8-121">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-enlist-an-orchestration"></a><span data-ttu-id="5dae8-122">登錄協調流程</span><span class="sxs-lookup"><span data-stu-id="5dae8-122">To enlist an orchestration</span></span>  
  
1.  <span data-ttu-id="5dae8-123">按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="5dae8-123">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="5dae8-124">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含您想要登錄的協調流程的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5dae8-124">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration that you want to enlist.</span></span>  
  
3.  <span data-ttu-id="5dae8-125">按一下**協調流程**，以滑鼠右鍵按一下協調流程登錄，然後按一下 **登錄**。</span><span class="sxs-lookup"><span data-stu-id="5dae8-125">Click **Orchestrations**, right-click the orchestration to enlist, and then click **Enlist**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5dae8-126">若要一次登錄多個協調流程、 按住 shift 鍵並選取要登錄的每個協調流程，以滑鼠右鍵按一下協調流程，然後**登錄**。</span><span class="sxs-lookup"><span data-stu-id="5dae8-126">To enlist multiple orchestrations at once, hold down the shift key and select each orchestration to enlist, right-click an orchestration, and then click **Enlist**.</span></span>  
  
     <span data-ttu-id="5dae8-127">如此便會登錄協調流程，並建立適當的訂閱。</span><span class="sxs-lookup"><span data-stu-id="5dae8-127">The orchestration is enlisted and the appropriate subscriptions are created.</span></span> <span data-ttu-id="5dae8-128">協調流程目前是處於停止狀態。</span><span class="sxs-lookup"><span data-stu-id="5dae8-128">The orchestration is in the stopped state.</span></span> <span data-ttu-id="5dae8-129">若要開始處理內送訊息，您必須明確地啟動協調流程上按一下滑鼠右鍵按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="5dae8-129">To start processing incoming messages, you must explicitly start the orchestration by right-clicking it and clicking **Start**.</span></span> <span data-ttu-id="5dae8-130">如需詳細資訊，請參閱[如何啟動協調流程](../core/how-to-start-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="5dae8-130">For more information, see [How to Start an Orchestration](../core/how-to-start-an-orchestration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dae8-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5dae8-131">See Also</span></span>  
 <span data-ttu-id="5dae8-132">[管理協調流程](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="5dae8-132">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 [<span data-ttu-id="5dae8-133">如何取消登錄協調流程</span><span class="sxs-lookup"><span data-stu-id="5dae8-133">How to Unenlist an Orchestration</span></span>](../core/how-to-unenlist-an-orchestration.md)