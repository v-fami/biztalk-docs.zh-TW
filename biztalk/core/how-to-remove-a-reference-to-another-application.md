---
title: "如何移除另一個應用程式的參考 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: applications, references
ms.assetid: cc867706-7c56-4386-b7ec-9fd7cf6c83a4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de51adb1a9c42874025527ad458ecb6e3c311b3f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-reference-to-another-application"></a><span data-ttu-id="6b243-102">如何移除另一個應用程式的參考</span><span class="sxs-lookup"><span data-stu-id="6b243-102">How to Remove a Reference to Another Application</span></span>
<span data-ttu-id="6b243-103">本主題描述如何使用 BizTalk Server 管理主控台，從某個應用程式中移除其他應用程式的參考。</span><span class="sxs-lookup"><span data-stu-id="6b243-103">This topic describes how to use the BizTalk Server Administration console to remove a reference from one application to another application.</span></span> <span data-ttu-id="6b243-104">當您不再需要使用目前應用程式中的成品，而該成品位於相同 BizTalk 群組的其他應用程式中時，請移除參考。</span><span class="sxs-lookup"><span data-stu-id="6b243-104">You remove a reference when you no longer need to use an artifact in the current application that exists in another application in the same BizTalk group.</span></span> <span data-ttu-id="6b243-105">如需新增參考的詳細資訊，請參閱[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。</span><span class="sxs-lookup"><span data-stu-id="6b243-105">For more information on adding references, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).</span></span>  
  
 <span data-ttu-id="6b243-106">如果目前應用程式中的成品仍在使用參考應用程式中的成品，移除參考的作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="6b243-106">If artifacts in the current application still use artifacts in the referenced application, the operation to remove the reference will fail.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="6b243-107">BizTalk Server 中的每個應用程式都會自動包含 BizTalk.系統應用程式的參考。</span><span class="sxs-lookup"><span data-stu-id="6b243-107">Every application in BizTalk Server automatically contains a reference to the BizTalk.System application.</span></span> <span data-ttu-id="6b243-108">這是因為每一個 BizTalk 應用程式都會使用 BizTalk 系統包含的成品。</span><span class="sxs-lookup"><span data-stu-id="6b243-108">This is because the artifacts that BizTalk.System contains are used by every BizTalk application.</span></span> <span data-ttu-id="6b243-109">您絕對不能移除 BizTalk.系統應用程式的參考，</span><span class="sxs-lookup"><span data-stu-id="6b243-109">You should never remove a reference to the BizTalk.System application.</span></span> <span data-ttu-id="6b243-110">否則您的應用程式可能無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="6b243-110">If you do, your application may not function correctly.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6b243-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="6b243-111">Prerequisites</span></span>  
 <span data-ttu-id="6b243-112">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="6b243-112">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="6b243-113">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="6b243-113">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-remove-a-reference-to-another-application"></a><span data-ttu-id="6b243-114">若要移除另一個應用程式的參考</span><span class="sxs-lookup"><span data-stu-id="6b243-114">To remove a reference to another application</span></span>  
  
1.  <span data-ttu-id="6b243-115">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="6b243-115">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="6b243-116">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，以滑鼠右鍵按一下您要從中移除參考 （參考到另一個應用程式），應用的程式，然後按一下**屬性**.</span><span class="sxs-lookup"><span data-stu-id="6b243-116">In the console tree, expand  **BizTalk Server Administration**, right-click the application from which you want to remove a reference (the one that refers to another application), and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="6b243-117">在 [屬性] 頁面的左窗格中，按一下**參考**。</span><span class="sxs-lookup"><span data-stu-id="6b243-117">In the left pane of the properties page, click **References**.</span></span>  
  
4.  <span data-ttu-id="6b243-118">在右窗格中，按一下 應用程式，您不想再參考這個應用程式，請按一下 **移除**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6b243-118">In the right pane, click the application that you no longer want to reference from this application, click **Remove**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b243-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b243-119">See Also</span></span>  
 [<span data-ttu-id="6b243-120">建立和修改 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="6b243-120">Creating and Modifying BizTalk Applications</span></span>](../core/creating-and-modifying-biztalk-applications.md)