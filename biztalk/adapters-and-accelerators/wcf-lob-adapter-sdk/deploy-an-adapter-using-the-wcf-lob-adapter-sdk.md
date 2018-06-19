---
title: 部署配接器使用 WCF LOB 配接器 SDK |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 376b4dcf-2d2c-4872-a394-67edc0c3d088
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c11ae1067fff276d8d24639d3e4d3cc6798c6ba5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967292"
---
# <a name="deploy-an-adapter-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="5153f-102">部署配接器使用 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="5153f-102">Deploy an adapter using the WCF LOB adapter SDK</span></span>
<span data-ttu-id="5153f-103">若要部署配接器，必須將配接器組件安裝到全域組件快取 (GAC)，然後註冊在 machine.config 檔案中的配接器。</span><span class="sxs-lookup"><span data-stu-id="5153f-103">To deploy an adapter, you must install the adapter assembly into the global assembly cache (GAC), and then register the adapter in the machine.config file.</span></span>  
  
## <a name="install-the-adapter-assembly-into-the-gac"></a><span data-ttu-id="5153f-104">配接器組件安裝到 GAC</span><span class="sxs-lookup"><span data-stu-id="5153f-104">Install the Adapter Assembly into the GAC</span></span>  
 <span data-ttu-id="5153f-105">之前使用配接器在 Visual Studio 使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]命令或在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]功能，您必須將組件安裝到 GAC。</span><span class="sxs-lookup"><span data-stu-id="5153f-105">Before consuming an adapter in Visual Studio using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] command or in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] by using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] feature, you must install the assembly into the GAC.</span></span> <span data-ttu-id="5153f-106">強式名稱的組件可以安裝到 GAC。</span><span class="sxs-lookup"><span data-stu-id="5153f-106">Only assemblies that are strong-named can be installed into the GAC.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5153f-107">若要完成此程序，您必須使用對 GAC 具有寫入權限的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="5153f-107">To complete this procedure, you must be logged on with an account that has Write permissions on the GAC.</span></span> <span data-ttu-id="5153f-108">本機電腦上的「系統管理員」帳戶具有這些權限。</span><span class="sxs-lookup"><span data-stu-id="5153f-108">The Administrators account on the local computer has these permissions.</span></span>  
  
#### <a name="configure-a-strong-name-assembly-key-file"></a><span data-ttu-id="5153f-109">設定強式名稱組件金鑰檔案</span><span class="sxs-lookup"><span data-stu-id="5153f-109">Configure a strong name assembly key file</span></span>  
  
1.  <span data-ttu-id="5153f-110">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，載入配接器專案檔需要強式名稱。</span><span class="sxs-lookup"><span data-stu-id="5153f-110">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], load the adapter project file that needs a strong name.</span></span>  
  
