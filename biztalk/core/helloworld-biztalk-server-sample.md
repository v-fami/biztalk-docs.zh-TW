---
title: "HelloWorld （BizTalk Server 範例） |Microsoft 文件"
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
- orchestrations, messages
ms.assetid: 4416029a-ca76-45a4-b66c-b44cb71ded58
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a5e8057837012d27a877117a169c2cd04fa3d8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="helloworld-biztalk-server-sample"></a><span data-ttu-id="3bb14-102">HelloWorld （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="3bb14-102">HelloWorld (BizTalk Server Sample)</span></span>
<span data-ttu-id="3bb14-103">HelloWorld 範例示範如何使用 BizTalk 協調流程，將 XML 訊息 (訂單) 轉換為相關但不同的訊息類型 (發票)。</span><span class="sxs-lookup"><span data-stu-id="3bb14-103">The HelloWorld sample demonstrates how to use BizTalk orchestrations to convert an XML message (a purchase order) into a related, but distinct, type of message (an invoice).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="3bb14-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="3bb14-104">What This Sample Does</span></span>  
 <span data-ttu-id="3bb14-105">這個範例會設定**中**做為接收位置的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3bb14-105">This sample configures the **In** folder as a receive location.</span></span> <span data-ttu-id="3bb14-106">當您將檔案，例如範例檔案**SamplePOInput.xml**，到這個資料夾，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用下列步驟處理訊息：</span><span class="sxs-lookup"><span data-stu-id="3bb14-106">When you place a file, such as the sample file **SamplePOInput.xml**, into this folder, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes the message using the following steps:</span></span>  
  
1.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3bb14-107"> 從接收位置資料夾擷取 XML 訂單訊息。</span><span class="sxs-lookup"><span data-stu-id="3bb14-107"> retrieves the XML purchase order message from the receive location folder.</span></span>  
  
2.  <span data-ttu-id="3bb14-108">協調流程使用對應檔案，從 XML 訂單建立 XML 發票。</span><span class="sxs-lookup"><span data-stu-id="3bb14-108">The orchestration uses the map file to create an XML invoice from the XML purchase order.</span></span>  
  
