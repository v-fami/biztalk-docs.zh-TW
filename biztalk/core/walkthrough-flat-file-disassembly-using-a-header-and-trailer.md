---
title: 逐步解說： 使用標頭和結尾的一般檔案解譯 |Microsoft Docs
description: 使用 「 一般檔案結構描述精靈 」 來建立標頭結構描述、 結尾結構描述和內文結構描述，並再解譯 BizTalk Server 的一般檔案
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715af9cc-d718-483d-b593-64462aa5a58b
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a39361e4da6dec9acf023911466f07572a3de13
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983911"
---
# <a name="walkthrough-flat-file-disassembly-using-a-header-and-trailer"></a><span data-ttu-id="deea6-103">逐步解說：使用標頭和結尾進行一般檔案解譯</span><span class="sxs-lookup"><span data-stu-id="deea6-103">Walkthrough: Flat File Disassembly Using a Header and Trailer</span></span>

## <a name="overview"></a><span data-ttu-id="deea6-104">概觀</span><span class="sxs-lookup"><span data-stu-id="deea6-104">Overview</span></span>
<span data-ttu-id="deea6-105">此逐步解說示範如何使用由「一般檔案結構描述精靈」所建立的結構描述，對包含標頭、結尾及重複訊息內文的檔案進行一般檔案解譯。</span><span class="sxs-lookup"><span data-stu-id="deea6-105">This walkthrough demonstrates the use of schemas created by the Flat File Schema Wizard to perform flat file disassembly of a file containing a header, a trailer, and a repeating message body.</span></span> <span data-ttu-id="deea6-106">在此逐步解說中，您將開發部分虛構的錯誤追蹤系統，使其符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="deea6-106">In this walkthrough, you develop part of a fictitious error-tracking system that meets the following requirements:</span></span>  
  
- <span data-ttu-id="deea6-107">錯誤訊息記錄到公司內各個不同的實體網站，再傳送至一個集中位置處理後放入各個後端系統。</span><span class="sxs-lookup"><span data-stu-id="deea6-107">Error messages are logged at various physical sites within the company and sent to a central location for processing into various back-end systems.</span></span>  
  
- <span data-ttu-id="deea6-108">會以一般檔案格式寫入錯誤訊息，其標頭指出位置，內文含有一或多個錯誤訊息，且結尾指出批次編號。</span><span class="sxs-lookup"><span data-stu-id="deea6-108">Error messages are written into a flat file format that contains a header indicating location, a body containing one or more error messages, and a trailer indicating the batch number.</span></span>  
  
