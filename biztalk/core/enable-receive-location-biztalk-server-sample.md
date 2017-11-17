---
title: "啟用接收位置 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, examples
- receive locations, enabling
- examples, receive locations
ms.assetid: dd04b38a-634d-4c9a-b31a-2f226fa91d19
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99923c3029b72dae660bee4b4089336e90e2e4e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="enable-receive-location-biztalk-server-sample"></a><span data-ttu-id="26625-102">啟用接收位置 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="26625-102">Enable Receive Location (BizTalk Server Sample)</span></span>
<span data-ttu-id="26625-103">「啟用接收位置」範例示範如何啟用接收位置，並選擇性地設定該接收位置的「輸入傳輸 URL」。</span><span class="sxs-lookup"><span data-stu-id="26625-103">The Enable Receive Location sample demonstrates how to enable a receive location and optionally set the Inbound Transport URL for that receive location.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="26625-104">如果在部署後不需要部署指令碼，就應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="26625-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="26625-105">必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。</span><span class="sxs-lookup"><span data-stu-id="26625-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="26625-106">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="26625-106">What This Sample Does</span></span>  
 <span data-ttu-id="26625-107">構成本範例之指令檔中的 Microsoft Visual Basic Scripting Edition (VBScript) 指令碼，會示範如何使用 BizTalk Server WMI 提供者來執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="26625-107">The Microsoft Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:</span></span>  
  
-   <span data-ttu-id="26625-108">在指定接收埠名稱和接收位置的情形下，查詢相符的接收位置清單。</span><span class="sxs-lookup"><span data-stu-id="26625-108">Given a receive port name and receive location, query for a list of matching receive locations.</span></span>  
  
-   <span data-ttu-id="26625-109">設定接收位置的輸入傳輸 URL (相對於安裝路徑)。</span><span class="sxs-lookup"><span data-stu-id="26625-109">Set the Inbound Transport URL for a receive location (relative to the installation path).</span></span>  
  
-   <span data-ttu-id="26625-110">啟用接收位置。</span><span class="sxs-lookup"><span data-stu-id="26625-110">Enable a receive location.</span></span>  
  
-   <span data-ttu-id="26625-111">處理任何錯誤，讓有意義的資訊能傳回給使用者。</span><span class="sxs-lookup"><span data-stu-id="26625-111">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="26625-112">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="26625-112">Where to Find This Sample</span></span>  
 <span data-ttu-id="26625-113">這個範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="26625-113">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="26625-114">\<*範例路徑*> \Admin\WMI\Enable 接收 Location\\</span><span class="sxs-lookup"><span data-stu-id="26625-114">\<*Samples Path*>\Admin\WMI\Enable Receive Location\\</span></span>  
  
 <span data-ttu-id="26625-115">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="26625-115">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="26625-116">檔案</span><span class="sxs-lookup"><span data-stu-id="26625-116">File(s)</span></span>|<span data-ttu-id="26625-117">Description</span><span class="sxs-lookup"><span data-stu-id="26625-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26625-118">在 \VBScript 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="26625-118">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="26625-119">EnableRecLoc.vbs</span><span class="sxs-lookup"><span data-stu-id="26625-119">EnableRecLoc.vbs</span></span>|<span data-ttu-id="26625-120">VBScript 檔案，其會接收指定要啟用之接收位置的參數，以及選擇性地指定與該接收位置關聯之「輸入傳輸 URL」新值的參數。</span><span class="sxs-lookup"><span data-stu-id="26625-120">VBScript file that takes parameters that specify a receive location to be enabled, and optionally, a new value for the Inbound Transport URL associated with that receive location.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="26625-121">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="26625-121">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="26625-122">「啟用接收位置」範例是由單一 VBScript 檔案組成，您並不需要建置或初始化該檔案。</span><span class="sxs-lookup"><span data-stu-id="26625-122">The Enable Receive Location sample consists of a single VBScript file that you do not need to build or initialize.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="26625-123">執行此範例</span><span class="sxs-lookup"><span data-stu-id="26625-123">Running This Sample</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="26625-124">執行此範例</span><span class="sxs-lookup"><span data-stu-id="26625-124">To run this sample</span></span>  
  
