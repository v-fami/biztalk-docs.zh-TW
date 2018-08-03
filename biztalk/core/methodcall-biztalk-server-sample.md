---
title: MethodCall （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, calling
- examples, orchestrations
- orchestrations, methods
ms.assetid: 6bdc72da-9478-403a-b706-3089b7374ac7
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ef3869161c699c48648bc0c22f1d9f40c9bde73
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986869"
---
# <a name="methodcall-biztalk-server-sample"></a><span data-ttu-id="209cf-102">MethodCall （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="209cf-102">MethodCall (BizTalk Server Sample)</span></span>
<span data-ttu-id="209cf-103">MethodCall 範例示範如何從 BizTalk Server 呼叫 .NET 方法。</span><span class="sxs-lookup"><span data-stu-id="209cf-103">The MethodCall sample demonstrates how to call a .NET-based method from a BizTalk Server orchestration.</span></span>  

## <a name="what-this-sample-does"></a><span data-ttu-id="209cf-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="209cf-104">What This Sample Does</span></span>  
 <span data-ttu-id="209cf-105">此範例使用下列步驟順序和 .NET 方法進行互動：</span><span class="sxs-lookup"><span data-stu-id="209cf-105">This sample interacts with a .NET-based method using the following sequence of steps:</span></span>  

1. <span data-ttu-id="209cf-106">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程會從 In 資料夾擷取 XML 輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="209cf-106">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration retrieves an XML input file from the In folder.</span></span> <span data-ttu-id="209cf-107">此檔案包含有關您要數學程式庫執行的加法或減法資訊。</span><span class="sxs-lookup"><span data-stu-id="209cf-107">This file contains information about an addition or subtraction you want the math library to perform.</span></span>  

2. <span data-ttu-id="209cf-108">協調程式會呼叫包含的數學程式庫，執行 XML 輸入檔案中指定的加法或減法。</span><span class="sxs-lookup"><span data-stu-id="209cf-108">The orchestration calls the included math library to perform the addition or subtraction specified in the XML input file.</span></span>  

3. <span data-ttu-id="209cf-109">適當的數學程式庫方法，或是**新增**或**Subtract**、 執行要求的計算和封裝為 XML 文件的結果。</span><span class="sxs-lookup"><span data-stu-id="209cf-109">The appropriate math library method, either **Add** or **Subtract**, performs the requested calculation and packages the result as an XML document.</span></span>  

4. <span data-ttu-id="209cf-110">協調流程會將產生的 .xml 檔案放到 Out 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="209cf-110">The orchestration places the resulting .xml file in the Out folder.</span></span>  

## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="209cf-111">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="209cf-111">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="209cf-112">此範例示範下列功能：</span><span class="sxs-lookup"><span data-stu-id="209cf-112">This sample demonstrates the following functionalities:</span></span>  

-   <span data-ttu-id="209cf-113">在協調程式中利用升級的屬性。</span><span class="sxs-lookup"><span data-stu-id="209cf-113">Leveraging the promoted properties in an orchestration.</span></span> <span data-ttu-id="209cf-114">InputSchema.xsd 中的三個項目會升級為辨別欄位。</span><span class="sxs-lookup"><span data-stu-id="209cf-114">The three elements in InputSchema.xsd are promoted as distinguished fields.</span></span> <span data-ttu-id="209cf-115">當協調流程收到輸入訊息時，它會取得這三個欄位的值，並將它們指派至協調流程中宣告的對應變數。</span><span class="sxs-lookup"><span data-stu-id="209cf-115">When the orchestration receives the input message, it gets the values of these three fields and assigns them to the corresponding variables declared in the orchestration.</span></span>  

-   <span data-ttu-id="209cf-116">使用**決定**」 圖形來表達協調流程中的"if-then-else"邏輯。</span><span class="sxs-lookup"><span data-stu-id="209cf-116">Using the **Decide** shape to express "if-then-else" logic in an orchestration.</span></span> <span data-ttu-id="209cf-117">協調流程會將辨別欄位的值指派給內部變數之後，即會進入**決定**圖形，以檢查是否應該執行的加法或減法。</span><span class="sxs-lookup"><span data-stu-id="209cf-117">After the orchestration assigns the values of distinguished fields to internal variables, it enters the **Decide** shape to check whether an addition or subtraction should be performed.</span></span> <span data-ttu-id="209cf-118">如果沒有需要執行的作業，協調流程就會終止。</span><span class="sxs-lookup"><span data-stu-id="209cf-118">If no operation needs to be performed, the orchestration terminates.</span></span>  

