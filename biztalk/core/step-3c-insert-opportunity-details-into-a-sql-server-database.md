---
title: 步驟 3c： 將機會詳細資料插入至 SQL Server 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3f6f9bbe-6f25-4393-8f92-aeeba9736acf
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ca5f0532c69a72e2a5c3d0d3875c9822db1a307
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023124"
---
# <a name="step-3c-insert-opportunity-details-into-a-sql-server-database"></a><span data-ttu-id="c5e92-102">步驟 3c： 將機會詳細資料插入至 SQL Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="c5e92-102">Step 3c: Insert Opportunity Details into a SQL Server Database</span></span>
<span data-ttu-id="c5e92-103">現在我們已經建置協調流程以將查詢傳送到 Salesforce 並接收回應。</span><span class="sxs-lookup"><span data-stu-id="c5e92-103">By now we have built the orchestration to send a query to Salesforce and receive a response.</span></span> <span data-ttu-id="c5e92-104">在本節中，我們會更新該協調流程以回應插入從到 Salesforce **OrderDetails**內部部署 SQL Server 資料庫中的資料表**訂單**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-104">In this section, we’ll update that orchestration to insert the response from Salesforce into an **OrderDetails** table in an on-premise SQL Server database, **Orders**.</span></span> <span data-ttu-id="c5e92-105">若要達到此目的，我們會執行下列一組廣泛的步驟：</span><span class="sxs-lookup"><span data-stu-id="c5e92-105">To achieve this, we’ll perform the following broad set of steps:</span></span>  
  
- <span data-ttu-id="c5e92-106">建立**OrderDetails**資料表中**訂單**內部部署 SQL Server 資料庫中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c5e92-106">Create an **OrderDetails** table in an **Orders** database in an on-premise SQL Server database.</span></span>  
  
- <span data-ttu-id="c5e92-107">使用[!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)]隨附[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]上產生插入作業結構描述**OrderDetails**資料表。</span><span class="sxs-lookup"><span data-stu-id="c5e92-107">Use the [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] available with [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] to generate the schema for the Insert operation on the **OrderDetails** table.</span></span>  
  
- <span data-ttu-id="c5e92-108">建立對應來轉換 Salesforce 回應訊息至訊息，以便插入**OrderDetails** SQL Server 中的資料表。</span><span class="sxs-lookup"><span data-stu-id="c5e92-108">Create a map to transform the Salesforce response message to the message for inserting into **OrderDetails** table in SQL Server.</span></span>  
  
- <span data-ttu-id="c5e92-109">更新協調流程使用要插入至回應訊息的轉換**OrderDetails**資料表。</span><span class="sxs-lookup"><span data-stu-id="c5e92-109">Update the orchestration to use the transform to insert the response message into the **OrderDetails** table.</span></span>  
  
## <a name="create-sql-server-database-and-table"></a><span data-ttu-id="c5e92-110">建立 SQL Server 資料庫和資料表</span><span class="sxs-lookup"><span data-stu-id="c5e92-110">Create SQL Server Database and Table</span></span>  
  
#### <a name="to-create-the-database-and-table"></a><span data-ttu-id="c5e92-111">若要建立資料庫和資料表</span><span class="sxs-lookup"><span data-stu-id="c5e92-111">To create the database and table</span></span>  
  
1.  <span data-ttu-id="c5e92-112">開啟 SQL Server Management Studio 並以系統管理員身分連接。</span><span class="sxs-lookup"><span data-stu-id="c5e92-112">Open SQL Server Management Studio and connect as an administrator.</span></span>  
  
2.  <span data-ttu-id="c5e92-113">以滑鼠右鍵按一下**資料庫**節點，然後按一下**新的資料庫**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-113">Right-click the **Databases** node and click **New Database**.</span></span> <span data-ttu-id="c5e92-114">將資料庫名稱指定為`Orders`並指定其他詳細資料，以建立新的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c5e92-114">Specify the database name as `Orders` and specify other details to create a new database.</span></span>  
  
