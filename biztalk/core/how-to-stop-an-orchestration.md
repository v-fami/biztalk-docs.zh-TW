---
title: "如何停止協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [orchestrations], stopping
- orchestrations, stopping
ms.assetid: a8009c23-ca83-4d2f-97dd-df660adbc279
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57e51842171c31f2da509e92d9364948aeceb1d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-stop-an-orchestration"></a><span data-ttu-id="7ed48-102">如何停止協調流程</span><span class="sxs-lookup"><span data-stu-id="7ed48-102">How to Stop an Orchestration</span></span>
<span data-ttu-id="7ed48-103">本主題描述如何使用 BizTalk Server 管理主控台來停止協調流程。</span><span class="sxs-lookup"><span data-stu-id="7ed48-103">This topic describes how to use the BizTalk Server Administration console to stop an orchestration.</span></span> <span data-ttu-id="7ed48-104">停止協調流程會停用並擱置所有到來的啟動訊息。</span><span class="sxs-lookup"><span data-stu-id="7ed48-104">Stopping an orchestration deactivates and suspends all of the arriving activation messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ed48-105">應用程式開發人員可以使用此主題中的程序，在開發程序中停止協調流程。</span><span class="sxs-lookup"><span data-stu-id="7ed48-105">The application developer stop an orchestration during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7ed48-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="7ed48-106">Prerequisites</span></span>  
 <span data-ttu-id="7ed48-107">若要執行這個主題中的程序，您必須使用「BizTalk Server 操作員」或「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="7ed48-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Operators group or the BizTalk Server Administrators group.</span></span> <span data-ttu-id="7ed48-108">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="7ed48-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-stop-an-orchestration"></a><span data-ttu-id="7ed48-109">停止協調流程</span><span class="sxs-lookup"><span data-stu-id="7ed48-109">To stop an orchestration</span></span>  
  
1.  <span data-ttu-id="7ed48-110">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="7ed48-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="7ed48-111">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含您想要停止的協調流程的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ed48-111">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration that you want to stop.</span></span>  
  
3.  <span data-ttu-id="7ed48-112">按一下**協調流程**，協調流程中，以滑鼠右鍵按一下，然後按一下**停止**。</span><span class="sxs-lookup"><span data-stu-id="7ed48-112">Click **Orchestrations**, right-click the orchestration, and then click **Stop**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed48-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ed48-113">See Also</span></span>  
 <span data-ttu-id="7ed48-114">[管理協調流程](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="7ed48-114">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 <span data-ttu-id="7ed48-115">[如何啟動協調流程](../core/how-to-start-an-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="7ed48-115">[How to Start an Orchestration](../core/how-to-start-an-orchestration.md) </span></span>  
 [<span data-ttu-id="7ed48-116">如何啟動和停止 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="7ed48-116">How to Start and Stop a BizTalk Application</span></span>](../core/how-to-start-and-stop-a-biztalk-application.md)