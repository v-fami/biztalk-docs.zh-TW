---
title: 如何將繫結匯出至繫結檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3734ae6d-b790-40f2-8403-d7c7fdbe381b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ab9dd60b37c16169f76e052706adb43c4606fcf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982215"
---
# <a name="how-to-export-bindings-to-a-binding-file"></a><span data-ttu-id="18c69-102">如何將繫結匯出至繫結檔案</span><span class="sxs-lookup"><span data-stu-id="18c69-102">How to Export Bindings to a Binding File</span></span>
<span data-ttu-id="18c69-103">您可以匯出至另一個現有 BizTalk 應用程式使用的繫結檔案的 BizTalk 應用程式的繫結。</span><span class="sxs-lookup"><span data-stu-id="18c69-103">You can export the bindings of a BizTalk application into another existing BizTalk application using a binding file.</span></span> <span data-ttu-id="18c69-104">您也可以匯出群組中的所有繫結或組件的繫結。</span><span class="sxs-lookup"><span data-stu-id="18c69-104">You can also export all the bindings in a group or the binding for an assembly.</span></span> <span data-ttu-id="18c69-105">接著，您可以將這些繫結匯入到應用程式或群組。</span><span class="sxs-lookup"><span data-stu-id="18c69-105">Subsequently, you can import those bindings into either an application or group.</span></span>  
  
 <span data-ttu-id="18c69-106">繫結檔案是 XML 檔案，描述 BizTalk 管理資料庫和其關聯性中的成品。</span><span class="sxs-lookup"><span data-stu-id="18c69-106">A binding file is an XML file that describes the artifacts in the BizTalk Management database and their relationships.</span></span> <span data-ttu-id="18c69-107">它包含每個 BizTalk Server 協調流程、 管線、 對應或結構描述範圍內的 BizTalk 組件、 應用程式或群組的繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="18c69-107">It contains binding information for each BizTalk Server orchestration, pipeline, map, or schema in the scope of a BizTalk assembly, application, or group.</span></span> <span data-ttu-id="18c69-108">它包含每個傳送埠的組態設定、 傳送埠群組、 接收埠、 接收位置和合作對象。</span><span class="sxs-lookup"><span data-stu-id="18c69-108">It contains the configuration settings for each send port, send port group, receive port, receive location, and party.</span></span> <span data-ttu-id="18c69-109">此外，它也會描述每個協調流程繫結至的主機和其信任層級。</span><span class="sxs-lookup"><span data-stu-id="18c69-109">It also describes which host each orchestration is bound to and its trust level.</span></span>  
  
## <a name="why-to-export-to-a-binding-file"></a><span data-ttu-id="18c69-110">若要匯出至繫結檔案的原因</span><span class="sxs-lookup"><span data-stu-id="18c69-110">Why to Export to a Binding File</span></span>  
 <span data-ttu-id="18c69-111">繫結檔案可加速部署在下列情況下不需要手動設定繫結：</span><span class="sxs-lookup"><span data-stu-id="18c69-111">Binding files can speed deployment in the following scenarios by avoiding the need to manually configure bindings:</span></span>  
  
- <span data-ttu-id="18c69-112">**將應用程式從一個部署環境移至另一個**</span><span class="sxs-lookup"><span data-stu-id="18c69-112">**Moving an application from one deployment environment to another**</span></span>  
  
   <span data-ttu-id="18c69-113">使用繫結檔案可加快部署速度所避免需要手動設定不同的部署環境的繫結這類從開發環境至測試環境。</span><span class="sxs-lookup"><span data-stu-id="18c69-113">Using a binding file can speed deployment by avoiding the need to manually configure bindings for different deployment environments, such as from a development environment to a test environment.</span></span>  
  
- <span data-ttu-id="18c69-114">**更新組件**</span><span class="sxs-lookup"><span data-stu-id="18c69-114">**Updating an assembly**</span></span>  
  
   <span data-ttu-id="18c69-115">您可以使用繫結檔案會自動套用或重新套用至組件的更新後的組件的繫結。</span><span class="sxs-lookup"><span data-stu-id="18c69-115">You can use a binding file to automatically apply or reapply the bindings to an assembly after an update of the assembly.</span></span>  
  
- <span data-ttu-id="18c69-116">**將組件部署到多個 BizTalk 群組**</span><span class="sxs-lookup"><span data-stu-id="18c69-116">**Deploying an assembly to multiple BizTalk groups**</span></span>  
  
   <span data-ttu-id="18c69-117">您可以避免需要個別設定使用繫結檔案部署到多個 BizTalk 群組的組件的繫結。</span><span class="sxs-lookup"><span data-stu-id="18c69-117">You can avoid the need to separately configure the bindings for an assembly deployed into multiple BizTalk groups by using a binding file.</span></span>  
  
  <span data-ttu-id="18c69-118">使用繫結檔案可讓您將繫結套用至應用程式的彈性。</span><span class="sxs-lookup"><span data-stu-id="18c69-118">Using a binding file gives you flexibility in applying bindings to an application.</span></span> <span data-ttu-id="18c69-119">當您匯出至.msi 檔案的應用程式時，您只能指定所有的應用程式的繫結會匯出至.msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="18c69-119">When you export an application to an .msi file, you can only specify that all of the bindings for the application will be exported to the .msi file.</span></span> <span data-ttu-id="18c69-120">您可以使用繫結檔案執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="18c69-120">With binding files you can do the following:</span></span>  
  
