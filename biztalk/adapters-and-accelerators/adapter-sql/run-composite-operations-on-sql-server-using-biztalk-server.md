---
title: 執行複合作業上使用 BizTalk Server 的 SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 86fd2aa1-20c7-4b58-9f35-83ba0c959cf1
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62605fef85727311b2a2396463c2b43b690e86e2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004327"
---
# <a name="run-composite-operations-on-sql-server-using-biztalk-server"></a><span data-ttu-id="cefa8-102">執行 SQL Server 上使用 BizTalk Server 的複合作業</span><span class="sxs-lookup"><span data-stu-id="cefa8-102">Run composite operations on SQL Server using BizTalk Server</span></span>
<span data-ttu-id="cefa8-103">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓配接器用戶端執行複合作業上的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cefa8-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables adapter clients to perform composite operations on the SQL Server database.</span></span> <span data-ttu-id="cefa8-104">複合作業可包括：</span><span class="sxs-lookup"><span data-stu-id="cefa8-104">A composite operation can include:</span></span>  
  
- <span data-ttu-id="cefa8-105">插入、 更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="cefa8-105">Insert, Update, and Delete operations.</span></span> <span data-ttu-id="cefa8-106">選取的作業不支援複合作業的一部分。</span><span class="sxs-lookup"><span data-stu-id="cefa8-106">A Select operation is not supported as part of a composite operation.</span></span>  
  
