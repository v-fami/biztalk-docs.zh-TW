---
title: File 配接器 （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, File adapters
- File adapters, examples
ms.assetid: d59cecb4-6353-44d5-b8d6-316446758536
caps.latest.revision: 46
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de68c57c6b435f85edf630a7b224c5d58ffd0cd6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "26010335"
---
# <a name="file-adapter-biztalk-server-sample"></a><span data-ttu-id="b8ed4-102">File 配接器 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="b8ed4-102">File Adapter (BizTalk Server Sample)</span></span>
<span data-ttu-id="b8ed4-103">File 配接器範例是以 Microsoft Visual C#.NET 才能使用 Microsoft BizTalk Server 撰寫的。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-103">The File Adapter sample is written in Microsoft Visual C# .NET to work with Microsoft BizTalk Server.</span></span> <span data-ttu-id="b8ed4-104">此範例提供可建置動態或靜態配接器的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-104">It provides code to build either a dynamic or a static adapter.</span></span>  <span data-ttu-id="b8ed4-105">不過，下列程序僅概述靜態配接器。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-105">However, the following procedure only outlines the static adapter.</span></span> <span data-ttu-id="b8ed4-106">靜態配接器具有一組靜態結構描述，且沒有自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-106">A static adapter is an adapter with a static set of schemas and no custom user interface.</span></span> <span data-ttu-id="b8ed4-107">動態配接器具有自訂使用者介面，並且可能有一組動態結構描述。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-107">A dynamic adapter has a custom user interface and potentially a dynamic set of schemas.</span></span> <span data-ttu-id="b8ed4-108">靜態和動態配接器都使用「新增配接器精靈」將結構描述新增至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-108">Both static and dynamic adapters use the Add Adapter Wizard to add their schemas to a BizTalk project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8ed4-109">File 配接器範例不是原生 FILE 配接器隨附於 BizTalk Server 相同。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-109">The File adapter sample is not the same as the native FILE adapter that ships with BizTalk Server.</span></span> <span data-ttu-id="b8ed4-110">因此，使用此範例選取傳輸類型時，請選取「靜態」，不要選取 FILE。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-110">Thus when selecting the transport type in using this sample select "static" instead of FILE.</span></span>  
  
 <span data-ttu-id="b8ed4-111">具有自訂使用者介面並且可能有一組動態結構描述的動態配接器，在配接器管理方面將需要額外的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-111">The dynamic adapter with a custom user interface and potentially dynamic set of schemas will require additional code in the adapter management side.</span></span> <span data-ttu-id="b8ed4-112">若要進一步了解使用動態結構描述集，請參閱[動態設計階段配接器組態](../core/dynamic-design-time-adapter-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-112">To better understand use of the dynamic set of schemas, see [Dynamic Design-Time Adapter Configuration](../core/dynamic-design-time-adapter-configuration.md).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="b8ed4-113">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="b8ed4-113">What This Sample Does</span></span>  
 <span data-ttu-id="b8ed4-114">此範例配接器會從檔案資料夾複製檔案，並當做訊息提交至 BizTalk，或者從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 取得訊息並放置在檔案資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-114">The sample adapter copies files from a file folder, submits to BizTalk as messages, or takes messages from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and drops to a file folder.</span></span> <span data-ttu-id="b8ed4-115">它提供可建置動態或靜態配接器的程式碼；不過，下列程序僅概述靜態配接器。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-115">It provides code to build either a dynamic or a static adapter; however, the following procedure only outlines the static adapter.</span></span> <span data-ttu-id="b8ed4-116">靜態配接器具有一組靜態結構描述，且沒有自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-116">A static adapter is an adapter with a static set of schemas and no custom user interface.</span></span> <span data-ttu-id="b8ed4-117">動態配接器具有自訂使用者介面，並且可能有一組動態結構描述。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-117">A dynamic adapter has a custom user interface and potentially a dynamic set of schemas.</span></span> <span data-ttu-id="b8ed4-118">靜態和動態配接器都使用「新增配接器精靈」將結構描述新增至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-118">Both static and dynamic adapters use the Add Adapter Wizard to add their schemas to a BizTalk project.</span></span>  
  
 <span data-ttu-id="b8ed4-119">您可以將範例 FILE 配接器當做範本，建立其他自訂配接器。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-119">You can use the sample file adapter as a template on which to create other custom adapters.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="b8ed4-120">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="b8ed4-120">Where to Find This Sample</span></span>  
 <span data-ttu-id="b8ed4-121">\<*範例路徑*\>**\AdaptersDevelopment\File 配接器**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-121">\<*Samples Path*\>**\AdaptersDevelopment\File Adapter**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8ed4-122">預設位置\<*範例路徑*\>是 *%programfiles%* \Microsoft BizTalk Server\SDK\Samples 時執行 32 位元的電腦上安裝 BizTalk ServerWindows 版本。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-122">The default location for \<*Samples Path*\> is *%ProgramFiles%* \Microsoft BizTalk Server\SDK\Samples when BizTalk Server is installed on a computer running a 32-bit version of Windows.</span></span> <span data-ttu-id="b8ed4-123">預設位置\<*範例路徑*\>是 *%programfiles （x86） %* \Microsoft BizTalk Server\SDK\Samples 時執行 64 位的電腦上安裝 BizTalk Server位元版本的 Windows。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-123">The default location for \<*Samples Path*\> is *%ProgramFiles(x86)%* \Microsoft BizTalk Server\SDK\Samples when BizTalk Server is installed on a computer running a 64-bit version of Windows.</span></span> <span data-ttu-id="b8ed4-124">若要判斷相關聯的值 *%programfiles%* 或 *%programfiles （x86） %* 環境變數類型 **echo %programfiles%** 或 **echo %programfiles （x86） %** 在命令提示字元並按下 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-124">To determine the values associated with the *%ProgramFiles%* or *%ProgramFiles(x86)%* environment variables type **echo %ProgramFiles%** or **echo %ProgramFiles(x86)%** at a command prompt and press ENTER.</span></span> <span data-ttu-id="b8ed4-125">如果在 64 位元作業系統上執行此範例，您必須變更任何的.reg 檔案中的所有參考 **%programfiles%** 至 **%programfiles （x86） %** 之前執行.reg 檔案。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-125">If running this sample on a 64-bit operating system, you will need to change all references in any of the .reg files from **%ProgramFiles%** to **%ProgramFiles(x86)%** before running the .reg files.</span></span>  
  
 <span data-ttu-id="b8ed4-126">下表顯示此範例中的檔案，並說明其用途。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-126">The following tables show the files in this sample and describe their purpose.</span></span>  
  
