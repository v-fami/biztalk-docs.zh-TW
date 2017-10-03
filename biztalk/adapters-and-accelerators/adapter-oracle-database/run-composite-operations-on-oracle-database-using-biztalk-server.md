---
title: "執行複合操作 Oracle 資料庫使用 BizTalk Server 上 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf47d95e-cdf1-4c9b-a15a-7cf123d0ea6d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54d0c9147f1e2aba18d66772553925ee6f5c8786
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="run-composite-operations-on-oracle-database-using-biztalk-server"></a><span data-ttu-id="87987-102">執行複合操作 Oracle 資料庫使用 BizTalk Server 上</span><span class="sxs-lookup"><span data-stu-id="87987-102">Run Composite Operations on Oracle Database using BizTalk Server</span></span>
<span data-ttu-id="87987-103">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓配接器執行複合操作 Oracle 資料庫上的用戶端。</span><span class="sxs-lookup"><span data-stu-id="87987-103">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] enables adapter clients to perform composite operations on Oracle database.</span></span> <span data-ttu-id="87987-104">複合作業可包括：</span><span class="sxs-lookup"><span data-stu-id="87987-104">A composite operation can include:</span></span>  
  
-   <span data-ttu-id="87987-105">插入、 更新、 刪除和選取資料表和檢視表上的作業。</span><span class="sxs-lookup"><span data-stu-id="87987-105">Insert, Update, Delete, and Select operations on tables and views.</span></span>  
  
-   <span data-ttu-id="87987-106">預存程序和函式，內部或外部的封裝。</span><span class="sxs-lookup"><span data-stu-id="87987-106">Stored procedures and functions, inside or outside a package.</span></span>  
  
 <span data-ttu-id="87987-107">單一複合作業可以有任意數目的這些作業，以任何順序。</span><span class="sxs-lookup"><span data-stu-id="87987-107">A single composite operation can have any number of these operations, in any order.</span></span> <span data-ttu-id="87987-108">比方說，您可以有兩個插入後面刪除，以及最後的預存程序執行。</span><span class="sxs-lookup"><span data-stu-id="87987-108">For example, you can have two inserts followed by a delete, and finally a stored procedure execution.</span></span> <span data-ttu-id="87987-109">此外，您可以有不同的資料庫資料表或檢視表為目標的不同作業。</span><span class="sxs-lookup"><span data-stu-id="87987-109">Also, you can have different operations targeting different database tables or views.</span></span> <span data-ttu-id="87987-110">如需配接器如何支援複合操作的詳細資訊，請參閱[Oracle 資料庫中執行複合操作](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-in-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="87987-110">For more information about how the adapter supports composite operations, see [Performing Composite Operations in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-in-oracle-database.md).</span></span> <span data-ttu-id="87987-111">複合操作的 SOAP 訊息結構的相關資訊，請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md)。</span><span class="sxs-lookup"><span data-stu-id="87987-111">For information about the structure of the SOAP message for composite operations, see [Message Schemas for the Composite Operation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md).</span></span>  
  
