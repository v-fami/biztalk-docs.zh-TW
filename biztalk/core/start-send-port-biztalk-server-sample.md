---
title: "啟動傳送埠 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, examples
- examples, send ports
- send ports, starting
ms.assetid: 84e54c9e-e9e8-4bb2-a191-20c29e127dae
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f293d00848c32f6b519349543c8a39824d9bca8c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="start-send-port-biztalk-server-sample"></a><span data-ttu-id="73a0f-102">啟動傳送埠 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="73a0f-102">Start Send Port (BizTalk Server Sample)</span></span>
<span data-ttu-id="73a0f-103">「啟動傳送埠」範例示範如何在使用 FILE 配接器時啟動傳送埠並選擇性地設定主要傳輸位址。</span><span class="sxs-lookup"><span data-stu-id="73a0f-103">The Start Send Port sample demonstrates how to start a send port and optionally set the Primary Transport Address when using the FILE adapter.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="73a0f-104">如果在部署後不需要部署指令碼，就應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="73a0f-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="73a0f-105">必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。</span><span class="sxs-lookup"><span data-stu-id="73a0f-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="73a0f-106">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="73a0f-106">What This Sample Does</span></span>  
 <span data-ttu-id="73a0f-107">構成本範例之指令檔中的 Visual Basic Scripting Edition (VBScript) 指令碼，會示範如何使用 BizTalk Server WMI 提供者來執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="73a0f-107">The Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:</span></span>  
  
-   <span data-ttu-id="73a0f-108">在指定傳送埠名稱情況下，查詢相符傳送埠的清單。</span><span class="sxs-lookup"><span data-stu-id="73a0f-108">Given a send port name, query for a list of matching send ports.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="73a0f-109">一般而言，只有一個傳送埠會符合指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="73a0f-109">Generally, there will only be one send port that matches a given name.</span></span>  
  
-   <span data-ttu-id="73a0f-110">設定這些傳送埠的主要傳輸位址 (相對於安裝路徑)。</span><span class="sxs-lookup"><span data-stu-id="73a0f-110">Set the Primary Transport Address for those send ports (relative to the installation path).</span></span>  
  
-   <span data-ttu-id="73a0f-111">啟動這些傳送埠。</span><span class="sxs-lookup"><span data-stu-id="73a0f-111">Start those send ports.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="73a0f-112">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="73a0f-112">Where to Find This Sample</span></span>  
 <span data-ttu-id="73a0f-113">這些範例檔案位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="73a0f-113">The sample files are located in the following SDK location:</span></span>  
  
 <span data-ttu-id="73a0f-114">\<*範例路徑*\>\Admin\WMI\Start 傳送 Port\\</span><span class="sxs-lookup"><span data-stu-id="73a0f-114">\<*Samples Path*\>\Admin\WMI\Start Send Port\\</span></span>  
  
 <span data-ttu-id="73a0f-115">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="73a0f-115">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="73a0f-116">檔案</span><span class="sxs-lookup"><span data-stu-id="73a0f-116">File(s)</span></span>|<span data-ttu-id="73a0f-117">Description</span><span class="sxs-lookup"><span data-stu-id="73a0f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73a0f-118">在 \VBScript 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="73a0f-118">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="73a0f-119">StartSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="73a0f-119">StartSendPort.vbs</span></span>|<span data-ttu-id="73a0f-120">VBScript 檔案，其使用參數指定要啟動的傳送埠，並選擇性地指定與該傳送埠相關聯之主要傳輸位址的新值。</span><span class="sxs-lookup"><span data-stu-id="73a0f-120">VBScript file that takes parameters that specify a send port to start, and optionally, a new value for the Primary Transport Address associated with that port.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="73a0f-121">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="73a0f-121">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="73a0f-122">「啟動傳送埠」範例是由單一的 VBScript 檔案組成，而您並不需要建置或初始化該檔案。</span><span class="sxs-lookup"><span data-stu-id="73a0f-122">The Start Send Port sample consists of a single VBScript file that you do not need to build or initialize.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="73a0f-123">執行此範例</span><span class="sxs-lookup"><span data-stu-id="73a0f-123">Running This Sample</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="73a0f-124">執行此範例</span><span class="sxs-lookup"><span data-stu-id="73a0f-124">To run this sample</span></span>  
  