|<span data-ttu-id="b8ed4-127">\File Adapter 檔案</span><span class="sxs-lookup"><span data-stu-id="b8ed4-127">\File Adapter files</span></span>|<span data-ttu-id="b8ed4-128">Description</span><span class="sxs-lookup"><span data-stu-id="b8ed4-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="b8ed4-129">\BizTalk Project 檔案</span><span class="sxs-lookup"><span data-stu-id="b8ed4-129">\BizTalk Project files</span></span>|<span data-ttu-id="b8ed4-130">包含配接器控管專案，可用來測試範例配接器。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-130">Contains the adapter harness project, used to test the sample adapter.</span></span>|  
|<span data-ttu-id="b8ed4-131">\Design Time 檔案</span><span class="sxs-lookup"><span data-stu-id="b8ed4-131">\Design Time files</span></span>|<span data-ttu-id="b8ed4-132">包含設計階段和管理專案 (AdapterManagement.csproj)。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-132">Contains the design time and management project (AdapterManagement.csproj).</span></span>|  
|<span data-ttu-id="b8ed4-133">\Runtime 檔案</span><span class="sxs-lookup"><span data-stu-id="b8ed4-133">\Runtime files</span></span>|<span data-ttu-id="b8ed4-134">包含執行階段檔案複製接收和傳輸專案 (DotNetFile.csproj)。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-134">Contains the run-time file-copy receive and transmit projects (DotNetFile.csproj).</span></span>|  
|<span data-ttu-id="b8ed4-135">DynamicAdapterManagement.reg</span><span class="sxs-lookup"><span data-stu-id="b8ed4-135">DynamicAdapterManagement.reg</span></span>|<span data-ttu-id="b8ed4-136">註冊範例動態配接器。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-136">Registers the sample dynamic adapter.</span></span>|  
|<span data-ttu-id="b8ed4-137">Instance.xml</span><span class="sxs-lookup"><span data-stu-id="b8ed4-137">Instance.xml</span></span>|<span data-ttu-id="b8ed4-138">透過 FILE 配接器傳遞的範例檔案。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-138">Sample file to pass through the file adapter.</span></span>|  
|<span data-ttu-id="b8ed4-139">StaticAdapterManagement.reg</span><span class="sxs-lookup"><span data-stu-id="b8ed4-139">StaticAdapterManagement.reg</span></span>|<span data-ttu-id="b8ed4-140">註冊範例靜態配接器。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-140">Registers the sample static adapter.</span></span>|  
  
|<span data-ttu-id="b8ed4-141">\BizTalk Project\Adapter Harness 檔案</span><span class="sxs-lookup"><span data-stu-id="b8ed4-141">\BizTalk Project\Adapter Harness files</span></span>|<span data-ttu-id="b8ed4-142">Description</span><span class="sxs-lookup"><span data-stu-id="b8ed4-142">Description</span></span>|  
|----------------------------------------------|-----------------|  
|<span data-ttu-id="b8ed4-143">AdapterHarness.odx、AdapterHarness.sln、AdapterHarnessProject.btproj</span><span class="sxs-lookup"><span data-stu-id="b8ed4-143">AdapterHarness.odx, AdapterHarness.sln, AdapterHarnessProject.btproj</span></span>|<span data-ttu-id="b8ed4-144">提供適用於 BizTalk 專案的專案、解決方案和相關檔案。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-144">Provides project, solution, and related files for the BizTalk project.</span></span>|  
|<span data-ttu-id="b8ed4-145">mySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="b8ed4-145">mySchema.xsd</span></span>|<span data-ttu-id="b8ed4-146">提供控管協調流程所預期的 Instance.xml 結構描述 (來自配接器的接收部分)，以及由協調流程傳遞到配接器的傳送部分的 Instance.xml 結構描述。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-146">Provides the Instance.xml schema expected by the harness orchestration from the receive part of the adapter, as well as the schema of the Instance.xml handed to the send part of the adapter by the orchestration.</span></span>|  
  
|<span data-ttu-id="b8ed4-147">\Design Time\Adapter Management 檔案</span><span class="sxs-lookup"><span data-stu-id="b8ed4-147">\Design Time\Adapter Management files</span></span>|<span data-ttu-id="b8ed4-148">Description</span><span class="sxs-lookup"><span data-stu-id="b8ed4-148">Description</span></span>|  
|---------------------------------------------|-----------------|  
|<span data-ttu-id="b8ed4-149">AdapterManagement.cs、AdapterManagement.csproj、AdapterManagement.sln</span><span class="sxs-lookup"><span data-stu-id="b8ed4-149">AdapterManagement.cs, AdapterManagement.csproj, AdapterManagement.sln</span></span>|<span data-ttu-id="b8ed4-150">適用於配接器設計階段的專案、解決方案和相關檔案。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-150">Project, solution, and related files for the adapter design-time.</span></span>|  
|<span data-ttu-id="b8ed4-151">AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="b8ed4-151">AssemblyInfo.cs</span></span>|<span data-ttu-id="b8ed4-152">包含此範例的組件資訊。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-152">Contains assembly information for this sample.</span></span>|  
|<span data-ttu-id="b8ed4-153">CategorySchema2.xml</span><span class="sxs-lookup"><span data-stu-id="b8ed4-153">CategorySchema2.xml</span></span>|<span data-ttu-id="b8ed4-154">範例配接器不使用。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-154">Not used by the sample adapter.</span></span>|  
|<span data-ttu-id="b8ed4-155">CategorySchema.xml</span><span class="sxs-lookup"><span data-stu-id="b8ed4-155">CategorySchema.xml</span></span>|<span data-ttu-id="b8ed4-156">包含靜態配接器的服務組織樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-156">Contains the service organization tree for the static adapter.</span></span>|  
|<span data-ttu-id="b8ed4-157">DotNetFileResource.resx</span><span class="sxs-lookup"><span data-stu-id="b8ed4-157">DotNetFileResource.resx</span></span>|<span data-ttu-id="b8ed4-158">包含資源。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-158">Contains resources.</span></span>|  
|<span data-ttu-id="b8ed4-159">ReceiveHandler.xsd、ReceiveLocation.xsd</span><span class="sxs-lookup"><span data-stu-id="b8ed4-159">ReceiveHandler.xsd, ReceiveLocation.xsd</span></span>|<span data-ttu-id="b8ed4-160">包含接收端處理常式和結束點自訂屬性結構描述</span><span class="sxs-lookup"><span data-stu-id="b8ed4-160">Contains receive side handler and endpoint custom property schemas</span></span>|  
|<span data-ttu-id="b8ed4-161">service1.wsdl</span><span class="sxs-lookup"><span data-stu-id="b8ed4-161">service1.wsdl</span></span>|<span data-ttu-id="b8ed4-162">包含配接器的作業定義。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-162">Contains operation definitions for the adapter.</span></span>|  
|<span data-ttu-id="b8ed4-163">TransmitHandler.xsd、TransmitLocation.xsd</span><span class="sxs-lookup"><span data-stu-id="b8ed4-163">TransmitHandler.xsd, TransmitLocation.xsd</span></span>|<span data-ttu-id="b8ed4-164">包含傳輸端處理常式和結束點自訂屬性結構描述</span><span class="sxs-lookup"><span data-stu-id="b8ed4-164">Contains transmit side handler and endpoint custom property schemas</span></span>|  
  
