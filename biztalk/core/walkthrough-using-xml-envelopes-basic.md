---
title: 逐步解說： 使用 XML 信封 （基本） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content-based routing, promoting properties
- promoting properties, routing messages
- promoting properties, content-based routing
- routing, messages
- routing, promoting properties
ms.assetid: 02d0c596-0cfe-4bae-9f1b-d7dbc17e18a9
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b637f37c8d0953417ca628204fe299318b91266
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022092"
---
# <a name="walkthrough-using-xml-envelopes-basic"></a><span data-ttu-id="84252-102">逐步解說： 使用 XML 信封 （基本）</span><span class="sxs-lookup"><span data-stu-id="84252-102">Walkthrough: Using XML Envelopes (Basic)</span></span>
<span data-ttu-id="84252-103">此範例藉由實作虛構錯誤追蹤系統的一部分，示範基本的 XML 信封解譯。</span><span class="sxs-lookup"><span data-stu-id="84252-103">This example demonstrates basic XML envelope disassembly by implementing part of a fictitious error-tracking system.</span></span> <span data-ttu-id="84252-104">這個範例符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="84252-104">The example meets the following requirements:</span></span>  
  
1.  <span data-ttu-id="84252-105">錯誤訊息記錄到公司內各個不同的實體網站，再傳送至一個集中位置處理後放入各個後端系統。</span><span class="sxs-lookup"><span data-stu-id="84252-105">Error messages are logged at various physical sites within the company and sent to a central location for processing into various back-end systems.</span></span>  
  
2.  <span data-ttu-id="84252-106">錯誤訊息會以 XML 格式寫入。</span><span class="sxs-lookup"><span data-stu-id="84252-106">Error messages are written in XML format.</span></span>  
  
