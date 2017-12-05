---
title: "列舉接收位置 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, examples
- receive locations, enumerating
- examples, receive locations
ms.assetid: 27ff8ac6-7e8e-4dde-84d1-d21bf417ddd7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82fcdc400395d7bbfd6de8f9bc0fca85114a25dc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="enumerate-receive-locations-biztalk-server-sample"></a><span data-ttu-id="d415d-102">列舉接收位置 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="d415d-102">Enumerate Receive Locations (BizTalk Server Sample)</span></span>
<span data-ttu-id="d415d-103">「列舉接收位置」範例會示範如何擷取一或多個接收位置的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d415d-103">The Enumerate Receive Locations sample demonstrates how to retrieve details about one or more receive locations.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="d415d-104">如果在部署後不需要部署指令碼，就應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="d415d-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="d415d-105">必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。</span><span class="sxs-lookup"><span data-stu-id="d415d-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="d415d-106">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="d415d-106">What This Sample Does</span></span>  
 <span data-ttu-id="d415d-107">這個範例包括存取 Windows WMI 物件模型中，Visual Basic Scripting Edition (VBScript) 版本和 Visual C# 版本會存取**System.Management** .NET Framework 所提供的物件。</span><span class="sxs-lookup"><span data-stu-id="d415d-107">This sample includes a Visual Basic Scripting Edition (VBScript) version that accesses the Windows WMI object model, and a Visual C# version that accesses the **System.Management** objects provided by the .NET Framework.</span></span> <span data-ttu-id="d415d-108">這兩個版本最後都會存取 BizTalk Server WMI 提供者來執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="d415d-108">Both of these versions ultimately access the BizTalk Server WMI provider to perform the following operations:</span></span>  
  
-   <span data-ttu-id="d415d-109">查詢設定的接收位置或特定接收位置，指定其名稱。</span><span class="sxs-lookup"><span data-stu-id="d415d-109">Query for the set of configured receive locations or for a specific receive location, given its name.</span></span>  
  
-   <span data-ttu-id="d415d-110">截取和顯示每個相關接收位置的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d415d-110">Retrieve and display details about each receive location of interest.</span></span>  
  
-   <span data-ttu-id="d415d-111">處理任何錯誤，讓有意義的資訊能傳回給使用者。</span><span class="sxs-lookup"><span data-stu-id="d415d-111">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="d415d-112">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="d415d-112">Where to Find This Sample</span></span>  
 <span data-ttu-id="d415d-113">範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="d415d-113">The samples are located in the following SDK locations:</span></span>  
  
-   <span data-ttu-id="d415d-114">VBScript 版： \<*範例路徑*\>\Admin\WMI\Enumerate Receive Locations\VBScript\\</span><span class="sxs-lookup"><span data-stu-id="d415d-114">VBScript version: \<*Samples Path*\>\Admin\WMI\Enumerate Receive Locations\VBScript\\</span></span>  
  
-   <span data-ttu-id="d415d-115">Visual C# 版本： \<*範例路徑*\>\Admin\WMI\Enumerate Receive Locations\CSharp\\</span><span class="sxs-lookup"><span data-stu-id="d415d-115">Visual C# version: \<*Samples Path*\>\Admin\WMI\Enumerate Receive Locations\CSharp\\</span></span>  
  
 <span data-ttu-id="d415d-116">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="d415d-116">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="d415d-117">檔案</span><span class="sxs-lookup"><span data-stu-id="d415d-117">File(s)</span></span>|<span data-ttu-id="d415d-118">Description</span><span class="sxs-lookup"><span data-stu-id="d415d-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d415d-119">在 \VBScript 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="d415d-119">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="d415d-120">EnumRecLocs.vbs</span><span class="sxs-lookup"><span data-stu-id="d415d-120">EnumRecLocs.vbs</span></span>|<span data-ttu-id="d415d-121">VBScript 檔，該檔案會擷取所有與設定的接收位置相關的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d415d-121">VBScript file that retrieves details about all configured receive locations.</span></span>|  
