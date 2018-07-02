---
title: HTTPSolicitResponse |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- examples, HTTP adapters
ms.assetid: b149544e-3279-4ac9-b31f-fff3e41ec8e7
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5a68e24cee95b25596ad5162223c34a75139c13
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981295"
---
# <a name="httpsolicitresponse"></a><span data-ttu-id="bf6b5-102">HTTPSolicitResponse</span><span class="sxs-lookup"><span data-stu-id="bf6b5-102">HTTPSolicitResponse</span></span>
<span data-ttu-id="bf6b5-103">HTTPSolicitResponse 範例會示範如何建立 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程，以運用 ASP.NET 應用程式協助處理協調流程資料。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-103">The HTTPSolicitResponse sample demonstrates how to create a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration that leverages an ASP.NET application to help process orchestration data.</span></span> <span data-ttu-id="bf6b5-104">在此範例中，協調流程會利用要求/回應埠，將訊息傳送至 ASP.NET 應用程式並擷取回應。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-104">In this sample, the orchestration makes use of a request/response port to send a message to the ASP.NET application and to retrieve the response.</span></span> <span data-ttu-id="bf6b5-105">藉由使用 HTTP 配接器，便能整合 BizTalk Server 協調流程與 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-105">You achieve the integration between the BizTalk Server orchestration and the ASP.NET application by using the HTTP adapter.</span></span> <span data-ttu-id="bf6b5-106">如需詳細資訊，請參閱 < [HTTP 配接器](../core/http-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-106">For more information, see [HTTP Adapter](../core/http-adapter.md).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="bf6b5-107">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="bf6b5-107">What This Sample Does</span></span>  
 <span data-ttu-id="bf6b5-108">此範例由 BizTalk Server 協調流程組成，它會接收一個包含兩個要相乘之數字的要求，並透過下列步驟順序滿足該要求：</span><span class="sxs-lookup"><span data-stu-id="bf6b5-108">This sample consists of a BizTalk Server orchestration that receives a request containing two numbers to be multiplied, and satisfies that request using the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="bf6b5-109">BizTalk Server 協調流程會從特定資料夾接收 .xml 輸入檔。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-109">The BizTalk Server orchestration retrieves an .xml input file from a specific folder.</span></span>  
  
2.  <span data-ttu-id="bf6b5-110">協調流程會使用 HTTP 要求，將 XML 從檔案轉寄至乘法運算器 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-110">The orchestration uses an HTTP request to forward the XML from the file to a multiplier ASP.NET application.</span></span>  
  
3.  <span data-ttu-id="bf6b5-111">乘法運算器 ASP.NET 應用程式會執行乘法運算，並且傳回 XML 格式的結果，以回應 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-111">The multiplier ASP.NET application responds to the HTTP request by performing the multiplication and returning the result as XML in the HTTP response.</span></span>  
  
4.  <span data-ttu-id="bf6b5-112">協調流程會接收 HTTP 回應中 XML 格式的結果，並將該結果寫入特定資料夾的 .xml 檔案中。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-112">The orchestration receives the result as XML in an HTTP response, and writes that result to an .xml file in a specific folder.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="bf6b5-113">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="bf6b5-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="bf6b5-114">\<*範例路徑*\>\AdaptersUsage\HTTPSolicitResponse</span><span class="sxs-lookup"><span data-stu-id="bf6b5-114">\<*Samples Path*\>\AdaptersUsage\HTTPSolicitResponse</span></span>  
  
 <span data-ttu-id="bf6b5-115">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-115">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="bf6b5-116">檔案</span><span class="sxs-lookup"><span data-stu-id="bf6b5-116">File(s)</span></span>|<span data-ttu-id="bf6b5-117">描述</span><span class="sxs-lookup"><span data-stu-id="bf6b5-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf6b5-118">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="bf6b5-118">Cleanup.bat</span></span>|<span data-ttu-id="bf6b5-119">從全域組件快取 (GAC) 解除部署並移除組件；移除傳送和接收埠；視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-119">Undeploys assemblies and removes them from the global assembly cache (GAC); removes send and receive ports; removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="bf6b5-120">HttpSolicitResponse.btproj、HttpSolicitResponse.sln</span><span class="sxs-lookup"><span data-stu-id="bf6b5-120">HttpSolicitResponse.btproj, HttpSolicitResponse.sln</span></span>|<span data-ttu-id="bf6b5-121">為包含協調流程 (會使用乘法運算器 ASP.NET 應用程式、相關結構描述等) 的 BizTalk 專案，提供專案和原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-121">Provides project and source files for the BizTalk project that contains the orchestration that uses the multiplier ASP.NET application, the associated schemas, and so on.</span></span>|  
