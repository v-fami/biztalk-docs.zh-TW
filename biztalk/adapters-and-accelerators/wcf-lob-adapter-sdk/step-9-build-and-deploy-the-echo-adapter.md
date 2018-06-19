---
title: 步驟 9： 建置並部署回應配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1ead10ab-1acf-47c5-ad16-dc6938601906
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b9a4985629427e44b8ca85f324c89ab719cf249
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967236"
---
# <a name="step-9-build-and-deploy-the-echo-adapter"></a><span data-ttu-id="2614a-102">步驟 9： 建置並部署回應配接器</span><span class="sxs-lookup"><span data-stu-id="2614a-102">Step 9: Build and Deploy the Echo Adapter</span></span>
<span data-ttu-id="2614a-103">![步驟 9 / 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-9of9.gif "Step_9of9")</span><span class="sxs-lookup"><span data-stu-id="2614a-103">![Step 9 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-9of9.gif "Step_9of9")</span></span>  
  
 <span data-ttu-id="2614a-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="2614a-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="2614a-105">在此步驟中，您將會執行部署回應配接器所需的工作。</span><span class="sxs-lookup"><span data-stu-id="2614a-105">In this step, you will perform the tasks necessary to deploy the Echo Adapter.</span></span> <span data-ttu-id="2614a-106">這項作業包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="2614a-106">This involves all of the following:</span></span>  
  
-   <span data-ttu-id="2614a-107">建立強式名稱的檔案，並將它指派給回應配接器組件</span><span class="sxs-lookup"><span data-stu-id="2614a-107">Create a strong name file and assign it to the Echo Adapter assembly</span></span>  
  
-   <span data-ttu-id="2614a-108">建立回應的配接器</span><span class="sxs-lookup"><span data-stu-id="2614a-108">Build the Echo Adapter</span></span>  
  
-   <span data-ttu-id="2614a-109">發行至 GAC 的組件</span><span class="sxs-lookup"><span data-stu-id="2614a-109">Publish the assembly into the GAC</span></span>  
  