- <span data-ttu-id="cefa8-107">當做作業執行的預存程序。</span><span class="sxs-lookup"><span data-stu-id="cefa8-107">Stored procedures executed as operations.</span></span>  
  
  <span data-ttu-id="cefa8-108">單一複合作業可以有任意數目的這些作業，以任何順序。</span><span class="sxs-lookup"><span data-stu-id="cefa8-108">A single composite operation can have any number of these operations, in any order.</span></span> <span data-ttu-id="cefa8-109">比方說，您可以有兩個 Insert 作業後面是刪除作業，以及最後的預存程序執行。</span><span class="sxs-lookup"><span data-stu-id="cefa8-109">For example, you can have two Insert operations followed by a Delete operation, and finally a stored procedure execution.</span></span> <span data-ttu-id="cefa8-110">此外，您可以有不同的資料庫資料表或檢視為目標的不同作業。</span><span class="sxs-lookup"><span data-stu-id="cefa8-110">Also, you can have different operations targeting different database tables or views.</span></span> <span data-ttu-id="cefa8-111">如需配接器如何支援複合作業的詳細資訊，請參閱[使用 SQL 配接器的 SQL Server 中執行複合作業](../../adapters-and-accelerators/adapter-sql/run-composite-operations-in-sql-server-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="cefa8-111">For more information about how the adapter supports composite operations, see [Run composite operations in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/run-composite-operations-in-sql-server-using-the-sql-adapter.md).</span></span> <span data-ttu-id="cefa8-112">複合作業的 SOAP 訊息結構的相關資訊，請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="cefa8-112">For information about the structure of the SOAP message for composite operations, see [Message Schemas for Composite Operations](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cefa8-113">如果您正在執行具有使用者定義類型的資料行的資料表上的作業，請確定您參考[資料表和檢視與使用 SQL 配接器的使用者定義型別上的作業](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md)開始開發您的應用程式之前。</span><span class="sxs-lookup"><span data-stu-id="cefa8-113">If you are performing operation on tables that have columns of user-defined types, make sure you refer to [Operations on Tables and Views with User-Defined Types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) before you start developing your application.</span></span>  
  
## <a name="how-to-perform-composite-operations-on-sql-server"></a><span data-ttu-id="cefa8-114">如何執行 SQL Server 上的複合作業</span><span class="sxs-lookup"><span data-stu-id="cefa8-114">How to Perform Composite Operations on SQL Server</span></span>  
 <span data-ttu-id="cefa8-115">使用 SQL Server 上執行運算[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="cefa8-115">Performing an operation on SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] involves procedural tasks described in [Building blocks to develop BizTalk applications with the SQL adapter](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md).</span></span> <span data-ttu-id="cefa8-116">若要執行複合作業上的 SQL Server 資料庫，這些工作如下：</span><span class="sxs-lookup"><span data-stu-id="cefa8-116">To perform composite operations on the SQL Server database, these tasks are:</span></span>  
  
1. <span data-ttu-id="cefa8-117">建立 BizTalk 專案，並產生您想要叫用的所有作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-117">Create a BizTalk project, and generate schema for all the operations you want to invoke.</span></span>  
  
2. <span data-ttu-id="cefa8-118">以手動方式建立結構描述檔案，其中包含您在上一個步驟中產生的所有結構描述的參考。</span><span class="sxs-lookup"><span data-stu-id="cefa8-118">Manually create a schema file that includes references to all the schemas you generated in the previous step.</span></span>  
  
3. <span data-ttu-id="cefa8-119">建立傳送和接收訊息，從 SQL Server 資料庫的 BizTalk 專案中的訊息。</span><span class="sxs-lookup"><span data-stu-id="cefa8-119">Create messages in the BizTalk project for sending and receiving messages from the SQL Server database.</span></span> <span data-ttu-id="cefa8-120">這些訊息必須符合您在上一個步驟中建立的要求和回應結構描述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-120">These messages must conform to the request and response schema you created in the previous step.</span></span>  
  
4. <span data-ttu-id="cefa8-121">建立協調流程叫用複合作業上的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cefa8-121">Create an orchestration to invoke the composite operation on the SQL Server database.</span></span>  
  
5. <span data-ttu-id="cefa8-122">建置和部署 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="cefa8-122">Build and deploy the BizTalk project.</span></span>  
  
6. <span data-ttu-id="cefa8-123">設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="cefa8-123">Configure the BizTalk application by creating physical send and receive ports.</span></span>  
  
7. <span data-ttu-id="cefa8-124">啟動 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="cefa8-124">Start the BizTalk application.</span></span>  
  
   <span data-ttu-id="cefa8-125">本主題提供有關如何執行這些工作的指示。</span><span class="sxs-lookup"><span data-stu-id="cefa8-125">This topic provides instructions on how to perform these tasks.</span></span>  
  
## <a name="sample-based-on-this-topic"></a><span data-ttu-id="cefa8-126">根據本主題的範例</span><span class="sxs-lookup"><span data-stu-id="cefa8-126">Sample Based on This Topic</span></span>  
 <span data-ttu-id="cefa8-127">，CompositeOperations，根據本主題提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cefa8-127">A sample, CompositeOperations, based on this topic is provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="cefa8-128">如需詳細資訊，請參閱 < [SQL 配接器的範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="cefa8-128">For more information, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span></span>  
  
## <a name="generating-schema"></a><span data-ttu-id="cefa8-129">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="cefa8-129">Generating Schema</span></span>  
 <span data-ttu-id="cefa8-130">本主題中，示範如何執行複合作業，下列工作將會執行指定的順序：</span><span class="sxs-lookup"><span data-stu-id="cefa8-130">In this topic, to demonstrate how to perform composite operations, the following tasks will be performed in the order specified:</span></span>  
  
- <span data-ttu-id="cefa8-131">[員工] 資料表中插入記錄。</span><span class="sxs-lookup"><span data-stu-id="cefa8-131">Insert record into the EMPLOYEE table.</span></span>  
  
- <span data-ttu-id="cefa8-132">藉由叫用 GET_LAST_EMP_DATA 預存程序中擷取最後一個插入的記錄的所有資料的行。</span><span class="sxs-lookup"><span data-stu-id="cefa8-132">Retrieve all the columns for the last inserted record by invoking the GET_LAST_EMP_DATA stored procedure.</span></span>  
  
- <span data-ttu-id="cefa8-133">從 [員工] 資料表中刪除記錄。</span><span class="sxs-lookup"><span data-stu-id="cefa8-133">Delete the record from the EMPLOYEE table.</span></span>  
  
  <span data-ttu-id="cefa8-134">執行指令碼提供範例來建立員工資料表。</span><span class="sxs-lookup"><span data-stu-id="cefa8-134">Run the scripts provided with the samples to create the EMPLOYEE table.</span></span> <span data-ttu-id="cefa8-135">如需有關範例的詳細資訊，請參閱 <<c0> [ 結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="cefa8-135">For more information about the samples, see [Schema Samples](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md).</span></span>  
  
  <span data-ttu-id="cefa8-136">您必須建立 BizTalk 專案，並使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]來產生這些作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-136">You must create a BizTalk project and use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate the schema for these operations.</span></span> <span data-ttu-id="cefa8-137">請參閱[擷取使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-137">See [Retrieving Metadata for SQL Server Operations in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) for more information about how to generate schemas.</span></span>  
  
## <a name="creating-a-composite-schema-definition"></a><span data-ttu-id="cefa8-138">建立複合的結構描述定義</span><span class="sxs-lookup"><span data-stu-id="cefa8-138">Creating a Composite Schema Definition</span></span>  
 <span data-ttu-id="cefa8-139">您現在必須建立複合的結構描述參考您針對個別作業所建立之結構描述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-139">You must now create a composite schema that references the schemas you created for the individual operations.</span></span> <span data-ttu-id="cefa8-140">執行下列步驟來建立複合的結構描述定義。</span><span class="sxs-lookup"><span data-stu-id="cefa8-140">Perform the following steps to create a composite schema definition.</span></span>  
  
#### <a name="to-add-a-composite-schema-definition"></a><span data-ttu-id="cefa8-141">若要新增複合結構描述定義</span><span class="sxs-lookup"><span data-stu-id="cefa8-141">To add a composite schema definition</span></span>  
  
1. <span data-ttu-id="cefa8-142">將結構描述檔案新增至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="cefa8-142">Add a schema file to the BizTalk project.</span></span> <span data-ttu-id="cefa8-143">以滑鼠右鍵按一下專案名稱，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-143">Right-click the project name, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="cefa8-144">在 [**加入新項目**] 對話方塊中，從**分類**方塊中，按一下**結構描述檔案**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-144">In the **Add New Item** dialog box, from the **Categories** box, click **Schema Files**.</span></span> <span data-ttu-id="cefa8-145">從**範本**方塊中，按一下**結構描述**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-145">From the **Templates** box, click **Schema**.</span></span> <span data-ttu-id="cefa8-146">指定結構描述檔案的名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-146">Specify a name for the schema file, and then click **OK**.</span></span>  
  
    <span data-ttu-id="cefa8-147">此範例中，結構描述檔案名稱指定為`CompositeSchema.xsd`。</span><span class="sxs-lookup"><span data-stu-id="cefa8-147">For this example, specify the schema file name as `CompositeSchema.xsd`.</span></span>  
  
2. <span data-ttu-id="cefa8-148">將參考加入至您想要執行之不同作業產生的結構描述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-148">Add references to the schema generated for the different operations that you want to perform.</span></span> <span data-ttu-id="cefa8-149">在此範例中，不同的作業產生的結構描述是：</span><span class="sxs-lookup"><span data-stu-id="cefa8-149">In this example, the different schemas generated for operations are:</span></span>  
  
   - <span data-ttu-id="cefa8-150">TableOperation.dbo.Employee.xsd，Insert 和 Delete 作業。</span><span class="sxs-lookup"><span data-stu-id="cefa8-150">TableOperation.dbo.Employee.xsd, for Insert and Delete operations.</span></span>  
  
   - <span data-ttu-id="cefa8-151">Procedure.dbo.xsd，如 GET_LAST_EMP_DATA 預存程序。</span><span class="sxs-lookup"><span data-stu-id="cefa8-151">Procedure.dbo.xsd, for the GET_LAST_EMP_DATA stored procedure.</span></span>  
  
     <span data-ttu-id="cefa8-152">若要新增的參考：</span><span class="sxs-lookup"><span data-stu-id="cefa8-152">To add references:</span></span>  
  
   1.  <span data-ttu-id="cefa8-153">以滑鼠右鍵按一下根目錄**\<結構描述\>** 節點中 CompositeSchema.xsd，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-153">Right-click the root **\<Schema\>** node in the CompositeSchema.xsd, and click **Properties**.</span></span>  
  
   2.  <span data-ttu-id="cefa8-154">在 **屬性**方塊中，按一下省略符號按鈕 **（...）** 對抗**匯入**屬性。</span><span class="sxs-lookup"><span data-stu-id="cefa8-154">In the **Property** box, click the ellipsis button **(…)** against the **Imports** property.</span></span>  
  
        <span data-ttu-id="cefa8-155">![匯入結構描述定義](../../adapters-and-accelerators/adapter-oracle-database/media/d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca.gif "d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca")</span><span class="sxs-lookup"><span data-stu-id="cefa8-155">![Import schema definitions](../../adapters-and-accelerators/adapter-oracle-database/media/d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca.gif "d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca")</span></span>  
  
   3.  <span data-ttu-id="cefa8-156">在 **匯入** 對話方塊中，從**匯入新結構描述為**清單中，選取**XSD 匯入**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-156">In the **Imports** dialog box, from the **Import new schema as** list, select **XSD Import**, and then click **Add**.</span></span>  
  
   4.  <span data-ttu-id="cefa8-157">在  **BizTalk 型別選擇器**對話方塊方塊中，展開 BizTalk 專案名稱節點，展開**結構描述**，然後選取您要匯入的結構描述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-157">In the **BizTalk Type Picker** dialog box, expand the BizTalk project name node, expand **Schemas**, and then select the schema you want to import.</span></span> <span data-ttu-id="cefa8-158">此範例中，選取 [< BizTalk_project_name >]。TableOperation_dbo_Employee。</span><span class="sxs-lookup"><span data-stu-id="cefa8-158">For this example, select <BizTalk_project_name>.TableOperation_dbo_Employee.</span></span> <span data-ttu-id="cefa8-159">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="cefa8-159">Click **OK**.</span></span>  
  
        <span data-ttu-id="cefa8-160">重複此步驟，匯入 < BizTalk_project_name >。Procedure_dbo 太。</span><span class="sxs-lookup"><span data-stu-id="cefa8-160">Repeat this step to import <BizTalk_project_name>.Procedure_dbo too.</span></span>  
  
   5.  <span data-ttu-id="cefa8-161">在 [**匯入**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-161">In the **Imports** dialog box, click **OK**.</span></span>  
  
3. <span data-ttu-id="cefa8-162">加入根結構描述節點中的兩個子節點。</span><span class="sxs-lookup"><span data-stu-id="cefa8-162">Add two child nodes to the root schema node.</span></span> <span data-ttu-id="cefa8-163">一個子節點對應至要求結構描述，用於執行複合作業。</span><span class="sxs-lookup"><span data-stu-id="cefa8-163">One child node corresponds to the request schema for performing the composite operation.</span></span> <span data-ttu-id="cefa8-164">另一個子節點對應至回應結構描述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-164">The other child node corresponds to the response schema.</span></span> <span data-ttu-id="cefa8-165">對應至要求結構描述的節點可以有任意名稱。</span><span class="sxs-lookup"><span data-stu-id="cefa8-165">The node that corresponds to the request schema can have any name.</span></span> <span data-ttu-id="cefa8-166">對應至回應結構描述的節點必須呼叫 < request_schema_node > 回應。</span><span class="sxs-lookup"><span data-stu-id="cefa8-166">The node that corresponds to the response schema must be called <request_schema_node>Response.</span></span> <span data-ttu-id="cefa8-167">針對此範例中，我們會呼叫要求結構描述節點**要求**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-167">For this example, we will call the request schema node as **Request**.</span></span> <span data-ttu-id="cefa8-168">因此，回應結構描述節點稱為**要求回應**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-168">So, the response schema node is called **RequestResponse**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="cefa8-169">根據預設，**根**節點也會加入至新的結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="cefa8-169">By default, a **Root** node is also added to a new schema file.</span></span> <span data-ttu-id="cefa8-170">您可以重新命名**根**節點，以**要求**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-170">You can rename the **Root** node to **Request**.</span></span> <span data-ttu-id="cefa8-171">若要重新命名節點，以滑鼠右鍵按一下節點名稱，然後按一下**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-171">To rename a node, right-click the node name and click **Rename**.</span></span>  
  
    <span data-ttu-id="cefa8-172">若要新增下的一個節點**\<結構描述\>** 節點：</span><span class="sxs-lookup"><span data-stu-id="cefa8-172">To add a node under the **\<Schema\>** node:</span></span>  
  
   1.  <span data-ttu-id="cefa8-173">以滑鼠右鍵按一下**\<結構描述\>** 節點，指向**插入結構描述節點**，然後按一下**子記錄**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-173">Right-click the **\<Schema\>** node, point to **Insert Schema Node**, and click **Child Record**.</span></span>  
  
   2.  <span data-ttu-id="cefa8-174">重新命名新節點**要求回應**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-174">Rename the new node to **RequestResponse**.</span></span>  
  
4. <span data-ttu-id="cefa8-175">新增子節點底下**要求**對應至複合作業的一部分，您將會執行每個作業的要求結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="cefa8-175">Add child nodes under the **Request** node that correspond to the request schema for each operation that you will perform as part of the composite operation.</span></span> <span data-ttu-id="cefa8-176">此範例中，您必須新增對應於下列子節點：</span><span class="sxs-lookup"><span data-stu-id="cefa8-176">For this example, you must add child nodes corresponding to the following:</span></span>  
  
   -   <span data-ttu-id="cefa8-177">插入和刪除員工資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="cefa8-177">Insert and Delete operations on the EMPLOYEE table.</span></span>  
  
   -   <span data-ttu-id="cefa8-178">GET_LAST_EMP_DATA 預存程序。</span><span class="sxs-lookup"><span data-stu-id="cefa8-178">GET_LAST_EMP_DATA stored procedure.</span></span>  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="cefa8-179">您必須將節點新增您要在其中執行作業的順序相同。</span><span class="sxs-lookup"><span data-stu-id="cefa8-179">You must add the nodes in the same order in which you want to perform the operations.</span></span> <span data-ttu-id="cefa8-180">例如，如果您想要插入一筆記錄，執行預存程序，然後再刪除記錄，您必須先新增插入作業的節點，後面接著節點預存程序，和最後一個節點的刪除作業。</span><span class="sxs-lookup"><span data-stu-id="cefa8-180">For example, if you want to insert a record, then execute a stored procedure, and then delete a record you must first add a node for the Insert operation, followed by a node for the stored procedure, and finally a node for the Delete operation.</span></span>  
  
    <span data-ttu-id="cefa8-181">若要將子節點，即可**要求**節點：</span><span class="sxs-lookup"><span data-stu-id="cefa8-181">To add child nodes to the **Request** node:</span></span>  
  
   1.  <span data-ttu-id="cefa8-182">以滑鼠右鍵按一下**要求**節點，指向**插入結構描述節點**，然後按一下**子記錄**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-182">Right-click the **Request** node, point to **Insert Schema Node**, and then click  **Child Record**.</span></span>  
  
        <span data-ttu-id="cefa8-183">![插入子節點的結構描述](../../adapters-and-accelerators/adapter-oracle-database/media/58992131-13a6-45c3-9513-5c0995091fae.gif "58992131-13a6-45c3-9513-5c0995091fae")</span><span class="sxs-lookup"><span data-stu-id="cefa8-183">![Insert child nodes for a schema](../../adapters-and-accelerators/adapter-oracle-database/media/58992131-13a6-45c3-9513-5c0995091fae.gif "58992131-13a6-45c3-9513-5c0995091fae")</span></span>  
  
   2.  <span data-ttu-id="cefa8-184">重新命名的記錄以對應至您為複合作業的一部分執行的作業的要求結構描述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-184">Rename the record to correspond to a request schema for an operation that you perform as part of the composite operation.</span></span> <span data-ttu-id="cefa8-185">例如，重新命名的節點"Insert"。</span><span class="sxs-lookup"><span data-stu-id="cefa8-185">For example, rename the node to “Insert”.</span></span>  
  
   3.  <span data-ttu-id="cefa8-186">地圖**插入**EMPLOYEE 資料表的 Insert 作業的要求結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="cefa8-186">Map the **Insert** node to the request schema for the Insert operation on the EMPLOYEE table.</span></span> <span data-ttu-id="cefa8-187">若要這樣做，請以滑鼠右鍵按一下**插入**節點，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-187">To do so, right-click the **Insert** node, and click **Properties**.</span></span> <span data-ttu-id="cefa8-188">在 [**屬性**] 方塊中，從**資料結構型別**清單中，選取**Insert （參考）**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-188">In the **Properties** box, from the **Data Structure Type** list, select **Insert (Reference)**.</span></span>  
  
        <span data-ttu-id="cefa8-189">![將子節點對應至要求結構描述](../../adapters-and-accelerators/adapter-sql/media/5ace18be-0fe8-44c6-bd2f-cb19035494b5.gif "5ace18be-0fe8-44c6-bd2f-cb19035494b5")</span><span class="sxs-lookup"><span data-stu-id="cefa8-189">![Map child nodes to the request schema](../../adapters-and-accelerators/adapter-sql/media/5ace18be-0fe8-44c6-bd2f-cb19035494b5.gif "5ace18be-0fe8-44c6-bd2f-cb19035494b5")</span></span>  
  
   4.  <span data-ttu-id="cefa8-190">重複這些步驟來加入 GET_LAST_EMP_DATA 預存程序和刪除作業的要求結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="cefa8-190">Repeat these steps to add nodes for the request schemas for GET_LAST_EMP_DATA stored procedure and the Delete operation.</span></span> <span data-ttu-id="cefa8-191">指定節點名稱，然後將它們對應到對應的結構描述，如下列表格中所述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-191">Specify the node names and map them to the corresponding schema as mentioned in the following table.</span></span>  
  
       |<span data-ttu-id="cefa8-192">節點名稱</span><span class="sxs-lookup"><span data-stu-id="cefa8-192">Node name</span></span>|<span data-ttu-id="cefa8-193">對應至結構描述</span><span class="sxs-lookup"><span data-stu-id="cefa8-193">Mapped to schema</span></span>|  
       |---------------|----------------------|  
       |<span data-ttu-id="cefa8-194">GET_LAST_EMP_DATA</span><span class="sxs-lookup"><span data-stu-id="cefa8-194">GET_LAST_EMP_DATA</span></span>|<span data-ttu-id="cefa8-195">GET_LAST_EMP_DATA （參考）</span><span class="sxs-lookup"><span data-stu-id="cefa8-195">GET_LAST_EMP_DATA (Reference)</span></span>|  
       |<span data-ttu-id="cefa8-196">DELETE</span><span class="sxs-lookup"><span data-stu-id="cefa8-196">Delete</span></span>|<span data-ttu-id="cefa8-197">刪除 （參考）</span><span class="sxs-lookup"><span data-stu-id="cefa8-197">Delete (Reference)</span></span>|  
  
5. <span data-ttu-id="cefa8-198">新增子節點底下**要求回應**對應至複合作業的一部分，您將會執行每個作業的回應結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="cefa8-198">Add child nodes under the **RequestResponse** node that correspond to the response schema for each operation that you will perform as part of the composite operation.</span></span> <span data-ttu-id="cefa8-199">此範例中，您必須新增對應於下列子節點：</span><span class="sxs-lookup"><span data-stu-id="cefa8-199">For this example, you must add child nodes corresponding to the following:</span></span>  
  
   -   <span data-ttu-id="cefa8-200">插入和刪除員工資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="cefa8-200">Insert and Delete operations on the EMPLOYEE table.</span></span>  
  
   -   <span data-ttu-id="cefa8-201">GET_LAST_EMP_DATA 預存程序。</span><span class="sxs-lookup"><span data-stu-id="cefa8-201">GET_LAST_EMP_DATA stored procedure.</span></span>  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="cefa8-202">您必須新增子節點底下的子節點順序相同**要求**節點。</span><span class="sxs-lookup"><span data-stu-id="cefa8-202">You must add the child nodes in the same order as the child nodes under the **Request** node.</span></span>  
  
    <span data-ttu-id="cefa8-203">若要將子節點，即可**要求回應**節點：</span><span class="sxs-lookup"><span data-stu-id="cefa8-203">To add child nodes to the **RequestResponse** node:</span></span>  
  
   1.  <span data-ttu-id="cefa8-204">以滑鼠右鍵按一下**要求回應**節點，指向**插入結構描述節點**，然後按一下**子記錄**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-204">Right-click the **RequestResponse** node, point to **Insert Schema Node**, and click **Child Record**.</span></span>  
  
   2.  <span data-ttu-id="cefa8-205">重新命名的記錄以對應至您為複合作業的一部分執行的作業的回應結構描述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-205">Rename the record to correspond to a response schema for an operation that you perform as part of the composite operation.</span></span> <span data-ttu-id="cefa8-206">例如，重新命名 「 InsertResponse"的節點。</span><span class="sxs-lookup"><span data-stu-id="cefa8-206">For example, rename the node to “InsertResponse”.</span></span>  
  
   3.  <span data-ttu-id="cefa8-207">地圖**InsertResponse** EMPLOYEE 資料表的 Insert 作業的回應結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="cefa8-207">Map the **InsertResponse** node to the response schema for the Insert operation on the EMPLOYEE table.</span></span> <span data-ttu-id="cefa8-208">若要這樣做，請以滑鼠右鍵按一下**InsertResponse**節點，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-208">To do so, right-click the **InsertResponse** node, and click **Properties**.</span></span> <span data-ttu-id="cefa8-209">在 [**屬性**] 方塊中，從**資料結構型別**清單中，選取**InsertResponse （參考）**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-209">In the **Properties** box, from the **Data Structure Type** list, select **InsertResponse (Reference)**.</span></span>  
  
   4.  <span data-ttu-id="cefa8-210">重複這些步驟來加入 GET_LAST_EMP_DATA 預存程序和刪除作業的回應結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="cefa8-210">Repeat these steps to add nodes for the response schemas for the GET_LAST_EMP_DATA stored procedure and the Delete operation.</span></span> <span data-ttu-id="cefa8-211">指定節點名稱，然後將它們對應到對應的結構描述，如下列表格中所述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-211">Specify the node names and map them to the corresponding schema as mentioned in the following table.</span></span>  
  
       |<span data-ttu-id="cefa8-212">節點名稱</span><span class="sxs-lookup"><span data-stu-id="cefa8-212">Node name</span></span>|<span data-ttu-id="cefa8-213">對應至結構描述</span><span class="sxs-lookup"><span data-stu-id="cefa8-213">Mapped to schema</span></span>|  
       |---------------|----------------------|  
       |<span data-ttu-id="cefa8-214">GET_LAST_EMP_DATAResponse</span><span class="sxs-lookup"><span data-stu-id="cefa8-214">GET_LAST_EMP_DATAResponse</span></span>|<span data-ttu-id="cefa8-215">GET_LAST_EMP_DATAResponse （參考）</span><span class="sxs-lookup"><span data-stu-id="cefa8-215">GET_LAST_EMP_DATAResponse (Reference)</span></span>|  
       |<span data-ttu-id="cefa8-216">DeleteResponse</span><span class="sxs-lookup"><span data-stu-id="cefa8-216">DeleteResponse</span></span>|<span data-ttu-id="cefa8-217">DeleteResponse （參考）</span><span class="sxs-lookup"><span data-stu-id="cefa8-217">DeleteResponse (Reference)</span></span>|  
  
6. <span data-ttu-id="cefa8-218">儲存**CompositeSchema.xsd**檔案。</span><span class="sxs-lookup"><span data-stu-id="cefa8-218">Save the **CompositeSchema.xsd** file.</span></span>  
  
## <a name="defining-messages-and-message-types"></a><span data-ttu-id="cefa8-219">定義訊息和訊息類型</span><span class="sxs-lookup"><span data-stu-id="cefa8-219">Defining Messages and Message Types</span></span>  
 <span data-ttu-id="cefa8-220">您在最後一個步驟中建立的複合結構描述會描述協調流程中的訊息所需的 「 類型 」。</span><span class="sxs-lookup"><span data-stu-id="cefa8-220">The composite schema that you created in the last step describes the “types” required for the messages in an orchestration.</span></span> <span data-ttu-id="cefa8-221">訊息通常是一個變數，要為其類型會定義對應的結構。</span><span class="sxs-lookup"><span data-stu-id="cefa8-221">A message is typically a variable, the type for which is defined by the corresponding schema.</span></span> <span data-ttu-id="cefa8-222">現在，您必須建立協調流程的訊息，並將它們連結至您在上一個步驟中建立的結構描述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-222">You must now create messages for the orchestration and link them to schema you created in the previous step.</span></span>  
  
#### <a name="to-create-messages-and-link-to-schema"></a><span data-ttu-id="cefa8-223">若要建立訊息，並連結至結構描述</span><span class="sxs-lookup"><span data-stu-id="cefa8-223">To create messages and link to schema</span></span>  
  
1.  <span data-ttu-id="cefa8-224">BizTalk 專案中新增協調流程。</span><span class="sxs-lookup"><span data-stu-id="cefa8-224">Add an orchestration to the BizTalk project.</span></span> <span data-ttu-id="cefa8-225">從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-225">From Solution Explorer, right-click the BizTalk project name, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="cefa8-226">輸入 BizTalk 協調流程的名稱，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-226">Type a name for the BizTalk orchestration, and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="cefa8-227">如果它尚未開啟，請開啟 BizTalk 專案，[協調流程檢視] 視窗。</span><span class="sxs-lookup"><span data-stu-id="cefa8-227">Open the Orchestration View window of the BizTalk project, if it is not already open.</span></span> <span data-ttu-id="cefa8-228">若要這樣做，請按一下**檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-228">To do so, click **View**, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
3.  <span data-ttu-id="cefa8-229">在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-229">In Orchestration View, right-click **Messages**, and then click **New Message**.</span></span>  
  
4.  <span data-ttu-id="cefa8-230">以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-230">Right-click the newly created message, and then select **Properties Window**.</span></span>  
  
5.  <span data-ttu-id="cefa8-231">在 [**屬性**] 窗格**Message_1**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cefa8-231">In the **Properties** pane for the **Message_1**, do the following:</span></span>  
  
    |<span data-ttu-id="cefa8-232">使用</span><span class="sxs-lookup"><span data-stu-id="cefa8-232">Use this</span></span>|<span data-ttu-id="cefa8-233">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cefa8-233">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="cefa8-234">識別碼</span><span class="sxs-lookup"><span data-stu-id="cefa8-234">Identifier</span></span>|<span data-ttu-id="cefa8-235">輸入 `Request`</span><span class="sxs-lookup"><span data-stu-id="cefa8-235">Type `Request`</span></span>|  
    |<span data-ttu-id="cefa8-236">訊息類型</span><span class="sxs-lookup"><span data-stu-id="cefa8-236">Message Type</span></span>|<span data-ttu-id="cefa8-237">從下拉式清單中，依序展開**結構描述**，然後選取*CompositeOp.CompositeSchema.Request*CompositeOp 所在的 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="cefa8-237">From the drop-down list, expand **Schemas**, and then select *CompositeOp.CompositeSchema.Request*, where CompositeOp is the name of your BizTalk project.</span></span> <span data-ttu-id="cefa8-238">CompositeSchema 是手動建立複合作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-238">CompositeSchema is the schema you created manually for the composite operations.</span></span>|  
  
6.  <span data-ttu-id="cefa8-239">重複步驟 2 來建立新的訊息。</span><span class="sxs-lookup"><span data-stu-id="cefa8-239">Repeat step 2 to create a new message.</span></span> <span data-ttu-id="cefa8-240">在 **屬性**窗格中的新訊息，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cefa8-240">In the **Properties** pane for the new message, do the following:</span></span>  
  
    |<span data-ttu-id="cefa8-241">使用</span><span class="sxs-lookup"><span data-stu-id="cefa8-241">Use this</span></span>|<span data-ttu-id="cefa8-242">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cefa8-242">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="cefa8-243">識別碼</span><span class="sxs-lookup"><span data-stu-id="cefa8-243">Identifier</span></span>|<span data-ttu-id="cefa8-244">輸入 `Response`</span><span class="sxs-lookup"><span data-stu-id="cefa8-244">Type `Response`</span></span>|  
    |<span data-ttu-id="cefa8-245">訊息類型</span><span class="sxs-lookup"><span data-stu-id="cefa8-245">Message Type</span></span>|<span data-ttu-id="cefa8-246">從下拉式清單中，依序展開**結構描述**，然後選取*CompositeOp.CompositeSchema.RequestResponse*。</span><span class="sxs-lookup"><span data-stu-id="cefa8-246">From the drop-down list, expand **Schemas**, and then select *CompositeOp.CompositeSchema.RequestResponse*.</span></span>|  
  
## <a name="setting-up-the-orchestration"></a><span data-ttu-id="cefa8-247">設定協調流程</span><span class="sxs-lookup"><span data-stu-id="cefa8-247">Setting up the Orchestration</span></span>  
 <span data-ttu-id="cefa8-248">您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行 SQL Server 上的複合作業。</span><span class="sxs-lookup"><span data-stu-id="cefa8-248">You must create a BizTalk orchestration to use [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for performing composite operations on SQL Server.</span></span> <span data-ttu-id="cefa8-249">在此協調流程中，卸除在要求訊息定義的接收位置。</span><span class="sxs-lookup"><span data-stu-id="cefa8-249">In this orchestration, you drop a request message at a defined receive location.</span></span> <span data-ttu-id="cefa8-250">要求訊息必須符合您稍早建立的複合結構描述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-250">The request message must conform to the composite schema you created earlier.</span></span> <span data-ttu-id="cefa8-251">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會取用這個訊息，並將它傳遞到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="cefa8-251">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] consumes this message and passes it on to SQL Server.</span></span> <span data-ttu-id="cefa8-252">從 SQL Server 的回應會儲存到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="cefa8-252">The response from SQL Server is saved to another location.</span></span> <span data-ttu-id="cefa8-253">您必須包含傳送和接收圖形，將訊息傳送至 SQL Server，並接收回應，分別。</span><span class="sxs-lookup"><span data-stu-id="cefa8-253">You must include Send and Receive shapes to send messages to SQL Server and receive responses, respectively.</span></span> <span data-ttu-id="cefa8-254">用於執行複合作業的基本協調流程如下所示：</span><span class="sxs-lookup"><span data-stu-id="cefa8-254">A basic orchestration for performing composite operations resembles the following:</span></span>  
  
 <span data-ttu-id="cefa8-255">![用於執行複合操作的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb.gif "4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb")</span><span class="sxs-lookup"><span data-stu-id="cefa8-255">![Orchestration to peform composite operations](../../adapters-and-accelerators/adapter-oracle-database/media/4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb.gif "4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb")</span></span>  
  
### <a name="adding-message-shapes"></a><span data-ttu-id="cefa8-256">新增訊息圖形</span><span class="sxs-lookup"><span data-stu-id="cefa8-256">Adding Message Shapes</span></span>  
 <span data-ttu-id="cefa8-257">請確定您針對每個訊息 圖形中指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="cefa8-257">Make sure you specify the following properties for each of the message shapes.</span></span> <span data-ttu-id="cefa8-258">剛剛提到的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。</span><span class="sxs-lookup"><span data-stu-id="cefa8-258">The names listed in the Shape column are the names of the message shapes as displayed in the just-mentioned orchestration.</span></span>  
  
|<span data-ttu-id="cefa8-259">形狀圖</span><span class="sxs-lookup"><span data-stu-id="cefa8-259">Shape</span></span>|<span data-ttu-id="cefa8-260">圖形類型</span><span class="sxs-lookup"><span data-stu-id="cefa8-260">Shape Type</span></span>|<span data-ttu-id="cefa8-261">屬性</span><span class="sxs-lookup"><span data-stu-id="cefa8-261">Properties</span></span>|  
|-----------|----------------|----------------|  
|<span data-ttu-id="cefa8-262">ReceiveMessage</span><span class="sxs-lookup"><span data-stu-id="cefa8-262">ReceiveMessage</span></span>|<span data-ttu-id="cefa8-263">Receive</span><span class="sxs-lookup"><span data-stu-id="cefa8-263">Receive</span></span>|<span data-ttu-id="cefa8-264">-設定**名稱**到*ReceiveMessage*</span><span class="sxs-lookup"><span data-stu-id="cefa8-264">-   Set **Name** to *ReceiveMessage*</span></span><br /><span data-ttu-id="cefa8-265">-設定**啟用**到 *，則為 True*</span><span class="sxs-lookup"><span data-stu-id="cefa8-265">-   Set **Activate** to *True*</span></span>|  
|<span data-ttu-id="cefa8-266">SendMessage</span><span class="sxs-lookup"><span data-stu-id="cefa8-266">SendMessage</span></span>|<span data-ttu-id="cefa8-267">Send</span><span class="sxs-lookup"><span data-stu-id="cefa8-267">Send</span></span>|<span data-ttu-id="cefa8-268">-設定**名稱**到*SendMessage*</span><span class="sxs-lookup"><span data-stu-id="cefa8-268">-   Set **Name** to *SendMessage*</span></span>|  
|<span data-ttu-id="cefa8-269">ReceiveResponse</span><span class="sxs-lookup"><span data-stu-id="cefa8-269">ReceiveResponse</span></span>|<span data-ttu-id="cefa8-270">Receive</span><span class="sxs-lookup"><span data-stu-id="cefa8-270">Receive</span></span>|<span data-ttu-id="cefa8-271">-設定**名稱**到*ReceiveResponse*</span><span class="sxs-lookup"><span data-stu-id="cefa8-271">-   Set **Name** to *ReceiveResponse*</span></span><br /><span data-ttu-id="cefa8-272">-設定**啟用**到*False*</span><span class="sxs-lookup"><span data-stu-id="cefa8-272">-   Set **Activate** to *False*</span></span>|  
|<span data-ttu-id="cefa8-273">SendResponse</span><span class="sxs-lookup"><span data-stu-id="cefa8-273">SendResponse</span></span>|<span data-ttu-id="cefa8-274">Send</span><span class="sxs-lookup"><span data-stu-id="cefa8-274">Send</span></span>|<span data-ttu-id="cefa8-275">-設定**名稱**到*SendResponse*</span><span class="sxs-lookup"><span data-stu-id="cefa8-275">-   Set **Name** to *SendResponse*</span></span>|  
  
### <a name="adding-ports"></a><span data-ttu-id="cefa8-276">新增連接埠</span><span class="sxs-lookup"><span data-stu-id="cefa8-276">Adding Ports</span></span>  
 <span data-ttu-id="cefa8-277">請確定您針對每個邏輯連接埠中指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="cefa8-277">Make sure you specify the following properties for each of the logical ports.</span></span> <span data-ttu-id="cefa8-278">協調流程中所示，連接埠資料行中所列的名稱會是連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="cefa8-278">The names listed in the Port column are the names of the ports as displayed in the orchestration.</span></span>  
  
|<span data-ttu-id="cefa8-279">通訊埠</span><span class="sxs-lookup"><span data-stu-id="cefa8-279">Port</span></span>|<span data-ttu-id="cefa8-280">屬性</span><span class="sxs-lookup"><span data-stu-id="cefa8-280">Properties</span></span>|  
|----------|----------------|  
|<span data-ttu-id="cefa8-281">MessageIn</span><span class="sxs-lookup"><span data-stu-id="cefa8-281">MessageIn</span></span>|<span data-ttu-id="cefa8-282">-設定**識別碼**到*MessageIn*</span><span class="sxs-lookup"><span data-stu-id="cefa8-282">-   Set **Identifier** to *MessageIn*</span></span><br /><span data-ttu-id="cefa8-283">-設定**型別**到*MessageInType*</span><span class="sxs-lookup"><span data-stu-id="cefa8-283">-   Set **Type** to *MessageInType*</span></span><br /><span data-ttu-id="cefa8-284">-設定**通訊模式**到*單向*</span><span class="sxs-lookup"><span data-stu-id="cefa8-284">-   Set **Communication Pattern** to *One-Way*</span></span><br /><span data-ttu-id="cefa8-285">-設定**通訊方向**到*接收*</span><span class="sxs-lookup"><span data-stu-id="cefa8-285">-   Set **Communication Direction** to *Receive*</span></span>|  
|<span data-ttu-id="cefa8-286">LOBPort</span><span class="sxs-lookup"><span data-stu-id="cefa8-286">LOBPort</span></span>|<span data-ttu-id="cefa8-287">-設定**識別碼**到*LOBPort*</span><span class="sxs-lookup"><span data-stu-id="cefa8-287">-   Set **Identifier** to *LOBPort*</span></span><br /><span data-ttu-id="cefa8-288">-設定**型別**到*LOBPortType*</span><span class="sxs-lookup"><span data-stu-id="cefa8-288">-   Set **Type** to *LOBPortType*</span></span><br /><span data-ttu-id="cefa8-289">-設定**通訊模式**到*要求-回應*</span><span class="sxs-lookup"><span data-stu-id="cefa8-289">-   Set **Communication Pattern** to *Request-Response*</span></span><br /><span data-ttu-id="cefa8-290">-設定**通訊方向**到*傳送接收*</span><span class="sxs-lookup"><span data-stu-id="cefa8-290">-   Set **Communication Direction** to *Send-Receive*</span></span>|  
|<span data-ttu-id="cefa8-291">ResponseOut</span><span class="sxs-lookup"><span data-stu-id="cefa8-291">ResponseOut</span></span>|<span data-ttu-id="cefa8-292">-設定**識別碼**到*ResponseOut*</span><span class="sxs-lookup"><span data-stu-id="cefa8-292">-   Set **Identifier** to *ResponseOut*</span></span><br /><span data-ttu-id="cefa8-293">-設定**型別**到*ResponseOutType*</span><span class="sxs-lookup"><span data-stu-id="cefa8-293">-   Set **Type** to *ResponseOutType*</span></span><br /><span data-ttu-id="cefa8-294">-設定**通訊模式**到*單向*</span><span class="sxs-lookup"><span data-stu-id="cefa8-294">-   Set **Communication Pattern** to *One-Way*</span></span><br /><span data-ttu-id="cefa8-295">-設定**通訊方向**到*傳送*</span><span class="sxs-lookup"><span data-stu-id="cefa8-295">-   Set **Communication Direction** to *Send*</span></span>|  
  
### <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a><span data-ttu-id="cefa8-296">為動作圖形指定訊息，並將其連接至連接埠</span><span class="sxs-lookup"><span data-stu-id="cefa8-296">Specify Messages for Action Shapes, and Connect Them to Ports</span></span>  
 <span data-ttu-id="cefa8-297">下表指定的屬性和屬性來指定動作圖形的訊息，以及連結至連接埠的訊息，您應該設定的值。</span><span class="sxs-lookup"><span data-stu-id="cefa8-297">The following table specifies the properties and their values that you should set to specify messages for action shapes and to link the messages to the ports.</span></span> <span data-ttu-id="cefa8-298">先前所述的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。</span><span class="sxs-lookup"><span data-stu-id="cefa8-298">The names listed in the Shape column are the names of the message shapes as displayed in the orchestration mentioned earlier.</span></span>  
  
|<span data-ttu-id="cefa8-299">形狀圖</span><span class="sxs-lookup"><span data-stu-id="cefa8-299">Shape</span></span>|<span data-ttu-id="cefa8-300">屬性</span><span class="sxs-lookup"><span data-stu-id="cefa8-300">Properties</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="cefa8-301">ReceiveMessage</span><span class="sxs-lookup"><span data-stu-id="cefa8-301">ReceiveMessage</span></span>|<span data-ttu-id="cefa8-302">-設定**訊息**到*要求*</span><span class="sxs-lookup"><span data-stu-id="cefa8-302">-   Set **Message** to *Request*</span></span><br /><span data-ttu-id="cefa8-303">-設定**作業**到*MessageIn.CompositeOp.Request*</span><span class="sxs-lookup"><span data-stu-id="cefa8-303">-   Set **Operation** to *MessageIn.CompositeOp.Request*</span></span>|  
|<span data-ttu-id="cefa8-304">SendMessage</span><span class="sxs-lookup"><span data-stu-id="cefa8-304">SendMessage</span></span>|<span data-ttu-id="cefa8-305">-設定**訊息**到*要求*</span><span class="sxs-lookup"><span data-stu-id="cefa8-305">-   Set **Message** to *Request*</span></span><br /><span data-ttu-id="cefa8-306">-設定**作業**到*LOBPort.CompositeOp.Request*</span><span class="sxs-lookup"><span data-stu-id="cefa8-306">-   Set **Operation** to *LOBPort.CompositeOp.Request*</span></span>|  
|<span data-ttu-id="cefa8-307">ReceiveResponse</span><span class="sxs-lookup"><span data-stu-id="cefa8-307">ReceiveResponse</span></span>|<span data-ttu-id="cefa8-308">-設定**訊息**到*回應*</span><span class="sxs-lookup"><span data-stu-id="cefa8-308">-   Set **Message** to *Response*</span></span><br /><span data-ttu-id="cefa8-309">-設定**作業**到*LOBPort.CompositeOp.Response*</span><span class="sxs-lookup"><span data-stu-id="cefa8-309">-   Set **Operation** to *LOBPort.CompositeOp.Response*</span></span>|  
|<span data-ttu-id="cefa8-310">SendResponse</span><span class="sxs-lookup"><span data-stu-id="cefa8-310">SendResponse</span></span>|<span data-ttu-id="cefa8-311">-設定**訊息**到*回應*</span><span class="sxs-lookup"><span data-stu-id="cefa8-311">-   Set **Message** to *Response*</span></span><br /><span data-ttu-id="cefa8-312">-設定**作業**到*ResponseOut.CompositeOp.Request*</span><span class="sxs-lookup"><span data-stu-id="cefa8-312">-   Set **Operation** to *ResponseOut.CompositeOp.Request*</span></span>|  
  
 <span data-ttu-id="cefa8-313">您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。</span><span class="sxs-lookup"><span data-stu-id="cefa8-313">After you have specified these properties, the message shapes and ports are connected and your orchestration is complete.</span></span>  
  
 <span data-ttu-id="cefa8-314">您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cefa8-314">You must now build the BizTalk solution and deploy it to a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="cefa8-315">如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="cefa8-315">For more information, see [Building and Running Orchestrations](../../core/building-and-running-orchestrations.md).</span></span>
  
## <a name="configuring-the-biztalk-application"></a><span data-ttu-id="cefa8-316">設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="cefa8-316">Configuring the BizTalk Application</span></span>  
 <span data-ttu-id="cefa8-317">您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在 [協調流程] 窗格底下[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="cefa8-317">After you have deployed the BizTalk project, the orchestration you created earlier is listed under the Orchestrations pane in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="cefa8-318">您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="cefa8-318">You must use the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to configure the application.</span></span> <span data-ttu-id="cefa8-319">如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。</span><span class="sxs-lookup"><span data-stu-id="cefa8-319">For a walkthrough, see [Walkthrough: Deploying a Basic BizTalk Application](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).</span></span>
  
 <span data-ttu-id="cefa8-320">設定應用程式包含：</span><span class="sxs-lookup"><span data-stu-id="cefa8-320">Configuring an application involves:</span></span>  
  
- <span data-ttu-id="cefa8-321">選取應用程式主機。</span><span class="sxs-lookup"><span data-stu-id="cefa8-321">Selecting a host for the application.</span></span>  
  
- <span data-ttu-id="cefa8-322">對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="cefa8-322">Mapping the ports that you created in your orchestration to physical ports in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="cefa8-323">此協調流程中，您必須：</span><span class="sxs-lookup"><span data-stu-id="cefa8-323">For this orchestration you must:</span></span>  
  
  - <span data-ttu-id="cefa8-324">定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息。</span><span class="sxs-lookup"><span data-stu-id="cefa8-324">Define a location on the hard disk and a corresponding file port where you will drop a request message.</span></span> <span data-ttu-id="cefa8-325">BizTalk 協調流程將會取用的要求訊息，並將它傳送到 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cefa8-325">The BizTalk orchestration will consume the request message and send it to the SQL Server database.</span></span>  
  
  - <span data-ttu-id="cefa8-326">定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 SQL Server 資料庫回應的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="cefa8-326">Define a location on the hard disk and a corresponding file port where the BizTalk orchestration will drop the response message containing the response from the SQL Server database.</span></span>  
  
  - <span data-ttu-id="cefa8-327">定義實體 Wcf-custom 或 WCF SQL 傳送埠將訊息傳送至 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cefa8-327">Define a physical WCF-Custom or WCF-SQL send port to send messages to the SQL Server database.</span></span> <span data-ttu-id="cefa8-328">因為作業是在單一交易中，執行複合作業的一部分，以確定**UseAmbientTransaction**繫結屬性設定為 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="cefa8-328">Because the operations that are being as part of the composite operation are executed in a single transaction, make sure the **UseAmbientTransaction** binding property is set to **True**.</span></span>  
  
     <span data-ttu-id="cefa8-329">您也必須在傳送埠中指定的動作。</span><span class="sxs-lookup"><span data-stu-id="cefa8-329">You must also specify the action in the send port.</span></span> <span data-ttu-id="cefa8-330">複合作業的動作是 「**CompositeOperation**"。</span><span class="sxs-lookup"><span data-stu-id="cefa8-330">The action for a composite operation is “**CompositeOperation**”.</span></span> <span data-ttu-id="cefa8-331">如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="cefa8-331">For information about how to create ports, see [Manually configure a physical port binding to the SQL adapter](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md).</span></span> <span data-ttu-id="cefa8-332">如需如何指定連接埠動作的詳細資訊，請參閱[設定 SQL 配接器的 SOAP 動作](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="cefa8-332">For more information about how to specify actions for ports, see [Configure the SOAP action for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md).</span></span>
  
    > [!NOTE]
    >  <span data-ttu-id="cefa8-333">產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立繫結檔案，其中包含連接埠與那些連接埠設定動作的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cefa8-333">Generating the schema using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] also creates a binding file that contains information about the ports and the actions to be set for those ports.</span></span> <span data-ttu-id="cefa8-334">您可以將從這個繫結檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫）。</span><span class="sxs-lookup"><span data-stu-id="cefa8-334">You can import this binding file from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create send ports (for outbound calls) or receive ports (for inbound calls).</span></span> <span data-ttu-id="cefa8-335">如需詳細資訊，請參閱 <<c0> [ 設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="cefa8-335">For more information, see [Configure a physical port binding using a port binding file to use the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).</span></span> <span data-ttu-id="cefa8-336">如果您匯入此繫結檔案，在 WCF 自訂] 或 [WCF-SQL 傳送連接埠上的動作會設定為與您在選取的所有作業都有關的動態動作[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述時。</span><span class="sxs-lookup"><span data-stu-id="cefa8-336">If you import this binding file, the action on the WCF-Custom or WCF-SQL send port is set to a dynamic action involving all the operations you selected in the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] while generating the schema.</span></span> <span data-ttu-id="cefa8-337">複合作業中，您必須取代"CompositeOperation 」 的動態動作。</span><span class="sxs-lookup"><span data-stu-id="cefa8-337">For a composite operation, you must replace the dynamic action with “CompositeOperation”.</span></span>  
  
## <a name="starting-the-application"></a><span data-ttu-id="cefa8-338">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="cefa8-338">Starting the Application</span></span>  
 <span data-ttu-id="cefa8-339">您必須啟動 BizTalk 應用程式來執行 SQL Server 資料庫上的複合作業。</span><span class="sxs-lookup"><span data-stu-id="cefa8-339">You must start the BizTalk application for performing composite operations on the SQL Server database.</span></span> <span data-ttu-id="cefa8-340">如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="cefa8-340">For instructions on starting a BizTalk application, see [How to Start an Orchestration](../../core/how-to-start-an-orchestration.md).</span></span>
  
 <span data-ttu-id="cefa8-341">在這個階段，請確定：</span><span class="sxs-lookup"><span data-stu-id="cefa8-341">At this stage, make sure:</span></span>  
  
-   <span data-ttu-id="cefa8-342">FILE 接收埠以接收要求訊息的協調流程正在執行。</span><span class="sxs-lookup"><span data-stu-id="cefa8-342">The FILE receive port to receive request messages for the orchestration is running.</span></span>  
  
-   <span data-ttu-id="cefa8-343">FILE 傳送埠，以接收回應訊息從協調流程正在執行。</span><span class="sxs-lookup"><span data-stu-id="cefa8-343">The FILE send port to receive the response messages from the orchestration is running.</span></span>  
  
-   <span data-ttu-id="cefa8-344">WCF 自訂] 或 [WCF-SQL 傳送埠將訊息傳送至 SQL Server 資料庫正在執行。</span><span class="sxs-lookup"><span data-stu-id="cefa8-344">The WCF-Custom or WCF-SQL send port to send messages to the SQL Server database is running.</span></span>  
  
-   <span data-ttu-id="cefa8-345">BizTalk 協調流程的作業正在執行。</span><span class="sxs-lookup"><span data-stu-id="cefa8-345">The BizTalk orchestration for the operation is running.</span></span>  
  
## <a name="executing-the-operation"></a><span data-ttu-id="cefa8-346">執行作業</span><span class="sxs-lookup"><span data-stu-id="cefa8-346">Executing the Operation</span></span>  
 <span data-ttu-id="cefa8-347">執行應用程式之後，您必須先卸除要求訊息至檔案接收位置。</span><span class="sxs-lookup"><span data-stu-id="cefa8-347">After you run the application, you must drop a request message to the FILE receive location.</span></span> <span data-ttu-id="cefa8-348">要求訊息的結構描述必須符合您稍早建立的複合作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="cefa8-348">The schema for the request message must conform to the schema for the composite operations you created earlier.</span></span> <span data-ttu-id="cefa8-349">例如，[員工] 資料表中插入記錄、 叫用 GET_LAST_EMP_DATA 預存程序中，並從 [員工] 資料表中刪除記錄的要求訊息是：</span><span class="sxs-lookup"><span data-stu-id="cefa8-349">For example, a request message that inserts a record in the EMPLOYEE table, invokes the GET_LAST_EMP_DATA stored procedure, and deletes a record from the EMPLOYEE table is:</span></span>  
  
```  
<Request xmlns="http://CompositeTest.CompositeSchema">  
  <Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
    <Rows>  
      <Employee xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
        <Name>John</Name>  
        <Designation>Manager</Designation>  
        <Salary>100000</Salary>  
      </Employee>  
    </Rows>  
  </Insert>  
  <GET_LAST_EMP_DATA xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/dbo" />  
  <Delete xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
    <Rows>  
      <Employee xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
        <Name>John</Name>  
      </Employee>  
    </Rows>  
  </Delete>  
</Request>  
```  
  
 <span data-ttu-id="cefa8-350">請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)如需有關執行 SQL Server 上的複合作業的要求訊息結構描述資料庫 使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cefa8-350">See [Message Schemas for Composite Operations](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md) for more information about the request message schema for performing composite operations on the SQL Server database using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
 <span data-ttu-id="cefa8-351">協調流程取用訊息，並將它傳送到 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cefa8-351">The orchestration consumes the message and sends it to the SQL Server database.</span></span> <span data-ttu-id="cefa8-352">從 SQL Server 資料庫的回應會儲存在其他定義的協調流程一部分的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="cefa8-352">The response from the SQL Server database is saved at the other FILE location defined as part of the orchestration.</span></span> <span data-ttu-id="cefa8-353">例如，從先前的要求訊息的 SQL Server 資料庫的回應是：</span><span class="sxs-lookup"><span data-stu-id="cefa8-353">For example, the response from the SQL Server database for the preceding request message is:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<RequestResponse xmlns="http://CompositeTest.CompositeSchema">  
  <InsertResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
    <InsertResult>  
      <long xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">10080</long>   
    </InsertResult>  
  </InsertResponse>  
  <GET_LAST_EMP_DATAResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/dbo">  
    <GET_LAST_EMP_DATAResult>  
      <DataSet xmlns="http://schemas.datacontract.org/2004/07/System.Data">  
        <xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
          <xs:element msdata:IsDataSet="true" name="NewDataSet">  
            <xs:complexType>  
              <xs:sequence>  
                <xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                  <xs:complexType>  
                    <xs:sequence>  
                      <xs:element minOccurs="0" name="Employee_ID" type="xs:int" />   
                      <xs:element minOccurs="0" name="Name" type="xs:string" />   
                      <xs:element minOccurs="0" name="DOJ" type="xs:dateTime" />   
                      <xs:element minOccurs="0" name="Designation" type="xs:string" />   
                      <xs:element minOccurs="0" name="Job_Description" type="xs:string" />   
                      <xs:element minOccurs="0" name="Photo" type="xs:base64Binary" />   
                      <xs:element minOccurs="0" name="Rating" type="xs:string" />   
                      <xs:element minOccurs="0" name="Salary" type="xs:decimal" />   
                      <xs:element minOccurs="0" name="Last_Modified" type="xs:base64Binary" />   
                    </xs:sequence>  
                  </xs:complexType>  
                </xs:element>  
              </xs:sequence>  
            </xs:complexType>  
          </xs:element>  
        </xs:schema>  
        <diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
          <NewDataSet xmlns="">  
            <NewTable>  
              <Employee_ID>10080</Employee_ID>   
              <Name>John</Name>   
              <Designation>Manager</Designation>   
              <Salary>100000.00</Salary>   
              <Last_Modified>AAAAAAAAF40=</Last_Modified>   
            </NewTable>  
          </NewDataSet>  
        </diffgr:diffgram>  
      </DataSet>  
    </GET_LAST_EMP_DATAResult>  
    <ReturnValue>0</ReturnValue>   
  </GET_LAST_EMP_DATAResponse>  
  <DeleteResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
    <DeleteResult>1</DeleteResult>   
  </DeleteResponse>  
</RequestResponse>  
```  
  
 <span data-ttu-id="cefa8-354">上述的回應包含多個結果集對應不同的作業執行複合作業的一部分。</span><span class="sxs-lookup"><span data-stu-id="cefa8-354">The preceding response contains multiple result sets corresponding the different operations performed as part of the composite operation.</span></span> <span data-ttu-id="cefa8-355">比方說，`InsertResult`項目包含 10080，這是新加入的資料錄的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="cefa8-355">For example, the `InsertResult` element contains 10080, which is the unique identifier for the newly added record.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="cefa8-356">最佳作法</span><span class="sxs-lookup"><span data-stu-id="cefa8-356">Best Practices</span></span>  
 <span data-ttu-id="cefa8-357">您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。</span><span class="sxs-lookup"><span data-stu-id="cefa8-357">After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the binding file.</span></span> <span data-ttu-id="cefa8-358">一旦您產生繫結檔案時，您可以匯入的組態設定檔案，，讓您不需要建立項目，例如傳送埠和接收相同的協調流程的連接埠。</span><span class="sxs-lookup"><span data-stu-id="cefa8-358">Once you generate a binding file, you can import the configuration settings from the file, so that you do not need to create items such as send ports and receive ports for the same orchestration.</span></span> <span data-ttu-id="cefa8-359">如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="cefa8-359">For more information about binding files, see [Reuse adapter bindings](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cefa8-360">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cefa8-360">See Also</span></span>  
[<span data-ttu-id="cefa8-361">使用 SQL 配接器開發 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="cefa8-361">Develop BizTalk applications using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)