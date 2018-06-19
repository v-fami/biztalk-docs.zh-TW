---
title: 繫結檔案和應用程式部署 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings
- deploying [applications], binding files
- assemblies, binding files
- bindings, applying
- groups, assemblies
- applications, binding files
- binding files, applications
- bindings, hosts
- deploying, assemblies
- updating, assemblies
- assemblies, updating
- hosts, bindings
- binding files, assemblies
- applications, moving
- assemblies, deploying
- binding files, about binding files
- bindings, about bindings
- groups, deploying
- binding files, deploying
- bindings, binding files
ms.assetid: 396ad021-8001-4ed8-8b28-85b72f981fae
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc6908f962cd3bb8f9fdec3fcaab6bc131c889da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234062"
---
# <a name="binding-files-and-application-deployment"></a><span data-ttu-id="e6514-102">繫結檔案和應用程式部署</span><span class="sxs-lookup"><span data-stu-id="e6514-102">Binding Files and Application Deployment</span></span>
<span data-ttu-id="e6514-103">本主題提供使用繫結檔案讓 BizTalk 組件和應用程式部署更為容易的概觀資訊。</span><span class="sxs-lookup"><span data-stu-id="e6514-103">This topic provides overview information about using binding files to make BizTalk assembly and application deployment easier.</span></span> <span data-ttu-id="e6514-104">您可能會在下列案例中發現，使用繫結檔案即可避免手動設定繫結，因此可以使部署加速：</span><span class="sxs-lookup"><span data-stu-id="e6514-104">You may find that binding files speed deployment in the following scenarios by avoiding the need to manually configure bindings:</span></span>  
  
-   <span data-ttu-id="e6514-105">將應用程式從一個部署環境移動到另一個部署環境。</span><span class="sxs-lookup"><span data-stu-id="e6514-105">Moving an application from one deployment environment to another.</span></span>  
  
-   <span data-ttu-id="e6514-106">更新組件。</span><span class="sxs-lookup"><span data-stu-id="e6514-106">Updating an assembly.</span></span>  
  
-   <span data-ttu-id="e6514-107">將組件部署至多個 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="e6514-107">Deploying an assembly to multiple BizTalk groups.</span></span>  
  
## <a name="what-is-a-binding"></a><span data-ttu-id="e6514-108">何謂繫結？</span><span class="sxs-lookup"><span data-stu-id="e6514-108">What is a binding?</span></span>  
 <span data-ttu-id="e6514-109">繫結會在邏輯端點 (例如協調流程連接埠或角色連結) 與實體端點 (例如傳送和接收埠或合作對象) 之間建立對應。</span><span class="sxs-lookup"><span data-stu-id="e6514-109">A binding creates a mapping between a logical endpoint, such as an orchestration port or a role link, and a physical endpoint, such as a send and receive port or party.</span></span> <span data-ttu-id="e6514-110">這讓通訊能在不同的 BizTalk 商務方案元件之間進行。</span><span class="sxs-lookup"><span data-stu-id="e6514-110">This enables communication between different components of a BizTalk business solution.</span></span> <span data-ttu-id="e6514-111">您可以使用 [BizTalk Server 管理主控台] 建立繫結。</span><span class="sxs-lookup"><span data-stu-id="e6514-111">You can create bindings by using the BizTalk Server Administration console.</span></span>  
  
## <a name="what-is-a-binding-file"></a><span data-ttu-id="e6514-112">何謂繫結檔案？</span><span class="sxs-lookup"><span data-stu-id="e6514-112">What is a binding file?</span></span>  
 <span data-ttu-id="e6514-113">繫結檔案是一種 .xml 檔案，其中包含在 BizTalk 組件、應用程式或群組之範圍中的每個 BizTalk 協調流程、管線、對應或結構描述的繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="e6514-113">A binding file is an .xml file that contains binding information for each BizTalk orchestration, pipeline, map, or schema in the scope of a BizTalk assembly, application, or group.</span></span> <span data-ttu-id="e6514-114">繫結檔案描述每個協調流程所繫結的主控件、其信任層級，以及每個傳送埠、傳送埠群組、接收埠、接收位置和已設定合作對象的設定。</span><span class="sxs-lookup"><span data-stu-id="e6514-114">The binding file describes what host each orchestration is bound to and its trust level as well as the settings for each send port, send port group, receive port, receive location, and party that has been configured.</span></span> <span data-ttu-id="e6514-115">您可以產生繫結檔案，然後將其所包含的繫結套用至組件、應用程式或群組，以避免需要在不同的部署環境中手動設定繫結。</span><span class="sxs-lookup"><span data-stu-id="e6514-115">You can generate binding files and then apply the bindings they contain to an assembly, application, or group to avoid needing to manually configure bindings in different deployment environments.</span></span>  
  
