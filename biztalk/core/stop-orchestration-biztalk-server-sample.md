---
title: "停止協調流程 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- orchestrations, stopping
ms.assetid: 83be44e9-819d-4ac5-8b75-84c23e6b5ba2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b0c88bdeb85b8ad493b85d2569061c35bd516e1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="stop-orchestration-biztalk-server-sample"></a><span data-ttu-id="dbe20-102">停止協調流程 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="dbe20-102">Stop Orchestration (BizTalk Server Sample)</span></span>
<span data-ttu-id="dbe20-103">「停止協調流程」範例會示範如何停止 BizTalk Server 協調流程，以及選擇性地將它取消登錄。</span><span class="sxs-lookup"><span data-stu-id="dbe20-103">The Stop Orchestration sample demonstrates how to stop a BizTalk Server orchestration and, optionally, to unenlist it.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="dbe20-104">如果在部署後不需要部署指令碼，就應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="dbe20-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="dbe20-105">必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。</span><span class="sxs-lookup"><span data-stu-id="dbe20-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="dbe20-106">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="dbe20-106">What This Sample Does</span></span>  
 <span data-ttu-id="dbe20-107">構成本範例之指令檔中的 Visual Basic Scripting Edition (VBScript) 指令碼，會示範如何使用 BizTalk Server WMI 提供者來執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="dbe20-107">The Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:</span></span>  
  
-   <span data-ttu-id="dbe20-108">在指定協調流程名稱和組件名稱的情形下，查詢已部署的特定 BizTalk Server 協調流程。</span><span class="sxs-lookup"><span data-stu-id="dbe20-108">Given an orchestration name and an assembly name, query for a specific deployed BizTalk Server orchestration.</span></span>  
  
-   <span data-ttu-id="dbe20-109">停止該協調流程。</span><span class="sxs-lookup"><span data-stu-id="dbe20-109">Stop that orchestration.</span></span>  
  
-   <span data-ttu-id="dbe20-110">取消登錄該協調流程 (選擇性)。</span><span class="sxs-lookup"><span data-stu-id="dbe20-110">Unenlist that orchestration (optionally).</span></span>  
  
-   <span data-ttu-id="dbe20-111">處理任何錯誤，讓有意義的資訊能傳回給使用者。</span><span class="sxs-lookup"><span data-stu-id="dbe20-111">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="dbe20-112">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="dbe20-112">Where to Find This Sample</span></span>  
 <span data-ttu-id="dbe20-113">這些範例檔案位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="dbe20-113">The sample files are located in the following SDK location:</span></span>  
  
 <span data-ttu-id="dbe20-114">\<*範例路徑*\>\Admin\WMI\Stop Orchestration\\</span><span class="sxs-lookup"><span data-stu-id="dbe20-114">\<*Samples Path*\>\Admin\WMI\Stop Orchestration\\</span></span>  
  
 <span data-ttu-id="dbe20-115">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="dbe20-115">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="dbe20-116">檔案</span><span class="sxs-lookup"><span data-stu-id="dbe20-116">File(s)</span></span>|<span data-ttu-id="dbe20-117">Description</span><span class="sxs-lookup"><span data-stu-id="dbe20-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dbe20-118">在 \VBScript 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="dbe20-118">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="dbe20-119">StopOrch.vbs</span><span class="sxs-lookup"><span data-stu-id="dbe20-119">StopOrch.vbs</span></span>|<span data-ttu-id="dbe20-120">會使用參數的 VBScript 檔案，這些參數會指定要停止和 (選擇性) 取消登錄的協調流程。</span><span class="sxs-lookup"><span data-stu-id="dbe20-120">VBScript file that takes parameters to specify an orchestration to be stopped and, optionally, unenlisted.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="dbe20-121">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="dbe20-121">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="dbe20-122">「停止協調流程」範例是由單一 VBScript 檔案組成，您並不需要建置或初始化該檔案。</span><span class="sxs-lookup"><span data-stu-id="dbe20-122">The Stop Orchestration sample consists of a single VBScript file that you do not need to build or initialize.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="dbe20-123">執行此範例</span><span class="sxs-lookup"><span data-stu-id="dbe20-123">Running This Sample</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="dbe20-124">執行此範例</span><span class="sxs-lookup"><span data-stu-id="dbe20-124">To run this sample</span></span>  
  