-   <span data-ttu-id="209cf-119">從協調流程呼叫外部組件。</span><span class="sxs-lookup"><span data-stu-id="209cf-119">Calling an external assembly from an orchestration.</span></span> <span data-ttu-id="209cf-120">如果要執行加法，協調流程會呼叫外部 C# 組件，並傳入兩個參數來執行加法。</span><span class="sxs-lookup"><span data-stu-id="209cf-120">If an addition is to be performed, the orchestration calls an external C# assembly and passes in two parameters to perform the addition.</span></span> <span data-ttu-id="209cf-121">相同的程序也適用於減法。</span><span class="sxs-lookup"><span data-stu-id="209cf-121">The same procedures apply to a subtraction.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="209cf-122">您必須先將組件安裝至全域組件快取後，才能從協調流程呼叫此組件；否則，您將在執行階段收到 XLANG 錯誤。</span><span class="sxs-lookup"><span data-stu-id="209cf-122">You need to install the assembly to the global assembly cache before you can call it from the orchestration; otherwise you will receive an XLANG error during run time.</span></span>  

-   <span data-ttu-id="209cf-123">使用**訊息指派**圖形來建構輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="209cf-123">Using the **Message Assignment** shape to construct the output message.</span></span>  

-   <span data-ttu-id="209cf-124">將下列程式碼放到「運算式」圖形中，來偵錯協調流程：</span><span class="sxs-lookup"><span data-stu-id="209cf-124">Debugging the orchestration by putting the following code in the Expression shape:</span></span>  

    ```  
    System.Diagnostics.Debug.WriteLine(iResult);  
    ```  

     <span data-ttu-id="209cf-125">您也可以使用下列程式碼將結果寫入事件記錄：</span><span class="sxs-lookup"><span data-stu-id="209cf-125">You can also write the result to the event log by using:</span></span>  

    ```  
    System.Diagnostics.EventLog.WriteEntry("MethodCall SDK Sample Debug", System.String.Format("Result = {0}", iResult);  
    ```  

## <a name="where-to-find-this-sample"></a><span data-ttu-id="209cf-126">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="209cf-126">Where to Find This Sample</span></span>  
 <span data-ttu-id="209cf-127">\<*範例路徑*\>\Orchestrations\MethodCall\\</span><span class="sxs-lookup"><span data-stu-id="209cf-127">\<*Samples Path*\>\Orchestrations\MethodCall\\</span></span>  

 <span data-ttu-id="209cf-128">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="209cf-128">The following table shows the files in this sample and describes their purpose.</span></span>  