## <a name="why-use-binding-files"></a><span data-ttu-id="e6514-116">為何使用繫結檔案？</span><span class="sxs-lookup"><span data-stu-id="e6514-116">Why use binding files?</span></span>  
 <span data-ttu-id="e6514-117">您可能需要在下列案例中使用繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="e6514-117">You may want to use binding files in the following scenarios.</span></span>  
  
### <a name="moving-from-one-environment-to-another"></a><span data-ttu-id="e6514-118">從一個環境移至另一個環境</span><span class="sxs-lookup"><span data-stu-id="e6514-118">Moving from one environment to another</span></span>  
 <span data-ttu-id="e6514-119">您可以使用繫結檔案，讓應用程式能夠更容易地從一個部署環境移至另一個部署環境，例如從開發環境移至測試環境。</span><span class="sxs-lookup"><span data-stu-id="e6514-119">You can use binding files to make it easier to move an application from one deployment environment to another, such as from a development environment to a test environment.</span></span> <span data-ttu-id="e6514-120">這是因為繫結通常都必須為不同的部署環境重新設定，不過藉由使用繫結檔案，即可避免重複執行這項手動組態步驟。</span><span class="sxs-lookup"><span data-stu-id="e6514-120">This is because bindings often must be reconfigured for different deployment environments, but by using binding files, you can avoid repeatedly performing this manual configuration step.</span></span>  
  
 <span data-ttu-id="e6514-121">您可以進行此項的一種方式，便是建立繫結庫，並在將應用程式部署到新環境時，從其中加以選取。</span><span class="sxs-lookup"><span data-stu-id="e6514-121">One way you can do this is to create a library of bindings from which to select when deploying the application into a new environment.</span></span> <span data-ttu-id="e6514-122">例如，您可以為測試環境建立繫結檔案，並為實際執行環境建立另一個繫結檔案，然後將這兩者都新增到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="e6514-122">For example, you can create a binding file for your test environment and another one for your production environment and then add them both to the application.</span></span> <span data-ttu-id="e6514-123">當您將應用程式匯入到測試環境時，即可選取套用測試繫結的選項。</span><span class="sxs-lookup"><span data-stu-id="e6514-123">When you import the application into the test environment, you can select an option to apply the test bindings.</span></span> <span data-ttu-id="e6514-124">同樣的，當您將應用程式匯入到實際執行環境時，也可以選取套用實際執行繫結的選項。</span><span class="sxs-lookup"><span data-stu-id="e6514-124">Likewise, when you import the application into the production environment, you can select an option to apply the production bindings.</span></span> <span data-ttu-id="e6514-125">這樣即可避免為不同環境手動重新設定繫結的需要。</span><span class="sxs-lookup"><span data-stu-id="e6514-125">This avoids the need to reconfigure bindings manually for different environments.</span></span> <span data-ttu-id="e6514-126">另一種方式則是在將應用程式匯入到目前的環境後，再匯入您所建立適用於該環境的繫結。</span><span class="sxs-lookup"><span data-stu-id="e6514-126">Another way is to import bindings that you have created for the current environment after importing the application into it.</span></span> <span data-ttu-id="e6514-127">這樣便會自動套用繫結。</span><span class="sxs-lookup"><span data-stu-id="e6514-127">This automatically applies the bindings.</span></span>  
  
### <a name="updating-an-assembly"></a><span data-ttu-id="e6514-128">更新組件</span><span class="sxs-lookup"><span data-stu-id="e6514-128">Updating an assembly</span></span>  
 <span data-ttu-id="e6514-129">當您在應用程式中更新組件時，其繫結通常都會遭到覆寫，或是組件可能根本不會繫結，進而使您必須手動重新設定繫結。</span><span class="sxs-lookup"><span data-stu-id="e6514-129">When you update an assembly in an application, its bindings are often overwritten or else the assembly may not be bound at all, forcing you to manually reconfigure bindings.</span></span> <span data-ttu-id="e6514-130">若要避免這種問題，您可以使用如下的繫結檔：</span><span class="sxs-lookup"><span data-stu-id="e6514-130">To avoid this, you can use a binding file as follows:</span></span>  
  