1.  <span data-ttu-id="dbe20-125">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="dbe20-125">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="dbe20-126">\<*範例路徑*\>\Admin\WMI\Stop Orchestration\VBScript\\</span><span class="sxs-lookup"><span data-stu-id="dbe20-126">\<*Samples Path*\>\Admin\WMI\Stop Orchestration\VBScript\\</span></span>  
  
2.  <span data-ttu-id="dbe20-127">執行 StopOrch.vbs 檔案，它會使用 cscript 程式，並傳遞下列命令列引數，其中第三個引數是選擇性引數：</span><span class="sxs-lookup"><span data-stu-id="dbe20-127">Run the file StopOrch.vbs using the cscript program, passing the following command-line arguments, of which the third one is optional:</span></span>  
  
    -   <span data-ttu-id="dbe20-128">**\<** ***OrchestrationName* \>。**</span><span class="sxs-lookup"><span data-stu-id="dbe20-128">**\<** ***OrchestrationName* \>.**</span></span> <span data-ttu-id="dbe20-129">要停止及 (選擇性) 要取消登錄之 BizTalk Server 協調流程的名稱。</span><span class="sxs-lookup"><span data-stu-id="dbe20-129">The name of the BizTalk Server orchestration to be stopped and, optionally, unenlisted.</span></span>  
  
    -   <span data-ttu-id="dbe20-130">**\<** ***AssemblyName* \>。**</span><span class="sxs-lookup"><span data-stu-id="dbe20-130">**\<** ***AssemblyName* \>.**</span></span> <span data-ttu-id="dbe20-131">其中已部署指定之協調流程的 BizTalk 組件名稱。</span><span class="sxs-lookup"><span data-stu-id="dbe20-131">The name of the BizTalk assembly in which the specified orchestration was deployed.</span></span> <span data-ttu-id="dbe20-132">如果組件名稱包含空格，請用引號括住該名稱。</span><span class="sxs-lookup"><span data-stu-id="dbe20-132">If the assembly name contains spaces, enclose the name in quotes.</span></span>  
  
    -   <span data-ttu-id="dbe20-133">**取消登錄。**</span><span class="sxs-lookup"><span data-stu-id="dbe20-133">**Unenlist.**</span></span> <span data-ttu-id="dbe20-134">選用的常值字串，表示除了停止指定之協調流程以外，還要將其取消登錄。</span><span class="sxs-lookup"><span data-stu-id="dbe20-134">An optional, literal string used to indicate that the specified orchestration should be unenlisted in addition to being stopped.</span></span>  
  
         <span data-ttu-id="dbe20-135">例如：</span><span class="sxs-lookup"><span data-stu-id="dbe20-135">For example:</span></span>  
  
        ```  
        cscript StopOrch.vbs MyBusinessOrchestration "My Business Assembly"  
        ```  
  
         <span data-ttu-id="dbe20-136">-或-</span><span class="sxs-lookup"><span data-stu-id="dbe20-136">-OR-</span></span>  
  
        ```  
        cscript StopOrch.vbs MyBusinessOrchestration MyBusinessAssembly Unenlist  
        ```  
  
## <a name="comments"></a><span data-ttu-id="dbe20-137">註解</span><span class="sxs-lookup"><span data-stu-id="dbe20-137">Comments</span></span>  
 <span data-ttu-id="dbe20-138">您也可以使用會存取 Windows WMI 物件模型的指令碼，執行所有可在「BizTalk Server 管理主控台」中執行的工作。</span><span class="sxs-lookup"><span data-stu-id="dbe20-138">All tasks that you can perform in the BizTalk Server Administration console can also be performed by using scripts that access the Windows WMI object model.</span></span>  
  
 <span data-ttu-id="dbe20-139">指令檔 StopOrch.vbs 包含詳細註解，其中含有其所執行作業的深入說明。</span><span class="sxs-lookup"><span data-stu-id="dbe20-139">The script file StopOrch.vbs contains detailed comments with further explanation about the operations that it performs.</span></span> <span data-ttu-id="dbe20-140">如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。</span><span class="sxs-lookup"><span data-stu-id="dbe20-140">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbe20-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="dbe20-141">See Also</span></span>  
 [<span data-ttu-id="dbe20-142">Admin-WMI (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="dbe20-142">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)