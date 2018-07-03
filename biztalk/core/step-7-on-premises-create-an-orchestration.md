---
title: 步驟 7 （內部部署）： 建立協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c0b6d0e-cf00-4eee-9b89-28210bad46f4
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc072b664b453a3f10b624f75fe161a515ecc902
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975815"
---
# <a name="step-7-on-premises-create-an-orchestration"></a>步驟 7 （內部部署）： 建立協調流程
根據商務案例之後,[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收銷售訂單訊息的服務匯流排佇列中，它需要檢查訊息中所訂購的數量是否大於 100。 如果數量大於 100 時，要將訊息插入至**SalesOrder**資料表。 否則，訊息會傳送至共用的檔案位置。 Northwind 會達成此商務邏輯，藉由建立協調流程。 本主題提供有關如何建立協調流程的逐步指引。  
  
### <a name="to-add-an-orchestration-to-the-includebtsbiztalkservernoversionincludesbtsbiztalkservernoversion-mdmd-project"></a>若要新增至協調流程[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您已經建立，以滑鼠右鍵按一下專案，指向**新增**，然後按一下**新項目**。  
  
2. 在 **新項目**對話方塊中，選取**BizTalk 協調流程**，輸入對應名稱為`OrderProcessing.odx`，然後按一下 **新增**。  
  
## <a name="create-messages-for-the-orchestration"></a>建立協調流程的訊息  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是的變數，其對應的結構描述所定義的型別。 現在，您必須建立協調流程的訊息，並將它們連結至您稍早產生的結構描述。 您需要建立下列三個訊息：  
  
|訊息名稱|對應到結構描述|  
|------------------|---------------------------|  
|Message1_SO_Inbound|這是訊息的執行個體**ECommerceSalesOrder.xsd**結構描述。|  
|Message2_SO_Inbound|此訊息是一份**Message1_SO_Inbound**。 最佳做法，您必須建立訊息的複本，並修改新訊息，讓原始訊息保持不變。 如需詳細資訊，請參閱 < [BizTalk Server 訊息](http://msdn.microsoft.com/library/aa560436)。|  
|Message1_SO_Outbound|這是訊息的執行個體**TableOperations.dbo.SalesOrder (Insert)** 結構描述。|  
  
#### <a name="to-create-the-messages"></a>建立訊息  
  
1.  開啟**協調流程檢視**的 BizTalk 專案中，如果它尚未開啟的視窗。 若要這樣做，請按一下**檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
2.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
3.  以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  
  
4.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  
  
    |屬性名稱|執行動作|  
    |-------------------|--------------------|  
    |識別碼|輸入 `Message1_SO_Inbound`|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*OrderProcessingDemo.ECommerceSalesOrder*，其中 *[orderprocessingdemo]* 是 BizTalk 的名稱專案。 *ECommerceSalesOrder*是從 「 服務匯流排 」 佇列接收的銷售訂單訊息的結構描述。|  
  
5.  重複步驟來建立訊息詳細資料如下：  
  
    |訊息名稱||  
    |------------------|-|  
    |Message2_SO_Inbound|-設定**識別碼**至 `Message2_SO_Inbound`<br />-設定**訊息類型**到*OrderProcessingDemo.ECommerceSalesOrder*|  
    |Message1_SO_Outbound|-設定**識別碼**至 `Message1_SO_Outound`<br />-設定**訊息類型**到*OrderProcessingDemo.TableOperation_dbo_SalesOrder.Insert*|  
  
## <a name="add-shapes-to-the-orchestration"></a>新增圖形至協調流程  
 協調流程圖形定義的流程[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。 在本節中，您可以新增必要的圖形至協調流程。  
  
#### <a name="to-add-shapes-to-the-orchestration"></a>若要將圖形加入至協調流程  
  
1.  若要開始，您必須新增**接收**圖形。 此圖形會接收連入的服務匯流排佇列的銷售訂單訊息。 在 [接收] 圖形上設定下列屬性。  
  
    1.  設定**啟用**要 **，則為 True**。  
  
    2.  設定**訊息**要**Message1_SO_Inbound**。  
  
    3.  設定**名稱**要**ReceiveOrder**。  
  
2.  如先前所述，您必須建立一份原始接收進入協調流程的銷售訂單訊息。  
  
    1.  拖放**建構的訊息**圖形下**ReceiveOrder**圖形。 因為您可以使用此圖形來建構類型 Message2_SO_Inbound 的訊息，設定**建構的訊息**屬性設**Message2_SO_Inbound**。  
  
    2.  新增**訊息指派**圖形內**建構訊息**圖形。 按兩下圖形以開啟 運算式編輯器中，並新增下列內容：  
  
        ```  
        Message2_SO_Inbound = Message1_SO_Inbound; //copy the message  
        Message2_SO_Inbound(*) = Message1_SO_Inbound(*); //copy the context properties on the message  
        ```  
  
         按一下 [確定] 。  
  
3.  根據商務案例中，訊息必須傳送至不同的目的地，根據已排序的項目數量。 因此，您必須現在擷取數量值傳入銷售訂單訊息。  
  
    1.  **Quantity** (ECommerceSalesOrder.xsd) 的輸入訊息中的項目包含訂購的數量的值。 您必須提升該屬性，使項目可用於協調流程中的運算式。 若要升級的屬性，開啟**ECommerceSalesOrder.xsd**結構描述，以滑鼠右鍵按一下**數量**，指向**升階**，然後按一下 **快速升級**.  
  
    2.  建立變數來儲存數量值。 若要建立的變數，從**協調流程檢視**，以滑鼠右鍵按一下**變數**，然後按一下**新變數**。 設定變數的下列屬性：  
  
        |屬性名稱|ReplTest1|  
        |-------------------|-----------|  
        |識別碼|輸入 `quantityOrdered`|  
        |類型|選取  **Int32**。|  
  
    3.  您現在必須將指派中的值**Quantity**項目**quantityOrdered**變數。 拖放**運算式編輯器**之後**建構訊息**圖形。 開啟編輯器，並輸入下列運算式：  
  
        ```  
        quantityOrdered = Message2_SO_Inbound.Quantity;  
        ```  
  
         按一下 [確定] 。  
  
4.  解壓縮之後的訂單數量，您現在需要建立的決策區塊，您的版面配置兩個不同的訊息流程會採用的路徑。 您在協調流程中建立的決策區塊加**決定**圖形。  
  
    1.  將拖放**決定**圖形之後**運算式編輯器**圖形。  
  
    2.  選取 [ **Rule_1**圖形然後在**屬性**] 視窗中，指定下列項目：  
  
        |屬性名稱|ReplTest1|  
        |-------------------|-----------|  
        |識別碼|輸入`Yes`。 **注意︰** 其他路由的預設名稱為**Else**。|  
        |運算式|輸入`quantityOrdered > 100`。|  
  
         您現在有兩個可用的路由。 如果中的值**quantityOrdered**變數是否大於 100，訊息會**是**路由。 否則，它會帶**Else**路由。 您現在必須定義要在每個路由中執行的動作。  
  
5.  根據商務案例，如果訂單數量大於 100，訊息必須插入至 SalesOrder 資料表。 因此，在**是**路由，您必須轉換 ECommerceSalesOrder.xsd 結構描述 TableOperations.SalesOrder.Insert 結構描述。 主題中建立插入結構描述[步驟 5 （內部部署）： 產生將訊息插入至 SalesOrder 資料表的結構描述](../core/step-5-generate-the-schema-for-inserting-a-message-into-salesorder-table.md)。 之後轉換結構描述，您必須傳送出訊息，以 SQL Server 資料庫資料表的訊息。  
  
    1.  內 **[是]** 路由傳送、 拖曳和卸除**建構訊息**圖形。 設定**建構的訊息**至圖形的屬性**Message1_SO_Outbound**。  
  
    2.  內**建構的訊息**圖形加入**轉換**圖形。 按兩下圖形以開啟**轉換組態** 對話方塊。 執行下列動作：  
  
        1.  選取 **現有的對應**選項。  
  
        2.  從**完整格式對應名稱**下拉式清單中，選取**OrderProcessingDemo.SalesOrder_SQL**。  
  
        3.  針對**來源**，選取**Message2_SO_Inbound**。  
  
        4.  針對**目的地**，選取**Message1_SO_Outound**。  
  
    3.  之後**建構的訊息**圖形、 拖曳和卸除**傳送**圖形，並設定**訊息**圖形，以屬性`Message1_SO_Outbound`。  
  
6.  根據商務案例，如果訂單數量小於 100，訊息必須傳送至共用的檔案位置。 因此，在**Else**路由，您必須新增 「 傳送 」 圖形。  
  
    1.  內**Else**路由傳送、 拖曳和卸除**傳送**圖形，並將**訊息**圖形，以屬性`Message2_SO_Inbound`。  
  
        > [!NOTE]
        >  因為相同接收來自服務匯流排佇列的訊息會傳送至檔案位置，而不進行任何處理，您可以設定為 Message2_SO_Inbound 的訊息。 Message2_SO_Inbound 表示接收的服務匯流排佇列的訊息。  
  
## <a name="add-ports-to-the-orchestration"></a>將連接埠加入協調流程  
 連接埠代表輸入和輸出媒介中轉移相關的協調流程的訊息。 訊息所使用的協調流程中使用的接收埠，並送出使用傳送埠。 在商務案例中，會將訊息從一個媒體 （服務匯流排佇列） 接收，並傳送到兩個不同位置 （SQL Server 資料庫或檔案共用位置） 為基礎的訊息處理。 因此，您必須建立一個接收埠和兩個傳送埠協調流程的一部分。  
  
#### <a name="to-add-ports"></a>若要新增連接埠  
  
1.  將拖放**連接埠**圖形至**連接埠介面**窗格**協調流程設計師**以啟動**連接埠組態精靈**。 在 [**歡迎**頁面上，按一下**下一步]**。  
  
2.  在 **連接埠內容**頁面上，為埠命名`ReceiveSO`，然後按一下 **下一步**。  
  
3.  在 **選取連接埠類型**頁面上，選取**建立新的連接埠類型**選項，然後選取**單向**通訊模式中，保留 存取限制的預設值，然後按一下 **下一步**。  
  
4.  在**連接埠繫結**頁面上，針對連接埠的選取方向**我將一律接收訊息，在此連接埠**保留為預設值，飛過的連接埠，然後按一下 [**下一步]**.  
  
5.  在最後一個頁面上，按一下**完成**。  
  
6.  重複步驟來建立兩個傳送埠。 在建立連接埠時，請指定下列值。  
  
    |連接埠名稱|屬性|  
    |---------------|----------------|  
    |[Sendtosql]|-設定**名稱**到**SendToSQL**<br />-選取**建立新的連接埠類型**<br />集通訊模式來**單向**<br />-若要設定連接埠方向**我將總是傳送的訊息在此連接埠**|  
    |[Sendtofile]|-設定**名稱**到 **[sendtofile]**<br />-選取**建立新的連接埠類型**<br />集通訊模式來**單向**<br />-若要設定連接埠方向**我將總是傳送的訊息在此連接埠**|  
  
## <a name="connect-ports-and-message-shapes"></a>連接連接埠和訊息圖形  
 您現在必須連接連接埠和訊息圖形，以完成協調流程。 當收到訊息時，會啟動協調流程**ReceiveOrder**圖形與協調流程結束時將訊息送出兩個傳送圖形。 您必須使用此條件來連接的連接埠和訊息圖形  
  
#### <a name="to-connect-ports-with-message-shapes"></a>連接埠與訊息圖形  
  
1.  連接**ReceiveSO**接收埠以**ReceiveOrder**圖形。  
  
2.  連接 「 傳送 」 圖形之下 **[是]** 路由傳送至**SendToSQL**傳送埠。 這表示如果訊息進入此路由 (**quantityOrdered** > 100)，它會傳送到**SalesOrder** SQL Server 資料庫中的資料表。  
  
3.  連接 「 傳送 」 圖形之下**Else**路由傳送至**SendToFile**傳送埠。 這表示如果訊息進入此路由 (**quantityOrdered** < = 100)，它會傳送至指定的檔案位置。  
  
     協調流程必須如下所示：  
  
     ![協調流程](../core/media/bts2010r2-tut1-orch.jpg "BTS2010R2_Tut1_Orch")  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)