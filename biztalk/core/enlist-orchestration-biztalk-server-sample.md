---
title: "登錄協調流程 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- orchestrations, enlisting
- examples, orchestrations
ms.assetid: d8d53e59-2313-40dd-a278-0a29d8eb4ce8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e8d85a49b410f0571e8e9cb0be816f1feda139e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="enlist-orchestration-biztalk-server-sample"></a><span data-ttu-id="5301b-102">登錄協調流程 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="5301b-102">Enlist Orchestration (BizTalk Server Sample)</span></span>
<span data-ttu-id="5301b-103">「登錄協調流程」範例會示範如何向主控件登錄 BizTalk Server 協調流程。</span><span class="sxs-lookup"><span data-stu-id="5301b-103">The Enlist Orchestration sample demonstrates how to enlist a BizTalk Server orchestration to a host.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="5301b-104">如果在部署後不需要部署指令碼，就應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="5301b-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="5301b-105">必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。</span><span class="sxs-lookup"><span data-stu-id="5301b-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="5301b-106">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="5301b-106">What This Sample Does</span></span>  
 <span data-ttu-id="5301b-107">這個範例包括存取 Windows Management Instrumentation (WMI) 物件模型中，Visual Basic Scripting Edition (VBScript) 版本和 Visual C# 版本會存取**System.Management**所提供的物件.NET Framework。</span><span class="sxs-lookup"><span data-stu-id="5301b-107">This sample includes a Visual Basic Scripting Edition (VBScript) version that accesses the Windows Management Instrumentation (WMI) object model, and a Visual C# version that accesses the **System.Management** objects provided by the .NET Framework.</span></span> <span data-ttu-id="5301b-108">這兩個版本最後都會存取 BizTalk Server WMI 提供者來執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5301b-108">Both of these versions ultimately access the BizTalk Server WMI provider to perform the following operations:</span></span>  
  
-   <span data-ttu-id="5301b-109">在指定協調流程名稱和組件名稱的情形下，查詢已部署的特定 BizTalk Server 協調流程。</span><span class="sxs-lookup"><span data-stu-id="5301b-109">Given an orchestration name and an assembly name, query for a specific deployed BizTalk Server orchestration.</span></span>  
  
-   <span data-ttu-id="5301b-110">向預設主控件登錄該協調流程。</span><span class="sxs-lookup"><span data-stu-id="5301b-110">Enlist that orchestration to the default host.</span></span>  
  
-   <span data-ttu-id="5301b-111">處理任何錯誤，讓有意義的資訊能傳回給使用者。</span><span class="sxs-lookup"><span data-stu-id="5301b-111">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="5301b-112">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="5301b-112">Where to Find This Sample</span></span>  
 <span data-ttu-id="5301b-113">範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="5301b-113">The samples are located in the following SDK locations:</span></span>  
  
-   <span data-ttu-id="5301b-114">VBScript 版： \<*範例路徑*\>\Admin\WMI\Enlist Orchestration\VBScript\\</span><span class="sxs-lookup"><span data-stu-id="5301b-114">VBScript version: \<*Samples Path*\>\Admin\WMI\Enlist Orchestration\VBScript\\</span></span>  
  
-   <span data-ttu-id="5301b-115">Visual C# 版本： \<*範例路徑*\>\Admin\WMI\Enlist Orchestration\CSharp\\</span><span class="sxs-lookup"><span data-stu-id="5301b-115">Visusal C# version: \<*Samples Path*\>\Admin\WMI\Enlist Orchestration\CSharp\\</span></span>  
  
 <span data-ttu-id="5301b-116">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="5301b-116">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="5301b-117">檔案</span><span class="sxs-lookup"><span data-stu-id="5301b-117">File(s)</span></span>|<span data-ttu-id="5301b-118">Description</span><span class="sxs-lookup"><span data-stu-id="5301b-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5301b-119">在 \VBScript 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="5301b-119">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="5301b-120">EnlistOrch.vbs</span><span class="sxs-lookup"><span data-stu-id="5301b-120">EnlistOrch.vbs</span></span>|<span data-ttu-id="5301b-121">VBScript 檔案，它會接受特定參數來指定要向主控件登錄的協調流程。</span><span class="sxs-lookup"><span data-stu-id="5301b-121">VBScript file that takes parameters to specify an orchestration to be enlisted to a host.</span></span>|  
|<span data-ttu-id="5301b-122">在 \CSharp 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="5301b-122">In the \CSharp folder:</span></span><br /><br /> <span data-ttu-id="5301b-123">App.ico、AssemblyInfo.cs、BTSampleEnlistOrc.csproj、BTSampleEnlistOrc.sln、EnlistOrc.cs</span><span class="sxs-lookup"><span data-stu-id="5301b-123">App.ico, AssemblyInfo.cs, BTSampleEnlistOrc.csproj, BTSampleEnlistOrc.sln, EnlistOrc.cs</span></span>|<span data-ttu-id="5301b-124">專案、方案和原始程式檔，用於建置 Visual C# 命令列應用程式，這個應用程式會接受特定參數來指定要向主控件登錄的協調流程。</span><span class="sxs-lookup"><span data-stu-id="5301b-124">Project, solution, and source files for building a Visual C# command-line application that takes parameters to specify an orchestration to be enlisted to a host.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="5301b-125">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="5301b-125">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="5301b-126">VBScript 版的「登錄協調流程」範例是由單一 Visual Basic 指令碼檔案所組成，您不需要建置或初始化該檔案。</span><span class="sxs-lookup"><span data-stu-id="5301b-126">The VBScript version of the Enlist Orchestration sample consists of a single Visual Basic script file that you do not need to build or initialize.</span></span>  
  