3.  <span data-ttu-id="c5e92-115">開啟查詢編輯器，然後執行下列查詢，以建立**OrderDetails**資料表中**訂單**資料庫：</span><span class="sxs-lookup"><span data-stu-id="c5e92-115">Open a query editor and run the following query to create an **OrderDetails** table in the **Orders** database:</span></span>  
  
    ```  
    USE [Orders]  
    GO  
    /****** Object:  Table [dbo].[OrderDetails]    Script Date: 07-12-2012 22:15:47 ******/  
    SET ANSI_NULLS ON  
    GO  
    SET QUOTED_IDENTIFIER ON  
    GO  
    SET ANSI_PADDING ON  
    GO  
    CREATE TABLE [dbo].[OrderDetails]([ID] [int] IDENTITY(1,1) NOT NULL,  
    [TITLE] [varchar](200) NULL,  
    [ProductName] [varchar](200) NULL,  
    [Quantity] [float] NULL,  
    [Amount] [float] NULL,  
    PRIMARY KEY CLUSTERED   
    (  
    [ID] ASC  
    )WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
    GO  
    SET ANSI_PADDING OFF  
    GO  
    ```  
  
## <a name="create-schema-for-insert-operation-on-orderdetails-table"></a><span data-ttu-id="c5e92-116">建立 OrderDetails 資料表上的插入作業的結構描述</span><span class="sxs-lookup"><span data-stu-id="c5e92-116">Create Schema for Insert Operation on OrderDetails Table</span></span>  
 <span data-ttu-id="c5e92-117">安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]提供[!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)]，可用於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案，以產生插入作業的結構描述上**OrderDetails**資料表。</span><span class="sxs-lookup"><span data-stu-id="c5e92-117">Installing [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] provides a [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] that can be used within a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project to generate the schema for the Insert operation on the **OrderDetails** table.</span></span> <span data-ttu-id="c5e92-118">本節中的步驟建立的訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="c5e92-118">This section provides steps to follow to create the message schema.</span></span>  
  
#### <a name="to-create-the-schema-for-insert-operation"></a><span data-ttu-id="c5e92-119">若要建立 Insert 作業的結構描述</span><span class="sxs-lookup"><span data-stu-id="c5e92-119">To create the schema for Insert operation</span></span>  
  
1. <span data-ttu-id="c5e92-120">以滑鼠右鍵按一下**BtsSalesforceIntegration**專案，指向**新增**，然後按一下**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-120">Right-click the **BtsSalesforceIntegration** project, point to **Add**, and then click **Add Generated Items**.</span></span> <span data-ttu-id="c5e92-121">在 **加入產生的項目** 對話方塊中，按一下**取用配接器服務**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-121">In the **Add Generated Items** dialog box, click **Consume Adapter Service**, and then click **Add**.</span></span>  
  
2. <span data-ttu-id="c5e92-122">在  [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)]，從 選取繫結下拉式清單中，按一下**sqlBinding**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-122">In the [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)], from the Select a binding drop-down, click **sqlBinding**, and then click **Configure**.</span></span>  
  
3. <span data-ttu-id="c5e92-123">在**設定介面卡**對話方塊的 **安全性**索引標籤上，如**用戶端認證類型**，選取**Windows**使用 Windows驗證連接到 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c5e92-123">In the **Configure Adapter** dialog box, under **Security** tab, for **Client credential type**, select **Windows** to use Windows authentication to connect to SQL Server database.</span></span>  
  
4. <span data-ttu-id="c5e92-124">在**設定介面卡**對話方塊的  **URI 屬性**索引標籤上，如**Initial Catalog**指定資料庫名稱 （訂單） 來連接到。</span><span class="sxs-lookup"><span data-stu-id="c5e92-124">In the **Configure Adapter** dialog box, under **URI Properties** tab, for **Initial Catalog** specify the database name (Orders) to connect to.</span></span> <span data-ttu-id="c5e92-125">針對**Server**指定您要連接到 SQL Server 安裝所在的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="c5e92-125">For **Server** specify the computer name where SQL Server you are connecting to is installed.</span></span> <span data-ttu-id="c5e92-126">SQL Server 資料庫使用時間是否在同一部電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案中，您可以只放句點 (**。**)。</span><span class="sxs-lookup"><span data-stu-id="c5e92-126">If the SQL Server database is on the same computer as the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project, you can just put a period (**.**).</span></span> <span data-ttu-id="c5e92-127">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="c5e92-127">Click **OK**.</span></span>  
  
