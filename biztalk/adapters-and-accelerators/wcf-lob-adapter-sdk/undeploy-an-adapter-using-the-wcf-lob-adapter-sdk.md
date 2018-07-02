---
title: 解除部署配接器使用 WCF LOB 配接器 SDK |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98f9a124-9e63-4451-af0e-ffee752fbeac
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84932fa0a140df157408ad77d9fc6bec8c0823fe
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974583"
---
# <a name="undeploy-an-adapter-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="33a8e-102">解除部署配接器使用 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="33a8e-102">Undeploy an adapter using the WCF LOB adapter SDK</span></span>
<span data-ttu-id="33a8e-103">若要解除部署配接器的電腦，使用者必須執行下列兩項工作：</span><span class="sxs-lookup"><span data-stu-id="33a8e-103">To undeploy an adapter from a computer, the user needs to perform the following two tasks:</span></span>  
  
1.  <span data-ttu-id="33a8e-104">從全域組件快取 (GAC)，解除安裝配接器組件 （及任何相依組件）。</span><span class="sxs-lookup"><span data-stu-id="33a8e-104">Uninstall the adapter assembly (and any dependent assemblies) from the global assembly cache (GAC).</span></span>  
  
2.  <span data-ttu-id="33a8e-105">在 machine.config 檔案中移除的配接器繫結和配接器繫結項目。</span><span class="sxs-lookup"><span data-stu-id="33a8e-105">Remove the adapter binding and adapter binding element in the machine.config file.</span></span>  
  
## <a name="uninstall-an-assembly-from-the-gac"></a><span data-ttu-id="33a8e-106">從 GAC 解除安裝組件</span><span class="sxs-lookup"><span data-stu-id="33a8e-106">Uninstall an Assembly from the GAC</span></span>  
  
#### <a name="use-the-windows-interface"></a><span data-ttu-id="33a8e-107">使用 Windows 介面</span><span class="sxs-lookup"><span data-stu-id="33a8e-107">Use the Windows interface</span></span>  
  
1.  <span data-ttu-id="33a8e-108">開啟 Windows 檔案總管，如下所示： 按一下**開始**，指向**所有程式**，指向**附屬應用程式**，然後按一下  **Windows 檔案總管**.</span><span class="sxs-lookup"><span data-stu-id="33a8e-108">Open Windows Explorer as follows: Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.</span></span>  
  
2.  <span data-ttu-id="33a8e-109">瀏覽至 GAC，，位於 systemdrive%\Windows\Assembly。</span><span class="sxs-lookup"><span data-stu-id="33a8e-109">Browse to the GAC, which is located at %systemdrive%\Windows\Assembly.</span></span>  
  
3.  <span data-ttu-id="33a8e-110">以滑鼠右鍵按一下包含您的應用程式在每個組件檔案中，按一下**解除安裝**，然後按一下**是**確認。</span><span class="sxs-lookup"><span data-stu-id="33a8e-110">Right-click each assembly file that is included in your application, click **Uninstall**, and then click **Yes** to confirm.</span></span>  
  
#### <a name="use-the-command-line"></a><span data-ttu-id="33a8e-111">使用命令列</span><span class="sxs-lookup"><span data-stu-id="33a8e-111">Use the command line</span></span>  
  