#### <a name="to-build-the-visual-c-version-of-the-enlist-orchestration-sample"></a><span data-ttu-id="5301b-127">若要建置 Visual C# 版的登錄協調流程範例</span><span class="sxs-lookup"><span data-stu-id="5301b-127">To build the Visual C# version of the Enlist Orchestration sample</span></span>  
  
1.  <span data-ttu-id="5301b-128">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟方案檔 BTSampleEnlistOrc.sln。</span><span class="sxs-lookup"><span data-stu-id="5301b-128">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file BTSampleEnlistOrc.sln.</span></span>  
  
2.  <span data-ttu-id="5301b-129">在**建置**功能表上，按一下 **建置方案**。</span><span class="sxs-lookup"><span data-stu-id="5301b-129">In the **Build** menu, click **Build Solution**.</span></span>  
  
#### <a name="to-run-the-enlist-orchestration-sample"></a><span data-ttu-id="5301b-130">若要執行登錄協調流程範例</span><span class="sxs-lookup"><span data-stu-id="5301b-130">To run the Enlist Orchestration sample.</span></span>  
  
1.  <span data-ttu-id="5301b-131">在命令視窗中，根據您打算執行此範例的 VBScript 版或 Visual C# 版，分別瀏覽至下列其中一個資料夾：</span><span class="sxs-lookup"><span data-stu-id="5301b-131">In a command window, navigate to one of the following folders, depending on whether you are planning to run the VBScript version or the Visual C# version of this sample, respectively:</span></span>  
  
     <span data-ttu-id="5301b-132">\<*範例路徑*\>\Admin\WMI\Enlist Orchestration\VBScript\\</span><span class="sxs-lookup"><span data-stu-id="5301b-132">\<*Samples Path*\>\Admin\WMI\Enlist Orchestration\VBScript\\</span></span>  
  
     <span data-ttu-id="5301b-133">\<*範例路徑*\>AdminWMIEnlist OrchestrationCSharpbinDebug</span><span class="sxs-lookup"><span data-stu-id="5301b-133">\<*Samples Path*\>AdminWMIEnlist OrchestrationCSharpbinDebug</span></span>  
  
2.  <span data-ttu-id="5301b-134">根據您打算執行此範例的 VBScript 版或 Visual C# 版，分別使用 cscript 程式執行 EnlistOrch.vbs 檔，或是執行 EnlistOrc.exe 檔。</span><span class="sxs-lookup"><span data-stu-id="5301b-134">Either run the file EnlistOrch.vbs using the cscript program, or run the file EnlistOrc.exe, depending on whether you are planning to run the VBScript version or the Visual C# version of this sample, respectively.</span></span> <span data-ttu-id="5301b-135">無論執行哪個版本，都會傳遞下列命令列引數：</span><span class="sxs-lookup"><span data-stu-id="5301b-135">In any event, pass the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="5301b-136">**\<** ***OrchestrationName* \>。**</span><span class="sxs-lookup"><span data-stu-id="5301b-136">**\<** ***OrchestrationName* \>.**</span></span> <span data-ttu-id="5301b-137">要登錄的協調流程名稱。</span><span class="sxs-lookup"><span data-stu-id="5301b-137">The name of the orchestration to be enlisted.</span></span>  
  
    -   <span data-ttu-id="5301b-138">**\<** ***AssemblyName* \>。**</span><span class="sxs-lookup"><span data-stu-id="5301b-138">**\<** ***AssemblyName* \>.**</span></span> <span data-ttu-id="5301b-139">協調流程已部署於其中的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="5301b-139">The name of the assembly in which the orchestration was deployed.</span></span> <span data-ttu-id="5301b-140">如果組件名稱包含空格，請用引號括住該名稱。</span><span class="sxs-lookup"><span data-stu-id="5301b-140">If the assembly name contains spaces, enclose the name in quotes.</span></span>  
  
         <span data-ttu-id="5301b-141">例如: (VBScript):</span><span class="sxs-lookup"><span data-stu-id="5301b-141">For example: (VBScript):</span></span>  
  
        ```  
        cscript EnlistOrch.vbs MyBusinessOrchestration "My Business Assembly"  
        ```  
  
         <span data-ttu-id="5301b-142">-或- (Visual C#)：</span><span class="sxs-lookup"><span data-stu-id="5301b-142">-OR- (Visual C#):</span></span>  
  
        ```  
        EnlistOrc MyBusinessOrchestration "My Business Assembly"  
        ```  
  
## <a name="comments"></a><span data-ttu-id="5301b-143">註解</span><span class="sxs-lookup"><span data-stu-id="5301b-143">Comments</span></span>  
 <span data-ttu-id="5301b-144">您可以在執行的所有工作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，也可以執行使用存取 Windows WMI 物件模型的指令碼和使用 Visual C# 存取**System.Management**提供物件.NET framework。</span><span class="sxs-lookup"><span data-stu-id="5301b-144">All tasks that you can perform in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console can also be performed by using script that accesses the Windows WMI object model and by using Visual C# that accesses the **System.Management** objects provided by the .NET Framework.</span></span>  
  
 <span data-ttu-id="5301b-145">指令檔 EnlistOrch.vbs 和 Visual C# 來源檔 EnlistOrc.cs，包含了詳細註解，以及這兩個檔案所執行作業的相關進一步說明。</span><span class="sxs-lookup"><span data-stu-id="5301b-145">The script file EnlistOrch.vbs and the Visual C# source file EnlistOrc.cs contain detailed comments with further explanation about the operations that they perform.</span></span> <span data-ttu-id="5301b-146">如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。</span><span class="sxs-lookup"><span data-stu-id="5301b-146">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5301b-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="5301b-147">See Also</span></span>  
 [<span data-ttu-id="5301b-148">Admin-WMI (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="5301b-148">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)