1.  <span data-ttu-id="26625-125">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="26625-125">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="26625-126">\<*範例路徑*> \Admin\WMI\Enable 接收 Location\VBScript\\</span><span class="sxs-lookup"><span data-stu-id="26625-126">\<*Samples Path*>\Admin\WMI\Enable Receive Location\VBScript\\</span></span>  
  
2.  <span data-ttu-id="26625-127">使用 cscript 程式執行 EnableRecLoc.vbs 檔案，並傳遞下列命令列引數，其中第三個引數是選擇性引數：</span><span class="sxs-lookup"><span data-stu-id="26625-127">Run the file EnableRecLoc.vbs using the cscript program, passing the following command-line arguments, of which the third one is optional:</span></span>  
  
    -   **\<**   
         <span data-ttu-id="26625-128">***ReceivePortName* >。**</span><span class="sxs-lookup"><span data-stu-id="26625-128">***ReceivePortName* >.**</span></span> <span data-ttu-id="26625-129">包含要啟用之接收位置的接收埠名稱。</span><span class="sxs-lookup"><span data-stu-id="26625-129">The name of the receive port that contains the receive location to be enabled.</span></span> <span data-ttu-id="26625-130">如果接收埠名稱包含空格，請用引號括住該名稱。</span><span class="sxs-lookup"><span data-stu-id="26625-130">If the receive port name contains spaces, enclose the name in quotes.</span></span>  
  
    -   **\<**   
         <span data-ttu-id="26625-131">***ReceiveLocationName* >。**</span><span class="sxs-lookup"><span data-stu-id="26625-131">***ReceiveLocationName* >.**</span></span> <span data-ttu-id="26625-132">要在指定之接收埠內啟用之接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="26625-132">The name of the receive location within the specified receive port to be enabled.</span></span> <span data-ttu-id="26625-133">如果接收位置名稱包含空格，請用引號括住該名稱。</span><span class="sxs-lookup"><span data-stu-id="26625-133">If the receive location name contains spaces, enclose the name in quotes.</span></span>  
  
    -   **\<**   
         <span data-ttu-id="26625-134">***InboundTransportURI* >。**</span><span class="sxs-lookup"><span data-stu-id="26625-134">***InboundTransportURI* >.**</span></span> <span data-ttu-id="26625-135">接收配接器 URI (相對於產品安裝位置)，您可以指定此引數來變更該 URI。</span><span class="sxs-lookup"><span data-stu-id="26625-135">A receive adapter URI, relative to the product installation location, that you can change by specifying this argument.</span></span> <span data-ttu-id="26625-136">如果輸入配接器 URI 包含空格，請用引號括住該 URI。</span><span class="sxs-lookup"><span data-stu-id="26625-136">If the inbound adapter URI contains spaces, enclose the URI in quotes.</span></span>  
  
         <span data-ttu-id="26625-137">例如：</span><span class="sxs-lookup"><span data-stu-id="26625-137">For example:</span></span>  
  
        ```  
        cscript EnableRecLoc.vbs "My Business Receive Port" MyBusinessReceiveLocation  
        ```  
  
         <span data-ttu-id="26625-138">-或-</span><span class="sxs-lookup"><span data-stu-id="26625-138">-OR-</span></span>  
  
        ```  
        cscript EnableRecLoc.vbs MyBusinessReceivePort "My Business Receive Location" SDK\Samples\HelloWorld\In\*.xml  
        ```  
  
## <a name="comments"></a><span data-ttu-id="26625-139">註解</span><span class="sxs-lookup"><span data-stu-id="26625-139">Comments</span></span>  
 <span data-ttu-id="26625-140">您也可以使用會存取 Windows WMI 物件模型的指令碼，執行所有可在 BizTalk Server 管理主控台中執行的工作。</span><span class="sxs-lookup"><span data-stu-id="26625-140">All tasks that you can perform in the BizTalk Server Administration console can also be performed by using script that accesses the Windows WMI object model.</span></span>  
  
 <span data-ttu-id="26625-141">指令檔 EnableRecLoc.vbs 包含詳細註解，內容會更進一步地解釋此檔案所執行作業的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="26625-141">The script file EnableRecLoc.vbs contains detailed comments with further explanation about the operations that it performs.</span></span>  
  
 <span data-ttu-id="26625-142">如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。</span><span class="sxs-lookup"><span data-stu-id="26625-142">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26625-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26625-143">See Also</span></span>  
 [<span data-ttu-id="26625-144">管理 WMI （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="26625-144">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)