-   <span data-ttu-id="e6514-131">**正在更新相同版本的組件。**</span><span class="sxs-lookup"><span data-stu-id="e6514-131">**Updating the same version of an assembly.**</span></span> <span data-ttu-id="e6514-132">如果組件具有早期繫結連接埠或動態連接埠，而且您有在 [ BizTalk Server 管理主控台] 中變更連接埠組態，當您以具有相同版本號碼的組件來更新組件時，便會遺失設定。</span><span class="sxs-lookup"><span data-stu-id="e6514-132">If the assembly has early bound ports or dynamic ports, and you changed the port configuration in the BizTalk Server Administration console, the settings will be lost when you update the assembly with an assembly having the same version number.</span></span> <span data-ttu-id="e6514-133">您可以為將要更新的組件匯出繫結檔。</span><span class="sxs-lookup"><span data-stu-id="e6514-133">You can export a binding file for the assembly you are going to update.</span></span> <span data-ttu-id="e6514-134">在更新組件後，您可以將組件匯入到應用程式中，然後再匯入其繫結檔以重新套用先前的繫結。</span><span class="sxs-lookup"><span data-stu-id="e6514-134">After updating the assembly you can import the assembly into the application and then import its binding file to reapply the previous bindings.</span></span>  
  
-   <span data-ttu-id="e6514-135">**更新組件的較新版本。**</span><span class="sxs-lookup"><span data-stu-id="e6514-135">**Updating an assembly with a newer version.**</span></span> <span data-ttu-id="e6514-136">您可以為將要更新的組件匯出繫結檔，然後予以編輯以反映新的組件版本。</span><span class="sxs-lookup"><span data-stu-id="e6514-136">You can export a binding file for the assembly that you are going to update and then edit it to reflect the new assembly version.</span></span> <span data-ttu-id="e6514-137">在將新的組件版本匯入到應用程式後，您便可以將繫結檔匯入到應用程式以套用繫結。</span><span class="sxs-lookup"><span data-stu-id="e6514-137">After you import the new assembly version into the application, you can import the binding file into the application to apply the bindings.</span></span> <span data-ttu-id="e6514-138">如需編輯繫結檔案的指示，請參閱[自訂繫結檔案](../core/customizing-binding-files.md)。</span><span class="sxs-lookup"><span data-stu-id="e6514-138">For instructions on editing a binding file, see [Customizing Binding Files](../core/customizing-binding-files.md).</span></span>  
  
### <a name="deploying-an-assembly-to-multiple-biztalk-groups"></a><span data-ttu-id="e6514-139">將組件部署至多個 BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="e6514-139">Deploying an assembly to multiple BizTalk groups</span></span>  
 <span data-ttu-id="e6514-140">當您將組件部署至多個 BizTalk 群組時，可以一起傳輸組件的繫結和組件本身。</span><span class="sxs-lookup"><span data-stu-id="e6514-140">When you deploy an assembly into multiple BizTalk groups, you can transport the bindings for the assembly along with the assembly.</span></span> <span data-ttu-id="e6514-141">這樣即可避免為每個群組中的組件分別設定繫結。</span><span class="sxs-lookup"><span data-stu-id="e6514-141">This avoids the need to separately configure the bindings for the assembly in each group.</span></span> <span data-ttu-id="e6514-142">您可以用下列方法進行：</span><span class="sxs-lookup"><span data-stu-id="e6514-142">You can do this as follows:</span></span>  
  
1.  <span data-ttu-id="e6514-143">匯出組件的繫結，進而為您所要部署的組件建立繫結檔。</span><span class="sxs-lookup"><span data-stu-id="e6514-143">Create a binding file for the assembly that you want to deploy by exporting the assembly's bindings.</span></span>  
  
2.  <span data-ttu-id="e6514-144">將組件及其繫結檔新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6514-144">Add the assembly and its binding file to an application.</span></span> <span data-ttu-id="e6514-145">如果您在部署組件時要與其他成品分開，應用程式便只能包含組件和繫結檔。</span><span class="sxs-lookup"><span data-stu-id="e6514-145">If you are deploying the assembly separately from other artifacts, the application can contain only the assembly and the binding file.</span></span>  
  
