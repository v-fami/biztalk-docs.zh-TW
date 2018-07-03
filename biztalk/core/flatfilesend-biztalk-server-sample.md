---
title: FlatFileSend （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52dd0018-e272-40db-a26a-509d444d7106
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 471f49c7bae30a032d50e474b80efbf12d2ffdd2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000743"
---
# <a name="flatfilesend-biztalk-server-sample"></a><span data-ttu-id="9ce7a-102">FlatFileSend (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="9ce7a-102">FlatFileSend (BizTalk Server Sample)</span></span>
<span data-ttu-id="9ce7a-103">FlatFileSend 範例示範如何使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將 XML 檔案處理成相等的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-103">The FlatFileSend sample demonstrates how you can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to process an XML file into the equivalent flat file.</span></span>  

## <a name="what-this-sample-does"></a><span data-ttu-id="9ce7a-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="9ce7a-104">What This Sample Does</span></span>  
 <span data-ttu-id="9ce7a-105">此範例將 [FFInput] 資料夾設定為接收位置。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-105">This sample configures the folder FFInput as a receive location.</span></span> <span data-ttu-id="9ce7a-106">當您將檔案 (例如範例檔案 FlatFileSend_in.xml) 放置於此資料夾時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 便會使用下列步驟來處理此檔案中的訊息：</span><span class="sxs-lookup"><span data-stu-id="9ce7a-106">When you place a file, such as the sample file FlatFileSend_in.xml, into this folder, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes the message in this file using the following steps:</span></span>  

1. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9ce7a-107"> 讀取接收位置資料夾 [FFInput] 中輸入檔的訊息。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-107"> reads the message from the input file in the receive location folder FFInput.</span></span>  

2. <span data-ttu-id="9ce7a-108">訊息透過 XML 接收管線傳遞。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-108">The message is passed through an XML receive pipeline.</span></span>  

3. <span data-ttu-id="9ce7a-109">在 MessageBox 資料庫中，訊息路由傳送至 FILE 傳送埠，這個傳送埠具有使用「一般檔案組合器」元件設定的傳送管線。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-109">In the MessageBox database, the message is routed to a FILE send port that has a send pipeline configured with a Flat File Assembler component.</span></span> <span data-ttu-id="9ce7a-110">「一般檔案組合器」元件會使用一般檔案結構描述，將 XML 訊息轉換成相等的一般檔案表示。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-110">The Flat File Assembler component converts the XML message to an equivalent flat file representation using a flat file schema.</span></span>  

4. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9ce7a-111"> 將轉換後的訊息寫入至傳送配接器資料夾 [FFOutput] 中的文字檔。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-111"> writes the converted message to a text file in the send adapter folder FFOutput.</span></span>  

## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="9ce7a-112">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="9ce7a-112">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="9ce7a-113">範例訊息大致指出了此範例的基本設計。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-113">The sample message dictates much of the basic design in this sample.</span></span> <span data-ttu-id="9ce7a-114">一般檔案訊息必須使用「一般檔案組合器」和自訂傳送管線內的一般檔案結構描述來組合。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-114">Flat file messages must be assembled using the Flat File Assembler and a flat file schema within a custom send pipeline.</span></span> <span data-ttu-id="9ce7a-115">這些和其他設計元素總結於下表中。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-115">These and other design elements are summarized in the following table.</span></span>  