|                                          <span data-ttu-id="209cf-129">檔案</span><span class="sxs-lookup"><span data-stu-id="209cf-129">File(s)</span></span>                                           |                                                                                           <span data-ttu-id="209cf-130">描述</span><span class="sxs-lookup"><span data-stu-id="209cf-130">Description</span></span>                                                                                            |
|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                        <span data-ttu-id="209cf-131">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="209cf-131">Cleanup.bat</span></span>                                         | <span data-ttu-id="209cf-132">用來解除部署組件，以及將它從全域組件快取中移除。</span><span class="sxs-lookup"><span data-stu-id="209cf-132">Used to undeploy assemblies and remove them from the global assembly cache.</span></span> <span data-ttu-id="209cf-133">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="209cf-133">Removes send and receive ports.</span></span> <span data-ttu-id="209cf-134">視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="209cf-134">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span> |
|                                         <span data-ttu-id="209cf-135">Input.xml</span><span class="sxs-lookup"><span data-stu-id="209cf-135">Input.xml</span></span>                                          |                                                                                        <span data-ttu-id="209cf-136">範例輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="209cf-136">Sample input file.</span></span>                                                                                        |
|                                         <span data-ttu-id="209cf-137">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="209cf-137">Setup.bat</span></span>                                          |                                                                            <span data-ttu-id="209cf-138">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="209cf-138">Used to build and initialize this sample.</span></span>                                                                             |
| <span data-ttu-id="209cf-139">在 \MathLibrary 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="209cf-139">In the \MathLibrary folder:</span></span><br /><br /> <span data-ttu-id="209cf-140">AssemblyInfo.cs, MathHelper.cs, MathLibrary.csproj</span><span class="sxs-lookup"><span data-stu-id="209cf-140">AssemblyInfo.cs, MathHelper.cs, MathLibrary.csproj</span></span> |                                                                <span data-ttu-id="209cf-141">此範例所使用之數學程式庫的專案和來源檔案。</span><span class="sxs-lookup"><span data-stu-id="209cf-141">Project and source files for the math library used by this sample.</span></span>                                                                |
|       <span data-ttu-id="209cf-142">在 \MethodCallSample 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="209cf-142">In the \MethodCallSample folder:</span></span><br /><br /> <span data-ttu-id="209cf-143">InputSchema.xsd, OutputSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="209cf-143">InputSchema.xsd, OutputSchema.xsd</span></span>       |                                                                    <span data-ttu-id="209cf-144">分別為輸入和輸出 .xml 檔案的結構描述。</span><span class="sxs-lookup"><span data-stu-id="209cf-144">Schemas for the input and output .xml files, respectively.</span></span>                                                                    |
| <span data-ttu-id="209cf-145">在 \MethodCallSample 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="209cf-145">In the \MethodCallSample folder:</span></span><br /><br /> <span data-ttu-id="209cf-146">MethodCallSample.btproj, MethodCallSample.sln</span><span class="sxs-lookup"><span data-stu-id="209cf-146">MethodCallSample.btproj, MethodCallSample.sln</span></span> |                                                                           <span data-ttu-id="209cf-147">這個範例的專案及解決方案檔案。</span><span class="sxs-lookup"><span data-stu-id="209cf-147">Project and solution files for this sample.</span></span>                                                                            |
|          <span data-ttu-id="209cf-148">在 \MethodCallSample 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="209cf-148">In the \MethodCallSample folder:</span></span><br /><br /> <span data-ttu-id="209cf-149">MethodCallSampleBinding.xml</span><span class="sxs-lookup"><span data-stu-id="209cf-149">MethodCallSampleBinding.xml</span></span>          |                                                                          <span data-ttu-id="209cf-150">用於自動化設定，例如連接埠繫結。</span><span class="sxs-lookup"><span data-stu-id="209cf-150">Used for automated setup such as port binding.</span></span>                                                                          |
|             <span data-ttu-id="209cf-151">在 \MethodCallSample 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="209cf-151">In the \MethodCallSample folder:</span></span><br /><br /> <span data-ttu-id="209cf-152">MethodCallService.odx</span><span class="sxs-lookup"><span data-stu-id="209cf-152">MethodCallService.odx</span></span>             |                <span data-ttu-id="209cf-153">呼叫數學程式庫執行要求之計算的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。</span><span class="sxs-lookup"><span data-stu-id="209cf-153">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration that calls the math library to perform the requested calculation.</span></span>                |

## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="209cf-154">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="209cf-154">Building and Initializing This Sample</span></span>  

#### <a name="to-build-and-initialize-the-methodcall-sample"></a><span data-ttu-id="209cf-155">建置和初始化 MethodCall 範例</span><span class="sxs-lookup"><span data-stu-id="209cf-155">To build and initialize the MethodCall sample</span></span>  

1. <span data-ttu-id="209cf-156">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="209cf-156">In a command window, navigate to the following folder:</span></span>  

    <span data-ttu-id="209cf-157">\<*範例路徑*\>\Orchestrations\MethodCall</span><span class="sxs-lookup"><span data-stu-id="209cf-157">\<*Samples Path*\>\Orchestrations\MethodCall</span></span>  

