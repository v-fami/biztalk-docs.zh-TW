---
title: "執行與 Oracle 資料庫中的大型物件資料類型的資料表上的作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operations, performing on tables
- operations, performing on LOB data
ms.assetid: 74276b85-daf1-4d0f-92f9-46d5c27a95a6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a1116947450fb1d900ea38be0254fb3d0f7f7c1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="run-operations-on-tables-with-large-object-data-types-in-oracle-database"></a>執行與 Oracle 資料庫中的大型物件資料類型的資料表上的作業
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]提供 Oracle 大型物件 (LOB) 資料類型的支援：  
  
-   二進位大型物件 (BLOB)  
  
-   字元大型物件 (CLOB)  
  
-   國家 （地區） 的字元大型物件 (NCLOB)  
  
-   二進位檔案 (BFILE)。 如需詳細資訊，請參閱[BFILE 資料型別使用 BizTalk Server 的 Oracle 資料庫中之資料表上執行的作業](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-bfile-data-types-in-oracle-db-using-biztalk.md)。  
  
 [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]做法是，面對 ReadLOB 和 UpdateLOB 作業，針對包含 LOB 資料行的資料表。 如需有關這些作業，請參閱[資料表和檢視表，包含 LOB 資料 Oracle 資料庫中的作業](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-and-views-that-contain-lob-data-in-oracle-database.md)。 如需叫用這些作業的 SOAP 訊息結構的詳細資訊，請參閱[特殊 LOB 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md)。  
  
