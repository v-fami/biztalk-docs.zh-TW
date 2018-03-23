---
title: CBRSample （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, routing
- messages, filters
- outbound maps
- examples, messages
- messages, routing
- examples, outbound maps
- examples, filters
- messages, examples
ms.assetid: 8fba494c-9257-4eed-8b6a-867056147c2c
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b772bc44d4a745d5bfa330e7df7fcadcf2c020db
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="cbrsample-biztalk-server-sample"></a><span data-ttu-id="3c499-102">CBRSample （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="3c499-102">CBRSample (BizTalk Server Sample)</span></span>
<span data-ttu-id="3c499-103">CBRSample 範例會示範如何套用篩選條件和輸出對應，以轉換並根據內容來路由執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="3c499-103">The CBRSample sample demonstrates how to apply filters and an outbound map to transform and route instance messages based on content.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="3c499-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="3c499-104">What This Sample Does</span></span>  
 <span data-ttu-id="3c499-105">此範例會示範如何根據國碼，將內含名稱、地址和連絡資訊的訊息路由至兩個資料夾之一。</span><span class="sxs-lookup"><span data-stu-id="3c499-105">This sample demonstrates the routing of a message containing name, address, and contact information to one of two folders based on country code.</span></span> <span data-ttu-id="3c499-106">具體來說，本範例執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="3c499-106">Specifically, this sample does the following:</span></span>  
  
1.  <span data-ttu-id="3c499-107">定義內含個人基本資訊的範例訊息格式，包括含使用者識別碼和完整名稱的身份識別、含國碼的地址，以及電話連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="3c499-107">Defines a sample message format containing basic information about a person including identity with user ID and full name, address with country code, and phone contact information.</span></span>  
  
2.  <span data-ttu-id="3c499-108">升級 **CountryCode** 屬性中輸入的文件，因此它可用於連接埠篩選器，以控制轉換和路由。</span><span class="sxs-lookup"><span data-stu-id="3c499-108">Promotes the **CountryCode** property in the input document so that it can be used in a port filter to control transformation and routing.</span></span>  
  
3.  <span data-ttu-id="3c499-109">將訊息轉換為加拿大版時 **CountryCode** 等於 200 或美國版本時 **CountryCode**等於 100。</span><span class="sxs-lookup"><span data-stu-id="3c499-109">Transforms the message into a Canadian version when **CountryCode** is equal to 200 or a U.S. version when **CountryCode**is equal to 100.</span></span> <span data-ttu-id="3c499-110">這兩種轉換會通過所有的資料，除中間初始 (**初始**)。</span><span class="sxs-lookup"><span data-stu-id="3c499-110">Both transforms pass through all data except middle initial (**Initial**).</span></span> <span data-ttu-id="3c499-111">加拿大版也會對應 **狀態** 至 **州/省** 和 **ZipCode** 至 **PinCode**。</span><span class="sxs-lookup"><span data-stu-id="3c499-111">The Canadian version also maps **State** to **Province** and **ZipCode** to **PinCode**.</span></span>  
  
