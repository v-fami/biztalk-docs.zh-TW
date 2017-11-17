---
title: "設定協調流程的繫結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9724a3a0-c217-4f98-b6d9-21f788ce50ba
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: adb695f9636327107887397372d5fc2dda74e4eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-bindings-for-an-orchestration"></a><span data-ttu-id="adcaf-102">如何設定協調流程的繫結</span><span class="sxs-lookup"><span data-stu-id="adcaf-102">How to Configure Bindings for an Orchestration</span></span>

## <a name="overview"></a><span data-ttu-id="adcaf-103">概觀</span><span class="sxs-lookup"><span data-stu-id="adcaf-103">Overview</span></span>
<span data-ttu-id="adcaf-104">本主題描述如何使用 BizTalk Server 管理主控台來設定協調流程的繫結。</span><span class="sxs-lookup"><span data-stu-id="adcaf-104">This topic describes how to use the BizTalk Server Administration console to configure bindings for an orchestration.</span></span> <span data-ttu-id="adcaf-105">此項作業包括將協調流程所定義的邏輯連接埠繫結至臨時或生產環境中的實體連接埠，以及將協調流程繫結至主控件。</span><span class="sxs-lookup"><span data-stu-id="adcaf-105">This involves binding the logical ports defined for the orchestration to physical ports in the staging or production environment as well as binding the orchestration to a host.</span></span> <span data-ttu-id="adcaf-106">如果已經繫結協調流程，您可以使用此程序來變更繫結。</span><span class="sxs-lookup"><span data-stu-id="adcaf-106">If the orchestration has already been bound, you can change the bindings by using this procedure.</span></span>  
  
 <span data-ttu-id="adcaf-107">在設定繫結之後，您可以登錄協調流程，然後加以啟動，這樣協調流程即可開始處理訊息。</span><span class="sxs-lookup"><span data-stu-id="adcaf-107">After configuring bindings, you can enlist the orchestration and then start it so that it begins processing messages.</span></span> <span data-ttu-id="adcaf-108">如需執行這些工作的指示，請參閱[如何登錄協調流程](../core/how-to-enlist-an-orchestration.md)和[如何啟動協調流程](../core/how-to-start-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="adcaf-108">For instructions on performing these tasks, see [How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md) and [How to Start an Orchestration](../core/how-to-start-an-orchestration.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adcaf-109">應用程式開發人員可以使用此主題中的程序，在開發程序中為協調流程設定繫結以測試其功能。</span><span class="sxs-lookup"><span data-stu-id="adcaf-109">The application developer can configure bindings for an orchestration to test its functionality during the development process either by using the procedure in this topic.</span></span> <span data-ttu-id="adcaf-110">您也可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="adcaf-110">You can also use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="adcaf-111">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="adcaf-111">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="adcaf-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="adcaf-112">Prerequisites</span></span>  
 <span data-ttu-id="adcaf-113">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="adcaf-113">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="adcaf-114">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="adcaf-114">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="configure-bindings-for-an-orchestration"></a><span data-ttu-id="adcaf-115">設定協調流程的繫結</span><span class="sxs-lookup"><span data-stu-id="adcaf-115">Configure bindings for an orchestration</span></span>  
  
1.  <span data-ttu-id="adcaf-116">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="adcaf-116">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="adcaf-117">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含您想要在協調的流程的應用程式設定繫結</span><span class="sxs-lookup"><span data-stu-id="adcaf-117">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration for which you want to configure bindings</span></span>  
  
3.  <span data-ttu-id="adcaf-118">按一下**協調流程**，以滑鼠右鍵按一下您要設定繫結，然後按一下 協調的流程**屬性**。</span><span class="sxs-lookup"><span data-stu-id="adcaf-118">Click **Orchestrations**, right-click the orchestration for which you want to configure bindings, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="adcaf-119">按一下**繫結** 索引標籤，並從**主機**清單中，選取要登錄協調流程的主控件。</span><span class="sxs-lookup"><span data-stu-id="adcaf-119">Click the **Bindings** tab, and from the **Host** list, select the host on which to enlist an orchestration.</span></span>  
  
5.  <span data-ttu-id="adcaf-120">從下拉式清單中**接收埠**每個輸入邏輯連接埠旁邊的資料行，選取您要繫結的邏輯連接埠的接收埠。</span><span class="sxs-lookup"><span data-stu-id="adcaf-120">From the drop-down lists in the **Receive Ports** column, next to each inbound logical port, select the receive port to which you want to bind the logical port.</span></span>  
  
6.  <span data-ttu-id="adcaf-121">從下拉式清單中**傳送埠/傳送埠群組**每個輸入邏輯連接埠旁邊的資料行，選取您想要繫結的邏輯連接埠，然後按一下傳送埠**確定**。</span><span class="sxs-lookup"><span data-stu-id="adcaf-121">From the drop-down list in the **Send Ports/Send Port Groups** column, next to each inbound logical port, select the send port to which you want to bind the logical port, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adcaf-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adcaf-122">See Also</span></span>  
 <span data-ttu-id="adcaf-123">[管理協調流程](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="adcaf-123">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 <span data-ttu-id="adcaf-124">[如何解除繫結協調流程](../core/how-to-unbind-an-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="adcaf-124">[How to Unbind an Orchestration](../core/how-to-unbind-an-orchestration.md) </span></span>  
 [<span data-ttu-id="adcaf-125">部署和管理 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="adcaf-125">Deploying and Managing BizTalk Applications</span></span>](../core/deploying-and-managing-biztalk-applications.md)