|<span data-ttu-id="d415d-122">在 \CSharp 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="d415d-122">In the \CSharp folder:</span></span><br /><br /> <span data-ttu-id="d415d-123">App.ico、AssemblyInfo.cs、BTSampleEnumerateRLs.csproj、BTSampleEnumerateRLs.sln、EnumRLs.cs</span><span class="sxs-lookup"><span data-stu-id="d415d-123">App.ico, AssemblyInfo.cs, BTSampleEnumerateRLs.csproj, BTSampleEnumerateRLs.sln, EnumRLs.cs</span></span>|<span data-ttu-id="d415d-124">專案、解決方案和來源檔，用於建置 Visual C# 命令列應用程式，以擷取所有設定接收位置或特定接收位置的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d415d-124">Project, solution, and source files for building a Visual C# command-line application that retrieves details about all configured receive locations, or about a specific receive location.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="d415d-125">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="d415d-125">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="d415d-126">VBScript 版的「列舉接收位置」範例是由單一 Visual Basic 指令碼檔案所組成，您不需要建置或初始化該檔案。</span><span class="sxs-lookup"><span data-stu-id="d415d-126">The VBScript version of the Enumerate Receive Locations sample consists of a single Visual Basic script file that you do not need to build or initialize.</span></span>  
  
#### <a name="to-build-the-visual-c-version-of-the-enumerate-receive-locations-sample"></a><span data-ttu-id="d415d-127">建置 Visual C# 版的列舉接收位置範例</span><span class="sxs-lookup"><span data-stu-id="d415d-127">To build the Visual C# version of the Enumerate Receive Locations sample</span></span>  
  
1.  <span data-ttu-id="d415d-128">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟方案檔 BTSampleEnumerateRLs.sln。</span><span class="sxs-lookup"><span data-stu-id="d415d-128">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file BTSampleEnumerateRLs.sln.</span></span>  
  
2.  <span data-ttu-id="d415d-129">在**建置**功能表上，按一下 **建置方案**。</span><span class="sxs-lookup"><span data-stu-id="d415d-129">In the **Build** menu, click **Build Solution**.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="d415d-130">執行此範例</span><span class="sxs-lookup"><span data-stu-id="d415d-130">Running This Sample</span></span>  
  
#### <a name="to-run-the-enumerate-receive-locations-sample"></a><span data-ttu-id="d415d-131">執行列舉接收位置範例</span><span class="sxs-lookup"><span data-stu-id="d415d-131">To run the Enumerate Receive Locations sample</span></span>  
  
1.  <span data-ttu-id="d415d-132">在命令視窗中，根據您要執行的是此範例的 VBScript 版或 Visual C# 版而定，分別瀏覽至下列其中一個資料夾：</span><span class="sxs-lookup"><span data-stu-id="d415d-132">In a command window, navigate to one of the following folders, depending on whether you are going to run the VBScript version or the Visual C# version of this sample, respectively:</span></span>  
  
     <span data-ttu-id="d415d-133">\<*範例路徑*\>\Admin\WMI\Enumerate 接收 Locations\VBScript\\</span><span class="sxs-lookup"><span data-stu-id="d415d-133">\<*Samples Path*\>\Admin\WMI\Enumerate Receive Locations\VBScript\\</span></span>  
  
     <span data-ttu-id="d415d-134">\<*範例路徑*\>\Admin\WMI\Enumerate 接收 Locations\CSharp\bin\Debug\\</span><span class="sxs-lookup"><span data-stu-id="d415d-134">\<*Samples Path*\>\Admin\WMI\Enumerate Receive Locations\CSharp\bin\Debug\\</span></span>  
  
