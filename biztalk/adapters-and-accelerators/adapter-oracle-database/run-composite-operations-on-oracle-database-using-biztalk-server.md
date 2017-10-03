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
# <a name="run-composite-operations-on-oracle-database-using-biztalk-server"></a>執行複合操作 Oracle 資料庫使用 BizTalk Server 上
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓配接器執行複合操作 Oracle 資料庫上的用戶端。 複合作業可包括：  
  
-   插入、 更新、 刪除和選取資料表和檢視表上的作業。  
  
-   預存程序和函式，內部或外部的封裝。  
  
 單一複合作業可以有任意數目的這些作業，以任何順序。 比方說，您可以有兩個插入後面刪除，以及最後的預存程序執行。 此外，您可以有不同的資料庫資料表或檢視表為目標的不同作業。 如需配接器如何支援複合操作的詳細資訊，請參閱[Oracle 資料庫中執行複合操作](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-in-oracle-database.md)。 複合操作的 SOAP 訊息結構的相關資訊，請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md)。  
  
## <a name="how-to-perform-composite-operations-on-oracle-database"></a>如何執行複合操作 Oracle 資料庫上？  
 使用 Oracle 資料庫上執行操作[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)。 若要執行複合操作 Oracle 資料庫上的，這些工作包括：  
  
1.  建立 BizTalk 專案中的[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並產生您想要叫用的所有作業的結構描述。  
  
2.  手動建立結構描述檔案，其中包含您在上一個步驟中產生的所有結構描述的參考。  
  
3.  建立傳送和從 Oracle 資料庫接收訊息的 BizTalk 專案中的訊息。 這些訊息必須符合您在上一個步驟中建立的要求和回應結構描述。  
  
4.  建立協調流程叫用 Oracle 資料庫上的複合作業。  
  
5.  建置和部署 BizTalk 專案。  
  
6.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
7.  啟動 BizTalk 應用程式。  
  
 本主題提供有關如何執行這些工作的指示。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題中，為了示範如何執行複合操作，我們會執行相同的順序的下列工作：  
  
-   將記錄插入 ACCOUNTACTIVITY 資料表。  
  
-   藉由叫用 GET_ALL_ACTIVITY 內的程序 ACCOUNT_PKG 封裝擷取 ACCOUNTACTIVITY 資料表中的所有記錄。  
  
-   從 ACCOUNTACTIVITY 資料表刪除記錄。  
  
 執行與範例來建立 ACCOUNTACTIVITY 資料表所提供的指令碼。 如需這些範例的詳細資訊，請參閱[結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)。  
  
 您必須建立 BizTalk 專案，並使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生結構描述。 請參閱[擷取 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)如需有關如何產生結構描述。  
  
## <a name="creating-a-composite-schema-definition"></a>建立複合的結構描述定義  
 您現在必須建立複合的結構描述中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]參考您針對個別作業所建立之結構描述的 BizTalk 專案。 執行下列步驟，以建立複合的結構描述定義。  
  
#### <a name="to-add-a-composite-schema-definition"></a>若要加入複合的結構描述定義  
  