5. <span data-ttu-id="c5e92-128">在 [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)]按一下  **Connect**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-128">In the [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] click **Connect**.</span></span> <span data-ttu-id="c5e92-129">建立連線之後，請選取 合約類型作為**用戶端 （傳出作業）**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-129">After the connection is established, select the contract type as **Client(Outbound operations)**.</span></span> <span data-ttu-id="c5e92-130">底下**選取類別目錄**方塊中，展開**資料表**，按一下  **OrderDetails**資料表，然後在右窗格中按一下**插入**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-130">Under the **Select a category** box, expand **Tables**, click **OrderDetails** table, and in the right pane click **Insert** and then click **Add**.</span></span>  
  
6. <span data-ttu-id="c5e92-131">指定**檔案名稱前置詞**如果您想要產生的結構描述識別碼的前置詞。</span><span class="sxs-lookup"><span data-stu-id="c5e92-131">Specify a **Filename Prefix** if you want to prefix the generated schemas with an identifier.</span></span> <span data-ttu-id="c5e92-132">本教學課程中，讓我們指定做為前置詞**InsertOrders** ，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-132">For this tutorial, let’s specify the prefix as **InsertOrders** and then click **OK**.</span></span>  
  
    <span data-ttu-id="c5e92-133">一連串的結構描述會新增至專案。</span><span class="sxs-lookup"><span data-stu-id="c5e92-133">A bunch of schemas are added to the project.</span></span> <span data-ttu-id="c5e92-134">我們將使用插入到訊息的結構描述**OrderDetails**資料表**InsertOrdersTableOperation.dbo.OrderDetails.xsd**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-134">The schema that we’ll use for inserting messages into the **OrderDetails** table is **InsertOrdersTableOperation.dbo.OrderDetails.xsd**.</span></span>  
  
## <a name="map-salesforce-response-and-insert-schemas"></a><span data-ttu-id="c5e92-135">對應 Salesforce 回應及插入結構描述</span><span class="sxs-lookup"><span data-stu-id="c5e92-135">Map Salesforce Response and Insert Schemas</span></span>  
 <span data-ttu-id="c5e92-136">既然我們已經有兩個結構描述 (來自 Salesforce 和插入回應**OrderDetails**)，我們必須對應至插入結構描述從 Salesforce 的回應結構描述**OrderDetails**以便從 Salesforce 的回應訊息可以插入 SQL Server 資料庫資料表中。</span><span class="sxs-lookup"><span data-stu-id="c5e92-136">Now that we have both the schemas (response from Salesforce and inserting into **OrderDetails**), we must map the response schema from Salesforce into the insert schema for **OrderDetails** so that the response message from Salesforce can be inserted in the SQL Server database table.</span></span>  
  
#### <a name="to-map-the-schemas"></a><span data-ttu-id="c5e92-137">若要在對應結構描述</span><span class="sxs-lookup"><span data-stu-id="c5e92-137">To map the schemas</span></span>  
  
1.  <span data-ttu-id="c5e92-138">以滑鼠右鍵按一下**BtsSalesforceIntegration**專案，指向**新增**，按一下 **新項目**，然後按一下**對應**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-138">Right-click the **BtsSalesforceIntegration** project, point to **Add**, click **New Item**, and then click **Map**.</span></span> <span data-ttu-id="c5e92-139">指定對應名稱為`QueryResult_Orders.btm`，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-139">Specify the map name as `QueryResult_Orders.btm` and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="c5e92-140">對應介面上，針對來源結構描述中，選取**QueryResult** ，然後針對目的地結構描述中，選取**InsertOrdersTableOperation.dbo.OrderDetails.xsd** ，然後在其中**插入**節點。</span><span class="sxs-lookup"><span data-stu-id="c5e92-140">On the map surface, for the source schema, select **QueryResult** and for the destination schema, select **InsertOrdersTableOperation.dbo.OrderDetails.xsd** and then within that, the **Insert** node.</span></span>  
  
3.  <span data-ttu-id="c5e92-141">對應兩個結構描述，如下列螢幕擷取畫面所示：</span><span class="sxs-lookup"><span data-stu-id="c5e92-141">Map the two schemas as shown in the following screenshot:</span></span>  
  
     <span data-ttu-id="c5e92-142">![對應至插入結構描述的 Salesforce 回應](../core/media/bts-sf-map-response-insert.jpg "BTS_SF_Map_Response_Insert")</span><span class="sxs-lookup"><span data-stu-id="c5e92-142">![Map Salesforce response to Insert schema](../core/media/bts-sf-map-response-insert.jpg "BTS_SF_Map_Response_Insert")</span></span>  
  
     <span data-ttu-id="c5e92-143">請注意，地圖會使用**迴圈**之間的運算質**記錄**並**OrderDetails**連結。</span><span class="sxs-lookup"><span data-stu-id="c5e92-143">Notice that the map uses a **Looping** functoid between the **records** and the **OrderDetails** link.</span></span> <span data-ttu-id="c5e92-144">這可確保所有一或多個節點下的次數**記錄**會對應至類似底下的節點發生次數**OrderDetails**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-144">This ensures that all one or more than one occurrences of nodes under **records** are mapped to similar occurrences of nodes under the **OrderDetails**.</span></span>  
  