4.  <span data-ttu-id="3c499-112">將美國的訊息路由至 US 目錄，將加拿大的訊息路由至 CAN 目錄。</span><span class="sxs-lookup"><span data-stu-id="3c499-112">Routes U.S. messages to the US directory and Canadian messages to the CAN directory.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="3c499-113">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="3c499-113">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="3c499-114">其設計依賴 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的預設傳送和接收 XML 管線、屬性升級、訂閱篩選器和輸出對應來路由傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="3c499-114">The design relies on the default send and receive XML pipelines, property promotion, subscription filters, and outbound maps within [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to route messages.</span></span> <span data-ttu-id="3c499-115">下表列出設計元素及其原因。</span><span class="sxs-lookup"><span data-stu-id="3c499-115">The following table shows design elements and their justification.</span></span>  
  
|<span data-ttu-id="3c499-116">設計元素</span><span class="sxs-lookup"><span data-stu-id="3c499-116">Design element</span></span>|<span data-ttu-id="3c499-117">已選取的原因</span><span class="sxs-lookup"><span data-stu-id="3c499-117">Reason(s) selected</span></span>|  
|--------------------|--------------------------|  
|<span data-ttu-id="3c499-118">預設 XML 接收管線</span><span class="sxs-lookup"><span data-stu-id="3c499-118">Default XML receive pipeline</span></span>|<span data-ttu-id="3c499-119">-XMLReceive 管線支援屬性升級;PassThruReceive 管線則否。</span><span class="sxs-lookup"><span data-stu-id="3c499-119">-   The XMLReceive pipeline supports property promotion; the PassThruReceive pipeline does not.</span></span><br /><span data-ttu-id="3c499-120">-將傳入的訊息時已是 XML 格式，而且不需要基本解譯和合作對象解析之外的處理。</span><span class="sxs-lookup"><span data-stu-id="3c499-120">-   The inbound message is already in XML format and does not require processing beyond basic disassembly and party resolution.</span></span>|  
|<span data-ttu-id="3c499-121">屬性升級</span><span class="sxs-lookup"><span data-stu-id="3c499-121">Property promotion</span></span>|<span data-ttu-id="3c499-122">-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]依賴屬性欄位來進行路由。</span><span class="sxs-lookup"><span data-stu-id="3c499-122">-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]depends upon property fields to do routing.</span></span> <span data-ttu-id="3c499-123">辨別欄位可用於協調流程，不能用於路由。</span><span class="sxs-lookup"><span data-stu-id="3c499-123">Distinguished fields are used by orchestrations and cannot be used for routing.</span></span>|  
|<span data-ttu-id="3c499-124">訂閱篩選器</span><span class="sxs-lookup"><span data-stu-id="3c499-124">Subscription filter</span></span>|<span data-ttu-id="3c499-125">-訂閱篩選器會執行實際的路由所擷取的訊息，以符合一或多個屬性欄位為基礎的準則。</span><span class="sxs-lookup"><span data-stu-id="3c499-125">-   The subscription filter performs the actual routing by capturing messages that meet one or more criteria based on property fields.</span></span>|  
|<span data-ttu-id="3c499-126">輸出對應</span><span class="sxs-lookup"><span data-stu-id="3c499-126">Outbound map</span></span>|<span data-ttu-id="3c499-127">對應轉換到另一種格式的資料。</span><span class="sxs-lookup"><span data-stu-id="3c499-127">-   Maps transform data from one format to another.</span></span> <span data-ttu-id="3c499-128">範例會將輸入訊息對應至美國或加拿大的格式。</span><span class="sxs-lookup"><span data-stu-id="3c499-128">The sample maps an inbound message to either a U.S. or Canadian format.</span></span>|  
|<span data-ttu-id="3c499-129">XMLTransmit</span><span class="sxs-lookup"><span data-stu-id="3c499-129">XMLTransmit</span></span>|<span data-ttu-id="3c499-130">-執行基本組件的外寄 XML 訊息。PassThruTransmit 管線提供額外的支援。</span><span class="sxs-lookup"><span data-stu-id="3c499-130">-   Performs basic assembly of outgoing XML messages; the PassThruTransmit pipeline provides no additional support.</span></span>|  
  
 <span data-ttu-id="3c499-131">基本模式擴充後可用於更複雜的情況。</span><span class="sxs-lookup"><span data-stu-id="3c499-131">This basic pattern can be extended and used for more complex scenarios.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="3c499-132">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="3c499-132">Where to Find This Sample</span></span>  
 <span data-ttu-id="3c499-133">這個範例位於 <`Samples Path>`\Messaging\CBRSample\\。</span><span class="sxs-lookup"><span data-stu-id="3c499-133">This sample is located at <`Samples Path>`\Messaging\CBRSample\\.</span></span>  
  
 <span data-ttu-id="3c499-134">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="3c499-134">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="3c499-135">파일</span><span class="sxs-lookup"><span data-stu-id="3c499-135">File(s)</span></span>|<span data-ttu-id="3c499-136">Description</span><span class="sxs-lookup"><span data-stu-id="3c499-136">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c499-137">CBRDataCAN.Xml, CBRDataUS.Xml</span><span class="sxs-lookup"><span data-stu-id="3c499-137">CBRDataCAN.Xml, CBRDataUS.Xml</span></span>|<span data-ttu-id="3c499-138">符合 CBRInputSchema.xsd 檔案中所定義結構描述的範例輸入檔。</span><span class="sxs-lookup"><span data-stu-id="3c499-138">Sample input files that conform to the schema defined in the file CBRInputSchema.xsd.</span></span>|  