2.  <span data-ttu-id="5153f-111">開啟[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="5153f-111">Open a [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt.</span></span>  
  
3.  <span data-ttu-id="5153f-112">在命令提示字元中，切換到您想要儲存金鑰檔案的資料夾，再輸入下列命令，然後按下 ENTER：</span><span class="sxs-lookup"><span data-stu-id="5153f-112">At the command prompt, from the folder where you want to store the key file, type the following command, and then press ENTER:</span></span>  
  
     <span data-ttu-id="5153f-113">**sn /k***file_name* **.snk** </span><span class="sxs-lookup"><span data-stu-id="5153f-113">**sn /k**  *file_name* **.snk**</span></span>  
  
     <span data-ttu-id="5153f-114">範例： **sn /k EchoAdapter.snk**</span><span class="sxs-lookup"><span data-stu-id="5153f-114">Example: **sn /k EchoAdapter.snk**</span></span>  
  
     <span data-ttu-id="5153f-115">確認訊息，**金鑰組寫入** \< *file_name*\>**.snk** `,`會出現在命令列。</span><span class="sxs-lookup"><span data-stu-id="5153f-115">A confirmation message, **Key pair written to** \<*file_name*\>**.snk**`,` displays on the command line.</span></span>  
  
4.  <span data-ttu-id="5153f-116">在 Visual Studio 方案總管 中，以滑鼠右鍵按一下專案，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="5153f-116">In Visual Studio Solution Explorer, right-click the project, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="5153f-117">在左窗格中，依序展開**通用屬性**，然後按一下 **組件**。</span><span class="sxs-lookup"><span data-stu-id="5153f-117">In the left pane, expand **Common Properties**, and then click **Assembly**.</span></span>  
  
6.  <span data-ttu-id="5153f-118">在右窗格中，捲動到**強式名稱**方塊。</span><span class="sxs-lookup"><span data-stu-id="5153f-118">In the right pane, scroll to the **Strong name** box.</span></span>  
  
7.  <span data-ttu-id="5153f-119">在**強式名稱**方塊中，按一下欄位旁**組件金鑰檔案**，按一下瀏覽按鈕 (**...**)，然後瀏覽至金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="5153f-119">In the **Strong name** box, click the field next to **Assembly Key File**, click the browse button (**…**), and then browse to the key file.</span></span>  
  
8.  <span data-ttu-id="5153f-120">按一下金鑰檔案，再按一下**開啟**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="5153f-120">Click the key file, click **Open**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="5153f-121">在 Visual Studio 功能表中，按一下 **建置**，然後選擇 **建置方案**。</span><span class="sxs-lookup"><span data-stu-id="5153f-121">On the Visual Studio menu, click **Build**, and then choose **Build Solution**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5153f-122">如果您的配接器組件相依於任何其他組件，請確定這些參考的組件簽署為強式名稱。否則，您會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="5153f-122">If your adapter assembly depends on any other assemblies, ensure these referenced assemblies are signed with a strong name; otherwise you will get an error.</span></span>  
  
 <span data-ttu-id="5153f-123">如果您有來源，您可以使用強式名稱重新編譯先前所示。</span><span class="sxs-lookup"><span data-stu-id="5153f-123">If you have the source, you can recompile with a strong name as shown previously.</span></span> <span data-ttu-id="5153f-124">如果參考組件屬於第三方，而且您將無法確定，將會為它指定強式名稱，您可以反組譯，然後切割為強式名稱組件。</span><span class="sxs-lookup"><span data-stu-id="5153f-124">If the reference assembly belongs to a third-party and you cannot ensure that it will be given a strong name, you can disassemble and then reassemble the assembly with a strong name.</span></span>  
  
 <span data-ttu-id="5153f-125">原始組件將會覆寫，因此如果您想要保留原始的版本，請確定您進行下列步驟進行之前它的備份複本。</span><span class="sxs-lookup"><span data-stu-id="5153f-125">Your original assembly will be overwritten, so if you want to keep the original version, ensure you make a backup copy of it before proceeding with the following steps.</span></span>  
  
 <span data-ttu-id="5153f-126">使用 Microsoft Intermediate Language (MSIL) 的解譯器解譯組件：</span><span class="sxs-lookup"><span data-stu-id="5153f-126">Use Microsoft Intermediate Language (MSIL) Disassembler to disassemble the assembly:</span></span>  
  
-   <span data-ttu-id="5153f-127">ILDASM thirdparty.dll /out:thirdparty.il</span><span class="sxs-lookup"><span data-stu-id="5153f-127">ILDASM thirdparty.dll /out:thirdparty.il</span></span>  
  
 <span data-ttu-id="5153f-128">MSIL 組譯工具可以用於切割為強式名稱組件：</span><span class="sxs-lookup"><span data-stu-id="5153f-128">Use MSIL Assembler to reassemble the assembly with a strong name:</span></span>  
  
-   <span data-ttu-id="5153f-129">ILASM thirdparty.il /dll /key=strongkeyfile.snk</span><span class="sxs-lookup"><span data-stu-id="5153f-129">ILASM thirdparty.il /dll /key=strongkeyfile.snk</span></span>  
  
#### <a name="install-an-assembly-in-the-gac"></a><span data-ttu-id="5153f-130">在 GAC 中安裝組件</span><span class="sxs-lookup"><span data-stu-id="5153f-130">Install an assembly in the GAC</span></span>  
  
1.  <span data-ttu-id="5153f-131">請確認您的配接器已簽署。</span><span class="sxs-lookup"><span data-stu-id="5153f-131">Verify that your adapter has been signed.</span></span>  
  
2.  <span data-ttu-id="5153f-132">開啟[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="5153f-132">Open a [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt.</span></span>  
  
3.  <span data-ttu-id="5153f-133">輸入以下命令：</span><span class="sxs-lookup"><span data-stu-id="5153f-133">Type the following command:</span></span>  
  
     <span data-ttu-id="5153f-134">**gacutil.exe /if"\<**  *組件.dll 檔案路徑*  **\>"**</span><span class="sxs-lookup"><span data-stu-id="5153f-134">**gacutil.exe /if "\<** *path to the assembly .dll file* **\>"**</span></span>  
  
4.  <span data-ttu-id="5153f-135">這會將組件安裝至 GAC，覆寫任何同名的現有組件。</span><span class="sxs-lookup"><span data-stu-id="5153f-135">This installs the assembly to the GAC, overwriting any existing assembly that has the same assembly name.</span></span>  
  
## <a name="register-the-adapter-in-machineconfig"></a><span data-ttu-id="5153f-136">在 Machine.config 中註冊配接器</span><span class="sxs-lookup"><span data-stu-id="5153f-136">Register the Adapter in Machine.config</span></span>  
 <span data-ttu-id="5153f-137">使用配接器開發[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]會呈現為 WCF 繫結。</span><span class="sxs-lookup"><span data-stu-id="5153f-137">An adapter developed using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is surfaced as a WCF binding.</span></span>  <span data-ttu-id="5153f-138">如需詳細資訊，請參閱 Microsoft.ServiceModel.Channels.Common.AdapterBinding。</span><span class="sxs-lookup"><span data-stu-id="5153f-138">See Microsoft.ServiceModel.Channels.Common.AdapterBinding for more information.</span></span>  <span data-ttu-id="5153f-139">註冊 WCF 配接器繫結使用\<bindingExtensions\>區段內\<系統。ServiceModel\>和 WCF 已註冊配接器傳輸繫結項目使用\<bindingElementExtensions\>區段內\<系統。ServiceModel\>。</span><span class="sxs-lookup"><span data-stu-id="5153f-139">The adapter binding is registered with WCF using \<bindingExtensions\> section within \<system.ServiceModel\> and the adapter transport binding element is registered with WCF using \<bindingElementExtensions\> section within \<system.ServiceModel\>.</span></span>  
  
 <span data-ttu-id="5153f-140">您可以手動編輯 machine.config 檔，使用文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="5153f-140">You can manually edit the machine.config file using a text editor.</span></span>  
  
#### <a name="manually-edit-the-machineconfig-file"></a><span data-ttu-id="5153f-141">手動編輯 machine.config 檔</span><span class="sxs-lookup"><span data-stu-id="5153f-141">Manually edit the machine.config file</span></span>  
  
1.  <span data-ttu-id="5153f-142">編輯位於 Microsoft .NET 組態資料夾中的 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="5153f-142">Edit the machine.config file located in the Microsoft .NET configuration folder.</span></span> <span data-ttu-id="5153f-143">若要這樣做，請按一下**啟動**，按一下 **執行**，輸入 notepad \<Windows 安裝路徑\>\Microsoft.NET\Framework\\< 版本\>\CONFIG\在 machine.config 中，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="5153f-143">To do this, click **Start**, click **Run**, type notepad \<Windows install path\>\Microsoft.NET\Framework\\<version\>\CONFIG\machine.config, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="5153f-144">更新 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="5153f-144">Update the machine.config file.</span></span> <span data-ttu-id="5153f-145">如果檔案不包含的 system.serviceModel 區段，結尾的組態檔，但在結尾根標記之前加入下列區段。</span><span class="sxs-lookup"><span data-stu-id="5153f-145">If the file does not contain a system.serviceModel section, add the following section at the end of the configuration file but before the closing root tag.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5153f-146">配接器的資訊來取代"myAdapterBinding"、 版本、 文化特性和其他組件特定的資訊。</span><span class="sxs-lookup"><span data-stu-id="5153f-146">Replace "myAdapterBinding", version, culture and other assembly-specific information with your adapter's information.</span></span>  
  
    ```  
    <system.serviceModel>  
      <extensions>  
        <bindingExtensions>  
            <add name="myAdapterBinding" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingCollectionElement,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken= fafafafafafafafa" />  
        </bindingExtensions>      <bindingElementExtensions>  
            <add name="echoAdapter" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingElementExtension,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken=37f23b4adb996dcf" />  
          </bindingElementExtensions>  
      </extensions>  
    </system.serviceModel>  
    ```  
  
     - <span data-ttu-id="5153f-147">或 -</span><span class="sxs-lookup"><span data-stu-id="5153f-147">OR -</span></span>  
  
     <span data-ttu-id="5153f-148">如果 machine.config 檔案中包含的 system.serviceModel 區段，判斷哪些項目遺漏，以及加入它們，配接器的資料來取代"MyAdapter 」 以及其他資訊。</span><span class="sxs-lookup"><span data-stu-id="5153f-148">If your machine.config file contains a system.serviceModel section, determine which elements are missing and add them, replacing "MyAdapter" and other information with your adapter's information.</span></span>  
  
    ```  
    <extensions>  
      <bindingExtensions>  
            <add name="myAdapterBinding" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingCollectionElement,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken= fafafafafafafafa" />  
      </bindingExtensions>  
          <bindingElementExtensions>  
            <add name="echoAdapter" type="Microsoft.Adapters.Samples.Echo.EchoAdapterBindingElementExtension,EchoAdapter, Version=0.0.0.0, Culture=neutral, PublicKeyToken=37f23b4adb996dcf" />  
          </bindingElementExtensions>  
    </extensions>  
    ```  
  
3.  <span data-ttu-id="5153f-149">關閉並儲存 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="5153f-149">Close and save the machine.config file.</span></span>  
  
 <span data-ttu-id="5153f-150">您也可以使用[服務組態編輯器](https://msdn.microsoft.com/library/ms732009.aspx)修改 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="5153f-150">You can also use the [Service Configuration Editor](https://msdn.microsoft.com/library/ms732009.aspx) to modify the machine.config file.</span></span>
  
#### <a name="edit-the-machineconfig-file-using-the-service-configuration-editor"></a><span data-ttu-id="5153f-151">編輯 machine.config 檔，使用 服務組態編輯器</span><span class="sxs-lookup"><span data-stu-id="5153f-151">Edit the machine.config file using the Service Configuration Editor</span></span>  
  
1.  <span data-ttu-id="5153f-152">開啟**服務組態編輯器**。</span><span class="sxs-lookup"><span data-stu-id="5153f-152">Open the **Service Configuration Editor**.</span></span> <span data-ttu-id="5153f-153">請參閱[服務組態編輯器](https://msdn.microsoft.com/library/ms732009.aspx)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5153f-153">See [Service Configuration Editor](https://msdn.microsoft.com/library/ms732009.aspx) for  more information.</span></span>
  
2.  <span data-ttu-id="5153f-154">在樹狀檢視窗格中 (標示為**組態**)，展開節點樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="5153f-154">In the tree view pane (labeled **Configuration**), expand the node tree.</span></span> <span data-ttu-id="5153f-155">按一下**進階**資料夾中，按一下 **延伸**資料夾，然後再選取繫結延伸項目。</span><span class="sxs-lookup"><span data-stu-id="5153f-155">Click the **Advanced** folder, click the **Extensions** folder, and then select the binding extensions element.</span></span>  
  
     <span data-ttu-id="5153f-156">![服務組態編輯器。] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/0a44a070-b788-4287-bd9e-c946fafcf11c.gif "0a44a070-b788-4287-bd9e-c946fafcf11c")</span><span class="sxs-lookup"><span data-stu-id="5153f-156">![Service configuration editor.](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/0a44a070-b788-4287-bd9e-c946fafcf11c.gif "0a44a070-b788-4287-bd9e-c946fafcf11c")</span></span>  
  
3.  <span data-ttu-id="5153f-157">建立新的繫結延伸模組。</span><span class="sxs-lookup"><span data-stu-id="5153f-157">Create a new binding extension.</span></span> <span data-ttu-id="5153f-158">按一下**新增** 按鈕以開啟 延伸模組**組態項目編輯器** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5153f-158">Click the **New** button to open the Extension **Configuration Element Editor** dialog box.</span></span> <span data-ttu-id="5153f-159">在**組態名稱**，輸入擴充功能，唯一的名稱，例如*MyAdapterExtension*。</span><span class="sxs-lookup"><span data-stu-id="5153f-159">In **Configuration Name**, enter a unique name for the extensions, for example *MyAdapterExtension*.</span></span>  
  
     <span data-ttu-id="5153f-160">![延伸模組組態元素編輯器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/1398a256-00fa-4591-99ee-54298a8cf6e3.gif "1398a256-00fa-4591-99ee-54298a8cf6e3")</span><span class="sxs-lookup"><span data-stu-id="5153f-160">![Extension configuration element editor](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/1398a256-00fa-4591-99ee-54298a8cf6e3.gif "1398a256-00fa-4591-99ee-54298a8cf6e3")</span></span>  
  
4.  <span data-ttu-id="5153f-161">按一下**類型**欄位，，然後按一下省略符號按鈕 (**...**) 若要開啟**繫結延伸型別瀏覽器** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5153f-161">Click the **Type** field, and then click the ellipsis button (**...**) to open the **Binding Extension Type Browser** dialog box.</span></span>  
  
5.  <span data-ttu-id="5153f-162">按一下 全域組件快取 (GAC) 圖示，列出 GAC 中的 Dll。</span><span class="sxs-lookup"><span data-stu-id="5153f-162">Click the global assembly cache (GAC) icon to list the DLLs in the GAC.</span></span>  
  
6.  <span data-ttu-id="5153f-163">按一下您的配接器組件。</span><span class="sxs-lookup"><span data-stu-id="5153f-163">Click your adapter assembly.</span></span>  
  
     <span data-ttu-id="5153f-164">![建置延伸模組類型瀏覽器。] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/7528e218-8930-4b01-b29d-8ec125a9b818.gif "7528e218-8930-4b01-b29d-8ec125a9b818")</span><span class="sxs-lookup"><span data-stu-id="5153f-164">![Building extension type browser.](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/7528e218-8930-4b01-b29d-8ec125a9b818.gif "7528e218-8930-4b01-b29d-8ec125a9b818")</span></span>  
  
7.  <span data-ttu-id="5153f-165">按一下**開啟**按鈕以選取的組件。</span><span class="sxs-lookup"><span data-stu-id="5153f-165">Click the **Open** button to select the assembly.</span></span>  
  
8.  <span data-ttu-id="5153f-166">在**繫結延伸型別瀏覽器**對話方塊方塊中，按一下 實作繫結的集合項目型別名稱。</span><span class="sxs-lookup"><span data-stu-id="5153f-166">In the **Binding Extension Type Browser** dialog box, click the type name that implements the binding collection element.</span></span>  
  
     <span data-ttu-id="5153f-167">![建置延伸模組類型瀏覽器。] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a5db2c6b-cdf7-4cd9-8cc4-6b0fb960b1ce.gif "a5db2c6b-cdf7-4cd9-8cc4-6b0fb960b1ce")</span><span class="sxs-lookup"><span data-stu-id="5153f-167">![Building extension type browser.](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a5db2c6b-cdf7-4cd9-8cc4-6b0fb960b1ce.gif "a5db2c6b-cdf7-4cd9-8cc4-6b0fb960b1ce")</span></span>  
  
9. <span data-ttu-id="5153f-168">按一下**開啟**按鈕以選取的類型。</span><span class="sxs-lookup"><span data-stu-id="5153f-168">Click the **Open** button to select the type.</span></span>  
  
10. <span data-ttu-id="5153f-169">按一下**確定**關閉**延伸模組組態元素編輯器** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5153f-169">Click **OK** to close the **Extension Configuration Element Editor** dialog box.</span></span>  
  
11. <span data-ttu-id="5153f-170">詳細資料窗格中**繫結延伸模組編輯器**，確認您的繫結延伸模組會出現。</span><span class="sxs-lookup"><span data-stu-id="5153f-170">In the details pane of the **Binding Extensions Editor**, verify that your binding extension appears.</span></span> <span data-ttu-id="5153f-171">在下圖中，MyAdapterExtension 反白顯示。</span><span class="sxs-lookup"><span data-stu-id="5153f-171">In the following figure, MyAdapterExtension is highlighted.</span></span>  
  
     <span data-ttu-id="5153f-172">![具有新增之延伸的服務組態編輯器。] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/955d37ea-cba5-49db-90de-0f8feb49c0e0.gif "955d37ea-cba5-49db-90de-0f8feb49c0e0")</span><span class="sxs-lookup"><span data-stu-id="5153f-172">![Service configuration editor with added extension.](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/955d37ea-cba5-49db-90de-0f8feb49c0e0.gif "955d37ea-cba5-49db-90de-0f8feb49c0e0")</span></span>  
  
12. <span data-ttu-id="5153f-173">關閉**服務組態編輯器**。</span><span class="sxs-lookup"><span data-stu-id="5153f-173">Close the **Service Configuration Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5153f-174">請參閱</span><span class="sxs-lookup"><span data-stu-id="5153f-174">See Also</span></span>  
 [<span data-ttu-id="5153f-175">部署配接器使用 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="5153f-175">Deploy an adapter using the WCF LOB adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md)