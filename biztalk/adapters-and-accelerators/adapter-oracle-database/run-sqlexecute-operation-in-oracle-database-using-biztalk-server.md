---
title: "使用 BizTalk Server 的 Oracle 資料庫中執行 SQLEXECUTE 操作 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLEXECUTE operation, performing by using BizTalk Server
- SQLEXECUTE operation
ms.assetid: 7fdd1ead-0bf0-46cf-86fc-db513f76f6b3
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa982b938fc4fcb9096ca30209938b3b635d9fb8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="run-sqlexecute-operation-in-oracle-database-using-biztalk-server"></a><span data-ttu-id="e8ff1-102">使用 BizTalk Server 的 Oracle 資料庫中執行 SQLEXECUTE 操作</span><span class="sxs-lookup"><span data-stu-id="e8ff1-102">Run SQLEXECUTE operation in Oracle Database using BizTalk Server</span></span>
<span data-ttu-id="e8ff1-103">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓用戶端上的 Oracle 資料庫執行參數化的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-103">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] enables clients to run parameterized SQL statement on an Oracle database.</span></span> <span data-ttu-id="e8ff1-104">若要支援這類作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現 SQLEXECUTE 操作。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-104">To support such operations, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces a SQLEXECUTE operation.</span></span> <span data-ttu-id="e8ff1-105">SQLEXECUTE 作業支援的參數集可讓您執行相同的 SQL 陳述式，一次針對每組所組成的輸入的參數區塊。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-105">SQLEXECUTE operation supports an input parameter block comprised of parameter sets that enable you to execute the same SQL statement once for each set.</span></span> <span data-ttu-id="e8ff1-106">SQLEXECUTE 操作傳回泛型的記錄組中的 SQL 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-106">The SQLEXECUTE operation returns the results of the SQL statement in a generic record set.</span></span> <span data-ttu-id="e8ff1-107">如需作業的詳細資訊，請參閱[SQLEXECUTE 操作 Oracle 資料庫中](../../adapters-and-accelerators/adapter-oracle-database/sqlexecute-operation-in-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-107">For more information about the operation, see [SQLEXECUTE Operation in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/sqlexecute-operation-in-oracle-database.md).</span></span> <span data-ttu-id="e8ff1-108">SQLEXECUTE 操作的 SOAP 訊息結構的相關資訊，請參閱[SQLEXECUTE 操作的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-108">For information about the structure of the SOAP message for SQLEXECUTE operation, see [Message Schemas for the SQLEXECUTE Operation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md).</span></span>  
  
## <a name="how-to-perform-a-sqlexecute-operation-on-an-oracle-database"></a><span data-ttu-id="e8ff1-109">如何執行 SQLEXECUTE 操作 Oracle 資料庫上？</span><span class="sxs-lookup"><span data-stu-id="e8ff1-109">How to Perform a SQLEXECUTE operation on an Oracle Database?</span></span>  
 <span data-ttu-id="e8ff1-110">針對 Oracle 資料庫使用執行運算[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-110">Performing an operation on an Oracle database using [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] involves procedural tasks described in [Building blocks to develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md).</span></span> <span data-ttu-id="e8ff1-111">若要執行 SQLEXECUTE 操作，這些工作包括：</span><span class="sxs-lookup"><span data-stu-id="e8ff1-111">To perform a SQLEXECUTE operation, these tasks are:</span></span>  
  
1.  <span data-ttu-id="e8ff1-112">建立 BizTalk 專案並 SQLEXECUTE 作業產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-112">Create a BizTalk project and generate schema for the SQLEXECUTE operation.</span></span> <span data-ttu-id="e8ff1-113">SQLEXECUTE 操作中，會顯示在根節點 （/） 下**選取類別目錄**窗格[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-113">The SQLEXECUTE operation is surfaced under the root node (/) in the **Select a category** pane in the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span></span>  
  
2.  <span data-ttu-id="e8ff1-114">建立傳送和從 Oracle 資料庫接收訊息的 BizTalk 專案中的訊息。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-114">Create messages in the BizTalk project for sending and receiving messages from the Oracle database.</span></span>  
  
3.  <span data-ttu-id="e8ff1-115">建立協調流程叫用 Oracle 資料庫資料表或檢視表上的作業。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-115">Create an orchestration to invoke the operation on the Oracle database table or view.</span></span>  
  
4.  <span data-ttu-id="e8ff1-116">建置和部署 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-116">Build and deploy the BizTalk project.</span></span>  
  
5.  <span data-ttu-id="e8ff1-117">設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-117">Configure the BizTalk application by creating physical send and receive ports.</span></span>  
  
6.  <span data-ttu-id="e8ff1-118">啟動 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-118">Start the BizTalk application.</span></span>  
  
 <span data-ttu-id="e8ff1-119">本主題提供執行這些工作的指示。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-119">This topic provides instructions to perform these tasks.</span></span>  
  
## <a name="sample-based-on-this-topic"></a><span data-ttu-id="e8ff1-120">根據本主題的範例</span><span class="sxs-lookup"><span data-stu-id="e8ff1-120">Sample Based On This Topic</span></span>  
 <span data-ttu-id="e8ff1-121">基礎的範例，SqlExec，本主題也會提供[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-121">A sample, SqlExec, based on this topic is also provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="e8ff1-122">如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-122">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="generating-schema"></a><span data-ttu-id="e8ff1-123">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="e8ff1-123">Generating Schema</span></span>  
 <span data-ttu-id="e8ff1-124">本主題中，以示範如何執行參數化的 SQL 查詢時，我們將作業產生結構描述 SQLEXECUTE 網址中的根節點 （/）**選取類別目錄**窗格[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-124">In this topic, to demonstrate how to run a parameterized SQL query, we will generate schema for SQLEXECUTE operation available at the root node (/) in the **Select a category** pane in the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span> <span data-ttu-id="e8ff1-125">請參閱[擷取 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)如需有關如何產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-125">See [Retrieve metadata for Oracle Database operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) for more information about how to generate schema.</span></span>  
  
## <a name="defining-messages-and-message-types"></a><span data-ttu-id="e8ff1-126">定義訊息和訊息類型</span><span class="sxs-lookup"><span data-stu-id="e8ff1-126">Defining Messages and Message Types</span></span>  
 <span data-ttu-id="e8ff1-127">您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-127">The schema that you generated earlier describes the "types" required for the messages in the orchestration.</span></span> <span data-ttu-id="e8ff1-128">訊息通常是為其型別由對應的結構描述所定義的變數。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-128">A message is typically a variable, the type for which is defined by the corresponding schema.</span></span> <span data-ttu-id="e8ff1-129">您必須連結產生的結構描述您在第一個步驟中的訊息從 BizTalk 專案的 [協調流程檢視] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-129">You must link the schema you generated in the first step to the messages from the Orchestration View window of the BizTalk project.</span></span>  
  
 <span data-ttu-id="e8ff1-130">本主題中，您必須建立兩個訊息，其中將要求傳送至 Oracle 資料庫與另一個則接收回應。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-130">For this topic, you must create two messages—one to send a request to the Oracle database and the other to receive a response.</span></span>  
  
 <span data-ttu-id="e8ff1-131">執行下列步驟來建立訊息，並將其連結至結構描述。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-131">Perform the following steps to create messages and link them to the schema.</span></span>  
  
#### <a name="to-create-messages-and-link-to-schema"></a><span data-ttu-id="e8ff1-132">建立訊息，以及連結至結構描述</span><span class="sxs-lookup"><span data-stu-id="e8ff1-132">To create messages and link to schema</span></span>  
  
1.  <span data-ttu-id="e8ff1-133">如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-133">Open the Orchestration View window of the BizTalk project, if it is not already open.</span></span> <span data-ttu-id="e8ff1-134">若要這樣做，請按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-134">To do so, click **View**, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
2.  <span data-ttu-id="e8ff1-135">在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-135">In Orchestration View, right-click **Messages**, and then click **New Message**.</span></span>  
  
3.  <span data-ttu-id="e8ff1-136">以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-136">Right-click the newly created message and then select **Properties Window**.</span></span>  
  
4.  <span data-ttu-id="e8ff1-137">在**屬性**窗格**Message_1**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e8ff1-137">In the **Properties** pane for **Message_1**, do the following:</span></span>  
  
    |<span data-ttu-id="e8ff1-138">使用</span><span class="sxs-lookup"><span data-stu-id="e8ff1-138">Use this</span></span>|<span data-ttu-id="e8ff1-139">動作</span><span class="sxs-lookup"><span data-stu-id="e8ff1-139">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="e8ff1-140">識別碼</span><span class="sxs-lookup"><span data-stu-id="e8ff1-140">Identifier</span></span>|<span data-ttu-id="e8ff1-141">型別**要求**。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-141">Type **Request**.</span></span>|  
    |<span data-ttu-id="e8ff1-142">訊息類型</span><span class="sxs-lookup"><span data-stu-id="e8ff1-142">Message Type</span></span>|<span data-ttu-id="e8ff1-143">從下拉式清單中，展開 **結構描述**，然後選取*SqlExec.OracleDBBindingSchema.SQLEXECUTE*，其中*SqlExec*是您的 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-143">From the drop-down list, expand **Schemas**, and then select *SqlExec.OracleDBBindingSchema.SQLEXECUTE*, where *SqlExec* is the name of your BizTalk project.</span></span> <span data-ttu-id="e8ff1-144">*OracleDBBindingSchema*是 SQLEXECUTE 作業產生的結構描述。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-144">*OracleDBBindingSchema* is the schema generated for the SQLEXECUTE operation.</span></span>|  
  
5.  <span data-ttu-id="e8ff1-145">重複步驟 2 來建立新的訊息。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-145">Repeat step 2 to create a new message.</span></span> <span data-ttu-id="e8ff1-146">在**屬性**窗格新訊息中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e8ff1-146">In the **Properties** pane for the new message, do the following:</span></span>  
  
    |<span data-ttu-id="e8ff1-147">使用</span><span class="sxs-lookup"><span data-stu-id="e8ff1-147">Use this</span></span>|<span data-ttu-id="e8ff1-148">動作</span><span class="sxs-lookup"><span data-stu-id="e8ff1-148">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="e8ff1-149">識別碼</span><span class="sxs-lookup"><span data-stu-id="e8ff1-149">Identifier</span></span>|<span data-ttu-id="e8ff1-150">型別**回應**。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-150">Type **Response**.</span></span>|  
    |<span data-ttu-id="e8ff1-151">訊息類型</span><span class="sxs-lookup"><span data-stu-id="e8ff1-151">Message Type</span></span>|<span data-ttu-id="e8ff1-152">從下拉式清單中，展開 **結構描述**，然後選取*SqlExec.OracleDBBindingSchema.SQLEXECUTEResponse*。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-152">From the drop-down list, expand **Schemas**, and then select *SqlExec.OracleDBBindingSchema.SQLEXECUTEResponse*.</span></span>|  
  
## <a name="setting-up-the-orchestration"></a><span data-ttu-id="e8ff1-153">設定協調流程</span><span class="sxs-lookup"><span data-stu-id="e8ff1-153">Setting up the Orchestration</span></span>  
 <span data-ttu-id="e8ff1-154">您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行參數化的 SQL 查詢使用 SQLEXECUTE 操作。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-154">You must create a BizTalk orchestration to use [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for running a parameterized SQL query using the SQLEXECUTE operation.</span></span> <span data-ttu-id="e8ff1-155">在此協調流程中，卸除要求訊息已定義的接收位置。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-155">In this orchestration, you drop a request message at a defined receive location.</span></span> <span data-ttu-id="e8ff1-156">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會取用這個訊息，並將它傳遞到 Oracle 資料庫中，透過 ODP。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-156">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] consumes this message and passes it on to the Oracle database via ODP.</span></span> <span data-ttu-id="e8ff1-157">從 Oracle 資料庫的回應會儲存到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-157">The response from the Oracle database is saved to another location.</span></span> <span data-ttu-id="e8ff1-158">典型的協調流程執行 SQLEXECUTE Oracle 資料庫上的作業就會包含：</span><span class="sxs-lookup"><span data-stu-id="e8ff1-158">A typical orchestration for performing SQLEXECUTE operation on Oracle database would contain:</span></span>  
  
-   <span data-ttu-id="e8ff1-159">傳送和接收圖形以將訊息傳送至 Oracle 資料庫，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-159">Send and Receive shapes to send messages to Oracle database and receive responses.</span></span>  
  
-   <span data-ttu-id="e8ff1-160">單向接收埠以接收要求訊息傳送到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-160">A one-way receive port to receive request messages to send to the Oracle database.</span></span>  
  
-   <span data-ttu-id="e8ff1-161">雙向傳送埠以傳送要求訊息到 Oracle 資料庫，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-161">A two-way send port to send request messages to Oracle database and receive responses.</span></span>  
  
-   <span data-ttu-id="e8ff1-162">單向傳送埠，以便從 Oracle 資料庫的回應傳送到資料夾。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-162">A one-way send port to send the responses from Oracle database to a folder.</span></span>  
  
 <span data-ttu-id="e8ff1-163">範例協調流程 SQLEXECUTE 操作如下所示：</span><span class="sxs-lookup"><span data-stu-id="e8ff1-163">A sample orchestration for the SQLEXECUTE operation resembles the following:</span></span>  
  
 <span data-ttu-id="e8ff1-164">![用於叫用 SQLEXECUTE 操作的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/bdb47660-6013-46f7-aa4b-fe5eb83f3a1e.gif "bdb47660-6013-46f7-aa4b-fe5eb83f3a1e")</span><span class="sxs-lookup"><span data-stu-id="e8ff1-164">![Orchestration to invoke the SQLEXECUTE operation](../../adapters-and-accelerators/adapter-oracle-database/media/bdb47660-6013-46f7-aa4b-fe5eb83f3a1e.gif "bdb47660-6013-46f7-aa4b-fe5eb83f3a1e")</span></span>  
  
### <a name="adding-message-shapes"></a><span data-ttu-id="e8ff1-165">新增訊息圖形</span><span class="sxs-lookup"><span data-stu-id="e8ff1-165">Adding Message Shapes</span></span>  
 <span data-ttu-id="e8ff1-166">請確定您針對每個訊息圖形指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-166">Make sure you specify the following properties for each of the message shapes.</span></span> <span data-ttu-id="e8ff1-167">圖形資料行中所列的名稱是訊息 圖形的名稱，為顯示在剛才提及的協調流程中。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-167">The names listed in the Shape column are the names of the message shapes as displayed in the just-mentioned orchestration.</span></span>  
  
|<span data-ttu-id="e8ff1-168">形狀圖</span><span class="sxs-lookup"><span data-stu-id="e8ff1-168">Shape</span></span>|<span data-ttu-id="e8ff1-169">圖形類型</span><span class="sxs-lookup"><span data-stu-id="e8ff1-169">Shape Type</span></span>|<span data-ttu-id="e8ff1-170">屬性</span><span class="sxs-lookup"><span data-stu-id="e8ff1-170">Properties</span></span>|  
|-----------|----------------|----------------|  
|<span data-ttu-id="e8ff1-171">ReceiveMessage</span><span class="sxs-lookup"><span data-stu-id="e8ff1-171">ReceiveMessage</span></span>|<span data-ttu-id="e8ff1-172">Receive</span><span class="sxs-lookup"><span data-stu-id="e8ff1-172">Receive</span></span>|<span data-ttu-id="e8ff1-173">-設定**名稱**至*ReceiveMessage*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-173">-   Set **Name** to *ReceiveMessage*</span></span><br /><span data-ttu-id="e8ff1-174">-設定**啟動**至*，則為 True*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-174">-   Set **Activate** to *True*</span></span>|  
|<span data-ttu-id="e8ff1-175">SendMessage</span><span class="sxs-lookup"><span data-stu-id="e8ff1-175">SendMessage</span></span>|<span data-ttu-id="e8ff1-176">Send</span><span class="sxs-lookup"><span data-stu-id="e8ff1-176">Send</span></span>|<span data-ttu-id="e8ff1-177">-設定**名稱**至*SendMessage*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-177">-   Set **Name** to *SendMessage*</span></span>|  
|<span data-ttu-id="e8ff1-178">ReceiveResponse</span><span class="sxs-lookup"><span data-stu-id="e8ff1-178">ReceiveResponse</span></span>|<span data-ttu-id="e8ff1-179">Receive</span><span class="sxs-lookup"><span data-stu-id="e8ff1-179">Receive</span></span>|<span data-ttu-id="e8ff1-180">-設定**名稱**至*ReceiveResponse*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-180">-   Set **Name** to *ReceiveResponse*</span></span><br /><span data-ttu-id="e8ff1-181">-設定**啟動**至*False*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-181">-   Set **Activate** to *False*</span></span>|  
|<span data-ttu-id="e8ff1-182">SendResponse</span><span class="sxs-lookup"><span data-stu-id="e8ff1-182">SendResponse</span></span>|<span data-ttu-id="e8ff1-183">Send</span><span class="sxs-lookup"><span data-stu-id="e8ff1-183">Send</span></span>|<span data-ttu-id="e8ff1-184">-設定**名稱**至*SendResponse*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-184">-   Set **Name** to *SendResponse*</span></span>|  
  
### <a name="adding-ports"></a><span data-ttu-id="e8ff1-185">新增連接埠</span><span class="sxs-lookup"><span data-stu-id="e8ff1-185">Adding Ports</span></span>  
 <span data-ttu-id="e8ff1-186">請確定您針對每個邏輯連接埠指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-186">Make sure you specify the following properties for each of the logical ports.</span></span> <span data-ttu-id="e8ff1-187">連接埠資料行中所列的名稱是連接埠的名稱，為顯示協調流程中。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-187">The names listed in the Port column are the names of the ports as displayed in the orchestration.</span></span>  
  
|<span data-ttu-id="e8ff1-188">通訊埠</span><span class="sxs-lookup"><span data-stu-id="e8ff1-188">Port</span></span>|<span data-ttu-id="e8ff1-189">屬性</span><span class="sxs-lookup"><span data-stu-id="e8ff1-189">Properties</span></span>|  
|----------|----------------|  
|<span data-ttu-id="e8ff1-190">FileIn</span><span class="sxs-lookup"><span data-stu-id="e8ff1-190">FileIn</span></span>|<span data-ttu-id="e8ff1-191">-設定**識別碼**至*FileIn*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-191">-   Set **Identifier** to *FileIn*</span></span><br /><span data-ttu-id="e8ff1-192">-設定**類型**至*FileInType*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-192">-   Set **Type** to *FileInType*</span></span><br /><span data-ttu-id="e8ff1-193">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-193">-   Set **Communication Pattern** to *One-Way*</span></span><br /><span data-ttu-id="e8ff1-194">-設定**通訊方向**至*接收*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-194">-   Set **Communication Direction** to *Receive*</span></span>|  
|<span data-ttu-id="e8ff1-195">LOBPort</span><span class="sxs-lookup"><span data-stu-id="e8ff1-195">LOBPort</span></span>|<span data-ttu-id="e8ff1-196">-設定**識別碼**至*LOBPort*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-196">-   Set **Identifier** to *LOBPort*</span></span><br /><span data-ttu-id="e8ff1-197">-設定**類型**至*LOBPortType*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-197">-   Set **Type** to *LOBPortType*</span></span><br /><span data-ttu-id="e8ff1-198">-設定**通訊模式**至*要求-回應*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-198">-   Set **Communication Pattern** to *Request-Response*</span></span><br /><span data-ttu-id="e8ff1-199">-設定**通訊方向**至*傳送接收*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-199">-   Set **Communication Direction** to *Send-Receive*</span></span>|  
|<span data-ttu-id="e8ff1-200">SaveResponse</span><span class="sxs-lookup"><span data-stu-id="e8ff1-200">SaveResponse</span></span>|<span data-ttu-id="e8ff1-201">-設定**識別碼**至*SaveResponse*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-201">-   Set **Identifier** to *SaveResponse*</span></span><br /><span data-ttu-id="e8ff1-202">-設定**類型**至*SaveResponseType*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-202">-   Set **Type** to *SaveResponseType*</span></span><br /><span data-ttu-id="e8ff1-203">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-203">-   Set **Communication Pattern** to *One-Way*</span></span><br /><span data-ttu-id="e8ff1-204">-設定**通訊方向**至*傳送*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-204">-   Set **Communication Direction** to *Send*</span></span>|  
  
## <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a><span data-ttu-id="e8ff1-205">指定訊息的動作圖形，並將它們連接至連接埠</span><span class="sxs-lookup"><span data-stu-id="e8ff1-205">Specify Messages for Action Shapes, and Connect Them to Ports</span></span>  
 <span data-ttu-id="e8ff1-206">下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-206">The following table specifies the properties and their values that you should set to specify messages for action shapes and to link the messages to the ports.</span></span> <span data-ttu-id="e8ff1-207">圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-207">The names listed in the Shape column are the names of the message shapes as displayed in the orchestration mentioned earlier.</span></span>  
  
|<span data-ttu-id="e8ff1-208">形狀圖</span><span class="sxs-lookup"><span data-stu-id="e8ff1-208">Shape</span></span>|<span data-ttu-id="e8ff1-209">屬性</span><span class="sxs-lookup"><span data-stu-id="e8ff1-209">Properties</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="e8ff1-210">ReceiveMessage</span><span class="sxs-lookup"><span data-stu-id="e8ff1-210">ReceiveMessage</span></span>|<span data-ttu-id="e8ff1-211">-設定**訊息**至*要求*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-211">-   Set **Message** to *Request*</span></span><br /><span data-ttu-id="e8ff1-212">-設定**作業**至*FileIn.SQLEXECUTE.Request*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-212">-   Set **Operation** to *FileIn.SQLEXECUTE.Request*</span></span>|  
|<span data-ttu-id="e8ff1-213">SendMessage</span><span class="sxs-lookup"><span data-stu-id="e8ff1-213">SendMessage</span></span>|<span data-ttu-id="e8ff1-214">-設定**訊息**至*要求*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-214">-   Set **Message** to *Request*</span></span><br /><span data-ttu-id="e8ff1-215">-設定**作業**至*LOBPort.SQLEXECUTE.Request*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-215">-   Set **Operation** to *LOBPort.SQLEXECUTE.Request*</span></span>|  
|<span data-ttu-id="e8ff1-216">ReceiveResponse</span><span class="sxs-lookup"><span data-stu-id="e8ff1-216">ReceiveResponse</span></span>|<span data-ttu-id="e8ff1-217">-設定**訊息**至*回應*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-217">-   Set **Message** to *Response*</span></span><br /><span data-ttu-id="e8ff1-218">-設定**作業**至*LOBPort.SQLEXECUTE.Response*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-218">-   Set **Operation** to *LOBPort.SQLEXECUTE.Response*</span></span>|  
|<span data-ttu-id="e8ff1-219">SendResponse</span><span class="sxs-lookup"><span data-stu-id="e8ff1-219">SendResponse</span></span>|<span data-ttu-id="e8ff1-220">-設定**訊息**至*回應*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-220">-   Set **Message** to *Response*</span></span><br /><span data-ttu-id="e8ff1-221">-設定**作業**至*SaveResponse.SQLEXECUTE.Request*</span><span class="sxs-lookup"><span data-stu-id="e8ff1-221">-   Set **Operation** to *SaveResponse.SQLEXECUTE.Request*</span></span>|  
  
 <span data-ttu-id="e8ff1-222">您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-222">After you have specified these properties, the message shapes and ports are connected and your orchestration is complete.</span></span>  
  
 <span data-ttu-id="e8ff1-223">您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-223">You must now build the BizTalk solution and deploy it to a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="e8ff1-224">如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-224">For more information, see [Building and Running Orchestrations](../../core/building-and-running-orchestrations.md).</span></span>  
  
## <a name="configuring-the-biztalk-application"></a><span data-ttu-id="e8ff1-225">設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="e8ff1-225">Configuring the BizTalk Application</span></span>  
 <span data-ttu-id="e8ff1-226">部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-226">After you have deployed the BizTalk project, the orchestration you created earlier is listed under the **Orchestrations** pane in the BizTalk Server Administration console.</span></span> <span data-ttu-id="e8ff1-227">您必須使用 BizTalk Server 管理主控台來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-227">You must use the BizTalk Server Administration console to configure the application.</span></span> <span data-ttu-id="e8ff1-228">如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-228">For a walkthrough, see [Walkthrough: Deploying a Basic BizTalk Application](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).</span></span>
  
 <span data-ttu-id="e8ff1-229">設定應用程式包括：</span><span class="sxs-lookup"><span data-stu-id="e8ff1-229">Configuring an application involves:</span></span>  
  
-   <span data-ttu-id="e8ff1-230">選取應用程式的主機。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-230">Selecting a host for the application.</span></span>  
  
-   <span data-ttu-id="e8ff1-231">對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-231">Mapping the ports that you created in your orchestration to physical ports in the BizTalk Server Administration console.</span></span> <span data-ttu-id="e8ff1-232">此協調流程中，您必須：</span><span class="sxs-lookup"><span data-stu-id="e8ff1-232">For this orchestration you must:</span></span>  
  
    -   <span data-ttu-id="e8ff1-233">定義位置上的硬碟和對應的檔案連接埠，您將在此置放要求訊息。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-233">Define a location on the hard disk and a corresponding file port where you will drop a request message.</span></span> <span data-ttu-id="e8ff1-234">BizTalk 協調流程會使用要求訊息，並將它傳送到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-234">The BizTalk orchestration will consume the request message and send it to the Oracle database.</span></span>  
  
    -   <span data-ttu-id="e8ff1-235">定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 Oracle 資料庫回應的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-235">Define a location on the hard disk and a corresponding file port where the BizTalk orchestration will drop the response message containing the response from the Oracle database.</span></span>  
  
    -   <span data-ttu-id="e8ff1-236">定義實體 Wcf-custom 或 Wcf-oracledb 傳送埠將訊息傳送至 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-236">Define a physical WCF-Custom or WCF-OracleDB send port to send messages to the Oracle database.</span></span> <span data-ttu-id="e8ff1-237">您也必須在傳送埠中指定的動作。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-237">You must also specify the action in the send port.</span></span> <span data-ttu-id="e8ff1-238">如需如何建立 Wcf-custom 或 Wcf-oracledb 連接埠相關資訊，請參閱[手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-238">For information about how to create WCF-Custom or WCF-OracleDB ports, see [Manually configure a physical port binding to Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md).</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="e8ff1-239">產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-239">Generating the schema using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] also creates a binding file that contains information about the ports and the actions to be set for those ports.</span></span> <span data-ttu-id="e8ff1-240">您可以從 BizTalk Server 管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （適用於進行傳入呼叫時），以匯入此繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-240">You can import this binding file from the BizTalk Server Administration console to create send ports (for outbound calls) or receive ports (for inbound calls).</span></span> <span data-ttu-id="e8ff1-241">如需詳細資訊，請參閱[設定使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-241">For more information, see [Configure a physical port binding using a port  binding file to Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).</span></span>  
  
## <a name="starting-the-application"></a><span data-ttu-id="e8ff1-242">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="e8ff1-242">Starting the Application</span></span>  
 <span data-ttu-id="e8ff1-243">您必須啟動 BizTalk 應用程式執行 SQLEXECUTE 作業。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-243">You must start the BizTalk application for performing the SQLEXECUTE operation.</span></span> <span data-ttu-id="e8ff1-244">如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-244">For instructions on starting a BizTalk application, see [How to Start an Orchestration](../../core/how-to-start-an-orchestration.md).</span></span>  
  
 <span data-ttu-id="e8ff1-245">在這個階段，請確定：</span><span class="sxs-lookup"><span data-stu-id="e8ff1-245">At this stage, make sure:</span></span>  
  
-   <span data-ttu-id="e8ff1-246">FILE 接收埠以接收要求訊息的協調流程執行。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-246">The FILE receive port to receive request messages for the orchestration is running.</span></span>  
  
-   <span data-ttu-id="e8ff1-247">FILE 傳送埠，以接收回應訊息從協調流程正在執行。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-247">The FILE send port to receive the response messages from the orchestration is running.</span></span>  
  
-   <span data-ttu-id="e8ff1-248">Wcf-custom 或 Wcf-oracledb 傳送埠將訊息傳送至 Oracle 資料庫正在執行。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-248">The WCF-Custom or WCF-OracleDB send port to send messages to the Oracle database is running.</span></span>  
  
-   <span data-ttu-id="e8ff1-249">BizTalk 協調流程的作業正在執行。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-249">The BizTalk orchestration for the operation is running.</span></span>  
  
## <a name="executing-the-operation"></a><span data-ttu-id="e8ff1-250">執行作業</span><span class="sxs-lookup"><span data-stu-id="e8ff1-250">Executing the Operation</span></span>  
 <span data-ttu-id="e8ff1-251">執行應用程式之後，您必須先卸除要求訊息到檔案接收位置。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-251">After you run the application, you must drop a request message to the FILE receive location.</span></span> <span data-ttu-id="e8ff1-252">要求訊息的結構描述必須符合您先前產生的 SQLEXECUTE 作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-252">The schema for the request message must conform to the schema for the SQLEXECUTE operation you generated earlier.</span></span> <span data-ttu-id="e8ff1-253">協調流程取用訊息，並將它傳送到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-253">The orchestration consumes the message and sends it to the Oracle database.</span></span> <span data-ttu-id="e8ff1-254">從 Oracle 資料庫的回應會儲存在其他的協調流程中定義的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-254">The response from the Oracle database is saved at the other FILE location defined as part of the orchestration.</span></span> <span data-ttu-id="e8ff1-255">請參閱[SQLEXECUTE 操作的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md)如需有關叫用 SQLEXECUTE 操作的要求訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-255">See [Message Schemas for the SQLEXECUTE Operation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md) for more information about the request message schema for invoking a SQLEXECUTE operation.</span></span>  
  
 <span data-ttu-id="e8ff1-256">因為 SQLEXECUTE 作業不會顯示在任何 Oracle 資料庫成品，您可以使用相同的結構描述檢視上執行參數化的 SQL 查詢，或在其他資料表上執行作業的程序。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-256">Because the SQLEXECUTE operation is not surfaced under any Oracle database artifact, you can use the same schema to perform a parameterized SQL query on a view or execute a procedure that operates on some other table.</span></span>  
  
 <span data-ttu-id="e8ff1-257">例如，下列要求訊息會使用 SQLEXECUTE 操作帳戶資料表上執行參數化的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-257">For example, the following request message performs a parameterized SELECT statement on the ACCOUNT table using the SQLEXECUTE operation.</span></span> <span data-ttu-id="e8ff1-258">SCOTT 結構描述下建立帳戶資料表，執行下列 SQL 指令碼提供範例。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-258">The ACCOUNT table is created under the SCOTT schema by running the SQL scripts provided with the samples.</span></span> <span data-ttu-id="e8ff1-259">若要深入了解這些範例，請參閱[結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-259">To know more about the samples, see [Schema Samples](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md).</span></span>  
  
```  
<SQLEXECUTE xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE">  
  <SQLSTATEMENT>select * from ACCOUNT where ACCTID=:num</SQLSTATEMENT>  
  <PARAMETERSCHEMA>num number</PARAMETERSCHEMA>  
  <PARAMETERSET>  
    <PARAMETERDATA xmlns="http://Microsoft.LobServices.OracleDB/2007/03">  
      <PARAMETER>  
        <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">100000</string>  
      </PARAMETER>  
    </PARAMETERDATA>  
  </PARAMETERSET>  
</SQLEXECUTE>  
```  
  
 <span data-ttu-id="e8ff1-260">從 Oracle 資料庫，如上述的要求訊息的回應為：</span><span class="sxs-lookup"><span data-stu-id="e8ff1-260">The response from Oracle database for the above request message is:</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8" ?>   
<SQLEXECUTEResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE">  
  <SQLEXECUTEResult>  
    <GenRecordRow xmlns="http://Microsoft.LobServices.OracleDB/2007/03">  
      <GenRecordColumn>  
        <GenRecordColumn>  
          <ColumnName>ACCTID</ColumnName>   
          <ColumnValue>100000</ColumnValue>   
          <ColumnType>System.Decimal</ColumnType>   
        </GenRecordColumn>  
        <GenRecordColumn>  
          <ColumnName>NAME</ColumnName>   
          <ColumnValue>Kim Ralls</ColumnValue>   
          <ColumnType>System.String</ColumnType>   
        </GenRecordColumn>  
        <GenRecordColumn>  
          <ColumnName>BALANCE</ColumnName>   
          <ColumnValue>10000</ColumnValue>   
          <ColumnType>System.Decimal</ColumnType>   
        </GenRecordColumn>  
      </GenRecordColumn>  
    </GenRecordRow>  
  </SQLEXECUTEResult>  
</SQLEXECUTEResponse>  
```  
  
## <a name="possible-exceptions"></a><span data-ttu-id="e8ff1-261">可能的例外狀況</span><span class="sxs-lookup"><span data-stu-id="e8ff1-261">Possible Exceptions</span></span>  
 <span data-ttu-id="e8ff1-262">如需有關例外狀況資訊可能會遇到執行 DML 作業使用時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[例外狀況和錯誤處理](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-262">For information about the exceptions you might encounter while performing a DML operation using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Exceptions and error handling](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md).</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="e8ff1-263">最佳作法</span><span class="sxs-lookup"><span data-stu-id="e8ff1-263">Best Practices</span></span>  
 <span data-ttu-id="e8ff1-264">您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-264">After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the bindings file.</span></span> <span data-ttu-id="e8ff1-265">一旦產生繫結檔案時，您可以匯入組態設定從檔案，因此您不需要建立傳送埠、 接收埠，等。 針對相同的協調流程。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-265">Once you generate a bindings file, you can import the configuration settings from the file so that you do not need to create the send ports, receive ports, etc. for the same orchestration.</span></span> <span data-ttu-id="e8ff1-266">如需繫結檔案的詳細資訊，請參閱[重複使用 Oracle 資料庫配接器繫結](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ff1-266">For more information about binding files, see [Reuse Oracle Database adapter bindings](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ff1-267">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8ff1-267">See Also</span></span>  
[<span data-ttu-id="e8ff1-268">開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊</span><span class="sxs-lookup"><span data-stu-id="e8ff1-268">Building Blocks to Develop BizTalk Applications with Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)