|<span data-ttu-id="bf6b5-122">HttpSolicitResponseBinding.xml</span><span class="sxs-lookup"><span data-stu-id="bf6b5-122">HttpSolicitResponseBinding.xml</span></span>|<span data-ttu-id="bf6b5-123">提供例如連接埠繫結等自動設定的功能。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-123">Provides for automated setup such as port binding.</span></span>|  
|<span data-ttu-id="bf6b5-124">MultiplyRequest.xsd、MultiplyResponse.xsd</span><span class="sxs-lookup"><span data-stu-id="bf6b5-124">MultiplyRequest.xsd, MultiplyResponse.xsd</span></span>|<span data-ttu-id="bf6b5-125">為乘法運算要求和回應 XML 訊息分別提供結構描述。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-125">Provides schemas for the multiplication request and response XML messages, respectively.</span></span>|  
|<span data-ttu-id="bf6b5-126">MultiplyTwoIntegers.odx</span><span class="sxs-lookup"><span data-stu-id="bf6b5-126">MultiplyTwoIntegers.odx</span></span>|<span data-ttu-id="bf6b5-127">提供 BizTalk Server 協調流程，它會接收要求乘法運算的 .xml 檔案、將該要求轉寄至乘法運算器 ASP.NET 應用程式，並將其回應寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-127">Provides a BizTalk Server orchestration that receives an .xml file requesting a multiplication operation, forwards the request to the multiplier ASP.NET application, and writes its response to a file.</span></span>|  
|<span data-ttu-id="bf6b5-128">request_in.xml</span><span class="sxs-lookup"><span data-stu-id="bf6b5-128">request_in.xml</span></span>|<span data-ttu-id="bf6b5-129">範例輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-129">Sample input file.</span></span>|  
|<span data-ttu-id="bf6b5-130">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="bf6b5-130">Setup.bat</span></span>|<span data-ttu-id="bf6b5-131">建置並初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-131">Builds and initializes this sample.</span></span>|  
|<span data-ttu-id="bf6b5-132">在 \Multiplier 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="bf6b5-132">In the \Multiplier folder:</span></span><br /><br /> <span data-ttu-id="bf6b5-133">Multiplier.aspx、 Multiplier.aspx.cs、 Multiplier.sln</span><span class="sxs-lookup"><span data-stu-id="bf6b5-133">Multiplier.aspx, Multiplier.aspx.cs, Multiplier.sln</span></span>|<span data-ttu-id="bf6b5-134">包含構成實作乘法運算器服務之 ASP.NET 應用程式的檔案，其中包括專案和方案檔、ASPX 檔案、Microsoft Visual C# .NET 原始程式檔等等。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-134">Contains files that constitute the ASP.NET application that implements the multiplier service, including project and solution files, ASPX files, Microsoft Visual C# .NET source files, and so on.</span></span>|  
  
## <a name="building-and-initializing-the-sample"></a><span data-ttu-id="bf6b5-135">建置和初始化範例</span><span class="sxs-lookup"><span data-stu-id="bf6b5-135">Building and Initializing the Sample</span></span>  
 <span data-ttu-id="bf6b5-136">請使用下列程序，建置和初始化 HTTPSolicitResponse 範例。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-136">Use the following procedure to build and initialize the HTTPSolicitResponse sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf6b5-137">如果接收位置包含任何大寫字元，這個範例便無法運作。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-137">This sample doesn't work if the name of the receive location contains any uppercase characters.</span></span>  
  
#### <a name="to-build-and-initialize-the-sample"></a><span data-ttu-id="bf6b5-138">建置和初始化範例</span><span class="sxs-lookup"><span data-stu-id="bf6b5-138">To build and initialize the sample</span></span>  
  
1. <span data-ttu-id="bf6b5-139">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="bf6b5-139">In a command window, navigate to the following folder:</span></span>  
  
    <span data-ttu-id="bf6b5-140">\<*範例路徑*\>\AdaptersUsage\HTTPSolicitResponse</span><span class="sxs-lookup"><span data-stu-id="bf6b5-140">\<*Samples Path*\>\AdaptersUsage\HTTPSolicitResponse</span></span>  
  