- <span data-ttu-id="18c69-121">從目前的應用程式的所有繫結，所有的繫結，從目前的群組或只有單一組件的繫結，請匯出至繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="18c69-121">Export to a binding file all bindings from the current application, all bindings from the current group, or only the bindings for a single assembly.</span></span> <span data-ttu-id="18c69-122">（您可以使用這樣的匯出繫結命令 [管理] 主控台中的應用程式。）</span><span class="sxs-lookup"><span data-stu-id="18c69-122">(You do so by using the Export Bindings command for an application in the Administration console.)</span></span>  
  
- <span data-ttu-id="18c69-123">如此會立即套用其繫結，或讓應用程式匯入另一個群組時，會套用繫結，您可以繫結檔案新增至應用程式 （使用 [新增資源] 命令）。</span><span class="sxs-lookup"><span data-stu-id="18c69-123">You can add a binding file to an application (using the Add Resources command) so that its bindings are applied immediately or so the bindings are applied when the application is imported into another group.</span></span>  
  
- <span data-ttu-id="18c69-124">您可以將多個繫結檔案新增至應用程式 （使用 [新增資源] 命令），並指定每個目標部署環境。</span><span class="sxs-lookup"><span data-stu-id="18c69-124">You can add multiple binding files to an application (using the Add Resources command) and specify a target deployment environment for each one.</span></span> <span data-ttu-id="18c69-125">這可讓您針對多個部署環境使用單一的部署套件。</span><span class="sxs-lookup"><span data-stu-id="18c69-125">This enables you to use a single deployment package for multiple deployment environments.</span></span> <span data-ttu-id="18c69-126">當您匯入應用程式時，您可以選取要套用的繫結。</span><span class="sxs-lookup"><span data-stu-id="18c69-126">When you import the application, you can select which bindings to apply.</span></span>  
  
- <span data-ttu-id="18c69-127">您可以匯出個別的繫結檔案的應用程式中的多個組件。</span><span class="sxs-lookup"><span data-stu-id="18c69-127">You can export separate binding files for multiple assemblies in an application.</span></span>  
  
- <span data-ttu-id="18c69-128">在產生繫結檔後，您依然能夠加以編輯以變更其繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="18c69-128">You can edit binding files after you generate them to change their binding information.</span></span>  
  
## <a name="how-to-export-to-a-binding-file"></a><span data-ttu-id="18c69-129">如何匯出至繫結檔案</span><span class="sxs-lookup"><span data-stu-id="18c69-129">How to Export to a Binding File</span></span>  
 <span data-ttu-id="18c69-130">在 BizTalk Server 管理主控台中，執行應用程式匯出繫結命令或命令列上使用 BTSTask ExportBindings 命令，您可以匯出繫結檔案的應用程式的繫結。</span><span class="sxs-lookup"><span data-stu-id="18c69-130">You export the bindings of an application to a binding file by executing the Export Bindings command for the application in the BizTalk Server Administration console, or by using the BTSTask ExportBindings command on the command line.</span></span>  
  
 <span data-ttu-id="18c69-131">基於安全性理由，當您匯出繫結檔案時，BizTalk Server 會從該檔案移除繫結的密碼。</span><span class="sxs-lookup"><span data-stu-id="18c69-131">For security reasons, when you export a binding file, BizTalk Server removes the passwords for the bindings from the file.</span></span> <span data-ttu-id="18c69-132">匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="18c69-132">After importing the bindings, you must reconfigure passwords for send ports and receive locations before they will function.</span></span> <span data-ttu-id="18c69-133">您可以在 BizTalk Server 管理主控台的 [傳輸屬性] 對話方塊中，為傳送埠或接收位置設定密碼。</span><span class="sxs-lookup"><span data-stu-id="18c69-133">You configure passwords in the Transport Properties dialog box of the BizTalk Server Administration console for the send port or receive location.</span></span>  
  
 <span data-ttu-id="18c69-134">繫結檔案中的資訊會取代現有的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="18c69-134">Information in a binding file supersedes existing configuration information.</span></span> <span data-ttu-id="18c69-135">如果繫結檔案中的成品名稱與現有組態中的成品名稱相符，則當您匯入繫結檔案時，繫結檔案中的成品將會更新現有組態中的成品。</span><span class="sxs-lookup"><span data-stu-id="18c69-135">If the name of an artifact in a binding file matches the name of an artifact in your existing configuration, the artifact in the binding file will update the artifact in your existing configuration when you import the binding file.</span></span>  
  
 <span data-ttu-id="18c69-136">如需如何儲存在繫結檔案的主機和信任層級，繫結檔案中的主控件和信任層級如何比對主機和信任層級中應用程式，並套用繫結的順序，請參閱[繫結檔案和應用程式部署](http://go.microsoft.com/fwlink/?LinkID=154726)(http://go.microsoft.com/fwlink/?LinkID=154726)。</span><span class="sxs-lookup"><span data-stu-id="18c69-136">For information about how hosts and trust levels are stored in binding files, how host and trust levels in a binding file are matched to hosts and trust levels in the application, and the order in which bindings are applied, see [Binding Files and Application Deployment](http://go.microsoft.com/fwlink/?LinkID=154726) (http://go.microsoft.com/fwlink/?LinkID=154726).</span></span> <span data-ttu-id="18c69-137">如需有關如何匯出 BizTalk 應用程式的繫結的指示，請參閱 <<c0> [ 如何匯出 BizTalk 應用程式的繫結](http://go.microsoft.com/fwlink/?LinkId=155009)(http://go.microsoft.com/fwlink/?LinkId=155009)。</span><span class="sxs-lookup"><span data-stu-id="18c69-137">For instructions on how to export bindings for a BizTalk application, see [How to Export Bindings for a BizTalk Application](http://go.microsoft.com/fwlink/?LinkId=155009) (http://go.microsoft.com/fwlink/?LinkId=155009).</span></span>