|    <span data-ttu-id="9ce7a-116">設計元素</span><span class="sxs-lookup"><span data-stu-id="9ce7a-116">Design element</span></span>    |                                                                                                                                                                    <span data-ttu-id="9ce7a-117">已選取的原因</span><span class="sxs-lookup"><span data-stu-id="9ce7a-117">Reason(s) selected</span></span>                                                                                                                                                                    |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9ce7a-118">自訂傳送管線</span><span class="sxs-lookup"><span data-stu-id="9ce7a-118">Custom send pipeline</span></span> | <span data-ttu-id="9ce7a-119">-自訂的管線會在將執行個體訊息轉譯成一般檔案格式; 使用 「 一般檔案組合器和一般檔案結構描述一般檔案組合器 」 本身並非管線，設定傳送管線中的時，無法使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-119">-   The custom pipeline uses the Flat File Assembler and a flat file schema to translate the instance messages into flat file format; the Flat File Assembler is not itself a pipeline and cannot be used when configuring a send pipeline in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management console.</span></span> |
|   <span data-ttu-id="9ce7a-120">一般檔案結構描述</span><span class="sxs-lookup"><span data-stu-id="9ce7a-120">Flat file schema</span></span>   |                                      <span data-ttu-id="9ce7a-121">-定義所有相同記錄與欄位特性 （包含結構） 的 XML 結構描述，並提供定義轉譯成一般檔案訊息 （反之亦然） 的 XML 執行個體訊息所需的一般檔案特性的所有的機制。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-121">-   Define all of the same record and field characteristics (including structure) as an XML schema and provides a mechanism for defining all of the flat file characteristics that are required to translate an XML instance message into a flat file message (or vice versa).</span></span>                                      |
| <span data-ttu-id="9ce7a-122">訂閱篩選器</span><span class="sxs-lookup"><span data-stu-id="9ce7a-122">Subscription filter</span></span>  |                                                                                                          <span data-ttu-id="9ce7a-123">-訂用帳戶篩選器會執行實際的路由： 擷取符合根據屬性欄位的一或多個準則的訊息。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-123">-   The subscription filter performs the actual routing by capturing messages that meet one or more criteria based on property fields.</span></span>                                                                                                          |
|      <span data-ttu-id="9ce7a-124">XMLReceive</span><span class="sxs-lookup"><span data-stu-id="9ce7a-124">XMLReceive</span></span>      |                                                                                                        <span data-ttu-id="9ce7a-125">-執行對內送 XML 訊息的處理。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-125">-   Performs processing of inbound XML messages.</span></span> <span data-ttu-id="9ce7a-126">在本範例中，來源訊息使用的是訂單的 XML 表示。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-126">For this example an XML representation of a purchase order is used as the source message.</span></span>                                                                                                        |

 <span data-ttu-id="9ce7a-127">這些項目結合後產生的解決方案，可從接收位置接受 XML 檔案格式的訂單訊息，再將一般檔案訂單寫出至傳送位置。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-127">These elements are combined to produce a solution that accepts purchase order messages in XML format from the receive location and writes out a flat file purchase order to the send location.</span></span>  

## <a name="where-to-find-this-sample"></a><span data-ttu-id="9ce7a-128">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="9ce7a-128">Where to Find This Sample</span></span>  
 <span data-ttu-id="9ce7a-129">*\<範例路徑\>* \Pipelines\AssemblerDisassembler\FlatFileSend</span><span class="sxs-lookup"><span data-stu-id="9ce7a-129">*\<Samples Path\>* \Pipelines\AssemblerDisassembler\FlatFileSend</span></span>  

 <span data-ttu-id="9ce7a-130">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-130">The following table shows the files in this sample and describes their purpose.</span></span>  


|                <span data-ttu-id="9ce7a-131">檔案</span><span class="sxs-lookup"><span data-stu-id="9ce7a-131">File(s)</span></span>                |                                                                                           <span data-ttu-id="9ce7a-132">描述</span><span class="sxs-lookup"><span data-stu-id="9ce7a-132">Description</span></span>                                                                                            |
|---------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <span data-ttu-id="9ce7a-133">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="9ce7a-133">Cleanup.bat</span></span>              | <span data-ttu-id="9ce7a-134">用來解除部署組件，以及將它從全域組件快取中移除。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-134">Used to undeploy assemblies and remove them from the global assembly cache.</span></span> <span data-ttu-id="9ce7a-135">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-135">Removes send and receive ports.</span></span> <span data-ttu-id="9ce7a-136">視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-136">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span> |
| <span data-ttu-id="9ce7a-137">FlatFileSend.btproj、FlatFileSend.sln</span><span class="sxs-lookup"><span data-stu-id="9ce7a-137">FlatFileSend.btproj, FlatFileSend.sln</span></span> |                                                                           <span data-ttu-id="9ce7a-138">這個範例的專案及解決方案檔案。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-138">Project and solution files for this sample.</span></span>                                                                            |
|        <span data-ttu-id="9ce7a-139">FlatFileSendBinding.xml</span><span class="sxs-lookup"><span data-stu-id="9ce7a-139">FlatFileSendBinding.xml</span></span>        |                                                                          <span data-ttu-id="9ce7a-140">用於自動化設定，例如連接埠繫結。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-140">Used for automated setup such as port binding.</span></span>                                                                          |
|          <span data-ttu-id="9ce7a-141">FlatFileSend_in.xml</span><span class="sxs-lookup"><span data-stu-id="9ce7a-141">FlatFileSend_in.xml</span></span>          |                                                                                        <span data-ttu-id="9ce7a-142">範例輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-142">Sample input file.</span></span>                                                                                        |
|                <span data-ttu-id="9ce7a-143">PO.xsd</span><span class="sxs-lookup"><span data-stu-id="9ce7a-143">PO.xsd</span></span>                 |                                                                                  <span data-ttu-id="9ce7a-144">輸出一般檔案的結構描述。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-144">Schema for outbound flat file.</span></span>                                                                                  |
|           <span data-ttu-id="9ce7a-145">SendPipeline.btp</span><span class="sxs-lookup"><span data-stu-id="9ce7a-145">SendPipeline.btp</span></span>            |                          <span data-ttu-id="9ce7a-146">使用「一般檔案組合器」元件設定的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送管線檔案。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-146">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send pipeline file with the Flat File Assembler component.</span></span>                           |
|               <span data-ttu-id="9ce7a-147">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="9ce7a-147">Setup.bat</span></span>               |                                                                            <span data-ttu-id="9ce7a-148">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-148">Used to build and initialize this sample.</span></span>                                                                             |