|<span data-ttu-id="b8ed4-165">\Runtime 檔案</span><span class="sxs-lookup"><span data-stu-id="b8ed4-165">\Runtime files</span></span>|<span data-ttu-id="b8ed4-166">Description</span><span class="sxs-lookup"><span data-stu-id="b8ed4-166">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="b8ed4-167">DotNetFile.csproj、DotNetFile.sln,</span><span class="sxs-lookup"><span data-stu-id="b8ed4-167">DotNetFile.csproj, DotNetFile.sln,</span></span><br /><br /> <span data-ttu-id="b8ed4-168">AssemblyInfo.cs、</span><span class="sxs-lookup"><span data-stu-id="b8ed4-168">AssemblyInfo.cs,</span></span><br /><br /> <span data-ttu-id="b8ed4-169">DotNetFileExceptions.cs、DotNetFileProperties.cs、DotNetFileReceiver.cs、DotNetFileReceiverEndPoint.cs、DotNetFileTransmitter.cs、</span><span class="sxs-lookup"><span data-stu-id="b8ed4-169">DotNetFileExceptions.cs, DotNetFileProperties.cs, DotNetFileReceiver.cs, DotNetFileReceiverEndPoint.cs, DotNetFileTransmitter.cs,</span></span><br /><br /> <span data-ttu-id="b8ed4-170">DotNetFileTransmitterEndpoint.cs、</span><span class="sxs-lookup"><span data-stu-id="b8ed4-170">DotNetFileTransmitterEndpoint.cs,</span></span><br /><br /> <span data-ttu-id="b8ed4-171">DotNetFileAsyncTransmitterBatch.cs、</span><span class="sxs-lookup"><span data-stu-id="b8ed4-171">DotNetFileAsyncTransmitterBatch.cs,</span></span><br /><br /> <span data-ttu-id="b8ed4-172">BatchMessage.cs</span><span class="sxs-lookup"><span data-stu-id="b8ed4-172">BatchMessage.cs</span></span>|<span data-ttu-id="b8ed4-173">適用於執行階段檔案複製傳送和接收配接器的檔案。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-173">Files for the run-time file-copy send and receive adapters.</span></span> <span data-ttu-id="b8ed4-174">您可以修改並以新名稱儲存這些檔案，做為自訂元件。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-174">You can modify and save these files under a new name for custom components.</span></span><br /><br /> <span data-ttu-id="b8ed4-175">DotNetFile.csproj 和 DotNetFile.sln 是專案與方案檔。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-175">DotNetFile.csproj and DotNetFile.sln are the project and solution files.</span></span><br /><br /> <span data-ttu-id="b8ed4-176">AssemblyInfo.cs 包含此範例的組件資訊。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-176">AssemblyInfo.cs contains assembly information for this sample.</span></span><br /><br /> <span data-ttu-id="b8ed4-177">DotNetFileReceiver.cs 會從接收位置讀取檔案，並將檔案提交至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-177">DotNetFileReceiver.cs reads the files from the receive locations and submits them to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="b8ed4-178">DotNetFileExceptions.cs 會在處理訊息期間實作程式碼以處理例外狀況</span><span class="sxs-lookup"><span data-stu-id="b8ed4-178">DotNetFileExceptions.cs,implements code to handle exceptions during message processing</span></span><br /><br /> <span data-ttu-id="b8ed4-179">DotNetFileProperties.cs 包含接收和傳送作業的通用屬性</span><span class="sxs-lookup"><span data-stu-id="b8ed4-179">DotNetFileProperties.cs, contains common properties for both Receive and Send operations</span></span><br /><br /> <span data-ttu-id="b8ed4-180">BatchMessage.cs 會實作批次訊息處理。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-180">BatchMessage.cs, implements batch messaging.</span></span><br /><br /> <span data-ttu-id="b8ed4-181">DotNetFileReceiverEndPoint.cs 是對應至接收位置/URI 的類別。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-181">DotNetFileReceiverEndPoint.cs, is a class corresponding to a Receive Location/URI.</span></span>  <span data-ttu-id="b8ed4-182">它會為新訊息輪詢指定資料夾</span><span class="sxs-lookup"><span data-stu-id="b8ed4-182">It handles polling the given folder for new messages</span></span><br /><br /> <span data-ttu-id="b8ed4-183">DotNetFileTransmitter.cs 是 DotNetFile 傳送配接器的單一類別。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-183">DotNetFileTransmitter.cs is a singleton class for DotNetFile send adapter.</span></span> <span data-ttu-id="b8ed4-184">傳遞到此配接器不同傳送埠的所有訊息都會經過這個類別</span><span class="sxs-lookup"><span data-stu-id="b8ed4-184">All the messages, going to various send ports of this adapter type go through this class</span></span><br /><br /> <span data-ttu-id="b8ed4-185">DotNetFileTransmitterEndpoint.cs 會處理傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-185">DotNetFileTransmitterEndpoint.cs,handles transmitting messages.</span></span>|  
  
|<span data-ttu-id="b8ed4-186">\SDK\Samples\AdaptersDevelopment\BaseAdapter\v1.0.2 檔案</span><span class="sxs-lookup"><span data-stu-id="b8ed4-186">\SDK\Samples\AdaptersDevelopment\BaseAdapter\v1.0.2 files</span></span>|<span data-ttu-id="b8ed4-187">Description</span><span class="sxs-lookup"><span data-stu-id="b8ed4-187">Description</span></span>|  
|--------------------------------------------------------------------|-----------------|  
|<span data-ttu-id="b8ed4-188">Adapter.cs、AdapterException.cs、AsyncTransmitter.cs、batch.cs、ConfigProperties.cs、ControlledTermination.cs、IManageEndpoints.cs、Receiver.cs、ReceiverEndpoint.cs</span><span class="sxs-lookup"><span data-stu-id="b8ed4-188">Adapter.cs, AdapterException.cs, AsyncTransmitter.cs, batch.cs, ConfigProperties.cs, ControlledTermination.cs, IManageEndpoints.cs, Receiver.cs, ReceiverEndpoint.cs</span></span>|<span data-ttu-id="b8ed4-189">提供組成 Base 配接器的類別。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-189">Provides classes that constitute the Base Adapter.</span></span> <span data-ttu-id="b8ed4-190">您可以使用這些類別來建立自己的配接器。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-190">You can use these to create your own adapters.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="b8ed4-191">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="b8ed4-191">How to Use This Sample</span></span>  
 <span data-ttu-id="b8ed4-192">將範例 FILE 配接器當做範本，建立其他自訂配接器。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-192">Use the sample file adapter as a template on which to create other custom adapters.</span></span>  
  
## <a name="building-this-sample"></a><span data-ttu-id="b8ed4-193">建置此範例</span><span class="sxs-lookup"><span data-stu-id="b8ed4-193">Building This Sample</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8ed4-194">如果 BizTalk 安裝是 64 位元，或安裝位置已有修改，則需要隨之變更 OutboundAssemblyPath、InboundAssemblyPath、AdapterMgmtAssemblyPath。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-194">If the BizTalk installation is 64-bit or the location of installation is modified, OutboundAssemblyPath, InboundAssemblyPath, AdapterMgmtAssemblyPath would need to be changed accordingly.</span></span>  
  
 <span data-ttu-id="b8ed4-195">使用下列程序建置和初始化 FILE 配接器範例。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-195">Use the following procedures to build and initialize the File Adapter sample.</span></span>  
  
#### <a name="to-create-a-strong-name-key-for-the-dotnetfileadapter-projects-and-the-base-adapter-project"></a><span data-ttu-id="b8ed4-196">為 DotNetFileAdapter 專案和 Base 配接器專案建立強式名稱金鑰</span><span class="sxs-lookup"><span data-stu-id="b8ed4-196">To create a strong name key for the DotNetFileAdapter projects and the Base Adapter project</span></span>  
  
1.  <span data-ttu-id="b8ed4-197">啟動 **Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-197">Start **Visual Studio Command Prompt**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b8ed4-198">以系統管理員身分執行命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-198">Run the command prompt as an Administrator.</span></span>  
  
2.  <span data-ttu-id="b8ed4-199">若要將目前目錄變更\<*範例路徑*\>**\AdaptersDevelopment\BaseAdapter\v1.0.2**目錄。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-199">Change the current directory to the \<*Samples Path*\>**\AdaptersDevelopment\BaseAdapter\v1.0.2** directory.</span></span>  
  
3.  <span data-ttu-id="b8ed4-200">在命令提示字元中，輸入 **sn – k BaseAdapter.snk** ，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-200">At the command prompt, type **sn –k BaseAdapter.snk** and then press ENTER.</span></span> <span data-ttu-id="b8ed4-201">這個 .snk 檔案可能因為先前已執行過其他範例而存在。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-201">This .snk file may already exist as a result of other samples being run previously.</span></span> <span data-ttu-id="b8ed4-202">如果檔案已經存在，您可以直接執行步驟 4 並略過這個步驟。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-202">If so, you can go right to step 4 and skip this step.</span></span>  
  
4.  <span data-ttu-id="b8ed4-203">若要將目前目錄變更\<*範例路徑*\>\\**AdaptersDevelopment\File Adapter\Runtime**目錄。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-203">Change the current directory to the \<*Samples Path*\>\\**AdaptersDevelopment\File Adapter\Runtime** directory.</span></span>  
  
