---
title: "XSLT 轉換元件 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], examples
- examples, pipeline components [custom]
- XSLT, examples
- examples, XSLT
ms.assetid: 9152e897-4db9-4924-b37e-fd9e908dbef1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8374e2069660998a46265986125b6b0159ea1961
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="xslt-transform-component-biztalk-server-sample"></a><span data-ttu-id="3a034-102">XSLT 轉換元件 (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="3a034-102">XSLT Transform Component (BizTalk Server Sample)</span></span>
<span data-ttu-id="3a034-103">「XSLT 轉換元件」範例示範如何使用 XSLT 撰寫自訂管線元件以轉換 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="3a034-103">The XSLT Transform Component sample demonstrates how to write a custom pipeline component to transform an XML message using XSLT.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="3a034-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="3a034-104">What This Sample Does</span></span>  
 <span data-ttu-id="3a034-105">該範例完成轉換的步驟如下：</span><span class="sxs-lookup"><span data-stu-id="3a034-105">The sample accomplishes the transformation with the following steps:</span></span>  
  
1.  <span data-ttu-id="3a034-106">從資料夾擷取 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="3a034-106">An XML document is retrieved from a folder.</span></span>  
  
2.  <span data-ttu-id="3a034-107">管線使用 Transform.xsl 將 XML 文件轉換為 HTML 電子郵件內文。</span><span class="sxs-lookup"><span data-stu-id="3a034-107">The pipeline transforms the XML document into the HTML body of an e-mail message using Transform.xsl.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="3a034-108">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="3a034-108">Where to Find This Sample</span></span>  
 <span data-ttu-id="3a034-109">*\<範例路徑 >*\Pipelines\XslTransformComponent\\</span><span class="sxs-lookup"><span data-stu-id="3a034-109">*\<Samples Path>*\Pipelines\XslTransformComponent\\</span></span>  
  
 <span data-ttu-id="3a034-110">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="3a034-110">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="3a034-111">檔案</span><span class="sxs-lookup"><span data-stu-id="3a034-111">File(s)</span></span>|<span data-ttu-id="3a034-112">Description</span><span class="sxs-lookup"><span data-stu-id="3a034-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a034-113">AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="3a034-113">AssemblyInfo.cs</span></span>|<span data-ttu-id="3a034-114">C# 組件檔案。</span><span class="sxs-lookup"><span data-stu-id="3a034-114">C# assembly file.</span></span>|  
|<span data-ttu-id="3a034-115">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="3a034-115">Cleanup.bat</span></span>|<span data-ttu-id="3a034-116">範例清除檔。</span><span class="sxs-lookup"><span data-stu-id="3a034-116">Sample cleanup file.</span></span>|  
|<span data-ttu-id="3a034-117">Confirmation.xsd</span><span class="sxs-lookup"><span data-stu-id="3a034-117">Confirmation.xsd</span></span>|<span data-ttu-id="3a034-118">範例結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="3a034-118">Sample schema file.</span></span>|  
|<span data-ttu-id="3a034-119">DocInstance.xml</span><span class="sxs-lookup"><span data-stu-id="3a034-119">DocInstance.xml</span></span>|<span data-ttu-id="3a034-120">用來轉換的範例 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="3a034-120">Sample .xml file to transform.</span></span>|  
|<span data-ttu-id="3a034-121">SendHtmlMessage.btproj</span><span class="sxs-lookup"><span data-stu-id="3a034-121">SendHtmlMessage.btproj</span></span>|<span data-ttu-id="3a034-122">BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="3a034-122">BizTalk project.</span></span>|  
|<span data-ttu-id="3a034-123">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="3a034-123">Setup.bat</span></span>|<span data-ttu-id="3a034-124">組態批次檔。</span><span class="sxs-lookup"><span data-stu-id="3a034-124">Configuration batch file.</span></span>|  
|<span data-ttu-id="3a034-125">Xml2HtmlSendPipeline.btp</span><span class="sxs-lookup"><span data-stu-id="3a034-125">Xml2HtmlSendPipeline.btp</span></span>|<span data-ttu-id="3a034-126">BizTalk Server 管線檔。</span><span class="sxs-lookup"><span data-stu-id="3a034-126">BizTalk Server pipeline file.</span></span>|  
|<span data-ttu-id="3a034-127">XslTransform.csproj</span><span class="sxs-lookup"><span data-stu-id="3a034-127">XslTransform.csproj</span></span>|<span data-ttu-id="3a034-128">C# 專案。</span><span class="sxs-lookup"><span data-stu-id="3a034-128">C# project.</span></span>|  
|<span data-ttu-id="3a034-129">XslTransformComponent.sln</span><span class="sxs-lookup"><span data-stu-id="3a034-129">XslTransformComponent.sln</span></span>|<span data-ttu-id="3a034-130">範例解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="3a034-130">Sample solution file.</span></span>|  
|<span data-ttu-id="3a034-131">XslTransformComponentBinding.XML</span><span class="sxs-lookup"><span data-stu-id="3a034-131">XslTransformComponentBinding.XML</span></span>|<span data-ttu-id="3a034-132">XML 繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="3a034-132">XML binding file.</span></span>|  
|<span data-ttu-id="3a034-133">XslTransformer.cs</span><span class="sxs-lookup"><span data-stu-id="3a034-133">XslTransformer.cs</span></span>|<span data-ttu-id="3a034-134">C# 原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="3a034-134">C# source code.</span></span>|  
|<span data-ttu-id="3a034-135">Transform.xsl</span><span class="sxs-lookup"><span data-stu-id="3a034-135">Transform.xsl</span></span>|<span data-ttu-id="3a034-136">用來轉換 DocInstance.xml 的 XSLT 檔案。</span><span class="sxs-lookup"><span data-stu-id="3a034-136">XSLT file used to transform DocInstance.xml.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="3a034-137">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="3a034-137">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="3a034-138">請使用下列程序，建置和初始化「XSLT 轉換元件」範例。</span><span class="sxs-lookup"><span data-stu-id="3a034-138">Use the following procedure to build and initialize the XSLT Transform Component sample.</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="3a034-139">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="3a034-139">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="3a034-140">在命令視窗中，將目錄變更 (**cd)**至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="3a034-140">In a command window, change directory (**cd)** to the following folder:</span></span>  
  
     <span data-ttu-id="3a034-141">*\<範例路徑 >*\Pipelines\XslTransformComponent</span><span class="sxs-lookup"><span data-stu-id="3a034-141">*\<Samples Path>*\Pipelines\XslTransformComponent</span></span>  
  
2.  <span data-ttu-id="3a034-142">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3a034-142">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="3a034-143">建立範例中所用之輸入 (\In) 和輸出 (\Out) 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3a034-143">Creates the input (\In) and output (\Out) folders used in the sample.</span></span>  
  
    -   <span data-ttu-id="3a034-144">產生新的金鑰檔案。</span><span class="sxs-lookup"><span data-stu-id="3a034-144">Generates a new key file.</span></span>  
  
    -   <span data-ttu-id="3a034-145">建置和部署「XSLT 轉換元件」管線。</span><span class="sxs-lookup"><span data-stu-id="3a034-145">Builds and deploys the XSLT Transform Component pipeline.</span></span>  
  
    -   <span data-ttu-id="3a034-146">若要建置的管線元件會將複製\<安裝路徑 > \Pipeline Components 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3a034-146">Copies the built pipeline component to the \<Installation Path>\Pipeline Components folder.</span></span>  
  
    -   <span data-ttu-id="3a034-147">建立傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="3a034-147">Creates the send and receive ports.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3a034-148">在嘗試執行此範例之前，您應該確認在建置和初始化程序期間沒有報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="3a034-148">You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3a034-149">若要復原 Setup.bat 所產生的變更，您必須先從 BizTalk Server 管理 MMC 主控台停止並重新啟動該主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a034-149">To undo changes made by Setup.bat, you must first stop and restart the host instance from the BizTalk Server Administration MMC console.</span></span> <span data-ttu-id="3a034-150">接著，執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="3a034-150">Next, run Cleanup.bat.</span></span> <span data-ttu-id="3a034-151">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="3a034-151">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="3a034-152">執行此範例</span><span class="sxs-lookup"><span data-stu-id="3a034-152">Running This Sample</span></span>  
 <span data-ttu-id="3a034-153">請使用下列程序，執行「XSLT 轉換元件」範例。</span><span class="sxs-lookup"><span data-stu-id="3a034-153">Use the following procedure to run the XSLT Transform Component sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="3a034-154">執行此範例</span><span class="sxs-lookup"><span data-stu-id="3a034-154">To run this sample</span></span>  
  
1.  <span data-ttu-id="3a034-155">將 DocInstance.xml 複製至 \In 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3a034-155">Copy DocInstance.xml to the \In folder.</span></span>  
  
2.  <span data-ttu-id="3a034-156">檢查 \Out 資料夾中的結果 (輸出檔名為 guid.htm)。</span><span class="sxs-lookup"><span data-stu-id="3a034-156">Examine the results in the \Out folder (the output filename is guid.htm).</span></span>  
  
## <a name="configuring-this-sample-using-smtp"></a><span data-ttu-id="3a034-157">使用 SMTP 設定此範例</span><span class="sxs-lookup"><span data-stu-id="3a034-157">Configuring This Sample Using SMTP</span></span>  
 <span data-ttu-id="3a034-158">請使用下列程序，將「XSLT 轉換元件」範例設定為與 SMTP 伺服器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="3a034-158">Use the following procedure to configure the XSLT Transform Component sample to work with an SMTP server.</span></span>  
  
#### <a name="to-configure-this-sample-using-smtp"></a><span data-ttu-id="3a034-159">若要使用 SMTP 設定此範例</span><span class="sxs-lookup"><span data-stu-id="3a034-159">To configure this sample using SMTP</span></span>  
  
1.  <span data-ttu-id="3a034-160">將「XSLT 轉換元件」傳送埠重新設定為使用 SMTP 傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="3a034-160">Reconfigure the XSLT Transform Component send port to use an SMTP transport type.</span></span>  
  
2.  <span data-ttu-id="3a034-161">將位址 (URL) 參數變更為符合您的 SMTP 組態以設定 SMTP 設定。</span><span class="sxs-lookup"><span data-stu-id="3a034-161">Configure the SMTP setting by changing the address (URI) parameters to match your SMTP configuration.</span></span>  
  
## <a name="running-this-sample-with-output-to-an-smtp-port"></a><span data-ttu-id="3a034-162">執行此範例並輸出至 SMTP 連接埠</span><span class="sxs-lookup"><span data-stu-id="3a034-162">Running This Sample with Output to an SMTP Port</span></span>  
 <span data-ttu-id="3a034-163">請使用下列程序，執行「XSLT 轉換元件」範例並輸出至 SMTP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="3a034-163">Use the following procedure to run the XSLT Transform Component sample with output to an SMTP port.</span></span>  
  
#### <a name="to-run-this-sample-with-output-to-an-smtp-port"></a><span data-ttu-id="3a034-164">若要執行此範例並輸出至 SMTP 連接埠</span><span class="sxs-lookup"><span data-stu-id="3a034-164">To run this sample with output to an SMTP port</span></span>  
  
1.  <span data-ttu-id="3a034-165">將 DocInstance.xml 複製至 \In 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3a034-165">Copy DocInstance.xml to the \In folder.</span></span>  
  
2.  <span data-ttu-id="3a034-166">檢查 SMTP 設定之傳送目標接收者的郵件用戶端中的結果。</span><span class="sxs-lookup"><span data-stu-id="3a034-166">Examine the results in the mail client for the recipient that SMTP is configured to send to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a034-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a034-167">See Also</span></span>  
 [<span data-ttu-id="3a034-168">管線 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="3a034-168">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)