-   <span data-ttu-id="2614a-110">註冊以回應配接器[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2614a-110">Register the Echo Adapter with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2614a-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="2614a-111">Prerequisites</span></span>  
 <span data-ttu-id="2614a-112">若要成功完成此步驟中，您應該熟悉強式名稱的檔案和 GAC。</span><span class="sxs-lookup"><span data-stu-id="2614a-112">To successfully complete this step, you should be familiar with strong name files and the GAC.</span></span> <span data-ttu-id="2614a-113">基本的了解[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]組態會有所助益，但非必要。</span><span class="sxs-lookup"><span data-stu-id="2614a-113">A basic understanding of [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] configuration is helpful but not required.</span></span>  
  
### <a name="to-assign-a-strong-name-to-your-assembly"></a><span data-ttu-id="2614a-114">指派強式名稱給組件</span><span class="sxs-lookup"><span data-stu-id="2614a-114">To assign a strong name to your assembly</span></span>  
  
1.  <span data-ttu-id="2614a-115">在 [方案總管] 中，以滑鼠右鍵按一下**EchoAdapter**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="2614a-115">In Solution Explorer, right-click the **EchoAdapter** project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="2614a-116">在 [EchoAdapter 屬性頁] 對話方塊中，選取**簽署**從左窗格。</span><span class="sxs-lookup"><span data-stu-id="2614a-116">In the EchoAdapter Property Pages dialog box, select **Signing** from the left pane.</span></span>  
  
3.  <span data-ttu-id="2614a-117">按一下**簽署組件** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2614a-117">Click the **Sign the assembly** tab.</span></span>  
  
4.  <span data-ttu-id="2614a-118">選擇**\<新...\>** 強式名稱的檔案。</span><span class="sxs-lookup"><span data-stu-id="2614a-118">Choose **\<new…\>** for the strong name file.</span></span> <span data-ttu-id="2614a-119">出現提示時輸入檔案名稱，輸入**EchoAdapter.snk**，取消選取保護我的金鑰檔使用的密碼選項，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="2614a-119">When prompted for a file name, type **EchoAdapter.snk**,deselect the protect my key file with a password option, then click **OK**.</span></span>  
  
5.  <span data-ttu-id="2614a-120">按一下**應用程式** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2614a-120">Click the **Application** tab.</span></span>  
  
6.  <span data-ttu-id="2614a-121">將組件名稱變更為**Microsoft.Adapters.Samples.EchoV2**。</span><span class="sxs-lookup"><span data-stu-id="2614a-121">Change the assembly name to **Microsoft.Adapters.Samples.EchoV2**.</span></span>  
  
7.  <span data-ttu-id="2614a-122">按一下**檔案**Visual Studio 功能表上選擇 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="2614a-122">Click **File** on the Visual Studio menu then choose **Save All**.</span></span>  
  
### <a name="to-build-and-deploy-echo-adapter"></a><span data-ttu-id="2614a-123">若要建置和部署回應配接器</span><span class="sxs-lookup"><span data-stu-id="2614a-123">To build and deploy Echo Adapter</span></span>  
  
1.  <span data-ttu-id="2614a-124">在 [方案總管] 中，以滑鼠右鍵按一下**EchoAdapter**專案，然後再按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="2614a-124">In Solution Explorer, right-click the **EchoAdapter** project, and then click **Build**.</span></span> <span data-ttu-id="2614a-125">如果組建沒有成功，修正任何錯誤，然後再次嘗試重建回應配接器。</span><span class="sxs-lookup"><span data-stu-id="2614a-125">If the build does not succeed, fix any errors and try rebuilding the Echo Adapter.</span></span>  
  
2.  <span data-ttu-id="2614a-126">開啟 Visual Studio 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="2614a-126">Open a Visual Studio command prompt.</span></span>  
  
3.  <span data-ttu-id="2614a-127">輸入以下命令：</span><span class="sxs-lookup"><span data-stu-id="2614a-127">Type the following command:</span></span>  
  
     <span data-ttu-id="2614a-128">**gacutil.exe /if"\<**  *路徑 assembly\Microsoft.Adapters.Samples.EchoV2.dll*  **\>"**</span><span class="sxs-lookup"><span data-stu-id="2614a-128">**gacutil.exe /if "\<** *path to assembly\Microsoft.Adapters.Samples.EchoV2.dll* **\>"**</span></span>  
  
     <span data-ttu-id="2614a-129">這會將組件安裝至 GAC，覆寫任何同名的現有組件。</span><span class="sxs-lookup"><span data-stu-id="2614a-129">This installs the assembly to the GAC, overwriting any existing assembly that has the same assembly name.</span></span>  
  
### <a name="to-register-the-echo-adapter-with-windows-communication-foundation"></a><span data-ttu-id="2614a-130">Windows Communication foundation 註冊回應配接器</span><span class="sxs-lookup"><span data-stu-id="2614a-130">To register the Echo Adapter with Windows Communication Foundation</span></span>  
  
1.  <span data-ttu-id="2614a-131">編輯位於 Microsoft .NET 組態資料夾中的 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="2614a-131">Edit the machine.config file located in the Microsoft .NET configuration folder.</span></span> <span data-ttu-id="2614a-132">若要這樣做，請按一下**啟動**，按一下 **執行**，型別**記事本\<Windows 安裝路徑\>\Microsoft.NET\Framework\\< 版本\>\CONFIG\machine.config**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="2614a-132">To do this, click **Start**, click **Run**, type **notepad \<Windows install path\>\Microsoft.NET\Framework\\<version\>\CONFIG\machine.config**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="2614a-133">更新 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="2614a-133">Update the machine.config file.</span></span> <span data-ttu-id="2614a-134">如果 machine.config 未包含的 system.serviceModel 區段，結尾的組態檔，但在結尾根標記之前加入下列區段。</span><span class="sxs-lookup"><span data-stu-id="2614a-134">If your machine.config does not contain a system.serviceModel section, add the following section at the end of the configuration file but before the closing root tag.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2614a-135">配接器的資訊來取代版本、 文化特性、 公開金鑰語彙基元和其他組件特定的資訊。</span><span class="sxs-lookup"><span data-stu-id="2614a-135">Replace the version, culture, public key token and other assembly-specific information with your adapter's information.</span></span>  
  
    ```  
    <system.serviceModel>  
      <client>  
        <endpoint binding="echoAdapterBindingV2" contract="IMetadataExchange"  
          name="echov2" />  
      </client>  
      <extensions>  
        <bindingElementExtensions>  
          <add name="echoAdapterV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingElementExtensionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
        </bindingElementExtensions>  
        <bindingExtensions>  
          <add name="echoAdapterBindingV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingCollectionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
        </bindingExtensions>  
      </extensions>  
    </system.serviceModel>  
    ```  
  
     - <span data-ttu-id="2614a-136">或 -</span><span class="sxs-lookup"><span data-stu-id="2614a-136">OR -</span></span>  
  
     <span data-ttu-id="2614a-137">如果 machine.config 包含 system.serviceModel 區段，判斷遺失哪些項目，並將其新增。</span><span class="sxs-lookup"><span data-stu-id="2614a-137">If your machine.config contains a system.serviceModel section, determine which elements are missing and add them.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2614a-138">配接器的資訊來取代版本、 文化特性、 公開金鑰語彙基元和其他組件特定的資訊。</span><span class="sxs-lookup"><span data-stu-id="2614a-138">Replace the version, culture, public key token and other assembly-specific information with your adapter's information.</span></span>  
  
    ```  
    <client>  
      <endpoint binding="echoAdapterBindingV2" contract="IMetadataExchange"  
        name="echov2" />  
    </client>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="echoAdapterV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingElementExtensionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
      </bindingElementExtensions>  
      <bindingExtensions>  
        <add name="echoAdapterBindingV2" type="Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingCollectionElement,Microsoft.Adapters.Samples.EchoV2, Version=1.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxxxxx" />  
      </bindingExtensions>  
    </extensions>  
    ```  
  
3.  <span data-ttu-id="2614a-139">儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="2614a-139">Save the machine.config file.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="2614a-140">我剛剛做什麼？</span><span class="sxs-lookup"><span data-stu-id="2614a-140">What Did I Just Do?</span></span>  
 <span data-ttu-id="2614a-141">在此回應配接器教學課程的最後一個步驟中，您加入回應配接器的強式名稱、 建置和部署配接器，然後修改 Machine.config 包含配接器的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2614a-141">In this final step of the Echo Adapter tutorial, you added a strong name to the Echo Adapter, built and deployed the adapter, then modified Machine.config to include information about the adapter.</span></span> <span data-ttu-id="2614a-142">此時，回應配接器應該可供取用應用程式。</span><span class="sxs-lookup"><span data-stu-id="2614a-142">At this point, the Echo Adapter should be available to consuming applications.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2614a-143">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2614a-143">Next Steps</span></span>  
 <span data-ttu-id="2614a-144">完成本教學課程。</span><span class="sxs-lookup"><span data-stu-id="2614a-144">This tutorial is complete.</span></span> <span data-ttu-id="2614a-145">如果您想要測試的.NET 專案中回應配接器功能，請參閱[教學課程 2： 使用回應配接器從.NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)。</span><span class="sxs-lookup"><span data-stu-id="2614a-145">If you want to test Echo Adapter functionality in a .NET project, see [Tutorial 2: Consume the Echo Adapter from .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2614a-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="2614a-146">See Also</span></span>  
 <span data-ttu-id="2614a-147">[步驟 8： 為回應配接器實作的同步輸入處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="2614a-147">[Step 8: Implement the Synchronous Inbound Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="2614a-148">教學課程 2：從 .NET 使用 Echo 配接器</span><span class="sxs-lookup"><span data-stu-id="2614a-148">Tutorial 2: Consume the Echo Adapter from .NET</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)