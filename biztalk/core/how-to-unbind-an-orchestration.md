---
title: "解除繫結協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a7c421d-e0cb-4b23-b472-e501056d6329
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce49c3e74846fac5943bda522d11218410f428ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unbind-an-orchestration"></a><span data-ttu-id="db3ae-102">解除繫結協調流程</span><span class="sxs-lookup"><span data-stu-id="db3ae-102">Unbind an Orchestration</span></span>

## <a name="overview"></a><span data-ttu-id="db3ae-103">概觀</span><span class="sxs-lookup"><span data-stu-id="db3ae-103">Overview</span></span>
<span data-ttu-id="db3ae-104">本主題描述如何使用 BizTalk Server 管理主控台從協調流程移除接收埠、傳送埠或主控件繫結。</span><span class="sxs-lookup"><span data-stu-id="db3ae-104">This topic describes how to use the BizTalk Server Administration console to remove receive port, send port, or host bindings from an orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db3ae-105">應用程式開發人員可以使用本主題中的程序，移除協調流程的繫結。</span><span class="sxs-lookup"><span data-stu-id="db3ae-105">The application developer can remove bindings for an orchestration  by using the procedure in this topic.</span></span> <span data-ttu-id="db3ae-106">您也可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="db3ae-106">You can also use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="db3ae-107">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="db3ae-107">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="db3ae-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="db3ae-108">Prerequisites</span></span>  
 <span data-ttu-id="db3ae-109">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="db3ae-109">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="db3ae-110">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="db3ae-110">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="remove-bindings-from-an-orchestration"></a><span data-ttu-id="db3ae-111">從協調流程移除繫結</span><span class="sxs-lookup"><span data-stu-id="db3ae-111">Remove bindings from an orchestration</span></span>  
  
1.  <span data-ttu-id="db3ae-112">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="db3ae-112">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="db3ae-113">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含您要移除的協調流程的應用程式繫結</span><span class="sxs-lookup"><span data-stu-id="db3ae-113">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration from which you want to remove bindings</span></span>  
  
3.  <span data-ttu-id="db3ae-114">按一下**協調流程**，以滑鼠右鍵按一下協調流程，按一下**屬性**，然後按一下 **繫結**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="db3ae-114">Click **Orchestrations**, right-click the orchestration, click **Properties**, and then click **Bindings** in the left pane.</span></span>  
  
4.  <span data-ttu-id="db3ae-115">若要移除的主機繫結，**主機**清單中，選取**\<無 >**。</span><span class="sxs-lookup"><span data-stu-id="db3ae-115">To remove the host bindings, from the **Hosts** list, select **\<None>**.</span></span>  
  
5.  <span data-ttu-id="db3ae-116">若要移除接收埠繫結，下方的下拉式清單**接收埠**，按一下  **\<無 >**。</span><span class="sxs-lookup"><span data-stu-id="db3ae-116">To remove receive port bindings, from the drop-down list under **Receive Ports**, click **\<None>**.</span></span>  
  
6.  <span data-ttu-id="db3ae-117">若要從底下的下拉式清單中移除傳送埠繫結，**傳送埠/傳送埠群組**，按一下  **\<無 >**。</span><span class="sxs-lookup"><span data-stu-id="db3ae-117">To remove send port bindings, from the drop-down list under **Send Ports/Send Port Groups**, click **\<None>**.</span></span>  
  
7.  <span data-ttu-id="db3ae-118">完成移除繫結，請按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="db3ae-118">When finished removing bindings, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db3ae-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db3ae-119">See Also</span></span>  
 <span data-ttu-id="db3ae-120">[管理協調流程](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="db3ae-120">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 <span data-ttu-id="db3ae-121">[如何設定協調流程的繫結](../core/how-to-configure-bindings-for-an-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="db3ae-121">[How to Configure Bindings for an Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md) </span></span>  
 [<span data-ttu-id="db3ae-122">部署和管理 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="db3ae-122">Deploying and Managing BizTalk Applications</span></span>](../core/deploying-and-managing-biztalk-applications.md)