## <a name="how-to-use-this-sample"></a><span data-ttu-id="9ce7a-149">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="9ce7a-149">How to Use This Sample</span></span>  
 <span data-ttu-id="9ce7a-150">您可以使用此範例，做為自己的一般檔案處理解決方案基礎。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-150">Use this sample as the basis for your own flat file processing solution.</span></span> <span data-ttu-id="9ce7a-151">您可以將本範例中所用的許多設計元素加以擴充，以符合自己的需求。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-151">You can extend many of the design elements used in this sample to fit your own requirements.</span></span>  

## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="9ce7a-152">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="9ce7a-152">Building and Initializing This Sample</span></span>  

1. <span data-ttu-id="9ce7a-153">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="9ce7a-153">In a command window, navigate to the following folder:</span></span>  

    <span data-ttu-id="9ce7a-154">*\<範例路徑\>* \Pipelines\AssemblerDisassembler\FlatFileSend</span><span class="sxs-lookup"><span data-stu-id="9ce7a-154">*\<Samples Path\>* \Pipelines\AssemblerDisassembler\FlatFileSend</span></span>  

2. <span data-ttu-id="9ce7a-155">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9ce7a-155">Run the file Setup.bat, which performs the following actions:</span></span>  

   - <span data-ttu-id="9ce7a-156">為資料夾內的這個範例建立輸入 (FFInput) 和輸出 (FFOutput) 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-156">Creates the input (FFInput) and output (FFOutput) folders for this sample in the folder:</span></span>  

      <span data-ttu-id="9ce7a-157">*\<範例路徑\>* \Pipelines\AssemblerDisassembler\FlatFileSend</span><span class="sxs-lookup"><span data-stu-id="9ce7a-157">*\<Samples Path\>* \Pipelines\AssemblerDisassembler\FlatFileSend</span></span>  

   - <span data-ttu-id="9ce7a-158">為此範例編譯 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-158">Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample.</span></span>  

   - <span data-ttu-id="9ce7a-159">建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-159">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.</span></span>  

     > [!NOTE]
     >  <span data-ttu-id="9ce7a-160">此範例會顯示下列警告時建立和繫結連接埠：`Warning: Receive handler not specified for receive location "FlatFileSend_RL"; updating with first receive handler with matching transport type. Warning: Host not specified for orchestration "FlatFileSend"; updating with first available host.`您可以放心地忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-160">This sample displays the following warnings when creating and binding the ports: `Warning: Receive handler not specified for receive location "FlatFileSend_RL"; updating with first receive handler with matching transport type. Warning: Host not specified for orchestration "FlatFileSend"; updating with first available host.` You can safely ignore these warnings.</span></span> <span data-ttu-id="9ce7a-161">(繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-161">(To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)</span></span>  

   - <span data-ttu-id="9ce7a-162">啟用接收位置並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-162">Enables the receive location, and starts the send port.</span></span>  

> [!NOTE]
>  <span data-ttu-id="9ce7a-163">在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-163">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="9ce7a-164">如果您選擇不執行 Setup.bat 就開啟和建置此範例中的專案，必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-164">If you choose to open and build the project in this sample without running Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="9ce7a-165">請使用這個金鑰組來簽署產生的組件。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-165">Use this key pair to sign the resulting assembly.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="9ce7a-166">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-166">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="9ce7a-167">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-167">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  

