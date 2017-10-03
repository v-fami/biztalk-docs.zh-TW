---
title: "部署應用程式的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e5fb4f6-f9bd-4322-93f9-723e9e3c3317
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09970e43bd53306a6394eeffc4c2e642a8333dbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-deploying-an-application"></a><span data-ttu-id="300b5-102">部署應用程式的已知的問題</span><span class="sxs-lookup"><span data-stu-id="300b5-102">Known Issues with Deploying an Application</span></span>
## <a name="deploying-a-biztalk-application"></a><span data-ttu-id="300b5-103">部署 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="300b5-103">Deploying a BizTalk Application</span></span>  
 <span data-ttu-id="300b5-104">**部署更新的應用程式需要修正的參考**</span><span class="sxs-lookup"><span data-stu-id="300b5-104">**Deploying an updated application requires correcting references**</span></span>  
  
 <span data-ttu-id="300b5-105">如果要部署全新的應用程式以取代現有的應用程式，則必須修改其他應用程式與您要取代之應用程式間的所有參考。</span><span class="sxs-lookup"><span data-stu-id="300b5-105">If you deploy an entirely new application to replace an existing application, you must correct any references between other applications and the application that you are replacing.</span></span>  
  
 <span data-ttu-id="300b5-106">**使用 Visual Studio 來部署應用程式可以停止應用程式**</span><span class="sxs-lookup"><span data-stu-id="300b5-106">**Using Visual Studio to deploy an application can stop applications**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="300b5-107">我們建議您避免使用 Visual Studio 部署到生產環境應用程式。</span><span class="sxs-lookup"><span data-stu-id="300b5-107">We recommend that you avoid using Visual Studio to deploy an application into a production environment.</span></span>  
  
 <span data-ttu-id="300b5-108">如果您使用 Visual Studio 部署到生產環境應用程式並重新啟動主控件執行個體選項是當您部署應用程式，包括未與相關聯時，將會重新啟動設為 True，在專案屬性中，所有的主控件執行個體此應用程式。</span><span class="sxs-lookup"><span data-stu-id="300b5-108">If you use Visual Studio to deploy an application into a production environment and the Restart Host Instances option is set to True in project properties, all host instances will restart when you deploy the application, including those that are not associated with this application.</span></span> <span data-ttu-id="300b5-109">這樣會停止在本機電腦的任何主控件執行個體上執行的所有其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="300b5-109">This will stop all other applications that are running on any host instance on the local computer.</span></span>  
  
