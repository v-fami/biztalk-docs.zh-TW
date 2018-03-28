---
title: 逐步解說： 使用標頭和結尾的一般檔案解譯 |Microsoft 文件
description: 使用 「 一般檔案結構描述精靈 」 來建立標頭結構描述、 結尾結構描述和內文結構描述，並再解譯一般檔案在 BizTalk Server
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715af9cc-d718-483d-b593-64462aa5a58b
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7c1406367f047794c6d8931352104bb59e6ca5b
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="walkthrough-flat-file-disassembly-using-a-header-and-trailer"></a><span data-ttu-id="3620e-103">逐步解說：使用標頭和結尾進行一般檔案解譯</span><span class="sxs-lookup"><span data-stu-id="3620e-103">Walkthrough: Flat File Disassembly Using a Header and Trailer</span></span>

## <a name="overview"></a><span data-ttu-id="3620e-104">概觀</span><span class="sxs-lookup"><span data-stu-id="3620e-104">Overview</span></span>
<span data-ttu-id="3620e-105">此逐步解說示範如何使用由「一般檔案結構描述精靈」所建立的結構描述，對包含標頭、結尾及重複訊息內文的檔案進行一般檔案解譯。</span><span class="sxs-lookup"><span data-stu-id="3620e-105">This walkthrough demonstrates the use of schemas created by the Flat File Schema Wizard to perform flat file disassembly of a file containing a header, a trailer, and a repeating message body.</span></span> <span data-ttu-id="3620e-106">在此逐步解說中，您將開發部分虛構的錯誤追蹤系統，使其符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="3620e-106">In this walkthrough, you develop part of a fictitious error-tracking system that meets the following requirements:</span></span>  
  
-   <span data-ttu-id="3620e-107">錯誤訊息記錄到公司內各個不同的實體網站，再傳送至一個集中位置處理後放入各個後端系統。</span><span class="sxs-lookup"><span data-stu-id="3620e-107">Error messages are logged at various physical sites within the company and sent to a central location for processing into various back-end systems.</span></span>  
  
-   <span data-ttu-id="3620e-108">會以一般檔案格式寫入錯誤訊息，其標頭指出位置，內文含有一或多個錯誤訊息，且結尾指出批次編號。</span><span class="sxs-lookup"><span data-stu-id="3620e-108">Error messages are written into a flat file format that contains a header indicating location, a body containing one or more error messages, and a trailer indicating the batch number.</span></span>  
  
