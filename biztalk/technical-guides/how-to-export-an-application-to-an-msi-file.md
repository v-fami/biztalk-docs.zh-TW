---
title: "如何匯出至.msi 檔案的應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7179e86-aa55-426b-a0db-19229ca5625a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 600118718585401d9ba6c3158b6510af55c53e74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-an-application-to-an-msi-file"></a><span data-ttu-id="915d6-102">如何匯出至.msi 檔案的應用程式</span><span class="sxs-lookup"><span data-stu-id="915d6-102">How to Export an Application to an .msi File</span></span>
<span data-ttu-id="915d6-103">您可以使用匯出 MSI 檔案精靈或 BTSTask，應用程式成品匯出至.msi 檔案將應用程式匯入新的 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="915d6-103">You can use the Export MSI File Wizard or BTSTask to export the application artifacts into an .msi file that you will use to import the application into a new BizTalk group.</span></span> <span data-ttu-id="915d6-104">此程序也會將執行它的電腦上安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="915d6-104">This process will also install the application on the computers that will run it.</span></span>  
  
## <a name="exporting-application-bindings-in-an-msi-file"></a><span data-ttu-id="915d6-105">匯出應用程式.msi 檔案中的繫結</span><span class="sxs-lookup"><span data-stu-id="915d6-105">Exporting Application Bindings in an .msi File</span></span>  
 <span data-ttu-id="915d6-106">當您匯出至.msi 檔案的應用程式時，您可以選取要匯出哪些資源。</span><span class="sxs-lookup"><span data-stu-id="915d6-106">When you export an application into an .msi file, you select which resources to export.</span></span> <span data-ttu-id="915d6-107">這些資源可以包含的全部或子集已部署的組件或匯出繫結可供使用。</span><span class="sxs-lookup"><span data-stu-id="915d6-107">These resources can include all or a subset of the deployed assemblies or bindings that are available for export.</span></span>  
  
 <span data-ttu-id="915d6-108">若要讓您更輕鬆地匯入您的開發環境的應用程式在稍後變更或新增項目，您可能想要匯出繫結每個應用程式，然後將其加入回應用程式。</span><span class="sxs-lookup"><span data-stu-id="915d6-108">To make it easier to import the applications back into your development environment at a later time to make changes or additions, you may want to export the bindings for each application and then add them back into the applications.</span></span> <span data-ttu-id="915d6-109">當您設定與資源類型"BiztalkBinding 」 時，您可以加入額外的繫結檔案至.msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="915d6-109">When you set the Resource type to "BiztalkBinding," you can add additional binding files to an .msi file.</span></span> <span data-ttu-id="915d6-110">您將加入每個繫結檔案，您必須指定應該套用這些繫結至環境名稱 （文字欄位）。</span><span class="sxs-lookup"><span data-stu-id="915d6-110">For each binding file that you add, you must specify the environment name (text field) that the bindings should be applied to.</span></span> <span data-ttu-id="915d6-111">然後在匯入時，您會詢問以選取目前匯環境名稱。</span><span class="sxs-lookup"><span data-stu-id="915d6-111">Then on import, you will be asked to select the environment name to which you are presently importing.</span></span> <span data-ttu-id="915d6-112">如果這些相符，則會套用至目標群組繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="915d6-112">If these match, then the binding file is applied to the target group.</span></span> <span data-ttu-id="915d6-113">您也可以指定任何環境加入繫結檔案名稱，這會導致無條件地套用到所有環境的繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="915d6-113">You can also specify no environment name for the added binding file, which will cause the set of bindings to be applied to all environments unconditionally.</span></span>  
  
 <span data-ttu-id="915d6-114">使用.msi 檔案會自動化功能可以否則有很多設定的手動工作。</span><span class="sxs-lookup"><span data-stu-id="915d6-114">Using an .msi file automates what can otherwise be a substantial set of manual tasks.</span></span> <span data-ttu-id="915d6-115">在實際執行環境中，您可以輕鬆部署到多個 BizTalk 群組組件所傳輸的繫結，以及組件的組件。</span><span class="sxs-lookup"><span data-stu-id="915d6-115">In a production environment, you can make it easier to deploy an assembly into multiple BizTalk groups by transporting the bindings for the assembly along with the assembly.</span></span> <span data-ttu-id="915d6-116">如果您的應用程式包含大量的成品，您可以將匯出之成品的一些單一的 Windows Installer 套件，以及一些成一或多個其他 Windows Installer 封裝。</span><span class="sxs-lookup"><span data-stu-id="915d6-116">If your application contains a significant number of artifacts, you can export some of the artifacts into one Windows Installer package and some into one or more other Windows Installer packages.</span></span>  
  
 <span data-ttu-id="915d6-117">同時匯出應用程式，您應該考慮一些重點。</span><span class="sxs-lookup"><span data-stu-id="915d6-117">While exporting the application, you should consider some important points.</span></span> <span data-ttu-id="915d6-118">例如，您可以匯出所有應用程式中的成品或您想要加入或更新的成品。</span><span class="sxs-lookup"><span data-stu-id="915d6-118">For example, you may either export all of the artifacts in the application or only the artifacts that you want to add or update.</span></span> <span data-ttu-id="915d6-119">如果您匯出檔案成品，請確定它是您想要在應用程式中使用的版本。</span><span class="sxs-lookup"><span data-stu-id="915d6-119">If you export a file artifact, make sure that it is the version that you want to use in the application.</span></span> <span data-ttu-id="915d6-120">更多這類點以及匯出至.msi 檔案的 BizTalk 應用程式的詳細資訊，請參閱[如何匯出 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154848)(http://go.microsoft.com/fwlink/?LinkID=154848)。</span><span class="sxs-lookup"><span data-stu-id="915d6-120">For more such points and for more information about exporting a BizTalk application into an .msi file, see [How to Export a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154848) (http://go.microsoft.com/fwlink/?LinkID=154848).</span></span>