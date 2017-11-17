---
title: "使用 BizTalk 配接器追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Adapter Trace Utility, installing
- installing, Adapter Trace Utility
- Adapter Trace Utility, enabling
- Adapter Trace Utility, running
- enabling, Adapter Trace Utility
ms.assetid: ddc6b2c7-9dee-43c1-950b-8fd580bfcb26
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45d83e1a250850d372c2e12c7ffebc79f823c287
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-biztalk-adapter-tracing"></a><span data-ttu-id="20ad6-102">使用 BizTalk 配接器追蹤</span><span class="sxs-lookup"><span data-stu-id="20ad6-102">Using BizTalk Adapter Tracing</span></span>
<span data-ttu-id="20ad6-103">本主題描述如何安裝 Trace Log tool (追蹤記錄工具) 以及如何啟用 BizTalk 配接器追蹤。</span><span class="sxs-lookup"><span data-stu-id="20ad6-103">This topic describes how to install the Trace Log tool and how to enable BizTalk adapter tracing.</span></span>  
  
## <a name="install-the-trace-log-tool"></a><span data-ttu-id="20ad6-104">安裝 Trace Log Tool (追蹤記錄工具)</span><span class="sxs-lookup"><span data-stu-id="20ad6-104">Install the Trace Log Tool</span></span>  
  
#### <a name="to-install-the-trace-log-tool-tracelogexe"></a><span data-ttu-id="20ad6-105">安裝 Trace Log tool (追蹤記錄工具) (tracelog.exe)</span><span class="sxs-lookup"><span data-stu-id="20ad6-105">To install the Trace Log tool (tracelog.exe)</span></span>  
  