-   <span data-ttu-id="3620e-109">如果訊息中沒有標頭、內文和結尾，則視同無效訊息。</span><span class="sxs-lookup"><span data-stu-id="3620e-109">Messages are considered invalid if they do not have a header, body, and trailer.</span></span>  
  
 <span data-ttu-id="3620e-110">完成此逐步解說後，將會建立 BizTalk Server 應用程式用於處理一般檔案，並將其輸出為 XML 以供後端系統處理。</span><span class="sxs-lookup"><span data-stu-id="3620e-110">When the walkthrough is completed you will have a BizTalk Server application that processes flat files and writes them out as XML for processing by a back-end system.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3620e-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="3620e-111">Prerequisites</span></span>  
 <span data-ttu-id="3620e-112">若要執行本範例，您必須已熟悉如何建立 BizTalk Server 專案和簽署組件，及使用「BizTalk Server 管理主控台」檢視應用程式和連接埠。</span><span class="sxs-lookup"><span data-stu-id="3620e-112">For this example you need to be comfortable with creating BizTalk Server projects, signing an assembly, and using the BizTalk Server Administration console to view applications and ports.</span></span> <span data-ttu-id="3620e-113">您也應該事先瞭解中提到的觀念[逐步解說： 部署基本 BizTalk 應用程式](../core/walkthrough-deploying-a-basic-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="3620e-113">You should also be comfortable with the ideas presented in [Walkthrough: Deploying a Basic BizTalk Application](../core/walkthrough-deploying-a-basic-biztalk-application.md).</span></span> <span data-ttu-id="3620e-114">對「一般檔案結構描述精靈」稍具基本認識的話亦有所助益，但並非必要條件。</span><span class="sxs-lookup"><span data-stu-id="3620e-114">Basic familiarity with the Flat File Schema Wizard is also helpful but not required.</span></span>  
  
## <a name="what-this-example-does"></a><span data-ttu-id="3620e-115">本範例的工作項目</span><span class="sxs-lookup"><span data-stu-id="3620e-115">What This Example Does</span></span>  
 <span data-ttu-id="3620e-116">本範例使用自訂管線和「一般檔案解譯器」元件來處理內送一般檔案訊息。</span><span class="sxs-lookup"><span data-stu-id="3620e-116">This example processes inbound flat file messages using a custom pipeline and the Flat File Disassembler component.</span></span> <span data-ttu-id="3620e-117">訊息將使用標頭、結尾和內文結構描述進行剖析，然後輸出至傳送位置再交由後端系統處理。</span><span class="sxs-lookup"><span data-stu-id="3620e-117">Messages are parsed using header, trailer, and body schemas and then written out to a send location for back-end processing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3620e-118">範例</span><span class="sxs-lookup"><span data-stu-id="3620e-118">Example</span></span>  
 <span data-ttu-id="3620e-119">若要建立範例，請依照以下各節所列的步驟進行。</span><span class="sxs-lookup"><span data-stu-id="3620e-119">To create the example, follow the steps outlined in the following sections.</span></span>  
  
### <a name="create-a-new-biztalk-project"></a><span data-ttu-id="3620e-120">建立新的 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="3620e-120">Create a New BizTalk Project</span></span>  
 <span data-ttu-id="3620e-121">建置方案前，您必須建立 BizTalk 專案、確定其具備強式名稱，並為其指定應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="3620e-121">Before building a solution you need to create a BizTalk project, ensure that it is strongly named, and assign it an application name.</span></span> <span data-ttu-id="3620e-122">指定應用程式名稱可避免 BizTalk Server 將方案部署至預設的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3620e-122">Assigning an application name prevents BizTalk Server from deploying the solution into the default BizTalk application.</span></span>  
  
1.  <span data-ttu-id="3620e-123">使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 建立新的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="3620e-123">Use [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to create a new BizTalk project.</span></span> <span data-ttu-id="3620e-124">呼叫專案 **FFDisassemblerWalkthrough**。</span><span class="sxs-lookup"><span data-stu-id="3620e-124">Call the project **FFDisassemblerWalkthrough**.</span></span>  
  
2.  <span data-ttu-id="3620e-125">產生金鑰檔並將其指派給專案。</span><span class="sxs-lookup"><span data-stu-id="3620e-125">Generate a key file and assign it to the project.</span></span> <span data-ttu-id="3620e-126">如需這項工作的詳細資訊，請參閱 [專案設計工具、 簽署頁](http://go.microsoft.com/fwlink/?LinkId=125876)。</span><span class="sxs-lookup"><span data-stu-id="3620e-126">For more information about this task, see [Signing Page, Project Designer](http://go.microsoft.com/fwlink/?LinkId=125876).</span></span>  
  
3.  <span data-ttu-id="3620e-127">在 專案部署屬性，將 **應用程式名稱** 至 「 FlatFileExample 」 及 「 **重新啟動主控件執行個體** 到 `True`。</span><span class="sxs-lookup"><span data-stu-id="3620e-127">In the deployment properties for the project, set **Application Name** to “FlatFileExample” and set **Restart Host Instances** to `True`.</span></span> <span data-ttu-id="3620e-128">設定此旗標係指示主控件清除組件所有已快取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3620e-128">Setting this flag tells the host to clear any cached instances of the assembly.</span></span>  
  
### <a name="create-the-sample-data-file"></a><span data-ttu-id="3620e-129">建立範例資料檔案</span><span class="sxs-lookup"><span data-stu-id="3620e-129">Create the Sample Data File</span></span>  
<span data-ttu-id="3620e-130">若要產生結構描述，您必須先建立測試檔案。</span><span class="sxs-lookup"><span data-stu-id="3620e-130">Before generating schemas, you need to create a test file.</span></span>   
  
1.  <span data-ttu-id="3620e-131">啟動「記事本」或其他文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="3620e-131">Start Notepad or another text editor.</span></span>  
  
2.  <span data-ttu-id="3620e-132">建立範例測試檔案。</span><span class="sxs-lookup"><span data-stu-id="3620e-132">Create a sample test file.</span></span> <span data-ttu-id="3620e-133">此檔案包含標頭指出回報錯誤的位置，結尾指出該批次的批次 ID，且內文含有一或多筆錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="3620e-133">The file consists of a header indicating the location reporting the error(s), a trailer with a batch ID for this batch, and a body consisting of one or more error records.</span></span> <span data-ttu-id="3620e-134">檔案的格式如下：</span><span class="sxs-lookup"><span data-stu-id="3620e-134">The format of the file is as follows:</span></span>  
  
    ```  
    Location  
    ERRORid|type|priority|description|errorDateTime  
    …additional error records   
    BatchID  
    ```  
  
    <span data-ttu-id="3620e-135">錯誤記錄是加上 「 錯誤 」 的文字，以分隔"&#124;"字元 （有別於位置）。</span><span class="sxs-lookup"><span data-stu-id="3620e-135">The ERROR record is tagged with the text “ERROR” and delimited with the “&#124;” character (versus positional).</span></span> <span data-ttu-id="3620e-136">ERROR 記錄的資料項目如下表所述。</span><span class="sxs-lookup"><span data-stu-id="3620e-136">The data elements of the ERROR record are described in the following table.</span></span>  
  
    |<span data-ttu-id="3620e-137">元素</span><span class="sxs-lookup"><span data-stu-id="3620e-137">Element</span></span>|<span data-ttu-id="3620e-138">資料類型</span><span class="sxs-lookup"><span data-stu-id="3620e-138">Data type</span></span>|<span data-ttu-id="3620e-139">Description</span><span class="sxs-lookup"><span data-stu-id="3620e-139">Description</span></span>|  
    |---|---|---|  
    |<span data-ttu-id="3620e-140">ID</span><span class="sxs-lookup"><span data-stu-id="3620e-140">ID</span></span>|<span data-ttu-id="3620e-141">integer</span><span class="sxs-lookup"><span data-stu-id="3620e-141">integer</span></span>|<span data-ttu-id="3620e-142">此錯誤的 ID。</span><span class="sxs-lookup"><span data-stu-id="3620e-142">ID for this error.</span></span>|  
    |<span data-ttu-id="3620e-143">型別</span><span class="sxs-lookup"><span data-stu-id="3620e-143">Type</span></span>|<span data-ttu-id="3620e-144">integer</span><span class="sxs-lookup"><span data-stu-id="3620e-144">integer</span></span>|<span data-ttu-id="3620e-145">錯誤的類型。</span><span class="sxs-lookup"><span data-stu-id="3620e-145">Type of error.</span></span>|  
    |<span data-ttu-id="3620e-146">優先權</span><span class="sxs-lookup"><span data-stu-id="3620e-146">Priority</span></span>|<span data-ttu-id="3620e-147">string</span><span class="sxs-lookup"><span data-stu-id="3620e-147">string</span></span>|<span data-ttu-id="3620e-148">優先順序指標：「低」、「中」或「高」。</span><span class="sxs-lookup"><span data-stu-id="3620e-148">Priority indicator: Low, Medium, or High.</span></span>|  
    |<span data-ttu-id="3620e-149">Description</span><span class="sxs-lookup"><span data-stu-id="3620e-149">Description</span></span>|<span data-ttu-id="3620e-150">string</span><span class="sxs-lookup"><span data-stu-id="3620e-150">string</span></span>|<span data-ttu-id="3620e-151">錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="3620e-151">Description of the error.</span></span>|  
    |<span data-ttu-id="3620e-152">錯誤日期時間</span><span class="sxs-lookup"><span data-stu-id="3620e-152">ErrorDateTime</span></span>|<span data-ttu-id="3620e-153">DateTime</span><span class="sxs-lookup"><span data-stu-id="3620e-153">DateTime</span></span>|<span data-ttu-id="3620e-154">發生錯誤的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="3620e-154">Date and time that the error occurred.</span></span>|  
  
    <span data-ttu-id="3620e-155">檔案中可能有一筆或多筆 ERROR 記錄。</span><span class="sxs-lookup"><span data-stu-id="3620e-155">The file can have one or more ERROR records.</span></span>  
  
     <span data-ttu-id="3620e-156">**-- OR --  **</span><span class="sxs-lookup"><span data-stu-id="3620e-156">**-- OR --  **</span></span>
  
     <span data-ttu-id="3620e-157">下列範例將資料複製到新的檔案。</span><span class="sxs-lookup"><span data-stu-id="3620e-157">Copy the following sample data into the new file.</span></span> <span data-ttu-id="3620e-158">最後一行包含尾端換行符號：</span><span class="sxs-lookup"><span data-stu-id="3620e-158">The last line contains a trailing linefeed:</span></span>
  
    ```  
    East Coast Facility  
    ERROR102|0|High|Sprocket query fails.|1999-05-31T13:20:00.000-05:00  
    ERROR16502|2|Low|Time threshold exceeded.|1999-05-31T13:20:00.000-05:00  
    8675309  
  
    ```  
  
3.  <span data-ttu-id="3620e-159">將新的範例檔案儲存到專案目錄中。</span><span class="sxs-lookup"><span data-stu-id="3620e-159">Save the new sample file in the project directory.</span></span> <span data-ttu-id="3620e-160">請使用描述性名稱如 "ErrorFile.txt" 以方便找到檔案。</span><span class="sxs-lookup"><span data-stu-id="3620e-160">Use a descriptive name like "ErrorFile.txt" so it can be located easily.</span></span>  
  
### <a name="create-and-test-the-header-trailer-and-body-schemas"></a><span data-ttu-id="3620e-161">建立並測試標頭、結尾和內文結構描述</span><span class="sxs-lookup"><span data-stu-id="3620e-161">Create and Test the Header, Trailer, and Body Schemas</span></span>  
 <span data-ttu-id="3620e-162">建立範例資料檔案後，下一步驟就是建立標頭、結尾和內文結構描述。</span><span class="sxs-lookup"><span data-stu-id="3620e-162">After the sample data file is created, the next step is to create the header, trailer, and body schemas.</span></span> <span data-ttu-id="3620e-163">這些結構描述將供「一般檔案解譯器」接收管線元件用來處理接收的訊息。</span><span class="sxs-lookup"><span data-stu-id="3620e-163">These schemas are used with the Flat File Disassembler receive pipeline component to process received messages.</span></span>  
  
##### <a name="use-the-flat-file-schema-wizard-to-create-the-header-schema"></a><span data-ttu-id="3620e-164">使用一般檔案結構描述精靈建立標頭結構描述</span><span class="sxs-lookup"><span data-stu-id="3620e-164">Use the Flat File Schema Wizard to create the header schema</span></span>  
  
1.  <span data-ttu-id="3620e-165">在專案中新增結構描述。</span><span class="sxs-lookup"><span data-stu-id="3620e-165">Add a new schema to the project.</span></span> <span data-ttu-id="3620e-166">在 方案總管 中，以滑鼠右鍵按一下 **FFDisassemblerWalkthrough**, ，指向  **新增**, ，然後按一下  **新項目**。</span><span class="sxs-lookup"><span data-stu-id="3620e-166">In Solution Explorer, right-click **FFDisassemblerWalkthrough**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="3620e-167">在 **加入新項目** 對話方塊中，按一下  **結構描述檔案** ，然後選取 **一般檔案結構描述精靈**。</span><span class="sxs-lookup"><span data-stu-id="3620e-167">In the **Add New Item** dialog box, click **Schema Files** and select **Flat File Schema Wizard**.</span></span> <span data-ttu-id="3620e-168">將新的結構描述"命名為 Header.xsd"，再按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="3620e-168">Name the new schema "Header.xsd" and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="3620e-169">在 **歡迎使用 BizTalk 一般檔案結構描述精靈** 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="3620e-169">On the **Welcome to the BizTalk Flat File Schema Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="3620e-170">在 **一般檔案結構描述資訊** 頁面上，按一下 **瀏覽** 並找出先前建立的範例資料檔案。</span><span class="sxs-lookup"><span data-stu-id="3620e-170">On the **Flat File Schema Information** page, click **Browse** and locate the sample data file created earlier.</span></span> <span data-ttu-id="3620e-171">變更 **記錄名稱** 「 標頭 」，確認字碼頁，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="3620e-171">Change the **Record Name** to "Header", verify the code page, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3620e-172">如果範例檔案儲存成 Unicode 格式，字碼頁即為 Little-Endian-UTF16 (1200)。</span><span class="sxs-lookup"><span data-stu-id="3620e-172">If you saved the sample file in Unicode format the code page will be Little-Endian-UTF16 (1200).</span></span> <span data-ttu-id="3620e-173">這對本範例不會造成不良影響。</span><span class="sxs-lookup"><span data-stu-id="3620e-173">This will not adversely affect the example.</span></span>  
  
5.  <span data-ttu-id="3620e-174">接著選取文件資料。</span><span class="sxs-lookup"><span data-stu-id="3620e-174">Next select the document data.</span></span> <span data-ttu-id="3620e-175">在 **選取文件資料** 頁面上，反白顯示的第一行的資料，包括新行字元 {CR} 和 {LF} 所示︰</span><span class="sxs-lookup"><span data-stu-id="3620e-175">On the **Select Document Data** page, highlight the first line of data including the new-line characters {CR} and {LF} as shown:</span></span>  
  
     <span data-ttu-id="3620e-176">![選取為標頭結構描述資料](../core/media/ffwiz-header-select-document-data.gif "ffwiz_header_select_document_data")</span><span class="sxs-lookup"><span data-stu-id="3620e-176">![Data selected for header schema](../core/media/ffwiz-header-select-document-data.gif "ffwiz_header_select_document_data")</span></span>  
  
     <span data-ttu-id="3620e-177">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="3620e-177">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="3620e-178">在 **選取記錄格式** 頁面上，按一下 **下一步** 接受預設值。</span><span class="sxs-lookup"><span data-stu-id="3620e-178">On the **Select Record Format** page, click **Next** to accept the default.</span></span> <span data-ttu-id="3620e-179">可接受預設值「依分隔符號」是因為資料檔案並未使用相對位置。</span><span class="sxs-lookup"><span data-stu-id="3620e-179">You can accept the default "by delimiter symbol" because the data file does not use relative position.</span></span>  
  
7.  <span data-ttu-id="3620e-180">在 **分隔記錄** 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="3620e-180">On the **Delimited Record** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="3620e-181">接著指定子項目。</span><span class="sxs-lookup"><span data-stu-id="3620e-181">Now you specify child elements.</span></span> <span data-ttu-id="3620e-182">標頭含有一個項目，名為 "Location"：</span><span class="sxs-lookup"><span data-stu-id="3620e-182">The header contains one element named "Location":</span></span>  
  
     <span data-ttu-id="3620e-183">![標頭定義的位置節點](../core/media/ffwiz-header-child-elements.gif "ffwiz_header_child_elements")</span><span class="sxs-lookup"><span data-stu-id="3620e-183">![Location node defined for header](../core/media/ffwiz-header-child-elements.gif "ffwiz_header_child_elements")</span></span>  
  
     <span data-ttu-id="3620e-184">按 **[下一步]** ，繼續進行。</span><span class="sxs-lookup"><span data-stu-id="3620e-184">Click **Next** to continue.</span></span>  
  
9. <span data-ttu-id="3620e-185">在 **結構描述檢視** 頁面上，確認結構描述。</span><span class="sxs-lookup"><span data-stu-id="3620e-185">On the **Schema View** page, verify the schema.</span></span>  
  
     <span data-ttu-id="3620e-186">![已完成的結構描述檢視顯示標頭結構描述](../core/media/ffwiz-header-schema-view.gif "ffwiz_header_schema_view")</span><span class="sxs-lookup"><span data-stu-id="3620e-186">![Schema view showing completed Header schema](../core/media/ffwiz-header-schema-view.gif "ffwiz_header_schema_view")</span></span>  
  
     <span data-ttu-id="3620e-187">當您滿意，請按一下  **完成** 來完成精靈。</span><span class="sxs-lookup"><span data-stu-id="3620e-187">When you are satisfied, click **Finish** to complete the wizard.</span></span>  
  
10. <span data-ttu-id="3620e-188">按一下**\<結構描述\>**標頭結構描述 窗格中的節點。</span><span class="sxs-lookup"><span data-stu-id="3620e-188">Click the **\<Schema\>** node in the Header schema pane.</span></span> <span data-ttu-id="3620e-189">在 [屬性] 窗格中，變更 **Element FormDefault** 至 **Qualified**。</span><span class="sxs-lookup"><span data-stu-id="3620e-189">In the Properties pane, change **Element FormDefault** to **Qualified**.</span></span> <span data-ttu-id="3620e-190">這表示區域宣告項目必須由執行個體文件中的目標命名空間限定。</span><span class="sxs-lookup"><span data-stu-id="3620e-190">This indicates that locally declared elements must be qualified by the target namespace in an instance document.</span></span>  
  
##### <a name="use-the-flat-file-schema-wizard-to-create-the-trailer-schema"></a><span data-ttu-id="3620e-191">使用一般檔案結構描述精靈建立結尾結構描述</span><span class="sxs-lookup"><span data-stu-id="3620e-191">Use the Flat File Schema Wizard to create the trailer schema</span></span>  
  
1.  <span data-ttu-id="3620e-192">在專案中新增結構描述。</span><span class="sxs-lookup"><span data-stu-id="3620e-192">Add a new schema to the project.</span></span> <span data-ttu-id="3620e-193">在 方案總管 中，以滑鼠右鍵按一下 **FFDisassemblerWalkthrough**, ，指向  **新增** , ，然後按一下  **新項目**。</span><span class="sxs-lookup"><span data-stu-id="3620e-193">In Solution Explorer, right-click **FFDisassemblerWalkthrough**, point to **Add** , and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="3620e-194">在 **加入新項目** 對話方塊中，按一下  **結構描述檔案** ，然後選取 **一般檔案結構描述精靈**。</span><span class="sxs-lookup"><span data-stu-id="3620e-194">In the **Add New Item** dialog box, click **Schema Files** and select **Flat File Schema Wizard**.</span></span> <span data-ttu-id="3620e-195">將新的結構描述"命名為 Trailer.xsd"，再按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="3620e-195">Name the new schema "Trailer.xsd" and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="3620e-196">在 **歡迎使用 BizTalk 一般檔案結構描述精靈** 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="3620e-196">On the **Welcome to the BizTalk Flat File Schema Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="3620e-197">在 **一般檔案結構描述資訊** 頁面上，按一下 **瀏覽** 並找出先前建立的範例資料檔案。</span><span class="sxs-lookup"><span data-stu-id="3620e-197">On the **Flat File Schema Information** page, click **Browse** and locate the sample data file created earlier.</span></span> <span data-ttu-id="3620e-198">變更 **記錄名稱** "Trailer"，以確認字碼頁，然後再按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="3620e-198">Change the **Record Name** to "Trailer", verify the code page, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3620e-199">如果範例檔案儲存成 Unicode 格式，字碼頁即為 Little-Endian-UTF16 (1200)。</span><span class="sxs-lookup"><span data-stu-id="3620e-199">If you saved the sample file in Unicode format the code page will be Little-Endian-UTF16 (1200).</span></span> <span data-ttu-id="3620e-200">這對本範例不會造成不良影響。</span><span class="sxs-lookup"><span data-stu-id="3620e-200">This will not adversely affect the example.</span></span>  
  
5.  <span data-ttu-id="3620e-201">接著選取文件資料。</span><span class="sxs-lookup"><span data-stu-id="3620e-201">Next select the document data.</span></span> <span data-ttu-id="3620e-202">在 **選取文件資料** 頁面上，反白顯示的最後一行的資料，包括新行字元 {CR} 和 {LF} 所示︰</span><span class="sxs-lookup"><span data-stu-id="3620e-202">On the **Select Document Data** page, highlight the last line of data including the new-line characters {CR} and {LF} as shown:</span></span>  
  
     <span data-ttu-id="3620e-203">![選取為結尾結構描述資料](../core/media/ffwiz-trailer-select-document-data.gif "ffwiz_trailer_select_document_data")</span><span class="sxs-lookup"><span data-stu-id="3620e-203">![Data selected for trailer schema](../core/media/ffwiz-trailer-select-document-data.gif "ffwiz_trailer_select_document_data")</span></span>  
  
     <span data-ttu-id="3620e-204">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="3620e-204">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="3620e-205">在 **選取記錄格式** 頁面上，按一下 **下一步** 接受預設值。</span><span class="sxs-lookup"><span data-stu-id="3620e-205">On the **Select Record Format** page, click **Next** to accept the default.</span></span> <span data-ttu-id="3620e-206">可接受預設值「依分隔符號」是因為資料檔案並未使用相對位置。</span><span class="sxs-lookup"><span data-stu-id="3620e-206">You can accept the default "by delimiter symbol" because the data file does not use relative position.</span></span>  
  
7.  <span data-ttu-id="3620e-207">在 **分隔記錄** 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="3620e-207">On the **Delimited Record** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="3620e-208">接著指定子項目。</span><span class="sxs-lookup"><span data-stu-id="3620e-208">Now you specify child elements.</span></span> <span data-ttu-id="3620e-209">結尾含有一個項目，名為 "BatchID"：</span><span class="sxs-lookup"><span data-stu-id="3620e-209">The header contains one element named "BatchID":</span></span>  
  
     <span data-ttu-id="3620e-210">![為結尾定義的位置節點](../core/media/ffwiz-trailer-child-elements.gif "ffwiz_trailer_child_elements")</span><span class="sxs-lookup"><span data-stu-id="3620e-210">![Location node defined for trailer](../core/media/ffwiz-trailer-child-elements.gif "ffwiz_trailer_child_elements")</span></span>  
  
     <span data-ttu-id="3620e-211">按 **[下一步]** ，繼續進行。</span><span class="sxs-lookup"><span data-stu-id="3620e-211">Click **Next** to continue.</span></span>  
  
9. <span data-ttu-id="3620e-212">在 **結構描述檢視** 頁面上，確認結構描述。</span><span class="sxs-lookup"><span data-stu-id="3620e-212">On the **Schema View** page, verify the schema.</span></span>  
  
     <span data-ttu-id="3620e-213">![結構描述檢視顯示完成結尾結構描述](../core/media/ffwiz-trailer-schema-view.gif "ffwiz_trailer_schema_view")</span><span class="sxs-lookup"><span data-stu-id="3620e-213">![Schema view showing completed Trailer schema](../core/media/ffwiz-trailer-schema-view.gif "ffwiz_trailer_schema_view")</span></span>  
  
     <span data-ttu-id="3620e-214">當您滿意，請按一下  **完成** 來完成精靈。</span><span class="sxs-lookup"><span data-stu-id="3620e-214">When you are satisfied, click **Finish** to complete the wizard.</span></span>  
  
10. <span data-ttu-id="3620e-215">按一下**\<結構描述\>**結尾結構描述 窗格中的節點。</span><span class="sxs-lookup"><span data-stu-id="3620e-215">Click the **\<Schema\>** node in the Trailer schema pane.</span></span> <span data-ttu-id="3620e-216">在 [屬性] 窗格中，變更 **elementFormDefault** 至 **Qualified**。</span><span class="sxs-lookup"><span data-stu-id="3620e-216">In the Properties pane, change **elementFormDefault** to **Qualified**.</span></span> <span data-ttu-id="3620e-217">這表示區域宣告項目必須由執行個體文件中的目標命名空間限定。</span><span class="sxs-lookup"><span data-stu-id="3620e-217">This indicates that locally declared elements must be qualified by the target namespace in an instance document.</span></span>  
  
##### <a name="use-the-flat-file-schema-wizard-to-create-the-body-schema"></a><span data-ttu-id="3620e-218">使用一般檔案結構描述精靈建立內文結構描述</span><span class="sxs-lookup"><span data-stu-id="3620e-218">Use the Flat File Schema Wizard to create the body schema</span></span>  
  
1.  <span data-ttu-id="3620e-219">在專案中新增結構描述。</span><span class="sxs-lookup"><span data-stu-id="3620e-219">Add a new schema to the project.</span></span> <span data-ttu-id="3620e-220">在 方案總管 中，以滑鼠右鍵按一下 **FFDisassemblerWalkthrough**, ，指向  **新增**, ，然後按一下  **新項目**。</span><span class="sxs-lookup"><span data-stu-id="3620e-220">In Solution Explorer, right-click **FFDisassemblerWalkthrough**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="3620e-221">在 **加入新項目** 對話方塊中，按一下  **結構描述檔案** ，然後選取 **一般檔案結構描述精靈**。</span><span class="sxs-lookup"><span data-stu-id="3620e-221">In the **Add New Item** dialog box, click **Schema Files** and select **Flat File Schema Wizard**.</span></span> <span data-ttu-id="3620e-222">將新的結構描述"命名為 Body.xsd"，再按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="3620e-222">Name the new schema "Body.xsd" and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="3620e-223">在 **歡迎使用 BizTalk 一般檔案結構描述精靈** 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="3620e-223">On the **Welcome to the BizTalk Flat File Schema Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="3620e-224">在 **一般檔案結構描述資訊** 頁面上，按一下 **瀏覽** 並找出先前建立的範例資料檔案。</span><span class="sxs-lookup"><span data-stu-id="3620e-224">On the **Flat File Schema Information** page, click **Browse** and locate the sample data file created earlier.</span></span> <span data-ttu-id="3620e-225">變更 **記錄名稱** 為"Body"，確認字碼頁，然後再按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="3620e-225">Change the **Record Name** to "Body", verify the code page, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3620e-226">如果範例檔案儲存成 Unicode 格式，字碼頁即為 Little-Endian-UTF16 (1200)。</span><span class="sxs-lookup"><span data-stu-id="3620e-226">If you saved the sample file in Unicode format the code page will be Little-Endian-UTF16 (1200).</span></span> <span data-ttu-id="3620e-227">這對本範例不會造成不良影響。</span><span class="sxs-lookup"><span data-stu-id="3620e-227">This will not adversely affect the example.</span></span>  
  
5.  <span data-ttu-id="3620e-228">接著選取文件資料。</span><span class="sxs-lookup"><span data-stu-id="3620e-228">Next select the document data.</span></span> <span data-ttu-id="3620e-229">在 **選取文件資料** 頁面上，反白顯示兩到三次的資料行含有新行字元 {CR} 和 {LF} 所示︰</span><span class="sxs-lookup"><span data-stu-id="3620e-229">On the **Select Document Data** page, highlight lines two and three of data including the new-line characters {CR} and {LF} as shown:</span></span>  
  
     <span data-ttu-id="3620e-230">![選取為內文結構描述資料](../core/media/ffwiz-body-select-document-data.gif "ffwiz_body_select_document_data")</span><span class="sxs-lookup"><span data-stu-id="3620e-230">![Data selected for body schema](../core/media/ffwiz-body-select-document-data.gif "ffwiz_body_select_document_data")</span></span>  
  
     <span data-ttu-id="3620e-231">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="3620e-231">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="3620e-232">在 **選取記錄格式** 頁面上，按一下 **下一步** 接受預設值。</span><span class="sxs-lookup"><span data-stu-id="3620e-232">On the **Select Record Format** page, click **Next** to accept the default.</span></span> <span data-ttu-id="3620e-233">可接受預設值「依分隔符號」是因為資料檔案並未使用相對位置。</span><span class="sxs-lookup"><span data-stu-id="3620e-233">You can accept the default "by delimiter symbol" because the data file does not use relative position.</span></span>  
  
7.  <span data-ttu-id="3620e-234">在 **分隔記錄** 頁面上，選取 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="3620e-234">On the **Delimited Record** page, select **Next**.</span></span>  
  
8.  <span data-ttu-id="3620e-235">接著定義子項目。</span><span class="sxs-lookup"><span data-stu-id="3620e-235">Next define the child elements.</span></span> <span data-ttu-id="3620e-236">變更 **Body_Child1** 至 **錯誤**並將其項目類型設定為 **重複記錄**。</span><span class="sxs-lookup"><span data-stu-id="3620e-236">Change **Body_Child1** to **Error**and set its element type to **Repeating record**.</span></span> <span data-ttu-id="3620e-237">設定 **Body_Child2** 項目記錄類型至 **忽略**。</span><span class="sxs-lookup"><span data-stu-id="3620e-237">Set the **Body_Child2** element record type to **Ignore**.</span></span>  
  
9. <span data-ttu-id="3620e-238">在 **結構描述檢視** 頁面上，按一下 **下一步** 定義 Error 記錄的子項目。</span><span class="sxs-lookup"><span data-stu-id="3620e-238">On the **Schema View** page, click **Next** to define the child elements of the Error record.</span></span>  
  
10. <span data-ttu-id="3620e-239">在 **選取文件資料** 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="3620e-239">On the **Select Document Data** page, click **Next**.</span></span> <span data-ttu-id="3620e-240">精靈會正確選擇記錄定義的資料。</span><span class="sxs-lookup"><span data-stu-id="3620e-240">The wizard chooses the record-defining data correctly.</span></span>  
  
11. <span data-ttu-id="3620e-241">在 **選取記錄格式** 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="3620e-241">On the **Select Record Format** page, click **Next**.</span></span> <span data-ttu-id="3620e-242">資料會以分隔符號進行格式化。</span><span class="sxs-lookup"><span data-stu-id="3620e-242">The data is formatted by delimiter symbol.</span></span>  
  
12. <span data-ttu-id="3620e-243">在 **分隔記錄** 頁面上，選取 **&#124;** 的 **子分隔符號**。</span><span class="sxs-lookup"><span data-stu-id="3620e-243">On the **Delimited Record** page, select **&#124;** for the **Child delimiter**.</span></span> <span data-ttu-id="3620e-244">接下來，選取 **記錄具有標記識別項** 核取方塊，然後輸入 **錯誤** 的標記值。</span><span class="sxs-lookup"><span data-stu-id="3620e-244">Next, select the **Record has a tag identifier** check box and type **ERROR** for the tag value.</span></span>  
  
     <span data-ttu-id="3620e-245">![設定分隔記錄具有標記識別項](../core/media/ffwiz-bodyerror-delimited-record.gif "ffwiz_bodyerror_delimited_record")</span><span class="sxs-lookup"><span data-stu-id="3620e-245">![Configuring delimited record with tag identifier](../core/media/ffwiz-bodyerror-delimited-record.gif "ffwiz_bodyerror_delimited_record")</span></span>  
  
     <span data-ttu-id="3620e-246">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="3620e-246">Click **Next**.</span></span>  
  
13. <span data-ttu-id="3620e-247">接著定義 Error 記錄的子項目。</span><span class="sxs-lookup"><span data-stu-id="3620e-247">Now define the child elements of the Error record.</span></span>  
  
     <span data-ttu-id="3620e-248">![定義包含五個元素的錯誤記錄](../core/media/ffwiz-bodyerror-child-elements.gif "ffwiz_bodyerror_child_elements")</span><span class="sxs-lookup"><span data-stu-id="3620e-248">![Error record defined with five elements](../core/media/ffwiz-bodyerror-child-elements.gif "ffwiz_bodyerror_child_elements")</span></span>  
  
     <span data-ttu-id="3620e-249">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="3620e-249">Click **Next**.</span></span>  
  
14. <span data-ttu-id="3620e-250">在 **結構描述檢視** 頁面上，確認結構描述。</span><span class="sxs-lookup"><span data-stu-id="3620e-250">On the **Schema View** page, verify the schema.</span></span>  
  
     <span data-ttu-id="3620e-251">![結構描述檢視顯示已完成的內文結構描述](../core/media/ffwiz-bodyerror-schema-view.gif "ffwiz_bodyerror_schema_view")</span><span class="sxs-lookup"><span data-stu-id="3620e-251">![Schema view showing completed Body schema](../core/media/ffwiz-bodyerror-schema-view.gif "ffwiz_bodyerror_schema_view")</span></span>  
  
     <span data-ttu-id="3620e-252">如果您所做的任何錯誤，請按一下 **回** 並進行必要的修正。</span><span class="sxs-lookup"><span data-stu-id="3620e-252">If you have made any mistakes, click **Back** and make the necessary corrections.</span></span> <span data-ttu-id="3620e-253">當您滿意，請按一下  **完成** 來完成精靈。</span><span class="sxs-lookup"><span data-stu-id="3620e-253">When you are satisfied, click **Finish** to complete the wizard.</span></span>  
  
15. <span data-ttu-id="3620e-254">按一下**\<結構描述\>** Body 結構描述窗格中的節點。</span><span class="sxs-lookup"><span data-stu-id="3620e-254">Click the **\<Schema\>** node in the Body schema pane.</span></span> <span data-ttu-id="3620e-255">在 [屬性] 窗格中，變更 **Element FormDefault** 至 **Qualified**。</span><span class="sxs-lookup"><span data-stu-id="3620e-255">In the Properties pane, change **Element FormDefault** to **Qualified**.</span></span> <span data-ttu-id="3620e-256">這表示區域宣告項目必須由執行個體文件中的目標命名空間限定。</span><span class="sxs-lookup"><span data-stu-id="3620e-256">This indicates that locally declared elements must be qualified by the target namespace in an instance document.</span></span>  
  
16. <span data-ttu-id="3620e-257">按一下**\<錯誤\>** Body 結構描述窗格上的節點。</span><span class="sxs-lookup"><span data-stu-id="3620e-257">Click the **\<Error\>** node on the Body schema pane.</span></span> <span data-ttu-id="3620e-258">在 [屬性] 窗格中，變更 **Max Occurs** 至 **1**。</span><span class="sxs-lookup"><span data-stu-id="3620e-258">In the Properties pane, change **Max Occurs** to **1**.</span></span> <span data-ttu-id="3620e-259">這可讓「一般檔案解譯器」將每項錯誤分割為個別的訊息。</span><span class="sxs-lookup"><span data-stu-id="3620e-259">This causes the Flat File Disassembler to split each error into its own message.</span></span>  
  
##### <a name="test-the-schemas-using-ffdasm"></a><span data-ttu-id="3620e-260">測試使用 FFDasm 的結構描述</span><span class="sxs-lookup"><span data-stu-id="3620e-260">Test the schemas using FFDasm</span></span>  
  
1.  <span data-ttu-id="3620e-261">開啟命令提示字元，再將目錄變更為您的專案目錄。</span><span class="sxs-lookup"><span data-stu-id="3620e-261">Open a command prompt and change the directory to your project directory.</span></span>  
  
2.  <span data-ttu-id="3620e-262">從命令提示字元執行 FFDasm.exe，如下所示。</span><span class="sxs-lookup"><span data-stu-id="3620e-262">From the command prompt, run FFDasm.exe as shown below.</span></span>  
  
    ```  
    <Samples Path>\SDK\Utilities\PipelineTools\FFDasm ErrorFile.txt  -hs header.xsd -bs body.xsd -ts Trailer.xsd  
    ```  
  
     <span data-ttu-id="3620e-263">這和其他管線工具的位置的詳細資訊，請參閱[管線工具](../core/pipeline-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="3620e-263">For information about the location of this and other pipeline tools, see [Pipeline Tools](../core/pipeline-tools.md).</span></span>  
  
3.  <span data-ttu-id="3620e-264">FFDasm.exe 會產生兩個名為 {GUID}.xml 的輸出檔，分別代表測試檔案中的一筆 ERROR 記錄。</span><span class="sxs-lookup"><span data-stu-id="3620e-264">FFDasm.exe should produce two output files named {GUID}.xml, one for each ERROR record in the test file.</span></span> <span data-ttu-id="3620e-265">高優先順序的錯誤記錄看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="3620e-265">The high-priority error record looks like the following:</span></span>  
  
    ```  
    <Body xmlns="http://FFDisassemblerWalkthrough.Body">  
      <Error>  
        <ID>102</ID>  
        <Type>0</Type>  
        <Priority>High</Priority>  
        <Description>Sprocket query fails.</Description>  
        <DateTime>1999-05-31T13:20:00.000-05:00</DateTime>  
      </Error>  
    </Body>  
    ```  
  
### <a name="create-a-custom-receive-pipeline"></a><span data-ttu-id="3620e-266">建立自訂接收管線</span><span class="sxs-lookup"><span data-stu-id="3620e-266">Create a Custom Receive Pipeline</span></span>  
 <span data-ttu-id="3620e-267">如今一般檔案結構描述已經定義完成，您必須建立自訂管線以使用「一般檔案解譯器」元件。</span><span class="sxs-lookup"><span data-stu-id="3620e-267">Now that the flat file schemas are defined, you need to create a custom pipeline that uses the Flat File Disassembler component.</span></span> <span data-ttu-id="3620e-268">然後即可將「一般檔案解譯器」元件設定為使用標頭、內文和結尾結構描述來拆解訊息。</span><span class="sxs-lookup"><span data-stu-id="3620e-268">The Flat File Disassembler component can then be configured to use the header, body, and trailer schemas to break up messages.</span></span>    
 
1.  <span data-ttu-id="3620e-269">在專案中新增接收管線。</span><span class="sxs-lookup"><span data-stu-id="3620e-269">Add a new receive pipeline to the project.</span></span> <span data-ttu-id="3620e-270">在 方案總管 中，以滑鼠右鍵按一下 **FFDisassemblerWalkthrough** 專案，指向 **新增**, ，然後按一下  **新項目**。</span><span class="sxs-lookup"><span data-stu-id="3620e-270">In Solution Explorer, right-click the **FFDisassemblerWalkthrough** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="3620e-271">在 **加入新項目** ] 對話方塊中，指向 **管線檔案** 然後按一下 [ **接收管線**。</span><span class="sxs-lookup"><span data-stu-id="3620e-271">In the **Add New Item** dialog box, point to **Pipeline Files** and then click **Receive Pipeline**.</span></span> <span data-ttu-id="3620e-272">將新管線"命名為 FFReceivePipeline"，再按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="3620e-272">Name the new pipeline "FFReceivePipeline" and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="3620e-273">將「一般檔案解譯器」元件從 [工具箱] 窗格拖曳到「解譯」步驟以設定新管線。</span><span class="sxs-lookup"><span data-stu-id="3620e-273">Configure the new pipeline by dragging the Flat File Disassembler component from the Toolbox pane to the Disassemble step.</span></span>  
  
4.  <span data-ttu-id="3620e-274">在 [屬性] 窗格中，設定 **文件結構描述** 至 **FFDisassemblerWalkthrough.Body**, 、 **標頭結構描述** 至 **FFDisassemblerWalkthrough.Header** 和 **結尾結構描述** 至 **FFDisassemblerWalkthrough.Trailer**。</span><span class="sxs-lookup"><span data-stu-id="3620e-274">In the Properties pane, set the **Document schema** to **FFDisassemblerWalkthrough.Body**, the **Header schema** to **FFDisassemblerWalkthrough.Header** and the **Trailer schema** to **FFDisassemblerWalkthrough.Trailer**.</span></span>  
  
### <a name="deploy-the-application-and-configure-the-send-and-receive-ports"></a><span data-ttu-id="3620e-275">部署應用程式並設定傳送埠和接收埠</span><span class="sxs-lookup"><span data-stu-id="3620e-275">Deploy the Application and Configure the Send and Receive Ports</span></span>  
 <span data-ttu-id="3620e-276">建立結構描述和自訂接收管線後，您必須編譯並部署專案。</span><span class="sxs-lookup"><span data-stu-id="3620e-276">With the schemas and custom receive pipeline created, you need to compile and deploy the project.</span></span> <span data-ttu-id="3620e-277">一旦專案部署完成，即可使用「BizTalk Server 管理主控台」設定傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="3620e-277">After it is deployed, you can use the BizTalk Server Administration console to configure the send and receive ports.</span></span>  

##### <a name="deploy"></a><span data-ttu-id="3620e-278">部署</span><span class="sxs-lookup"><span data-stu-id="3620e-278">Deploy</span></span>  
1.  <span data-ttu-id="3620e-279">從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，專案上按一下滑鼠右鍵，然後按一下 部署方案**部署**。</span><span class="sxs-lookup"><span data-stu-id="3620e-279">From within [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], deploy the solution by right-clicking on the project and then clicking **Deploy**.</span></span>  
  
2.  <span data-ttu-id="3620e-280">使用 BizTalk Server 管理主控台中，展開 **應用程式** 群組，以確認 **FlatFileExample** 呈現為自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="3620e-280">Using the BizTalk Server Administration console, expand the **Applications** group to verify that **FlatFileExample** is present as a custom application.</span></span>  
  
##### <a name="configure-the-receive-port"></a><span data-ttu-id="3620e-281">設定接收埠</span><span class="sxs-lookup"><span data-stu-id="3620e-281">Configure the receive port</span></span>  
  
1.  <span data-ttu-id="3620e-282">使用 Windows 檔案總管底下建立名為"Receive" **FFDisassemblerWalkthrough** 專案目錄。</span><span class="sxs-lookup"><span data-stu-id="3620e-282">Use Windows Explorer to create a directory named "Receive" under the **FFDisassemblerWalkthrough** project directory.</span></span>  
  
2.  <span data-ttu-id="3620e-283">在 BizTalk Server 管理主控台中，展開 **FlatFileExample** 應用程式，以滑鼠右鍵按一下 **接收埠**, ，指向  **新增**, ，然後按一下  **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="3620e-283">In the BizTalk Server Administration console, expand the **FlatFileExample** application, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
3.  <span data-ttu-id="3620e-284">在 **接收埠屬性** 對話方塊方塊中，設定為"ReceiveError"的連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="3620e-284">In the **Receive Port Properties** dialog box, set the name of the port to "ReceiveError".</span></span>  
  
4.  <span data-ttu-id="3620e-285">按一下  **接收位置**, ，然後按一下  **新增** 新增接收位置。</span><span class="sxs-lookup"><span data-stu-id="3620e-285">Click **Receive Locations**, and then click **New** to add a receive location.</span></span> <span data-ttu-id="3620e-286">將新的接收位置命名為 "ReceiveErrorLocation"。</span><span class="sxs-lookup"><span data-stu-id="3620e-286">Name the new receive location "ReceiveErrorLocation".</span></span> <span data-ttu-id="3620e-287">設定 **接收管線** 至 **FFReceivePipeline**。</span><span class="sxs-lookup"><span data-stu-id="3620e-287">Set the **Receive Pipeline** to **FFReceivePipeline**.</span></span> <span data-ttu-id="3620e-288">如 **傳輸類型**, ，請選取 **檔案**, ，然後按一下  **設定**。</span><span class="sxs-lookup"><span data-stu-id="3620e-288">For **Transport Type**, select **FILE**, and then click **Configure**.</span></span> <span data-ttu-id="3620e-289">選取您建立，並接著設定的接收目錄 **檔案遮罩** 至 \*.txt。</span><span class="sxs-lookup"><span data-stu-id="3620e-289">Select the receive directory you created, and then set the **File mask** to \*.txt.</span></span>  
  
5.  <span data-ttu-id="3620e-290">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3620e-290">Click **OK**.</span></span> <span data-ttu-id="3620e-291">接收埠即設定完成。</span><span class="sxs-lookup"><span data-stu-id="3620e-291">Your receive port should now be configured.</span></span> <span data-ttu-id="3620e-292">按一下  **確定** 關閉。</span><span class="sxs-lookup"><span data-stu-id="3620e-292">Click **OK** to close.</span></span>  
  
##### <a name="configure-the-send-port"></a><span data-ttu-id="3620e-293">設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="3620e-293">Configure the send port</span></span>  
  
1.  <span data-ttu-id="3620e-294">使用 Windows 檔案總管底下建立名為 「 傳送 」 **FFDisassemblerWalkthrough** 專案目錄。</span><span class="sxs-lookup"><span data-stu-id="3620e-294">Use Windows Explorer to create a directory named "Send" under the **FFDisassemblerWalkthrough** project directory.</span></span>  
  
2.  <span data-ttu-id="3620e-295">在 BizTalk Server 管理主控台中，展開 **FlatFileExample** 應用程式，以滑鼠右鍵按一下 **傳送埠**, ，指向  **新增**, ，然後按一下  **靜態單向傳送埠 …**。</span><span class="sxs-lookup"><span data-stu-id="3620e-295">In the BizTalk Server Administration console, expand the **FlatFileExample** application, right-click **Send Ports**, point to **New**, and then click **Static One-Way  Send Port…**.</span></span>  
  
3.  <span data-ttu-id="3620e-296">在 **傳送埠屬性** 對話方塊方塊中，設定 「 傳送 」 的連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="3620e-296">In the **Send Port Properties** dialog box, set the name of the port to "Send".</span></span>  
  
4.  <span data-ttu-id="3620e-297">傳輸類型，請選取 **檔案**, ，然後按一下  **設定**。</span><span class="sxs-lookup"><span data-stu-id="3620e-297">For transport type, select **FILE**, and then click **Configure**.</span></span> <span data-ttu-id="3620e-298">將目的資料夾設定為剛才建立的傳送目錄。</span><span class="sxs-lookup"><span data-stu-id="3620e-298">Set the destination folder to the send directory you created earlier.</span></span>  
  
5.  <span data-ttu-id="3620e-299">接著設定篩選條件。</span><span class="sxs-lookup"><span data-stu-id="3620e-299">Now configure the filter.</span></span> <span data-ttu-id="3620e-300">按一下  **篩選** 並加入下列運算式︰</span><span class="sxs-lookup"><span data-stu-id="3620e-300">Click **Filters** and add one expression:</span></span>  
  
    -   <span data-ttu-id="3620e-301">BTS.MessageType == **http://FFDisassemblerWalkthrough.Body#Body**</span><span class="sxs-lookup"><span data-stu-id="3620e-301">BTS.MessageType == **http://FFDisassemblerWalkthrough.Body#Body**</span></span>  
  
6.  <span data-ttu-id="3620e-302">按一下  **確定** 完成傳送埠組態。</span><span class="sxs-lookup"><span data-stu-id="3620e-302">Click **OK** to complete the send port configuration.</span></span> <span data-ttu-id="3620e-303">傳送埠即設定完成。</span><span class="sxs-lookup"><span data-stu-id="3620e-303">Your send port should be configured.</span></span>  
  
### <a name="run-the-example"></a><span data-ttu-id="3620e-304">執行範例</span><span class="sxs-lookup"><span data-stu-id="3620e-304">Run the Example</span></span>  
 <span data-ttu-id="3620e-305">現在即可開始執行範例。</span><span class="sxs-lookup"><span data-stu-id="3620e-305">It is now time to run the example.</span></span> <span data-ttu-id="3620e-306">之後您可以使用 BizTalk Server 管理主控台來啟動應用程式，將測試檔案複製到接收位置，並觀察傳送位置中產生的結果。</span><span class="sxs-lookup"><span data-stu-id="3620e-306">After using the BizTalk Server Management console to start the application, copy the test files to the receive location and observe what is produced in the send location.</span></span>  
  
1.  <span data-ttu-id="3620e-307">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**FlatFileExample**應用程式，，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="3620e-307">In the BizTalk Server Administration console, right-click the **FlatFileExample** application, and then click **Start**.</span></span> <span data-ttu-id="3620e-308">此登錄和啟動傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="3620e-308">This enlists and starts the send and receive ports.</span></span>  
  
2.  <span data-ttu-id="3620e-309">將範例 Errorfile.txt 複本放到接收目錄中。</span><span class="sxs-lookup"><span data-stu-id="3620e-309">Drop the copy of the sample Errorfile.txt into the receive directory.</span></span> <span data-ttu-id="3620e-310">傳送目錄中應該就會產生兩個輸出檔。</span><span class="sxs-lookup"><span data-stu-id="3620e-310">Two output files should be written to the send directory.</span></span>  
  