|<span data-ttu-id="3c499-139">CBRInput2CANMap.btm, CBRInput2USMap.btm</span><span class="sxs-lookup"><span data-stu-id="3c499-139">CBRInput2CANMap.btm, CBRInput2USMap.btm</span></span>|<span data-ttu-id="3c499-140">加拿大的檔案與美國格式轉換，會分別對應。</span><span class="sxs-lookup"><span data-stu-id="3c499-140">Map files for the Canadian and U.S. format transformations, respectively.</span></span>|  
|<span data-ttu-id="3c499-141">CBRInputSchema.xsd, CBROutputSchemaCAN.xsd, CBROutputSchemaUS.xsd</span><span class="sxs-lookup"><span data-stu-id="3c499-141">CBRInputSchema.xsd, CBROutputSchemaCAN.xsd, CBROutputSchemaUS.xsd</span></span>|<span data-ttu-id="3c499-142">分別為輸入格式、加拿大輸出格式和美國輸出格式的結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="3c499-142">Schema files for the input format, the Canadian output format, and the U.S. output format, respectively.</span></span>|  
|<span data-ttu-id="3c499-143">CBRPromotedPropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="3c499-143">CBRPromotedPropertySchema.xsd</span></span>|<span data-ttu-id="3c499-144">對應至已升級屬性結構描述檔案 **CountryCode** 項目在 XML 輸入檔。</span><span class="sxs-lookup"><span data-stu-id="3c499-144">Schema file for the promoted property that corresponds to the **CountryCode** element in the XML input files.</span></span>|  
|<span data-ttu-id="3c499-145">CBRSample.btproj, CBRSample.sln</span><span class="sxs-lookup"><span data-stu-id="3c499-145">CBRSample.btproj, CBRSample.sln</span></span>|<span data-ttu-id="3c499-146">此範例的 BizTalk 專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="3c499-146">BizTalk project and solution files for this sample.</span></span>|  
|<span data-ttu-id="3c499-147">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="3c499-147">Cleanup.bat</span></span>|<span data-ttu-id="3c499-148">用來解除部署組件，以及將它從全域組件快取中移除。</span><span class="sxs-lookup"><span data-stu-id="3c499-148">Used to undeploy assemblies and remove them from the global assembly cache.</span></span> <span data-ttu-id="3c499-149">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="3c499-149">Removes send and receive ports.</span></span> <span data-ttu-id="3c499-150">視需要移除 Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="3c499-150">Removes Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="3c499-151">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="3c499-151">Setup.bat</span></span>|<span data-ttu-id="3c499-152">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="3c499-152">Used to build and initialize this sample.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="3c499-153">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="3c499-153">How to Use This Sample</span></span>  
 <span data-ttu-id="3c499-154">使用此範例，做為根據內容路由訊息之必要動作的操作範例。</span><span class="sxs-lookup"><span data-stu-id="3c499-154">Use this sample as a working example of the actions required to route a message based on content.</span></span>  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="3c499-155">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="3c499-155">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="3c499-156">若要建置和初始化 CBRSample 範例，必須為此範例建置和部署 BizTalk 專案、設定接收埠和位置，以及設定兩個不同的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="3c499-156">To build and initialize the CBRSample sample, you need to build and deploy the BizTalk project for this sample, configure the receive port and location, and configure two different send ports.</span></span>  
  