3.  <span data-ttu-id="84252-107">錯誤訊息可以單獨傳送，而不使用信封，也可以包含在信封中進行批次傳送。</span><span class="sxs-lookup"><span data-stu-id="84252-107">An error message can be sent singly without an envelope or as a batch contained within an envelope.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="84252-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="84252-108">Prerequisites</span></span>  
 <span data-ttu-id="84252-109">若要執行本範例，您必須已熟悉如何建立 BizTalk Server 專案、簽署組件，及使用 BizTalk Server 管理主控台檢視應用程式和連接埠。</span><span class="sxs-lookup"><span data-stu-id="84252-109">For this example you need to be comfortable with creating BizTalk projects, signing an assembly, and using the BizTalk Server Administration console to view applications and ports.</span></span> <span data-ttu-id="84252-110">您也應該事先瞭解中提到的觀念[逐步解說： 部署基本 BizTalk 應用程式](../core/walkthrough-deploying-a-basic-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="84252-110">You should also be comfortable with the ideas presented in [Walkthrough: Deploying a Basic BizTalk Application](../core/walkthrough-deploying-a-basic-biztalk-application.md).</span></span>  
  
## <a name="what-this-example-does"></a><span data-ttu-id="84252-111">本範例的工作項目</span><span class="sxs-lookup"><span data-stu-id="84252-111">What This Example Does</span></span>  
 <span data-ttu-id="84252-112">此範例定義信封結構描述並使用 XmlDisassembler 管線，以處理內含單一錯誤訊息或批次錯誤訊息的內送訊息。</span><span class="sxs-lookup"><span data-stu-id="84252-112">The example processes inbound messages containing either a single error message or a batch of error messages by defining an envelope schema and using the XmlDisassembler pipeline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84252-113">範例</span><span class="sxs-lookup"><span data-stu-id="84252-113">Example</span></span>  
 <span data-ttu-id="84252-114">若要建立範例，請依照以下各節所列的步驟進行。</span><span class="sxs-lookup"><span data-stu-id="84252-114">To create the example, follow the steps outlined in the following sections.</span></span>  
  
### <a name="create-a-new-biztalk-project"></a><span data-ttu-id="84252-115">建立新的 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="84252-115">Create a New BizTalk Project</span></span>  
 <span data-ttu-id="84252-116">建置方案前，您必須建立 BizTalk 專案、確定其具備強式名稱，並為其指定應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="84252-116">Before building a solution you need to create a BizTalk project, ensure that it is strongly named, and assign it an application name.</span></span> <span data-ttu-id="84252-117">指定應用程式名稱可避免 BizTalk Server 將方案部署至預設的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="84252-117">Assigning an application name prevents BizTalk Server from deploying the solution into the default BizTalk application.</span></span>  
  
##### <a name="to-create-and-configure-a-new-biztalk-project"></a><span data-ttu-id="84252-118">建立和設定新的 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="84252-118">To create and configure a new BizTalk project</span></span>  
  
1. <span data-ttu-id="84252-119">使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 建立新的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="84252-119">Use [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to create a new BizTalk project.</span></span> <span data-ttu-id="84252-120">呼叫專案**BasicXMLEnvelope**。</span><span class="sxs-lookup"><span data-stu-id="84252-120">Call the project **BasicXMLEnvelope**.</span></span>  
  
2. <span data-ttu-id="84252-121">產生金鑰檔並將其指派給專案。</span><span class="sxs-lookup"><span data-stu-id="84252-121">Generate a key file and assign it to the project.</span></span> <span data-ttu-id="84252-122">如需有關這項工作的詳細資訊，請參閱 <<c0> [ 如何設定強式名稱組件金鑰檔案](../core/how-to-configure-a-strong-name-assembly-key-file.md)。</span><span class="sxs-lookup"><span data-stu-id="84252-122">For more information about this task, see [How to Configure a Strong Name Assembly Key File](../core/how-to-configure-a-strong-name-assembly-key-file.md).</span></span>  
  
3. <span data-ttu-id="84252-123">在專案的部署組態屬性，將指派**應用程式名稱**並設定**重新啟動主控件執行個體**到`True`。</span><span class="sxs-lookup"><span data-stu-id="84252-123">In the deployment configuration properties for the project, assign an **Application Name** and set **Restart Host Instances** to `True`.</span></span> <span data-ttu-id="84252-124">設定此旗標係指示主控件清除組件所有已快取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="84252-124">Setting this flag tells the host to clear any cached instances of the assembly.</span></span>  
  
### <a name="create-the-error-schema"></a><span data-ttu-id="84252-125">建立 Error 結構描述</span><span class="sxs-lookup"><span data-stu-id="84252-125">Create the Error Schema</span></span>  
 <span data-ttu-id="84252-126">在此步驟中，您要建立 Error 結構描述。</span><span class="sxs-lookup"><span data-stu-id="84252-126">In this step you create the Error schema.</span></span> <span data-ttu-id="84252-127">它會定義系統的關鍵訊息。</span><span class="sxs-lookup"><span data-stu-id="84252-127">It defines the key message for the system.</span></span>  
  
##### <a name="to-create-the-error-schema"></a><span data-ttu-id="84252-128">若要建立 Error 結構描述</span><span class="sxs-lookup"><span data-stu-id="84252-128">To create the Error schema</span></span>  
  
1. <span data-ttu-id="84252-129">新增名稱為 "Error" 的結構描述至專案。</span><span class="sxs-lookup"><span data-stu-id="84252-129">Add a new schema named "Error" to the project.</span></span>  
  
2. <span data-ttu-id="84252-130">變更結構描述目標命名空間**http://BasicXMLEnvelope**。</span><span class="sxs-lookup"><span data-stu-id="84252-130">Change the target namespace for the schema to **http://BasicXMLEnvelope**.</span></span>  
  
3. <span data-ttu-id="84252-131">變更結構描述屬性**Element FormDefault**下方**進階**類別**Qualified**。</span><span class="sxs-lookup"><span data-stu-id="84252-131">Change the schema property **Element FormDefault** under the **Advanced** category to **Qualified**.</span></span> <span data-ttu-id="84252-132">這表示區域宣告項目必須由執行個體文件中的目標命名空間限定。</span><span class="sxs-lookup"><span data-stu-id="84252-132">This indicates that locally declared elements must be qualified by the target namespace in an instance document.</span></span>  
  
4. <span data-ttu-id="84252-133">重新命名根節點為 "Error"，並建立下列五個子項目 (括號內顯示其個別的類型)：</span><span class="sxs-lookup"><span data-stu-id="84252-133">Rename the root node "Error" and create five child elements with the types indicated:</span></span>  
  
   - <span data-ttu-id="84252-134">ID (xs:int)</span><span class="sxs-lookup"><span data-stu-id="84252-134">ID, xs:int</span></span>  
  
   - <span data-ttu-id="84252-135">Type (xs:int)</span><span class="sxs-lookup"><span data-stu-id="84252-135">Type, xs:int</span></span>  
  
   - <span data-ttu-id="84252-136">Priority (xs:string)</span><span class="sxs-lookup"><span data-stu-id="84252-136">Priority, xs:string</span></span>  
  
   - <span data-ttu-id="84252-137">Description (xs:string)</span><span class="sxs-lookup"><span data-stu-id="84252-137">Description, xs:string</span></span>  
  
   - <span data-ttu-id="84252-138">ErrorDateTime (xs:string)</span><span class="sxs-lookup"><span data-stu-id="84252-138">ErrorDateTime, xs:string</span></span>  
  
     <span data-ttu-id="84252-139">您的結構描述應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="84252-139">Your schema should look like the following:</span></span>  
  
     <span data-ttu-id="84252-140">![已完成的錯誤結構描述](../core/media/error-schema.gif "error_schema")</span><span class="sxs-lookup"><span data-stu-id="84252-140">![Completed Error schema](../core/media/error-schema.gif "error_schema")</span></span>  
  
5. <span data-ttu-id="84252-141">建立此結構描述的範例訊息。</span><span class="sxs-lookup"><span data-stu-id="84252-141">Create a sample message for this schema.</span></span> <span data-ttu-id="84252-142">這會用來確認是否正確處理了信封外部的單一訊息。</span><span class="sxs-lookup"><span data-stu-id="84252-142">This is used to verify that single messages outside of an envelope are processed properly.</span></span> <span data-ttu-id="84252-143">下列是範例訊息：</span><span class="sxs-lookup"><span data-stu-id="84252-143">An example sample message is:</span></span>  
  
   ```  
   <Error xmlns="http://BasicXMLEnvelope">  
     <ID>1</ID>  
     <Type>5</Type>  
     <Priority>Low</Priority>  
     <Description>Sprocket widget prints reports slowly.</Description>  
     <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
   </Error>  
   ```  
  
    <span data-ttu-id="84252-144">將此訊息儲存到專案目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="84252-144">Save this message in a file in the project directory.</span></span>  
  
### <a name="create-the-envelope-schema"></a><span data-ttu-id="84252-145">建立信封結構描述</span><span class="sxs-lookup"><span data-stu-id="84252-145">Create the Envelope Schema</span></span>  
 <span data-ttu-id="84252-146">信封包含一或多個錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="84252-146">The envelope contains one or more error messages.</span></span> <span data-ttu-id="84252-147">在這個基本範例中，信封本身沒有屬性和項目。</span><span class="sxs-lookup"><span data-stu-id="84252-147">In this basic example, the envelope does not have properties and elements of its own.</span></span>  
  
##### <a name="to-create-the-envelope-schema"></a><span data-ttu-id="84252-148">若要建立信封結構描述</span><span class="sxs-lookup"><span data-stu-id="84252-148">To create the envelope schema</span></span>  
  
1.  <span data-ttu-id="84252-149">新增名稱為 "Envelope" 的結構描述至 BasicXMLEnvelope 專案。</span><span class="sxs-lookup"><span data-stu-id="84252-149">Add a new schema named "Envelope" to the BasicXMLEnvelope project.</span></span>  
  
2.  <span data-ttu-id="84252-150">變更的目標命名空間**http://BasicXMLEnvelope**。</span><span class="sxs-lookup"><span data-stu-id="84252-150">Change the target namespace to **http://BasicXMLEnvelope**.</span></span>  
  
3.  <span data-ttu-id="84252-151">將根節點的名稱，由 "Root" 變更為 "Envelope"。</span><span class="sxs-lookup"><span data-stu-id="84252-151">Change the name of the root node from "Root" to "Envelope".</span></span>  
  
4.  <span data-ttu-id="84252-152">現在將結構描述標示為信封結構描述。</span><span class="sxs-lookup"><span data-stu-id="84252-152">Now mark the schema as an envelope schema.</span></span> <span data-ttu-id="84252-153">按一下  **\<結構描述\>** 節點。</span><span class="sxs-lookup"><span data-stu-id="84252-153">Click the **\<Schema\>** node.</span></span> <span data-ttu-id="84252-154">在 屬性 窗格中，設定 結構描述參考屬性**信封**至`OK`。</span><span class="sxs-lookup"><span data-stu-id="84252-154">In the Properties pane, set the schema reference property **Envelope** to `OK`.</span></span>  
  
5.  <span data-ttu-id="84252-155">設定**Body XPath**屬性。</span><span class="sxs-lookup"><span data-stu-id="84252-155">Set the **Body XPath** property.</span></span> <span data-ttu-id="84252-156">若要這樣做，請按一下**信封**節點。</span><span class="sxs-lookup"><span data-stu-id="84252-156">To do this, click the **Envelope** node.</span></span> <span data-ttu-id="84252-157">在 [屬性] 視窗中，按一下省略符號 (**...**) 按鈕**Body XPath**屬性中，選取**信封**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="84252-157">In the Properties window, click the ellipsis (**...**) button in the **Body XPath** property, select **Envelope**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="84252-158">新增 Any 項目子系至 [Envelope] 節點。</span><span class="sxs-lookup"><span data-stu-id="84252-158">Add an Any element child to the Envelope node.</span></span> <span data-ttu-id="84252-159">錯誤訊息將會包含在此項目中。</span><span class="sxs-lookup"><span data-stu-id="84252-159">The error message will be contained in this element.</span></span> <span data-ttu-id="84252-160">您的結構描述應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="84252-160">Your schema should look like the following:</span></span>  
  
     <span data-ttu-id="84252-161">![已完成的信封結構描述](../core/media/envelope-schema.gif "envelope_schema")</span><span class="sxs-lookup"><span data-stu-id="84252-161">![Completed envelope schema](../core/media/envelope-schema.gif "envelope_schema")</span></span>  
  
7.  <span data-ttu-id="84252-162">建立包含信封及一或多則範例訊息的範例訊息。</span><span class="sxs-lookup"><span data-stu-id="84252-162">Create a sample message containing an envelope and one or more sample messages.</span></span> <span data-ttu-id="84252-163">範例訊息如下：</span><span class="sxs-lookup"><span data-stu-id="84252-163">An example message is:</span></span>  
  
    ```  
    <Envelope xmlns="http://BasicXMLEnvelope">  
      <Error>  
        <ID>102</ID>  
        <Type>0</Type>  
        <Priority>High</Priority>  
        <Description>Sprocket query fails.</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
      <Error>  
        <ID>16502</ID>  
        <Type>2</Type>  
        <Priority>Low</Priority>  
        <Description>Time threshold exceeded.</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
    </Envelope>  
    ```  
  
     <span data-ttu-id="84252-164">將此訊息儲存到專案目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="84252-164">Save this message in a file in the project directory.</span></span>  
  
### <a name="deploy-and-configure-the-send-and-receive-ports"></a><span data-ttu-id="84252-165">部署並設定傳送埠和接收埠</span><span class="sxs-lookup"><span data-stu-id="84252-165">Deploy and Configure the Send and Receive Ports</span></span>  
 <span data-ttu-id="84252-166">建立結構描述後，您必須編譯並部署專案。</span><span class="sxs-lookup"><span data-stu-id="84252-166">With the schemas created, you need to compile and deploy the project.</span></span> <span data-ttu-id="84252-167">一旦專案部署完成，即可使用「BizTalk Server 管理主控台」設定傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="84252-167">After it is deployed, you can use the BizTalk Server Administration console to configure the send and receive ports.</span></span>  
  
##### <a name="to-deploy-basicxmlenvelope"></a><span data-ttu-id="84252-168">若要部署 BasicXMLEnvelope</span><span class="sxs-lookup"><span data-stu-id="84252-168">To deploy BasicXMLEnvelope</span></span>  
  
1. <span data-ttu-id="84252-169">從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，選擇**部署 basicxmlenvelope**從 [建置] 功能表。</span><span class="sxs-lookup"><span data-stu-id="84252-169">From [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], choose **Deploy BasicXMLEnvelope** from the Build menu.</span></span> <span data-ttu-id="84252-170">這會在 BizTalk Server 中建置並部署為應用程式 "BasicXMLEnvelope"。</span><span class="sxs-lookup"><span data-stu-id="84252-170">This will build and deploy it to BizTalk Server as the application "BasicXMLEnvelope".</span></span>  
  
2. <span data-ttu-id="84252-171">在 BizTalk Server 管理主控台中，依序展開**應用程式**群組，以確認**BasicXMLEnvelope**呈現為自訂的應用程式。</span><span class="sxs-lookup"><span data-stu-id="84252-171">In the BizTalk Server Administration console, expand the **Applications** group to verify that **BasicXMLEnvelope** is present as a custom application.</span></span>  
  
##### <a name="to-configure-the-receive-port"></a><span data-ttu-id="84252-172">設定接收埠</span><span class="sxs-lookup"><span data-stu-id="84252-172">To configure the receive port</span></span>  
  
1.  <span data-ttu-id="84252-173">使用 Windows 檔案總管來建立名為"Receive"目錄，底下**BasicXMLEnvelope**專案目錄。</span><span class="sxs-lookup"><span data-stu-id="84252-173">Use Windows Explorer to create a directory named "Receive" under the **BasicXMLEnvelope** project directory.</span></span>  
  
2.  <span data-ttu-id="84252-174">在 BizTalk Server 管理主控台中，依序展開**BasicXMLEnvelope**應用程式，以滑鼠右鍵按一下**接收埠**，指向**新增**，然後按一下  **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="84252-174">In the BizTalk Server Administration console, expand the **BasicXMLEnvelope** application, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
3.  <span data-ttu-id="84252-175">在 **接收埠屬性**對話方塊方塊中，設定為"Receive"的連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="84252-175">In the **Receive Port Properties** dialog box, set the name of the port to "Receive".</span></span>  
  
4.  <span data-ttu-id="84252-176">以滑鼠右鍵按一下接收位置，然後**新增**新增接收埠。</span><span class="sxs-lookup"><span data-stu-id="84252-176">Right-click Receive Locations, and then click **New** to add a receive port.</span></span> <span data-ttu-id="84252-177">將新連接埠命名為 "ReceiveError"。</span><span class="sxs-lookup"><span data-stu-id="84252-177">Name the new port "ReceiveError".</span></span> <span data-ttu-id="84252-178">設定**接收管線**要**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="84252-178">Set the **Receive Pipeline** to **XMLReceive**.</span></span> <span data-ttu-id="84252-179">針對**傳輸類型**，選取**檔案**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="84252-179">For **Transport Type**, select **FILE**, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="84252-180">選取上面所建立的接收目錄，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="84252-180">Select the receive directory created above and click **OK**.</span></span> <span data-ttu-id="84252-181">接收埠即設定完成。</span><span class="sxs-lookup"><span data-stu-id="84252-181">Your receive port should now be configured.</span></span> <span data-ttu-id="84252-182">按一下 **確定**關閉。</span><span class="sxs-lookup"><span data-stu-id="84252-182">Click **OK** to close.</span></span>  
  
##### <a name="to-configure-the-send-port"></a><span data-ttu-id="84252-183">設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="84252-183">To configure the send port</span></span>  
  
1.  <span data-ttu-id="84252-184">使用 Windows 檔案總管底下建立名為 「 傳送 」 的目錄**BasicXMLEnvelope**專案目錄。</span><span class="sxs-lookup"><span data-stu-id="84252-184">Use Windows Explorer to create a directory named "Send" under the **BasicXMLEnvelope** project directory.</span></span>  
  
2.  <span data-ttu-id="84252-185">在 BizTalk Server 管理主控台中，依序展開**BasicXMLEnvelope**應用程式，以滑鼠右鍵按一下**傳送連接埠**，指向**新增**，然後按一下  **靜態單向**。</span><span class="sxs-lookup"><span data-stu-id="84252-185">In the BizTalk Server Administration console, expand the **BasicXMLEnvelope** application, right-click **Send Ports**, point to **New**, and then click **Static One-Way**.</span></span>  
  
3.  <span data-ttu-id="84252-186">在 **傳送埠屬性**對話方塊方塊中，設定 「 傳送 」 的連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="84252-186">In the **Send Port Properties** dialog box, set the name of the port to "Send".</span></span>  
  
4.  <span data-ttu-id="84252-187">針對**傳輸類型**，選取**檔案**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="84252-187">For **Transport Type**, select **FILE**, and then click **Configure**.</span></span> <span data-ttu-id="84252-188">為您稍早建立的傳送目錄設定的目的地資料夾，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="84252-188">Set the destination folder to the send directory you created earlier and click **OK**.</span></span>  
  
5.  <span data-ttu-id="84252-189">按一下 **篩選器**並新增有單一篩選條件：</span><span class="sxs-lookup"><span data-stu-id="84252-189">Click **Filters** and add a single filter:</span></span>  
  
    -   <span data-ttu-id="84252-190">BTS.MessageType == **http://BasicXMLEnvelope#Error**</span><span class="sxs-lookup"><span data-stu-id="84252-190">BTS.MessageType == **http://BasicXMLEnvelope#Error**</span></span>  
  
6.  <span data-ttu-id="84252-191">按一下 **確定**完成傳送埠組態。</span><span class="sxs-lookup"><span data-stu-id="84252-191">Click **OK** to complete the send port configuration.</span></span> <span data-ttu-id="84252-192">傳送埠即設定完成。</span><span class="sxs-lookup"><span data-stu-id="84252-192">Your send port should be configured.</span></span>  
  
### <a name="run-the-example"></a><span data-ttu-id="84252-193">執行範例</span><span class="sxs-lookup"><span data-stu-id="84252-193">Run the Example</span></span>  
 <span data-ttu-id="84252-194">現在即可開始執行範例。</span><span class="sxs-lookup"><span data-stu-id="84252-194">It is now time to run the example.</span></span> <span data-ttu-id="84252-195">在使用 BizTalk Server 管理主控台啟動 BasicXMLEnvelope 應用程式後，您應將測試檔案複製到接收位置，然後檢查傳送位置所產生的結果。</span><span class="sxs-lookup"><span data-stu-id="84252-195">After using the BizTalk Server Management console to start the BasicXMLEnvelope application, you will copy the test files to the receive location and observe what is produced in the send location.</span></span>  
  
##### <a name="to-run-the-basicxmlenvelope-example"></a><span data-ttu-id="84252-196">若要執行 BasicXMLEnvelope 範例</span><span class="sxs-lookup"><span data-stu-id="84252-196">To run the BasicXMLEnvelope example</span></span>  
  
1.  <span data-ttu-id="84252-197">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**BasicXMLEnvelope**應用程式，然後按一下**開始**。</span><span class="sxs-lookup"><span data-stu-id="84252-197">In the BizTalk Server Administration console, right-click the **BasicXMLEnvelope** application and then click **Start**.</span></span> <span data-ttu-id="84252-198">這樣就會登錄並啟動傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="84252-198">This will enlist and start the send and receive ports.</span></span>  
  
2.  <span data-ttu-id="84252-199">將每一個範例檔案拖曳到接收目錄中。</span><span class="sxs-lookup"><span data-stu-id="84252-199">Drop each of the sample files into the receive directory.</span></span> <span data-ttu-id="84252-200">如果使用先前提供的範例，您應該會在處理完成時發現傳送位置中有三則個別的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="84252-200">If you use the samples given earlier, you should find three individual error messages in the send location when processing is completed.</span></span>  
  
## <a name="extending-the-example"></a><span data-ttu-id="84252-201">擴充範例</span><span class="sxs-lookup"><span data-stu-id="84252-201">Extending the Example</span></span>  
 <span data-ttu-id="84252-202">您可以擴充這個範例以配合其他需求。</span><span class="sxs-lookup"><span data-stu-id="84252-202">You can extend the example to accommodate other requirements.</span></span> <span data-ttu-id="84252-203">本節說明兩種常見的案例：</span><span class="sxs-lookup"><span data-stu-id="84252-203">This section addresses two common scenarios:</span></span>  
  
- <span data-ttu-id="84252-204">如果是將錯誤批次放在信封中提交，則解譯中的個別訊息失敗應該不會阻止進一步處理其他未失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="84252-204">If a batch of errors is submitted within an envelope, individual message failures in disassembly should not prohibit other nonfailing messages from being further processed.</span></span>  
  
- <span data-ttu-id="84252-205">這些錯誤應該會按照優先順序，傳送到不同的位置。</span><span class="sxs-lookup"><span data-stu-id="84252-205">Errors should be delivered to different locations based on error priority.</span></span> <span data-ttu-id="84252-206">高優先順序的訊息會被加速處理，而其他優先順序則透過一般通道處理。</span><span class="sxs-lookup"><span data-stu-id="84252-206">High-priority messages are expedited while other priorities are handled through normal channels.</span></span>  
  
  <span data-ttu-id="84252-207">下列各節會擴充範例以處理這些需求。</span><span class="sxs-lookup"><span data-stu-id="84252-207">The following sections extend the example to handle these requirements.</span></span>  
  
### <a name="recoverable-interchange-processing"></a><span data-ttu-id="84252-208">可復原交換處理</span><span class="sxs-lookup"><span data-stu-id="84252-208">Recoverable Interchange Processing</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="84252-209"> 支援可復原交換處理。</span><span class="sxs-lookup"><span data-stu-id="84252-209"> supports recoverable interchange processing.</span></span> <span data-ttu-id="84252-210">藉由使用這項功能，您可以確保訊息批次在解譯中發生失敗時，不會整個批次都失敗，而只限於個別的訊息。</span><span class="sxs-lookup"><span data-stu-id="84252-210">By using this feature, you can ensure that batches of messages fail individually in disassembly and not as a batch.</span></span>  
  
##### <a name="to-configure-the-example-for-recoverable-interchange-processing"></a><span data-ttu-id="84252-211">若要設定可復原交換處理的範例。</span><span class="sxs-lookup"><span data-stu-id="84252-211">To configure the example for recoverable interchange processing</span></span>  
  
1.  <span data-ttu-id="84252-212">在 BizTalk Server 管理主控台中，依序展開**BasicXMLEnvelope**應用程式中，按一下**接收埠**，然後按兩下 接收埠。</span><span class="sxs-lookup"><span data-stu-id="84252-212">In the BizTalk Server Administration console, expand the **BasicXMLEnvelope** application, click **Receive Ports**, and then double-click the Receive port.</span></span> <span data-ttu-id="84252-213">這是您先前建立的連接埠。</span><span class="sxs-lookup"><span data-stu-id="84252-213">This is the port you created previously.</span></span>  
  
2.  <span data-ttu-id="84252-214">在 [**接收埠屬性**] 對話方塊中，按一下**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="84252-214">In the **Receive Port Properties** dialog box, click **Receive Locations**.</span></span> <span data-ttu-id="84252-215">按一下 [**屬性**即可啟動**ReceiveError 接收位置屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="84252-215">Click **Properties** to bring up the **ReceiveError Receive Location Properties** dialog box.</span></span> <span data-ttu-id="84252-216">按一下省略符號 (**...**) 按鈕**接收管線**。</span><span class="sxs-lookup"><span data-stu-id="84252-216">Click the ellipsis (**...**) button for the **Receive Pipeline**.</span></span>  
  
3.  <span data-ttu-id="84252-217">在 **設定管線-XMLReceive**  對話方塊中，將**可復原交換處理**屬性設`True`，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="84252-217">In the **Configure Pipeline - XMLReceive** dialog box, set the **Recoverable Interchange Processing** property to `True`, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="84252-218">按一下  **確定**以關閉**接收位置屬性**對話方塊，然後再按一下**確定**關閉**接收埠屬性**對話方塊方塊。</span><span class="sxs-lookup"><span data-stu-id="84252-218">Click **OK** to close the **Receive Location Properties** dialog box, and then click **OK** to close the **Receive Port Properties** dialog box.</span></span>  
  
##### <a name="to-create-a-sample-file-and-run-the-example"></a><span data-ttu-id="84252-219">若要建立範例檔案，然後執行範例</span><span class="sxs-lookup"><span data-stu-id="84252-219">To create a sample file and run the example</span></span>  
  
1.  <span data-ttu-id="84252-220">若要建立範例檔案，請產生範例中所建立之信封範例檔案的複本、將不存在的命名空間加入至其中一個 Error 執行個體，然後儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="84252-220">To create a sample file, make a copy of the envelope sample file created in the example, add a nonexistent namespace to one of the Error instances, and then save the file:</span></span>  
  
    ```  
    <Envelope xmlns="http://BasicXMLEnvelope">  
      <Error>  
        <ID>102</ID>  
        <Type>0</Type>  
        <Priority>High</Priority>  
        <Description>Sprocket query fails to return any sprockets even though some exist</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
      <Error xmlns="http://ThisIsAnError">  
        <ID>16502</ID>  
        <Type>2</Type>  
        <Priority>Low</Priority>  
        <Description>Time threshold exceeded.</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
    </Envelope>  
    ```  
  
2.  <span data-ttu-id="84252-221">在 BizTalk Server 管理主控台中，按一下**應用程式**，並確認**BasicXMLEnvelope**應用程式正在執行。</span><span class="sxs-lookup"><span data-stu-id="84252-221">In the BizTalk Server Administration console, click **Applications** and verify that the **BasicXMLEnvelope** application is running.</span></span>  
  
3.  <span data-ttu-id="84252-222">將訊息拖曳到接收位置中。</span><span class="sxs-lookup"><span data-stu-id="84252-222">Drop the message in the receive location.</span></span> <span data-ttu-id="84252-223">處理之後，您應該會發現傳送位置中有第一個訊息，而第二個 (低優先順序) 訊息則是在擱置佇列中。</span><span class="sxs-lookup"><span data-stu-id="84252-223">After processing, you should find the first message in the send location and the second, low-priority, message in the Suspended queue.</span></span>  
  
### <a name="content-based-routing-cbr"></a><span data-ttu-id="84252-224">以內容為基礎的路由 (CBR)</span><span class="sxs-lookup"><span data-stu-id="84252-224">Content-Based Routing (CBR)</span></span>  
 <span data-ttu-id="84252-225">您可以使用以內容為基礎的路由，根據訊息的內容來傳送路由訊息。</span><span class="sxs-lookup"><span data-stu-id="84252-225">You can use content-based routing to route messages based on their content.</span></span> <span data-ttu-id="84252-226">在此案例中，路由會根據優先順序進行，「高」優先順序訊息會進入一個傳送位置，而「低」和「中」優先順序訊息則進入不同的傳送位置。</span><span class="sxs-lookup"><span data-stu-id="84252-226">In this scenario, routing is based on priority, with High messages going to one send location and Low and Medium messages going to a different send location.</span></span>  
  
 <span data-ttu-id="84252-227">若要擴充範例，您必須完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="84252-227">To extend the sample, you must complete the following tasks:</span></span>  
  
1.  <span data-ttu-id="84252-228">升階**優先順序**BasicXMLEnvelope 專案中 Error 結構描述中的欄位。</span><span class="sxs-lookup"><span data-stu-id="84252-228">Promote the **Priority** field in the Error schema in the BasicXMLEnvelope project.</span></span> <span data-ttu-id="84252-229">以內容為基礎的路由需要升級的屬性才能路由傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="84252-229">Content-based routing relies on promoted properties to route messages.</span></span> <span data-ttu-id="84252-230">如需詳細資訊，請參閱 <<c0> [ 升級屬性](../core/promoting-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="84252-230">For more information, see [Promoting Properties](../core/promoting-properties.md).</span></span>  
  
2.  <span data-ttu-id="84252-231">建立和設定兩個額外的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="84252-231">Create and configure two additional send ports.</span></span> <span data-ttu-id="84252-232">這些連接埠會使用篩選條件來確保收到適當的訊息。</span><span class="sxs-lookup"><span data-stu-id="84252-232">The ports use a filter to ensure they receive appropriate messages.</span></span>  
  
##### <a name="to-promote-the-priority-field-in-the-error-schema"></a><span data-ttu-id="84252-233">升級 Error 結構描述中的 Priority 欄位</span><span class="sxs-lookup"><span data-stu-id="84252-233">To promote the Priority field in the Error schema</span></span>  
  
1. <span data-ttu-id="84252-234">具有**BasicXMLEnvelope**中開啟專案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟**錯誤**結構描述並展開**錯誤**節點。</span><span class="sxs-lookup"><span data-stu-id="84252-234">With the **BasicXMLEnvelope** project open in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the **Error** schema and expand the **Error** node.</span></span>  
  
2. <span data-ttu-id="84252-235">以滑鼠右鍵按一下**優先權**項目，指向**升階**，然後按一下**快速升級**。</span><span class="sxs-lookup"><span data-stu-id="84252-235">Right-click the **Priority** element, point to **Promote**, and then click **Quick Promote**.</span></span>  
  
3. <span data-ttu-id="84252-236">按一下 **確定**以確認要升級的屬性的新屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="84252-236">Click **OK** to confirm the addition of a new property schema for the promoted properties.</span></span>  
  
4. <span data-ttu-id="84252-237">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，開啟 新增屬性結構描述 propertyschema.xsd 結構描述。</span><span class="sxs-lookup"><span data-stu-id="84252-237">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, open the new property schema PropertySchema.xsd.</span></span> <span data-ttu-id="84252-238">移除結構描述中的"Field1"。</span><span class="sxs-lookup"><span data-stu-id="84252-238">Remove "Field1" from the schema.</span></span>  
  
5. <span data-ttu-id="84252-239">現在，重新編譯並重新部署方案。</span><span class="sxs-lookup"><span data-stu-id="84252-239">Now recompile and redeploy the solution.</span></span> <span data-ttu-id="84252-240">在 [建置] 功能表中，選擇 [部署 BasicXMLEnvelope]。</span><span class="sxs-lookup"><span data-stu-id="84252-240">On the Build menu, choose Deploy BasicXMLEnvelope.</span></span>  
  
6. <span data-ttu-id="84252-241">此專案已設定為要在重新部署方案時重設主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="84252-241">The project was configured to reset the host instance when the solution is redeployed.</span></span> <span data-ttu-id="84252-242">如果您變更了這個設定，就必須先停止再啟動主控件。</span><span class="sxs-lookup"><span data-stu-id="84252-242">If you have changed this, you need to stop and start the host.</span></span>  
  
##### <a name="to-configure-the-low-and-medium-priority-send-port"></a><span data-ttu-id="84252-243">設定低和中等優先順序的傳送埠</span><span class="sxs-lookup"><span data-stu-id="84252-243">To configure the low and medium-priority send port</span></span>  
  
1.  <span data-ttu-id="84252-244">使用 Windows 檔案總管底下建立名為"SendLowMediumPriority" **BasicXMLEnvelope**專案目錄。</span><span class="sxs-lookup"><span data-stu-id="84252-244">Use Windows Explorer to create a directory named "SendLowMediumPriority" under the **BasicXMLEnvelope** project directory.</span></span>  
  
2.  <span data-ttu-id="84252-245">在 BizTalk Server 管理主控台中，依序展開**BasicXMLEnvelope**應用程式，以滑鼠右鍵按一下**傳送連接埠**，指向**新增**，然後按一下  **靜態單向**。</span><span class="sxs-lookup"><span data-stu-id="84252-245">In the BizTalk Server Administration console, expand the **BasicXMLEnvelope** application, right-click **Send Ports**, point to **New**, and then click **Static One-Way**.</span></span>  
  
3.  <span data-ttu-id="84252-246">在 **傳送埠屬性**對話方塊方塊中，設定為"SendLowMediumPriority"的連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="84252-246">In the **Send Port Properties** dialog box, set the name of the port to "SendLowMediumPriority".</span></span>  
  
4.  <span data-ttu-id="84252-247">針對**傳輸類型**，選取**檔案**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="84252-247">For **Transport Type**, select **FILE**, and then click **Configure**.</span></span> <span data-ttu-id="84252-248">將目的資料夾設定為剛才建立的目錄。</span><span class="sxs-lookup"><span data-stu-id="84252-248">Set the destination folder to the directory you created earlier.</span></span> <span data-ttu-id="84252-249">按一下 **確定**關閉。</span><span class="sxs-lookup"><span data-stu-id="84252-249">Click **OK** to close.</span></span>  
  
5.  <span data-ttu-id="84252-250">按一下 **篩選器**並加入三個篩選條件運算式：</span><span class="sxs-lookup"><span data-stu-id="84252-250">Click **Filters** and add three filter expressions:</span></span>  
  
    -   <span data-ttu-id="84252-251">BTS。MessageType = =http://BasicXMLEnvelope#Error和</span><span class="sxs-lookup"><span data-stu-id="84252-251">BTS.MessageType == http://BasicXMLEnvelope#Error And</span></span>  
  
    -   <span data-ttu-id="84252-252">BasicXMLEnvelope.PropertySchema.Priority == Low Or</span><span class="sxs-lookup"><span data-stu-id="84252-252">BasicXMLEnvelope.PropertySchema.Priority == Low Or</span></span>  
  
    -   <span data-ttu-id="84252-253">BasicXMLEnvelope.PropertySchema.Priority == Medium</span><span class="sxs-lookup"><span data-stu-id="84252-253">BasicXMLEnvelope.PropertySchema.Priority == Medium</span></span>  
  
6.  <span data-ttu-id="84252-254">按一下 **確定**以完成低和中等優先順序的傳送埠設定。</span><span class="sxs-lookup"><span data-stu-id="84252-254">Click **OK** to complete the low and medium-priority send port configuration.</span></span>  
  
##### <a name="to-configure-the-high-priority-send-port"></a><span data-ttu-id="84252-255">設定高優先順序的傳送埠</span><span class="sxs-lookup"><span data-stu-id="84252-255">To configure the high-priority send port</span></span>  
  
1.  <span data-ttu-id="84252-256">使用 Windows 檔案總管底下建立名為"SendHighPriority" **BasicXMLEnvelope**專案目錄。</span><span class="sxs-lookup"><span data-stu-id="84252-256">Use Windows Explorer to create a directory named "SendHighPriority" under the **BasicXMLEnvelope** project directory.</span></span>  
  
2.  <span data-ttu-id="84252-257">在 BizTalk Server 管理主控台中，依序展開**BasicXMLEnvelope**應用程式，以滑鼠右鍵按一下**傳送連接埠**，指向**新增**，然後按一下  **靜態單向**。</span><span class="sxs-lookup"><span data-stu-id="84252-257">In the BizTalk Server Administration console, expand the **BasicXMLEnvelope** application, right-click **Send Ports**, point to **New**, and then click **Static One-Way**.</span></span>  
  
3.  <span data-ttu-id="84252-258">在 **傳送埠屬性**對話方塊方塊中，設定為"SendHighPriority"的連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="84252-258">In the **Send Port Properties** dialog box, set the name of the port to "SendHighPriority".</span></span>  
  
4.  <span data-ttu-id="84252-259">針對**傳輸類型**，選取**檔案**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="84252-259">For **Transport Type**, select **FILE**, and then click **Configure**.</span></span> <span data-ttu-id="84252-260">將目的資料夾設定為剛才建立的目錄。</span><span class="sxs-lookup"><span data-stu-id="84252-260">Set the destination folder to the directory you created earlier.</span></span> <span data-ttu-id="84252-261">按一下 **確定**關閉。</span><span class="sxs-lookup"><span data-stu-id="84252-261">Click **OK** to close.</span></span>  
  
5.  <span data-ttu-id="84252-262">按一下 **篩選器**並加入兩個篩選條件運算式：</span><span class="sxs-lookup"><span data-stu-id="84252-262">Click **Filters** and add two filter expressions:</span></span>  
  
    -   <span data-ttu-id="84252-263">BTS。MessageType = =http://BasicXMLEnvelope#Error和</span><span class="sxs-lookup"><span data-stu-id="84252-263">BTS.MessageType == http://BasicXMLEnvelope#Error And</span></span>  
  
    -   <span data-ttu-id="84252-264">BasicXMLEnvelope.PropertySchema.Priority == High</span><span class="sxs-lookup"><span data-stu-id="84252-264">BasicXMLEnvelope.PropertySchema.Priority == High</span></span>  
  
6.  <span data-ttu-id="84252-265">按一下 **確定**以完成高優先順序的傳送埠設定。</span><span class="sxs-lookup"><span data-stu-id="84252-265">Click **OK** to complete the high-priority send port configuration.</span></span>  
  
##### <a name="to-test-the-routing-solution"></a><span data-ttu-id="84252-266">測試路由方案</span><span class="sxs-lookup"><span data-stu-id="84252-266">To test the routing solution</span></span>  
  
1.  <span data-ttu-id="84252-267">在 BizTalk Server 管理主控台中，依序展開**應用程式**群組中，以滑鼠右鍵按一下**BasicXMLEnvelope**應用程式，，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="84252-267">In the BizTalk Server Administration console, expand the **Applications** group, right-click the **BasicXMLEnvelope** application, and then click **Start**.</span></span> <span data-ttu-id="84252-268">當系統提示您確認時，按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="84252-268">When prompted to confirm, click **Start**.</span></span> <span data-ttu-id="84252-269">這樣就會登錄新的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="84252-269">This enlists the new send ports.</span></span>  
  
2.  <span data-ttu-id="84252-270">將測試訊息拖曳到接收位置中。</span><span class="sxs-lookup"><span data-stu-id="84252-270">Drop the test message into the receive location.</span></span> <span data-ttu-id="84252-271">請注意錯誤訊息是如何路由傳送至不同的傳送位置：</span><span class="sxs-lookup"><span data-stu-id="84252-271">Notice how error messages are routed to the different send locations:</span></span>  
  
    -   <span data-ttu-id="84252-272">具有「低」、「中」或「高」優先順序，且順利通過訊息處理的錯誤訊息，會路由傳送至原始傳送位置 (基本範例中所設定的) 及依優先順序區分的傳送位置。</span><span class="sxs-lookup"><span data-stu-id="84252-272">Error messages that have a Low, Medium, or High priority and do not fail message processing are routed both to the original send location (configured in the core example) and the send location by priority.</span></span> <span data-ttu-id="84252-273">如果是具有「低」或「中」優先順序的訊息，原始傳送位置及「低/中」傳送位置內都會出現其複本。</span><span class="sxs-lookup"><span data-stu-id="84252-273">For messages with a Low or Medium priority, a copy appears in both the original send location and the Low/Medium send location.</span></span>  
  
    -   <span data-ttu-id="84252-274">如果已啟用可復原交換處理，就不會路由失敗的錯誤訊息和 nonfailed 的訊息適當地路由傳送如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="84252-274">If recoverable interchange processing is enabled, the failed error message is not routed and the nonfailed message is properly routed as expected.</span></span> <span data-ttu-id="84252-275">之所以不會傳送失敗訊息，是因為其訊息類型與篩選條件中使用的類型不相符。</span><span class="sxs-lookup"><span data-stu-id="84252-275">The failed message is not routed because its message type does not match the type used in the configured filters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84252-276">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84252-276">See Also</span></span>  
 <span data-ttu-id="84252-277">[可復原交換處理](../core/recoverable-interchange-processing.md) </span><span class="sxs-lookup"><span data-stu-id="84252-277">[Recoverable Interchange Processing](../core/recoverable-interchange-processing.md) </span></span>  
 <span data-ttu-id="84252-278">[升級屬性](../core/promoting-properties.md) </span><span class="sxs-lookup"><span data-stu-id="84252-278">[Promoting Properties](../core/promoting-properties.md) </span></span>  
 [<span data-ttu-id="84252-279">CBRSample (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="84252-279">CBRSample (BizTalk Server Sample)</span></span>](../core/cbrsample-biztalk-server-sample.md)