- <span data-ttu-id="deea6-109">如果訊息中沒有標頭、內文和結尾，則視同無效訊息。</span><span class="sxs-lookup"><span data-stu-id="deea6-109">Messages are considered invalid if they do not have a header, body, and trailer.</span></span>  
  
  <span data-ttu-id="deea6-110">完成此逐步解說後，將會建立 BizTalk Server 應用程式用於處理一般檔案，並將其輸出為 XML 以供後端系統處理。</span><span class="sxs-lookup"><span data-stu-id="deea6-110">When the walkthrough is completed you will have a BizTalk Server application that processes flat files and writes them out as XML for processing by a back-end system.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="deea6-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="deea6-111">Prerequisites</span></span>  
 <span data-ttu-id="deea6-112">若要執行本範例，您必須已熟悉如何建立 BizTalk Server 專案和簽署組件，及使用「BizTalk Server 管理主控台」檢視應用程式和連接埠。</span><span class="sxs-lookup"><span data-stu-id="deea6-112">For this example you need to be comfortable with creating BizTalk Server projects, signing an assembly, and using the BizTalk Server Administration console to view applications and ports.</span></span> <span data-ttu-id="deea6-113">您也應該事先瞭解中提到的觀念[逐步解說： 部署基本 BizTalk 應用程式](../core/walkthrough-deploying-a-basic-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="deea6-113">You should also be comfortable with the ideas presented in [Walkthrough: Deploying a Basic BizTalk Application](../core/walkthrough-deploying-a-basic-biztalk-application.md).</span></span> <span data-ttu-id="deea6-114">對「一般檔案結構描述精靈」稍具基本認識的話亦有所助益，但並非必要條件。</span><span class="sxs-lookup"><span data-stu-id="deea6-114">Basic familiarity with the Flat File Schema Wizard is also helpful but not required.</span></span>  
  
## <a name="what-this-example-does"></a><span data-ttu-id="deea6-115">本範例的工作項目</span><span class="sxs-lookup"><span data-stu-id="deea6-115">What This Example Does</span></span>  
 <span data-ttu-id="deea6-116">本範例使用自訂管線和「一般檔案解譯器」元件來處理內送一般檔案訊息。</span><span class="sxs-lookup"><span data-stu-id="deea6-116">This example processes inbound flat file messages using a custom pipeline and the Flat File Disassembler component.</span></span> <span data-ttu-id="deea6-117">訊息將使用標頭、結尾和內文結構描述進行剖析，然後輸出至傳送位置再交由後端系統處理。</span><span class="sxs-lookup"><span data-stu-id="deea6-117">Messages are parsed using header, trailer, and body schemas and then written out to a send location for back-end processing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="deea6-118">範例</span><span class="sxs-lookup"><span data-stu-id="deea6-118">Example</span></span>  
 <span data-ttu-id="deea6-119">若要建立範例，請依照以下各節所列的步驟進行。</span><span class="sxs-lookup"><span data-stu-id="deea6-119">To create the example, follow the steps outlined in the following sections.</span></span>  
  
### <a name="create-a-new-biztalk-project"></a><span data-ttu-id="deea6-120">建立新的 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="deea6-120">Create a New BizTalk Project</span></span>  
 <span data-ttu-id="deea6-121">建置方案前，您必須建立 BizTalk 專案、確定其具備強式名稱，並為其指定應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="deea6-121">Before building a solution you need to create a BizTalk project, ensure that it is strongly named, and assign it an application name.</span></span> <span data-ttu-id="deea6-122">指定應用程式名稱可避免 BizTalk Server 將方案部署至預設的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="deea6-122">Assigning an application name prevents BizTalk Server from deploying the solution into the default BizTalk application.</span></span>  
  
1. <span data-ttu-id="deea6-123">使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 建立新的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="deea6-123">Use [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to create a new BizTalk project.</span></span> <span data-ttu-id="deea6-124">呼叫專案**FFDisassemblerWalkthrough**。</span><span class="sxs-lookup"><span data-stu-id="deea6-124">Call the project **FFDisassemblerWalkthrough**.</span></span>  
  
2. <span data-ttu-id="deea6-125">產生金鑰檔並將其指派給專案。</span><span class="sxs-lookup"><span data-stu-id="deea6-125">Generate a key file and assign it to the project.</span></span> <span data-ttu-id="deea6-126">如需有關這項工作的詳細資訊，請參閱 <<c0> [ 專案設計工具、 簽署頁](http://go.microsoft.com/fwlink/?LinkId=125876)。</span><span class="sxs-lookup"><span data-stu-id="deea6-126">For more information about this task, see [Signing Page, Project Designer](http://go.microsoft.com/fwlink/?LinkId=125876).</span></span>  
  
3. <span data-ttu-id="deea6-127">在 專案部署屬性，將**應用程式名稱**為"FlatFileExample 」，並將**重新啟動主控件執行個體**到`True`。</span><span class="sxs-lookup"><span data-stu-id="deea6-127">In the deployment properties for the project, set **Application Name** to “FlatFileExample” and set **Restart Host Instances** to `True`.</span></span> <span data-ttu-id="deea6-128">設定此旗標係指示主控件清除組件所有已快取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="deea6-128">Setting this flag tells the host to clear any cached instances of the assembly.</span></span>  
  
### <a name="create-the-sample-data-file"></a><span data-ttu-id="deea6-129">建立範例資料檔案</span><span class="sxs-lookup"><span data-stu-id="deea6-129">Create the Sample Data File</span></span>  
<span data-ttu-id="deea6-130">若要產生結構描述，您必須先建立測試檔案。</span><span class="sxs-lookup"><span data-stu-id="deea6-130">Before generating schemas, you need to create a test file.</span></span>   
  
1.  <span data-ttu-id="deea6-131">啟動「記事本」或其他文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="deea6-131">Start Notepad or another text editor.</span></span>  
  
2.  <span data-ttu-id="deea6-132">建立範例測試檔案。</span><span class="sxs-lookup"><span data-stu-id="deea6-132">Create a sample test file.</span></span> <span data-ttu-id="deea6-133">此檔案包含標頭指出回報錯誤的位置，結尾指出該批次的批次 ID，且內文含有一或多筆錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="deea6-133">The file consists of a header indicating the location reporting the error(s), a trailer with a batch ID for this batch, and a body consisting of one or more error records.</span></span> <span data-ttu-id="deea6-134">檔案的格式如下：</span><span class="sxs-lookup"><span data-stu-id="deea6-134">The format of the file is as follows:</span></span>  
  
    ```  
    Location  
    ERRORid|type|priority|description|errorDateTime  
    …additional error records   
    BatchID  
    ```  
  
    <span data-ttu-id="deea6-135">錯誤記錄會加上"ERROR"文字，而且以分隔 」&#124;"字元 （有別於位置）。</span><span class="sxs-lookup"><span data-stu-id="deea6-135">The ERROR record is tagged with the text “ERROR” and delimited with the “&#124;” character (versus positional).</span></span> <span data-ttu-id="deea6-136">ERROR 記錄的資料項目如下表所述。</span><span class="sxs-lookup"><span data-stu-id="deea6-136">The data elements of the ERROR record are described in the following table.</span></span>  
  
    |<span data-ttu-id="deea6-137">元素</span><span class="sxs-lookup"><span data-stu-id="deea6-137">Element</span></span>|<span data-ttu-id="deea6-138">資料類型</span><span class="sxs-lookup"><span data-stu-id="deea6-138">Data type</span></span>|<span data-ttu-id="deea6-139">描述</span><span class="sxs-lookup"><span data-stu-id="deea6-139">Description</span></span>|  
    |---|---|---|  
    |<span data-ttu-id="deea6-140">ID</span><span class="sxs-lookup"><span data-stu-id="deea6-140">ID</span></span>|<span data-ttu-id="deea6-141">integer</span><span class="sxs-lookup"><span data-stu-id="deea6-141">integer</span></span>|<span data-ttu-id="deea6-142">此錯誤的 ID。</span><span class="sxs-lookup"><span data-stu-id="deea6-142">ID for this error.</span></span>|  
    |<span data-ttu-id="deea6-143">類型</span><span class="sxs-lookup"><span data-stu-id="deea6-143">Type</span></span>|<span data-ttu-id="deea6-144">integer</span><span class="sxs-lookup"><span data-stu-id="deea6-144">integer</span></span>|<span data-ttu-id="deea6-145">錯誤的類型。</span><span class="sxs-lookup"><span data-stu-id="deea6-145">Type of error.</span></span>|  
    |<span data-ttu-id="deea6-146">優先權</span><span class="sxs-lookup"><span data-stu-id="deea6-146">Priority</span></span>|<span data-ttu-id="deea6-147">string</span><span class="sxs-lookup"><span data-stu-id="deea6-147">string</span></span>|<span data-ttu-id="deea6-148">優先順序指標：「低」、「中」或「高」。</span><span class="sxs-lookup"><span data-stu-id="deea6-148">Priority indicator: Low, Medium, or High.</span></span>|  
    |<span data-ttu-id="deea6-149">描述</span><span class="sxs-lookup"><span data-stu-id="deea6-149">Description</span></span>|<span data-ttu-id="deea6-150">string</span><span class="sxs-lookup"><span data-stu-id="deea6-150">string</span></span>|<span data-ttu-id="deea6-151">錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="deea6-151">Description of the error.</span></span>|  
    |<span data-ttu-id="deea6-152">錯誤日期時間</span><span class="sxs-lookup"><span data-stu-id="deea6-152">ErrorDateTime</span></span>|<span data-ttu-id="deea6-153">DateTime</span><span class="sxs-lookup"><span data-stu-id="deea6-153">DateTime</span></span>|<span data-ttu-id="deea6-154">發生錯誤的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="deea6-154">Date and time that the error occurred.</span></span>|  
  
    <span data-ttu-id="deea6-155">檔案中可能有一筆或多筆 ERROR 記錄。</span><span class="sxs-lookup"><span data-stu-id="deea6-155">The file can have one or more ERROR records.</span></span>  
  
     <span data-ttu-id="deea6-156">* *-或--* *</span><span class="sxs-lookup"><span data-stu-id="deea6-156">**-- OR --  **</span></span>
  
     <span data-ttu-id="deea6-157">將下列的範例資料複製到新的檔案。</span><span class="sxs-lookup"><span data-stu-id="deea6-157">Copy the following sample data into the new file.</span></span> <span data-ttu-id="deea6-158">最後一行包含尾端換行字元：</span><span class="sxs-lookup"><span data-stu-id="deea6-158">The last line contains a trailing linefeed:</span></span>
  
    ```  
    East Coast Facility  
    ERROR102|0|High|Sprocket query fails.|1999-05-31T13:20:00.000-05:00  
    ERROR16502|2|Low|Time threshold exceeded.|1999-05-31T13:20:00.000-05:00  
    8675309  
  
    ```  
  
3.  <span data-ttu-id="deea6-159">將新的範例檔案儲存到專案目錄中。</span><span class="sxs-lookup"><span data-stu-id="deea6-159">Save the new sample file in the project directory.</span></span> <span data-ttu-id="deea6-160">請使用描述性名稱如 "ErrorFile.txt" 以方便找到檔案。</span><span class="sxs-lookup"><span data-stu-id="deea6-160">Use a descriptive name like "ErrorFile.txt" so it can be located easily.</span></span>  
  
### <a name="create-and-test-the-header-trailer-and-body-schemas"></a><span data-ttu-id="deea6-161">建立並測試標頭、結尾和內文結構描述</span><span class="sxs-lookup"><span data-stu-id="deea6-161">Create and Test the Header, Trailer, and Body Schemas</span></span>  
 <span data-ttu-id="deea6-162">建立範例資料檔案後，下一步驟就是建立標頭、結尾和內文結構描述。</span><span class="sxs-lookup"><span data-stu-id="deea6-162">After the sample data file is created, the next step is to create the header, trailer, and body schemas.</span></span> <span data-ttu-id="deea6-163">這些結構描述將供「一般檔案解譯器」接收管線元件用來處理接收的訊息。</span><span class="sxs-lookup"><span data-stu-id="deea6-163">These schemas are used with the Flat File Disassembler receive pipeline component to process received messages.</span></span>  
  
##### <a name="use-the-flat-file-schema-wizard-to-create-the-header-schema"></a><span data-ttu-id="deea6-164">使用一般檔案結構描述精靈建立標頭結構描述</span><span class="sxs-lookup"><span data-stu-id="deea6-164">Use the Flat File Schema Wizard to create the header schema</span></span>  
  
1.  <span data-ttu-id="deea6-165">在專案中新增結構描述。</span><span class="sxs-lookup"><span data-stu-id="deea6-165">Add a new schema to the project.</span></span> <span data-ttu-id="deea6-166">在 [方案總管] 中，以滑鼠右鍵按一下**FFDisassemblerWalkthrough**，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="deea6-166">In Solution Explorer, right-click **FFDisassemblerWalkthrough**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="deea6-167">在 [**加入新項目**] 對話方塊中，按一下**結構描述檔案**，然後選取**一般檔案結構描述精靈**。</span><span class="sxs-lookup"><span data-stu-id="deea6-167">In the **Add New Item** dialog box, click **Schema Files** and select **Flat File Schema Wizard**.</span></span> <span data-ttu-id="deea6-168">命名新的結構描述"命名為 Header.xsd"，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="deea6-168">Name the new schema "Header.xsd" and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="deea6-169">在 [**歡迎使用 BizTalk 一般檔案結構描述精靈**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="deea6-169">On the **Welcome to the BizTalk Flat File Schema Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="deea6-170">在 **一般檔案結構描述資訊**頁面上，按一下**瀏覽**並找出稍早建立的範例資料檔案。</span><span class="sxs-lookup"><span data-stu-id="deea6-170">On the **Flat File Schema Information** page, click **Browse** and locate the sample data file created earlier.</span></span> <span data-ttu-id="deea6-171">變更**記錄名稱**為"Header"，確認字碼頁，然後**下一步**。</span><span class="sxs-lookup"><span data-stu-id="deea6-171">Change the **Record Name** to "Header", verify the code page, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="deea6-172">如果範例檔案儲存成 Unicode 格式，字碼頁即為 Little-Endian-UTF16 (1200)。</span><span class="sxs-lookup"><span data-stu-id="deea6-172">If you saved the sample file in Unicode format the code page will be Little-Endian-UTF16 (1200).</span></span> <span data-ttu-id="deea6-173">這對本範例不會造成不良影響。</span><span class="sxs-lookup"><span data-stu-id="deea6-173">This will not adversely affect the example.</span></span>  
  
5.  <span data-ttu-id="deea6-174">接著選取文件資料。</span><span class="sxs-lookup"><span data-stu-id="deea6-174">Next select the document data.</span></span> <span data-ttu-id="deea6-175">在 **選取文件資料**頁面上，反白顯示的第一行的資料，包括新行字元 {CR} 和 {LF} 所示：</span><span class="sxs-lookup"><span data-stu-id="deea6-175">On the **Select Document Data** page, highlight the first line of data including the new-line characters {CR} and {LF} as shown:</span></span>  
  
     <span data-ttu-id="deea6-176">![選取為標頭結構描述的資料](../core/media/ffwiz-header-select-document-data.gif "ffwiz_header_select_document_data")</span><span class="sxs-lookup"><span data-stu-id="deea6-176">![Data selected for header schema](../core/media/ffwiz-header-select-document-data.gif "ffwiz_header_select_document_data")</span></span>  
  
     <span data-ttu-id="deea6-177">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="deea6-177">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="deea6-178">在 [**選取記錄格式**頁面上，按一下**下一步]** 接受預設值。</span><span class="sxs-lookup"><span data-stu-id="deea6-178">On the **Select Record Format** page, click **Next** to accept the default.</span></span> <span data-ttu-id="deea6-179">可接受預設值「依分隔符號」是因為資料檔案並未使用相對位置。</span><span class="sxs-lookup"><span data-stu-id="deea6-179">You can accept the default "by delimiter symbol" because the data file does not use relative position.</span></span>  
  
7.  <span data-ttu-id="deea6-180">在 [**分隔記錄**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="deea6-180">On the **Delimited Record** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="deea6-181">接著指定子項目。</span><span class="sxs-lookup"><span data-stu-id="deea6-181">Now you specify child elements.</span></span> <span data-ttu-id="deea6-182">標頭含有一個項目，名為 "Location"：</span><span class="sxs-lookup"><span data-stu-id="deea6-182">The header contains one element named "Location":</span></span>  
  
     <span data-ttu-id="deea6-183">![定義的標頭位置節點](../core/media/ffwiz-header-child-elements.gif "ffwiz_header_child_elements")</span><span class="sxs-lookup"><span data-stu-id="deea6-183">![Location node defined for header](../core/media/ffwiz-header-child-elements.gif "ffwiz_header_child_elements")</span></span>  
  
     <span data-ttu-id="deea6-184">按 **[下一步]** ，繼續進行。</span><span class="sxs-lookup"><span data-stu-id="deea6-184">Click **Next** to continue.</span></span>  
  
9. <span data-ttu-id="deea6-185">在 **結構描述檢視**頁面上，確認結構描述。</span><span class="sxs-lookup"><span data-stu-id="deea6-185">On the **Schema View** page, verify the schema.</span></span>  
  
     <span data-ttu-id="deea6-186">![已完成的結構描述檢視顯示標頭結構描述](../core/media/ffwiz-header-schema-view.gif "ffwiz_header_schema_view")</span><span class="sxs-lookup"><span data-stu-id="deea6-186">![Schema view showing completed Header schema](../core/media/ffwiz-header-schema-view.gif "ffwiz_header_schema_view")</span></span>  
  
     <span data-ttu-id="deea6-187">當您滿意，請按一下**完成**以完成精靈。</span><span class="sxs-lookup"><span data-stu-id="deea6-187">When you are satisfied, click **Finish** to complete the wizard.</span></span>  
  
10. <span data-ttu-id="deea6-188">按一下 [ **\<結構描述\>** 標頭結構描述] 窗格中的節點。</span><span class="sxs-lookup"><span data-stu-id="deea6-188">Click the **\<Schema\>** node in the Header schema pane.</span></span> <span data-ttu-id="deea6-189">在 [屬性] 窗格中，變更**Element FormDefault**要**Qualified**。</span><span class="sxs-lookup"><span data-stu-id="deea6-189">In the Properties pane, change **Element FormDefault** to **Qualified**.</span></span> <span data-ttu-id="deea6-190">這表示區域宣告項目必須由執行個體文件中的目標命名空間限定。</span><span class="sxs-lookup"><span data-stu-id="deea6-190">This indicates that locally declared elements must be qualified by the target namespace in an instance document.</span></span>  
  
##### <a name="use-the-flat-file-schema-wizard-to-create-the-trailer-schema"></a><span data-ttu-id="deea6-191">使用一般檔案結構描述精靈建立結尾結構描述</span><span class="sxs-lookup"><span data-stu-id="deea6-191">Use the Flat File Schema Wizard to create the trailer schema</span></span>  
  
1.  <span data-ttu-id="deea6-192">在專案中新增結構描述。</span><span class="sxs-lookup"><span data-stu-id="deea6-192">Add a new schema to the project.</span></span> <span data-ttu-id="deea6-193">在 [方案總管] 中，以滑鼠右鍵按一下**FFDisassemblerWalkthrough**，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="deea6-193">In Solution Explorer, right-click **FFDisassemblerWalkthrough**, point to **Add** , and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="deea6-194">在 [**加入新項目**] 對話方塊中，按一下**結構描述檔案**，然後選取**一般檔案結構描述精靈**。</span><span class="sxs-lookup"><span data-stu-id="deea6-194">In the **Add New Item** dialog box, click **Schema Files** and select **Flat File Schema Wizard**.</span></span> <span data-ttu-id="deea6-195">命名新的結構描述"命名為 Trailer.xsd"，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="deea6-195">Name the new schema "Trailer.xsd" and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="deea6-196">在 [**歡迎使用 BizTalk 一般檔案結構描述精靈**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="deea6-196">On the **Welcome to the BizTalk Flat File Schema Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="deea6-197">在 **一般檔案結構描述資訊**頁面上，按一下**瀏覽**並找出稍早建立的範例資料檔案。</span><span class="sxs-lookup"><span data-stu-id="deea6-197">On the **Flat File Schema Information** page, click **Browse** and locate the sample data file created earlier.</span></span> <span data-ttu-id="deea6-198">變更**記錄名稱**改為"Trailer"，確認字碼頁，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="deea6-198">Change the **Record Name** to "Trailer", verify the code page, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="deea6-199">如果範例檔案儲存成 Unicode 格式，字碼頁即為 Little-Endian-UTF16 (1200)。</span><span class="sxs-lookup"><span data-stu-id="deea6-199">If you saved the sample file in Unicode format the code page will be Little-Endian-UTF16 (1200).</span></span> <span data-ttu-id="deea6-200">這對本範例不會造成不良影響。</span><span class="sxs-lookup"><span data-stu-id="deea6-200">This will not adversely affect the example.</span></span>  
  
5.  <span data-ttu-id="deea6-201">接著選取文件資料。</span><span class="sxs-lookup"><span data-stu-id="deea6-201">Next select the document data.</span></span> <span data-ttu-id="deea6-202">在 **選取文件資料**頁面上，反白顯示的最後一行的資料，包括新行字元 {CR} 和 {LF} 所示：</span><span class="sxs-lookup"><span data-stu-id="deea6-202">On the **Select Document Data** page, highlight the last line of data including the new-line characters {CR} and {LF} as shown:</span></span>  
  
     <span data-ttu-id="deea6-203">![選取為結尾結構描述的資料](../core/media/ffwiz-trailer-select-document-data.gif "ffwiz_trailer_select_document_data")</span><span class="sxs-lookup"><span data-stu-id="deea6-203">![Data selected for trailer schema](../core/media/ffwiz-trailer-select-document-data.gif "ffwiz_trailer_select_document_data")</span></span>  
  
     <span data-ttu-id="deea6-204">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="deea6-204">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="deea6-205">在 [**選取記錄格式**頁面上，按一下**下一步]** 接受預設值。</span><span class="sxs-lookup"><span data-stu-id="deea6-205">On the **Select Record Format** page, click **Next** to accept the default.</span></span> <span data-ttu-id="deea6-206">可接受預設值「依分隔符號」是因為資料檔案並未使用相對位置。</span><span class="sxs-lookup"><span data-stu-id="deea6-206">You can accept the default "by delimiter symbol" because the data file does not use relative position.</span></span>  
  
7.  <span data-ttu-id="deea6-207">在 [**分隔記錄**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="deea6-207">On the **Delimited Record** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="deea6-208">接著指定子項目。</span><span class="sxs-lookup"><span data-stu-id="deea6-208">Now you specify child elements.</span></span> <span data-ttu-id="deea6-209">結尾含有一個項目，名為 "BatchID"：</span><span class="sxs-lookup"><span data-stu-id="deea6-209">The header contains one element named "BatchID":</span></span>  
  
     <span data-ttu-id="deea6-210">![為結尾定義的位置節點](../core/media/ffwiz-trailer-child-elements.gif "ffwiz_trailer_child_elements")</span><span class="sxs-lookup"><span data-stu-id="deea6-210">![Location node defined for trailer](../core/media/ffwiz-trailer-child-elements.gif "ffwiz_trailer_child_elements")</span></span>  
  
     <span data-ttu-id="deea6-211">按 **[下一步]** ，繼續進行。</span><span class="sxs-lookup"><span data-stu-id="deea6-211">Click **Next** to continue.</span></span>  
  
9. <span data-ttu-id="deea6-212">在 **結構描述檢視**頁面上，確認結構描述。</span><span class="sxs-lookup"><span data-stu-id="deea6-212">On the **Schema View** page, verify the schema.</span></span>  
  
     <span data-ttu-id="deea6-213">![結構描述檢視顯示已完成結尾結構描述](../core/media/ffwiz-trailer-schema-view.gif "ffwiz_trailer_schema_view")</span><span class="sxs-lookup"><span data-stu-id="deea6-213">![Schema view showing completed Trailer schema](../core/media/ffwiz-trailer-schema-view.gif "ffwiz_trailer_schema_view")</span></span>  
  
     <span data-ttu-id="deea6-214">當您滿意，請按一下**完成**以完成精靈。</span><span class="sxs-lookup"><span data-stu-id="deea6-214">When you are satisfied, click **Finish** to complete the wizard.</span></span>  
  
10. <span data-ttu-id="deea6-215">按一下 [ **\<結構描述\>** 結尾結構描述] 窗格中的節點。</span><span class="sxs-lookup"><span data-stu-id="deea6-215">Click the **\<Schema\>** node in the Trailer schema pane.</span></span> <span data-ttu-id="deea6-216">在 [屬性] 窗格中，變更**elementFormDefault**要**Qualified**。</span><span class="sxs-lookup"><span data-stu-id="deea6-216">In the Properties pane, change **elementFormDefault** to **Qualified**.</span></span> <span data-ttu-id="deea6-217">這表示區域宣告項目必須由執行個體文件中的目標命名空間限定。</span><span class="sxs-lookup"><span data-stu-id="deea6-217">This indicates that locally declared elements must be qualified by the target namespace in an instance document.</span></span>  
  
##### <a name="use-the-flat-file-schema-wizard-to-create-the-body-schema"></a><span data-ttu-id="deea6-218">使用 「 一般檔案結構描述精靈 」 建立的內文結構描述</span><span class="sxs-lookup"><span data-stu-id="deea6-218">Use the Flat File Schema Wizard to create the body schema</span></span>  
  
1.  <span data-ttu-id="deea6-219">在專案中新增結構描述。</span><span class="sxs-lookup"><span data-stu-id="deea6-219">Add a new schema to the project.</span></span> <span data-ttu-id="deea6-220">在 [方案總管] 中，以滑鼠右鍵按一下**FFDisassemblerWalkthrough**，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="deea6-220">In Solution Explorer, right-click **FFDisassemblerWalkthrough**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="deea6-221">在 [**加入新項目**] 對話方塊中，按一下**結構描述檔案**，然後選取**一般檔案結構描述精靈**。</span><span class="sxs-lookup"><span data-stu-id="deea6-221">In the **Add New Item** dialog box, click **Schema Files** and select **Flat File Schema Wizard**.</span></span> <span data-ttu-id="deea6-222">命名新的結構描述"命名為 Body.xsd"，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="deea6-222">Name the new schema "Body.xsd" and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="deea6-223">在 [**歡迎使用 BizTalk 一般檔案結構描述精靈**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="deea6-223">On the **Welcome to the BizTalk Flat File Schema Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="deea6-224">在 **一般檔案結構描述資訊**頁面上，按一下**瀏覽**並找出稍早建立的範例資料檔案。</span><span class="sxs-lookup"><span data-stu-id="deea6-224">On the **Flat File Schema Information** page, click **Browse** and locate the sample data file created earlier.</span></span> <span data-ttu-id="deea6-225">變更**記錄名稱**為"Body"，確認字碼頁，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="deea6-225">Change the **Record Name** to "Body", verify the code page, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="deea6-226">如果範例檔案儲存成 Unicode 格式，字碼頁即為 Little-Endian-UTF16 (1200)。</span><span class="sxs-lookup"><span data-stu-id="deea6-226">If you saved the sample file in Unicode format the code page will be Little-Endian-UTF16 (1200).</span></span> <span data-ttu-id="deea6-227">這對本範例不會造成不良影響。</span><span class="sxs-lookup"><span data-stu-id="deea6-227">This will not adversely affect the example.</span></span>  
  
5.  <span data-ttu-id="deea6-228">接著選取文件資料。</span><span class="sxs-lookup"><span data-stu-id="deea6-228">Next select the document data.</span></span> <span data-ttu-id="deea6-229">在 **選取文件資料**頁面上，反白顯示兩個和第三的資料行含有新行字元 {CR} 和 {LF} 所示：</span><span class="sxs-lookup"><span data-stu-id="deea6-229">On the **Select Document Data** page, highlight lines two and three of data including the new-line characters {CR} and {LF} as shown:</span></span>  
  
     <span data-ttu-id="deea6-230">![選取為內文結構描述的資料](../core/media/ffwiz-body-select-document-data.gif "ffwiz_body_select_document_data")</span><span class="sxs-lookup"><span data-stu-id="deea6-230">![Data selected for body schema](../core/media/ffwiz-body-select-document-data.gif "ffwiz_body_select_document_data")</span></span>  
  
     <span data-ttu-id="deea6-231">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="deea6-231">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="deea6-232">在 [**選取記錄格式**頁面上，按一下**下一步]** 接受預設值。</span><span class="sxs-lookup"><span data-stu-id="deea6-232">On the **Select Record Format** page, click **Next** to accept the default.</span></span> <span data-ttu-id="deea6-233">可接受預設值「依分隔符號」是因為資料檔案並未使用相對位置。</span><span class="sxs-lookup"><span data-stu-id="deea6-233">You can accept the default "by delimiter symbol" because the data file does not use relative position.</span></span>  
  
7.  <span data-ttu-id="deea6-234">在 [**分隔記錄**頁面上，選取**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="deea6-234">On the **Delimited Record** page, select **Next**.</span></span>  
  
8.  <span data-ttu-id="deea6-235">接著定義子項目。</span><span class="sxs-lookup"><span data-stu-id="deea6-235">Next define the child elements.</span></span> <span data-ttu-id="deea6-236">變更**Body_Child1**要**錯誤**並將其項目類型設定為**重複記錄**。</span><span class="sxs-lookup"><span data-stu-id="deea6-236">Change **Body_Child1** to **Error**and set its element type to **Repeating record**.</span></span> <span data-ttu-id="deea6-237">設定**Body_Child2**項目記錄型別**忽略**。</span><span class="sxs-lookup"><span data-stu-id="deea6-237">Set the **Body_Child2** element record type to **Ignore**.</span></span>  
  
9. <span data-ttu-id="deea6-238">在 [**結構描述檢視**頁面上，按一下**下一步]** 定義 Error 記錄的子項目。</span><span class="sxs-lookup"><span data-stu-id="deea6-238">On the **Schema View** page, click **Next** to define the child elements of the Error record.</span></span>  
  
10. <span data-ttu-id="deea6-239">在 [**選取文件資料**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="deea6-239">On the **Select Document Data** page, click **Next**.</span></span> <span data-ttu-id="deea6-240">精靈會正確選擇記錄定義的資料。</span><span class="sxs-lookup"><span data-stu-id="deea6-240">The wizard chooses the record-defining data correctly.</span></span>  
  
11. <span data-ttu-id="deea6-241">在 [**選取記錄格式**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="deea6-241">On the **Select Record Format** page, click **Next**.</span></span> <span data-ttu-id="deea6-242">資料會以分隔符號進行格式化。</span><span class="sxs-lookup"><span data-stu-id="deea6-242">The data is formatted by delimiter symbol.</span></span>  
  
12. <span data-ttu-id="deea6-243">在 **分隔記錄**頁面上，選取 **&#124;** 如**子分隔符號**。</span><span class="sxs-lookup"><span data-stu-id="deea6-243">On the **Delimited Record** page, select **&#124;** for the **Child delimiter**.</span></span> <span data-ttu-id="deea6-244">接下來，選取**記錄具有標記識別項**核取方塊，然後輸入**錯誤**做為標記值。</span><span class="sxs-lookup"><span data-stu-id="deea6-244">Next, select the **Record has a tag identifier** check box and type **ERROR** for the tag value.</span></span>  
  
     <span data-ttu-id="deea6-245">![設定分隔記錄具有標記識別項](../core/media/ffwiz-bodyerror-delimited-record.gif "ffwiz_bodyerror_delimited_record")</span><span class="sxs-lookup"><span data-stu-id="deea6-245">![Configuring delimited record with tag identifier](../core/media/ffwiz-bodyerror-delimited-record.gif "ffwiz_bodyerror_delimited_record")</span></span>  
  
     <span data-ttu-id="deea6-246">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="deea6-246">Click **Next**.</span></span>  
  
13. <span data-ttu-id="deea6-247">接著定義 Error 記錄的子項目。</span><span class="sxs-lookup"><span data-stu-id="deea6-247">Now define the child elements of the Error record.</span></span>  
  
     <span data-ttu-id="deea6-248">![定義包含五個元素的錯誤記錄](../core/media/ffwiz-bodyerror-child-elements.gif "ffwiz_bodyerror_child_elements")</span><span class="sxs-lookup"><span data-stu-id="deea6-248">![Error record defined with five elements](../core/media/ffwiz-bodyerror-child-elements.gif "ffwiz_bodyerror_child_elements")</span></span>  
  
     <span data-ttu-id="deea6-249">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="deea6-249">Click **Next**.</span></span>  
  
14. <span data-ttu-id="deea6-250">在 **結構描述檢視**頁面上，確認結構描述。</span><span class="sxs-lookup"><span data-stu-id="deea6-250">On the **Schema View** page, verify the schema.</span></span>  
  
     <span data-ttu-id="deea6-251">![結構描述檢視顯示已完成的內文結構描述](../core/media/ffwiz-bodyerror-schema-view.gif "ffwiz_bodyerror_schema_view")</span><span class="sxs-lookup"><span data-stu-id="deea6-251">![Schema view showing completed Body schema](../core/media/ffwiz-bodyerror-schema-view.gif "ffwiz_bodyerror_schema_view")</span></span>  
  
     <span data-ttu-id="deea6-252">如果您所做的任何錯誤，請按一下**回**並進行必要的修正。</span><span class="sxs-lookup"><span data-stu-id="deea6-252">If you have made any mistakes, click **Back** and make the necessary corrections.</span></span> <span data-ttu-id="deea6-253">當您滿意，請按一下**完成**以完成精靈。</span><span class="sxs-lookup"><span data-stu-id="deea6-253">When you are satisfied, click **Finish** to complete the wizard.</span></span>  
  
15. <span data-ttu-id="deea6-254">按一下 [ **\<結構描述\>** Body] 結構描述窗格中的節點。</span><span class="sxs-lookup"><span data-stu-id="deea6-254">Click the **\<Schema\>** node in the Body schema pane.</span></span> <span data-ttu-id="deea6-255">在 [屬性] 窗格中，變更**Element FormDefault**要**Qualified**。</span><span class="sxs-lookup"><span data-stu-id="deea6-255">In the Properties pane, change **Element FormDefault** to **Qualified**.</span></span> <span data-ttu-id="deea6-256">這表示區域宣告項目必須由執行個體文件中的目標命名空間限定。</span><span class="sxs-lookup"><span data-stu-id="deea6-256">This indicates that locally declared elements must be qualified by the target namespace in an instance document.</span></span>  
  
16. <span data-ttu-id="deea6-257">按一下 [ **\<錯誤\>** Body] 結構描述窗格上的節點。</span><span class="sxs-lookup"><span data-stu-id="deea6-257">Click the **\<Error\>** node on the Body schema pane.</span></span> <span data-ttu-id="deea6-258">在 [屬性] 窗格中，變更**Max Occurs**要**1**。</span><span class="sxs-lookup"><span data-stu-id="deea6-258">In the Properties pane, change **Max Occurs** to **1**.</span></span> <span data-ttu-id="deea6-259">這可讓「一般檔案解譯器」將每項錯誤分割為個別的訊息。</span><span class="sxs-lookup"><span data-stu-id="deea6-259">This causes the Flat File Disassembler to split each error into its own message.</span></span>  
  
##### <a name="test-the-schemas-using-ffdasm"></a><span data-ttu-id="deea6-260">測試使用 FFDasm 的結構描述</span><span class="sxs-lookup"><span data-stu-id="deea6-260">Test the schemas using FFDasm</span></span>  
  
1.  <span data-ttu-id="deea6-261">開啟命令提示字元，再將目錄變更為您的專案目錄。</span><span class="sxs-lookup"><span data-stu-id="deea6-261">Open a command prompt and change the directory to your project directory.</span></span>  
  
2.  <span data-ttu-id="deea6-262">從命令提示字元執行 FFDasm.exe，如下所示。</span><span class="sxs-lookup"><span data-stu-id="deea6-262">From the command prompt, run FFDasm.exe as shown below.</span></span>  
  
    ```  
    <Samples Path>\SDK\Utilities\PipelineTools\FFDasm ErrorFile.txt  -hs header.xsd -bs body.xsd -ts Trailer.xsd  
    ```  
  
     <span data-ttu-id="deea6-263">這和其他管線工具的位置相關資訊，請參閱[管線工具](../core/pipeline-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="deea6-263">For information about the location of this and other pipeline tools, see [Pipeline Tools](../core/pipeline-tools.md).</span></span>  
  
3.  <span data-ttu-id="deea6-264">FFDasm.exe 會產生兩個名為 {GUID}.xml 的輸出檔，分別代表測試檔案中的一筆 ERROR 記錄。</span><span class="sxs-lookup"><span data-stu-id="deea6-264">FFDasm.exe should produce two output files named {GUID}.xml, one for each ERROR record in the test file.</span></span> <span data-ttu-id="deea6-265">高優先順序的錯誤記錄看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="deea6-265">The high-priority error record looks like the following:</span></span>  
  
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
  
### <a name="create-a-custom-receive-pipeline"></a><span data-ttu-id="deea6-266">建立自訂接收管線</span><span class="sxs-lookup"><span data-stu-id="deea6-266">Create a Custom Receive Pipeline</span></span>  
 <span data-ttu-id="deea6-267">如今一般檔案結構描述已經定義完成，您必須建立自訂管線以使用「一般檔案解譯器」元件。</span><span class="sxs-lookup"><span data-stu-id="deea6-267">Now that the flat file schemas are defined, you need to create a custom pipeline that uses the Flat File Disassembler component.</span></span> <span data-ttu-id="deea6-268">然後即可將「一般檔案解譯器」元件設定為使用標頭、內文和結尾結構描述來拆解訊息。</span><span class="sxs-lookup"><span data-stu-id="deea6-268">The Flat File Disassembler component can then be configured to use the header, body, and trailer schemas to break up messages.</span></span>    
 
1.  <span data-ttu-id="deea6-269">在專案中新增接收管線。</span><span class="sxs-lookup"><span data-stu-id="deea6-269">Add a new receive pipeline to the project.</span></span> <span data-ttu-id="deea6-270">在 [方案總管] 中，以滑鼠右鍵按一下**FFDisassemblerWalkthrough**專案，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="deea6-270">In Solution Explorer, right-click the **FFDisassemblerWalkthrough** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="deea6-271">在 **加入新項目** 對話方塊中，指向**管線檔案**，然後按一下 **接收管線**。</span><span class="sxs-lookup"><span data-stu-id="deea6-271">In the **Add New Item** dialog box, point to **Pipeline Files** and then click **Receive Pipeline**.</span></span> <span data-ttu-id="deea6-272">命名新的管線"為 FFReceivePipeline"，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="deea6-272">Name the new pipeline "FFReceivePipeline" and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="deea6-273">將「一般檔案解譯器」元件從 [工具箱] 窗格拖曳到「解譯」步驟以設定新管線。</span><span class="sxs-lookup"><span data-stu-id="deea6-273">Configure the new pipeline by dragging the Flat File Disassembler component from the Toolbox pane to the Disassemble step.</span></span>  
  
4.  <span data-ttu-id="deea6-274">在 [屬性] 窗格中，設定**文件結構描述**要**FFDisassemblerWalkthrough.Body**，則**標頭結構描述**至**FFDisassemblerWalkthrough.Header**而**結尾結構描述**要**FFDisassemblerWalkthrough.Trailer**。</span><span class="sxs-lookup"><span data-stu-id="deea6-274">In the Properties pane, set the **Document schema** to **FFDisassemblerWalkthrough.Body**, the **Header schema** to **FFDisassemblerWalkthrough.Header** and the **Trailer schema** to **FFDisassemblerWalkthrough.Trailer**.</span></span>  
  
### <a name="deploy-the-application-and-configure-the-send-and-receive-ports"></a><span data-ttu-id="deea6-275">部署應用程式並設定傳送埠和接收埠</span><span class="sxs-lookup"><span data-stu-id="deea6-275">Deploy the Application and Configure the Send and Receive Ports</span></span>  
 <span data-ttu-id="deea6-276">建立結構描述和自訂接收管線後，您必須編譯並部署專案。</span><span class="sxs-lookup"><span data-stu-id="deea6-276">With the schemas and custom receive pipeline created, you need to compile and deploy the project.</span></span> <span data-ttu-id="deea6-277">一旦專案部署完成，即可使用「BizTalk Server 管理主控台」設定傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="deea6-277">After it is deployed, you can use the BizTalk Server Administration console to configure the send and receive ports.</span></span>  

##### <a name="deploy"></a><span data-ttu-id="deea6-278">部署</span><span class="sxs-lookup"><span data-stu-id="deea6-278">Deploy</span></span>  
1. <span data-ttu-id="deea6-279">內在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，將方案部署的專案上按一下滑鼠右鍵，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="deea6-279">From within [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], deploy the solution by right-clicking on the project and then clicking **Deploy**.</span></span>  
  
2. <span data-ttu-id="deea6-280">使用 BizTalk Server 管理主控台中，依序展開**應用程式**群組，以確認**FlatFileExample**呈現為自訂的應用程式。</span><span class="sxs-lookup"><span data-stu-id="deea6-280">Using the BizTalk Server Administration console, expand the **Applications** group to verify that **FlatFileExample** is present as a custom application.</span></span>  
  
##### <a name="configure-the-receive-port"></a><span data-ttu-id="deea6-281">設定接收埠</span><span class="sxs-lookup"><span data-stu-id="deea6-281">Configure the receive port</span></span>  
  
1.  <span data-ttu-id="deea6-282">使用 Windows 檔案總管來建立名為"Receive"目錄，底下**FFDisassemblerWalkthrough**專案目錄。</span><span class="sxs-lookup"><span data-stu-id="deea6-282">Use Windows Explorer to create a directory named "Receive" under the **FFDisassemblerWalkthrough** project directory.</span></span>  
  
2.  <span data-ttu-id="deea6-283">在 BizTalk Server 管理主控台中，依序展開**FlatFileExample**應用程式，以滑鼠右鍵按一下**接收埠**，指向**新增**，然後按一下  **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="deea6-283">In the BizTalk Server Administration console, expand the **FlatFileExample** application, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
3.  <span data-ttu-id="deea6-284">在 **接收埠屬性**對話方塊方塊中，設定為"ReceiveError"的連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="deea6-284">In the **Receive Port Properties** dialog box, set the name of the port to "ReceiveError".</span></span>  
  
4.  <span data-ttu-id="deea6-285">按一下 **接收位置**，然後按一下**新增**新增接收位置。</span><span class="sxs-lookup"><span data-stu-id="deea6-285">Click **Receive Locations**, and then click **New** to add a receive location.</span></span> <span data-ttu-id="deea6-286">將新的接收位置命名為 "ReceiveErrorLocation"。</span><span class="sxs-lookup"><span data-stu-id="deea6-286">Name the new receive location "ReceiveErrorLocation".</span></span> <span data-ttu-id="deea6-287">設定**接收管線**要**FFReceivePipeline**。</span><span class="sxs-lookup"><span data-stu-id="deea6-287">Set the **Receive Pipeline** to **FFReceivePipeline**.</span></span> <span data-ttu-id="deea6-288">針對**傳輸類型**，選取**檔案**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="deea6-288">For **Transport Type**, select **FILE**, and then click **Configure**.</span></span> <span data-ttu-id="deea6-289">選取的接收目錄，您建立，並將**檔案遮罩**至 \*.txt。</span><span class="sxs-lookup"><span data-stu-id="deea6-289">Select the receive directory you created, and then set the **File mask** to \*.txt.</span></span>  
  
5.  <span data-ttu-id="deea6-290">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="deea6-290">Click **OK**.</span></span> <span data-ttu-id="deea6-291">接收埠即設定完成。</span><span class="sxs-lookup"><span data-stu-id="deea6-291">Your receive port should now be configured.</span></span> <span data-ttu-id="deea6-292">按一下 **確定**關閉。</span><span class="sxs-lookup"><span data-stu-id="deea6-292">Click **OK** to close.</span></span>  
  
##### <a name="configure-the-send-port"></a><span data-ttu-id="deea6-293">設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="deea6-293">Configure the send port</span></span>  
  
1.  <span data-ttu-id="deea6-294">使用 Windows 檔案總管底下建立名為 「 傳送 」 的目錄**FFDisassemblerWalkthrough**專案目錄。</span><span class="sxs-lookup"><span data-stu-id="deea6-294">Use Windows Explorer to create a directory named "Send" under the **FFDisassemblerWalkthrough** project directory.</span></span>  
  
2.  <span data-ttu-id="deea6-295">在 BizTalk Server 管理主控台中，依序展開**FlatFileExample**應用程式，以滑鼠右鍵按一下**傳送連接埠**，指向**新增**，然後按一下  **靜態單向傳送埠...**.</span><span class="sxs-lookup"><span data-stu-id="deea6-295">In the BizTalk Server Administration console, expand the **FlatFileExample** application, right-click **Send Ports**, point to **New**, and then click **Static One-Way  Send Port…**.</span></span>  
  
3.  <span data-ttu-id="deea6-296">在 **傳送埠屬性**對話方塊方塊中，設定 「 傳送 」 的連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="deea6-296">In the **Send Port Properties** dialog box, set the name of the port to "Send".</span></span>  
  
4.  <span data-ttu-id="deea6-297">傳輸類型 選取**檔案**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="deea6-297">For transport type, select **FILE**, and then click **Configure**.</span></span> <span data-ttu-id="deea6-298">將目的資料夾設定為剛才建立的傳送目錄。</span><span class="sxs-lookup"><span data-stu-id="deea6-298">Set the destination folder to the send directory you created earlier.</span></span>  
  
5.  <span data-ttu-id="deea6-299">接著設定篩選條件。</span><span class="sxs-lookup"><span data-stu-id="deea6-299">Now configure the filter.</span></span> <span data-ttu-id="deea6-300">按一下 **篩選器**並加入下列運算式：</span><span class="sxs-lookup"><span data-stu-id="deea6-300">Click **Filters** and add one expression:</span></span>  
  
    -   <span data-ttu-id="deea6-301">BTS.MessageType == **http://FFDisassemblerWalkthrough.Body#Body**</span><span class="sxs-lookup"><span data-stu-id="deea6-301">BTS.MessageType == **http://FFDisassemblerWalkthrough.Body#Body**</span></span>  
  
6.  <span data-ttu-id="deea6-302">按一下 **確定**完成傳送埠組態。</span><span class="sxs-lookup"><span data-stu-id="deea6-302">Click **OK** to complete the send port configuration.</span></span> <span data-ttu-id="deea6-303">傳送埠即設定完成。</span><span class="sxs-lookup"><span data-stu-id="deea6-303">Your send port should be configured.</span></span>  
  
### <a name="run-the-example"></a><span data-ttu-id="deea6-304">執行範例</span><span class="sxs-lookup"><span data-stu-id="deea6-304">Run the Example</span></span>  
 <span data-ttu-id="deea6-305">現在即可開始執行範例。</span><span class="sxs-lookup"><span data-stu-id="deea6-305">It is now time to run the example.</span></span> <span data-ttu-id="deea6-306">之後您可以使用 BizTalk Server 管理主控台來啟動應用程式，請將測試檔案複製到接收位置，並觀察 傳送位置中所產生的結果。</span><span class="sxs-lookup"><span data-stu-id="deea6-306">After using the BizTalk Server Management console to start the application, copy the test files to the receive location and observe what is produced in the send location.</span></span>  
  
1.  <span data-ttu-id="deea6-307">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**FlatFileExample**應用程式，，然後按一下**開始**。</span><span class="sxs-lookup"><span data-stu-id="deea6-307">In the BizTalk Server Administration console, right-click the **FlatFileExample** application, and then click **Start**.</span></span> <span data-ttu-id="deea6-308">此登錄和啟動傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="deea6-308">This enlists and starts the send and receive ports.</span></span>  
  
2.  <span data-ttu-id="deea6-309">將範例 Errorfile.txt 複本放到接收目錄中。</span><span class="sxs-lookup"><span data-stu-id="deea6-309">Drop the copy of the sample Errorfile.txt into the receive directory.</span></span> <span data-ttu-id="deea6-310">傳送目錄中應該就會產生兩個輸出檔。</span><span class="sxs-lookup"><span data-stu-id="deea6-310">Two output files should be written to the send directory.</span></span>  
  