2.  <span data-ttu-id="d415d-135">根據您要執行的是此範例的 VBScript 版或 Visual C# 版而定，分別使用 cscript 程式執行 EnumRecLocs.vbs 檔，或是執行 EnumRl.exe 檔。</span><span class="sxs-lookup"><span data-stu-id="d415d-135">Either run the file EnumRecLocs.vbs using the cscript program, or run the file EnumRl.exe, depending on whether you are going to run the VBScript version or the Visual C# version of this sample, respectively.</span></span> <span data-ttu-id="d415d-136">針對 Visual C# 版本，傳遞下列兩個命令列引數的其中一個：</span><span class="sxs-lookup"><span data-stu-id="d415d-136">For the Visual C# version, pass one of the following two command-line arguments:</span></span>  
  
    -   <span data-ttu-id="d415d-137">**\<ReceiveLocationName\>。**</span><span class="sxs-lookup"><span data-stu-id="d415d-137">**\<ReceiveLocationName\>.**</span></span> <span data-ttu-id="d415d-138">要顯示其詳細資訊的接收位置名稱。</span><span class="sxs-lookup"><span data-stu-id="d415d-138">The name of the receive location for which details will be displayed.</span></span> <span data-ttu-id="d415d-139">如果接收位置名稱包含空格，請用引號括住該名稱。</span><span class="sxs-lookup"><span data-stu-id="d415d-139">If the receive location name contains spaces, enclose the name in quotes.</span></span>  
  
    -   <span data-ttu-id="d415d-140">**/?.**</span><span class="sxs-lookup"><span data-stu-id="d415d-140">**/?.**</span></span> <span data-ttu-id="d415d-141">顯示說明。</span><span class="sxs-lookup"><span data-stu-id="d415d-141">Displays help.</span></span>  
  
         <span data-ttu-id="d415d-142">例如 (VBScript)：</span><span class="sxs-lookup"><span data-stu-id="d415d-142">For example (VBScript):</span></span>  
  
        ```  
        cscript EnumRecLocs.vbs  
        ```  
  
         <span data-ttu-id="d415d-143">-或- (Visual C#)：</span><span class="sxs-lookup"><span data-stu-id="d415d-143">-OR- (Visual C#):</span></span>  
  
        ```  
        EnumRl "My Receive Location #3"  
        ```  
  
         <span data-ttu-id="d415d-144">-或- (Visual C#)：</span><span class="sxs-lookup"><span data-stu-id="d415d-144">-OR- (Visual C#):</span></span>  
  
        ```  
        EnumRl /?  
        ```  
  
    > [!NOTE]
    >  <span data-ttu-id="d415d-145">此範例的 VBScript 版不接受任何命令列參數，因此只能擷取和顯示所有設定接收位置的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d415d-145">The VBScript version of this sample does not accept any command-line parameters, and therefore is only capable of retrieving and displaying details about all configured receive locations.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="d415d-146">註解</span><span class="sxs-lookup"><span data-stu-id="d415d-146">Comments</span></span>  
 <span data-ttu-id="d415d-147">您可以在執行的所有工作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，也可以執行使用存取 Windows WMI 物件模型的指令碼和使用 Visual C# 存取**System.Management**提供物件.NET framework。</span><span class="sxs-lookup"><span data-stu-id="d415d-147">All tasks that you can perform in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console can also be performed by using script that accesses the Windows WMI object model and by using Visual C# that accesses the **System.Management** objects provided by the .NET Framework.</span></span>  
  
 <span data-ttu-id="d415d-148">指令碼檔案 EnumRecLocs.vbs 和 Visual C# 來源檔 EnumRLs.cs 包含詳細註解，以及有關這兩個檔案所執行作業的進一步說明。</span><span class="sxs-lookup"><span data-stu-id="d415d-148">The script file EnumRecLocs.vbs and the Visual C# source file EnumRLs.cs contain detailed comments with further explanation about the operations that they perform.</span></span> <span data-ttu-id="d415d-149">如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。</span><span class="sxs-lookup"><span data-stu-id="d415d-149">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d415d-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="d415d-150">See Also</span></span>  
 [<span data-ttu-id="d415d-151">Admin-WMI (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="d415d-151">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)