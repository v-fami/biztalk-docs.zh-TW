---
title: "如何將成品移至不同的應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- artifacts, moving
- applications, artifacts
ms.assetid: 861e7782-0566-4478-a0bd-f8ced1ea6d56
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdc28eb92b09d459ba5f05439572f07e3f35411f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-an-artifact-to-a-different-application"></a><span data-ttu-id="7d3dc-102">如何將成品移到另一個應用程式</span><span class="sxs-lookup"><span data-stu-id="7d3dc-102">How to Move an Artifact to a Different Application</span></span>
<span data-ttu-id="7d3dc-103">本主題描述如何使用 BizTalk Server 管理主控台的 [移至應用程式] 命令，在 BizTalk 群組內將成品從某個應用程式移到另一個。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-103">This topic describes how to move an artifact from one application to another within a BizTalk group by using the Move To Application command of the BizTalk Server Administration console.</span></span> <span data-ttu-id="7d3dc-104">如果您需要將已經存在於某個應用程式中的成品用於相同 BizTalk 群組內的另一個應用程式，可能會想要這樣做。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-104">You might want to do this if you need to use an artifact that already exists in one application in a different application in the same BizTalk group.</span></span>  
  
 <span data-ttu-id="7d3dc-105">在移動成品時，請牢記下列要點：</span><span class="sxs-lookup"><span data-stu-id="7d3dc-105">When moving an artifact, bear in mind the following important points:</span></span>  
  
-   <span data-ttu-id="7d3dc-106">**應用程式必須在相同的群組。**</span><span class="sxs-lookup"><span data-stu-id="7d3dc-106">**The applications must be in the same group.**</span></span> <span data-ttu-id="7d3dc-107">只有當成品移動來源的應用程式與成品移入的目標應用程式位於相同 BizTalk 群組的情況下，[移至應用程式] 命令才會執行。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-107">The Move To Application command only works if the application from which you want to move the artifact is in the same BizTalk group as the application to which you want to move the artifact.</span></span> <span data-ttu-id="7d3dc-108">如果您想要將此成品移到另一個群組中的應用程式，可以從此成品目前所在的應用程式匯出此成品，然後將它匯入到新的應用程式，或是將此成品加入到此應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-108">If you want to move the artifact to an application in a different group, you can either export the artifact from the application in which it currently exists and then import it into the new application, or add the artifact to the application.</span></span> <span data-ttu-id="7d3dc-109">如需指示，請參閱[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)，[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)，和[如何建立或新增成品](../core/how-to-create-or-add-an-artifact.md)。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-109">For instructions, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md), [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md), and [How to Create or Add an Artifact](../core/how-to-create-or-add-an-artifact.md).</span></span> <span data-ttu-id="7d3dc-110">您必須手動移除該成品從原始的應用程式中所述[如何從應用程式移除成品](../core/how-to-remove-an-artifact-from-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-110">You must then manually remove the artifact from the original application, as described in [How to Remove an Artifact from an Application](../core/how-to-remove-an-artifact-from-an-application.md).</span></span>  
  
-   <span data-ttu-id="7d3dc-111">**移動成品時，可能也會移動的成品的相依或相依於它。**</span><span class="sxs-lookup"><span data-stu-id="7d3dc-111">**Moving an artifact may also move artifacts on which it depends or that depend on it.**</span></span> <span data-ttu-id="7d3dc-112">當您將成品移到新的應用程式時，除非新的應用程式有參考移動之成品所相依之成品的所在應用程式，否則也會移動該成品所相依的其他任何成品。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-112">When you move an artifact to a new application, any other artifacts on which it has dependencies are also moved unless the new application has a reference to the application(s) containing the artifacts on which the moved artifact depends.</span></span> <span data-ttu-id="7d3dc-113">此外，相依於移動之成品的任何成品也會移動，除非包含這些成品的應用程式有參考新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-113">Also, any artifacts that have dependencies on the moved artifact are moved unless the application(s) containing them have a reference to the new application.</span></span> <span data-ttu-id="7d3dc-114">當您移動成品時，系統會為您顯示也將一併移動之其他成品的清單。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-114">When moving an artifact, you are shown the list of other artifacts that will also be moved.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d3dc-115">如果您需要在兩個或多個應用程式中使用相同的成品，您可能需要建立一項參考，從您想要使用此成品的應用程式參考到目前包含此成品的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-115">If you need to use the same artifact in two or more applications, you may need to create a reference from the application in which you want to use the artifact to the one currently containing the artifact.</span></span> <span data-ttu-id="7d3dc-116">這是因為某些類型的成品在 BizTalk 群組中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-116">This is because certain types of artifacts must be unique in a BizTalk group.</span></span> <span data-ttu-id="7d3dc-117">如需詳細資訊，請參閱[成品，必須是唯一的應用程式或群組](../core/artifacts-that-must-be-unique-in-an-application-or-group.md)。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-117">For more information, see [Artifacts That Must Be Unique in an Application or Group](../core/artifacts-that-must-be-unique-in-an-application-or-group.md).</span></span> <span data-ttu-id="7d3dc-118">如需新增參考的指示，請參閱[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-118">For instructions on adding references, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).</span></span> <span data-ttu-id="7d3dc-119">請注意，新增對另一個應用程式的參考會在應用程式之間建立相依性，也會影響您必須部署這些應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-119">Be aware that adding a reference to another application creates dependencies between the applications and affects the way you must deploy them.</span></span> <span data-ttu-id="7d3dc-120">如需背景資訊，請參閱[相依性和應用程式部署](../core/dependencies-and-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-120">For background information, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7d3dc-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="7d3dc-121">Prerequisites</span></span>  
 <span data-ttu-id="7d3dc-122">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-122">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="7d3dc-123">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-123">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-move-an-artifact-to-a-different-application"></a><span data-ttu-id="7d3dc-124">將成品移到不同的應用程式</span><span class="sxs-lookup"><span data-stu-id="7d3dc-124">To move an artifact to a different application</span></span>  
  
1.  <span data-ttu-id="7d3dc-125">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-125">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="7d3dc-126">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 依序展開 [BizTalk 群組] 和想要移動之成品的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-126">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, and then expand the application from which you want to move an artifact.</span></span>  
  
3.  <span data-ttu-id="7d3dc-127">按一下包含您想要移動，以滑鼠右鍵按一下成品，然後按一下該成品的資料夾**移至應用程式**。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-127">Click the folder containing the artifact that you want to move, right-click the artifact, and then click **Move To Application**.</span></span>  
  
4.  <span data-ttu-id="7d3dc-128">在**目的端應用程式**方塊，按一下箭頭，然後按一下您要移動之成品的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-128">In the **Destination application** box, click the arrow, and then click the application to which you want to move the artifact.</span></span>  
  
     <span data-ttu-id="7d3dc-129">**移動成品**方塊會顯示要移動，以及所有相依的成品，也將一併移動之成品。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-129">The **Moving Artifacts** box displays the artifact to move, along with all dependent artifacts, which will be moved as well.</span></span>  
  
5.  <span data-ttu-id="7d3dc-130">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="7d3dc-130">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d3dc-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d3dc-131">See Also</span></span>  
 [<span data-ttu-id="7d3dc-132">建立和修改 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="7d3dc-132">Creating and Modifying BizTalk Applications</span></span>](../core/creating-and-modifying-biztalk-applications.md)