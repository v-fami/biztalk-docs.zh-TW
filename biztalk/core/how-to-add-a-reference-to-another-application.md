---
title: 如何將參考加入另一個應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications, referencing
ms.assetid: 6a177560-ee1f-403a-a68a-ade409a39a35
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25668e7cfcb7d810d999c01eef28e5116b46c298
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-reference-to-another-application"></a><span data-ttu-id="a7211-102">如何新增另一個應用程式的參考</span><span class="sxs-lookup"><span data-stu-id="a7211-102">How to Add a Reference to Another Application</span></span>
<span data-ttu-id="a7211-103">本主題說明如何使用 BizTalk Server 管理主控台，在應用程式中加入另一個應用程式的參考。</span><span class="sxs-lookup"><span data-stu-id="a7211-103">This topic describes how to use the BizTalk Server Administration console to add a reference from one application to another application.</span></span> <span data-ttu-id="a7211-104">您也可以加入其他應用程式的參考，當您匯入您的應用程式使用匯入精靈中所述[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a7211-104">You can also add a reference to the other application when you import your application by using the Import Wizard, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span>  
  
 <span data-ttu-id="a7211-105">當您想在目前應用程式中使用相同 BizTalk 群組內另一個應用程式的現有成品，便可以加入參考。</span><span class="sxs-lookup"><span data-stu-id="a7211-105">You add a reference when you want to use an artifact in the current application that already exists in another application in the same BizTalk group.</span></span> <span data-ttu-id="a7211-106">這是因為大多數類型的成品在 BizTalk 群組中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a7211-106">This is because most types of artifacts must be unique in a BizTalk group.</span></span> <span data-ttu-id="a7211-107">因此，您應加入另一個已包含成品之應用程式的參考，而不要在目前的應用程式中加入重複成品。</span><span class="sxs-lookup"><span data-stu-id="a7211-107">Rather than adding the duplicate artifact to the current application, you add a reference to the other application that already contains the artifact.</span></span> <span data-ttu-id="a7211-108">如需詳細資訊，請參閱[成品，必須是唯一的應用程式或群組](../core/artifacts-that-must-be-unique-in-an-application-or-group.md)。</span><span class="sxs-lookup"><span data-stu-id="a7211-108">For more information, see [Artifacts That Must Be Unique in an Application or Group](../core/artifacts-that-must-be-unique-in-an-application-or-group.md).</span></span>  
  
 <span data-ttu-id="a7211-109">當您想要使用另一個應用程式中現有的虛擬目錄或憑證時，不一定要加入參考。</span><span class="sxs-lookup"><span data-stu-id="a7211-109">It is not necessary to add a reference when you want to use a virtual directory or a certificate that already exists in another application.</span></span> <span data-ttu-id="a7211-110">而且建議您不要加入參考，因為這會造成循環參考。</span><span class="sxs-lookup"><span data-stu-id="a7211-110">Furthermore, we recommend against doing this because it can create a circular reference.</span></span>  
  
 <span data-ttu-id="a7211-111">匯入具有相依性的應用程式時，也會匯入參考。</span><span class="sxs-lookup"><span data-stu-id="a7211-111">When you import an application that has dependencies, references can be imported as well.</span></span> <span data-ttu-id="a7211-112">新增對另一個應用程式的參考時，請記住這會影響您部署這些應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="a7211-112">When adding a reference to another application, bear in mind that this affects the way you deploy both applications.</span></span> <span data-ttu-id="a7211-113">如需詳細資訊，請參閱[相依性和應用程式部署](../core/dependencies-and-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="a7211-113">For more information, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a7211-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="a7211-114">Prerequisites</span></span>  
 <span data-ttu-id="a7211-115">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="a7211-115">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="a7211-116">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a7211-116">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-add-a-reference-to-another-application"></a><span data-ttu-id="a7211-117">若要新增另一個應用程式的參考</span><span class="sxs-lookup"><span data-stu-id="a7211-117">To add a reference to another application</span></span>  
  
1.  <span data-ttu-id="a7211-118">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a7211-118">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a7211-119">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下您要建立參考的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a7211-119">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and right-click the application in which you want to create a reference.</span></span> <span data-ttu-id="a7211-120">這是您想要在其中使用另一個應用程式中所包含成品的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a7211-120">This is the application in which you want to use an artifact that is contained in another application.</span></span>  
  
3.  <span data-ttu-id="a7211-121">指向**新增**，然後按一下 **參考**。</span><span class="sxs-lookup"><span data-stu-id="a7211-121">Point to **Add** and then click **References**.</span></span>  
  
4.  <span data-ttu-id="a7211-122">在**應用程式**，選取您要加入的參考 （包含的應用程式的成品或您想要使用的成品），應用程式，然後按一下核取方塊**確定**。</span><span class="sxs-lookup"><span data-stu-id="a7211-122">In **Applications**, select the check box of the application to which you want to add a reference (the application containing the artifact or artifacts that you want to use), and then click **OK**.</span></span>  
  
     <span data-ttu-id="a7211-123">參考隨即加入至目前應用程式中。</span><span class="sxs-lookup"><span data-stu-id="a7211-123">The reference is added to the current application.</span></span> <span data-ttu-id="a7211-124">在主控台樹狀結構中，目前應用程式中所參考的另一個應用程式會加上手形圖示，表示有一或多個應用程式參考它。</span><span class="sxs-lookup"><span data-stu-id="a7211-124">In the console tree, a hand icon is added to the application that you referred from this application to indicate that it is referenced by one or more other applications.</span></span>  
  
     <span data-ttu-id="a7211-125">![共用應用程式圖示](../core/media/sharedapplicationicon.gif "SharedApplicationIcon")</span><span class="sxs-lookup"><span data-stu-id="a7211-125">![Shared application icon](../core/media/sharedapplicationicon.gif "SharedApplicationIcon")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7211-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7211-126">See Also</span></span>  
 [<span data-ttu-id="a7211-127">建立和修改 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="a7211-127">Creating and Modifying BizTalk Applications</span></span>](../core/creating-and-modifying-biztalk-applications.md)