4.  <span data-ttu-id="c5e92-145">儲存對應變更。</span><span class="sxs-lookup"><span data-stu-id="c5e92-145">Save changes to the map.</span></span>  
  
## <a name="update-the-orchestration-to-insert-messages-into-sql-server"></a><span data-ttu-id="c5e92-146">更新協調流程將訊息插入 SQL Server</span><span class="sxs-lookup"><span data-stu-id="c5e92-146">Update the Orchestration to Insert Messages into SQL Server</span></span>  
 <span data-ttu-id="c5e92-147">在本節中，我們將使用協調流程中的對應，將 Salesforce 回應訊息轉換成 SQL Server 資料表中插入訂單詳細資料的訊息。</span><span class="sxs-lookup"><span data-stu-id="c5e92-147">In this section, we’ll use the map in the orchestration to transform the Salesforce response message into a message for inserting order details in a SQL Server table.</span></span> <span data-ttu-id="c5e92-148">我們也會新增至該訊息送到 SQL Server 的連接埠。</span><span class="sxs-lookup"><span data-stu-id="c5e92-148">We’ll also add a port to send that message to SQL Server.</span></span>  
  
#### <a name="to-update-the-orchestration"></a><span data-ttu-id="c5e92-149">若要更新的協調流程</span><span class="sxs-lookup"><span data-stu-id="c5e92-149">To update the orchestration</span></span>  
  
1. <span data-ttu-id="c5e92-150">建立插入結構描述的訊息變數。</span><span class="sxs-lookup"><span data-stu-id="c5e92-150">Create a message variable for the insert schema.</span></span> <span data-ttu-id="c5e92-151">從 [協調流程] 檢視中，以滑鼠右鍵按一下**訊息**節點，然後再按一下**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-151">From the orchestration view, right-click the **Messages** node, and then click **New Message**.</span></span> <span data-ttu-id="c5e92-152">設定訊息名稱作為**InsertOrders**訊息做為類型**BtsSalesforceIntegration.InsertOrdersTableOperation_dbo_OrderDetails.Insert**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-152">Set the message name as **InsertOrders** and message type as **BtsSalesforceIntegration.InsertOrdersTableOperation_dbo_OrderDetails.Insert**.</span></span>  
  
2. <span data-ttu-id="c5e92-153">新增 建構訊息 」 圖形之後**ReceiveQueryResult**圖形。</span><span class="sxs-lookup"><span data-stu-id="c5e92-153">Add a Construct Message shape after the **ReceiveQueryResult** shape.</span></span> <span data-ttu-id="c5e92-154">設定圖形的名稱`ConstructOrders`並設定**建構的訊息**屬性設**InsertOrders**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-154">Set the name of the shape to `ConstructOrders` and set the **Messages Constructed** property to **InsertOrders**.</span></span>  
  
3. <span data-ttu-id="c5e92-155">內**ConstructOrders**圖形中新增**轉換**圖形。</span><span class="sxs-lookup"><span data-stu-id="c5e92-155">Within the **ConstructOrders** shape, add a **Transform** shape.</span></span> <span data-ttu-id="c5e92-156">按兩下以開啟 [轉換組態] 對話方塊中的 [轉換] 圖形。</span><span class="sxs-lookup"><span data-stu-id="c5e92-156">Double-click the Transform shape to open the Transform Configuration dialog box.</span></span> <span data-ttu-id="c5e92-157">在對話方塊中，選取**現有的對應**選項，然後再從下拉式清單選取**BtsSalesforceIntegration.QueryResult_Orders**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-157">In the dialog box, select the **Existing Map** option, and then from the drop-down select **BtsSalesforceIntegration.QueryResult_Orders**.</span></span> <span data-ttu-id="c5e92-158">設定**來源**來**QueryResultMsg**，**目的地**來**InsertOrders**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-158">Set **Source** to **QueryResultMsg**, **Destination** to **InsertOrders**, and then click **OK**.</span></span>  
  