5.  <span data-ttu-id="b8ed4-204">在命令提示字元中，輸入 **sn – k DotNetFileAdapter.snk** ，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-204">At the command prompt, type **sn –k DotNetFileAdapter.snk** and then press ENTER.</span></span>  
  
6.  <span data-ttu-id="b8ed4-205">在命令提示字元中，輸入 **結束** ，然後按 enter 鍵關閉命令提示字元視窗。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-205">At the command prompt, type **exit** and then press ENTER to close the command prompt window.</span></span>  
  
#### <a name="to-build-the-receiver-run-time-project"></a><span data-ttu-id="b8ed4-206">建置接收器執行階段專案</span><span class="sxs-lookup"><span data-stu-id="b8ed4-206">To build the receiver run-time project</span></span>  
  
1.  <span data-ttu-id="b8ed4-207">按一下  **啟動**, ，指向  **所有程式**, ，指向 **附屬應用程式**, ，然後按一下  **Windows 檔案總管**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-207">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.</span></span>  
  
2.  <span data-ttu-id="b8ed4-208">瀏覽至\<*範例路徑*\>**"\AdaptersDevelopment\File Adapter\Runtime"** 目錄，然後再按兩下**DotNetFile.sln**.</span><span class="sxs-lookup"><span data-stu-id="b8ed4-208">Navigate to the \<*Samples Path*\>**”\AdaptersDevelopment\File Adapter\Runtime”** directory, and then double-click **DotNetFile.sln**.</span></span>  
  