2. <span data-ttu-id="bf6b5-141">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="bf6b5-141">Run the file Setup.bat, which performs the following actions:</span></span>  
  
   - <span data-ttu-id="bf6b5-142">為此範例建立輸入和輸出資料夾：</span><span class="sxs-lookup"><span data-stu-id="bf6b5-142">Creates the input and output folders for this sample:</span></span>  
  
      <span data-ttu-id="bf6b5-143">\<*範例路徑*\>\AdaptersUsage\HttpSolicitResponse\HttpSolicitResponseInput</span><span class="sxs-lookup"><span data-stu-id="bf6b5-143">\<*Samples Path*\>\AdaptersUsage\HttpSolicitResponse\HttpSolicitResponseInput</span></span>  
  
      <span data-ttu-id="bf6b5-144">\<*範例路徑*\>\AdaptersUsage\HttpSolicitResponse\HttpSolicitResponseOutput</span><span class="sxs-lookup"><span data-stu-id="bf6b5-144">\<*Samples Path*\>\AdaptersUsage\HttpSolicitResponse\HttpSolicitResponseOutput</span></span>  
  
   - <span data-ttu-id="bf6b5-145">編譯及設定此範例所使用的乘法運算器 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-145">Compiles and configures the multiplier ASP.NET application used by this sample.</span></span>  
  
     > [!NOTE]
     >  <span data-ttu-id="bf6b5-146">在建立應用程式集區在 [IIS 管理員] 中，設定**DefaultAppPool** .NET Framework 版本設 **.Net Framework v4.0**。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-146">While creating application pool in IIS Manager, set the **DefaultAppPool** .NET Framework version to **.Net Framework v4.0**.</span></span>  
  
   - <span data-ttu-id="bf6b5-147">編譯及部署此範例中所使用的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-147">Compiles and deploys the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration used in this sample.</span></span>  
  
   - <span data-ttu-id="bf6b5-148">建立並繫結必要的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置和連接埠。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-148">Creates and binds the necessary [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location and ports.</span></span>  
  
     > [!NOTE]
     >  <span data-ttu-id="bf6b5-149">此範例會在建立和繫結連接埠時顯示下列警告：</span><span class="sxs-lookup"><span data-stu-id="bf6b5-149">This sample displays the following warnings when creating and binding the ports:</span></span>  
  
     > [!NOTE]
     >  `Warning: Receive handler not specified for receive location "HttpSolicitResponseReceiveLocation"; updating with first receive handler with matching transport type.`  
  
     > [!NOTE]
     >  `Warning: Host not specified for orchestration "Microsoft.Samples.BizTalk.HttpSolicitResponse.MultiplyTwoIntegers"; updating with first available host.`  
  
   - <span data-ttu-id="bf6b5-150">啟用接收位置並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-150">Enables the receive location, and starts the send port.</span></span>  
  
     > [!NOTE]
     >  <span data-ttu-id="bf6b5-151">在這個範例中，協調流程會使用雙向連接埠透過 HTTP 與 ASP.NET 應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-151">The orchestration in this sample uses a two-way port for the HTTP interaction with the ASP.NET application.</span></span>  
  
     > [!NOTE]
     >  <span data-ttu-id="bf6b5-152">在嘗試執行此範例之前，您必須確認 BizTalk 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-152">You should confirm that BizTalk did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
     > [!NOTE]
     >  <span data-ttu-id="bf6b5-153">若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-153">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name Utility (sn.exe).</span></span> <span data-ttu-id="bf6b5-154">使用此金鑰組簽署所產生的組件。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-154">Use this key pair to sign the resulting assemblies.</span></span>  
  
     > [!NOTE]
     >  <span data-ttu-id="bf6b5-155">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-155">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="bf6b5-156">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-156">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="bf6b5-157">執行範例</span><span class="sxs-lookup"><span data-stu-id="bf6b5-157">Running the Sample</span></span>  
 <span data-ttu-id="bf6b5-158">請依照下列程序執行 HTTPSolicitResponse 範例。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-158">Use the following procedure to run the HTTPSolicitResponse sample.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="bf6b5-159">執行範例</span><span class="sxs-lookup"><span data-stu-id="bf6b5-159">To run the sample</span></span>  
  
1.  <span data-ttu-id="bf6b5-160">將 request_in.xml 檔案複本貼入資料夾 HttpSolicitResponseInput。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-160">Paste a copy of the file request_in.xml into the folder HttpSolicitResponseInput.</span></span>  
  
2.  <span data-ttu-id="bf6b5-161">觀察資料夾 HttpSolicitResponseOutput 中建立的 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-161">Observe the .xml file created in the folder HttpSolicitResponseOutput.</span></span> <span data-ttu-id="bf6b5-162">這個 .xml 檔案的名稱是根據訊息識別碼 GUID 為基礎。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-162">The name of this .xml file is based on the message ID GUID.</span></span> <span data-ttu-id="bf6b5-163">這個檔案包含乘法運算的 XML 格式結果。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-163">This file contains the XML-formatted result of the multiplication operation.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf6b5-164">您可以變更輸入檔中的運算元值，執行不同的乘法運算。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-164">You can change the operand values in the input file to perform a different multiplication operation.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="bf6b5-165">註解</span><span class="sxs-lookup"><span data-stu-id="bf6b5-165">Comments</span></span>  
 <span data-ttu-id="bf6b5-166">您可以調整這個範例，以便與公開 HTTP 介面的不同外部系統通訊。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-166">You can adapt this sample to communicate with a different external system that exposes an HTTP interface.</span></span>  
  
 <span data-ttu-id="bf6b5-167">MultiplyRequest.xsd 和 MultiplyResponse.xsd 檔案都是 XML 結構描述，會分別針對乘法運算器 ASP.NET 應用程式定義輸入和輸出資料。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-167">The files MultiplyRequest.xsd and MultiplyResponse.xsd are the XML schemas that define the format of the input and output data for the multiplier ASP.NET application.</span></span> <span data-ttu-id="bf6b5-168">協調流程會使用這些檔案來定義要求和回應訊息類型。</span><span class="sxs-lookup"><span data-stu-id="bf6b5-168">The orchestration uses these files to define the request and response message types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf6b5-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf6b5-169">See Also</span></span>  
 [<span data-ttu-id="bf6b5-170">HTTP 配接器範例</span><span class="sxs-lookup"><span data-stu-id="bf6b5-170">HTTP Adapter Samples</span></span>](../core/http-adapter-samples.md)