1. <span data-ttu-id="33a8e-112">開啟[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="33a8e-112">Open a [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt.</span></span>  
  
2. <span data-ttu-id="33a8e-113">在命令提示字元中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="33a8e-113">At the command prompt, type the following command:</span></span>  
  
    <span data-ttu-id="33a8e-114">**gacutil /u** \<*完整*<em>組件名稱</em>\></span><span class="sxs-lookup"><span data-stu-id="33a8e-114">**gacutil /u** \<*fully qualified*<em>assembly name</em>\></span></span>  
  
    <span data-ttu-id="33a8e-115">這個命令中，組件名稱會是要從 GAC 解除安裝組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="33a8e-115">In this command, the assembly name is the name of the assembly to uninstall from the GAC.</span></span>  
  
    <span data-ttu-id="33a8e-116">下列範例會從 GAC 中移除名為 hello.dll 的組件。</span><span class="sxs-lookup"><span data-stu-id="33a8e-116">The following example removes an assembly named hello.dll from the GAC.</span></span>  
  
    `gacutil /u "MyAdapter,Version=1.0.0.0, Culture=neutral, PublicKeyToken=fafafafafafafafa"`
  
## <a name="remove-the-adapter-binding-from-the-machineconfig-file"></a><span data-ttu-id="33a8e-117">移除 Machine.config 檔案中的配接器繫結</span><span class="sxs-lookup"><span data-stu-id="33a8e-117">Remove the Adapter Binding from the Machine.config File</span></span>  
 <span data-ttu-id="33a8e-118">您可以手動編輯 machine.config 檔案，以移除配接器的繫結，或 服務組態編輯器。</span><span class="sxs-lookup"><span data-stu-id="33a8e-118">You can manually edit the machine.config file to remove the adapter binding, or use the Service Configuration Editor.</span></span> <span data-ttu-id="33a8e-119">此區段會列出這兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="33a8e-119">This section lists both steps.</span></span> 
  
#### <a name="manually-edit-the-machineconfig-file"></a><span data-ttu-id="33a8e-120">手動編輯 machine.config 檔</span><span class="sxs-lookup"><span data-stu-id="33a8e-120">Manually edit the machine.config file</span></span>  
  
1.  <span data-ttu-id="33a8e-121">編輯位於 Microsoft .NET 組態資料夾中的 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="33a8e-121">Edit the machine.config file located in the Microsoft .NET configuration folder.</span></span> <span data-ttu-id="33a8e-122">若要這樣做，請按一下**開始**，按一下**執行**，型別**記事本\<Windows 安裝路徑\>\Microsoft.NET\Framework\\< 版本\>\CONFIG\machine.config**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="33a8e-122">To do this, click **Start**, click **Run**, type **notepad \<Windows install path\>\Microsoft.NET\Framework\\<version\>\CONFIG\machine.config**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33a8e-123">進行變更，以防範編輯錯誤之前，請先備份 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="33a8e-123">Make a backup of the machine.config file before you make changes to guard against editing mistakes.</span></span>  
  
2.  <span data-ttu-id="33a8e-124">更新 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="33a8e-124">Update the machine.config file.</span></span> <span data-ttu-id="33a8e-125">尋找您想要移除介面的卡 bindingExtensions 項目。</span><span class="sxs-lookup"><span data-stu-id="33a8e-125">Find the bindingExtensions element for the adapter you want to remove.</span></span> <span data-ttu-id="33a8e-126">根據存在的其他資訊，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="33a8e-126">Based on the other information that is present, do one of the following:</span></span>  
  
    -   <span data-ttu-id="33a8e-127">如果有其他 bindingExtensions，移除只有您的配接器延伸模組。</span><span class="sxs-lookup"><span data-stu-id="33a8e-127">If there are other bindingExtensions, remove only your adapter extension.</span></span>  
  
    -   <span data-ttu-id="33a8e-128">如果不有任何其他 bindingExtensions，您可以移除 bindingExtensions 區段 （包括您的配接器延伸模組）。</span><span class="sxs-lookup"><span data-stu-id="33a8e-128">If there are no other bindingExtensions, you can remove the bindingExtensions section (including your adapter extension).</span></span>  
  
    -   <span data-ttu-id="33a8e-129">如果沒有其他 bindingExtensions 或延伸模組，您可以移除延伸模組區段。</span><span class="sxs-lookup"><span data-stu-id="33a8e-129">If there are no other bindingExtensions or extensions, you can remove the extensions section.</span></span>  
  
    -   <span data-ttu-id="33a8e-130">最後，如果 system.serviceModel 包含只有您的配接器延伸模組，您可以移除整個的 system.serviceModel 區段。</span><span class="sxs-lookup"><span data-stu-id="33a8e-130">Finally, if system.serviceModel contains only your adapter extension, you can remove the entire system.serviceModel section.</span></span>  
  
3.  <span data-ttu-id="33a8e-131">重複步驟 2 bindingElementExtensions 項目。</span><span class="sxs-lookup"><span data-stu-id="33a8e-131">Repeat step 2 for the bindingElementExtensions element.</span></span>  
  
4.  <span data-ttu-id="33a8e-132">關閉並儲存 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="33a8e-132">Close and save the machine.config file.</span></span>  
  
#### <a name="use-the-service-configuration-editor-do-change-the-machineconfig-file"></a><span data-ttu-id="33a8e-133">使用 服務組態編輯器變更 machine.config 檔案</span><span class="sxs-lookup"><span data-stu-id="33a8e-133">Use the Service Configuration Editor do change the machine.config file</span></span>  
  
1.  <span data-ttu-id="33a8e-134">開啟 [服務組態編輯器]。</span><span class="sxs-lookup"><span data-stu-id="33a8e-134">Open Service Configuration Editor.</span></span> <span data-ttu-id="33a8e-135">請參閱[服務組態編輯器](https://msdn.microsoft.com/library/ms732009.aspx)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="33a8e-135">See [Service Configuration Editor](https://msdn.microsoft.com/library/ms732009.aspx) for more information.</span></span>
  
2.  <span data-ttu-id="33a8e-136">在樹狀檢視窗格中 (標示**組態**)，展開節點樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="33a8e-136">In the tree view pane (labeled **Configuration**), expand the node tree.</span></span> <span data-ttu-id="33a8e-137">按一下 **進階**資料夾中，按一下**延伸模組**資料夾，然後再選取繫結延伸模組項目。</span><span class="sxs-lookup"><span data-stu-id="33a8e-137">Click the **Advanced** folder, click the **Extensions** folder, and then select the binding extensions element.</span></span>  
  
3.  <span data-ttu-id="33a8e-138">在繫結延伸模組編輯器的詳細資料窗格中，按一下您想要刪除此項目，然後按一下 繫結延伸模組**刪除**。</span><span class="sxs-lookup"><span data-stu-id="33a8e-138">In the details pane of the Binding Extensions Editor, click the binding extension that you want to delete, and then click **Delete**.</span></span> <span data-ttu-id="33a8e-139">在下圖中，MyAdapterExtension 會反白顯示，並將被刪除。</span><span class="sxs-lookup"><span data-stu-id="33a8e-139">In the following figure, MyAdapterExtension is highlighted and will be deleted.</span></span>  
  
     <span data-ttu-id="33a8e-140">![具有新增延伸模組的服務組態編輯器。] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/955d37ea-cba5-49db-90de-0f8feb49c0e0.gif "955d37ea-cba5-49db-90de-0f8feb49c0e0")</span><span class="sxs-lookup"><span data-stu-id="33a8e-140">![Service configuration editor with added extension.](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/955d37ea-cba5-49db-90de-0f8feb49c0e0.gif "955d37ea-cba5-49db-90de-0f8feb49c0e0")</span></span>  
  
4.  <span data-ttu-id="33a8e-141">關閉 [服務組態編輯器]。</span><span class="sxs-lookup"><span data-stu-id="33a8e-141">Close the Service Configuration Editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a8e-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33a8e-142">See Also</span></span>  
 [<span data-ttu-id="33a8e-143">部署配接器使用 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="33a8e-143">Deploy an adapter using the WCF LOB adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md)