3.  <span data-ttu-id="b8ed4-209">重新建置配接器接收器執行階段專案，在方案總管] 中，以滑鼠右鍵按一下 **DotNetFile**, ，然後按一下 [ **重建**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-209">To rebuild the Adapter Receiver run-time project, in Solution Explorer, right-click **DotNetFile**, and then click **Rebuild**.</span></span>  
  
4.  <span data-ttu-id="b8ed4-210">從 **檔案** ] 功能表上，按一下 [ **結束** 以關閉 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-210">From the **File** menu, click **Exit** to close Visual Studio.</span></span>  
  
#### <a name="to-build-the-adapter-design-time-project"></a><span data-ttu-id="b8ed4-211">建置配接器執行階段專案</span><span class="sxs-lookup"><span data-stu-id="b8ed4-211">To build the adapter design-time project</span></span>  
  
1.  <span data-ttu-id="b8ed4-212">在 Windows 檔案總管，瀏覽至\<*範例路徑*\>**"\AdaptersDevelopment\File Adapter\Design Time\Adapter Management"** 目錄，然後再按兩下**AdapterManagement.sln**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-212">In Windows Explorer, navigate to the \<*Samples Path*\>**”\AdaptersDevelopment\File Adapter\Design Time\Adapter Management”** directory, and then double-click **AdapterManagement.sln**.</span></span>  
  
2.  <span data-ttu-id="b8ed4-213">在 方案總管 中，以滑鼠右鍵按一下 **AdapterManagement**, ，然後按一下  **重建**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-213">In Solution Explorer, right-click **AdapterManagement**, and then click **Rebuild**.</span></span>  
  
3.  <span data-ttu-id="b8ed4-214">從 **檔案** ] 功能表上，按一下 [ **結束** 以關閉 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-214">From the **File** menu, click **Exit** to close Visual Studio.</span></span>  
  
#### <a name="to-register-the-sample-static-adapter"></a><span data-ttu-id="b8ed4-215">註冊範例靜態配接器</span><span class="sxs-lookup"><span data-stu-id="b8ed4-215">To register the sample static adapter</span></span>  
  
1.  <span data-ttu-id="b8ed4-216">在 Windows 檔案總管，瀏覽至\<*範例路徑*\>**"\AdaptersDevelopment\File 配接器 」** 目錄。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-216">In Windows Explorer, navigate to the \<*Samples Path*\>**”\AdaptersDevelopment\File Adapter”** directory.</span></span>  
  
2.  <span data-ttu-id="b8ed4-217">若要將範例配接器新增至登錄中，按兩下 **StaticAdapterManagement.reg**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-217">To add the sample adapter to the registry, double-click **StaticAdapterManagement.reg**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b8ed4-218">StaticAdapterManagement.reg 包括硬式編碼路徑 C:\Program Files\Microsoft BizTalk Server\\。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-218">StaticAdapterManagement.reg includes hard-coded paths to C:\Program Files\Microsoft BizTalk Server\\.</span></span> <span data-ttu-id="b8ed4-219">如果您未安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]%programfiles%\microsoft BizTalk 目錄下，如果您從 BizTalk Server 2009 或 BizTalk Server 2006 R2 升級您的 BizTalk Server 安裝，或如果您正在執行的電腦上安裝 BizTalk Server64 位元的 Windows 版本，您必須將檔案 StaticAdapterManagement.reg 修改為適當的路徑。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-219">If you did not install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the %ProgramFiles%\Microsoft BizTalk Server\ directory, if you upgraded your BizTalk Server installation from BizTalk Server 2009 or BizTalk Server 2006 R2, or if you installed BizTalk Server on a computer that is running a 64-bit version of Windows, you must modify the file StaticAdapterManagement.reg with the appropriate paths.</span></span> <span data-ttu-id="b8ed4-220">根據預設，BizTalk Server 會安裝到 %programfiles(x86) %\Microsoft BizTalk Server\ 目錄上執行 Windows 64 位元版本的電腦。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-220">By default, BizTalk Server is installed into the %ProgramFiles(x86)%\Microsoft BizTalk Server\ directory on computers that are running a 64-bit version of Windows.</span></span> <span data-ttu-id="b8ed4-221">請將與 "InboundAssemblyPath"、"OutboundAssemblyPath" 和 "AdapterMgmtAssemblyPath" 值關聯的路徑更新為指向所指定檔案的正確位置。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-221">Update the paths associated with the "InboundAssemblyPath", "OutboundAssemblyPath" and "AdapterMgmtAssemblyPath" values to point to the correct location of the specified files.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b8ed4-222">如果您在 64 位元電腦上安裝 BizTalk，變更所有 HKEY_CLASSES_ROOT\CLSID\ 登錄項目執行個體都變更為 HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ 中 **StaticAdapterManagement.reg** 登錄檔。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-222">If you install BizTalk on a 64 bit machine, change all instances of the HKEY_CLASSES_ROOT\CLSID\ registry entry to HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ in the **StaticAdapterManagement.reg** registry file.</span></span>  
  
3.  <span data-ttu-id="b8ed4-223">在 **登錄編輯程式** 對話方塊中，按一下  **是** 以將範例配接器新增至登錄，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-223">In the **Registry Editor** dialog box, click **Yes** to add the sample adapter to the registry, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="b8ed4-224">若要關閉 Windows 檔案總管，在 **檔案** ] 功能表上，按一下 [ **關閉**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-224">To close Windows Explorer, on the **File** menu, click **Close**.</span></span>  
  
#### <a name="to-install-the-sample-static-adapter"></a><span data-ttu-id="b8ed4-225">安裝範例靜態配接器</span><span class="sxs-lookup"><span data-stu-id="b8ed4-225">To install the sample static adapter</span></span>  
  
1.  <span data-ttu-id="b8ed4-226">按一下**啟動**，選取**所有程式**，選取[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後選取**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-226">Click **Start**, select **All Programs**, select [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then select **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b8ed4-227">在 BizTalk Server 管理主控台中，按一下以展開 **BizTalk Server 管理**, ，按一下以展開 **BizTalk 群組**, ，然後按一下以展開 **平台設定**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-227">In the BizTalk Server Administration console, click to expand **BizTalk Server Administration**, click to expand **BizTalk Group**, and click to expand **Platform Settings**.</span></span>  
  
3.  <span data-ttu-id="b8ed4-228">以滑鼠右鍵按一下 **配接器**, ，按一下  **新增**, ，然後按一下  **配接器**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-228">Right click **Adapters**, click **New**, and then click **Adapter**.</span></span>  
  
4.  <span data-ttu-id="b8ed4-229">在 **新增配接器** 對話方塊方塊中，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-229">In the **Add Adapter** dialog box, do the following.</span></span>  
  
    |<span data-ttu-id="b8ed4-230">使用</span><span class="sxs-lookup"><span data-stu-id="b8ed4-230">Use this</span></span>|<span data-ttu-id="b8ed4-231">動作</span><span class="sxs-lookup"><span data-stu-id="b8ed4-231">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b8ed4-232">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-232">**Name**</span></span>|<span data-ttu-id="b8ed4-233">型別 **靜態**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-233">Type **Static**.</span></span>|  
    |<span data-ttu-id="b8ed4-234">**配接器**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-234">**Adapter**</span></span>|<span data-ttu-id="b8ed4-235">選取 **Static dotnetfile** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-235">Select **Static DotNetFile** from the drop-down list.</span></span>|  
    |<span data-ttu-id="b8ed4-236">**註解**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-236">**Comment**</span></span>|<span data-ttu-id="b8ed4-237">型別 **範例配接器**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-237">Type **Sample Adapter**.</span></span>|  
  
5.  <span data-ttu-id="b8ed4-238">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-238">Click **OK**.</span></span>  
  
     <span data-ttu-id="b8ed4-239">靜態配接器現在會出現在 [BizTalk 管理主控台] 右邊視窗的配接器清單中。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-239">The static adapter now appears in the list of adapters in the right window of the BizTalk Administration console.</span></span>  
  
#### <a name="to-stop-and-restart-the-host-instance"></a><span data-ttu-id="b8ed4-240">停止並重新啟動主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="b8ed4-240">To stop and restart the host instance</span></span>  
  
1.  <span data-ttu-id="b8ed4-241">按一下**啟動**，選取**所有程式**，選取[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後選取**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-241">Click **Start**, select **All Programs**, select [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and select **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b8ed4-242">在 BizTalk Server 管理主控台中，按一下以展開 **BizTalk Server 管理**, ，按一下以展開 **BizTalk 群組**, ，按一下以展開 **平台設定** 按一下 **主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-242">In the BizTalk Server Administration console, click to expand **BizTalk Server Administration**, click to expand **BizTalk Group**, click to expand **Platform Settings** and click **Host Instances**.</span></span> <span data-ttu-id="b8ed4-243">在右窗格中選取 BizTalkServerApplication。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-243">Select the BizTalkServerApplication in the right pane.</span></span>  
  
3.  <span data-ttu-id="b8ed4-244">在 結果 窗格中，以滑鼠右鍵按一下主控件執行個體 （通常是電腦名稱），以及  **重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-244">In the results pane, right-click the host instance (typically, the computer name), and then click **Restart**.</span></span>  
  
### <a name="running-this-sample"></a><span data-ttu-id="b8ed4-245">執行此範例</span><span class="sxs-lookup"><span data-stu-id="b8ed4-245">Running This Sample</span></span>  
  
##### <a name="to-run-the-file-adapter-sample"></a><span data-ttu-id="b8ed4-246">執行 FILE 配接器範例</span><span class="sxs-lookup"><span data-stu-id="b8ed4-246">To run the File Adapter sample</span></span>  
  
1.  <span data-ttu-id="b8ed4-247">按一下  **啟動**, ，指向  **所有程式**, ，指向 **附屬應用程式**, ，然後按一下  **Windows 檔案總管**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-247">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.</span></span>  
  
2.  <span data-ttu-id="b8ed4-248">BizTalk Server 安裝磁碟機上建立下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="b8ed4-248">Create the following folders on the BizTalk Server installation drive:</span></span>  
  
    -   <span data-ttu-id="b8ed4-249">*\<drive\>*:**\Temp**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-249">*\<drive\>*:**\Temp**</span></span>  
  
    -   <span data-ttu-id="b8ed4-250">*\<drive\>*:**\Temp\Send**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-250">*\<drive\>*:**\Temp\Send**</span></span>  
  
    -   <span data-ttu-id="b8ed4-251">*\<drive\>*:**\Temp\Receive**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-251">*\<drive\>*:**\Temp\Receive**</span></span>  
  
3.  <span data-ttu-id="b8ed4-252">若要關閉 Windows 檔案總管，在 **檔案** ] 功能表上，按一下 [ **關閉**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-252">To close Windows Explorer, on the **File** menu, click **Close**.</span></span>  
  
4.  <span data-ttu-id="b8ed4-253">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-253">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
5.  <span data-ttu-id="b8ed4-254">以滑鼠右鍵按一下 **BizTalk Server 管理**  節點，然後選取 **連接至現有的群組**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-254">Right-click the **BizTalk Server Administration**  node and select **Connect to Existing Group**.</span></span>  
  
6.  <span data-ttu-id="b8ed4-255">在 **連接至現有的 BizTalk Server 組態資料庫** 對話方塊方塊中，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-255">In the **Connect to Existing BizTalk Server Configuration Database** dialog box, do the following.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b8ed4-256">「BizTalk 管理」資料庫也稱為「BizTalk 組態」資料庫。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-256">The BizTalk Management database is also referred to as the BizTalk Configuration database.</span></span>  
  
    |<span data-ttu-id="b8ed4-257">使用</span><span class="sxs-lookup"><span data-stu-id="b8ed4-257">Use this</span></span>|<span data-ttu-id="b8ed4-258">動作</span><span class="sxs-lookup"><span data-stu-id="b8ed4-258">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b8ed4-259">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-259">**SQL Server**</span></span>|<span data-ttu-id="b8ed4-260">型別 **。**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-260">Type **.**</span></span> <span data-ttu-id="b8ed4-261">(句點)。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-261">(a period).</span></span>|  
    |<span data-ttu-id="b8ed4-262">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-262">**Database**</span></span>|<span data-ttu-id="b8ed4-263">選取由組態精靈建立的 BizTalk 管理資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-263">Select the name of the BizTalk Management database that was created by the Configuration Wizard.</span></span> <span data-ttu-id="b8ed4-264">「 組態精靈 」 所使用的預設資料庫名稱是 **BizTalkMgmtDb**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-264">The default database name used by the Configuration Wizard is **BizTalkMgmtDb**.</span></span>|  
  
7.  <span data-ttu-id="b8ed4-265">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-265">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="b8ed4-266">展開**BizTalk 群組 [*伺服器名稱*]** 節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**應用程式**] 節點，展開 [ **BizTalk Application 1**節點。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-266">Expand the **BizTalk Group[*server name*]** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand the **Applications** node, expand the  **BizTalk Application 1** node.</span></span>  
  
9. <span data-ttu-id="b8ed4-267">以滑鼠右鍵按一下 **傳送埠** 節點，然後再按一下 **新增**, ，請選取 **靜態單向傳送埠**, ，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-267">Right-click the **Send Ports** node, and then click **New**, select **Static One-Way Send Port**, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="b8ed4-268">在 **傳送埠屬性** 對話方塊中，選取 **一般**, ，並執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-268">In the **Send Port Properties** dialog box, select **General**, and do the following.</span></span>  
  
    |<span data-ttu-id="b8ed4-269">使用</span><span class="sxs-lookup"><span data-stu-id="b8ed4-269">Use this</span></span>|<span data-ttu-id="b8ed4-270">動作</span><span class="sxs-lookup"><span data-stu-id="b8ed4-270">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b8ed4-271">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-271">**Name**</span></span>|<span data-ttu-id="b8ed4-272">型別 **AdapterSend**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-272">Type **AdapterSend**.</span></span>|  
    |<span data-ttu-id="b8ed4-273">**傳輸類型**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-273">**Transport Type**</span></span>|<span data-ttu-id="b8ed4-274">選取 **靜態** 從下拉式清單按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-274">Select **Static** from the drop-down list and click **Configure**.</span></span><br /><br /> <span data-ttu-id="b8ed4-275">-在**目錄**方塊中，輸入 ***\<磁碟機\>*:\Temp\Send**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-275">-   In the **Directory** box, type ***\<drive\>*:\Temp\Send**.</span></span><br /><span data-ttu-id="b8ed4-276">-在 **檔案模式** 方塊中，選取 **CreateNew**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-276">-   In the **File Mode** box, select **CreateNew**.</span></span><br /><span data-ttu-id="b8ed4-277">-在 **檔案名稱** 方塊中，輸入 **%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-277">-   In the **File Name** box, type **%MessageID%.xml**.</span></span><br /><span data-ttu-id="b8ed4-278">-按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-278">-   Click **OK**.</span></span><br /><span data-ttu-id="b8ed4-279">- **URI**欄位應該會顯示 ***\<磁碟機\>*:\Temp\Send\\%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-279">-   The **URI** field should show ***\<drive\>*:\Temp\Send\\%MessageID%.xml**.</span></span>|  
    |<span data-ttu-id="b8ed4-280">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-280">**Send pipeline**</span></span>|<span data-ttu-id="b8ed4-281">選取 **PassThruTransmit (Microsoft.BizTalk.DefaultPipelines.PassThruTransmit)**, ，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-281">Select **PassThruTransmit (Microsoft.BizTalk.DefaultPipelines.PassThruTransmit)**, and then click **OK**.</span></span>|  
  
11. <span data-ttu-id="b8ed4-282">在 **BizTalk Application 1** 節點按一下 **接收埠**, ，然後選取 **新增 / 單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-282">Under the **BizTalk Application 1** node click **Receive Ports**, and select **New / One-Way Receive Port**.</span></span>  
  
12. <span data-ttu-id="b8ed4-283">在 **建立新接收埠** 對話方塊中，於 **指定接收埠類型** 方塊中，選取 **單向接收埠** 從下拉式清單，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-283">In the **Create New Receive Port** dialog box, in the **Specify the type of Receive Port** box, select **One-way Receive Port** from the drop-down list, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="b8ed4-284">在 **接收埠屬性** 對話方塊中，於 **名稱** 方塊中，輸入 **AdapterReceive**, ，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-284">In the **Receive Port Properties** dialog box, in the **Name** box, type **AdapterReceive**, and then click **OK**.</span></span>  
  
14. <span data-ttu-id="b8ed4-285">在 **BizTalk Application 1** 以滑鼠右鍵按一下節點 **接收位置**, ，然後選取 **新增 / 單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-285">Under the **BizTalk Application 1** node right click **Receive Locations**, and select **New / One-way Receive Location**.</span></span>  
  
15. <span data-ttu-id="b8ed4-286">在 **選取接收埠** 對話方塊中，選取 **AdapterReceive** 然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-286">In the **Select a Receive Port** dialog, select **AdapterReceive** then click **OK**.</span></span>  
  
16. <span data-ttu-id="b8ed4-287">在 **接收位置屬性** 對話方塊方塊中，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-287">In the **Receive Location Properties** dialog box, do the following.</span></span>  
  
    |<span data-ttu-id="b8ed4-288">使用</span><span class="sxs-lookup"><span data-stu-id="b8ed4-288">Use this</span></span>|<span data-ttu-id="b8ed4-289">動作</span><span class="sxs-lookup"><span data-stu-id="b8ed4-289">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b8ed4-290">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-290">**Name**</span></span>|<span data-ttu-id="b8ed4-291">型別 **AdapterReceiveLocation**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-291">Type **AdapterReceiveLocation**</span></span>|  
    |<span data-ttu-id="b8ed4-292">**傳輸類型**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-292">**Transport Type**</span></span>|<span data-ttu-id="b8ed4-293">選取 **靜態** 從下拉式清單和叫用 **設定** 來存取這些其餘屬性。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-293">Select **Static** from the drop-down list and hit **Configure** to access these remaining properties.</span></span>|  
    |<span data-ttu-id="b8ed4-294">**URI**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-294">**URI**</span></span>|<span data-ttu-id="b8ed4-295">-按一下省略符號按鈕 (**...**)。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-295">-   Click the ellipsis button (**…**).</span></span><br /><span data-ttu-id="b8ed4-296">-在 **數字的檔案在批次** 方塊中，輸入 **20**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-296">-   In the **Number Of Files In Batch** box, type **20**.</span></span><br /><span data-ttu-id="b8ed4-297">-在**目錄**方塊中，輸入 ***\<磁碟機\>*:\Temp\Receive**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-297">-   In the **Directory** box, type ***\<drive\>*:\Temp\Receive**.</span></span><br /><span data-ttu-id="b8ed4-298">-確認 **檔案遮罩** 屬性設定為 **\*.xml**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-298">-   Ensure the **File Mask** property is set to **\*.xml**.</span></span><br /><span data-ttu-id="b8ed4-299">-在 **輪詢間隔** 方塊中，輸入 **5**, ，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-299">-   In the **Polling Interval** box, type **5**, and click **OK**.</span></span><br /><span data-ttu-id="b8ed4-300">-確認**URI**標籤包含 \***\<磁碟機\>\*:\Temp\Receive\\\*.xml**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-300">-   Ensure the **URI** label contains \***\<drive\>\*:\Temp\Receive\\\*.xml**.</span></span>|  
    |<span data-ttu-id="b8ed4-301">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-301">**Receive Handler**</span></span>|<span data-ttu-id="b8ed4-302">選取 **BizTalkServerApplication** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-302">Select **BizTalkServerApplication** from the drop-down list.</span></span>|  
    |<span data-ttu-id="b8ed4-303">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-303">**Receive Pipeline**</span></span>|<span data-ttu-id="b8ed4-304">選取 **XMLReceive** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-304">Select **XMLReceive** from the drop-down list.</span></span>|  
  
17. <span data-ttu-id="b8ed4-305">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-305">Click **OK**.</span></span>  
  
     <span data-ttu-id="b8ed4-306">若要繼續 *建置、 部署和繫結範例配接器*。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-306">Proceed to *Building, Deploying, and Binding the Sample Adapter*.</span></span>  
  
### <a name="building-deploying-and-binding-the-sample-adapter"></a><span data-ttu-id="b8ed4-307">建置、部署和繫結範例配接器</span><span class="sxs-lookup"><span data-stu-id="b8ed4-307">Building, Deploying, and Binding the Sample Adapter</span></span>  
 <span data-ttu-id="b8ed4-308">在配接器可以使用之前，您必須先建置專案、將協調流程繫結至連接埠以及登錄配接器。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-308">Before the adapter goes live, you must build the project, bind the orchestration with the ports, and enlist the adapter.</span></span>  
  
##### <a name="to-create-a-strong-name-key-for-the-static-adapter"></a><span data-ttu-id="b8ed4-309">建立靜態配接器的強式名稱金鑰</span><span class="sxs-lookup"><span data-stu-id="b8ed4-309">To create a strong name key for the static adapter</span></span>  
  
1.  <span data-ttu-id="b8ed4-310">啟動 **Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-310">Start **Visual Studio Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="b8ed4-311">在命令提示字元中，變更目前的目錄\<*範例路徑*\>**\AdaptersDevelopment\File Adapter\BizTalk Project\Adapter Harness**目錄。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-311">At the command prompt, change the current directory to the \<*Samples Path*\>**\AdaptersDevelopment\File Adapter\BizTalk Project\Adapter Harness** directory.</span></span>  
  
3.  <span data-ttu-id="b8ed4-312">在命令提示字元中，輸入 **sn – k AdapterHarness.snk**, ，然後按下 enter。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-312">At the command prompt, type **sn –k AdapterHarness.snk**, and then pressENTER.</span></span>  
  
4.  <span data-ttu-id="b8ed4-313">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-313">Click **OK**.</span></span>  
  
##### <a name="to-build-the-adapter-harness-project"></a><span data-ttu-id="b8ed4-314">建置配接器控管專案</span><span class="sxs-lookup"><span data-stu-id="b8ed4-314">To build the Adapter Harness project</span></span>  
  
-   <span data-ttu-id="b8ed4-315">在 方案總管 中，以滑鼠右鍵按一下 **adapterharnessproject**, ，然後按一下  **重建**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-315">In Solution Explorer, right-click **AdapterHarnessProject**, and then click **Rebuild**.</span></span>  
  
##### <a name="to-deploy-the-adapter-harness-project"></a><span data-ttu-id="b8ed4-316">部署配接器控管專案</span><span class="sxs-lookup"><span data-stu-id="b8ed4-316">To deploy the Adapter Harness project</span></span>  
  
1.  <span data-ttu-id="b8ed4-317">在 方案總管 中，當重新建置專案之後，以滑鼠右鍵按一下 **adapterharnessproject**, ，然後按一下  **部署**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-317">In Solution Explorer, when the project has rebuilt, right-click **AdapterHarnessProject**, and then click **Deploy**.</span></span>  
  
2.  <span data-ttu-id="b8ed4-318">在 BizTalk Server 管理主控台 中，選取的專案，您已部署，然後再按一下 **重新整理**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-318">In BizTalk Server Administration console, select the project you have deployed, and then click **Refresh**.</span></span>  
  
##### <a name="to-bind-the-orchestration-with-the-ports"></a><span data-ttu-id="b8ed4-319">將協調流程繫結至連接埠</span><span class="sxs-lookup"><span data-stu-id="b8ed4-319">To bind the orchestration with the ports</span></span>  
  
1.  <span data-ttu-id="b8ed4-320">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，在適當[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式中，展開 **協調流程**節點。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-320">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, under the appropriate [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, expand the **Orchestrations** node.</span></span>  
  
2.  <span data-ttu-id="b8ed4-321">以滑鼠右鍵按一下 **AdapterHarness.AdapterHarnessType**, ，然後按一下  **繫結**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-321">Right-click **AdapterHarness.AdapterHarnessType**, and then click **Bind**.</span></span>  
  
3.  <span data-ttu-id="b8ed4-322">在 **連接埠繫結屬性-AdapterHarness.AdapterHarnessType-Binding Configurations** 對話方塊方塊中，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-322">In the **Port Binding Properties - AdapterHarness.AdapterHarnessType- Binding Configurations** dialog box, do the following.</span></span>  
  
    |<span data-ttu-id="b8ed4-323">使用</span><span class="sxs-lookup"><span data-stu-id="b8ed4-323">Use this</span></span>|<span data-ttu-id="b8ed4-324">動作</span><span class="sxs-lookup"><span data-stu-id="b8ed4-324">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b8ed4-325">**AdapterFileReceivePort**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-325">**AdapterFileReceivePort**</span></span>|<span data-ttu-id="b8ed4-326">選取 **AdapterReceive** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-326">Select **AdapterReceive** from the drop-down list.</span></span>|  
    |<span data-ttu-id="b8ed4-327">**AdapterFileSendPort**</span><span class="sxs-lookup"><span data-stu-id="b8ed4-327">**AdapterFileSendPort**</span></span>|<span data-ttu-id="b8ed4-328">選取 **AdapterSend** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-328">Select **AdapterSend** from the drop-down list.</span></span>|  
  
4.  <span data-ttu-id="b8ed4-329">在左窗格中，按一下  **主機**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-329">In the left pane, click **Host**.</span></span>  
  
5.  <span data-ttu-id="b8ed4-330">在 **主機** 方塊中，選取 **BizTalkServerApplication** 從下拉式清單，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-330">In the **Host** box, select **BizTalkServerApplication** from the drop-down list, and then click **OK**.</span></span>  
  
 <span data-ttu-id="b8ed4-331">若要繼續 *管理範例配接器*。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-331">Proceed to *Administering the Sample Adapter*.</span></span>  
  
### <a name="administering-the-sample-adapter"></a><span data-ttu-id="b8ed4-332">管理範例配接器</span><span class="sxs-lookup"><span data-stu-id="b8ed4-332">Administering the Sample Adapter</span></span>  
 <span data-ttu-id="b8ed4-333">請在 [BizTalk 管理主控台] 中完成範例配接器的管理工作。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-333">You complete administration tasks for the sample adapter in the BizTalk Administration console.</span></span>  
  
##### <a name="to-administer-the-file-adapter-sample"></a><span data-ttu-id="b8ed4-334">管理 FILE 配接器範例</span><span class="sxs-lookup"><span data-stu-id="b8ed4-334">To administer the File Adapter sample</span></span>  
  
1.  <span data-ttu-id="b8ed4-335">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-335">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b8ed4-336">在左窗格中，按一下以展開 **應用程式**, ，按一下以展開 **BizTalk Application 1**, ，然後按一下 **接收位置**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-336">In the left pane, click to expand **Applications**, click to expand **BizTalk Application 1**, and click **Receive Locations**.</span></span>  
  
3.  <span data-ttu-id="b8ed4-337">請確定 **AdapterReceive** 狀態是  **啟用**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-337">Ensure the **AdapterReceive** status is **Enabled**.</span></span>  
  
     <span data-ttu-id="b8ed4-338">如果狀態不是 **啟用**, ，以滑鼠右鍵按一下 **AdapterReceive** 中右窗格中，然後按一下 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-338">If the status is not **Enabled**, right-click **AdapterReceive** in the right pane, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="b8ed4-339">在左窗格中，按一下  **協調流程** ，並確定 **AdapterHarness.AdapterHarnessType** 是 **編列**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-339">In the left pane, click **Orchestrations** and ensure that **AdapterHarness.AdapterHarnessType** is **Enlisted**.</span></span> <span data-ttu-id="b8ed4-340">以滑鼠右鍵按一下 **AdapterHarness.AdapterHarnessType**, ，然後按一下  **登錄** (如果 AdapterHarness.AdapterHarnessType 已經登錄， **登錄** 就無法使用功能表選項)。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-340">Right click **AdapterHarness.AdapterHarnessType**, and then click **Enlist** (if AdapterHarness.AdapterHarnessType is already enlisted, the **Enlist** menu option is unavailable).</span></span>  
  
5.  <span data-ttu-id="b8ed4-341">以滑鼠右鍵按一下 **AdapterHarness.AdapterHarnessType** ，然後選取 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-341">Right-click **AdapterHarness.AdapterHarnessType** and select **Start**.</span></span> <span data-ttu-id="b8ed4-342">此協調流程的狀態應該變更為 **執行**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-342">The status of this orchestration should change to **Running**.</span></span>  
  
 <span data-ttu-id="b8ed4-343">若要繼續 *測試範例配接器*。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-343">Proceed to *Testing the Sample Adapter*.</span></span>  
  
### <a name="testing-the-sample-adapter"></a><span data-ttu-id="b8ed4-344">測試範例配接器</span><span class="sxs-lookup"><span data-stu-id="b8ed4-344">Testing the Sample Adapter</span></span>  
 <span data-ttu-id="b8ed4-345">部署範例配接器之後，您必須停止並重新啟動主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-345">After you deploy the sample adapter, you must stop and restart the host instance.</span></span> <span data-ttu-id="b8ed4-346">請務必先測試範例配接器，再運用到實際執行的環境中。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-346">It is critical that you test the sample adapter before you place it into production.</span></span>  
  
##### <a name="to-stop-and-restart-the-host-instance"></a><span data-ttu-id="b8ed4-347">停止並重新啟動主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="b8ed4-347">To stop and restart the host instance</span></span>  
  
1.  <span data-ttu-id="b8ed4-348">在 **BizTalk Server 管理** 主控台中，按一下以展開 **BizTalk Server 管理**, ，按一下以展開 **BizTalk 群組**, ，按一下以展開 **平台設定** 按一下 **主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-348">In the **BizTalk Server Administration** console, click to expand **BizTalk Server Administration**, click to expand **BizTalk Group**, click to expand **Platform Settings** and click **Host Instances**.</span></span> <span data-ttu-id="b8ed4-349">在右窗格中選取 BizTalkServerApplication。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-349">Select the BizTalkServerApplication in the right pane.</span></span>  
  
2.  <span data-ttu-id="b8ed4-350">主控件執行個體 （通常是電腦名稱），以滑鼠右鍵按一下，然後按一下  **停止**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-350">Right-click the host instance (typically, the computer name), and then click **Stop**.</span></span>  
  
     <span data-ttu-id="b8ed4-351">主控件執行個體的狀態變更為 **已停止**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-351">The status of the host instance changes to **Stopped**.</span></span>  
  
3.  <span data-ttu-id="b8ed4-352">以滑鼠右鍵按一下主控件執行個體，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-352">Right-click the host instance, and then click **Start**.</span></span>  
  
     <span data-ttu-id="b8ed4-353">主控件執行個體的狀態變更為 **執行**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-353">The status of the host instance changes to **Running**.</span></span>  
  
##### <a name="to-test-the-sample-static-adapter-runtime"></a><span data-ttu-id="b8ed4-354">測試範例靜態配接器執行階段</span><span class="sxs-lookup"><span data-stu-id="b8ed4-354">To test the sample static adapter runtime</span></span>  
  
1.  <span data-ttu-id="b8ed4-355">在 Windows 檔案總管，瀏覽至\<*範例路徑*\>**\AdaptersDevelopment\File 配接器**目錄，並複製到剪貼簿 InstanceXML.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-355">In Windows Explorer, navigate to the \<*Samples Path*\>**\AdaptersDevelopment\File Adapter** directory, and copy the InstanceXML.xml file to your clipboard.</span></span>  
  
2.  <span data-ttu-id="b8ed4-356">瀏覽至*\<磁碟機\>*:**\Temp\Receive**並將 Instance.xml 檔案貼到資料夾。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-356">Navigate to *\<drive\>*:**\Temp\Receive** and paste the Instance.xml file into the folder.</span></span>  
  
     <span data-ttu-id="b8ed4-357">如果傳輸和接收配接器使用，則檔案應該從*\<磁碟機\>*:**\Temp\Receive**資料夾*\<磁碟機\>* :**\Temp\Send**資料夾。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-357">If the transmit and receive adapters are working, the file should move from the *\<drive\>*:**\Temp\Receive** folder to the *\<drive\>*:**\Temp\Send** folder.</span></span>  
  
##### <a name="to-test-the-sample-add-adapter-wizard-functionality-for-the-sample-static-adapter"></a><span data-ttu-id="b8ed4-358">測試範例靜態配接器的範例新增配接器精靈功能</span><span class="sxs-lookup"><span data-stu-id="b8ed4-358">To test the sample Add Adapter Wizard functionality for the sample static adapter</span></span>  
  
1.  <span data-ttu-id="b8ed4-359">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下 **[adapterharnessproject]**，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-359">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click **AdapterHarnessProject**, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="b8ed4-360">在 **加入產生的項目-adapterharnessproject** 對話方塊中，按一下  **新增配接器中繼資料**, ，然後按一下  **開啟**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-360">In the **Add Generated Items - AdapterHarnessProject** dialog box, click **Add Adapter Metadata**, and then click **Open**.</span></span>  
  
     <span data-ttu-id="b8ed4-361">已註冊的配接器清單便會出現。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-361">The list of registered adapters appears.</span></span>  
  
3.  <span data-ttu-id="b8ed4-362">選取 **Static dotnetfile]**, ，然後按一下 [ **下一步**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-362">Select **Static DotNetFile**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="b8ed4-363">配接器所公開的服務組織便會出現。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-363">The service organization exposed by the adapter appears.</span></span>  
  
4.  <span data-ttu-id="b8ed4-364">展開 **服務組織**, ，**健康照護**, ，然後按一下  **管理**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-364">Expand **Service Organization**, **Health Care**, and then click **Administrative**.</span></span>  
  
     <span data-ttu-id="b8ed4-365">請注意， **資格** 顯示方式和其他節點。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-365">Notice that **Eligibility** displays differently from the other nodes.</span></span> <span data-ttu-id="b8ed4-366">**資格** 是您可以選取 [服務] 節點。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-366">**Eligibility** is a service node that you can select.</span></span> <span data-ttu-id="b8ed4-367">其他節點是組織節點，沒有說明任何特定的服務。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-367">The other nodes are organization nodes that do not describe any specific service.</span></span>  
  
5.  <span data-ttu-id="b8ed4-368">選取 **資格** 節點，然後再按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-368">Select the **Eligibility** node, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="b8ed4-369">BizTalk 會將 .odx 檔案和 .xsd 檔案匯入專案。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-369">BizTalk imports an .odx file and an .xsd file into the project.</span></span>  
  
     <span data-ttu-id="b8ed4-370">現在，您可以在 BizTalk 專案中，使用排程中的配接器所匯入的結構描述、PortTypes、Operations 和 MessageTypes。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-370">You can now use the schemas, PortTypes, Operations, and MessageTypes imported from the adapter in the schedule for the BizTalk project.</span></span>  
  
## <a name="classes-or-methods-used-in-this-sample"></a><span data-ttu-id="b8ed4-371">在此範例中使用的類別或方法</span><span class="sxs-lookup"><span data-stu-id="b8ed4-371">Classes or Methods used in this Sample</span></span>  
 <span data-ttu-id="b8ed4-372">介面︰ IBaseMessage、 IPropertyBag、 IBTTransportProxy</span><span class="sxs-lookup"><span data-stu-id="b8ed4-372">Interfaces: IBaseMessage, IPropertyBag, IBTTransportProxy</span></span>  
  
 <span data-ttu-id="b8ed4-373">類別 （來自 Base 配接器）︰ AsyncTransmitterEndpoint、 AsyncTransmitter、 BatchMessage、 ControlledTermination、 ReceiverEndpoint、 DotNetFileCommonProperties、 BatchOperationType</span><span class="sxs-lookup"><span data-stu-id="b8ed4-373">Classes (from Base Adapter): AsyncTransmitterEndpoint, AsyncTransmitter, BatchMessage, ControlledTermination, ReceiverEndpoint, DotNetFileCommonProperties, BatchOperationType</span></span>  
  
### <a name="comments"></a><span data-ttu-id="b8ed4-374">註解</span><span class="sxs-lookup"><span data-stu-id="b8ed4-374">Comments</span></span>  
 <span data-ttu-id="b8ed4-375">完成範例配接器之後, 您可以修改範例配接器建立自訂靜態或動態配接器的詳細資訊，請參閱[配接器設計階段組態](../core/adapter-design-time-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="b8ed4-375">After completing the sample adapter, you can modify the sample adapter to create a custom static or dynamic adapter For more information, see [Adapter Design-Time Configuration](../core/adapter-design-time-configuration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8ed4-376">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8ed4-376">See Also</span></span>  
 <span data-ttu-id="b8ed4-377">[配接器範例-使用方式](../core/adapter-samples-usage.md) </span><span class="sxs-lookup"><span data-stu-id="b8ed4-377">[Adapter Samples - Usage](../core/adapter-samples-usage.md) </span></span>  
 [<span data-ttu-id="b8ed4-378">註冊配接器</span><span class="sxs-lookup"><span data-stu-id="b8ed4-378">Registering an Adapter</span></span>](../core/registering-an-adapter.md)