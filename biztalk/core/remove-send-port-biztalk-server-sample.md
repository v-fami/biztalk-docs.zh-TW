---
title: "移除傳送埠 （BizTalk Server 範例） |Microsoft 文件"
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
- send ports, deleting
- deleting, send ports
ms.assetid: e6643525-fa9f-4d39-880f-314749a68471
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8b82af2be42342d51429e42d1952816ee0dd07a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="remove-send-port-biztalk-server-sample"></a><span data-ttu-id="fc18a-102">移除傳送埠 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="fc18a-102">Remove Send Port (BizTalk Server Sample)</span></span>
<span data-ttu-id="fc18a-103">「移除傳送埠」範例會示範如何取消登錄一或多個傳送埠，並且將其移除。</span><span class="sxs-lookup"><span data-stu-id="fc18a-103">The Remove Send Port sample demonstrates how to unenlist and remove one or more send ports.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="fc18a-104">如果在部署後不需要部署指令碼，就應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="fc18a-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="fc18a-105">必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。</span><span class="sxs-lookup"><span data-stu-id="fc18a-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="fc18a-106">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="fc18a-106">What This Sample Does</span></span>  
 <span data-ttu-id="fc18a-107">構成本範例之指令檔中的 Visual Basic Scripting Edition (VBScript) 指令碼，會示範如何使用 BizTalk Server WMI 提供者來執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="fc18a-107">The Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:</span></span>  
  
-   <span data-ttu-id="fc18a-108">在指定傳送埠名稱情況下，查詢相符傳送埠的清單。</span><span class="sxs-lookup"><span data-stu-id="fc18a-108">Given a send port name, query for a list of matching send ports.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc18a-109">一般而言，只有一個傳送埠會符合指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="fc18a-109">Generally, there will only be one send port that matches a given name.</span></span>  
  
-   <span data-ttu-id="fc18a-110">取消登錄這些傳送埠。</span><span class="sxs-lookup"><span data-stu-id="fc18a-110">Unenlist those send ports.</span></span>  
  
-   <span data-ttu-id="fc18a-111">刪除這些傳送埠。</span><span class="sxs-lookup"><span data-stu-id="fc18a-111">Delete those send ports.</span></span>  
  
-   <span data-ttu-id="fc18a-112">處理任何錯誤，讓有意義的資訊能傳回給使用者。</span><span class="sxs-lookup"><span data-stu-id="fc18a-112">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="fc18a-113">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="fc18a-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="fc18a-114">這個範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="fc18a-114">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="fc18a-115">\<*範例路徑*\>\Admin\WMI\Remove 傳送 Port\\</span><span class="sxs-lookup"><span data-stu-id="fc18a-115">\<*Samples Path*\>\Admin\WMI\Remove Send Port\\</span></span>  
  
 <span data-ttu-id="fc18a-116">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="fc18a-116">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="fc18a-117">檔案</span><span class="sxs-lookup"><span data-stu-id="fc18a-117">File(s)</span></span>|<span data-ttu-id="fc18a-118">Description</span><span class="sxs-lookup"><span data-stu-id="fc18a-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc18a-119">在 \VBScript 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="fc18a-119">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="fc18a-120">RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="fc18a-120">RemoveSendPort.vbs</span></span>|<span data-ttu-id="fc18a-121">VBScript 檔案，它會接收一個參數，而該參數會指定一或多個要取消登錄和移除的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="fc18a-121">VBScript file that takes a parameter that specifies one or more send ports to unenlist and remove.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="fc18a-122">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="fc18a-122">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="fc18a-123">「移除傳送埠」範例是由單一的 VBScript 檔案組成，而您並不需要建置或初始化該檔案。</span><span class="sxs-lookup"><span data-stu-id="fc18a-123">The Remove Send Port sample consists of a single VBScript file that you not need to build or initialize.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="fc18a-124">執行此範例</span><span class="sxs-lookup"><span data-stu-id="fc18a-124">Running This Sample</span></span>  
  
#### <a name="to-run-the-remove-send-port-sample"></a><span data-ttu-id="fc18a-125">若要執行移除傳送埠範例</span><span class="sxs-lookup"><span data-stu-id="fc18a-125">To run the Remove Send Port sample</span></span>  
  
1.  <span data-ttu-id="fc18a-126">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="fc18a-126">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="fc18a-127">\<*範例路徑*\>\Admin\WMI\Remove 接收 Port\VBScript\\</span><span class="sxs-lookup"><span data-stu-id="fc18a-127">\<*Samples Path*\>\Admin\WMI\Remove Receive Port\VBScript\\</span></span>  
  
2.  <span data-ttu-id="fc18a-128">執行 RemoveSendPort.vbs 檔案，它會使用 cscript 程式，並傳遞下列命令列引數：</span><span class="sxs-lookup"><span data-stu-id="fc18a-128">Run the file RemoveSendPort.vbs using the cscript program, passing the following command-line argument:</span></span>  
  
     <span data-ttu-id="fc18a-129">**\<** ***SendPortName* \>。**</span><span class="sxs-lookup"><span data-stu-id="fc18a-129">**\<** ***SendPortName* \>.**</span></span> <span data-ttu-id="fc18a-130">要移除之傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="fc18a-130">The name of the send port(s) to remove.</span></span> <span data-ttu-id="fc18a-131">如果傳送埠名稱包含空格，請用引號括住該名稱。</span><span class="sxs-lookup"><span data-stu-id="fc18a-131">If the send port name contains spaces, enclose the name in quotes.</span></span>  
  
     <span data-ttu-id="fc18a-132">例如：</span><span class="sxs-lookup"><span data-stu-id="fc18a-132">For example:</span></span>  
  
    ```  
    cscript RemoveSendPort.vbs "My Business Send Port"  
    ```  
  
## <a name="comments"></a><span data-ttu-id="fc18a-133">註解</span><span class="sxs-lookup"><span data-stu-id="fc18a-133">Comments</span></span>  
 <span data-ttu-id="fc18a-134">您也可以使用會存取 Windows WMI 物件模型的指令碼，執行所有可在 BizTalk Server 管理主控台中執行的工作。</span><span class="sxs-lookup"><span data-stu-id="fc18a-134">All tasks that you can perform in the BizTalk Server Administration console can also be performed by using script that accesses the Windows WMI object model.</span></span>  
  
 <span data-ttu-id="fc18a-135">指令檔 RemoveSendPort.vbs 包含詳細註解，其中含有其所執行作業的深入說明。</span><span class="sxs-lookup"><span data-stu-id="fc18a-135">The script file RemoveSendPort.vbs contains detailed comments with further explanation about the operations that it performs.</span></span> <span data-ttu-id="fc18a-136">如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。</span><span class="sxs-lookup"><span data-stu-id="fc18a-136">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc18a-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="fc18a-137">See Also</span></span>  
 [<span data-ttu-id="fc18a-138">Admin-WMI (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="fc18a-138">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)