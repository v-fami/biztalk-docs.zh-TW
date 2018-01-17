---
title: "配接器登錄檔案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6750f0ed-4411-4a63-a7fe-f66132cd1e22
caps.latest.revision: "35"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c38d00cbaf5d34aa880f5efd1d9e9a59d59c4e0
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="adapter-registration-file"></a><span data-ttu-id="3889b-102">配接器登錄檔案</span><span class="sxs-lookup"><span data-stu-id="3889b-102">Adapter Registration File</span></span>
<span data-ttu-id="3889b-103">順利建立自訂配接器程式碼之後，必須向 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 註冊。</span><span class="sxs-lookup"><span data-stu-id="3889b-103">After the custom adapter code has been successfully built it must be registered with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="3889b-104">若要執行此作業，可將登錄更新為適當配接器設定。</span><span class="sxs-lookup"><span data-stu-id="3889b-104">You do this by updating the registry with the appropriate adapter settings.</span></span> <span data-ttu-id="3889b-105">您可以手動寫入登錄檔案，但由於輸入精確和複雜資訊容易發生錯誤，</span><span class="sxs-lookup"><span data-stu-id="3889b-105">You can manually write a registry file, but this is prone to errors due to the preciseness and complexity of the information that you need to enter.</span></span> <span data-ttu-id="3889b-106">更好的選擇是要執行配接器登錄精靈。</span><span class="sxs-lookup"><span data-stu-id="3889b-106">A better decision is to run the Adapter Registry Wizard.</span></span> <span data-ttu-id="3889b-107">配接器登錄精靈 」 可讓您所有相同選項與從頭建立登錄檔，並降低檔案發生錯誤的可能性。</span><span class="sxs-lookup"><span data-stu-id="3889b-107">The Adapter Registry Wizard gives you all the same options as creating a registry file from scratch, and reduces the likelihood of errors in the file.</span></span> <span data-ttu-id="3889b-108">如需配接器登錄精靈 」 的詳細資訊，請參閱[配接器登錄精靈](../core/adapter-registry-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="3889b-108">For more information about the Adapter Registry Wizard, see [Adapter Registry Wizard](../core/adapter-registry-wizard.md).</span></span>  
  
 <span data-ttu-id="3889b-109">StaticAdapterManagement.reg 和 DynamicAdapterManagement.reg 檔案位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk Server\SDK\Samples\AdaptersDevelopment\File 配接器。</span><span class="sxs-lookup"><span data-stu-id="3889b-109">The StaticAdapterManagement.reg file and DynamicAdapterManagement.reg file are located at *\<drive\>*:\Program Files\Microsoft BizTalk Server\SDK\Samples\AdaptersDevelopment\File Adapter.</span></span> <span data-ttu-id="3889b-110">當您執行其中一個檔案 (按兩下檔案，或以滑鼠右鍵按一下它，並選取 **合併**)，它向登錄註冊範例 file 配接器，並將組件安裝到全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="3889b-110">When you run one of these files (you can double-click it or right-click it and and select **Merge**), it registers the sample file adapter with the registry and installs the assembly into the global assembly cache.</span></span> <span data-ttu-id="3889b-111">若要註冊自訂配接器最好的選擇是使用配接器登錄精靈 」 建立新的登錄檔。</span><span class="sxs-lookup"><span data-stu-id="3889b-111">To register your custom adapter the best option is to create a new registry file by using the Adapter Registry Wizard.</span></span> <span data-ttu-id="3889b-112">如果自訂靜態配接器與範例配接器相似，並且您決定修改現有的登錄檔案，請開啟 StaticAdapterManagement.reg 檔案並修改下列屬性：</span><span class="sxs-lookup"><span data-stu-id="3889b-112">If your custom static adapter is similar to the sample adapter, and you decide to modify the existing registry file instead, open and modify the following properties in the StaticAdapterManagement.reg file:</span></span>  
  
-   <span data-ttu-id="3889b-113">**條件約束**</span><span class="sxs-lookup"><span data-stu-id="3889b-113">**Constraints**</span></span>  
  
-   <span data-ttu-id="3889b-114">**InboundTypeName**</span><span class="sxs-lookup"><span data-stu-id="3889b-114">**InboundTypeName**</span></span>  
  
-   <span data-ttu-id="3889b-115">**InboundAssemblyPath**</span><span class="sxs-lookup"><span data-stu-id="3889b-115">**InboundAssemblyPath**</span></span>  
  
-   <span data-ttu-id="3889b-116">**OutboundTypeName**</span><span class="sxs-lookup"><span data-stu-id="3889b-116">**OutboundTypeName**</span></span>  
  
-   <span data-ttu-id="3889b-117">**OutboundAssemblyPath**</span><span class="sxs-lookup"><span data-stu-id="3889b-117">**OutboundAssemblyPath**</span></span>  
  
-   <span data-ttu-id="3889b-118">**AdapterMgmtTypeName**</span><span class="sxs-lookup"><span data-stu-id="3889b-118">**AdapterMgmtTypeName**</span></span>  
  
-   <span data-ttu-id="3889b-119">**AdapterMgmtAssemblyPath**</span><span class="sxs-lookup"><span data-stu-id="3889b-119">**AdapterMgmtAssemblyPath**</span></span>  
  
-   <span data-ttu-id="3889b-120">**PropertyNameSpace**</span><span class="sxs-lookup"><span data-stu-id="3889b-120">**PropertyNameSpace**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3889b-121">如 **OutboundAssemblyPath** 和 **AdapterMgmtAssemblyPath** 建議，您的本機路徑中包含的屬性值，因為安裝在不同伺服器位置時，組態可能會中斷。</span><span class="sxs-lookup"><span data-stu-id="3889b-121">For **OutboundAssemblyPath** and **AdapterMgmtAssemblyPath** we recommend that you not include the local path in the property value, because the configuration could break when installed on different server locations.</span></span> <span data-ttu-id="3889b-122">更好的選擇是使用強式名稱，並將它安裝在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="3889b-122">A better choice is to use a strong name and install it in the global assembly cache.</span></span>  
  
 <span data-ttu-id="3889b-123">有兩個選擇可指定實作配接器接收器、配接器傳輸器和配接器管理的 .NET 類型：</span><span class="sxs-lookup"><span data-stu-id="3889b-123">You have two options for specifying the .NET type that implements the adapter receiver, adapter transmitter, and adapter management:</span></span>  
  
1.  <span data-ttu-id="3889b-124">配接器安裝至資料夾，並指定 * TypeName 和 \*AssemblyPath 其中 \*TypeName 是型別。類別的 FullName 和 \*AssemblyPath 是組件的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="3889b-124">Install the adapter to a folder and specify *TypeName and \*AssemblyPath where \*TypeName is type.FullName of the class and \*AssemblyPath is the path and file name of the assembly.</span></span>  
  
2.  <span data-ttu-id="3889b-125">在全域組件快取中安裝配接器，只指定 * TypeName 其中 \*TypeName 是型別。AssemblyQualifiedName 的類別。</span><span class="sxs-lookup"><span data-stu-id="3889b-125">Install the adapter in the global assembly cache and specify just *TypeName where \*TypeName is type.AssemblyQualifiedName of the class.</span></span> <span data-ttu-id="3889b-126">這是建議選項。</span><span class="sxs-lookup"><span data-stu-id="3889b-126">This is the recommended option.</span></span>  
  
 <span data-ttu-id="3889b-127">所有配接器都必須具有下列指定之 GUID 的登錄機碼：</span><span class="sxs-lookup"><span data-stu-id="3889b-127">All adapters must have the following registry keys with the specified GUID:</span></span>  
  
-   <span data-ttu-id="3889b-128">**實作類別\\{7F46FC3E-3C2C-405B-A47F-8D17942BA8F9}**</span><span class="sxs-lookup"><span data-stu-id="3889b-128">**Implemented Categories\\{7F46FC3E-3C2C-405B-A47F-8D17942BA8F9}**</span></span>  
  
-   <span data-ttu-id="3889b-129">**"InboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A281}"**</span><span class="sxs-lookup"><span data-stu-id="3889b-129">**"InboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A281}"**</span></span>  
  
-   <span data-ttu-id="3889b-130">**"OutboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A283}"**</span><span class="sxs-lookup"><span data-stu-id="3889b-130">**"OutboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A283}"**</span></span>  
  
-   <span data-ttu-id="3889b-131">**"ReceiveLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A280}"**</span><span class="sxs-lookup"><span data-stu-id="3889b-131">**"ReceiveLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A280}"**</span></span>  
  
-   <span data-ttu-id="3889b-132">**"TransmitLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A282}"**</span><span class="sxs-lookup"><span data-stu-id="3889b-132">**"TransmitLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A282}"**</span></span>  
  
 <span data-ttu-id="3889b-133">對於傳送和接收處理常式以及位置屬性頁，以配接器架構為基礎的配接器都必須使用這些特定的 GUID。</span><span class="sxs-lookup"><span data-stu-id="3889b-133">Adapters based on the adapter framework must use these specific GUIDS for send and receive handler and location property pages.</span></span> <span data-ttu-id="3889b-134">請注意，是否配接器是僅限傳送配接器只要 **OutboundProtocol_PageProv**和 **TransmitLocation_PageProv**Guid。</span><span class="sxs-lookup"><span data-stu-id="3889b-134">Note that if an adapter is a send-only adapter it just needs the **OutboundProtocol_PageProv**and **TransmitLocation_PageProv**GUIDs.</span></span> <span data-ttu-id="3889b-135">同樣地僅接收配接器只需要 **InboundProtocol_PageProv** 和 **ReceiveLocation_PageProv** Guid。</span><span class="sxs-lookup"><span data-stu-id="3889b-135">Similarly a receive-only adapter merely requires the **InboundProtocol_PageProv** and **ReceiveLocation_PageProv** GUIDs.</span></span>  
  
 <span data-ttu-id="3889b-136">下列程式碼來自 StaticAdapterManagement.reg 檔案，而來自 DynamicAdapterManagement.reg 檔案的程式碼幾乎完全相同。</span><span class="sxs-lookup"><span data-stu-id="3889b-136">The following code is from the StaticAdapterManagement.reg file, and the code for the DynamicAdapterManagement.reg file is almost identical.</span></span> <span data-ttu-id="3889b-137">如需每個登錄屬性的詳細資訊，請參閱[登錄配接器](../core/registering-an-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="3889b-137">For more information about each of the registry properties, see [Registering an Adapter](../core/registering-an-adapter.md).</span></span> <span data-ttu-id="3889b-138">變更登錄檔案之後，請儲存並執行檔案。</span><span class="sxs-lookup"><span data-stu-id="3889b-138">After making the changes to the registry file, save the file and run it.</span></span>  
  
```  
Windows Registry Editor Version 5.00  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}]  
@="Static DotNetFile Adapter"  
"AppID"="{12A6EBAA-CF68-4B58-B36E-A5A19B22C04E}"  
  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}\BizTalk]  
@="BizTalk"  
"TransportType"="Static DotNetFile"  
"Constraints"=dword:00003C0b  
  
"InboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A281}"  
"OutboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A283}"  
"ReceiveLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A280}"  
"TransmitLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A282}"  
  
"InboundEngineCLSID"="{3D4B599E-2202-4bbb-9FC6-7ACA3906E5DE}"  
"InboundTypeName"="Microsoft.BizTalk.SDKSamples.Adapters.DotNetFileReceiver""InboundAssemblyPath"="C:\\Program Files\\Microsoft BizTalk Server <version>\\SDK\\Samples\\AdaptersDevelopment\\File Adapter\\Runtime\\bin\\Debug\\Microsoft.BizTalk.SDKSamples.Adapters.DotNetFile.Runtime.dll"  
"OutboundEngineCLSID"="{024DB758-AAF9-415e-A121-4AC245DD49EC}"  
"OutboundTypeName"="Microsoft.BizTalk.SDKSamples.Adapters.DotNetFileTransmitter""OutboundAssemblyPath"="C:\\Program Files\\Microsoft BizTalk Server <version>\SDK\\Samples\\AdaptersDevelopment\\File Adapter\\Runtime\\bin\\Debug\\Microsoft.BizTalk.SDKSamples.Adapters.DotNetFile.Runtime.dll""AdapterMgmtTypeName"="Microsoft.BizTalk.SDKSamples.Adapters.Designtime.StaticAdapterManagement""AdapterMgmtAssemblyPath"="C:\\Program Files\\Microsoft BizTalk Server <version>\SDK\\Samples\\AdaptersDevelopment\\File Adapter\\Design Time\\Adapter Management\\bin\\Debug\\Microsoft.BizTalk.SDKSamples.Adapters.DotNetFile.Designtime.dll""PropertyNameSpace"="http://schemas.microsoft.com/BizTalk/2003/SDK_Samples/Messaging/Transports/dotnetfile-properties"  
"AliasesXML"="<AdapterAliasList><AdapterAlias>DotNetFILE://</AdapterAlias></AdapterAliasList>"  
"ReceiveHandlerPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
"SendHandlerPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
"ReceiveLocationPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
"SendLocationPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}\Implemented Categories]  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}\Implemented Categories\{7F46FC3E-3C2C-405B-A47F-8D17942BA8F9}]  
```  
  
### <a name="to-register-the-static-sample-adapter"></a><span data-ttu-id="3889b-139">若要註冊靜態範例配接器</span><span class="sxs-lookup"><span data-stu-id="3889b-139">To register the static sample adapter</span></span>  
  
1.  <span data-ttu-id="3889b-140">請完成下列程序，以執行 SDK 中的 FILE 配接器範例。</span><span class="sxs-lookup"><span data-stu-id="3889b-140">Complete the procedure to run the file adapter sample in the SDK.</span></span> <span data-ttu-id="3889b-141">如需詳細資訊，請參閱[File 配接器 （BizTalk Server 範例）](../core/file-adapter-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="3889b-141">For more information, see [File Adapter (BizTalk Server Sample)](../core/file-adapter-biztalk-server-sample.md).</span></span>  
  
2.  <span data-ttu-id="3889b-142">按一下  **啟動**, ，指向  **所有程式**, ，指向 **附屬應用程式**, ，然後按一下  **Windows 檔案總管**。</span><span class="sxs-lookup"><span data-stu-id="3889b-142">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.</span></span>  
  
3.  <span data-ttu-id="3889b-143">瀏覽至安裝磁碟機，以便讓 BizTalk Server，然後瀏覽 **<**  `drive` **>: \Program Files\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\SDK\Samples\AdaptersUsage\File 配接器**。</span><span class="sxs-lookup"><span data-stu-id="3889b-143">Navigate to the installation drive for BizTalk Server, and then navigate to **<**`drive`**>:\Program Files\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**\SDK\Samples\AdaptersUsage\File Adapter**.</span></span>  
  
4.  <span data-ttu-id="3889b-144">若要將範例配接器新增至登錄中，按兩下 **StaticAdapterManagement.reg**。(如果您想要將動態 file 配接器新增至登錄，請執行**DynamicAdapterManagement.reg**改為與該檔案 everywhere else 依適當情況使用。)</span><span class="sxs-lookup"><span data-stu-id="3889b-144">To add the sample adapter to the registry, double-click **StaticAdapterManagement.reg**. (If you want to add the dynamic file adapter to the registry run **DynamicAdapterManagement.reg** instead and use that file everywhere else as appropriate.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3889b-145">如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不是安裝在電腦的磁碟機 C，您必須將 StaticAdapterManagement.reg 檔案修改為正確的安裝路徑。</span><span class="sxs-lookup"><span data-stu-id="3889b-145">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is not installed on drive C of your computer, you must modify the StaticAdapterManagement.reg file with the appropriate installation path.</span></span> <span data-ttu-id="3889b-146">C︰ 搜尋該檔案，並取代正確的安裝磁碟機。</span><span class="sxs-lookup"><span data-stu-id="3889b-146">Search the file for C: and replace it with the correct installation drive.</span></span>  
  
5.  <span data-ttu-id="3889b-147">在 **登錄編輯程式** 對話方塊中，按一下 **是** 以將範例配接器新增至登錄，然後按一下 **確定** 以關閉對話方塊，確認資訊已新增至登錄。</span><span class="sxs-lookup"><span data-stu-id="3889b-147">In the **Registry Editor** dialog box, click **Yes** to add the sample adapter to the registry, and then click **OK** to close the dialog box, verifying that the information was added to the registry.</span></span>  
  
6.  <span data-ttu-id="3889b-148">若要關閉 Windows 檔案總管，在 **檔案** ] 功能表上，按一下 [ **關閉**。</span><span class="sxs-lookup"><span data-stu-id="3889b-148">To close Windows Explorer, on the **File** menu, click **Close**.</span></span>  
  
     <span data-ttu-id="3889b-149">現在範例靜態配接器已經在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中註冊。</span><span class="sxs-lookup"><span data-stu-id="3889b-149">The sample static adapter is now registered with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>