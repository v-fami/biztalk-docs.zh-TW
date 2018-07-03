---
title: 如何變更預設的應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications, default
- applications, modifying
- modifying, applications
ms.assetid: cfa5e88f-0bbb-4edd-a840-722dcdcce266
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b4122b7ab0581be974ee1fdd38ba2cc3ddbc41e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986551"
---
# <a name="how-to-change-the-default-application"></a><span data-ttu-id="5d3a7-102">如何變更預設應用程式</span><span class="sxs-lookup"><span data-stu-id="5d3a7-102">How to Change the Default Application</span></span>
<span data-ttu-id="5d3a7-103">本主題說明如何透過在 BizTalk Server 管理主控台中編輯應用程式的屬性，變更預設的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-103">This topic describes how to change the default application by editing the properties of an application in the BizTalk Server Administration console.</span></span> <span data-ttu-id="5d3a7-104">您也可以變更預設的應用程式建立新的應用程式並將它指定為預設應用程式中所述[如何建立應用程式](../core/how-to-create-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-104">You can also change the default application by creating a new application and specifying it as the default application, as described in [How to Create an Application](../core/how-to-create-an-application.md).</span></span>  
  
 <span data-ttu-id="5d3a7-105">安裝 BizTalk Sever 時，系統會在 BizTalk 管理資料庫中建立一個名為 BizTalk Application 1 的預設應用程式，並將它顯示在 BizTalk Server 管理主控台中。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-105">When you install BizTalk Server, a default application named BizTalk Application 1 is created in the BizTalk Management database and appears in the BizTalk Server Administration console.</span></span> <span data-ttu-id="5d3a7-106">當您從舊版的 BizTalk Server 進行升級時，您的成品會自動放入此應用程式中。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-106">When you upgrade from an earlier version of BizTalk Server, your artifacts are automatically placed in this application.</span></span> <span data-ttu-id="5d3a7-107">此外，如果您使用 BTSTask 匯入 Windows Installer (.msi) 檔案，但未指定應用程式，.msi 檔案中的成品也會匯入此預設應用程式中。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-107">In addition, when you import a Windows Installer (.msi) file by using BTSTask without specifying an application, the artifacts in the .msi file are imported into the default application.</span></span>  
  
 <span data-ttu-id="5d3a7-108">您不能刪除預設應用程式，但是可以變更預設的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-108">You cannot delete the default application; however, you can change which application is the default.</span></span> <span data-ttu-id="5d3a7-109">變更預設應用程式後，您就可以視需要刪除先前的預設應用程式。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-109">If you change the default application, you can then delete the application that was previously the default, if you want.</span></span> <span data-ttu-id="5d3a7-110">如需相關指示，請參閱 <<c0> [ 如何從 BizTalk 群組刪除 BizTalk 應用程式](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md)。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-110">For instructions, see [How to Delete a BizTalk Application from the BizTalk Group](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md).</span></span>  
  
 <span data-ttu-id="5d3a7-111">變更預設應用程式時，所有的成品都會保留在原始的預設應用程式中。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-111">When you change the default application, all of the artifacts remain in the application that was originally the default.</span></span> <span data-ttu-id="5d3a7-112">如果需要，您也可以從應用程式中明確移出這些成品。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-112">You can explicitly move the artifacts out of the application, if you want.</span></span> <span data-ttu-id="5d3a7-113">如需相關指示，請參閱 <<c0> [ 如何將成品移至不同的應用程式](../core/how-to-move-an-artifact-to-a-different-application.md)。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-113">For instructions, see [How to Move an Artifact to a Different Application](../core/how-to-move-an-artifact-to-a-different-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5d3a7-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="5d3a7-114">Prerequisites</span></span>  
 <span data-ttu-id="5d3a7-115">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-115">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="5d3a7-116">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-116">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-change-the-default-application"></a><span data-ttu-id="5d3a7-117">若要變更預設應用程式</span><span class="sxs-lookup"><span data-stu-id="5d3a7-117">To change the default application</span></span>  
  
1. <span data-ttu-id="5d3a7-118">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-118">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="5d3a7-119">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 BizTalk 群組、 以滑鼠右鍵按一下您想要設成預設值，然後按一下 應用程式**屬性**。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-119">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, right-click the application that you want to make the default, and then click **Properties**.</span></span>  
  
3. <span data-ttu-id="5d3a7-120">選取 **將此設為預設應用程式**核取方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="5d3a7-120">Select the **Make this the default application** check box, and click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d3a7-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d3a7-121">See Also</span></span>  
 [<span data-ttu-id="5d3a7-122">建立和修改 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="5d3a7-122">Creating and Modifying BizTalk Applications</span></span>](../core/creating-and-modifying-biztalk-applications.md)