1.  將結構描述檔案中的 BizTalk 專案加入[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 以滑鼠右鍵按一下方案名稱，指向**新增**，然後按一下 **新項目**。 在**加入新項目**對話方塊中，從**類別**方塊中，按一下**結構描述檔案**。 從**範本**方塊中，按一下**結構描述**。 指定結構描述檔案的名稱，然後按一下**確定**。  
  
     此範例中，結構描述檔案名稱指定為`CompositeSchema.xsd`。  
  
2.  將參考加入至您想要執行的不同作業產生的結構描述。 在此範例中，不同的結構描述產生的作業如下：  
  
    -   OracleDBBinding.xsd ACCOUNTACTIVITY 資料表的 Insert 和 Delete 作業。  
  
    -   OracleDBBinding2.xsd GET_ALL_ACTIVITY 程序。  
  
     若要加入的參考：  
  
    1.  以滑鼠右鍵按一下根**\<結構描述 >**中 CompositeSchema.xsd，按一下節點**屬性**。  
  
    2.  在**屬性**方塊中，按一下省略符號按鈕**（...）**針對**匯入**屬性。  
  
         ![匯入結構描述定義](../../adapters-and-accelerators/adapter-oracle-database/media/d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca.gif "d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca")  
  
    3.  在**匯入**對話方塊中，從**匯入新結構描述為**清單中，選取**XSD 匯入**，然後按一下 **新增**。  
  
    4.  在**BizTalk 型別選擇器**對話方塊方塊中，展開 BizTalk 專案名稱節點，展開**結構描述**，然後選取您要匯入的結構描述。 此範例中，選取 < BizTalk_project_name >。OracleDBBinding.xsd。 按一下 **[確定]**。  
  
         重複此步驟，匯入 < BizTalk_project_name >。OracleDBBinding2.xsd 太。  
  
    5.  在**匯入**對話方塊中，按一下 **確定**。  
  
3.  將兩個子節點加入至根結構描述節點。 一個子節點對應至要求結構描述執行複合作業。 另一個子節點對應至回應結構描述。 對應至要求結構描述的節點可以有任何名稱。 對應至回應結構描述的節點必須呼叫 < request_schema_node > 回應。 針對此範例中，我們會呼叫要求結構描述節點，做為**要求**。 因此，呼叫的回應結構描述節點**RequestResponse**。  
  
    > [!NOTE]
    >  根據預設，**根**節點也會加入至新的結構描述檔案。 您可以重新命名**根**節點**要求**。 若要重新命名的節點，以滑鼠右鍵按一下節點名稱，然後按一下**重新命名**。  
  
     若要加入的節點下**\<結構描述 >**節點：  
  
    1.  以滑鼠右鍵按一下**\<結構描述 >**節點，指向**插入結構描述節點**，然後按一下**子記錄**。  
  
    2.  重新命名新的節點**RequestResponse**。  
  
4.  加入子節點底下**要求**對應到複合作業的一部分，您將執行每個作業的要求結構描述的節點。 對於此範例中，您必須將對應於下列子節點：  
  
    -   插入和刪除 ACCOUNTACTIVITY 資料表上的作業。  
  
    -   GET_ALL_ACTIVITY 程序。  
  
    > [!IMPORTANT]
    >  您必須將節點加入您要執行作業的順序相同。 例如，如果您想要插入的記錄，然後執行預存程序，然後刪除記錄，您必須先新增的節點代表插入作業，後面接著預存程序中，節點和最後一個刪除作業。  
  
     若要加入至子節點**要求**節點：  
  
    1.  以滑鼠右鍵按一下**要求**節點，指向**插入結構描述節點**，然後按一下 **子記錄**。  
  
         ![插入結構描述的子節點](../../adapters-and-accelerators/adapter-oracle-database/media/58992131-13a6-45c3-9513-5c0995091fae.gif "58992131-13a6-45c3-9513-5c0995091fae")  
  
    2.  重新命名為對應至複合作業的一部分執行的操作的要求結構描述的記錄。 例如，重新命名 「 插入 」 至節點。  
  
    3.  地圖**插入**ACCOUNTACTIVITY 資料表的 Insert 作業的要求結構描述的節點。 若要這樣做，請以滑鼠右鍵按一下**插入**節點，然後按一下**屬性**。 在**屬性** 方塊中，從**資料結構型別**清單中，選取**插入 （參考）**。  
  
         ![將子節點對應至要求結構描述](../../adapters-and-accelerators/adapter-oracle-database/media/b4ebd3c7-14e5-4c37-abd7-83f0b4db4c9e.gif "b4ebd3c7-14e5-4c37-abd7-83f0b4db4c9e")  
  
    4.  重複這些步驟來加入 GET_ALL_ACTIVITY 預存程序和刪除作業的要求結構描述的節點。 指定節點名稱，然後將它們對應至對應的結構描述，如下列表格中所述。  
  
        |節點名稱|對應至結構描述|  
        |---------------|----------------------|  
        |GET_ALL_ACTIVITY|GET_ALL_ACTIVITY （參考）|  
        |DELETE|刪除 （參考）|  
  
5.  加入子節點底下**RequestResponse**對應到複合作業的一部分，您將執行每個作業的回應結構描述的節點。 對於此範例中，您必須將對應於下列子節點：  
  
    -   插入和刪除 ACCOUNTACTIVITY 資料表上的作業。  
  
    -   GET_ALL_ACTIVITY 預存程序。  
  
    > [!IMPORTANT]
    >  您必須加入子節點下的子節點的順序相同**要求**節點。  
  
     若要加入至子節點**RequestResponse**節點：  
  
    1.  以滑鼠右鍵按一下**RequestResponse**節點，指向**插入結構描述節點**，然後按一下**子記錄**。  
  
    2.  重新命名為對應至複合作業的一部分執行的操作的回應結構描述的記錄。 例如，重新命名 「 InsertResponse"的節點。  
  
    3.  地圖**InsertResponse** ACCOUNTACTIVITY 資料表的 Insert 作業的回應結構描述的節點。 若要這樣做，請以滑鼠右鍵按一下**InsertResponse**節點，然後按一下**屬性**。 在**屬性** 方塊中，從**資料結構型別**清單中，選取**InsertResponse （參考）**。  
  
    4.  重複這些步驟來加入 GET_ALL_ACTIVITY 預存程序和刪除作業的回應結構描述的節點。 指定節點名稱，然後將它們對應至對應的結構描述，如下列表格中所述。  
  
        |節點名稱|對應至結構描述|  
        |---------------|----------------------|  
        |GET_ALL_ACTIVITYResponse|GET_ALL_ACTIVITYResponse （參考）|  
        |DeleteResponse|DeleteResponse （參考）|  
  
6.  儲存**CompositeSchema.xsd**檔案。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您在最後一個步驟中建立複合結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 您現在必須建立協調流程的訊息，並將它們連結至您在上一個步驟中建立的結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>建立訊息，以及連結至結構描述  
  
1.  中的 BizTalk 專案中新增協調流程[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 從 方案總管 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下 **新項目**。 輸入 BizTalk 協調流程的名稱，然後按一下**新增**。  
  
2.  如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。  
  
3.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
4.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
5.  在**屬性**窗格**Message_1**，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Request`|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*Composite_Op.CompositeSchema.Request*Composite_Op 所在的 BizTalk 專案的名稱。 CompositeSchema 是手動建立的複合作業的結構描述。|  
  
6.  重複步驟 2 來建立新的訊息。 在**屬性**窗格新訊息中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|輸入 `Response`|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*Composite_Op.CompositeSchema.RequestResponse*。|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行複合操作 Oracle 資料庫上的。 在此協調流程中，卸除要求訊息已定義的接收位置。 要求訊息必須符合您稍早建立的複合結構描述。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會取用這個訊息，並將它傳遞到 Oracle 資料庫。 從 Oracle 資料庫的回應會儲存到另一個位置。 您必須包含傳送和接收圖形，將訊息傳送至 Oracle 資料庫，並接收回應，分別。 用於執行複合操作的基本協調流程如下所示：  
  
 ![用於執行複合操作的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb.gif "4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息圖形指定下列屬性。 圖形資料行中所列的名稱是訊息 圖形的名稱，為顯示在剛才提及的協調流程中。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**至*ReceiveMessage*<br />-設定**啟動**至*，則為 True*|  
|SendMessage|Send|-設定**名稱**至*SendMessage*|  
|ReceiveResponse|Receive|-設定**名稱**至*ReceiveResponse*<br />-設定**啟動**至*False*|  
|SendResponse|Send|-設定**名稱**至*SendResponse*|  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠指定下列屬性。 連接埠資料行中所列的名稱是連接埠的名稱，為顯示協調流程中。  
  
|通訊埠|屬性|  
|----------|----------------|  
|MessageIn|-設定**識別碼**至*MessageIn*<br />-設定**類型**至*MessageInType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*接收*|  
|LOBPort|-設定**識別碼**至*LOBPort*<br />-設定**類型**至*LOBPortType*<br />-設定**通訊模式**至*要求-回應*<br />-設定**通訊方向**至*傳送接收*|  
|ResponseOut|-設定**識別碼**至*ResponseOut*<br />-設定**類型**至*ResponseOutType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*傳送*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>指定訊息的動作圖形，並將它們連接至連接埠  
 下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。 圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**訊息**至*要求*<br />-設定**作業**至*MessageIn.CompositeOp.Request*|  
|SendMessage|-設定**訊息**至*要求*<br />-設定**作業**至*LOBPort.CompositeOp.Request*|  
|ReceiveResponse|-設定**訊息**至*回應*<br />-設定**作業**至*LOBPort.CompositeOp.Response*|  
|SendResponse|-設定**訊息**至*回應*<br />-設定**作業**至*ResponseOut.CompositeOp.Request*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 在 [協調流程] 窗格中您已部署的 BizTalk 專案後，會列出您稍早建立的協調流程[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。 如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 此協調流程中，您必須：  
  
    -   定義位置上的硬碟和對應的檔案連接埠，您將在此置放要求訊息。 BizTalk 協調流程會使用要求訊息，並將它傳送給 Oracle 資料庫。  
  
    -   定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含從 Oracle 資料庫回應的回應訊息。  
  
    -   定義實體 Wcf-custom 或 Wcf-oracledb 傳送埠將訊息傳送至 Oracle 資料庫。 因為作業都是因為在單一交易中，執行屬於複合作業確定**UseAmbientTransaction**繫結屬性設定為**True**。  
  
         您也必須在傳送埠中指定的動作。 複合作業的動作是 「 http://Microsoft.LobServices.OracleDB/2007/03/CompositeOperation"。 如需如何建立連接埠相關資訊，請參閱[手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。 如需如何指定連接埠動作的詳細資訊，請參閱[設定 Oracle 資料庫的 SOAP 動作](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md)。  
  
        > [!NOTE]
        >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。 您可以從這個繫結檔案匯[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （用於進行傳入呼叫時）。 如需詳細資訊，請參閱[設定使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。 如果您匯入此繫結檔案時，傳送埠上的動作會設定為與您在選取的所有作業都有關的動態動作[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]時產生結構描述。 複合作業中，您必須取代的動態 「 http://Microsoft.LobServices.OracleDB/2007/03/CompositeOperation 」 動作。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動執行複合操作 Oracle 資料庫上的 BizTalk 應用程式。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   Wcf-custom 或 Wcf-oracledb 傳送埠將訊息傳送至 Oracle 資料庫正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須先卸除要求訊息到檔案接收位置。 要求訊息的結構描述必須符合您稍早建立的複合作業的結構描述。 例如，ACCOUNTACTIVITY 資料表中插入記錄、 叫用的 GET_ALL_ACTIVITY 預存程序，並從 ACCOUNTACTIVITY 資料表中刪除記錄的要求訊息是：  
  
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
  
 先前的要求訊息第一次插入一筆記錄，然後再叫用的 GET_ALL_ACTIVITY 程序取得 ACCOUNTACTIVITY 資料表中的所有記錄。 然後，插入的記錄會刪除指定的篩選子句。 請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md)如需有關要求訊息結構描述，用於執行複合操作 oracle 資料庫使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
 協調流程取用訊息，並將它傳送到 Oracle 資料庫。 從 Oracle 資料庫的回應會儲存在其他的協調流程中定義的檔案位置。 例如，從先前的要求訊息的 Oracle 資料庫回應如下所示：  
  
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
  
 上述的回應會包含多個結果集對應複合作業的一部分執行的不同作業。 例如，`InsertResult`元素包含 '1'，表示插入作業所插入的資料列數目。 同樣地，`DeleteResult`元素包含 '1'，表示刪除作業所刪除的資料列數目。  
  
> [!IMPORTANT]
>  如果您執行複合操作時遇到逾時問題然後可能是因為連線的數目小於的複合運算涉及作業數目：  
>   
>  -   預存程序包含 BFILE、 BLOB、 CLOB、 NCLOB、 和 REF CURSOR 做為 OUT 或 IN OUT 參數。  
> -   選取作業。  
>   
>  若要解決此問題，您必須確定是否有"n"這類的複合運算中的作業數目，為指定的值**MinPoolSize**繫結屬性是"n + 1"或更新版本。 如需有關**MinPoolSize**繫結屬性，請參閱[使用繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，可以組態設定匯入檔案，使您不需要建立項目，例如傳送埠和接收相同的協調流程連接埠。 如需繫結檔案的詳細資訊，請參閱[重複使用 Oracle 資料庫配接器繫結](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)