1.  <span data-ttu-id="73a0f-125">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="73a0f-125">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="73a0f-126">\<*範例路徑*\>\Admin\WMI\Start 傳送 Port\VBScript\\</span><span class="sxs-lookup"><span data-stu-id="73a0f-126">\<*Samples Path*\>\Admin\WMI\Start Send Port\VBScript\\</span></span>  
  
2.  <span data-ttu-id="73a0f-127">使用 cscript 程式執行 StartSendPort.vbs 檔案，以便傳遞下列命令列引數，其中第二個引數是選用項目：</span><span class="sxs-lookup"><span data-stu-id="73a0f-127">Run the file StartSendPort.vbs using the cscript program, passing the following command-line arguments, the second of which is optional:</span></span>  
  
    -   <span data-ttu-id="73a0f-128">**\<** ***SendPortName* \>。**</span><span class="sxs-lookup"><span data-stu-id="73a0f-128">**\<** ***SendPortName* \>.**</span></span> <span data-ttu-id="73a0f-129">要啟動之傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="73a0f-129">The name of the send port to start.</span></span> <span data-ttu-id="73a0f-130">如果傳送埠名稱包含空格，請用引號括住該名稱。</span><span class="sxs-lookup"><span data-stu-id="73a0f-130">If the send port name contains spaces, enclose the name in quotes.</span></span>  
  
    -   <span data-ttu-id="73a0f-131">**\<** ***PrimaryTransportAddress* \>。**</span><span class="sxs-lookup"><span data-stu-id="73a0f-131">**\<** ***PrimaryTransportAddress* \>.**</span></span> <span data-ttu-id="73a0f-132">主要傳輸位址 (相對於產品安裝位置)，藉由指定此參數可加以變更。</span><span class="sxs-lookup"><span data-stu-id="73a0f-132">The Primary Transport Address, relative to the product installation location, that you can change by specifying this argument.</span></span> <span data-ttu-id="73a0f-133">如果主要配接器位址包含空格，請用引號括住此位址。</span><span class="sxs-lookup"><span data-stu-id="73a0f-133">If the primary adapter address contains spaces, enclose the name in quotes.</span></span>  
  
         <span data-ttu-id="73a0f-134">例如：</span><span class="sxs-lookup"><span data-stu-id="73a0f-134">For example:</span></span>  
  
        ```  
        cscript StartSendPort.vbs "My Business Send Port" SDK\Samples\HelloWorld\Out\%MessageID%.xml  
        ```  
  
## <a name="comments"></a><span data-ttu-id="73a0f-135">註解</span><span class="sxs-lookup"><span data-stu-id="73a0f-135">Comments</span></span>  
 <span data-ttu-id="73a0f-136">您也可以使用會存取 Windows WMI 物件模型的指令碼，執行所有可在 BizTalk Server 管理主控台中執行的工作。</span><span class="sxs-lookup"><span data-stu-id="73a0f-136">All tasks that you can perform in the BizTalk Server Administration console can also be performed by using script that accesses the Windows WMI object model.</span></span>  
  
 <span data-ttu-id="73a0f-137">指令檔 StartSendPort.vbs 包含詳細註解，其中含有其所執行作業的深入說明。</span><span class="sxs-lookup"><span data-stu-id="73a0f-137">The script file StartSendPort.vbs contains detailed comments with further explanation about the operations that it performs.</span></span> <span data-ttu-id="73a0f-138">如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。</span><span class="sxs-lookup"><span data-stu-id="73a0f-138">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a0f-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="73a0f-139">See Also</span></span>  
 [<span data-ttu-id="73a0f-140">Admin-WMI (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="73a0f-140">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)