4. <span data-ttu-id="c5e92-159">在後**ConstructOrders**圖形中新增 「 傳送 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="c5e92-159">After the **ConstructOrders** shape, add a Send shape.</span></span> <span data-ttu-id="c5e92-160">命名圖形`SendOrders`並設定為訊息類型**InsertOrders**。</span><span class="sxs-lookup"><span data-stu-id="c5e92-160">Name the shape `SendOrders` and set the message type as **InsertOrders**.</span></span>  
  
5. <span data-ttu-id="c5e92-161">新增 Salesforce 中插入訂單詳細資料的連接埠。</span><span class="sxs-lookup"><span data-stu-id="c5e92-161">Add a port to insert order details into Salesforce.</span></span> <span data-ttu-id="c5e92-162">在 [連接埠組態精靈] 中，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="c5e92-162">In the Port Configuration wizard, select the following options:</span></span>  
  
   - <span data-ttu-id="c5e92-163">將連接埠名稱指定為`SendToSQL`。</span><span class="sxs-lookup"><span data-stu-id="c5e92-163">Specify the port name as `SendToSQL`.</span></span>  
  
   - <span data-ttu-id="c5e92-164">選取 [建立新的連接埠類型] 選項。</span><span class="sxs-lookup"><span data-stu-id="c5e92-164">Select the option to create a new port type.</span></span>  
  
   - <span data-ttu-id="c5e92-165">設定**通訊模式**要*單向*。</span><span class="sxs-lookup"><span data-stu-id="c5e92-165">Set **Communication Pattern** to *One-Way*.</span></span>  
  
   - <span data-ttu-id="c5e92-166">設定**連接埠通訊方向**要*我將總是傳送的訊息在此連接埠*並設定**連接埠繫結**至*稍後指定*。</span><span class="sxs-lookup"><span data-stu-id="c5e92-166">Set **Port direction of communication** to *I’ll always be sending messages on this port* and set **Port binding** to *Specify later*.</span></span>  
  
     <span data-ttu-id="c5e92-167">連接**要求**連接埠的作業**SendOrders**傳送完成的協調流程的圖形。</span><span class="sxs-lookup"><span data-stu-id="c5e92-167">Connect the **Request** operation of port to the **SendOrders** Send shape to complete the orchestration.</span></span> <span data-ttu-id="c5e92-168">下列螢幕擷取畫面說明完成的協調流程，端對端。</span><span class="sxs-lookup"><span data-stu-id="c5e92-168">The following screenshot depicts the completed orchestration, end-to-end.</span></span>  
  
     <span data-ttu-id="c5e92-169">![Salesforce 整合的完整 orchesration](../core/media/bts-sf-complete-orch.jpg "BTS_SF_Complete_Orch")</span><span class="sxs-lookup"><span data-stu-id="c5e92-169">![Complete orchesration for Salesforce integration](../core/media/bts-sf-complete-orch.jpg "BTS_SF_Complete_Orch")</span></span>  
  
     <span data-ttu-id="c5e92-170">將強式名稱金鑰檔加入至專案，並將變更儲存至專案。</span><span class="sxs-lookup"><span data-stu-id="c5e92-170">Add a strong name key file to the project and save changes to the project.</span></span>  
  
   <span data-ttu-id="c5e92-171">本主題中的步驟，我們已完成的協調流程，以接收來自 Salesforce 的商機通知、 查詢 Salesforce，如需詳細資訊的機會;，然後將查詢回應插入 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c5e92-171">With the steps in this topic, we have completed the orchestration, to receive an opportunity notification from Salesforce, query Salesforce for more details about the opportunity, and then insert the query response into a SQL Server database.</span></span> <span data-ttu-id="c5e92-172">在後續主題中，我們將建置一些其他重要元件的方案用來向 Salesforce 和 Salesforce 回應 BizTalk Server 中的程序。</span><span class="sxs-lookup"><span data-stu-id="c5e92-172">In the subsequent topics, we’ll build some other key components of the solution that are used to authenticate with Salesforce and process Salesforce response within BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5e92-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5e92-173">See Also</span></span>  
 [<span data-ttu-id="c5e92-174">步驟 3：在 Visual Studio 中建立 BizTalk Server 解決方案</span><span class="sxs-lookup"><span data-stu-id="c5e92-174">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)