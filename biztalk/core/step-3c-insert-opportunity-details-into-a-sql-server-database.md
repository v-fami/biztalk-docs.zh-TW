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
# <a name="step-3c-insert-opportunity-details-into-a-sql-server-database"></a>步驟 3c： 將機會詳細資料插入至 SQL Server 資料庫
現在我們已經建置協調流程以將查詢傳送到 Salesforce 並接收回應。 在本節中，我們會更新該協調流程以回應插入從到 Salesforce **OrderDetails**內部部署 SQL Server 資料庫中的資料表**訂單**。 若要達到此目的，我們會執行下列一組廣泛的步驟：  
  
- 建立**OrderDetails**資料表中**訂單**內部部署 SQL Server 資料庫中的資料庫。  
  
- 使用[!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)]隨附[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]上產生插入作業結構描述**OrderDetails**資料表。  
  
- 建立對應來轉換 Salesforce 回應訊息至訊息，以便插入**OrderDetails** SQL Server 中的資料表。  
  
- 更新協調流程使用要插入至回應訊息的轉換**OrderDetails**資料表。  
  
## <a name="create-sql-server-database-and-table"></a>建立 SQL Server 資料庫和資料表  
  
#### <a name="to-create-the-database-and-table"></a>若要建立資料庫和資料表  
  
1.  開啟 SQL Server Management Studio 並以系統管理員身分連接。  
  
2.  以滑鼠右鍵按一下**資料庫**節點，然後按一下**新的資料庫**。 將資料庫名稱指定為`Orders`並指定其他詳細資料，以建立新的資料庫。  
  
3.  開啟查詢編輯器，然後執行下列查詢，以建立**OrderDetails**資料表中**訂單**資料庫：  
  
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
  
## <a name="create-schema-for-insert-operation-on-orderdetails-table"></a>建立 OrderDetails 資料表上的插入作業的結構描述  
 安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]提供[!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)]，可用於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案，以產生插入作業的結構描述上**OrderDetails**資料表。 本節中的步驟建立的訊息結構描述。  
  
#### <a name="to-create-the-schema-for-insert-operation"></a>若要建立 Insert 作業的結構描述  
  
1. 以滑鼠右鍵按一下**BtsSalesforceIntegration**專案，指向**新增**，然後按一下**新增產生的項目**。 在 **加入產生的項目** 對話方塊中，按一下**取用配接器服務**，然後按一下 **新增**。  
  
2. 在  [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)]，從 選取繫結下拉式清單中，按一下**sqlBinding**，然後按一下**設定**。  
  
3. 在**設定介面卡**對話方塊的 **安全性**索引標籤上，如**用戶端認證類型**，選取**Windows**使用 Windows驗證連接到 SQL Server 資料庫。  
  
4. 在**設定介面卡**對話方塊的  **URI 屬性**索引標籤上，如**Initial Catalog**指定資料庫名稱 （訂單） 來連接到。 針對**Server**指定您要連接到 SQL Server 安裝所在的電腦名稱。 SQL Server 資料庫使用時間是否在同一部電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案中，您可以只放句點 (**。**)。 按一下 [確定] 。  
  
5. 在 [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)]按一下  **Connect**。 建立連線之後，請選取 合約類型作為**用戶端 （傳出作業）**。 底下**選取類別目錄**方塊中，展開**資料表**，按一下  **OrderDetails**資料表，然後在右窗格中按一下**插入**，然後按一下 **新增**。  
  
6. 指定**檔案名稱前置詞**如果您想要產生的結構描述識別碼的前置詞。 本教學課程中，讓我們指定做為前置詞**InsertOrders** ，然後按一下**確定**。  
  
    一連串的結構描述會新增至專案。 我們將使用插入到訊息的結構描述**OrderDetails**資料表**InsertOrdersTableOperation.dbo.OrderDetails.xsd**。  
  
## <a name="map-salesforce-response-and-insert-schemas"></a>對應 Salesforce 回應及插入結構描述  
 既然我們已經有兩個結構描述 (來自 Salesforce 和插入回應**OrderDetails**)，我們必須對應至插入結構描述從 Salesforce 的回應結構描述**OrderDetails**以便從 Salesforce 的回應訊息可以插入 SQL Server 資料庫資料表中。  
  