## <a name="how-to-perform-composite-operations-on-oracle-database"></a><span data-ttu-id="87987-112">如何執行複合操作 Oracle 資料庫上？</span><span class="sxs-lookup"><span data-stu-id="87987-112">How to Perform Composite Operations on Oracle Database?</span></span>  
 <span data-ttu-id="87987-113">使用 Oracle 資料庫上執行操作[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="87987-113">Performing an operation on Oracle database using [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] involves procedural tasks described in [Building blocks to develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md).</span></span> <span data-ttu-id="87987-114">若要執行複合操作 Oracle 資料庫上的，這些工作包括：</span><span class="sxs-lookup"><span data-stu-id="87987-114">To perform composite operations on Oracle database, these tasks are:</span></span>  
  
1.  <span data-ttu-id="87987-115">建立 BizTalk 專案中的[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並產生您想要叫用的所有作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="87987-115">Create a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and generate schema for all the operations you want to invoke.</span></span>  
  
2.  <span data-ttu-id="87987-116">手動建立結構描述檔案，其中包含您在上一個步驟中產生的所有結構描述的參考。</span><span class="sxs-lookup"><span data-stu-id="87987-116">Manually create a schema file that includes references to all the schemas you generated in the previous step.</span></span>  
  
3.  <span data-ttu-id="87987-117">建立傳送和從 Oracle 資料庫接收訊息的 BizTalk 專案中的訊息。</span><span class="sxs-lookup"><span data-stu-id="87987-117">Create messages in the BizTalk project for sending and receiving messages from Oracle database.</span></span> <span data-ttu-id="87987-118">這些訊息必須符合您在上一個步驟中建立的要求和回應結構描述。</span><span class="sxs-lookup"><span data-stu-id="87987-118">These messages must conform to the request and response schema you created in the previous step.</span></span>  
  
4.  <span data-ttu-id="87987-119">建立協調流程叫用 Oracle 資料庫上的複合作業。</span><span class="sxs-lookup"><span data-stu-id="87987-119">Create an orchestration to invoke the composite operation on Oracle database.</span></span>  
  
5.  <span data-ttu-id="87987-120">建置和部署 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="87987-120">Build and deploy the BizTalk project.</span></span>  
  
6.  <span data-ttu-id="87987-121">設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="87987-121">Configure the BizTalk application by creating physical send and receive ports.</span></span>  
  
7.  <span data-ttu-id="87987-122">啟動 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="87987-122">Start the BizTalk application.</span></span>  
  
 <span data-ttu-id="87987-123">本主題提供有關如何執行這些工作的指示。</span><span class="sxs-lookup"><span data-stu-id="87987-123">This topic provides instructions on how to perform these tasks.</span></span>  
  
## <a name="generating-schema"></a><span data-ttu-id="87987-124">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="87987-124">Generating Schema</span></span>  
 <span data-ttu-id="87987-125">本主題中，為了示範如何執行複合操作，我們會執行相同的順序的下列工作：</span><span class="sxs-lookup"><span data-stu-id="87987-125">In this topic, to demonstrate how to perform composite operations, we will perform the following tasks in the same order:</span></span>  
  
-   <span data-ttu-id="87987-126">將記錄插入 ACCOUNTACTIVITY 資料表。</span><span class="sxs-lookup"><span data-stu-id="87987-126">Insert record into the ACCOUNTACTIVITY table.</span></span>  
  
-   <span data-ttu-id="87987-127">藉由叫用 GET_ALL_ACTIVITY 內的程序 ACCOUNT_PKG 封裝擷取 ACCOUNTACTIVITY 資料表中的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="87987-127">Retrieve all the records in the ACCOUNTACTIVITY table by invoking the GET_ALL_ACTIVITY procedure within the ACCOUNT_PKG package.</span></span>  
  
-   <span data-ttu-id="87987-128">從 ACCOUNTACTIVITY 資料表刪除記錄。</span><span class="sxs-lookup"><span data-stu-id="87987-128">Delete the record from the ACCOUNTACTIVITY table.</span></span>  
  
 <span data-ttu-id="87987-129">執行與範例來建立 ACCOUNTACTIVITY 資料表所提供的指令碼。</span><span class="sxs-lookup"><span data-stu-id="87987-129">Run the scripts provided with the samples to create the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="87987-130">如需這些範例的詳細資訊，請參閱[結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="87987-130">For more information about the samples, see [Schema Samples](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md).</span></span>  
  
 <span data-ttu-id="87987-131">您必須建立 BizTalk 專案，並使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="87987-131">You must create a BizTalk project and use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate the schema.</span></span> <span data-ttu-id="87987-132">請參閱[擷取 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)如需有關如何產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="87987-132">See [Retrieve metadata for Oracle Database operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) for more information about how to generate schemas.</span></span>  
  
## <a name="creating-a-composite-schema-definition"></a><span data-ttu-id="87987-133">建立複合的結構描述定義</span><span class="sxs-lookup"><span data-stu-id="87987-133">Creating a Composite Schema Definition</span></span>  
 <span data-ttu-id="87987-134">您現在必須建立複合的結構描述中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]參考您針對個別作業所建立之結構描述的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="87987-134">You must now create a composite schema in the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] BizTalk project that references the schemas you created for the individual operations.</span></span> <span data-ttu-id="87987-135">執行下列步驟，以建立複合的結構描述定義。</span><span class="sxs-lookup"><span data-stu-id="87987-135">Perform the following steps to create a composite schema definition.</span></span>  
  
#### <a name="to-add-a-composite-schema-definition"></a><span data-ttu-id="87987-136">若要加入複合的結構描述定義</span><span class="sxs-lookup"><span data-stu-id="87987-136">To add a composite schema definition</span></span>  
  
1.  <span data-ttu-id="87987-137">將結構描述檔案中的 BizTalk 專案加入[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="87987-137">Add a schema file to the BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="87987-138">以滑鼠右鍵按一下方案名稱，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="87987-138">Right-click the solution name, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="87987-139">在**加入新項目**對話方塊中，從**類別**方塊中，按一下**結構描述檔案**。</span><span class="sxs-lookup"><span data-stu-id="87987-139">In the **Add New Item** dialog box, from the **Categories** box, click **Schema Files**.</span></span> <span data-ttu-id="87987-140">從**範本**方塊中，按一下**結構描述**。</span><span class="sxs-lookup"><span data-stu-id="87987-140">From the **Templates** box, click **Schema**.</span></span> <span data-ttu-id="87987-141">指定結構描述檔案的名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="87987-141">Specify a name for the schema file and click **OK**.</span></span>  
  
     <span data-ttu-id="87987-142">此範例中，結構描述檔案名稱指定為`CompositeSchema.xsd`。</span><span class="sxs-lookup"><span data-stu-id="87987-142">For this example, specify the schema file name as `CompositeSchema.xsd`.</span></span>  
  
2.  <span data-ttu-id="87987-143">將參考加入至您想要執行的不同作業產生的結構描述。</span><span class="sxs-lookup"><span data-stu-id="87987-143">Add references to the schema generated for the different operations that you want to perform.</span></span> <span data-ttu-id="87987-144">在此範例中，不同的結構描述產生的作業如下：</span><span class="sxs-lookup"><span data-stu-id="87987-144">In this example, the different schemas generated for operations are:</span></span>  
  
    -   <span data-ttu-id="87987-145">OracleDBBinding.xsd ACCOUNTACTIVITY 資料表的 Insert 和 Delete 作業。</span><span class="sxs-lookup"><span data-stu-id="87987-145">OracleDBBinding.xsd, for Insert and Delete operations on ACCOUNTACTIVITY table.</span></span>  
  
    -   <span data-ttu-id="87987-146">OracleDBBinding2.xsd GET_ALL_ACTIVITY 程序。</span><span class="sxs-lookup"><span data-stu-id="87987-146">OracleDBBinding2.xsd, for the GET_ALL_ACTIVITY procedure.</span></span>  
  
     <span data-ttu-id="87987-147">若要加入的參考：</span><span class="sxs-lookup"><span data-stu-id="87987-147">To add references:</span></span>  
  
    1.  <span data-ttu-id="87987-148">以滑鼠右鍵按一下根**\<結構描述 >**中 CompositeSchema.xsd，按一下節點**屬性**。</span><span class="sxs-lookup"><span data-stu-id="87987-148">Right-click the root **\<Schema>** node in the CompositeSchema.xsd, and click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="87987-149">在**屬性**方塊中，按一下省略符號按鈕**（...）**針對**匯入**屬性。</span><span class="sxs-lookup"><span data-stu-id="87987-149">In the **Property** box, click the ellipsis button **(…)** against the **Imports** property.</span></span>  
  
         <span data-ttu-id="87987-150">![匯入結構描述定義](../../adapters-and-accelerators/adapter-oracle-database/media/d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca.gif "d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca")</span><span class="sxs-lookup"><span data-stu-id="87987-150">![Import schema definitions](../../adapters-and-accelerators/adapter-oracle-database/media/d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca.gif "d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca")</span></span>  
  
    3.  <span data-ttu-id="87987-151">在**匯入**對話方塊中，從**匯入新結構描述為**清單中，選取**XSD 匯入**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="87987-151">In the **Imports** dialog box, from the **Import new schema as** list, select **XSD Import**, and then click **Add**.</span></span>  
  
    4.  <span data-ttu-id="87987-152">在**BizTalk 型別選擇器**對話方塊方塊中，展開 BizTalk 專案名稱節點，展開**結構描述**，然後選取您要匯入的結構描述。</span><span class="sxs-lookup"><span data-stu-id="87987-152">In the **BizTalk Type Picker** dialog box, expand the BizTalk project name node, expand **Schemas**, and then select the schema you want to import.</span></span> <span data-ttu-id="87987-153">此範例中，選取 < BizTalk_project_name >。OracleDBBinding.xsd。</span><span class="sxs-lookup"><span data-stu-id="87987-153">For this example, select <BizTalk_project_name>.OracleDBBinding.xsd.</span></span> <span data-ttu-id="87987-154">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="87987-154">Click **OK**.</span></span>  
  
         <span data-ttu-id="87987-155">重複此步驟，匯入 < BizTalk_project_name >。OracleDBBinding2.xsd 太。</span><span class="sxs-lookup"><span data-stu-id="87987-155">Repeat this step to import <BizTalk_project_name>.OracleDBBinding2.xsd too.</span></span>  
  
    5.  <span data-ttu-id="87987-156">在**匯入**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="87987-156">In the **Imports** dialog box, click **OK**.</span></span>  
  
3.  <span data-ttu-id="87987-157">將兩個子節點加入至根結構描述節點。</span><span class="sxs-lookup"><span data-stu-id="87987-157">Add two child nodes to the root schema node.</span></span> <span data-ttu-id="87987-158">一個子節點對應至要求結構描述執行複合作業。</span><span class="sxs-lookup"><span data-stu-id="87987-158">One child node corresponds to the request schema for performing the composite operation.</span></span> <span data-ttu-id="87987-159">另一個子節點對應至回應結構描述。</span><span class="sxs-lookup"><span data-stu-id="87987-159">The other child node corresponds to the response schema.</span></span> <span data-ttu-id="87987-160">對應至要求結構描述的節點可以有任何名稱。</span><span class="sxs-lookup"><span data-stu-id="87987-160">The node that corresponds to the request schema can have any name.</span></span> <span data-ttu-id="87987-161">對應至回應結構描述的節點必須呼叫 < request_schema_node > 回應。</span><span class="sxs-lookup"><span data-stu-id="87987-161">The node that corresponds to the response schema must be called <request_schema_node>Response.</span></span> <span data-ttu-id="87987-162">針對此範例中，我們會呼叫要求結構描述節點，做為**要求**。</span><span class="sxs-lookup"><span data-stu-id="87987-162">For this example, we will call the request schema node as **Request**.</span></span> <span data-ttu-id="87987-163">因此，呼叫的回應結構描述節點**RequestResponse**。</span><span class="sxs-lookup"><span data-stu-id="87987-163">So, the response schema node is called **RequestResponse**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87987-164">根據預設，**根**節點也會加入至新的結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="87987-164">By default, a **Root** node is also added to a new schema file.</span></span> <span data-ttu-id="87987-165">您可以重新命名**根**節點**要求**。</span><span class="sxs-lookup"><span data-stu-id="87987-165">You can rename the **Root** node to **Request**.</span></span> <span data-ttu-id="87987-166">若要重新命名的節點，以滑鼠右鍵按一下節點名稱，然後按一下**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="87987-166">To rename a node, right-click the node name and click **Rename**.</span></span>  
  
     <span data-ttu-id="87987-167">若要加入的節點下**\<結構描述 >**節點：</span><span class="sxs-lookup"><span data-stu-id="87987-167">To add a node under the **\<Schema>** node:</span></span>  
  
    1.  <span data-ttu-id="87987-168">以滑鼠右鍵按一下**\<結構描述 >**節點，指向**插入結構描述節點**，然後按一下**子記錄**。</span><span class="sxs-lookup"><span data-stu-id="87987-168">Right-click the **\<Schema>** node, point to **Insert Schema Node**, and click **Child Record**.</span></span>  
  
    2.  <span data-ttu-id="87987-169">重新命名新的節點**RequestResponse**。</span><span class="sxs-lookup"><span data-stu-id="87987-169">Rename the new node to **RequestResponse**.</span></span>  
  
4.  <span data-ttu-id="87987-170">加入子節點底下**要求**對應到複合作業的一部分，您將執行每個作業的要求結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="87987-170">Add child nodes under the **Request** node that correspond to the request schema for each operation that you will perform as part of the composite operation.</span></span> <span data-ttu-id="87987-171">對於此範例中，您必須將對應於下列子節點：</span><span class="sxs-lookup"><span data-stu-id="87987-171">For this example, you must add child nodes corresponding to the following:</span></span>  
  
    -   <span data-ttu-id="87987-172">插入和刪除 ACCOUNTACTIVITY 資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="87987-172">Insert and Delete operations on the ACCOUNTACTIVITY table.</span></span>  
  
    -   <span data-ttu-id="87987-173">GET_ALL_ACTIVITY 程序。</span><span class="sxs-lookup"><span data-stu-id="87987-173">GET_ALL_ACTIVITY procedure.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="87987-174">您必須將節點加入您要執行作業的順序相同。</span><span class="sxs-lookup"><span data-stu-id="87987-174">You must add the nodes in the same order in which you want to perform the operations.</span></span> <span data-ttu-id="87987-175">例如，如果您想要插入的記錄，然後執行預存程序，然後刪除記錄，您必須先新增的節點代表插入作業，後面接著預存程序中，節點和最後一個刪除作業。</span><span class="sxs-lookup"><span data-stu-id="87987-175">For example, if you want to insert a record, then execute a stored procedure, and then delete a record you must first add a node for the Insert operation, followed by a node for the stored procedure, and finally a node for the Delete operation.</span></span>  
  
     <span data-ttu-id="87987-176">若要加入至子節點**要求**節點：</span><span class="sxs-lookup"><span data-stu-id="87987-176">To add child nodes to the **Request** node:</span></span>  
  
    1.  <span data-ttu-id="87987-177">以滑鼠右鍵按一下**要求**節點，指向**插入結構描述節點**，然後按一下 **子記錄**。</span><span class="sxs-lookup"><span data-stu-id="87987-177">Right-click the **Request** node, point to **Insert Schema Node**, and then click  **Child Record**.</span></span>  
  
         <span data-ttu-id="87987-178">![插入結構描述的子節點](../../adapters-and-accelerators/adapter-oracle-database/media/58992131-13a6-45c3-9513-5c0995091fae.gif "58992131-13a6-45c3-9513-5c0995091fae")</span><span class="sxs-lookup"><span data-stu-id="87987-178">![Insert child nodes for a schema](../../adapters-and-accelerators/adapter-oracle-database/media/58992131-13a6-45c3-9513-5c0995091fae.gif "58992131-13a6-45c3-9513-5c0995091fae")</span></span>  
  
    2.  <span data-ttu-id="87987-179">重新命名為對應至複合作業的一部分執行的操作的要求結構描述的記錄。</span><span class="sxs-lookup"><span data-stu-id="87987-179">Rename the record to correspond to a request schema for an operation that you perform as part of the composite operation.</span></span> <span data-ttu-id="87987-180">例如，重新命名 「 插入 」 至節點。</span><span class="sxs-lookup"><span data-stu-id="87987-180">For example, rename the node to “Insert”.</span></span>  
  
    3.  <span data-ttu-id="87987-181">地圖**插入**ACCOUNTACTIVITY 資料表的 Insert 作業的要求結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="87987-181">Map the **Insert** node to the request schema for the Insert operation on the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="87987-182">若要這樣做，請以滑鼠右鍵按一下**插入**節點，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="87987-182">To do so, right-click the **Insert** node, and click **Properties**.</span></span> <span data-ttu-id="87987-183">在**屬性** 方塊中，從**資料結構型別**清單中，選取**插入 （參考）**。</span><span class="sxs-lookup"><span data-stu-id="87987-183">In the **Properties** box, from the **Data Structure Type** list, select **Insert (Reference)**.</span></span>  
  
         <span data-ttu-id="87987-184">![將子節點對應至要求結構描述](../../adapters-and-accelerators/adapter-oracle-database/media/b4ebd3c7-14e5-4c37-abd7-83f0b4db4c9e.gif "b4ebd3c7-14e5-4c37-abd7-83f0b4db4c9e")</span><span class="sxs-lookup"><span data-stu-id="87987-184">![Map child nodes to request schema](../../adapters-and-accelerators/adapter-oracle-database/media/b4ebd3c7-14e5-4c37-abd7-83f0b4db4c9e.gif "b4ebd3c7-14e5-4c37-abd7-83f0b4db4c9e")</span></span>  
  
    4.  <span data-ttu-id="87987-185">重複這些步驟來加入 GET_ALL_ACTIVITY 預存程序和刪除作業的要求結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="87987-185">Repeat these steps to add nodes for the request schemas for GET_ALL_ACTIVITY stored procedure and the Delete operation.</span></span> <span data-ttu-id="87987-186">指定節點名稱，然後將它們對應至對應的結構描述，如下列表格中所述。</span><span class="sxs-lookup"><span data-stu-id="87987-186">Specify the node names and map them to the corresponding schema as mentioned in the following table.</span></span>  
  
        |<span data-ttu-id="87987-187">節點名稱</span><span class="sxs-lookup"><span data-stu-id="87987-187">Node name</span></span>|<span data-ttu-id="87987-188">對應至結構描述</span><span class="sxs-lookup"><span data-stu-id="87987-188">Mapped to schema</span></span>|  
        |---------------|----------------------|  
        |<span data-ttu-id="87987-189">GET_ALL_ACTIVITY</span><span class="sxs-lookup"><span data-stu-id="87987-189">GET_ALL_ACTIVITY</span></span>|<span data-ttu-id="87987-190">GET_ALL_ACTIVITY （參考）</span><span class="sxs-lookup"><span data-stu-id="87987-190">GET_ALL_ACTIVITY (Reference)</span></span>|  
        |<span data-ttu-id="87987-191">DELETE</span><span class="sxs-lookup"><span data-stu-id="87987-191">Delete</span></span>|<span data-ttu-id="87987-192">刪除 （參考）</span><span class="sxs-lookup"><span data-stu-id="87987-192">Delete (Reference)</span></span>|  
  
5.  <span data-ttu-id="87987-193">加入子節點底下**RequestResponse**對應到複合作業的一部分，您將執行每個作業的回應結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="87987-193">Add child nodes under the **RequestResponse** node that correspond to the response schema for each operation that you will perform as part of the composite operation.</span></span> <span data-ttu-id="87987-194">對於此範例中，您必須將對應於下列子節點：</span><span class="sxs-lookup"><span data-stu-id="87987-194">For this example, you must add child nodes corresponding to the following:</span></span>  
  
    -   <span data-ttu-id="87987-195">插入和刪除 ACCOUNTACTIVITY 資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="87987-195">Insert and Delete operations on the ACCOUNTACTIVITY table.</span></span>  
  
    -   <span data-ttu-id="87987-196">GET_ALL_ACTIVITY 預存程序。</span><span class="sxs-lookup"><span data-stu-id="87987-196">GET_ALL_ACTIVITY stored procedure.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="87987-197">您必須加入子節點下的子節點的順序相同**要求**節點。</span><span class="sxs-lookup"><span data-stu-id="87987-197">You must add the child nodes in the same order as the child nodes under the **Request** node.</span></span>  
  
     <span data-ttu-id="87987-198">若要加入至子節點**RequestResponse**節點：</span><span class="sxs-lookup"><span data-stu-id="87987-198">To add child nodes to the **RequestResponse** node:</span></span>  
  
    1.  <span data-ttu-id="87987-199">以滑鼠右鍵按一下**RequestResponse**節點，指向**插入結構描述節點**，然後按一下**子記錄**。</span><span class="sxs-lookup"><span data-stu-id="87987-199">Right-click the **RequestResponse** node, point to **Insert Schema Node**, and click **Child Record**.</span></span>  
  
    2.  <span data-ttu-id="87987-200">重新命名為對應至複合作業的一部分執行的操作的回應結構描述的記錄。</span><span class="sxs-lookup"><span data-stu-id="87987-200">Rename the record to correspond to a response schema for an operation that you perform as part of the composite operation.</span></span> <span data-ttu-id="87987-201">例如，重新命名 「 InsertResponse"的節點。</span><span class="sxs-lookup"><span data-stu-id="87987-201">For example, rename the node to “InsertResponse”.</span></span>  
  
    3.  <span data-ttu-id="87987-202">地圖**InsertResponse** ACCOUNTACTIVITY 資料表的 Insert 作業的回應結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="87987-202">Map the **InsertResponse** node to the response schema for the Insert operation on the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="87987-203">若要這樣做，請以滑鼠右鍵按一下**InsertResponse**節點，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="87987-203">To do so, right-click the **InsertResponse** node, and click **Properties**.</span></span> <span data-ttu-id="87987-204">在**屬性** 方塊中，從**資料結構型別**清單中，選取**InsertResponse （參考）**。</span><span class="sxs-lookup"><span data-stu-id="87987-204">In the **Properties** box, from the **Data Structure Type** list, select **InsertResponse (Reference)**.</span></span>  
  
    4.  <span data-ttu-id="87987-205">重複這些步驟來加入 GET_ALL_ACTIVITY 預存程序和刪除作業的回應結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="87987-205">Repeat these steps to add nodes for the response schemas for the GET_ALL_ACTIVITY stored procedure and the Delete operation.</span></span> <span data-ttu-id="87987-206">指定節點名稱，然後將它們對應至對應的結構描述，如下列表格中所述。</span><span class="sxs-lookup"><span data-stu-id="87987-206">Specify the node names and map them to the corresponding schema as mentioned in the following table.</span></span>  
  
        |<span data-ttu-id="87987-207">節點名稱</span><span class="sxs-lookup"><span data-stu-id="87987-207">Node name</span></span>|<span data-ttu-id="87987-208">對應至結構描述</span><span class="sxs-lookup"><span data-stu-id="87987-208">Mapped to schema</span></span>|  
        |---------------|----------------------|  
        |<span data-ttu-id="87987-209">GET_ALL_ACTIVITYResponse</span><span class="sxs-lookup"><span data-stu-id="87987-209">GET_ALL_ACTIVITYResponse</span></span>|<span data-ttu-id="87987-210">GET_ALL_ACTIVITYResponse （參考）</span><span class="sxs-lookup"><span data-stu-id="87987-210">GET_ALL_ACTIVITYResponse (Reference)</span></span>|  
        |<span data-ttu-id="87987-211">DeleteResponse</span><span class="sxs-lookup"><span data-stu-id="87987-211">DeleteResponse</span></span>|<span data-ttu-id="87987-212">DeleteResponse （參考）</span><span class="sxs-lookup"><span data-stu-id="87987-212">DeleteResponse (Reference)</span></span>|  
  
6.  <span data-ttu-id="87987-213">儲存**CompositeSchema.xsd**檔案。</span><span class="sxs-lookup"><span data-stu-id="87987-213">Save the **CompositeSchema.xsd** file.</span></span>  
  
## <a name="defining-messages-and-message-types"></a><span data-ttu-id="87987-214">定義訊息和訊息類型</span><span class="sxs-lookup"><span data-stu-id="87987-214">Defining Messages and Message Types</span></span>  
 <span data-ttu-id="87987-215">您在最後一個步驟中建立複合結構描述會描述 「 類型 」 所需的協調流程中的訊息。</span><span class="sxs-lookup"><span data-stu-id="87987-215">The composite schema that you created in the last step describes the “types” required for the messages in an orchestration.</span></span> <span data-ttu-id="87987-216">訊息通常是為其型別由對應的結構描述所定義的變數。</span><span class="sxs-lookup"><span data-stu-id="87987-216">A message is typically a variable, the type for which is defined by the corresponding schema.</span></span> <span data-ttu-id="87987-217">您現在必須建立協調流程的訊息，並將它們連結至您在上一個步驟中建立的結構描述。</span><span class="sxs-lookup"><span data-stu-id="87987-217">You must now create messages for the orchestration and link them to schema you created in the previous step.</span></span>  
  
#### <a name="to-create-messages-and-link-to-schema"></a><span data-ttu-id="87987-218">建立訊息，以及連結至結構描述</span><span class="sxs-lookup"><span data-stu-id="87987-218">To create messages and link to schema</span></span>  
  
1.  <span data-ttu-id="87987-219">中的 BizTalk 專案中新增協調流程[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="87987-219">Add an orchestration to the BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="87987-220">從 方案總管 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="87987-220">From Solution Explorer, right-click the BizTalk project name, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="87987-221">輸入 BizTalk 協調流程的名稱，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="87987-221">Type a name for the BizTalk orchestration, and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="87987-222">如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。</span><span class="sxs-lookup"><span data-stu-id="87987-222">Open the Orchestration View window of the BizTalk project, if it is not already open.</span></span> <span data-ttu-id="87987-223">若要這樣做，請按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="87987-223">To do so, click **View**, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
3.  <span data-ttu-id="87987-224">在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。</span><span class="sxs-lookup"><span data-stu-id="87987-224">In Orchestration View, right-click **Messages**, and then click **New Message**.</span></span>  
  
4.  <span data-ttu-id="87987-225">以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="87987-225">Right-click the newly created message, and then select **Properties Window**.</span></span>  
  
5.  <span data-ttu-id="87987-226">在**屬性**窗格**Message_1**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="87987-226">In the **Properties** pane for the **Message_1**, do the following:</span></span>  
  
    |<span data-ttu-id="87987-227">使用</span><span class="sxs-lookup"><span data-stu-id="87987-227">Use this</span></span>|<span data-ttu-id="87987-228">動作</span><span class="sxs-lookup"><span data-stu-id="87987-228">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="87987-229">識別碼</span><span class="sxs-lookup"><span data-stu-id="87987-229">Identifier</span></span>|<span data-ttu-id="87987-230">輸入 `Request`</span><span class="sxs-lookup"><span data-stu-id="87987-230">Type `Request`</span></span>|  
    |<span data-ttu-id="87987-231">訊息類型</span><span class="sxs-lookup"><span data-stu-id="87987-231">Message Type</span></span>|<span data-ttu-id="87987-232">從下拉式清單中，展開 **結構描述**，然後選取*Composite_Op.CompositeSchema.Request*Composite_Op 所在的 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="87987-232">From the drop-down list, expand **Schemas**, and then select *Composite_Op.CompositeSchema.Request*, where Composite_Op is the name of your BizTalk project.</span></span> <span data-ttu-id="87987-233">CompositeSchema 是手動建立的複合作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="87987-233">CompositeSchema is the schema you created manually for the composite operations.</span></span>|  
  
6.  <span data-ttu-id="87987-234">重複步驟 2 來建立新的訊息。</span><span class="sxs-lookup"><span data-stu-id="87987-234">Repeat step 2 to create a new message.</span></span> <span data-ttu-id="87987-235">在**屬性**窗格新訊息中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="87987-235">In the **Properties** pane for the new message, do the following:</span></span>  
  
    |<span data-ttu-id="87987-236">使用</span><span class="sxs-lookup"><span data-stu-id="87987-236">Use this</span></span>|<span data-ttu-id="87987-237">動作</span><span class="sxs-lookup"><span data-stu-id="87987-237">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="87987-238">識別碼</span><span class="sxs-lookup"><span data-stu-id="87987-238">Identifier</span></span>|<span data-ttu-id="87987-239">輸入 `Response`</span><span class="sxs-lookup"><span data-stu-id="87987-239">Type `Response`</span></span>|  
    |<span data-ttu-id="87987-240">訊息類型</span><span class="sxs-lookup"><span data-stu-id="87987-240">Message Type</span></span>|<span data-ttu-id="87987-241">從下拉式清單中，展開 **結構描述**，然後選取*Composite_Op.CompositeSchema.RequestResponse*。</span><span class="sxs-lookup"><span data-stu-id="87987-241">From the drop-down list, expand **Schemas**, and then select *Composite_Op.CompositeSchema.RequestResponse*.</span></span>|  
  
## <a name="setting-up-the-orchestration"></a><span data-ttu-id="87987-242">設定協調流程</span><span class="sxs-lookup"><span data-stu-id="87987-242">Setting up the Orchestration</span></span>  
 <span data-ttu-id="87987-243">您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行複合操作 Oracle 資料庫上的。</span><span class="sxs-lookup"><span data-stu-id="87987-243">You must create a BizTalk orchestration to use [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for performing composite operations on Oracle database.</span></span> <span data-ttu-id="87987-244">在此協調流程中，卸除要求訊息已定義的接收位置。</span><span class="sxs-lookup"><span data-stu-id="87987-244">In this orchestration, you drop a request message at a defined receive location.</span></span> <span data-ttu-id="87987-245">要求訊息必須符合您稍早建立的複合結構描述。</span><span class="sxs-lookup"><span data-stu-id="87987-245">The request message must conform to the composite schema you created earlier.</span></span> <span data-ttu-id="87987-246">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會取用這個訊息，並將它傳遞到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="87987-246">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] consumes this message and passes it on to Oracle database.</span></span> <span data-ttu-id="87987-247">從 Oracle 資料庫的回應會儲存到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="87987-247">The response from Oracle database is saved to another location.</span></span> <span data-ttu-id="87987-248">您必須包含傳送和接收圖形，將訊息傳送至 Oracle 資料庫，並接收回應，分別。</span><span class="sxs-lookup"><span data-stu-id="87987-248">You must include Send and Receive shapes to send messages to Oracle database and receive responses, respectively.</span></span> <span data-ttu-id="87987-249">用於執行複合操作的基本協調流程如下所示：</span><span class="sxs-lookup"><span data-stu-id="87987-249">A basic orchestration for performing composite operations resembles the following:</span></span>  
  
 <span data-ttu-id="87987-250">![用於執行複合操作的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb.gif "4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb")</span><span class="sxs-lookup"><span data-stu-id="87987-250">![Orchestration to peform composite operations](../../adapters-and-accelerators/adapter-oracle-database/media/4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb.gif "4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb")</span></span>  
  
### <a name="adding-message-shapes"></a><span data-ttu-id="87987-251">新增訊息圖形</span><span class="sxs-lookup"><span data-stu-id="87987-251">Adding Message Shapes</span></span>  
 <span data-ttu-id="87987-252">請確定您針對每個訊息圖形指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="87987-252">Make sure you specify the following properties for each of the message shapes.</span></span> <span data-ttu-id="87987-253">圖形資料行中所列的名稱是訊息 圖形的名稱，為顯示在剛才提及的協調流程中。</span><span class="sxs-lookup"><span data-stu-id="87987-253">The names listed in the Shape column are the names of the message shapes as displayed in the just-mentioned orchestration.</span></span>  
  
|<span data-ttu-id="87987-254">形狀圖</span><span class="sxs-lookup"><span data-stu-id="87987-254">Shape</span></span>|<span data-ttu-id="87987-255">圖形類型</span><span class="sxs-lookup"><span data-stu-id="87987-255">Shape Type</span></span>|<span data-ttu-id="87987-256">屬性</span><span class="sxs-lookup"><span data-stu-id="87987-256">Properties</span></span>|  
|-----------|----------------|----------------|  
|<span data-ttu-id="87987-257">ReceiveMessage</span><span class="sxs-lookup"><span data-stu-id="87987-257">ReceiveMessage</span></span>|<span data-ttu-id="87987-258">Receive</span><span class="sxs-lookup"><span data-stu-id="87987-258">Receive</span></span>|<span data-ttu-id="87987-259">-設定**名稱**至*ReceiveMessage*</span><span class="sxs-lookup"><span data-stu-id="87987-259">-   Set **Name** to *ReceiveMessage*</span></span><br /><span data-ttu-id="87987-260">-設定**啟動**至*，則為 True*</span><span class="sxs-lookup"><span data-stu-id="87987-260">-   Set **Activate** to *True*</span></span>|  
|<span data-ttu-id="87987-261">SendMessage</span><span class="sxs-lookup"><span data-stu-id="87987-261">SendMessage</span></span>|<span data-ttu-id="87987-262">Send</span><span class="sxs-lookup"><span data-stu-id="87987-262">Send</span></span>|<span data-ttu-id="87987-263">-設定**名稱**至*SendMessage*</span><span class="sxs-lookup"><span data-stu-id="87987-263">-   Set **Name** to *SendMessage*</span></span>|  
|<span data-ttu-id="87987-264">ReceiveResponse</span><span class="sxs-lookup"><span data-stu-id="87987-264">ReceiveResponse</span></span>|<span data-ttu-id="87987-265">Receive</span><span class="sxs-lookup"><span data-stu-id="87987-265">Receive</span></span>|<span data-ttu-id="87987-266">-設定**名稱**至*ReceiveResponse*</span><span class="sxs-lookup"><span data-stu-id="87987-266">-   Set **Name** to *ReceiveResponse*</span></span><br /><span data-ttu-id="87987-267">-設定**啟動**至*False*</span><span class="sxs-lookup"><span data-stu-id="87987-267">-   Set **Activate** to *False*</span></span>|  
|<span data-ttu-id="87987-268">SendResponse</span><span class="sxs-lookup"><span data-stu-id="87987-268">SendResponse</span></span>|<span data-ttu-id="87987-269">Send</span><span class="sxs-lookup"><span data-stu-id="87987-269">Send</span></span>|<span data-ttu-id="87987-270">-設定**名稱**至*SendResponse*</span><span class="sxs-lookup"><span data-stu-id="87987-270">-   Set **Name** to *SendResponse*</span></span>|  
  
### <a name="adding-ports"></a><span data-ttu-id="87987-271">新增連接埠</span><span class="sxs-lookup"><span data-stu-id="87987-271">Adding Ports</span></span>  
 <span data-ttu-id="87987-272">請確定您針對每個邏輯連接埠指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="87987-272">Make sure you specify the following properties for each of the logical ports.</span></span> <span data-ttu-id="87987-273">連接埠資料行中所列的名稱是連接埠的名稱，為顯示協調流程中。</span><span class="sxs-lookup"><span data-stu-id="87987-273">The names listed in the Port column are the names of the ports as displayed in the orchestration.</span></span>  
  
|<span data-ttu-id="87987-274">通訊埠</span><span class="sxs-lookup"><span data-stu-id="87987-274">Port</span></span>|<span data-ttu-id="87987-275">屬性</span><span class="sxs-lookup"><span data-stu-id="87987-275">Properties</span></span>|  
|----------|----------------|  
|<span data-ttu-id="87987-276">MessageIn</span><span class="sxs-lookup"><span data-stu-id="87987-276">MessageIn</span></span>|<span data-ttu-id="87987-277">-設定**識別碼**至*MessageIn*</span><span class="sxs-lookup"><span data-stu-id="87987-277">-   Set **Identifier** to *MessageIn*</span></span><br /><span data-ttu-id="87987-278">-設定**類型**至*MessageInType*</span><span class="sxs-lookup"><span data-stu-id="87987-278">-   Set **Type** to *MessageInType*</span></span><br /><span data-ttu-id="87987-279">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="87987-279">-   Set **Communication Pattern** to *One-Way*</span></span><br /><span data-ttu-id="87987-280">-設定**通訊方向**至*接收*</span><span class="sxs-lookup"><span data-stu-id="87987-280">-   Set **Communication Direction** to *Receive*</span></span>|  
|<span data-ttu-id="87987-281">LOBPort</span><span class="sxs-lookup"><span data-stu-id="87987-281">LOBPort</span></span>|<span data-ttu-id="87987-282">-設定**識別碼**至*LOBPort*</span><span class="sxs-lookup"><span data-stu-id="87987-282">-   Set **Identifier** to *LOBPort*</span></span><br /><span data-ttu-id="87987-283">-設定**類型**至*LOBPortType*</span><span class="sxs-lookup"><span data-stu-id="87987-283">-   Set **Type** to *LOBPortType*</span></span><br /><span data-ttu-id="87987-284">-設定**通訊模式**至*要求-回應*</span><span class="sxs-lookup"><span data-stu-id="87987-284">-   Set **Communication Pattern** to *Request-Response*</span></span><br /><span data-ttu-id="87987-285">-設定**通訊方向**至*傳送接收*</span><span class="sxs-lookup"><span data-stu-id="87987-285">-   Set **Communication Direction** to *Send-Receive*</span></span>|  
|<span data-ttu-id="87987-286">ResponseOut</span><span class="sxs-lookup"><span data-stu-id="87987-286">ResponseOut</span></span>|<span data-ttu-id="87987-287">-設定**識別碼**至*ResponseOut*</span><span class="sxs-lookup"><span data-stu-id="87987-287">-   Set **Identifier** to *ResponseOut*</span></span><br /><span data-ttu-id="87987-288">-設定**類型**至*ResponseOutType*</span><span class="sxs-lookup"><span data-stu-id="87987-288">-   Set **Type** to *ResponseOutType*</span></span><br /><span data-ttu-id="87987-289">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="87987-289">-   Set **Communication Pattern** to *One-Way*</span></span><br /><span data-ttu-id="87987-290">-設定**通訊方向**至*傳送*</span><span class="sxs-lookup"><span data-stu-id="87987-290">-   Set **Communication Direction** to *Send*</span></span>|  
  
### <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a><span data-ttu-id="87987-291">指定訊息的動作圖形，並將它們連接至連接埠</span><span class="sxs-lookup"><span data-stu-id="87987-291">Specify Messages for Action Shapes, and Connect Them to Ports</span></span>  
 <span data-ttu-id="87987-292">下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。</span><span class="sxs-lookup"><span data-stu-id="87987-292">The following table specifies the properties and their values that you should set to specify messages for action shapes and to link the messages to the ports.</span></span> <span data-ttu-id="87987-293">圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。</span><span class="sxs-lookup"><span data-stu-id="87987-293">The names listed in the Shape column are the names of the message shapes as displayed in the orchestration mentioned earlier.</span></span>  
  
|<span data-ttu-id="87987-294">形狀圖</span><span class="sxs-lookup"><span data-stu-id="87987-294">Shape</span></span>|<span data-ttu-id="87987-295">屬性</span><span class="sxs-lookup"><span data-stu-id="87987-295">Properties</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="87987-296">ReceiveMessage</span><span class="sxs-lookup"><span data-stu-id="87987-296">ReceiveMessage</span></span>|<span data-ttu-id="87987-297">-設定**訊息**至*要求*</span><span class="sxs-lookup"><span data-stu-id="87987-297">-   Set **Message** to *Request*</span></span><br /><span data-ttu-id="87987-298">-設定**作業**至*MessageIn.CompositeOp.Request*</span><span class="sxs-lookup"><span data-stu-id="87987-298">-   Set **Operation** to *MessageIn.CompositeOp.Request*</span></span>|  
|<span data-ttu-id="87987-299">SendMessage</span><span class="sxs-lookup"><span data-stu-id="87987-299">SendMessage</span></span>|<span data-ttu-id="87987-300">-設定**訊息**至*要求*</span><span class="sxs-lookup"><span data-stu-id="87987-300">-   Set **Message** to *Request*</span></span><br /><span data-ttu-id="87987-301">-設定**作業**至*LOBPort.CompositeOp.Request*</span><span class="sxs-lookup"><span data-stu-id="87987-301">-   Set **Operation** to *LOBPort.CompositeOp.Request*</span></span>|  
|<span data-ttu-id="87987-302">ReceiveResponse</span><span class="sxs-lookup"><span data-stu-id="87987-302">ReceiveResponse</span></span>|<span data-ttu-id="87987-303">-設定**訊息**至*回應*</span><span class="sxs-lookup"><span data-stu-id="87987-303">-   Set **Message** to *Response*</span></span><br /><span data-ttu-id="87987-304">-設定**作業**至*LOBPort.CompositeOp.Response*</span><span class="sxs-lookup"><span data-stu-id="87987-304">-   Set **Operation** to *LOBPort.CompositeOp.Response*</span></span>|  
|<span data-ttu-id="87987-305">SendResponse</span><span class="sxs-lookup"><span data-stu-id="87987-305">SendResponse</span></span>|<span data-ttu-id="87987-306">-設定**訊息**至*回應*</span><span class="sxs-lookup"><span data-stu-id="87987-306">-   Set **Message** to *Response*</span></span><br /><span data-ttu-id="87987-307">-設定**作業**至*ResponseOut.CompositeOp.Request*</span><span class="sxs-lookup"><span data-stu-id="87987-307">-   Set **Operation** to *ResponseOut.CompositeOp.Request*</span></span>|  
  
 <span data-ttu-id="87987-308">您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。</span><span class="sxs-lookup"><span data-stu-id="87987-308">After you have specified these properties, the message shapes and ports are connected and your orchestration is complete.</span></span>  
  
 <span data-ttu-id="87987-309">您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="87987-309">You must now build the BizTalk solution and deploy it to a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="87987-310">如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="87987-310">For more information, see [Building and Running Orchestrations](../../core/building-and-running-orchestrations.md).</span></span>  
  
## <a name="configuring-the-biztalk-application"></a><span data-ttu-id="87987-311">設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="87987-311">Configuring the BizTalk Application</span></span>  
 <span data-ttu-id="87987-312">在 [協調流程] 窗格中您已部署的 BizTalk 專案後，會列出您稍早建立的協調流程[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="87987-312">After you have deployed the BizTalk project, the orchestration you created earlier is listed under the Orchestrations pane in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="87987-313">您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="87987-313">You must use the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to configure the application.</span></span> <span data-ttu-id="87987-314">如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。</span><span class="sxs-lookup"><span data-stu-id="87987-314">For a walkthrough, see [Walkthrough: Deploying a Basic BizTalk Application](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).</span></span>
  
 <span data-ttu-id="87987-315">設定應用程式包括：</span><span class="sxs-lookup"><span data-stu-id="87987-315">Configuring an application involves:</span></span>  
  
-   <span data-ttu-id="87987-316">選取應用程式的主機。</span><span class="sxs-lookup"><span data-stu-id="87987-316">Selecting a host for the application.</span></span>  
  
-   <span data-ttu-id="87987-317">對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="87987-317">Mapping the ports that you created in your orchestration to physical ports in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="87987-318">此協調流程中，您必須：</span><span class="sxs-lookup"><span data-stu-id="87987-318">For this orchestration you must:</span></span>  
  
    -   <span data-ttu-id="87987-319">定義位置上的硬碟和對應的檔案連接埠，您將在此置放要求訊息。</span><span class="sxs-lookup"><span data-stu-id="87987-319">Define a location on the hard disk and a corresponding file port where you will drop a request message.</span></span> <span data-ttu-id="87987-320">BizTalk 協調流程會使用要求訊息，並將它傳送給 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="87987-320">The BizTalk orchestration will consume the request message and send it to Oracle database.</span></span>  
  
    -   <span data-ttu-id="87987-321">定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 Oracle 資料庫回應的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="87987-321">Define a location on the hard disk and a corresponding file port where the BizTalk orchestration will drop the response message containing the response from Oracle database.</span></span>  
  
    -   <span data-ttu-id="87987-322">定義實體 Wcf-custom 或 Wcf-oracledb 傳送埠將訊息傳送至 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="87987-322">Define a physical WCF-Custom or WCF-OracleDB send port to send messages to Oracle database.</span></span> <span data-ttu-id="87987-323">因為作業都是因為在單一交易中，執行屬於複合作業確定**UseAmbientTransaction**繫結屬性設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="87987-323">Because the operations that are being as part of the composite operation are executed in a single transaction, make sure the **UseAmbientTransaction** binding property is set to **True**.</span></span>  
  
         <span data-ttu-id="87987-324">您也必須在傳送埠中指定的動作。</span><span class="sxs-lookup"><span data-stu-id="87987-324">You must also specify the action in the send port.</span></span> <span data-ttu-id="87987-325">複合作業的動作是 「 http://Microsoft.LobServices.OracleDB/2007/03/CompositeOperation"。</span><span class="sxs-lookup"><span data-stu-id="87987-325">The action for a composite operation is “http://Microsoft.LobServices.OracleDB/2007/03/CompositeOperation”.</span></span> <span data-ttu-id="87987-326">如需如何建立連接埠相關資訊，請參閱[手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="87987-326">For information about how to create ports, see [Manually configure a physical port binding to the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md).</span></span> <span data-ttu-id="87987-327">如需如何指定連接埠動作的詳細資訊，請參閱[設定 Oracle 資料庫的 SOAP 動作](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="87987-327">For more information about how to specify actions for ports, see [Configure the SOAP action for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md).</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="87987-328">產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="87987-328">Generating the schema using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] also creates a binding file that contains information about the ports and the actions to be set for those ports.</span></span> <span data-ttu-id="87987-329">您可以從這個繫結檔案匯[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （用於進行傳入呼叫時）。</span><span class="sxs-lookup"><span data-stu-id="87987-329">You can import this binding file from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create send ports (for outbound calls) or receive ports (for inbound calls).</span></span> <span data-ttu-id="87987-330">如需詳細資訊，請參閱[設定使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="87987-330">For more information, see [Configure a physical port binding using a port binding file to Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).</span></span> <span data-ttu-id="87987-331">如果您匯入此繫結檔案時，傳送埠上的動作會設定為與您在選取的所有作業都有關的動態動作[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]時產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="87987-331">If you import this binding file, the action on the send port is set to a dynamic action involving all the operations you selected in the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] while generating the schema.</span></span> <span data-ttu-id="87987-332">複合作業中，您必須取代的動態 「 http://Microsoft.LobServices.OracleDB/2007/03/CompositeOperation 」 動作。</span><span class="sxs-lookup"><span data-stu-id="87987-332">For a composite operation, you must replace the dynamic action with “http://Microsoft.LobServices.OracleDB/2007/03/CompositeOperation”.</span></span>  
  
## <a name="starting-the-application"></a><span data-ttu-id="87987-333">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="87987-333">Starting the Application</span></span>  
 <span data-ttu-id="87987-334">您必須啟動執行複合操作 Oracle 資料庫上的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="87987-334">You must start the BizTalk application for performing composite operations on Oracle database.</span></span> <span data-ttu-id="87987-335">如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="87987-335">For instructions on starting a BizTalk application, see [How to Start an Orchestration](../../core/how-to-start-an-orchestration.md).</span></span>  
  
 <span data-ttu-id="87987-336">在這個階段，請確定：</span><span class="sxs-lookup"><span data-stu-id="87987-336">At this stage, make sure:</span></span>  
  
-   <span data-ttu-id="87987-337">FILE 接收埠以接收要求訊息的協調流程執行。</span><span class="sxs-lookup"><span data-stu-id="87987-337">The FILE receive port to receive request messages for the orchestration is running.</span></span>  
  
-   <span data-ttu-id="87987-338">FILE 傳送埠，以接收回應訊息從協調流程正在執行。</span><span class="sxs-lookup"><span data-stu-id="87987-338">The FILE send port to receive the response messages from the orchestration is running.</span></span>  
  
-   <span data-ttu-id="87987-339">Wcf-custom 或 Wcf-oracledb 傳送埠將訊息傳送至 Oracle 資料庫正在執行。</span><span class="sxs-lookup"><span data-stu-id="87987-339">The WCF-Custom or WCF-OracleDB send port to send messages to Oracle database is running.</span></span>  
  
-   <span data-ttu-id="87987-340">BizTalk 協調流程的作業正在執行。</span><span class="sxs-lookup"><span data-stu-id="87987-340">The BizTalk orchestration for the operation is running.</span></span>  
  
## <a name="executing-the-operation"></a><span data-ttu-id="87987-341">執行作業</span><span class="sxs-lookup"><span data-stu-id="87987-341">Executing the Operation</span></span>  
 <span data-ttu-id="87987-342">執行應用程式之後，您必須先卸除要求訊息到檔案接收位置。</span><span class="sxs-lookup"><span data-stu-id="87987-342">After you run the application, you must drop a request message to the FILE receive location.</span></span> <span data-ttu-id="87987-343">要求訊息的結構描述必須符合您稍早建立的複合作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="87987-343">The schema for the request message must conform to the schema for the composite operations you created earlier.</span></span> <span data-ttu-id="87987-344">例如，ACCOUNTACTIVITY 資料表中插入記錄、 叫用的 GET_ALL_ACTIVITY 預存程序，並從 ACCOUNTACTIVITY 資料表中刪除記錄的要求訊息是：</span><span class="sxs-lookup"><span data-stu-id="87987-344">For example, a request message that inserts a record in the ACCOUNTACTIVITY table, invokes the GET_ALL_ACTIVITY stored procedure, and deletes a record from the ACCOUNTACTIVITY table is:</span></span>  
  
```  
<Request xmlns="http://Composite_Op.CompositeSchema">  
  <Insert xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY">  
    <RECORDSET>  
      <ACCOUNTACTIVITYRECORDINSERT>  
        <TID>1</TID>  
        <ACCOUNT>100001</ACCOUNT>  
        <AMOUNT>1500</AMOUNT>  
        <DESCRIPTION></DESCRIPTION>  
        <TRANSDATE>2008-06-21T15:52:19</TRANSDATE>  
        <PROCESSED>n</PROCESSED>  
      </ACCOUNTACTIVITYRECORDINSERT >  
    </RECORDSET>  
  </Insert>  
  <GET_ALL_ACTIVITY xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG"/>  
  <Delete xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY">  
    <FILTER>WHERE AMOUNT = 1500</FILTER>  
  </Delete>  
</Request>  
```  
  
 <span data-ttu-id="87987-345">先前的要求訊息第一次插入一筆記錄，然後再叫用的 GET_ALL_ACTIVITY 程序取得 ACCOUNTACTIVITY 資料表中的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="87987-345">The preceding request message first inserts a record and then invokes the GET_ALL_ACTIVITY procedure to get all the records in the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="87987-346">然後，插入的記錄會刪除指定的篩選子句。</span><span class="sxs-lookup"><span data-stu-id="87987-346">Then, the inserted record is deleted by specifying a FILTER clause.</span></span> <span data-ttu-id="87987-347">請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md)如需有關要求訊息結構描述，用於執行複合操作 oracle 資料庫使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="87987-347">See [Message Schemas for the Composite Operation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md) for more information about the request message schema for performing composite operations on Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
 <span data-ttu-id="87987-348">協調流程取用訊息，並將它傳送到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="87987-348">The orchestration consumes the message and sends it to Oracle database.</span></span> <span data-ttu-id="87987-349">從 Oracle 資料庫的回應會儲存在其他的協調流程中定義的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="87987-349">The response from Oracle database is saved at the other FILE location defined as part of the orchestration.</span></span> <span data-ttu-id="87987-350">例如，從先前的要求訊息的 Oracle 資料庫回應如下所示：</span><span class="sxs-lookup"><span data-stu-id="87987-350">For example, the response from Oracle database for the preceding request message resembles the following:</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8" ?>   
<RequestResponse xmlns="http://Composite_Op.CompositeSchema">  
  <InsertResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOOT/Table/ACCOUNTACTIVITY">  
    <InsertResult>1</InsertResult>   
  </InsertResponse>  
  <GET_ALL_ACTIVITYResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
    <ALLRECS>  
      \<xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
        \<xs:element msdata:IsDataSet="true" name="NewDataSet">  
          \<xs:complexType>  
            \<xs:sequence>  
              \<xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                \<xs:complexType>  
                  \<xs:sequence>  
                    \<xs:element minOccurs="0" name="TID" type="xs:decimal" />   
                    \<xs:element minOccurs="0" name="ACCOUNT" type="xs:decimal" />   
                    \<xs:element minOccurs="0" name="AMOUNT" type="xs:decimal" />   
                    \<xs:element minOccurs="0" name="DESCRIPTION" type="xs:string" />   
                    \<xs:element minOccurs="0" name="TRANSDATE" type="xs:dateTime" />   
                    \<xs:element minOccurs="0" name="PROCESSED" type="xs:string" />   
                  \</xs:sequence>  
                \</xs:complexType>  
              \</xs:element>  
            \</xs:sequence>  
          \</xs:complexType>  
        \</xs:element>  
      \</xs:schema>  
      \<diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
        <NewDataSet xmlns="">  
          <NewTable>  
            ......   
            ......   
          </NewTable>  
          ......  
          ......  
          <NewTable>  
            <TID>10</TID>   
            <ACCOUNT>100001</ACCOUNT>   
            <AMOUNT>1000</AMOUNT>   
            <TRANSDATE>2008-07-28T21:39:57</TRANSDATE>   
            <PROCESSED>n</PROCESSED>   
          </NewTable>  
        </NewDataSet>  
      \</diffgr:diffgram>  
    </ALLRECS>  
  </GET_ALL_ACTIVITYResponse>  
  <DeleteResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY">  
    <DeleteResult>1</DeleteResult>   
  </DeleteResponse>  
</RequestResponse>  
```  
  
 <span data-ttu-id="87987-351">上述的回應會包含多個結果集對應複合作業的一部分執行的不同作業。</span><span class="sxs-lookup"><span data-stu-id="87987-351">The preceding response contains multiple result sets corresponding the different operations performed as part of the composite operation.</span></span> <span data-ttu-id="87987-352">例如，`InsertResult`元素包含 '1'，表示插入作業所插入的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="87987-352">For example, the `InsertResult` element contains ‘1’, indicating the number of rows inserted by the Insert operation.</span></span> <span data-ttu-id="87987-353">同樣地，`DeleteResult`元素包含 '1'，表示刪除作業所刪除的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="87987-353">Similarly, the `DeleteResult` element contains ‘1’, indicating the number of rows deleted by the Delete operation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="87987-354">如果您執行複合操作時遇到逾時問題然後可能是因為連線的數目小於的複合運算涉及作業數目：</span><span class="sxs-lookup"><span data-stu-id="87987-354">If you experience time-out issues while executing a composite operation then it could be because the number of connections is less than the number of operations in a composite operation involving:</span></span>  
>   
>  -   <span data-ttu-id="87987-355">預存程序包含 BFILE、 BLOB、 CLOB、 NCLOB、 和 REF CURSOR 做為 OUT 或 IN OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="87987-355">Stored procedures containing BFILE, BLOB, CLOB, NCLOB, and REF CURSOR as OUT or IN OUT parameters.</span></span>  
> -   <span data-ttu-id="87987-356">選取作業。</span><span class="sxs-lookup"><span data-stu-id="87987-356">Select operation.</span></span>  
>   
>  <span data-ttu-id="87987-357">若要解決此問題，您必須確定是否有"n"這類的複合運算中的作業數目，為指定的值**MinPoolSize**繫結屬性是"n + 1"或更新版本。</span><span class="sxs-lookup"><span data-stu-id="87987-357">To resolve this issue, you must ensure that if there are “n” number of such operations in a composite operation, the value specified for the **MinPoolSize** binding property is “n+1” or greater.</span></span> <span data-ttu-id="87987-358">如需有關**MinPoolSize**繫結屬性，請參閱[使用繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。</span><span class="sxs-lookup"><span data-stu-id="87987-358">For more information about the **MinPoolSize** binding property, see [Working with binding properties](https://msdn.microsoft.com/library/dd788467.aspx).</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="87987-359">最佳作法</span><span class="sxs-lookup"><span data-stu-id="87987-359">Best Practices</span></span>  
 <span data-ttu-id="87987-360">您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。</span><span class="sxs-lookup"><span data-stu-id="87987-360">After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the binding file.</span></span> <span data-ttu-id="87987-361">一旦產生繫結檔案時，可以組態設定匯入檔案，使您不需要建立項目，例如傳送埠和接收相同的協調流程連接埠。</span><span class="sxs-lookup"><span data-stu-id="87987-361">Once you generate a binding file, you can import the configuration settings from the file, so that you do not need to create items such as send ports and receive ports for the same orchestration.</span></span> <span data-ttu-id="87987-362">如需繫結檔案的詳細資訊，請參閱[重複使用 Oracle 資料庫配接器繫結](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="87987-362">For more information about binding files, see [Reuse Oracle Database adapter bindings](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87987-363">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87987-363">See Also</span></span>  
[<span data-ttu-id="87987-364">開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊</span><span class="sxs-lookup"><span data-stu-id="87987-364">Building Blocks to Develop BizTalk Applications with Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)