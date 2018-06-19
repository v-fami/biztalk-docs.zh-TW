---
title: 執行複合操作 SQL Server 上使用 BizTalk Server |Microsoft 文件
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
ms.openlocfilehash: 0f6891f300a89684481184bf255f3cdd54d25845
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968020"
---
# <a name="run-composite-operations-on-sql-server-using-biztalk-server"></a><span data-ttu-id="3de49-102">執行複合操作 SQL Server 上使用 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="3de49-102">Run composite operations on SQL Server using BizTalk Server</span></span>
<span data-ttu-id="3de49-103">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓配接器用戶端執行複合操作上的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3de49-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables adapter clients to perform composite operations on the SQL Server database.</span></span> <span data-ttu-id="3de49-104">複合作業可包括：</span><span class="sxs-lookup"><span data-stu-id="3de49-104">A composite operation can include:</span></span>  
  
-   <span data-ttu-id="3de49-105">插入、 更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="3de49-105">Insert, Update, and Delete operations.</span></span> <span data-ttu-id="3de49-106">選取的作業不支援複合作業。</span><span class="sxs-lookup"><span data-stu-id="3de49-106">A Select operation is not supported as part of a composite operation.</span></span>  
  
-   <span data-ttu-id="3de49-107">當做作業執行的預存程序。</span><span class="sxs-lookup"><span data-stu-id="3de49-107">Stored procedures executed as operations.</span></span>  
  
 <span data-ttu-id="3de49-108">單一複合作業可以有任意數目的這些作業，以任何順序。</span><span class="sxs-lookup"><span data-stu-id="3de49-108">A single composite operation can have any number of these operations, in any order.</span></span> <span data-ttu-id="3de49-109">例如，您可以有後面是刪除作業，以及最後的預存程序執行兩項插入作業。</span><span class="sxs-lookup"><span data-stu-id="3de49-109">For example, you can have two Insert operations followed by a Delete operation, and finally a stored procedure execution.</span></span> <span data-ttu-id="3de49-110">此外，您可以有不同的資料庫資料表或檢視表為目標的不同作業。</span><span class="sxs-lookup"><span data-stu-id="3de49-110">Also, you can have different operations targeting different database tables or views.</span></span> <span data-ttu-id="3de49-111">如需配接器如何支援複合操作的詳細資訊，請參閱[使用 SQL 配接器的 SQL Server 中執行複合操作](../../adapters-and-accelerators/adapter-sql/run-composite-operations-in-sql-server-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="3de49-111">For more information about how the adapter supports composite operations, see [Run composite operations in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/run-composite-operations-in-sql-server-using-the-sql-adapter.md).</span></span> <span data-ttu-id="3de49-112">複合操作的 SOAP 訊息結構的相關資訊，請參閱[複合操作的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="3de49-112">For information about the structure of the SOAP message for composite operations, see [Message Schemas for Composite Operations](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3de49-113">如果您正在執行具有使用者定義類型的資料行的資料表上的作業，請確定您參考[資料表和檢視表使用 SQL 配接器的使用者定義類型的作業](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md)開始開發應用程式之前。</span><span class="sxs-lookup"><span data-stu-id="3de49-113">If you are performing operation on tables that have columns of user-defined types, make sure you refer to [Operations on Tables and Views with User-Defined Types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) before you start developing your application.</span></span>  
  
## <a name="how-to-perform-composite-operations-on-sql-server"></a><span data-ttu-id="3de49-114">如何執行 SQL Server 上的複合作業</span><span class="sxs-lookup"><span data-stu-id="3de49-114">How to Perform Composite Operations on SQL Server</span></span>  
 <span data-ttu-id="3de49-115">使用 SQL Server 上執行操作[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[開發 BizTalk 應用程式與 SQL 配接器的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="3de49-115">Performing an operation on SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] involves procedural tasks described in [Building blocks to develop BizTalk applications with the SQL adapter](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md).</span></span> <span data-ttu-id="3de49-116">若要執行複合操作上的 SQL Server 資料庫，這些工作包括：</span><span class="sxs-lookup"><span data-stu-id="3de49-116">To perform composite operations on the SQL Server database, these tasks are:</span></span>  
  
1.  <span data-ttu-id="3de49-117">建立 BizTalk 專案，並產生您想要叫用的所有作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3de49-117">Create a BizTalk project, and generate schema for all the operations you want to invoke.</span></span>  
  
2.  <span data-ttu-id="3de49-118">手動建立結構描述檔案，其中包含您在上一個步驟中產生的所有結構描述的參考。</span><span class="sxs-lookup"><span data-stu-id="3de49-118">Manually create a schema file that includes references to all the schemas you generated in the previous step.</span></span>  
  
3.  <span data-ttu-id="3de49-119">建立傳送和接收訊息，從 SQL Server 資料庫的 BizTalk 專案中的訊息。</span><span class="sxs-lookup"><span data-stu-id="3de49-119">Create messages in the BizTalk project for sending and receiving messages from the SQL Server database.</span></span> <span data-ttu-id="3de49-120">這些訊息必須符合您在上一個步驟中建立的要求和回應結構描述。</span><span class="sxs-lookup"><span data-stu-id="3de49-120">These messages must conform to the request and response schema you created in the previous step.</span></span>  
  
4.  <span data-ttu-id="3de49-121">建立協調流程叫用 SQL Server 資料庫的複合作業。</span><span class="sxs-lookup"><span data-stu-id="3de49-121">Create an orchestration to invoke the composite operation on the SQL Server database.</span></span>  
  
5.  <span data-ttu-id="3de49-122">建置和部署 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="3de49-122">Build and deploy the BizTalk project.</span></span>  
  
6.  <span data-ttu-id="3de49-123">設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="3de49-123">Configure the BizTalk application by creating physical send and receive ports.</span></span>  
  
7.  <span data-ttu-id="3de49-124">啟動 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3de49-124">Start the BizTalk application.</span></span>  
  
 <span data-ttu-id="3de49-125">本主題提供有關如何執行這些工作的指示。</span><span class="sxs-lookup"><span data-stu-id="3de49-125">This topic provides instructions on how to perform these tasks.</span></span>  
  
## <a name="sample-based-on-this-topic"></a><span data-ttu-id="3de49-126">根據本主題的範例</span><span class="sxs-lookup"><span data-stu-id="3de49-126">Sample Based on This Topic</span></span>  
 <span data-ttu-id="3de49-127">基礎的範例，CompositeOperations，本主題隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3de49-127">A sample, CompositeOperations, based on this topic is provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="3de49-128">如需詳細資訊，請參閱[SQL 配接器範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="3de49-128">For more information, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span></span>  
  
## <a name="generating-schema"></a><span data-ttu-id="3de49-129">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="3de49-129">Generating Schema</span></span>  
 <span data-ttu-id="3de49-130">本主題中，以示範如何執行複合操作，下列工作將會執行指定的順序：</span><span class="sxs-lookup"><span data-stu-id="3de49-130">In this topic, to demonstrate how to perform composite operations, the following tasks will be performed in the order specified:</span></span>  
  
-   <span data-ttu-id="3de49-131">EMPLOYEE 資料表中插入記錄。</span><span class="sxs-lookup"><span data-stu-id="3de49-131">Insert record into the EMPLOYEE table.</span></span>  
  
-   <span data-ttu-id="3de49-132">叫用 GET_LAST_EMP_DATA 預存程序所擷取最後一個插入的記錄的所有資料的行。</span><span class="sxs-lookup"><span data-stu-id="3de49-132">Retrieve all the columns for the last inserted record by invoking the GET_LAST_EMP_DATA stored procedure.</span></span>  
  
-   <span data-ttu-id="3de49-133">從 EMPLOYEE 資料表刪除記錄。</span><span class="sxs-lookup"><span data-stu-id="3de49-133">Delete the record from the EMPLOYEE table.</span></span>  
  
 <span data-ttu-id="3de49-134">執行與建立員工資料表範例中提供的指令碼。</span><span class="sxs-lookup"><span data-stu-id="3de49-134">Run the scripts provided with the samples to create the EMPLOYEE table.</span></span> <span data-ttu-id="3de49-135">如需這些範例的詳細資訊，請參閱[結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="3de49-135">For more information about the samples, see [Schema Samples](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md).</span></span>  
  
 <span data-ttu-id="3de49-136">您必須建立 BizTalk 專案，並使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]來產生這些作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3de49-136">You must create a BizTalk project and use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate the schema for these operations.</span></span> <span data-ttu-id="3de49-137">請參閱[擷取中繼資料，使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="3de49-137">See [Retrieving Metadata for SQL Server Operations in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) for more information about how to generate schemas.</span></span>  
  
## <a name="creating-a-composite-schema-definition"></a><span data-ttu-id="3de49-138">建立複合的結構描述定義</span><span class="sxs-lookup"><span data-stu-id="3de49-138">Creating a Composite Schema Definition</span></span>  
 <span data-ttu-id="3de49-139">您現在必須建立複合的結構描述參考您針對個別作業所建立之結構描述。</span><span class="sxs-lookup"><span data-stu-id="3de49-139">You must now create a composite schema that references the schemas you created for the individual operations.</span></span> <span data-ttu-id="3de49-140">執行下列步驟，以建立複合的結構描述定義。</span><span class="sxs-lookup"><span data-stu-id="3de49-140">Perform the following steps to create a composite schema definition.</span></span>  
  
#### <a name="to-add-a-composite-schema-definition"></a><span data-ttu-id="3de49-141">若要加入複合的結構描述定義</span><span class="sxs-lookup"><span data-stu-id="3de49-141">To add a composite schema definition</span></span>  
  
1.  <span data-ttu-id="3de49-142">將結構描述檔案加入至 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="3de49-142">Add a schema file to the BizTalk project.</span></span> <span data-ttu-id="3de49-143">以滑鼠右鍵按一下專案名稱，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="3de49-143">Right-click the project name, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="3de49-144">在**加入新項目**對話方塊中，從**類別**方塊中，按一下**結構描述檔案**。</span><span class="sxs-lookup"><span data-stu-id="3de49-144">In the **Add New Item** dialog box, from the **Categories** box, click **Schema Files**.</span></span> <span data-ttu-id="3de49-145">從**範本**方塊中，按一下**結構描述**。</span><span class="sxs-lookup"><span data-stu-id="3de49-145">From the **Templates** box, click **Schema**.</span></span> <span data-ttu-id="3de49-146">指定結構描述檔案的名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3de49-146">Specify a name for the schema file, and then click **OK**.</span></span>  
  
     <span data-ttu-id="3de49-147">此範例中，結構描述檔案名稱指定為`CompositeSchema.xsd`。</span><span class="sxs-lookup"><span data-stu-id="3de49-147">For this example, specify the schema file name as `CompositeSchema.xsd`.</span></span>  
  
2.  <span data-ttu-id="3de49-148">將參考加入至您想要執行的不同作業產生的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3de49-148">Add references to the schema generated for the different operations that you want to perform.</span></span> <span data-ttu-id="3de49-149">在此範例中，不同的結構描述產生的作業如下：</span><span class="sxs-lookup"><span data-stu-id="3de49-149">In this example, the different schemas generated for operations are:</span></span>  
  
    -   <span data-ttu-id="3de49-150">TableOperation.dbo.Employee.xsd Insert 和 Delete 作業。</span><span class="sxs-lookup"><span data-stu-id="3de49-150">TableOperation.dbo.Employee.xsd, for Insert and Delete operations.</span></span>  
  
    -   <span data-ttu-id="3de49-151">Procedure.dbo.xsd，如 GET_LAST_EMP_DATA 預存程序。</span><span class="sxs-lookup"><span data-stu-id="3de49-151">Procedure.dbo.xsd, for the GET_LAST_EMP_DATA stored procedure.</span></span>  
  
     <span data-ttu-id="3de49-152">若要加入的參考：</span><span class="sxs-lookup"><span data-stu-id="3de49-152">To add references:</span></span>  
  
    1.  <span data-ttu-id="3de49-153">以滑鼠右鍵按一下根**\<結構描述\>** 中 CompositeSchema.xsd，按一下節點**屬性**。</span><span class="sxs-lookup"><span data-stu-id="3de49-153">Right-click the root **\<Schema\>** node in the CompositeSchema.xsd, and click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="3de49-154">在**屬性**方塊中，按一下省略符號按鈕 **（...）** 針對**匯入**屬性。</span><span class="sxs-lookup"><span data-stu-id="3de49-154">In the **Property** box, click the ellipsis button **(…)** against the **Imports** property.</span></span>  
  
         <span data-ttu-id="3de49-155">![匯入結構描述定義](../../adapters-and-accelerators/adapter-oracle-database/media/d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca.gif "d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca")</span><span class="sxs-lookup"><span data-stu-id="3de49-155">![Import schema definitions](../../adapters-and-accelerators/adapter-oracle-database/media/d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca.gif "d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca")</span></span>  
  
    3.  <span data-ttu-id="3de49-156">在**匯入**對話方塊中，從**匯入新結構描述為**清單中，選取**XSD 匯入**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="3de49-156">In the **Imports** dialog box, from the **Import new schema as** list, select **XSD Import**, and then click **Add**.</span></span>  
  
    4.  <span data-ttu-id="3de49-157">在**BizTalk 型別選擇器**對話方塊方塊中，展開 BizTalk 專案名稱節點，展開**結構描述**，然後選取您要匯入的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3de49-157">In the **BizTalk Type Picker** dialog box, expand the BizTalk project name node, expand **Schemas**, and then select the schema you want to import.</span></span> <span data-ttu-id="3de49-158">此範例中，選取 < BizTalk_project_name >。TableOperation_dbo_Employee。</span><span class="sxs-lookup"><span data-stu-id="3de49-158">For this example, select <BizTalk_project_name>.TableOperation_dbo_Employee.</span></span> <span data-ttu-id="3de49-159">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3de49-159">Click **OK**.</span></span>  
  
         <span data-ttu-id="3de49-160">重複此步驟，匯入 < BizTalk_project_name >。Procedure_dbo 太。</span><span class="sxs-lookup"><span data-stu-id="3de49-160">Repeat this step to import <BizTalk_project_name>.Procedure_dbo too.</span></span>  
  
    5.  <span data-ttu-id="3de49-161">在**匯入**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="3de49-161">In the **Imports** dialog box, click **OK**.</span></span>  
  
3.  <span data-ttu-id="3de49-162">將兩個子節點加入至根結構描述節點。</span><span class="sxs-lookup"><span data-stu-id="3de49-162">Add two child nodes to the root schema node.</span></span> <span data-ttu-id="3de49-163">一個子節點對應至要求結構描述執行複合作業。</span><span class="sxs-lookup"><span data-stu-id="3de49-163">One child node corresponds to the request schema for performing the composite operation.</span></span> <span data-ttu-id="3de49-164">另一個子節點對應至回應結構描述。</span><span class="sxs-lookup"><span data-stu-id="3de49-164">The other child node corresponds to the response schema.</span></span> <span data-ttu-id="3de49-165">對應至要求結構描述的節點可以有任何名稱。</span><span class="sxs-lookup"><span data-stu-id="3de49-165">The node that corresponds to the request schema can have any name.</span></span> <span data-ttu-id="3de49-166">對應至回應結構描述的節點必須呼叫 < request_schema_node > 回應。</span><span class="sxs-lookup"><span data-stu-id="3de49-166">The node that corresponds to the response schema must be called <request_schema_node>Response.</span></span> <span data-ttu-id="3de49-167">針對此範例中，我們會呼叫要求結構描述節點，做為**要求**。</span><span class="sxs-lookup"><span data-stu-id="3de49-167">For this example, we will call the request schema node as **Request**.</span></span> <span data-ttu-id="3de49-168">因此，呼叫的回應結構描述節點**RequestResponse**。</span><span class="sxs-lookup"><span data-stu-id="3de49-168">So, the response schema node is called **RequestResponse**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3de49-169">根據預設，**根**節點也會加入至新的結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="3de49-169">By default, a **Root** node is also added to a new schema file.</span></span> <span data-ttu-id="3de49-170">您可以重新命名**根**節點**要求**。</span><span class="sxs-lookup"><span data-stu-id="3de49-170">You can rename the **Root** node to **Request**.</span></span> <span data-ttu-id="3de49-171">若要重新命名的節點，以滑鼠右鍵按一下節點名稱，然後按一下**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="3de49-171">To rename a node, right-click the node name and click **Rename**.</span></span>  
  
     <span data-ttu-id="3de49-172">若要加入的節點下**\<結構描述\>** 節點：</span><span class="sxs-lookup"><span data-stu-id="3de49-172">To add a node under the **\<Schema\>** node:</span></span>  
  
    1.  <span data-ttu-id="3de49-173">以滑鼠右鍵按一下**\<結構描述\>** 節點，指向**插入結構描述節點**，然後按一下**子記錄**。</span><span class="sxs-lookup"><span data-stu-id="3de49-173">Right-click the **\<Schema\>** node, point to **Insert Schema Node**, and click **Child Record**.</span></span>  
  
    2.  <span data-ttu-id="3de49-174">重新命名新的節點**RequestResponse**。</span><span class="sxs-lookup"><span data-stu-id="3de49-174">Rename the new node to **RequestResponse**.</span></span>  
  
4.  <span data-ttu-id="3de49-175">加入子節點底下**要求**對應到複合作業的一部分，您將執行每個作業的要求結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="3de49-175">Add child nodes under the **Request** node that correspond to the request schema for each operation that you will perform as part of the composite operation.</span></span> <span data-ttu-id="3de49-176">對於此範例中，您必須將對應於下列子節點：</span><span class="sxs-lookup"><span data-stu-id="3de49-176">For this example, you must add child nodes corresponding to the following:</span></span>  
  
    -   <span data-ttu-id="3de49-177">插入和刪除員工資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="3de49-177">Insert and Delete operations on the EMPLOYEE table.</span></span>  
  
    -   <span data-ttu-id="3de49-178">GET_LAST_EMP_DATA 預存程序。</span><span class="sxs-lookup"><span data-stu-id="3de49-178">GET_LAST_EMP_DATA stored procedure.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3de49-179">您必須將節點加入您要執行作業的順序相同。</span><span class="sxs-lookup"><span data-stu-id="3de49-179">You must add the nodes in the same order in which you want to perform the operations.</span></span> <span data-ttu-id="3de49-180">例如，如果您想要插入的記錄，然後執行預存程序，然後刪除記錄，您必須先新增的節點代表插入作業，後面接著預存程序中，節點和最後一個刪除作業。</span><span class="sxs-lookup"><span data-stu-id="3de49-180">For example, if you want to insert a record, then execute a stored procedure, and then delete a record you must first add a node for the Insert operation, followed by a node for the stored procedure, and finally a node for the Delete operation.</span></span>  
  
     <span data-ttu-id="3de49-181">若要加入至子節點**要求**節點：</span><span class="sxs-lookup"><span data-stu-id="3de49-181">To add child nodes to the **Request** node:</span></span>  
  
    1.  <span data-ttu-id="3de49-182">以滑鼠右鍵按一下**要求**節點，指向**插入結構描述節點**，然後按一下 **子記錄**。</span><span class="sxs-lookup"><span data-stu-id="3de49-182">Right-click the **Request** node, point to **Insert Schema Node**, and then click  **Child Record**.</span></span>  
  
         <span data-ttu-id="3de49-183">![插入結構描述的子節點](../../adapters-and-accelerators/adapter-oracle-database/media/58992131-13a6-45c3-9513-5c0995091fae.gif "58992131-13a6-45c3-9513-5c0995091fae")</span><span class="sxs-lookup"><span data-stu-id="3de49-183">![Insert child nodes for a schema](../../adapters-and-accelerators/adapter-oracle-database/media/58992131-13a6-45c3-9513-5c0995091fae.gif "58992131-13a6-45c3-9513-5c0995091fae")</span></span>  
  
    2.  <span data-ttu-id="3de49-184">重新命名為對應至複合作業的一部分執行的操作的要求結構描述的記錄。</span><span class="sxs-lookup"><span data-stu-id="3de49-184">Rename the record to correspond to a request schema for an operation that you perform as part of the composite operation.</span></span> <span data-ttu-id="3de49-185">例如，重新命名 「 插入 」 至節點。</span><span class="sxs-lookup"><span data-stu-id="3de49-185">For example, rename the node to “Insert”.</span></span>  
  
    3.  <span data-ttu-id="3de49-186">地圖**插入**EMPLOYEE 資料表的 Insert 作業的要求結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="3de49-186">Map the **Insert** node to the request schema for the Insert operation on the EMPLOYEE table.</span></span> <span data-ttu-id="3de49-187">若要這樣做，請以滑鼠右鍵按一下**插入**節點，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="3de49-187">To do so, right-click the **Insert** node, and click **Properties**.</span></span> <span data-ttu-id="3de49-188">在**屬性** 方塊中，從**資料結構型別**清單中，選取**插入 （參考）**。</span><span class="sxs-lookup"><span data-stu-id="3de49-188">In the **Properties** box, from the **Data Structure Type** list, select **Insert (Reference)**.</span></span>  
  
         <span data-ttu-id="3de49-189">![將子節點對應至要求結構描述](../../adapters-and-accelerators/adapter-sql/media/5ace18be-0fe8-44c6-bd2f-cb19035494b5.gif "5ace18be-0fe8-44c6-bd2f-cb19035494b5")</span><span class="sxs-lookup"><span data-stu-id="3de49-189">![Map child nodes to the request schema](../../adapters-and-accelerators/adapter-sql/media/5ace18be-0fe8-44c6-bd2f-cb19035494b5.gif "5ace18be-0fe8-44c6-bd2f-cb19035494b5")</span></span>  
  
    4.  <span data-ttu-id="3de49-190">重複這些步驟來加入 GET_LAST_EMP_DATA 預存程序和刪除作業的要求結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="3de49-190">Repeat these steps to add nodes for the request schemas for GET_LAST_EMP_DATA stored procedure and the Delete operation.</span></span> <span data-ttu-id="3de49-191">指定節點名稱，然後將它們對應至對應的結構描述，如下列表格中所述。</span><span class="sxs-lookup"><span data-stu-id="3de49-191">Specify the node names and map them to the corresponding schema as mentioned in the following table.</span></span>  
  
        |<span data-ttu-id="3de49-192">節點名稱</span><span class="sxs-lookup"><span data-stu-id="3de49-192">Node name</span></span>|<span data-ttu-id="3de49-193">對應至結構描述</span><span class="sxs-lookup"><span data-stu-id="3de49-193">Mapped to schema</span></span>|  
        |---------------|----------------------|  
        |<span data-ttu-id="3de49-194">GET_LAST_EMP_DATA</span><span class="sxs-lookup"><span data-stu-id="3de49-194">GET_LAST_EMP_DATA</span></span>|<span data-ttu-id="3de49-195">GET_LAST_EMP_DATA （參考）</span><span class="sxs-lookup"><span data-stu-id="3de49-195">GET_LAST_EMP_DATA (Reference)</span></span>|  
        |<span data-ttu-id="3de49-196">DELETE</span><span class="sxs-lookup"><span data-stu-id="3de49-196">Delete</span></span>|<span data-ttu-id="3de49-197">刪除 （參考）</span><span class="sxs-lookup"><span data-stu-id="3de49-197">Delete (Reference)</span></span>|  
  
5.  <span data-ttu-id="3de49-198">加入子節點底下**RequestResponse**對應到複合作業的一部分，您將執行每個作業的回應結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="3de49-198">Add child nodes under the **RequestResponse** node that correspond to the response schema for each operation that you will perform as part of the composite operation.</span></span> <span data-ttu-id="3de49-199">對於此範例中，您必須將對應於下列子節點：</span><span class="sxs-lookup"><span data-stu-id="3de49-199">For this example, you must add child nodes corresponding to the following:</span></span>  
  
    -   <span data-ttu-id="3de49-200">插入和刪除員工資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="3de49-200">Insert and Delete operations on the EMPLOYEE table.</span></span>  
  
    -   <span data-ttu-id="3de49-201">GET_LAST_EMP_DATA 預存程序。</span><span class="sxs-lookup"><span data-stu-id="3de49-201">GET_LAST_EMP_DATA stored procedure.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3de49-202">您必須加入子節點下的子節點的順序相同**要求**節點。</span><span class="sxs-lookup"><span data-stu-id="3de49-202">You must add the child nodes in the same order as the child nodes under the **Request** node.</span></span>  
  
     <span data-ttu-id="3de49-203">若要加入至子節點**RequestResponse**節點：</span><span class="sxs-lookup"><span data-stu-id="3de49-203">To add child nodes to the **RequestResponse** node:</span></span>  
  
    1.  <span data-ttu-id="3de49-204">以滑鼠右鍵按一下**RequestResponse**節點，指向**插入結構描述節點**，然後按一下**子記錄**。</span><span class="sxs-lookup"><span data-stu-id="3de49-204">Right-click the **RequestResponse** node, point to **Insert Schema Node**, and click **Child Record**.</span></span>  
  
    2.  <span data-ttu-id="3de49-205">重新命名為對應至複合作業的一部分執行的操作的回應結構描述的記錄。</span><span class="sxs-lookup"><span data-stu-id="3de49-205">Rename the record to correspond to a response schema for an operation that you perform as part of the composite operation.</span></span> <span data-ttu-id="3de49-206">例如，重新命名 「 InsertResponse"的節點。</span><span class="sxs-lookup"><span data-stu-id="3de49-206">For example, rename the node to “InsertResponse”.</span></span>  
  
    3.  <span data-ttu-id="3de49-207">地圖**InsertResponse** EMPLOYEE 資料表的 Insert 作業的回應結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="3de49-207">Map the **InsertResponse** node to the response schema for the Insert operation on the EMPLOYEE table.</span></span> <span data-ttu-id="3de49-208">若要這樣做，請以滑鼠右鍵按一下**InsertResponse**節點，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="3de49-208">To do so, right-click the **InsertResponse** node, and click **Properties**.</span></span> <span data-ttu-id="3de49-209">在**屬性** 方塊中，從**資料結構型別**清單中，選取**InsertResponse （參考）**。</span><span class="sxs-lookup"><span data-stu-id="3de49-209">In the **Properties** box, from the **Data Structure Type** list, select **InsertResponse (Reference)**.</span></span>  
  
    4.  <span data-ttu-id="3de49-210">重複這些步驟來加入 GET_LAST_EMP_DATA 預存程序和刪除作業的回應結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="3de49-210">Repeat these steps to add nodes for the response schemas for the GET_LAST_EMP_DATA stored procedure and the Delete operation.</span></span> <span data-ttu-id="3de49-211">指定節點名稱，然後將它們對應至對應的結構描述，如下列表格中所述。</span><span class="sxs-lookup"><span data-stu-id="3de49-211">Specify the node names and map them to the corresponding schema as mentioned in the following table.</span></span>  
  
        |<span data-ttu-id="3de49-212">節點名稱</span><span class="sxs-lookup"><span data-stu-id="3de49-212">Node name</span></span>|<span data-ttu-id="3de49-213">對應至結構描述</span><span class="sxs-lookup"><span data-stu-id="3de49-213">Mapped to schema</span></span>|  
        |---------------|----------------------|  
        |<span data-ttu-id="3de49-214">GET_LAST_EMP_DATAResponse</span><span class="sxs-lookup"><span data-stu-id="3de49-214">GET_LAST_EMP_DATAResponse</span></span>|<span data-ttu-id="3de49-215">GET_LAST_EMP_DATAResponse （參考）</span><span class="sxs-lookup"><span data-stu-id="3de49-215">GET_LAST_EMP_DATAResponse (Reference)</span></span>|  
        |<span data-ttu-id="3de49-216">DeleteResponse</span><span class="sxs-lookup"><span data-stu-id="3de49-216">DeleteResponse</span></span>|<span data-ttu-id="3de49-217">DeleteResponse （參考）</span><span class="sxs-lookup"><span data-stu-id="3de49-217">DeleteResponse (Reference)</span></span>|  
  
6.  <span data-ttu-id="3de49-218">儲存**CompositeSchema.xsd**檔案。</span><span class="sxs-lookup"><span data-stu-id="3de49-218">Save the **CompositeSchema.xsd** file.</span></span>  
  
## <a name="defining-messages-and-message-types"></a><span data-ttu-id="3de49-219">定義訊息和訊息類型</span><span class="sxs-lookup"><span data-stu-id="3de49-219">Defining Messages and Message Types</span></span>  
 <span data-ttu-id="3de49-220">您在最後一個步驟中建立複合結構描述會描述 「 類型 」 所需的協調流程中的訊息。</span><span class="sxs-lookup"><span data-stu-id="3de49-220">The composite schema that you created in the last step describes the “types” required for the messages in an orchestration.</span></span> <span data-ttu-id="3de49-221">訊息通常是為其型別由對應的結構描述所定義的變數。</span><span class="sxs-lookup"><span data-stu-id="3de49-221">A message is typically a variable, the type for which is defined by the corresponding schema.</span></span> <span data-ttu-id="3de49-222">您現在必須建立協調流程的訊息，並將它們連結至您在上一個步驟中建立的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3de49-222">You must now create messages for the orchestration and link them to schema you created in the previous step.</span></span>  
  
#### <a name="to-create-messages-and-link-to-schema"></a><span data-ttu-id="3de49-223">建立訊息，以及連結至結構描述</span><span class="sxs-lookup"><span data-stu-id="3de49-223">To create messages and link to schema</span></span>  
  
1.  <span data-ttu-id="3de49-224">BizTalk 專案中新增協調流程。</span><span class="sxs-lookup"><span data-stu-id="3de49-224">Add an orchestration to the BizTalk project.</span></span> <span data-ttu-id="3de49-225">從 方案總管 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="3de49-225">From Solution Explorer, right-click the BizTalk project name, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="3de49-226">輸入 BizTalk 協調流程的名稱，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="3de49-226">Type a name for the BizTalk orchestration, and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="3de49-227">如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。</span><span class="sxs-lookup"><span data-stu-id="3de49-227">Open the Orchestration View window of the BizTalk project, if it is not already open.</span></span> <span data-ttu-id="3de49-228">若要這樣做，請按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="3de49-228">To do so, click **View**, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
3.  <span data-ttu-id="3de49-229">在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。</span><span class="sxs-lookup"><span data-stu-id="3de49-229">In Orchestration View, right-click **Messages**, and then click **New Message**.</span></span>  
  
4.  <span data-ttu-id="3de49-230">以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="3de49-230">Right-click the newly created message, and then select **Properties Window**.</span></span>  
  
5.  <span data-ttu-id="3de49-231">在**屬性**窗格**Message_1**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3de49-231">In the **Properties** pane for the **Message_1**, do the following:</span></span>  
  
    |<span data-ttu-id="3de49-232">使用</span><span class="sxs-lookup"><span data-stu-id="3de49-232">Use this</span></span>|<span data-ttu-id="3de49-233">動作</span><span class="sxs-lookup"><span data-stu-id="3de49-233">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="3de49-234">識別碼</span><span class="sxs-lookup"><span data-stu-id="3de49-234">Identifier</span></span>|<span data-ttu-id="3de49-235">輸入 `Request`</span><span class="sxs-lookup"><span data-stu-id="3de49-235">Type `Request`</span></span>|  
    |<span data-ttu-id="3de49-236">訊息類型</span><span class="sxs-lookup"><span data-stu-id="3de49-236">Message Type</span></span>|<span data-ttu-id="3de49-237">從下拉式清單中，展開 **結構描述**，然後選取*CompositeOp.CompositeSchema.Request*CompositeOp 所在的 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="3de49-237">From the drop-down list, expand **Schemas**, and then select *CompositeOp.CompositeSchema.Request*, where CompositeOp is the name of your BizTalk project.</span></span> <span data-ttu-id="3de49-238">CompositeSchema 是手動建立的複合作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3de49-238">CompositeSchema is the schema you created manually for the composite operations.</span></span>|  
  
6.  <span data-ttu-id="3de49-239">重複步驟 2 來建立新的訊息。</span><span class="sxs-lookup"><span data-stu-id="3de49-239">Repeat step 2 to create a new message.</span></span> <span data-ttu-id="3de49-240">在**屬性**窗格新訊息中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3de49-240">In the **Properties** pane for the new message, do the following:</span></span>  
  
    |<span data-ttu-id="3de49-241">使用</span><span class="sxs-lookup"><span data-stu-id="3de49-241">Use this</span></span>|<span data-ttu-id="3de49-242">動作</span><span class="sxs-lookup"><span data-stu-id="3de49-242">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="3de49-243">識別碼</span><span class="sxs-lookup"><span data-stu-id="3de49-243">Identifier</span></span>|<span data-ttu-id="3de49-244">輸入 `Response`</span><span class="sxs-lookup"><span data-stu-id="3de49-244">Type `Response`</span></span>|  
    |<span data-ttu-id="3de49-245">訊息類型</span><span class="sxs-lookup"><span data-stu-id="3de49-245">Message Type</span></span>|<span data-ttu-id="3de49-246">從下拉式清單中，展開 **結構描述**，然後選取*CompositeOp.CompositeSchema.RequestResponse*。</span><span class="sxs-lookup"><span data-stu-id="3de49-246">From the drop-down list, expand **Schemas**, and then select *CompositeOp.CompositeSchema.RequestResponse*.</span></span>|  
  
## <a name="setting-up-the-orchestration"></a><span data-ttu-id="3de49-247">設定協調流程</span><span class="sxs-lookup"><span data-stu-id="3de49-247">Setting up the Orchestration</span></span>  
 <span data-ttu-id="3de49-248">您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行 SQL Server 上的複合作業。</span><span class="sxs-lookup"><span data-stu-id="3de49-248">You must create a BizTalk orchestration to use [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for performing composite operations on SQL Server.</span></span> <span data-ttu-id="3de49-249">在此協調流程中，卸除要求訊息已定義的接收位置。</span><span class="sxs-lookup"><span data-stu-id="3de49-249">In this orchestration, you drop a request message at a defined receive location.</span></span> <span data-ttu-id="3de49-250">要求訊息必須符合您稍早建立的複合結構描述。</span><span class="sxs-lookup"><span data-stu-id="3de49-250">The request message must conform to the composite schema you created earlier.</span></span> <span data-ttu-id="3de49-251">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會取用這個訊息，並將它傳遞到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="3de49-251">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] consumes this message and passes it on to SQL Server.</span></span> <span data-ttu-id="3de49-252">從 SQL Server 的回應會儲存到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="3de49-252">The response from SQL Server is saved to another location.</span></span> <span data-ttu-id="3de49-253">您必須包含傳送和接收送到 SQL Server 的訊息並接收回應，分別圖形。</span><span class="sxs-lookup"><span data-stu-id="3de49-253">You must include Send and Receive shapes to send messages to SQL Server and receive responses, respectively.</span></span> <span data-ttu-id="3de49-254">用於執行複合操作的基本協調流程如下所示：</span><span class="sxs-lookup"><span data-stu-id="3de49-254">A basic orchestration for performing composite operations resembles the following:</span></span>  
  
 <span data-ttu-id="3de49-255">![用於執行複合操作的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb.gif "4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb")</span><span class="sxs-lookup"><span data-stu-id="3de49-255">![Orchestration to peform composite operations](../../adapters-and-accelerators/adapter-oracle-database/media/4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb.gif "4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb")</span></span>  
  
### <a name="adding-message-shapes"></a><span data-ttu-id="3de49-256">新增訊息圖形</span><span class="sxs-lookup"><span data-stu-id="3de49-256">Adding Message Shapes</span></span>  
 <span data-ttu-id="3de49-257">請確定您針對每個訊息圖形指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="3de49-257">Make sure you specify the following properties for each of the message shapes.</span></span> <span data-ttu-id="3de49-258">圖形資料行中所列的名稱是訊息 圖形的名稱，為顯示在剛才提及的協調流程中。</span><span class="sxs-lookup"><span data-stu-id="3de49-258">The names listed in the Shape column are the names of the message shapes as displayed in the just-mentioned orchestration.</span></span>  
  
|<span data-ttu-id="3de49-259">形狀圖</span><span class="sxs-lookup"><span data-stu-id="3de49-259">Shape</span></span>|<span data-ttu-id="3de49-260">圖形類型</span><span class="sxs-lookup"><span data-stu-id="3de49-260">Shape Type</span></span>|<span data-ttu-id="3de49-261">屬性</span><span class="sxs-lookup"><span data-stu-id="3de49-261">Properties</span></span>|  
|-----------|----------------|----------------|  
|<span data-ttu-id="3de49-262">ReceiveMessage</span><span class="sxs-lookup"><span data-stu-id="3de49-262">ReceiveMessage</span></span>|<span data-ttu-id="3de49-263">Receive</span><span class="sxs-lookup"><span data-stu-id="3de49-263">Receive</span></span>|<span data-ttu-id="3de49-264">-設定**名稱**至*ReceiveMessage*</span><span class="sxs-lookup"><span data-stu-id="3de49-264">-   Set **Name** to *ReceiveMessage*</span></span><br /><span data-ttu-id="3de49-265">-設定**啟動**至 *，則為 True*</span><span class="sxs-lookup"><span data-stu-id="3de49-265">-   Set **Activate** to *True*</span></span>|  
|<span data-ttu-id="3de49-266">SendMessage</span><span class="sxs-lookup"><span data-stu-id="3de49-266">SendMessage</span></span>|<span data-ttu-id="3de49-267">Send</span><span class="sxs-lookup"><span data-stu-id="3de49-267">Send</span></span>|<span data-ttu-id="3de49-268">-設定**名稱**至*SendMessage*</span><span class="sxs-lookup"><span data-stu-id="3de49-268">-   Set **Name** to *SendMessage*</span></span>|  
|<span data-ttu-id="3de49-269">ReceiveResponse</span><span class="sxs-lookup"><span data-stu-id="3de49-269">ReceiveResponse</span></span>|<span data-ttu-id="3de49-270">Receive</span><span class="sxs-lookup"><span data-stu-id="3de49-270">Receive</span></span>|<span data-ttu-id="3de49-271">-設定**名稱**至*ReceiveResponse*</span><span class="sxs-lookup"><span data-stu-id="3de49-271">-   Set **Name** to *ReceiveResponse*</span></span><br /><span data-ttu-id="3de49-272">-設定**啟動**至*False*</span><span class="sxs-lookup"><span data-stu-id="3de49-272">-   Set **Activate** to *False*</span></span>|  
|<span data-ttu-id="3de49-273">SendResponse</span><span class="sxs-lookup"><span data-stu-id="3de49-273">SendResponse</span></span>|<span data-ttu-id="3de49-274">Send</span><span class="sxs-lookup"><span data-stu-id="3de49-274">Send</span></span>|<span data-ttu-id="3de49-275">-設定**名稱**至*SendResponse*</span><span class="sxs-lookup"><span data-stu-id="3de49-275">-   Set **Name** to *SendResponse*</span></span>|  
  
### <a name="adding-ports"></a><span data-ttu-id="3de49-276">新增連接埠</span><span class="sxs-lookup"><span data-stu-id="3de49-276">Adding Ports</span></span>  
 <span data-ttu-id="3de49-277">請確定您針對每個邏輯連接埠指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="3de49-277">Make sure you specify the following properties for each of the logical ports.</span></span> <span data-ttu-id="3de49-278">連接埠資料行中所列的名稱是連接埠的名稱，為顯示協調流程中。</span><span class="sxs-lookup"><span data-stu-id="3de49-278">The names listed in the Port column are the names of the ports as displayed in the orchestration.</span></span>  
  
|<span data-ttu-id="3de49-279">通訊埠</span><span class="sxs-lookup"><span data-stu-id="3de49-279">Port</span></span>|<span data-ttu-id="3de49-280">屬性</span><span class="sxs-lookup"><span data-stu-id="3de49-280">Properties</span></span>|  
|----------|----------------|  
|<span data-ttu-id="3de49-281">MessageIn</span><span class="sxs-lookup"><span data-stu-id="3de49-281">MessageIn</span></span>|<span data-ttu-id="3de49-282">-設定**識別碼**至*MessageIn*</span><span class="sxs-lookup"><span data-stu-id="3de49-282">-   Set **Identifier** to *MessageIn*</span></span><br /><span data-ttu-id="3de49-283">-設定**類型**至*MessageInType*</span><span class="sxs-lookup"><span data-stu-id="3de49-283">-   Set **Type** to *MessageInType*</span></span><br /><span data-ttu-id="3de49-284">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="3de49-284">-   Set **Communication Pattern** to *One-Way*</span></span><br /><span data-ttu-id="3de49-285">-設定**通訊方向**至*接收*</span><span class="sxs-lookup"><span data-stu-id="3de49-285">-   Set **Communication Direction** to *Receive*</span></span>|  
|<span data-ttu-id="3de49-286">LOBPort</span><span class="sxs-lookup"><span data-stu-id="3de49-286">LOBPort</span></span>|<span data-ttu-id="3de49-287">-設定**識別碼**至*LOBPort*</span><span class="sxs-lookup"><span data-stu-id="3de49-287">-   Set **Identifier** to *LOBPort*</span></span><br /><span data-ttu-id="3de49-288">-設定**類型**至*LOBPortType*</span><span class="sxs-lookup"><span data-stu-id="3de49-288">-   Set **Type** to *LOBPortType*</span></span><br /><span data-ttu-id="3de49-289">-設定**通訊模式**至*要求-回應*</span><span class="sxs-lookup"><span data-stu-id="3de49-289">-   Set **Communication Pattern** to *Request-Response*</span></span><br /><span data-ttu-id="3de49-290">-設定**通訊方向**至*傳送接收*</span><span class="sxs-lookup"><span data-stu-id="3de49-290">-   Set **Communication Direction** to *Send-Receive*</span></span>|  
|<span data-ttu-id="3de49-291">ResponseOut</span><span class="sxs-lookup"><span data-stu-id="3de49-291">ResponseOut</span></span>|<span data-ttu-id="3de49-292">-設定**識別碼**至*ResponseOut*</span><span class="sxs-lookup"><span data-stu-id="3de49-292">-   Set **Identifier** to *ResponseOut*</span></span><br /><span data-ttu-id="3de49-293">-設定**類型**至*ResponseOutType*</span><span class="sxs-lookup"><span data-stu-id="3de49-293">-   Set **Type** to *ResponseOutType*</span></span><br /><span data-ttu-id="3de49-294">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="3de49-294">-   Set **Communication Pattern** to *One-Way*</span></span><br /><span data-ttu-id="3de49-295">-設定**通訊方向**至*傳送*</span><span class="sxs-lookup"><span data-stu-id="3de49-295">-   Set **Communication Direction** to *Send*</span></span>|  
  
### <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a><span data-ttu-id="3de49-296">指定訊息的動作圖形，並將它們連接至連接埠</span><span class="sxs-lookup"><span data-stu-id="3de49-296">Specify Messages for Action Shapes, and Connect Them to Ports</span></span>  
 <span data-ttu-id="3de49-297">下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。</span><span class="sxs-lookup"><span data-stu-id="3de49-297">The following table specifies the properties and their values that you should set to specify messages for action shapes and to link the messages to the ports.</span></span> <span data-ttu-id="3de49-298">圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。</span><span class="sxs-lookup"><span data-stu-id="3de49-298">The names listed in the Shape column are the names of the message shapes as displayed in the orchestration mentioned earlier.</span></span>  
  
|<span data-ttu-id="3de49-299">形狀圖</span><span class="sxs-lookup"><span data-stu-id="3de49-299">Shape</span></span>|<span data-ttu-id="3de49-300">屬性</span><span class="sxs-lookup"><span data-stu-id="3de49-300">Properties</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="3de49-301">ReceiveMessage</span><span class="sxs-lookup"><span data-stu-id="3de49-301">ReceiveMessage</span></span>|<span data-ttu-id="3de49-302">-設定**訊息**至*要求*</span><span class="sxs-lookup"><span data-stu-id="3de49-302">-   Set **Message** to *Request*</span></span><br /><span data-ttu-id="3de49-303">-設定**作業**至*MessageIn.CompositeOp.Request*</span><span class="sxs-lookup"><span data-stu-id="3de49-303">-   Set **Operation** to *MessageIn.CompositeOp.Request*</span></span>|  
|<span data-ttu-id="3de49-304">SendMessage</span><span class="sxs-lookup"><span data-stu-id="3de49-304">SendMessage</span></span>|<span data-ttu-id="3de49-305">-設定**訊息**至*要求*</span><span class="sxs-lookup"><span data-stu-id="3de49-305">-   Set **Message** to *Request*</span></span><br /><span data-ttu-id="3de49-306">-設定**作業**至*LOBPort.CompositeOp.Request*</span><span class="sxs-lookup"><span data-stu-id="3de49-306">-   Set **Operation** to *LOBPort.CompositeOp.Request*</span></span>|  
|<span data-ttu-id="3de49-307">ReceiveResponse</span><span class="sxs-lookup"><span data-stu-id="3de49-307">ReceiveResponse</span></span>|<span data-ttu-id="3de49-308">-設定**訊息**至*回應*</span><span class="sxs-lookup"><span data-stu-id="3de49-308">-   Set **Message** to *Response*</span></span><br /><span data-ttu-id="3de49-309">-設定**作業**至*LOBPort.CompositeOp.Response*</span><span class="sxs-lookup"><span data-stu-id="3de49-309">-   Set **Operation** to *LOBPort.CompositeOp.Response*</span></span>|  
|<span data-ttu-id="3de49-310">SendResponse</span><span class="sxs-lookup"><span data-stu-id="3de49-310">SendResponse</span></span>|<span data-ttu-id="3de49-311">-設定**訊息**至*回應*</span><span class="sxs-lookup"><span data-stu-id="3de49-311">-   Set **Message** to *Response*</span></span><br /><span data-ttu-id="3de49-312">-設定**作業**至*ResponseOut.CompositeOp.Request*</span><span class="sxs-lookup"><span data-stu-id="3de49-312">-   Set **Operation** to *ResponseOut.CompositeOp.Request*</span></span>|  
  
 <span data-ttu-id="3de49-313">您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。</span><span class="sxs-lookup"><span data-stu-id="3de49-313">After you have specified these properties, the message shapes and ports are connected and your orchestration is complete.</span></span>  
  
 <span data-ttu-id="3de49-314">您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3de49-314">You must now build the BizTalk solution and deploy it to a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="3de49-315">如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="3de49-315">For more information, see [Building and Running Orchestrations](../../core/building-and-running-orchestrations.md).</span></span>
  
## <a name="configuring-the-biztalk-application"></a><span data-ttu-id="3de49-316">設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="3de49-316">Configuring the BizTalk Application</span></span>  
 <span data-ttu-id="3de49-317">在 [協調流程] 窗格中您已部署的 BizTalk 專案後，會列出您稍早建立的協調流程[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="3de49-317">After you have deployed the BizTalk project, the orchestration you created earlier is listed under the Orchestrations pane in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="3de49-318">您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="3de49-318">You must use the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to configure the application.</span></span> <span data-ttu-id="3de49-319">如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。</span><span class="sxs-lookup"><span data-stu-id="3de49-319">For a walkthrough, see [Walkthrough: Deploying a Basic BizTalk Application](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).</span></span>
  
 <span data-ttu-id="3de49-320">設定應用程式包括：</span><span class="sxs-lookup"><span data-stu-id="3de49-320">Configuring an application involves:</span></span>  
  
-   <span data-ttu-id="3de49-321">選取應用程式的主機。</span><span class="sxs-lookup"><span data-stu-id="3de49-321">Selecting a host for the application.</span></span>  
  
-   <span data-ttu-id="3de49-322">對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="3de49-322">Mapping the ports that you created in your orchestration to physical ports in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="3de49-323">此協調流程中，您必須：</span><span class="sxs-lookup"><span data-stu-id="3de49-323">For this orchestration you must:</span></span>  
  
    -   <span data-ttu-id="3de49-324">定義位置上的硬碟和對應的檔案連接埠，您將在此置放要求訊息。</span><span class="sxs-lookup"><span data-stu-id="3de49-324">Define a location on the hard disk and a corresponding file port where you will drop a request message.</span></span> <span data-ttu-id="3de49-325">BizTalk 協調流程會使用要求訊息，並將它傳送給 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3de49-325">The BizTalk orchestration will consume the request message and send it to the SQL Server database.</span></span>  
  
    -   <span data-ttu-id="3de49-326">定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 SQL Server 資料庫回應的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="3de49-326">Define a location on the hard disk and a corresponding file port where the BizTalk orchestration will drop the response message containing the response from the SQL Server database.</span></span>  
  
    -   <span data-ttu-id="3de49-327">定義實體 Wcf-custom 或 WCF SQL 傳送埠將訊息傳送至 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3de49-327">Define a physical WCF-Custom or WCF-SQL send port to send messages to the SQL Server database.</span></span> <span data-ttu-id="3de49-328">因為作業都是因為在單一交易中，執行屬於複合作業確定**UseAmbientTransaction**繫結屬性設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="3de49-328">Because the operations that are being as part of the composite operation are executed in a single transaction, make sure the **UseAmbientTransaction** binding property is set to **True**.</span></span>  
  
         <span data-ttu-id="3de49-329">您也必須在傳送埠中指定的動作。</span><span class="sxs-lookup"><span data-stu-id="3de49-329">You must also specify the action in the send port.</span></span> <span data-ttu-id="3de49-330">複合操作的動作是 「**CompositeOperation**"。</span><span class="sxs-lookup"><span data-stu-id="3de49-330">The action for a composite operation is “**CompositeOperation**”.</span></span> <span data-ttu-id="3de49-331">如需如何建立連接埠相關資訊，請參閱[手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="3de49-331">For information about how to create ports, see [Manually configure a physical port binding to the SQL adapter](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md).</span></span> <span data-ttu-id="3de49-332">如需如何指定連接埠動作的詳細資訊，請參閱[設定 SQL 配接器的 SOAP 動作](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="3de49-332">For more information about how to specify actions for ports, see [Configure the SOAP action for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md).</span></span>
  
        > [!NOTE]
        >  <span data-ttu-id="3de49-333">產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="3de49-333">Generating the schema using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] also creates a binding file that contains information about the ports and the actions to be set for those ports.</span></span> <span data-ttu-id="3de49-334">您可以從這個繫結檔案匯[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （用於進行傳入呼叫時）。</span><span class="sxs-lookup"><span data-stu-id="3de49-334">You can import this binding file from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create send ports (for outbound calls) or receive ports (for inbound calls).</span></span> <span data-ttu-id="3de49-335">如需詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="3de49-335">For more information, see [Configure a physical port binding using a port binding file to use the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).</span></span> <span data-ttu-id="3de49-336">如果您匯入此繫結檔案，Wcf-custom 或 WCF SQL 傳送埠上的動作會設定為與您在選取的所有作業都有關的動態動作[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]時產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="3de49-336">If you import this binding file, the action on the WCF-Custom or WCF-SQL send port is set to a dynamic action involving all the operations you selected in the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] while generating the schema.</span></span> <span data-ttu-id="3de49-337">複合作業中，您必須取代的動態 「 CompositeOperation 」 動作。</span><span class="sxs-lookup"><span data-stu-id="3de49-337">For a composite operation, you must replace the dynamic action with “CompositeOperation”.</span></span>  
  
## <a name="starting-the-application"></a><span data-ttu-id="3de49-338">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="3de49-338">Starting the Application</span></span>  
 <span data-ttu-id="3de49-339">您必須啟動 BizTalk 應用程式執行的 SQL Server 資料庫上的複合作業。</span><span class="sxs-lookup"><span data-stu-id="3de49-339">You must start the BizTalk application for performing composite operations on the SQL Server database.</span></span> <span data-ttu-id="3de49-340">如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="3de49-340">For instructions on starting a BizTalk application, see [How to Start an Orchestration](../../core/how-to-start-an-orchestration.md).</span></span>
  
 <span data-ttu-id="3de49-341">在這個階段，請確定：</span><span class="sxs-lookup"><span data-stu-id="3de49-341">At this stage, make sure:</span></span>  
  
-   <span data-ttu-id="3de49-342">FILE 接收埠以接收要求訊息的協調流程執行。</span><span class="sxs-lookup"><span data-stu-id="3de49-342">The FILE receive port to receive request messages for the orchestration is running.</span></span>  
  
-   <span data-ttu-id="3de49-343">FILE 傳送埠，以接收回應訊息從協調流程正在執行。</span><span class="sxs-lookup"><span data-stu-id="3de49-343">The FILE send port to receive the response messages from the orchestration is running.</span></span>  
  
-   <span data-ttu-id="3de49-344">Wcf-custom 或 WCF SQL 傳送埠將訊息傳送至 SQL Server 資料庫正在執行。</span><span class="sxs-lookup"><span data-stu-id="3de49-344">The WCF-Custom or WCF-SQL send port to send messages to the SQL Server database is running.</span></span>  
  
-   <span data-ttu-id="3de49-345">BizTalk 協調流程的作業正在執行。</span><span class="sxs-lookup"><span data-stu-id="3de49-345">The BizTalk orchestration for the operation is running.</span></span>  
  
## <a name="executing-the-operation"></a><span data-ttu-id="3de49-346">執行作業</span><span class="sxs-lookup"><span data-stu-id="3de49-346">Executing the Operation</span></span>  
 <span data-ttu-id="3de49-347">執行應用程式之後，您必須先卸除要求訊息到檔案接收位置。</span><span class="sxs-lookup"><span data-stu-id="3de49-347">After you run the application, you must drop a request message to the FILE receive location.</span></span> <span data-ttu-id="3de49-348">要求訊息的結構描述必須符合您稍早建立的複合作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3de49-348">The schema for the request message must conform to the schema for the composite operations you created earlier.</span></span> <span data-ttu-id="3de49-349">例如，員工資料表中插入記錄、 叫用的 GET_LAST_EMP_DATA 預存程序，並從 EMPLOYEE 資料表中刪除記錄的要求訊息是：</span><span class="sxs-lookup"><span data-stu-id="3de49-349">For example, a request message that inserts a record in the EMPLOYEE table, invokes the GET_LAST_EMP_DATA stored procedure, and deletes a record from the EMPLOYEE table is:</span></span>  
  
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
  
 <span data-ttu-id="3de49-350">請參閱[複合操作的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)如需有關執行 SQL Server 上的複合作業的要求訊息結構描述資料庫使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3de49-350">See [Message Schemas for Composite Operations](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md) for more information about the request message schema for performing composite operations on the SQL Server database using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
 <span data-ttu-id="3de49-351">協調流程取用訊息，並將它傳送到 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3de49-351">The orchestration consumes the message and sends it to the SQL Server database.</span></span> <span data-ttu-id="3de49-352">從 SQL Server 資料庫的回應會儲存在其他的協調流程中定義的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="3de49-352">The response from the SQL Server database is saved at the other FILE location defined as part of the orchestration.</span></span> <span data-ttu-id="3de49-353">比方說，是從先前的要求訊息的 SQL Server 資料庫的回應：</span><span class="sxs-lookup"><span data-stu-id="3de49-353">For example, the response from the SQL Server database for the preceding request message is:</span></span>  
  
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
  
 <span data-ttu-id="3de49-354">上述的回應會包含多個結果集對應複合作業的一部分執行的不同作業。</span><span class="sxs-lookup"><span data-stu-id="3de49-354">The preceding response contains multiple result sets corresponding the different operations performed as part of the composite operation.</span></span> <span data-ttu-id="3de49-355">例如，`InsertResult`元素包含 10080，這是新加入的記錄的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="3de49-355">For example, the `InsertResult` element contains 10080, which is the unique identifier for the newly added record.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="3de49-356">最佳作法</span><span class="sxs-lookup"><span data-stu-id="3de49-356">Best Practices</span></span>  
 <span data-ttu-id="3de49-357">您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。</span><span class="sxs-lookup"><span data-stu-id="3de49-357">After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the binding file.</span></span> <span data-ttu-id="3de49-358">一旦產生繫結檔案時，可以組態設定匯入檔案，使您不需要建立項目，例如傳送埠和接收相同的協調流程連接埠。</span><span class="sxs-lookup"><span data-stu-id="3de49-358">Once you generate a binding file, you can import the configuration settings from the file, so that you do not need to create items such as send ports and receive ports for the same orchestration.</span></span> <span data-ttu-id="3de49-359">如需繫結檔案的詳細資訊，請參閱[重複使用配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="3de49-359">For more information about binding files, see [Reuse adapter bindings](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3de49-360">請參閱</span><span class="sxs-lookup"><span data-stu-id="3de49-360">See Also</span></span>  
[<span data-ttu-id="3de49-361">使用 SQL 配接器開發 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="3de49-361">Develop BizTalk applications using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)