## <a name="running-this-sample"></a><span data-ttu-id="9ce7a-168">執行此範例</span><span class="sxs-lookup"><span data-stu-id="9ce7a-168">Running This Sample</span></span>  

1.  <span data-ttu-id="9ce7a-169">將 FlatFileSend_in.xml 檔案的複本放在 FFInput 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-169">Put a copy of the file FlatFileSend_in.xml into the folder FFInput.</span></span>  

2.  <span data-ttu-id="9ce7a-170">觀察建立於 FFOutput 資料夾內的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-170">Observe the text file created in the folder FFOutput.</span></span> <span data-ttu-id="9ce7a-171">這個文字檔的名稱是以訊息識別碼 GUID 為根據。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-171">The name of the text file is based on the message ID GUID.</span></span> <span data-ttu-id="9ce7a-172">此檔案包含相當於 XML 輸入檔 FlatFileSend_in.xml 的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="9ce7a-172">This file contains the flat file equivalent of the XML input file FlatFileSend_in.xml.</span></span>  

## <a name="classes-or-methods-used-in-this-sample"></a><span data-ttu-id="9ce7a-173">在此範例中使用的類別或方法</span><span class="sxs-lookup"><span data-stu-id="9ce7a-173">Classes or Methods Used in This Sample</span></span>  
 <span data-ttu-id="9ce7a-174">組態指令碼 Setup.bat 和 Cleanup.bat 依賴下列系統管理 Windows Management Instrumentation (WMI) 指令碼：</span><span class="sxs-lookup"><span data-stu-id="9ce7a-174">The configuration scripts Setup.bat and Cleanup.bat rely on the following administrative Windows Management Instrumentation (WMI) scripts:</span></span>  

- <span data-ttu-id="9ce7a-175">啟動傳送埠\StartSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="9ce7a-175">Start Send Port\StartSendPort.vbs</span></span>  

- <span data-ttu-id="9ce7a-176">啟用接收位置\EnableRecLoc</span><span class="sxs-lookup"><span data-stu-id="9ce7a-176">Enable Receive Location\EnableRecLoc</span></span>  

- <span data-ttu-id="9ce7a-177">移除傳送埠\RemoveSendPort</span><span class="sxs-lookup"><span data-stu-id="9ce7a-177">Remove Send Port\RemoveSendPort</span></span>  

  <span data-ttu-id="9ce7a-178">安裝和清除批次檔使用的是下列 BTSTask：</span><span class="sxs-lookup"><span data-stu-id="9ce7a-178">The setup and cleanup batch files use BTSTask as follows:</span></span>  

- <span data-ttu-id="9ce7a-179">**BTSTask ImportBindings**套用繫結檔案，並建立應用程式、 連接埠和繫結</span><span class="sxs-lookup"><span data-stu-id="9ce7a-179">**BTSTask ImportBindings** to apply the binding file and create the application, ports, and bindings</span></span>  

- <span data-ttu-id="9ce7a-180">**BTSTask RemoveApp**用以移除 FlatFileSendApplication</span><span class="sxs-lookup"><span data-stu-id="9ce7a-180">**BTSTask RemoveApp** to remove the FlatFileSendApplication</span></span>  

## <a name="see-also"></a><span data-ttu-id="9ce7a-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ce7a-181">See Also</span></span>  
- [<span data-ttu-id="9ce7a-182">一般檔案結構描述</span><span class="sxs-lookup"><span data-stu-id="9ce7a-182">Flat File Schemas</span></span>](../core/flat-file-schemas.md)   
- [<span data-ttu-id="9ce7a-183">預設管線</span><span class="sxs-lookup"><span data-stu-id="9ce7a-183">Default Pipelines</span></span>](../core/default-pipelines.md)   
- [<span data-ttu-id="9ce7a-184">Pipelines-AssemblerDisassembler (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="9ce7a-184">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)   
- <span data-ttu-id="9ce7a-185">**WMI 指令碼範例** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="9ce7a-185">**WMI Script Samples** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
- [<span data-ttu-id="9ce7a-186">BTSTask 命令列參考</span><span class="sxs-lookup"><span data-stu-id="9ce7a-186">BTSTask Command-Line Reference</span></span>](../core/btstask-command-line-reference.md)   
- [<span data-ttu-id="9ce7a-187">FlatFileReceive (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="9ce7a-187">FlatFileReceive (BizTalk Server Sample)</span></span>](../core/flatfilereceive-biztalk-server-sample.md)