1.  <span data-ttu-id="20ad6-106">從 [Microsoft® Windows® Software Development Kit Update for Windows Vista](http://go.microsoft.com/fwlink/?LinkId=128279) 網站 (英文) 下載追蹤記錄工具。</span><span class="sxs-lookup"><span data-stu-id="20ad6-106">Download the Trace Log tool from the [Microsoft® Windows® Software Development Kit Update for Windows Vista](http://go.microsoft.com/fwlink/?LinkId=128279) Web site.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20ad6-107">即使您是執行 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，也是安裝這個版本 (6.0) 的 SDK。</span><span class="sxs-lookup"><span data-stu-id="20ad6-107">Install this version (6.0) of the SDK even if you are running [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)].</span></span> <span data-ttu-id="20ad6-108">如果您安裝**Windows SDK for Windows Server 2008 和.NET Framework 3.5**版本 (v。</span><span class="sxs-lookup"><span data-stu-id="20ad6-108">If you install the **Windows SDK for Windows Server 2008 and .NET Framework 3.5** version (v.</span></span> <span data-ttu-id="20ad6-109">6.1)，則不會安裝追蹤記錄工具。</span><span class="sxs-lookup"><span data-stu-id="20ad6-109">6.1), it will not install the Trace Log tool.</span></span>  
  
2.  <span data-ttu-id="20ad6-110">按一下網頁下方的 **PSDK-x86.exe** 檔案連結，啟動 **Microsoft® Windows® Software Development Kit Update for Windows Vista** Web 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="20ad6-110">Start the **Microsoft® Windows® Software Development Kit Update for Windows Vista** Web installation program by clicking the link for the **PSDK-x86.exe** file at the bottom of the Web page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20ad6-111">如果您使用 64 位元版本的 Windows，請選擇適合您系統的正確下載檔案。</span><span class="sxs-lookup"><span data-stu-id="20ad6-111">If you are using a 64-bit version of Windows choose the correct files to download for your system.</span></span>  
  
3.  <span data-ttu-id="20ad6-112">在 [選取安裝類型]  對話方塊中，選擇 [自訂]  安裝的選項，然後再按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="20ad6-112">In the **Select an Installation Type** dialog box, choose the option for a **Custom** installation, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="20ad6-113">接受預設安裝位置，然後按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="20ad6-113">Accept the default installation location and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="20ad6-114">在 **[自訂安裝]** 對話方塊中，按一下以清除所有可用的功能。</span><span class="sxs-lookup"><span data-stu-id="20ad6-114">In the **Custom Installation** dialog box, click to clear all the available features.</span></span>  
  
6.  <span data-ttu-id="20ad6-115">展開 **[Microsoft Windows Core SDK]** 功能，然後展開 **[工具]** 功能。</span><span class="sxs-lookup"><span data-stu-id="20ad6-115">Expand the **Microsoft Windows Core SDK** feature, and then expand the **Tools** feature.</span></span>  
  
7.  <span data-ttu-id="20ad6-116">選擇 **[工具 (Intel 64 位元)]** 功能，然後按一下 **[將會安裝至本機硬碟]**。</span><span class="sxs-lookup"><span data-stu-id="20ad6-116">Choose the **Tools (Intel 64-bit)** feature, and then click **Will be installed on local hard drive**.</span></span>  
  
8.  <span data-ttu-id="20ad6-117">按 **[下一步]**，然後再按 **[下一步]** ，以開始安裝。</span><span class="sxs-lookup"><span data-stu-id="20ad6-117">Click **Next**, and then click **Next** again to start the installation.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20ad6-118">在安裝 **Microsoft ® Windows ® Software Development Kit Update for Windows Vista** 之後，可能會提示您重新開機，視您選擇要與追蹤記錄工具一起安裝的其他功能而定。</span><span class="sxs-lookup"><span data-stu-id="20ad6-118">After installing the **Microsoft® Windows® Software Development Kit Update for Windows Vista** you may be prompted to reboot depending upon what other features you chose to install along with the Trace Log tool.</span></span> <span data-ttu-id="20ad6-119">這是因為 **Microsoft ® Windows ® Software Development Kit Update for Windows Vista** 的特定元件必須等到完成重新開機之後才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="20ad6-119">This is because certain components of the **Microsoft® Windows® Software Development Kit Update for Windows Vista** will not function correctly until the reboot has been completed.</span></span> <span data-ttu-id="20ad6-120">Trace Log tool (追蹤記錄工具) 不需重新開機就可使用。</span><span class="sxs-lookup"><span data-stu-id="20ad6-120">You do not need to reboot to use the Trace Log tool.</span></span>  
  
## <a name="enable-biztalk-adapter-tracing-with-tracecmd"></a><span data-ttu-id="20ad6-121">使用 trace.cmd 啟用 BizTalk 配接器追蹤</span><span class="sxs-lookup"><span data-stu-id="20ad6-121">Enable BizTalk Adapter Tracing with trace.cmd</span></span>  
  
#### <a name="to-enable-biztalk-adapter-tracing"></a><span data-ttu-id="20ad6-122">啟用 BizTalk 配接器追蹤</span><span class="sxs-lookup"><span data-stu-id="20ad6-122">To enable BizTalk adapter tracing</span></span>  
  
1.  <span data-ttu-id="20ad6-123">在命令提示字元，將目前的目錄變更為已安裝 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 的目錄。</span><span class="sxs-lookup"><span data-stu-id="20ad6-123">At a command prompt, change the current directory to the directory where [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] is installed.</span></span> <span data-ttu-id="20ad6-124">根據預設，[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]安裝在[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]目錄。</span><span class="sxs-lookup"><span data-stu-id="20ad6-124">By default, [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] is installed in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] directory.</span></span>  <span data-ttu-id="20ad6-125">如果使用 64 位元版本的 Windows 和[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，安裝路徑是[!INCLUDE[btsBizTalkServerPathx64](../includes/btsbiztalkserverpathx64-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="20ad6-125">If using a 64-bit version of Windows and [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], the installation path is [!INCLUDE[btsBizTalkServerPathx64](../includes/btsbiztalkserverpathx64-md.md)].</span></span>  
  
2.  <span data-ttu-id="20ad6-126">輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="20ad6-126">Type the following command, and then press ENTER:</span></span>  
  
     <span data-ttu-id="20ad6-127">**trace-tools"追蹤記錄工具的路徑 」**</span><span class="sxs-lookup"><span data-stu-id="20ad6-127">**trace -tools "Path of the Trace Log tool"**</span></span>  
  
     <span data-ttu-id="20ad6-128">依照預設，追蹤記錄工具 (tracelog.exe) 位於 **C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin** 目錄中。</span><span class="sxs-lookup"><span data-stu-id="20ad6-128">By default, the Trace Log tool (tracelog.exe) is located in the **C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin** directory.</span></span> <span data-ttu-id="20ad6-129">如果使用 64 位元版本的 Windows，追蹤記錄工具位於 **C:\Program Files (x86)\Microsoft SDKs\Windows\v6.0\Bin**。</span><span class="sxs-lookup"><span data-stu-id="20ad6-129">If using a 64-bit version of Windows the Trace Log tool is located at **C:\Program Files (x86)\Microsoft SDKs\Windows\v6.0\Bin**.</span></span>  <span data-ttu-id="20ad6-130">您必須用引號括住追蹤記錄工具的路徑。</span><span class="sxs-lookup"><span data-stu-id="20ad6-130">You must enclose the path of the Trace Log tool in quotation marks.</span></span>  
  
     <span data-ttu-id="20ad6-131">例如，輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="20ad6-131">For example, type the following command, and then press ENTER:</span></span>  
  
     <span data-ttu-id="20ad6-132">**trace-tools"C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin"**</span><span class="sxs-lookup"><span data-stu-id="20ad6-132">**trace -tools "C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin"**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20ad6-133">**-tools** 參數在 Trace.cmd 檔案中指示 Tracelog.exe 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="20ad6-133">The **-tools** switch indicates to the Trace.cmd file the location of the Tracelog.exe file.</span></span>  
    >   
    >  <span data-ttu-id="20ad6-134">如果命令成功執行，則輸出類似如下：</span><span class="sxs-lookup"><span data-stu-id="20ad6-134">If the command successfully runs, the output will be like below:</span></span>  
    >   
    >  <span data-ttu-id="20ad6-135">**追蹤 2.0-管理 BizTalk 2006 版本位元追蹤。**</span><span class="sxs-lookup"><span data-stu-id="20ad6-135">**trace 2.0 - Manage BizTalk 2006 Release Bits Tracing.**</span></span>  
    >   
    >  <span data-ttu-id="20ad6-136">**設定到"C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin"TRACE_TOOL_SEARCH_PATH**</span><span class="sxs-lookup"><span data-stu-id="20ad6-136">**Setting TRACE_TOOL_SEARCH_PATH to "C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin "**</span></span>  
  
## <a name="capture-trace-output-with-tracecmd"></a><span data-ttu-id="20ad6-137">使用 trace.cmd 擷取追蹤輸入</span><span class="sxs-lookup"><span data-stu-id="20ad6-137">Capture Trace output with trace.cmd</span></span>  
  
#### <a name="to-capture-trace-output"></a><span data-ttu-id="20ad6-138">擷取追蹤輸入</span><span class="sxs-lookup"><span data-stu-id="20ad6-138">To capture trace output</span></span>  
  
1.  <span data-ttu-id="20ad6-139">在命令提示字元，將目前的目錄變更為已安裝 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 的目錄。</span><span class="sxs-lookup"><span data-stu-id="20ad6-139">At a command prompt, change the current directory to the directory where [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] is installed.</span></span>  
  
2.  <span data-ttu-id="20ad6-140">在命令提示字元，輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="20ad6-140">At a command prompt, type the following command, and then press ENTER:</span></span>  
  
     <span data-ttu-id="20ad6-141">**追蹤-開始**</span><span class="sxs-lookup"><span data-stu-id="20ad6-141">**trace -start**</span></span>  
  
3.  <span data-ttu-id="20ad6-142">重現要擷取追蹤輸出的實例。</span><span class="sxs-lookup"><span data-stu-id="20ad6-142">Reproduce the scenario for which you want to capture trace output.</span></span>  
  
4.  <span data-ttu-id="20ad6-143">在命令提示字元，輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="20ad6-143">At a command prompt, type the following command, and then press ENTER:</span></span>  
  
     <span data-ttu-id="20ad6-144">**追蹤-停止**</span><span class="sxs-lookup"><span data-stu-id="20ad6-144">**trace -stop**</span></span>  
  
5.  <span data-ttu-id="20ad6-145">停止追蹤，名為二進位檔案之後**Btstrace.bin**資料夾中產生其中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="20ad6-145">After you stop the trace, a binary file that is named **Btstrace.bin** is generated in the folder where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed.</span></span>  
  
6.  <span data-ttu-id="20ad6-146">可以將 **Btstrace.bin** 檔案傳送至 Microsoft 產品支援服務以供分析。</span><span class="sxs-lookup"><span data-stu-id="20ad6-146">Send the **Btstrace.bin** file to Microsoft Product Support Services for analysis.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ad6-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20ad6-147">See Also</span></span>  
 <span data-ttu-id="20ad6-148">[使用配接器](../core/using-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="20ad6-148">[Using Adapters](../core/using-adapters.md) </span></span>  
 [<span data-ttu-id="20ad6-149">Windows SharePoint Services 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="20ad6-149">Troubleshooting the Windows SharePoint Services Adapter</span></span>](../core/troubleshooting-the-windows-sharepoint-services-adapter.md)