3.  <span data-ttu-id="e6514-146">匯出應用程式的 .msi 檔案，並確定選取要匯出的繫結檔。</span><span class="sxs-lookup"><span data-stu-id="e6514-146">Export an .msi file for the application, being sure to select the binding file to export as well.</span></span>  
  
4.  <span data-ttu-id="e6514-147">將應用程式 .msi 檔案匯入到您要在其中部署的 BizTalk 群組和應用程式中。</span><span class="sxs-lookup"><span data-stu-id="e6514-147">Import the application .msi file into the BizTalk groups and applications where you want to deploy it.</span></span> <span data-ttu-id="e6514-148">在匯入時，檔案中的繫結便會自動套用至組件。</span><span class="sxs-lookup"><span data-stu-id="e6514-148">The bindings in the file are automatically applied to the assembly on import.</span></span>  
  
## <a name="how-can-i-generate-and-use-binding-files"></a><span data-ttu-id="e6514-149">我如何能夠產生和使用繫結檔？</span><span class="sxs-lookup"><span data-stu-id="e6514-149">How can I generate and use binding files?</span></span>  
 <span data-ttu-id="e6514-150">繫結檔案不會自動產生 BizTalk 組件、 應用程式或群組，但您可以產生繫結檔案匯出繫結中所述[匯出繫結](../core/exporting-bindings6.md)。</span><span class="sxs-lookup"><span data-stu-id="e6514-150">A binding file is not automatically generated for a BizTalk assembly, application, or group, but you can generate a binding file by exporting bindings, as described in [Exporting Bindings](../core/exporting-bindings6.md).</span></span> <span data-ttu-id="e6514-151">您可以再將繫結檔案匯入應用程式或群組中所述[如何匯入到 BizTalk 應用程式的繫結](../core/how-to-import-bindings-into-a-biztalk-application.md)和[如何匯入到 BizTalk 群組的繫結](../core/how-to-import-bindings-into-a-biztalk-group.md)，它會自動套用其繫結。</span><span class="sxs-lookup"><span data-stu-id="e6514-151">You can then import the binding file into an application or group, as described in [How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md) and [How to Import Bindings into a BizTalk Group](../core/how-to-import-bindings-into-a-biztalk-group.md), which automatically applies its bindings.</span></span>  
  
 <span data-ttu-id="e6514-152">或者，您可以新增繫結檔案至應用程式以便應用程式匯入另一個群組，而非立即套用中所述，會套用其繫結[如何將繫結檔案新增至應用程式](../core/how-to-add-a-binding-file-to-an-application2.md).</span><span class="sxs-lookup"><span data-stu-id="e6514-152">Alternatively, you can add the binding file to an application so that its bindings are applied when the application is imported into another group, rather than being applied immediately, as described in [How to Add a Binding File to an Application](../core/how-to-add-a-binding-file-to-an-application2.md).</span></span> <span data-ttu-id="e6514-153">只要使用最後一種方法，您就能將多個繫結檔新增到應用程式，並能選擇性地指定每個繫結檔的目標部署環境。</span><span class="sxs-lookup"><span data-stu-id="e6514-153">Using the last method, you can add multiple binding files to an application and optionally specify a target deployment environment for each one.</span></span> <span data-ttu-id="e6514-154">當您匯入應用程式時，然後您可以選取要套用，哪些繫結中所述，根據目標部署環境，[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e6514-154">When you import the application, you can then select which bindings to apply, based on the target deployment environment, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span> <span data-ttu-id="e6514-155">使用最後一種方法，您也可以針對應用程式中的不同組件而匯入個別的繫結檔。</span><span class="sxs-lookup"><span data-stu-id="e6514-155">Using the last method, you can also import separate binding files for the different assemblies in your application.</span></span>  
  
 <span data-ttu-id="e6514-156">在產生繫結檔後，您依然能夠加以編輯以變更其繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="e6514-156">You can edit binding files after you generate them to change their binding information.</span></span> <span data-ttu-id="e6514-157">如需詳細資訊，請參閱[自訂繫結檔案](../core/customizing-binding-files.md)。</span><span class="sxs-lookup"><span data-stu-id="e6514-157">For more information, see [Customizing Binding Files](../core/customizing-binding-files.md).</span></span>  
  
## <a name="how-are-bindings-applied"></a><span data-ttu-id="e6514-158">繫結是如何套用的？</span><span class="sxs-lookup"><span data-stu-id="e6514-158">How are bindings applied?</span></span>  
 <span data-ttu-id="e6514-159">當繫結檔匯入至應用程式，或是當應用程式匯入至新的 BizTalk 群組時，便會套用繫結。</span><span class="sxs-lookup"><span data-stu-id="e6514-159">Bindings are applied when a binding file is imported into an application, or when an application is imported into a new BizTalk group.</span></span> <span data-ttu-id="e6514-160">在使用繫結檔時，最好先瞭解成品如何繫結到主控件，以及套用繫結的順序。</span><span class="sxs-lookup"><span data-stu-id="e6514-160">When using binding files, it is important to understand how artifacts are bound to hosts and in the order in which bindings are applied.</span></span>  
  
### <a name="binding-to-hosts"></a><span data-ttu-id="e6514-161">繫結到主控件</span><span class="sxs-lookup"><span data-stu-id="e6514-161">Binding to hosts</span></span>  
 <span data-ttu-id="e6514-162">當繫結個別匯出或是做為應用程式的一部分而匯出時，主控件和信任層級便會存放在繫結檔中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e6514-162">When bindings are exported either separately or as part of an application, hosts and trust levels are stored in the binding file as follows:</span></span>  
  
-   <span data-ttu-id="e6514-163">**傳送埠。**</span><span class="sxs-lookup"><span data-stu-id="e6514-163">**Send Port.**</span></span> <span data-ttu-id="e6514-164">與傳送處理常式相關聯之主控件的信任層級。</span><span class="sxs-lookup"><span data-stu-id="e6514-164">Trust level of the host associated with the send handler.</span></span>  
  
-   <span data-ttu-id="e6514-165">**接收位置。**</span><span class="sxs-lookup"><span data-stu-id="e6514-165">**Receive Location.**</span></span> <span data-ttu-id="e6514-166">與接收處理常式相關聯之主控件的信任層級。</span><span class="sxs-lookup"><span data-stu-id="e6514-166">Trust level of the host associated with the receive handler.</span></span>  
  
-   <span data-ttu-id="e6514-167">**協調流程。**</span><span class="sxs-lookup"><span data-stu-id="e6514-167">**Orchestration.**</span></span> <span data-ttu-id="e6514-168">主控件的信任層級。</span><span class="sxs-lookup"><span data-stu-id="e6514-168">Trust Level of the host.</span></span>  
  
 <span data-ttu-id="e6514-169">當繫結匯入至應用程式，或是應用程式從 .msi 檔案匯入至新的 BizTalk 群組時，繫結檔中的主控件和信任層級便會與應用程式中的主控件和信任層級相符，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e6514-169">When the bindings are imported into an application, or an application is imported from the .msi file into a new BizTalk group, hosts and trust levels in the binding files are matched to hosts and trust levels in the application, as follows:</span></span>  
  
-   <span data-ttu-id="e6514-170">**傳送埠。**</span><span class="sxs-lookup"><span data-stu-id="e6514-170">**Send Port.**</span></span> <span data-ttu-id="e6514-171">傳送埠會繫結至具有相同名稱的傳送處理常式，並會繫結至與存放在繫結檔中的主控件具有相同信任層級的主控件。</span><span class="sxs-lookup"><span data-stu-id="e6514-171">The send port is bound to a send handler of the same name and bound to a host with the same trust level as that stored in the binding file.</span></span>  
  
-   <span data-ttu-id="e6514-172">**接收位置。**</span><span class="sxs-lookup"><span data-stu-id="e6514-172">**Receive Location.**</span></span> <span data-ttu-id="e6514-173">接收位置會繫結至具有相同名稱的接收處理常式，並會繫結至與存放在繫結檔中的主控件具有相同信任層級的主控件。</span><span class="sxs-lookup"><span data-stu-id="e6514-173">The receive location is bound to a receive handler of the same name and bound to a host with the same trust level as that stored in the binding file.</span></span>  
  
-   <span data-ttu-id="e6514-174">**協調流程。**</span><span class="sxs-lookup"><span data-stu-id="e6514-174">**Orchestrations.**</span></span> <span data-ttu-id="e6514-175">協調流程會繫結至具有相同名稱的主控件，以及在繫結檔中具有相同信任層級的主控件。</span><span class="sxs-lookup"><span data-stu-id="e6514-175">The orchestration is bound to a host with the same name and trust level and as that in the binding file.</span></span>  
  
### <a name="order-in-which-bindings-are-applied"></a><span data-ttu-id="e6514-176">套用繫結的順序</span><span class="sxs-lookup"><span data-stu-id="e6514-176">Order in which bindings are applied</span></span>  
 <span data-ttu-id="e6514-177">當您匯入應用程式時，將依下列順序套用繫結：</span><span class="sxs-lookup"><span data-stu-id="e6514-177">When you import an application, bindings are applied in the following order:</span></span>  
  
1.  <span data-ttu-id="e6514-178">並非透過繫結檔案明確加入至應用程式，而是使用者明確選定欲匯出至應用程式 .msi 檔案的應用程式繫結 (由 BizTalk Server 所產生)。</span><span class="sxs-lookup"><span data-stu-id="e6514-178">Application bindings generated by BizTalk Server that were not explicitly added to the application via a binding file, but that were explicitly selected by the user for export into the application .msi file.</span></span>  
  
2.  <span data-ttu-id="e6514-179">已經加入應用程式的繫結檔中，而且沒有指定目標部署環境的繫結。</span><span class="sxs-lookup"><span data-stu-id="e6514-179">Bindings in binding files that have been added to the application, and which do not have a target deployment environment specified.</span></span> <span data-ttu-id="e6514-180">這些繫結不會以特定的順序套用。</span><span class="sxs-lookup"><span data-stu-id="e6514-180">These bindings are applied in no specific order.</span></span>  
  
3.  <span data-ttu-id="e6514-181">已經加入應用程式的繫結檔，而且其相關聯目標部署環境與應用程式匯入所選定的部署環境相符的繫結。</span><span class="sxs-lookup"><span data-stu-id="e6514-181">Bindings in binding files that have been added to the application, and which have an associated target deployment environment that matches the deployment environment selected for application import.</span></span> <span data-ttu-id="e6514-182">這些繫結不會以特定的順序套用。</span><span class="sxs-lookup"><span data-stu-id="e6514-182">These bindings are applied in no specific order.</span></span>  
  
 <span data-ttu-id="e6514-183">由於繫結是在匯入過程中套用，新的繫結會覆寫先前已套用的同名繫結。</span><span class="sxs-lookup"><span data-stu-id="e6514-183">As bindings are applied during the import process, bindings that have already been applied are overwritten by new bindings that have the same name.</span></span> <span data-ttu-id="e6514-184">也就是說，同名的繫結當中最後套用的繫結將會生效。</span><span class="sxs-lookup"><span data-stu-id="e6514-184">In other words, the last binding of a particular name to be applied takes effect.</span></span>  
  
 <span data-ttu-id="e6514-185">例如，如果現有的應用程式包括名為 SendPort1 的傳送埠，而且套用的繫結檔以相同名稱描述某個傳送埠，繫結檔中的設定便會覆寫 SendPort1 的現有設定。</span><span class="sxs-lookup"><span data-stu-id="e6514-185">For example, if an existing application includes a send port named SendPort1, and a binding file is applied that describes a send port with the same name, the settings in the binding file will overwrite the existing settings for SendPort1.</span></span> <span data-ttu-id="e6514-186">例如，如果現有的應用程式包括名為 ErrorHandling.ErrorHandler.ResubmitLogic 的協調流程，而且繫結檔描述具有相同名稱的協調流程，該協調流程的所有現有繫結便會以繫結檔中的繫結寫入。</span><span class="sxs-lookup"><span data-stu-id="e6514-186">If an existing application includes an orchestration named ErrorHandling.ErrorHandler.ResubmitLogic, for example, and a binding file describes an orchestration having the same name, all of the existing bindings for the orchestration will be written with the bindings in the binding file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6514-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6514-187">See Also</span></span>  
 [<span data-ttu-id="e6514-188">了解 BizTalk 應用程式部署和管理</span><span class="sxs-lookup"><span data-stu-id="e6514-188">Understanding BizTalk Application Deployment and Management</span></span>](../core/understanding-biztalk-application-deployment-and-management.md)