#### <a name="to-map-the-schemas"></a>若要在對應結構描述  
  
1.  以滑鼠右鍵按一下**BtsSalesforceIntegration**專案，指向**新增**，按一下 **新項目**，然後按一下**對應**。 指定對應名稱為`QueryResult_Orders.btm`，然後按一下 **新增**。  
  
2.  對應介面上，針對來源結構描述中，選取**QueryResult** ，然後針對目的地結構描述中，選取**InsertOrdersTableOperation.dbo.OrderDetails.xsd** ，然後在其中**插入**節點。  
  
3.  對應兩個結構描述，如下列螢幕擷取畫面所示：  
  
     ![對應至插入結構描述的 Salesforce 回應](../core/media/bts-sf-map-response-insert.jpg "BTS_SF_Map_Response_Insert")  
  
     請注意，地圖會使用**迴圈**之間的運算質**記錄**並**OrderDetails**連結。 這可確保所有一或多個節點下的次數**記錄**會對應至類似底下的節點發生次數**OrderDetails**。  
  
4.  儲存對應變更。  
  
## <a name="update-the-orchestration-to-insert-messages-into-sql-server"></a>更新協調流程將訊息插入 SQL Server  
 在本節中，我們將使用協調流程中的對應，將 Salesforce 回應訊息轉換成 SQL Server 資料表中插入訂單詳細資料的訊息。 我們也會新增至該訊息送到 SQL Server 的連接埠。  
  
#### <a name="to-update-the-orchestration"></a>若要更新的協調流程  
  
1. 建立插入結構描述的訊息變數。 從 [協調流程] 檢視中，以滑鼠右鍵按一下**訊息**節點，然後再按一下**新訊息**。 設定訊息名稱作為**InsertOrders**訊息做為類型**BtsSalesforceIntegration.InsertOrdersTableOperation_dbo_OrderDetails.Insert**。  
  
2. 新增 建構訊息 」 圖形之後**ReceiveQueryResult**圖形。 設定圖形的名稱`ConstructOrders`並設定**建構的訊息**屬性設**InsertOrders**。  
  
3. 內**ConstructOrders**圖形中新增**轉換**圖形。 按兩下以開啟 [轉換組態] 對話方塊中的 [轉換] 圖形。 在對話方塊中，選取**現有的對應**選項，然後再從下拉式清單選取**BtsSalesforceIntegration.QueryResult_Orders**。 設定**來源**來**QueryResultMsg**，**目的地**來**InsertOrders**，然後按一下**確定**。  
  
4. 在後**ConstructOrders**圖形中新增 「 傳送 」 圖形。 命名圖形`SendOrders`並設定為訊息類型**InsertOrders**。  
  
5. 新增 Salesforce 中插入訂單詳細資料的連接埠。 在 [連接埠組態精靈] 中，選取下列選項：  
  
   - 將連接埠名稱指定為`SendToSQL`。  
  
   - 選取 [建立新的連接埠類型] 選項。  
  
   - 設定**通訊模式**要*單向*。  
  
   - 設定**連接埠通訊方向**要*我將總是傳送的訊息在此連接埠*並設定**連接埠繫結**至*稍後指定*。  
  
     連接**要求**連接埠的作業**SendOrders**傳送完成的協調流程的圖形。 下列螢幕擷取畫面說明完成的協調流程，端對端。  
  
     ![Salesforce 整合的完整 orchesration](../core/media/bts-sf-complete-orch.jpg "BTS_SF_Complete_Orch")  
  
     將強式名稱金鑰檔加入至專案，並將變更儲存至專案。  
  
   本主題中的步驟，我們已完成的協調流程，以接收來自 Salesforce 的商機通知、 查詢 Salesforce，如需詳細資訊的機會;，然後將查詢回應插入 SQL Server 資料庫。 在後續主題中，我們將建置一些其他重要元件的方案用來向 Salesforce 和 Salesforce 回應 BizTalk Server 中的程序。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3：在 Visual Studio 中建立 BizTalk Server 解決方案](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)