> [!NOTE]
>  當使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，ReadLOB 作業不支援從 Oracle 資料庫的資料流 LOB 類型資料。 若要從 Oracle 資料庫使用資料流 LOB 資料[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]您應該改為使用選取的作業。 如需串流的詳細資訊，請參閱[Oracle 資料庫中的 LOB 資料類型的資料流支援](../../adapters-and-accelerators/adapter-oracle-database/streaming-support-for-lob-data-types-in-oracle-database.md)。 此外，從 Oracle 資料庫 ReadLOB 作業回應將會失敗的驗證，WSDL。 如需如何解決失敗的指示，請參閱[疑難排解操作問題](https://msdn.microsoft.com/library/dd787883.aspx)。  
  
## <a name="how-to-perform-operations-on-lob-data"></a>如何在 LOB 資料上執行作業？  
 針對 Oracle 資料庫使用執行運算[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)。 要叫用 Oracle 資料庫中資料表上的 ReadLOB 和 UpdateLOB 作業，這些工作包括：  
  
1.  建立 BizTalk 專案，並產生 ReadLOB 和 UpdateLOB 作業的結構描述。  
  
2.  建立傳送和從 Oracle 資料庫接收訊息的 BizTalk 專案中的訊息。 您必須建立傳送要求和接收這兩項作業的回應訊息。  
  
3.  建立協調流程叫用 ReadLOB 和 UpdateLOB 作業。  
  
4.  建置和部署 BizTalk 專案。  
  
5.  設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6.  啟動 BizTalk 應用程式。  
  
 本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 基礎的範例，Operate_LOB，本主題也會提供[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 在本主題中，以示範如何執行 ReadLOB 和 UpdateLOB 作業，我們會產生下 SCOTT 結構描述的 Oracle 資料庫中的 CUSTOMER 資料表中顯示這些作業的中繼資料。 SCOTT 結構描述下建立此資料表，執行下列 SQL 指令碼提供範例。 若要深入了解這些範例，請參閱[結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。 訊息通常是為其型別由對應的結構描述所定義的變數。 您必須連結產生的結構描述您在第一個步驟中的訊息從 BizTalk 專案的 [協調流程檢視] 視窗。  
  
 本主題中，您必須建立兩個要求-回應訊息集 — 一個要求-回應設定 ReadLOB 作業和第二個要求-回應針對 UpdateLOB 作業進行設定。  
  
 執行下列步驟來建立訊息，並將其連結至結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>建立訊息，以及連結至結構描述  
  
1.  如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。  
  
2.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。  
  
3.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  
  
4.  在**屬性**窗格**Message_1**，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |識別碼|型別**要求**。|  
    |訊息類型|從下拉式清單中，展開 **結構描述**，然後選取*Operate_LOB。OracleDBBindingSchema.ReadLOB**，*其中*Operate_LOB*是您的 BizTalk 專案的名稱。 *OracleDBBindingSchema*是 CUSTOMER 資料表的 ReadLOB 和 UpdateLOB 作業產生的結構描述。|  
  
5.  重複上述步驟，建立三個的多個訊息。 在**屬性**窗格，以新的訊息，執行下列動作：  
  
    |若要設定識別項|若要設定訊息類型|  
    |-----------------------|-------------------------|  
    |回應|*Operate_LOB。OracleDBBindingSchema.ReadLOBResponse*|  
    |Request2|*Operate_LOB。OracleDBBindingSchema.UpdateLOB*|  
    |Response2|*Operate_LOB。OracleDBBindingSchema.UpdateLOBResponse*|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]叫用 ReadLOB 和 UpdateLOB 資料表上的作業。 在此協調流程，您卸除兩個要求訊息，一個用於 ReadLOB 作業，另一個則用於 UpdateLOB 作業。 在接收位置就會捨棄這些訊息。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]取用訊息，並將其傳遞到 Oracle 資料庫中，透過 ODP。 從 Oracle 資料庫的回應會儲存到另一個位置。  
  
 因為協調流程會挑選兩個要求同時，您需要在協調流程中包含平行動作圖形。 針對每個平行的動作，您必須包含傳送和接收圖形以將訊息傳送至 Oracle 資料庫，並接收回應。 不過，您可以使用相同的連接埠來傳送和接收訊息，這兩個作業。 典型的協調流程同時執行 ReadLOB 和 UpdateLOB 作業就會包含：  
  
-   傳送和接收圖形以將訊息傳送至 Oracle 資料庫，並接收回應。  
  
-   單向接收埠以接收要求訊息傳送到 Oracle 資料庫。  
  
-   雙向傳送埠以傳送要求訊息到 Oracle 資料庫，並接收回應。  
  
-   單向傳送埠，以便從 Oracle 資料庫的回應傳送到資料夾。  
  
 範例協調流程如下所示：  
  
 ![用於讀取和更新 LOB 資料的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/6523b5e4-3689-433a-8287-eebc36f10442.gif "6523b5e4-3689-433a-8287-eebc36f10442")  
  
### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息圖形指定下列屬性。 圖形資料行中所列的名稱是訊息 圖形的名稱，為顯示在剛才提及的協調流程中。 下表列出您必須將包含在其中一個平行動作圖形。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**至*ReceiveMessage*<br />-設定**啟動**至*，則為 True*|  
|SendMessage|Send|-設定**名稱**至*SendMessage*|  
|ReceiveResponse|Receive|-設定**名稱**至*ReceiveResponse*<br />-設定**啟動**至*False*|  
|SendResponse|Send|-設定**名稱**至*SendResponse*|  
  
 下表列出您必須包含平行動作圖形。  
  
|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage2|Receive|-設定**名稱**至*ReceiveMessage2*<br />-設定**啟動**至*，則為 True*|  
|SendMessage2|Send|-設定**名稱**至*SendMessage2*|  
|ReceiveResponse2|Receive|-設定**名稱**至*ReceiveResponse2*<br />-設定**啟動**至*False*|  
|SendResponse2|Send|-設定**名稱**至*SendResponse2*|  
  
### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠指定下列屬性。 連接埠資料行中所列的名稱是連接埠的名稱，為顯示協調流程中。  
  
|通訊埠|屬性|  
|----------|----------------|  
|FileIn|-設定**識別碼**至*FileIn*<br />-設定**類型**至*FileInType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*接收*|  
|LOBPort|-設定**識別碼**至*LOBPort*<br />-設定**類型**至*LOBPortType*<br />-設定**通訊模式**至*要求-回應*<br />-設定**通訊方向**至*傳送接收*|  
|SaveResponse|-設定**識別碼**至*SaveResponse*<br />-設定**類型**至*SaveResponseType*<br />-設定**通訊模式**至*單向*<br />-設定**通訊方向**至*傳送*|  
  
 因為您要處理兩個要求和回應訊息使用這些連接埠，您必須建立兩個作業，每個連接埠，其中每個作業都會對應到一種訊息類型。 若要建立作業，以滑鼠右鍵按一下連接埠圖形，，然後選取**新作業**。 名稱為每個連接埠的第一個作業**ReadLOB**和每個連接埠做為第二項作業**UpdateLOB**。  
  
### <a name="using-correlation"></a>使用相互關聯  
 相互關聯是將內送訊息與適當協調流程執行個體相比對的程序。 在協調流程中您將會卸除這兩個要求訊息，一個用於每個多載。 您可使用相互關聯，以正確的協調流程關聯的要求訊息。 如需有關相互關聯的詳細資訊，請參閱[使用協調流程中的相互關聯](../../core/using-correlations-in-orchestrations.md)。  
  
##### <a name="to-use-correlations"></a>若要使用的相互關聯  
  
1.  從每個作業所產生的結構描述升級屬性。 例如，從 ReadLOB 作業結構描述; 升級 LOB_COLUMN 屬性從 UpdateLOB 作業結構描述中升級的篩選屬性。 若要升級的屬性，以滑鼠右鍵按一下結構描述檢視中的屬性，指向**升階**，然後選取**快速升級**。 這會加入您的 BizTalk 專案的 propertyschema.xsd 結構描述檔案。  
  
     如需升級屬性的資訊，請參閱[升級屬性](../../core/promoting-properties.md)。  
  
2.  從協調流程 檢視中，以滑鼠右鍵按一下**相互關聯類型**，然後選取**新相互關聯類型**。  
  
3.  **相互關聯屬性**對話方塊會列出您在步驟 1 中升級的屬性。 選取屬性，然後按一下**新增**。  
  
4.  按一下 **[確定]**。  
  
5.  若要建立其他升級屬性的相互關聯類型，重複這些步驟。  
  
6.  重新命名依據的作業相關聯的相互關聯類型。 您無法重新命名的相互關聯類型*CorrelationType_ReadLOB* （針對 ReadLOB 作業） 和*CorrelationType_UpdateLOB* （針對 UpdateLOB 作業）。  
  
7.  從協調流程 檢視中，以滑鼠右鍵按一下**相互關聯集**，然後選取**新相互關聯集**。  
  
8.  以滑鼠右鍵按一下新加入的相互關聯集，然後按一下**屬性**。 在**屬性** 窗格中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |相互關聯類型|*Operate_LOB。CorrelationType_ReadLOB*|  
    |識別碼|*Correlation_ReadLOB*|  
  
9. 加入另一個相互關聯集，並指定 [屬性] 窗格的下列屬性。  
  
    |使用|動作|  
    |--------------|----------------|  
    |相互關聯類型|*Operate_LOB。CorrelationType_UpdateLOB*|  
    |識別碼|*Correlation_UpdateLOB*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>指定訊息的動作圖形，並將它們連接至連接埠  
 下表指定屬性和其值，您應該設定以指定動作圖形的訊息，並將它們連結至連接埠。 圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**初始化相互關聯集**至*Correlation_ReadLOB*<br />-設定**訊息**至*要求*<br />-設定**作業**至*FileIn.ReadLOB.Request*|  
|SendMessage|-設定**訊息**至*要求*<br />-設定**作業**至*LOBPort.ReadLOB.Request*|  
|ReceiveResponse|-設定**訊息**至*回應*<br />-設定**作業**至*LOBPort.ReadLOB.Response*|  
|SendResponse|-設定**訊息**至*回應*<br />-設定**作業**至*SaveResponse.ReadLOB.Request*|  
|ReceiveMessage2|-設定**初始化相互關聯集**至*Correlation_UpdateLOB*<br />-設定**訊息**至*Request2*<br />-設定**作業**至*FileIn.UpdateLOB.Request*|  
|SendMessage2|-設定**訊息**至*Request2*<br />-設定**作業**至*LOBPort.UpdateLOB.Request*|  
|ReceiveResponse2|-設定**訊息**至*Response2*<br />-設定**作業**至*LOBPort.UpdateLOB.Response*|  
|SendResponse2|-設定**訊息**至*回應*<br />-設定**作業**至*SaveResponse.UpdateLOB.Request*|  
  
 您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包括：  
  
-   選取應用程式的主機。  
  
-   對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。 此協調流程中，您必須：  
  
    -   定義位置上的硬碟和對應的檔案連接埠，您將在此置放要求訊息，各一個 ReadLOB 和 UpdateLOB 作業。 BizTalk 協調流程會使用要求訊息，並將它傳送到 Oracle 資料庫。  
  
    -   定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除的回應訊息，一個用於每個作業，其中包含來自 Oracle 資料庫的回應。  
  
    -   定義實體 Wcf-custom 或 Wcf-oracledb 傳送埠將訊息傳送至 Oracle 資料庫。 您也必須在傳送埠中指定的動作。 如需如何建立 Wcf-custom 或 Wcf-oracledb 連接埠相關資訊，請參閱[手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。 因為 Wcf-oracledb 的 Wcf-custom 傳送埠將接收符合一個以上的結構描述的訊息及執行兩項作業，您必須設定這兩個作業的動態動作。 如需動作的詳細資訊，請參閱[設定 Oracle 資料庫的 SOAP 動作](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md)。 此協調流程，此動作應該如下所示設定：  
  
        ```  
        <BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
          <Operation Name="ReadLOB" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/ReadLOB" />  
          <Operation Name="UpdateLOB" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/UpdateLOB" />  
        </BtsActionMapping>  
        ```  
  
        > [!NOTE]
        >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。 您可以從 BizTalk Server 管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （適用於進行傳入呼叫時），以匯入此繫結檔案。 如需詳細資訊，請參閱[設定使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。  
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式執行的 Oracle 資料庫上的作業。 如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   Wcf-custom 傳送埠或 Wcf-oracledb 將訊息傳送至 Oracle 資料庫執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須卸除檔案的訊息接收位置的要求。 要求訊息的結構描述必須符合您先前產生的作業的結構描述。 請參閱[特殊 LOB 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md)如需有關叫用作業上使用的 LOB 資料類型的要求訊息結構描述[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
 協調流程會使用要求訊息，並將它們傳送到 Oracle 資料庫。 從 Oracle 資料庫的回應會儲存在其他的協調流程中定義的檔案位置。  
  
 此協調流程中，我們先卸除 UpdateLOB 作業，以便更新相片 （BLOB 資料類型資料行） 的客戶資料表的要求訊息。 要叫用更新 PHOTO 欄找出特定客戶的要求訊息是：  
  
```  
<UpdateLOB xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER">  
  <LOB_COLUMN>PHOTO</LOB_COLUMN>  
  <FILTER>Name='Mindy Martin'</FILTER>  
  <Stream>YWJjZA==</Stream>  
</UpdateLOB>  
```  
  
> [!NOTE]
>  篩選條件字串必須永遠提取一個相符的資料列否則 Oracle 資料庫配接器擲回 XmlReaderParsingException。 也針對值\<資料流\>項目必須是 base64Binary 型別。  
  
 UpdateLOB 作業的回應為：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<UpdateLOBResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER"></UpdateLOBResponse>  
```  
  
 我們現在要求訊息置放 ReadLOB 作業來讀取 UpdateLOB 作業已更新的資料。 要叫用 ReadLOB 上的作業將 PHOTO 資料找出特定客戶的要求訊息是：  
  
```  
<ReadLOB xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER">  
  <LOB_COLUMN>PHOTO</LOB_COLUMN>  
  <FILTER>NAME='Mindy Martin'</FILTER>  
</ReadLOB>  
```  
  
> [!NOTE]
>  篩選條件字串必須永遠提取一個相符的資料列。 如果有一個以上相符的資料列，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]只會傳回第一個 （符合） 的資料列的 LOB 資料行。  
  
 ReadLOB 作業的回應為：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<ReadLOBResponse mlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER">  
  <ReadLOBResult>YWJjZA==</ReadLOBResult>  
</ReadLOBResponse>  
```  
  
> [!NOTE]
>  ReadLOB 作業的回應可能會以 WSDL 對其驗證失敗。 您必須執行某些工作來驗證對 WSDL ReadLOB。 如需詳細資訊，請參閱[疑難排解操作問題](https://msdn.microsoft.com/library/dd787883.aspx)。  
  
## <a name="possible-exceptions"></a>可能的例外狀況  
 例外狀況的資訊可能會出現在執行包含使用 LOB 資料的資料表上的作業時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[例外狀況和錯誤處理](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。 一旦產生繫結檔案時，您可以匯入組態設定從檔案，因此您不需要建立傳送埠、 接收埠，等。 針對相同的協調流程。 如需繫結檔案的詳細資訊，請參閱[重複使用的 Oracle 資料庫配接器繫結](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)。  
  
## <a name="see-also"></a>請參閱  
[開發 BizTalk 應用程式的建置組塊，與 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)