## <a name="adding-artifacts-to-a-biztalk-application"></a><span data-ttu-id="300b5-110">將成品新增至 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="300b5-110">Adding Artifacts to a BizTalk Application</span></span>  
 <span data-ttu-id="300b5-111">**移動成品可以移動相依性**</span><span class="sxs-lookup"><span data-stu-id="300b5-111">**Moving an artifact can move dependencies**</span></span>  
  
 <span data-ttu-id="300b5-112">當您將成品移到新的應用程式時，在其有相依性的其他任何成品也會移除非新的應用程式有某個參照指向已移動的成品相依成品的應用程式。</span><span class="sxs-lookup"><span data-stu-id="300b5-112">When you move an artifact to a new application, any other artifacts on which it has dependencies are also moved unless the new application has a reference to the application(s) containing the artifacts that the moved artifact depends upon.</span></span> <span data-ttu-id="300b5-113">此外，相依於移動之成品的任何成品也會移動，除非包含這些成品的應用程式有參考新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="300b5-113">Also, any artifacts that have dependencies on the moved artifact also will be moved unless the application(s) containing them have a reference to the new application.</span></span> <span data-ttu-id="300b5-114">當您移動成品時，系統會為您顯示也將一併移動之其他成品的清單。</span><span class="sxs-lookup"><span data-stu-id="300b5-114">When moving an artifact, you will be shown the list of other artifacts that will also be moved.</span></span> <span data-ttu-id="300b5-115">如需移動成品的指示，請參閱[如何將成品移至不同的應用程式](http://go.microsoft.com/fwlink/?LinkId=154999)(http://go.microsoft.com/fwlink/?LinkId=154999)。</span><span class="sxs-lookup"><span data-stu-id="300b5-115">For instructions on moving an artifact, see [How to Move an Artifact to a Different Application](http://go.microsoft.com/fwlink/?LinkId=154999) (http://go.microsoft.com/fwlink/?LinkId=154999).</span></span>  
  
## <a name="exporting-a-biztalk-application"></a><span data-ttu-id="300b5-116">匯出 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="300b5-116">Exporting a BizTalk Application</span></span>  
 <span data-ttu-id="300b5-117">**安裝 Windows Vista 上的.msi 檔案時，就可以顯示不正確的錯誤**</span><span class="sxs-lookup"><span data-stu-id="300b5-117">**An incorrect error can be displayed when installing an .msi file on Windows Vista**</span></span>  
  
 <span data-ttu-id="300b5-118">當安裝.msi 封裝使用匯出[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]上[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]Windows Vista® 上執行，您可能會收到下列不正確的錯誤，則 「 安裝程式發現未預期的錯誤，安裝此套件。</span><span class="sxs-lookup"><span data-stu-id="300b5-118">When installing an .msi package exported using [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] on [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] running on Windows Vista®, you may receive the following incorrect error, "The installer has encountered an unexpected error installing this package.</span></span> <span data-ttu-id="300b5-119">這可能表示封裝有問題。</span><span class="sxs-lookup"><span data-stu-id="300b5-119">This may indicate a problem with this package.</span></span> <span data-ttu-id="300b5-120">錯誤碼是 2869」。</span><span class="sxs-lookup"><span data-stu-id="300b5-120">The error code is 2869."</span></span> <span data-ttu-id="300b5-121">若要更正這個錯誤，第一次匯入封裝使用[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]重新匯出和安裝封裝。</span><span class="sxs-lookup"><span data-stu-id="300b5-121">To correct this error, first import the package using [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and then re-export and install the package.</span></span>  
  
## <a name="importing-a-biztalk-application"></a><span data-ttu-id="300b5-122">匯入 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="300b5-122">Importing a BizTalk Application</span></span>  
 <span data-ttu-id="300b5-123">**密碼不會移除從繫結檔案新增至應用程式**</span><span class="sxs-lookup"><span data-stu-id="300b5-123">**Passwords are not removed from binding files added to an application**</span></span>  
  
 <span data-ttu-id="300b5-124">基於安全性考量，應用程式匯出期間將從應用程式繫結移除密碼。</span><span class="sxs-lookup"><span data-stu-id="300b5-124">For security reasons, during application export, passwords are removed from application bindings.</span></span> <span data-ttu-id="300b5-125">但是，並不是從新增至應用程式的繫結檔案中移除密碼。</span><span class="sxs-lookup"><span data-stu-id="300b5-125">They are not, however, removed from any binding files that were added to the application.</span></span> <span data-ttu-id="300b5-126">匯入應用程式後，您必須重新設定密碼，應用程式才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="300b5-126">After importing the application, you will need to reconfigure the passwords in order for the application to function.</span></span> <span data-ttu-id="300b5-127">您可以藉由編輯繫結檔案，或使用管理主控台。</span><span class="sxs-lookup"><span data-stu-id="300b5-127">You can do this by editing the binding file or by using the Administration console.</span></span> <span data-ttu-id="300b5-128">如需有關編輯繫結檔案的詳細資訊，請參閱[自訂繫結檔案](http://go.microsoft.com/fwlink/?LinkId=155000)(http://go.microsoft.com/fwlink/?LinkId=155000)。</span><span class="sxs-lookup"><span data-stu-id="300b5-128">For more information about editing a binding file, see [Customizing Binding Files](http://go.microsoft.com/fwlink/?LinkId=155000) (http://go.microsoft.com/fwlink/?LinkId=155000).</span></span> <span data-ttu-id="300b5-129">如需設定配接器安全性的詳細資訊，請參閱[使用配接器](http://go.microsoft.com/fwlink/?LinkId=155001)(http://go.microsoft.com/fwlink/?LinkId=155001)。</span><span class="sxs-lookup"><span data-stu-id="300b5-129">For more information about configuring security for adapters, see [Using Adapters](http://go.microsoft.com/fwlink/?LinkId=155001) (http://go.microsoft.com/fwlink/?LinkId=155001).</span></span>  
  
 <span data-ttu-id="300b5-130">**BizTalk Server 不會回復已編寫指令碼匯入或安裝**</span><span class="sxs-lookup"><span data-stu-id="300b5-130">**BizTalk Server does not roll back scripted imports or installs**</span></span>  
  
 <span data-ttu-id="300b5-131">當匯入作業失敗時，除了自訂指令碼執行的動作外，BizTalk Server 會回復所有的匯入作業。</span><span class="sxs-lookup"><span data-stu-id="300b5-131">If an import fails, BizTalk Server rolls back all import operations except for any actions performed by custom scripts.</span></span> <span data-ttu-id="300b5-132">這也適用於安裝和解除安裝作業。</span><span class="sxs-lookup"><span data-stu-id="300b5-132">This is also true for install and uninstall operations.</span></span>  
  
 <span data-ttu-id="300b5-133">**遺漏的結構描述可能不會報告匯入之後**</span><span class="sxs-lookup"><span data-stu-id="300b5-133">**A missing schema might not be reported after an import**</span></span>  
  
 <span data-ttu-id="300b5-134">如果您在一個使用其他應用程式中之屬性結構描述的應用程式內建立傳送埠的篩選，然後再將此應用程式匯入至新的 BizTalk 群組，那麼您在安裝及啟動應用程式時，將不會收到結構描述遺失的警告，並且篩選功能也無法運作。</span><span class="sxs-lookup"><span data-stu-id="300b5-134">If you create a filter for a send port in one application that uses a property schema in another application, and then import the first application into a new BizTalk group, you will not receive a warning that the schema is missing, and filtering will not function when the application is installed and started.</span></span> <span data-ttu-id="300b5-135">在安裝沒有包含結構描述的應用程式之前，您可以先匯入包含結構描述的應用程式來修正問題。</span><span class="sxs-lookup"><span data-stu-id="300b5-135">You can correct the problem by importing the application that contains the schema before you install the application that does not contain the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="300b5-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="300b5-136">See Also</span></span>  
 [<span data-ttu-id="300b5-137">部署應用程式</span><span class="sxs-lookup"><span data-stu-id="300b5-137">Deploying an Application</span></span>](../technical-guides/deploying-an-application.md)