3.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3bb14-109">將產生的 XML 發票訊息放到傳送配接器**出**資料夾。</span><span class="sxs-lookup"><span data-stu-id="3bb14-109"> places the resulting XML invoice message into the send adapter **Out** folder.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="3bb14-110">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="3bb14-110">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="3bb14-111">在公司間的訊息交換案例中，通常必須將從交易夥伴收到的輸入訊息轉換為內部應用程式可辨識的格式。</span><span class="sxs-lookup"><span data-stu-id="3bb14-111">In an intercompany message-exchange scenario, it is often necessary to convert inbound messages received from trading partners into a format that internal applications can recognize.</span></span> <span data-ttu-id="3bb14-112">這個範例會使用**接收**圖形，**轉換**圖形，而**傳送**」 圖形達到這個結果。</span><span class="sxs-lookup"><span data-stu-id="3bb14-112">This sample uses a **Receive** shape, a **Transform** shape, and a **Send** shape to achieve this result.</span></span> <span data-ttu-id="3bb14-113">**轉換**圖形在扮演重要的角色在此範例中，所以發生訊息格式轉換。</span><span class="sxs-lookup"><span data-stu-id="3bb14-113">The **Transform** shape plays the important role in this sample because it is where the message format conversion occurs.</span></span> <span data-ttu-id="3bb14-114">您拖曳**轉換**塑造成您的協調流程，並為其設定來源訊息、 對應名稱和目的訊息。</span><span class="sxs-lookup"><span data-stu-id="3bb14-114">You drag a **Transform** shape into your orchestration and configure the source message, map name, and destination message for it.</span></span> <span data-ttu-id="3bb14-115">在執行階段，會使用您所指定的對應將來源訊息對應到目的訊息。</span><span class="sxs-lookup"><span data-stu-id="3bb14-115">During run time, the source message is mapped to the destination message by using the map you designated.</span></span>  
  
 <span data-ttu-id="3bb14-116">如需有關**轉換**圖形，請參閱[如何設定 「 轉換 」 圖形](../core/how-to-configure-the-transform-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="3bb14-116">For more information about the **Transform** shape, see [How to Configure the Transform Shape](../core/how-to-configure-the-transform-shape.md).</span></span> <span data-ttu-id="3bb14-117">如需建置對應的詳細資訊，請參閱[建立對應使用 BizTalk 對應工具](../core/creating-maps-using-biztalk-mapper.md)。</span><span class="sxs-lookup"><span data-stu-id="3bb14-117">For more information about building a map, see [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md).</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="3bb14-118">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="3bb14-118">Where to Find This Sample</span></span>  
 <span data-ttu-id="3bb14-119">\<*範例路徑*> \Orchestrations\HelloWorld\\</span><span class="sxs-lookup"><span data-stu-id="3bb14-119">\<*Samples Path*>\Orchestrations\HelloWorld\\</span></span>  
  
 <span data-ttu-id="3bb14-120">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="3bb14-120">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="3bb14-121">檔案</span><span class="sxs-lookup"><span data-stu-id="3bb14-121">File(s)</span></span>|<span data-ttu-id="3bb14-122">Description</span><span class="sxs-lookup"><span data-stu-id="3bb14-122">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3bb14-123">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="3bb14-123">Cleanup.bat</span></span>|<span data-ttu-id="3bb14-124">用來解除部署組件，以及將它從全域組件快取中移除。</span><span class="sxs-lookup"><span data-stu-id="3bb14-124">Used to undeploy assemblies and remove them from the global assembly cache.</span></span> <span data-ttu-id="3bb14-125">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="3bb14-125">Removes send and receive ports.</span></span> <span data-ttu-id="3bb14-126">視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="3bb14-126">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="3bb14-127">HelloOrchestration.odx</span><span class="sxs-lookup"><span data-stu-id="3bb14-127">HelloOrchestration.odx</span></span>|<span data-ttu-id="3bb14-128">協調訂單到發票之轉換的協調流程。</span><span class="sxs-lookup"><span data-stu-id="3bb14-128">Orchestration that coordinates the conversion of the purchase order into an invoice.</span></span>|  
|<span data-ttu-id="3bb14-129">HelloWorld.btproj, HelloWorld.sln</span><span class="sxs-lookup"><span data-stu-id="3bb14-129">HelloWorld.btproj, HelloWorld.sln</span></span>|<span data-ttu-id="3bb14-130">這個範例的專案及解決方案檔案。</span><span class="sxs-lookup"><span data-stu-id="3bb14-130">Project and solution files for this sample.</span></span>|  
|<span data-ttu-id="3bb14-131">HelloWorldBinding.xml</span><span class="sxs-lookup"><span data-stu-id="3bb14-131">HelloWorldBinding.xml</span></span>|<span data-ttu-id="3bb14-132">用於自動化設定，例如連接埠繫結。</span><span class="sxs-lookup"><span data-stu-id="3bb14-132">Used for automated setup such as port binding.</span></span>|  
|<span data-ttu-id="3bb14-133">InvoiceSchema.xsd, POSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="3bb14-133">InvoiceSchema.xsd, POSchema.xsd</span></span>|<span data-ttu-id="3bb14-134">分別是發票和訂單訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3bb14-134">Schemas for the invoice and purchase order messages, respectively.</span></span>|  
|<span data-ttu-id="3bb14-135">POToInvoice.btm</span><span class="sxs-lookup"><span data-stu-id="3bb14-135">POToInvoice.btm</span></span>|<span data-ttu-id="3bb14-136">將訂單轉換為發票的對應。</span><span class="sxs-lookup"><span data-stu-id="3bb14-136">Map for converting the purchase order to an invoice.</span></span>|  
|<span data-ttu-id="3bb14-137">SamplePOInput.xml</span><span class="sxs-lookup"><span data-stu-id="3bb14-137">SamplePOInput.xml</span></span>|<span data-ttu-id="3bb14-138">範例輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="3bb14-138">Sample input file.</span></span>|  
|<span data-ttu-id="3bb14-139">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="3bb14-139">Setup.bat</span></span>|<span data-ttu-id="3bb14-140">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="3bb14-140">Used to build and initialize this sample.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="3bb14-141">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="3bb14-141">Building and Initializing This Sample</span></span>  
  
#### <a name="to-build-and-initialize-the-helloworld-sample"></a><span data-ttu-id="3bb14-142">建置和初始化 HelloWorld 範例</span><span class="sxs-lookup"><span data-stu-id="3bb14-142">To build and initialize the HelloWorld sample</span></span>  
  
1.  <span data-ttu-id="3bb14-143">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="3bb14-143">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="3bb14-144">\<*範例路徑*> \Orchestrations\HelloWorld</span><span class="sxs-lookup"><span data-stu-id="3bb14-144">\<*Samples Path*>\Orchestrations\HelloWorld</span></span>  
  
2.  <span data-ttu-id="3bb14-145">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3bb14-145">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="3bb14-146">在下列資料夾中為這個範例建立輸入 (In) 和輸出 (Out) 資料夾：</span><span class="sxs-lookup"><span data-stu-id="3bb14-146">Creates the input (In) and output (Out) folders for this sample in the following folder:</span></span>  
  
         <span data-ttu-id="3bb14-147">\<*範例路徑*> \Orchestrations\HelloWorld</span><span class="sxs-lookup"><span data-stu-id="3bb14-147">\<*Samples Path*>\Orchestrations\HelloWorld</span></span>  
  
    -   <span data-ttu-id="3bb14-148">為此範例編譯 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="3bb14-148">Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample.</span></span>  
  
    -   <span data-ttu-id="3bb14-149">建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置以及傳送埠和接收埠，並將其繫結至協調流程。</span><span class="sxs-lookup"><span data-stu-id="3bb14-149">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports to the orchestration.</span></span>  
  
    -   <span data-ttu-id="3bb14-150">啟用接收位置並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="3bb14-150">Enables the receive location, and starts the send port.</span></span> <span data-ttu-id="3bb14-151">登錄和啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="3bb14-151">Enlists and starts orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3bb14-152">在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="3bb14-152">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span> <span data-ttu-id="3bb14-153">您可檢視事件記錄進行確認。</span><span class="sxs-lookup"><span data-stu-id="3bb14-153">You can confirm this by viewing your event logs.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="3bb14-154">執行此範例</span><span class="sxs-lookup"><span data-stu-id="3bb14-154">Running This Sample</span></span>  
  
#### <a name="to-run-the-helloworld-sample"></a><span data-ttu-id="3bb14-155">執行 HelloWorld 範例</span><span class="sxs-lookup"><span data-stu-id="3bb14-155">To run the HelloWorld sample</span></span>  
  
1.  <span data-ttu-id="3bb14-156">Samplepoinput 檔的複本貼到**中**資料夾。</span><span class="sxs-lookup"><span data-stu-id="3bb14-156">Paste a copy of the file SamplePOInput.xml into the **In** folder.</span></span>  
  
2.  <span data-ttu-id="3bb14-157">觀察中建立的.xml 檔案**出**資料夾。</span><span class="sxs-lookup"><span data-stu-id="3bb14-157">Observe the .xml file created in the **Out** folder.</span></span> <span data-ttu-id="3bb14-158">此檔案包含從輸入檔案 SamplePOInput.xml 建構的 XML 發票。</span><span class="sxs-lookup"><span data-stu-id="3bb14-158">This file contains the XML invoice constructed from the input file SamplePOInput.xml.</span></span> <span data-ttu-id="3bb14-159">這個檔案的名稱的格式是\< *MessageID*>.xml，其中 *\<MessageID >*產生來唯一識別訊息的 GUID。</span><span class="sxs-lookup"><span data-stu-id="3bb14-159">The format of the name of this file is \<*MessageID*>.xml, where *\<MessageID>* is the GUID generated to uniquely identify the message.</span></span>  
  
## <a name="uninstalling-this-sample"></a><span data-ttu-id="3bb14-160">解除安裝這個範例</span><span class="sxs-lookup"><span data-stu-id="3bb14-160">Uninstalling This Sample</span></span>  
  
#### <a name="to-uninstall-the-helloworld-sample"></a><span data-ttu-id="3bb14-161">解除安裝 HelloWorld 範例</span><span class="sxs-lookup"><span data-stu-id="3bb14-161">To uninstall the HelloWorld sample</span></span>  
  
1.  <span data-ttu-id="3bb14-162">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="3bb14-162">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="3bb14-163">\<*範例路徑*> \Orchestrations\HelloWorld\\</span><span class="sxs-lookup"><span data-stu-id="3bb14-163">\<*Samples Path*>\Orchestrations\HelloWorld\\</span></span>  
  
2.  <span data-ttu-id="3bb14-164">執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="3bb14-164">Run Cleanup.bat.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb14-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bb14-165">See Also</span></span>  
 [<span data-ttu-id="3bb14-166">協調流程 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="3bb14-166">Orchestrations (BizTalk Server Samples Folder)</span></span>](../core/orchestrations-biztalk-server-samples-folder.md)