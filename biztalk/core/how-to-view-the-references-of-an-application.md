---
title: 如何檢視應用程式的參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications, viewing
- applications, referencing
ms.assetid: 5f1026e1-c73e-495d-8160-9ba68f38b9d8
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a23583edde1e1edbf4f0613904ebf24271a225f5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979271"
---
# <a name="how-to-view-the-references-of-an-application"></a><span data-ttu-id="86acb-102">如何檢視應用程式的參考</span><span class="sxs-lookup"><span data-stu-id="86acb-102">How to View the References of an Application</span></span>
<span data-ttu-id="86acb-103">本主題說明如何使用「BizTalk Server 管理」主控台，檢視目前應用程式所參考的應用程式清單。</span><span class="sxs-lookup"><span data-stu-id="86acb-103">This topic describes how to use the BizTalk Server Administration console to view the list of applications to which the current application has references.</span></span> <span data-ttu-id="86acb-104">如需有關如何新增參考的詳細資訊，請參閱[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。</span><span class="sxs-lookup"><span data-stu-id="86acb-104">For more information about adding references, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).</span></span> <span data-ttu-id="86acb-105">您也可以檢視參考此應用程式的應用程式清單。</span><span class="sxs-lookup"><span data-stu-id="86acb-105">You can also view the list of applications that have references to this application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="86acb-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="86acb-106">Prerequisites</span></span>  
 <span data-ttu-id="86acb-107">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="86acb-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="86acb-108">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="86acb-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-view-the-references-for-an-application"></a><span data-ttu-id="86acb-109">若要檢視應用程式的參考</span><span class="sxs-lookup"><span data-stu-id="86acb-109">To view the references for an application</span></span>  
  
1. <span data-ttu-id="86acb-110">按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="86acb-110">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="86acb-111">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下您想要檢視，然後按一下其參考的應用程式**屬性**。</span><span class="sxs-lookup"><span data-stu-id="86acb-111">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click the application whose references you want to view, and click **Properties**.</span></span>  
  
3. <span data-ttu-id="86acb-112">在 [屬性] 頁面的左窗格中，按一下**參考**。</span><span class="sxs-lookup"><span data-stu-id="86acb-112">In the left pane of the properties page, click **References**.</span></span>  
  
    <span data-ttu-id="86acb-113">此應用程式參考的應用程式會列在右邊窗格上半部，</span><span class="sxs-lookup"><span data-stu-id="86acb-113">The applications to which this application refers are listed in the upper section of the right pane.</span></span> <span data-ttu-id="86acb-114">參考此應用程式的應用程式會列在右邊窗格下半部。</span><span class="sxs-lookup"><span data-stu-id="86acb-114">The applications that refer to this application are listed in the lower section of the right pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86acb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86acb-115">See Also</span></span>  
 [<span data-ttu-id="86acb-116">建立和修改 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="86acb-116">Creating and Modifying BizTalk Applications</span></span>](../core/creating-and-modifying-biztalk-applications.md)