2. <span data-ttu-id="209cf-158">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="209cf-158">Run the file Setup.bat, which performs the following actions:</span></span>  

   - <span data-ttu-id="209cf-159">在 MethodCall 中建立此範例的輸入 (In) 和輸出 (Out) 資料夾。</span><span class="sxs-lookup"><span data-stu-id="209cf-159">Creates the input (In) and output (Out) folders for this sample in the MethodCall folder.</span></span>  

   - <span data-ttu-id="209cf-160">編譯此範例的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案，並部署產生的組件。</span><span class="sxs-lookup"><span data-stu-id="209cf-160">Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample, and deploys the resulting assemblies.</span></span>  

   - <span data-ttu-id="209cf-161">建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置以及傳送埠和接收埠，並將其繫結至協調流程。</span><span class="sxs-lookup"><span data-stu-id="209cf-161">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports to the orchestration.</span></span>  

   - <span data-ttu-id="209cf-162">啟用接收位置並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="209cf-162">Enables the receive location, and starts the send port.</span></span> <span data-ttu-id="209cf-163">登錄和啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="209cf-163">Enlists and starts orchestration.</span></span>  

> [!NOTE]
>  <span data-ttu-id="209cf-164">在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="209cf-164">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  

## <a name="running-this-sample"></a><span data-ttu-id="209cf-165">執行此範例</span><span class="sxs-lookup"><span data-stu-id="209cf-165">Running This Sample</span></span>  

#### <a name="to-run-the-methodcall-sample"></a><span data-ttu-id="209cf-166">執行 MethodCall 範例</span><span class="sxs-lookup"><span data-stu-id="209cf-166">To run the MethodCall sample</span></span>  

1.  <span data-ttu-id="209cf-167">將檔案 Input.xml 的複本貼到 In 資料夾。</span><span class="sxs-lookup"><span data-stu-id="209cf-167">Paste a copy of the file Input.xml into the In folder.</span></span>  

2.  <span data-ttu-id="209cf-168">觀察在 Out 資料夾中建立的 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="209cf-168">Observe the .xml file created in the Out folder.</span></span> <span data-ttu-id="209cf-169">此檔案包含要求的加法或減法計算的結果。</span><span class="sxs-lookup"><span data-stu-id="209cf-169">This file contains the result of the requested addition or subtraction calculation.</span></span> <span data-ttu-id="209cf-170">這個檔案的名稱的格式\< *MessageID*\>.xml，其中*\<MessageID\>* 會產生來唯一識別該訊息的 GUID.</span><span class="sxs-lookup"><span data-stu-id="209cf-170">The format of the name of this file is \<*MessageID*\>.xml, where *\<MessageID\>* is the GUID generated to uniquely identify the message.</span></span>  

3.  <span data-ttu-id="209cf-171">您可修改輸入檔案，要求不同的加法或減法計算。</span><span class="sxs-lookup"><span data-stu-id="209cf-171">You can modify the input file to request different addition or subtraction calculations.</span></span>  

## <a name="uninstalling-this-sample"></a><span data-ttu-id="209cf-172">解除安裝這個範例</span><span class="sxs-lookup"><span data-stu-id="209cf-172">Uninstalling This Sample</span></span>  

#### <a name="to-uninstall-the-methodcall-sample"></a><span data-ttu-id="209cf-173">解除安裝 MethodCall 範例</span><span class="sxs-lookup"><span data-stu-id="209cf-173">To uninstall the MethodCall sample</span></span>  

1. <span data-ttu-id="209cf-174">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元，變更目錄 (**cd**) 來\<*範例路徑*\>\Orchestrations\MethodCall\\。</span><span class="sxs-lookup"><span data-stu-id="209cf-174">At a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to \<*Samples Path*\>\Orchestrations\MethodCall\\.</span></span>  

2. <span data-ttu-id="209cf-175">執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="209cf-175">Run Cleanup.bat.</span></span>  

## <a name="see-also"></a><span data-ttu-id="209cf-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="209cf-176">See Also</span></span>  
 [<span data-ttu-id="209cf-177">協調流程 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="209cf-177">Orchestrations (BizTalk Server Samples Folder)</span></span>](../core/orchestrations-biztalk-server-samples-folder.md)