---
title: "移除接收埠 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive ports, examples
- deleting, receive ports
- examples, receive ports
- receive ports, deleting
ms.assetid: de97d914-b8e8-4365-8041-3b455c351f86
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b97c3b6fe5e743e6bf19c979b994cc7eb5a942de
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="remove-receive-port-biztalk-server-sample"></a><span data-ttu-id="2ce9f-102">移除接收埠 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="2ce9f-102">Remove Receive Port (BizTalk Server Sample)</span></span>
<span data-ttu-id="2ce9f-103">「移除接收埠」範例會示範如何移除一或多個接收埠。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-103">The Remove Receive Port sample demonstrates how to remove one or more receive ports.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="2ce9f-104">如果在部署後不需要部署指令碼，就應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="2ce9f-105">必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="2ce9f-106">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="2ce9f-106">What This Sample Does</span></span>  
 <span data-ttu-id="2ce9f-107">構成本範例之指令檔中的 Visual Basic Scripting Edition (VBScript) 指令碼，會示範如何使用 BizTalk Server WMI 提供者來執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="2ce9f-107">The Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:</span></span>  
  
-   <span data-ttu-id="2ce9f-108">指定接收埠名稱，查詢相符的接收埠的清單。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-108">Given a receive port name, query for a list of matching receive ports.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ce9f-109">一般而言，只有一個接收埠會符合指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-109">Generally, there will only be one receive port that matches a given name.</span></span>  
  
-   <span data-ttu-id="2ce9f-110">移除這些接收埠。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-110">Remove those receive ports.</span></span>  
  
-   <span data-ttu-id="2ce9f-111">處理任何錯誤，讓有意義的資訊能傳回給使用者。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-111">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="2ce9f-112">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="2ce9f-112">Where to Find This Sample</span></span>  
 <span data-ttu-id="2ce9f-113">這些範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="2ce9f-113">The samples are located in the following SDK location:</span></span>  
  
 <span data-ttu-id="2ce9f-114">\<*範例路徑*> \Admin\WMI\Remove 接收 Port\\</span><span class="sxs-lookup"><span data-stu-id="2ce9f-114">\<*Samples Path*>\Admin\WMI\Remove Receive Port\\</span></span>  
  
 <span data-ttu-id="2ce9f-115">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-115">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="2ce9f-116">檔案</span><span class="sxs-lookup"><span data-stu-id="2ce9f-116">File(s)</span></span>|<span data-ttu-id="2ce9f-117">Description</span><span class="sxs-lookup"><span data-stu-id="2ce9f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ce9f-118">在 \VBScript 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="2ce9f-118">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="2ce9f-119">RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="2ce9f-119">RemoveReceivePort.vbs</span></span>|<span data-ttu-id="2ce9f-120">VBScript 檔案，它會接收特定參數來指定一或多個要移除的接收埠。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-120">VBScript file that takes a parameter that specifies one or more receive ports to remove.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="2ce9f-121">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="2ce9f-121">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="2ce9f-122">「移除接收埠」範例是由單一的 VBScript 檔案組成，而您並不需要建置或初始化該檔案。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-122">The Remove Receive Port sample consists of a single VBScript file that you do not need to build or initialize.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="2ce9f-123">執行此範例</span><span class="sxs-lookup"><span data-stu-id="2ce9f-123">Running This Sample</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="2ce9f-124">執行此範例</span><span class="sxs-lookup"><span data-stu-id="2ce9f-124">To run this sample</span></span>  
  
1.  <span data-ttu-id="2ce9f-125">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="2ce9f-125">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="2ce9f-126">\<*範例路徑*> \Admin\WMI\Remove 接收 Port\VBScript\\</span><span class="sxs-lookup"><span data-stu-id="2ce9f-126">\<*Samples Path*>\Admin\WMI\Remove Receive Port\VBScript\\</span></span>  
  
2.  <span data-ttu-id="2ce9f-127">使用 cscript 程式執行 RemoveReceivePort.vbs 檔案，並傳遞下列命令列引數：</span><span class="sxs-lookup"><span data-stu-id="2ce9f-127">Run the file RemoveReceivePort.vbs using the cscript program, passing the following command-line argument:</span></span>  
  
     **\<**   
     <span data-ttu-id="2ce9f-128">***ReceivePortName* >**。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-128">***ReceivePortName* >**.</span></span> <span data-ttu-id="2ce9f-129">要移除之接收埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-129">The name of the receive port(s) to remove.</span></span> <span data-ttu-id="2ce9f-130">如果接收埠名稱包含空格，請用引號括住該名稱。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-130">If the receive port name contains spaces, enclose the name in quotes.</span></span>  
  
     <span data-ttu-id="2ce9f-131">例如：</span><span class="sxs-lookup"><span data-stu-id="2ce9f-131">For example:</span></span>  
  
    ```  
    cscript RemoveReceivePort.vbs "My Business Receive Port"  
    ```  
  
## <a name="comments"></a><span data-ttu-id="2ce9f-132">註解</span><span class="sxs-lookup"><span data-stu-id="2ce9f-132">Comments</span></span>  
 <span data-ttu-id="2ce9f-133">您也可以使用會存取 Windows WMI 物件模型的指令碼，執行所有可在 BizTalk Server 管理主控台中執行的工作。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-133">All tasks that you can perform in the BizTalk Server Administration console can also be performed by using script that accesses the Windows WMI object model.</span></span>  
  
 <span data-ttu-id="2ce9f-134">指令檔 RemoveReceivePort.vbs 包含詳細註解，內容會更進一步地解釋此檔案所執行作業的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-134">The script file RemoveReceivePort.vbs contains detailed comments with further explanation about the operations that it performs.</span></span> <span data-ttu-id="2ce9f-135">如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。</span><span class="sxs-lookup"><span data-stu-id="2ce9f-135">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ce9f-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ce9f-136">See Also</span></span>  
 [<span data-ttu-id="2ce9f-137">管理 WMI （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="2ce9f-137">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)