#### <a name="to-build-and-deploy-the-biztalk-project-for-this-sample"></a><span data-ttu-id="3c499-157">若要為此範例建置和部署 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="3c499-157">To build and deploy the BizTalk project for this sample</span></span>  
  
1.  <span data-ttu-id="3c499-158">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="3c499-158">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="3c499-159">`<Samples Path>` **\Messaging\CBRSample**</span><span class="sxs-lookup"><span data-stu-id="3c499-159">`<Samples Path>` **\Messaging\CBRSample**</span></span>  
  
2.  <span data-ttu-id="3c499-160">執行 **Setup.bat**, ，其可執行下列動作︰</span><span class="sxs-lookup"><span data-stu-id="3c499-160">Run **Setup.bat**, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="3c499-161">建立輸入 (**中**) 和輸出資料夾 (**美國** 和 **可以**) 此範例。</span><span class="sxs-lookup"><span data-stu-id="3c499-161">Creates the input (**In**) and output folders (**US** and **CAN**) for this sample.</span></span>  
  
    -   <span data-ttu-id="3c499-162">為這個範例編譯和部署 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="3c499-162">Compiles and deploys the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample.</span></span>  
  
    -   <span data-ttu-id="3c499-163">建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="3c499-163">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c499-164">此範例會在建立和繫結連接埠時顯示警告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3c499-164">This sample displays the following warning when creating and binding the ports:</span></span>  
    >   
    >  <span data-ttu-id="3c499-165">**警告︰ 指定接收處理常式未針對接收位置"CBRReceiveLocation";更新與第一個接收處理常式使用符合傳輸類型。**</span><span class="sxs-lookup"><span data-stu-id="3c499-165">**Warning: Receive handler not specified for receive location "CBRReceiveLocation"; updating with first receive handler with matching transport type.**</span></span>  
    >   
    >  <span data-ttu-id="3c499-166">您可以放心地忽略此警告。</span><span class="sxs-lookup"><span data-stu-id="3c499-166">You can safely ignore this warning.</span></span> <span data-ttu-id="3c499-167">(繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。</span><span class="sxs-lookup"><span data-stu-id="3c499-167">(To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c499-168">在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="3c499-168">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c499-169">如果您選擇不執行 Setup.bat 就開啟和建置此範例中的專案，必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="3c499-169">If you choose to open and build the project in this sample without running Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="3c499-170">請使用這個金鑰組來簽署產生的組件。</span><span class="sxs-lookup"><span data-stu-id="3c499-170">Use this key pair to sign the resulting assembly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c499-171">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="3c499-171">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="3c499-172">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="3c499-172">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
#### <a name="to-prepare-to-configure-the-receive-port-and-location-and-the-send-ports"></a><span data-ttu-id="3c499-173">若要準備設定接收埠和位置以及傳送埠</span><span class="sxs-lookup"><span data-stu-id="3c499-173">To prepare to configure the receive port and location, and the send ports</span></span>  
  
1.  <span data-ttu-id="3c499-174">在 **Microsoft SQL Management Studio**, ，選取正確的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="3c499-174">In **Microsoft SQL Management Studio**, select the correct BizTalk Management database.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c499-175">「BizTalk 管理」資料庫也稱為「BizTalk 組態」資料庫。</span><span class="sxs-lookup"><span data-stu-id="3c499-175">The BizTalk Management database is also referred to as the BizTalk Configuration database.</span></span>  
  
#### <a name="to-configure-enlist-and-start-the-us-send-port"></a><span data-ttu-id="3c499-176">若要設定、 登錄和啟動美國傳送埠</span><span class="sxs-lookup"><span data-stu-id="3c499-176">To configure, enlist, and start the U.S. send port</span></span>  
  
1.  <span data-ttu-id="3c499-177">在 BizTalk Server 管理主控台中，展開 **傳送埠**, ，以滑鼠右鍵按一下 **cbrussendport**, ，然後按一下  **編輯**。</span><span class="sxs-lookup"><span data-stu-id="3c499-177">In the BizTalk Server Administration console, expand **Send Ports**, right-click **CBRUSSendPort**, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="3c499-178">在 **靜態單向傳送埠屬性** 對話方塊 對話方塊中，左邊的資料夾樹狀目錄中選取 **篩選 & 對應 #124;篩選器**, ，然後加入新的資料列，藉由設定 **屬性** 至 **CBRSample.CountryCode**, 、 離開 **運算子** 資料行設定為 **==**, ，並設定 **值** 資料行 **100**。</span><span class="sxs-lookup"><span data-stu-id="3c499-178">In the **Static One-Way Send Port Properties** dialog box, in the folder tree to the left of the dialog box, select **Filters & Mapping &#124; Filters**, and then add a new row by setting **Property** to **CBRSample.CountryCode**, leaving the **Operator** column set to **==**, and setting the **Value** column to **100**.</span></span>  
  
3.  <span data-ttu-id="3c499-179">在對話方塊左邊的資料夾樹狀目錄中，選取 **篩選 & 對應 #124;輸出對應**, ，請將 **要套用的對應** 屬性 **CBRSample.CBRInput2USMap**, ，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="3c499-179">In the folder tree to the left of the dialog box, select **Filters & Mapping &#124; Outbound Maps**, set the **Map to apply** property to **CBRSample.CBRInput2USMap**, and then click **OK**.</span></span> <span data-ttu-id="3c499-180">您可能必須按一下捲軸按鈕，才能檢視到對應。</span><span class="sxs-lookup"><span data-stu-id="3c499-180">You may have to click the scroll button to bring the map into view.</span></span>  
  
#### <a name="to-configure-enlist-and-start-the-canadian-send-port"></a><span data-ttu-id="3c499-181">若要設定、登錄和啟動加拿大傳送埠</span><span class="sxs-lookup"><span data-stu-id="3c499-181">To configure, enlist, and start the Canadian send port</span></span>  
  
1.  <span data-ttu-id="3c499-182">在 BizTalk Server 管理主控台中，展開 **傳送埠**, ，以滑鼠右鍵按一下 **cbrcansendport**, ，然後按一下  **編輯**。</span><span class="sxs-lookup"><span data-stu-id="3c499-182">In the BizTalk Server Administration console, expand **Send Ports**, right-click **CBRCANSendPort**, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="3c499-183">在 **靜態單向傳送埠屬性** 對話方塊 對話方塊中，左邊的資料夾樹狀目錄中選取 **篩選 & 對應 #124;篩選器**, ，然後加入新的資料列，藉由設定 **屬性** 至 **CBRSample.CountryCode**, 、 離開 **運算子** 資料行設定為 **==**, ，並設定 **值** 資料行 **200**。</span><span class="sxs-lookup"><span data-stu-id="3c499-183">In the **Static One-Way Send Port Properties** dialog box, in the folder tree to the left of the dialog box, select **Filters & Mapping &#124; Filters**, and then add a new row by setting **Property** to **CBRSample.CountryCode**, leaving the **Operator** column set to **==**, and setting the **Value** column to **200**.</span></span>  
  
3.  <span data-ttu-id="3c499-184">在對話方塊左邊的資料夾樹狀目錄中，選取 **篩選 & 對應 #124;輸出對應**, ，請將 **要套用的對應** 屬性 **CBRSample.CBRInput2CANMap**, ，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="3c499-184">In the folder tree to the left of the dialog box, select **Filters & Mapping &#124; Outbound Maps**, set the **Map to apply** property to **CBRSample.CBRInput2CANMap**, and then click **OK**.</span></span>  
  
 <span data-ttu-id="3c499-185">這些步驟會將傳送埠連接至接收埠。</span><span class="sxs-lookup"><span data-stu-id="3c499-185">These steps connect the send port to the receive port.</span></span> <span data-ttu-id="3c499-186">範例使用已升級的屬性來路由文件。</span><span class="sxs-lookup"><span data-stu-id="3c499-186">The sample uses promoted properties to route the documents.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3c499-187"> 現在已準備就緒可使用此範例。</span><span class="sxs-lookup"><span data-stu-id="3c499-187"> is ready now to work with this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="3c499-188">執行此範例</span><span class="sxs-lookup"><span data-stu-id="3c499-188">Running This Sample</span></span>  
 <span data-ttu-id="3c499-189">請使用下列程序執行 CBRSample 範例。</span><span class="sxs-lookup"><span data-stu-id="3c499-189">Use the following procedure to run the CBRSample sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="3c499-190">執行此範例</span><span class="sxs-lookup"><span data-stu-id="3c499-190">To run this sample</span></span>  
  
1.  <span data-ttu-id="3c499-191">複製輸入的檔 **[cbrdatacan.xml]** 和 **[cbrdataus.xml]**, ，到下列輸入資料夾︰</span><span class="sxs-lookup"><span data-stu-id="3c499-191">Copy the input files, **CBRDataCAN.xml** and **CBRDataUS.xml**, into the following input folder:</span></span>  
  
     <span data-ttu-id="3c499-192">`<Samples Path>` **\Messaging\CBRSample\In**</span><span class="sxs-lookup"><span data-stu-id="3c499-192">`<Samples Path>` **\Messaging\CBRSample\In**</span></span>  
  
2.  <span data-ttu-id="3c499-193">觀察每個檔案如何轉換和路由傳送至下列其中兩個輸出的值為基礎的資料夾其 **CountryCode** 項目 (100 和 200):</span><span class="sxs-lookup"><span data-stu-id="3c499-193">Observe how each of these files is transformed and routed to one of the following two output folders based on the value of their **CountryCode** element (100 versus 200):</span></span>  
  
    -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3c499-194"> 轉換和路由的輸入的檔**[cbrdatacan.xml]**至資料夾：</span><span class="sxs-lookup"><span data-stu-id="3c499-194"> transforms and routes the input file **CBRDataCAN.xml** to the folder:</span></span>  
  
         <span data-ttu-id="3c499-195">`<Samples Path>` **\Messaging\CBRSample\CAN**</span><span class="sxs-lookup"><span data-stu-id="3c499-195">`<Samples Path>` **\Messaging\CBRSample\CAN**</span></span>  
  
    -   <span data-ttu-id="3c499-196">BizTalk Server 轉換和路由的輸入的檔 **[cbrdataus.xml]** 資料夾︰</span><span class="sxs-lookup"><span data-stu-id="3c499-196">BizTalk Server transforms and routes the input file **CBRDataUS.xml** to the folder:</span></span>  
  
         <span data-ttu-id="3c499-197">`<Samples Path>` **\Messaging\CBRSample\US**</span><span class="sxs-lookup"><span data-stu-id="3c499-197">`<Samples Path>` **\Messaging\CBRSample\US**</span></span>  
  
## <a name="classes-or-methods-used-in-this-sample"></a><span data-ttu-id="3c499-198">在此範例中使用的類別或方法</span><span class="sxs-lookup"><span data-stu-id="3c499-198">Classes or Methods Used in This Sample</span></span>  
 <span data-ttu-id="3c499-199">無。</span><span class="sxs-lookup"><span data-stu-id="3c499-199">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c499-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c499-200">See Also</span></span>  
 <span data-ttu-id="3c499-201">[預設管線](../core/default-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="3c499-201">[Default Pipelines](../core/default-pipelines.md) </span></span>  
 <span data-ttu-id="3c499-202">[如何設定傳送埠的輸出對應](../core/how-to-configure-outbound-maps-for-a-send-port.md) </span><span class="sxs-lookup"><span data-stu-id="3c499-202">[How to Configure Outbound Maps for a Send Port](../core/how-to-configure-outbound-maps-for-a-send-port.md) </span></span>  
 [<span data-ttu-id="3c499-203">傳訊 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="3c499-203">Messaging (BizTalk Server Samples Folder)</span></span>](../core/messaging-biztalk-server-samples-folder.md)