---
title: 具有 Oracle 資料庫中的大型物件資料類型的資料表執行作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- operations, performing on tables
- operations, performing on LOB data
ms.assetid: 74276b85-daf1-4d0f-92f9-46d5c27a95a6
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ea86bd08a926c3274b16b26b093380396f17887
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966983"
---
# <a name="run-operations-on-tables-with-large-object-data-types-in-oracle-database"></a>具有 Oracle 資料庫中的大型物件資料類型的資料表執行作業
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]提供 Oracle 的大型物件 (LOB) 資料類型的支援：  

- 二進位大型物件 (BLOB)  

- 字元大型物件 (CLOB)  

- 國家字元大型物件 (NCLOB)  

- 二進位檔案 (BFILE)。 如需詳細資訊，請參閱 <<c0> [ 正在執行的作業，對具有 BFILE 資料類型，使用 BizTalk Server 的 Oracle 資料庫中的資料表上](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-bfile-data-types-in-oracle-db-using-biztalk.md)。  

  [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]的做法是呈現 ReadLOB 和 UpdateLOB 作業針對包含 LOB 資料行的資料表。 如需這些作業的詳細資訊請參閱 <<c0> [ 上的資料表和檢視表，包含 LOB 資料 Oracle 資料庫中的作業](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-and-views-that-contain-lob-data-in-oracle-database.md)。 如需叫用這些作業的 SOAP 訊息結構的詳細資訊，請參閱[特殊 LOB 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md)。  

> [!NOTE]
>  使用時[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，ReadLOB 作業不支援從 Oracle 資料庫的資料流 LOB 類型資料。 將資料從 Oracle 資料庫使用的串流 LOB[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]您應該改為使用選取的作業。 如需串流的詳細資訊，請參閱 < [Oracle 資料庫中的 LOB 資料類型的資料流支援](../../adapters-and-accelerators/adapter-oracle-database/streaming-support-for-lob-data-types-in-oracle-database.md)。 此外，從 Oracle 資料庫 ReadLOB 作業回應將會失敗 WSDL 驗證。 如需如何以因應措施失敗的指示，請參閱[疑難排解操作問題](https://msdn.microsoft.com/library/dd787883.aspx)。  

## <a name="how-to-perform-operations-on-lob-data"></a>如何執行 LOB 資料的作業？  
 執行 Oracle 資料庫使用運算[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)。 要叫用 Oracle 資料庫中資料表上的 ReadLOB 和 UpdateLOB 作業，這些工作如下：  

1. 建立 BizTalk 專案，並針對 ReadLOB 和 UpdateLOB 作業產生結構描述。  

2. 建立傳送和接收訊息，從 Oracle 資料庫的 BizTalk 專案中的訊息。 您必須建立傳送要求和接收作業的回應訊息。  

3. 建立協調流程叫用 ReadLOB 和 UpdateLOB 作業。  

4. 建置和部署 BizTalk 專案。  

5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  

6. 啟動 BizTalk 應用程式。  

   本主題提供執行這些工作的指示。  

## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 ，Operate_LOB，根據本主題也提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  

## <a name="generating-schema"></a>產生結構描述  
 在本主題中，示範如何執行 ReadLOB 和 UpdateLOB 作業，我們會產生針對 CUSTOMER 資料表中的 Oracle 資料庫中的 SCOTT 結構描述下顯示這些作業的中繼資料。 SCOTT 結構描述下建立這份資料表，藉由執行 SQL 指令碼提供範例。 若要深入了解範例，請參閱[結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)。  

## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 您必須連結產生的結構描述您的第一個步驟中的訊息從 BizTalk 專案的 [協調流程檢視] 視窗。  

 本主題中，您必須建立兩個要求-回應訊息集 — 一個要求-回應為 ReadLOB 作業，並針對 UpdateLOB 作業設定第二個要求回應。  

 執行下列步驟來建立訊息，並將它們連結至結構描述。  

#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  

1. 如果它尚未開啟，請開啟 BizTalk 專案，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  

2. 在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  

3. 以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  

4. 在 [**屬性**] 窗格**Message_1**，執行下列動作：  


   |   使用   |                                                                                                                                       以進行此動作                                                                                                                                       |
   |--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |  識別碼  |                                                                                                                                   型別**要求**。                                                                                                                                    |
   | 訊息類型 | 從下拉式清單中，依序展開**結構描述**，然後選取*Operate_LOB。OracleDBBindingSchema.ReadLOB*<em>，</em>何處*Operate_LOB*是 BizTalk 專案的名稱。 *OracleDBBindingSchema*是 CUSTOMER 資料表的 ReadLOB 和 UpdateLOB 作業產生的結構描述。 |


5. 重複上述步驟來建立三個的多個訊息。 在 **屬性**窗格中新的訊息，執行下列動作：  

   |若要設定識別項|若要設定訊息類型|  
   |-----------------------|-------------------------|  
   |回應|*Operate_LOB。OracleDBBindingSchema.ReadLOBResponse*|  
   |要求 2|*Operate_LOB。OracleDBBindingSchema.UpdateLOB*|  
   |Response2|*Operate_LOB。OracleDBBindingSchema.UpdateLOBResponse*|  

## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]叫用 ReadLOB 和 UpdateLOB 資料表上的作業。 在此協調流程中，您已卸除兩個要求訊息，一個用於 ReadLOB 作業，另一個則用於 UpdateLOB 作業。 在接收位置會捨棄這些訊息。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]取用訊息，並將它們傳遞到 Oracle 資料庫中，透過 ODP。 從 Oracle 資料庫的回應會儲存到另一個位置。  

 因為協調流程會同時取得兩個要求，您需要在協調流程中包含 「 平行動作 」 圖形。 針對每個平行的動作，您必須包含傳送和接收圖形，將訊息傳送至 Oracle 資料庫，並接收回應。 不過，您可以使用相同的連接埠來傳送和接收訊息的這兩項作業。 典型的協調流程，來同時執行的 ReadLOB 和 UpdateLOB 作業會包含：  

- 傳送和接收圖形以將訊息傳送至 Oracle 資料庫，並接收回應。  

- 單向接收埠以接收要求訊息傳送到 Oracle 資料庫。  

- 雙向傳送埠以傳送要求訊息到 Oracle 資料庫，並接收回應。  

- 若要從 Oracle 資料庫的回應傳送到資料夾的單向傳送埠。  

  範例協調流程如下所示：  

  ![用於讀取及更新 LOB 資料的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/6523b5e4-3689-433a-8287-eebc36f10442.gif "6523b5e4-3689-433a-8287-eebc36f10442")  

### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息 圖形中指定下列屬性。 剛剛提到的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。 下表列出您必須包含其中一個平行動作圖形。  

|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-設定**名稱**到*ReceiveMessage*<br />-設定**啟用**到 *，則為 True*|  
|SendMessage|Send|-設定**名稱**到*SendMessage*|  
|ReceiveResponse|Receive|-設定**名稱**到*ReceiveResponse*<br />-設定**啟用**到*False*|  
|SendResponse|Send|-設定**名稱**到*SendResponse*|  

 下表列出您必須包含平行動作圖形。  

|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveMessage2|Receive|-設定**名稱**到*ReceiveMessage2*<br />-設定**啟用**到 *，則為 True*|  
|SendMessage2|Send|-設定**名稱**到*SendMessage2*|  
|ReceiveResponse2|Receive|-設定**名稱**到*ReceiveResponse2*<br />-設定**啟用**到*False*|  
|SendResponse2|Send|-設定**名稱**到*SendResponse2*|  

### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠中指定下列屬性。 協調流程中所示，連接埠資料行中所列的名稱會是連接埠的名稱。  

|通訊埠|屬性|  
|----------|----------------|  
|FileIn|-設定**識別碼**到*FileIn*<br />-設定**型別**到*FileInType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*接收*|  
|LOBPort|-設定**識別碼**到*LOBPort*<br />-設定**型別**到*LOBPortType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*|  
|SaveResponse|-設定**識別碼**到*SaveResponse*<br />-設定**型別**到*SaveResponseType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*傳送*|  

 因為您將會處理兩個要求和回應訊息使用這些連接埠，您必須建立每個連接埠，其中的每個作業都對應到一種訊息類型的兩個作業。 若要建立作業，以滑鼠右鍵按一下 連接埠圖形，然後按**新的作業**。 名稱為每個連接埠的第一個作業**ReadLOB**和 每個連接埠做為第二項作業**UpdateLOB**。  

### <a name="using-correlation"></a>使用相互關聯  
 相互關聯是將內送訊息與適當協調流程執行個體相比對的程序。 在協調流程中您將會卸除這兩個要求訊息，一個用於每個多載。 使用相互關聯，您將建立關聯的要求訊息與正確的協調流程。 如需有關相互關聯的詳細資訊，請參閱 <<c0> [ 協調流程中使用的相互關聯](../../core/using-correlations-in-orchestrations.md)。  

##### <a name="to-use-correlations"></a>若要使用的相互關聯  

1.  從每個作業所產生的結構描述升級屬性。 例如，從 ReadLOB 作業結構描述; 升級 LOB_COLUMN 屬性從 UpdateLOB 作業結構描述中升級的篩選屬性。 若要升級的屬性，以滑鼠右鍵按一下結構描述檢視中的屬性，指向**升階**，然後選取**快速升級**。 這會將 propertyschema.xsd 結構描述檔案加入至 BizTalk 專案中。  

     如需升級屬性的資訊，請參閱[升級屬性](../../core/promoting-properties.md)。  

2.  從 [協調流程] 檢視中，以滑鼠右鍵按一下**相互關聯類型**，然後選取**新相互關聯類型**。  

3.  **相互關聯屬性**對話方塊會列出您在步驟 1 中升級的屬性。 選取的屬性，然後按一下**新增**。  

4.  按一下 [確定] 。  

5.  若要建立其他升級屬性的相互關聯類型，重複這些步驟。  

6.  重新命名相關聯的作業為基礎的相互關聯類型。 您可以重新命名的相互關聯型別*CorrelationType_ReadLOB* （適用於 ReadLOB 作業） 和*CorrelationType_UpdateLOB* （適用於 UpdateLOB 作業）。  

7.  從協調流程 檢視中，以滑鼠右鍵按一下**相互關聯集**，然後選取**新相互關聯集**。  

8.  新加入的相互關聯集，以滑鼠右鍵按一下，然後按一下**屬性**。 在 [**屬性**] 窗格中，執行下列動作：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |相互關聯類型|*Operate_LOB。CorrelationType_ReadLOB*|  
    |識別碼|*Correlation_ReadLOB*|  

9. 新增另一個相互關聯集，並指定下列屬性從 [屬性] 窗格。  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |相互關聯類型|*Operate_LOB。CorrelationType_UpdateLOB*|  
    |識別碼|*Correlation_UpdateLOB*|  

## <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>為動作圖形指定訊息，並將其連接至連接埠  
 下表指定的屬性和指定動作圖形的訊息，並將它們連結至連接埠，您應該設定其值。 先前所述的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  

|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**初始化相互關聯集**到*Correlation_ReadLOB*<br />-設定**訊息**到*要求*<br />-設定**作業**到*FileIn.ReadLOB.Request*|  
|SendMessage|-設定**訊息**到*要求*<br />-設定**作業**到*LOBPort.ReadLOB.Request*|  
|ReceiveResponse|-設定**訊息**到*回應*<br />-設定**作業**到*LOBPort.ReadLOB.Response*|  
|SendResponse|-設定**訊息**到*回應*<br />-設定**作業**到*SaveResponse.ReadLOB.Request*|  
|ReceiveMessage2|-設定**初始化相互關聯集**到*Correlation_UpdateLOB*<br />-設定**訊息**到*要求 2*<br />-設定**作業**到*FileIn.UpdateLOB.Request*|  
|SendMessage2|-設定**訊息**到*要求 2*<br />-設定**作業**到*LOBPort.UpdateLOB.Request*|  
|ReceiveResponse2|-設定**訊息**到*Response2*<br />-設定**作業**到*LOBPort.UpdateLOB.Response*|  
|SendResponse2|-設定**訊息**到*回應*<br />-設定**作業**到*SaveResponse.UpdateLOB.Request*|  

 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  

 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  

## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程**在 BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。

 設定應用程式包含：  

- 選取應用程式主機。  

- 對應您在您在 BizTalk Server 管理主控台中的實體連接埠的協調流程中建立的連接埠。 此協調流程中，您必須：  

  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息，各一個 ReadLOB 和 UpdateLOB 作業。 BizTalk 協調流程將會取用的要求訊息，並將它傳送到 Oracle 資料庫。  

  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程會放置回應訊息，一個用於每個作業，包含從 Oracle 資料庫回應的位置。  

  - 定義實體 Wcf-custom 或 Wcf-oracledb 傳送埠將訊息傳送至 Oracle 資料庫。 您也必須在傳送埠中指定的動作。 如需如何建立 Wcf-custom 或 Wcf-oracledb 連接埠的詳細資訊，請參閱[手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。 因為 Wcf-oracledb 的 Wcf-custom 傳送埠將和接收的訊息符合多個結構描述，會執行兩項作業，您必須設定兩個作業的動態動作。 如需有關動作的詳細資訊，請參閱[設定 Oracle 資料庫的 SOAP 動作](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md)。 此協調流程中，動作應該依下列方式設定：  

    ```  
    <BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
      <Operation Name="ReadLOB" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/ReadLOB" />  
      <Operation Name="UpdateLOB" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/UpdateLOB" />  
    </BtsActionMapping>  
    ```  

    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠設定動作的相關資訊的繫結檔案。 您可以從 BizTalk Server 管理主控台，來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫），以匯入此繫結檔案。 如需詳細資訊，請參閱 <<c0> [ 設定為使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。  

## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式執行的 Oracle 資料庫上作業。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  

 在這個階段，請確定：  

-   FILE 接收埠以接收要求訊息的協調流程正在執行。  

-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  

-   Wcf-custom 傳送埠或 Wcf-oracledb 將訊息傳送至 Oracle 資料庫執行。  

-   BizTalk 協調流程的作業正在執行。  

## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須卸除檔案的訊息接收位置的要求。 要求訊息的結構描述必須符合您稍早產生的作業的結構描述。 請參閱[特殊 LOB 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md)如需針對 LOB 資料類型使用叫用作業的要求訊息結構描述[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  

 協調流程會使用要求訊息，並將它們傳送到 Oracle 資料庫。 從 Oracle 資料庫的回應會儲存在其他定義協調流程的一部分的檔案位置。  

 此協調流程中，我們先卸除 UpdateLOB 作業更新 PHOTO 資料行 （的 BLOB 資料類型） 的 CUSTOMER 資料表中的要求訊息。 要叫用更新 PHOTO 資料行特定客戶的要求訊息是：  

```  
<UpdateLOB xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER">  
  <LOB_COLUMN>PHOTO</LOB_COLUMN>  
  <FILTER>Name='Mindy Martin'</FILTER>  
  <Stream>YWJjZA==</Stream>  
</UpdateLOB>  
```  

> [!NOTE]
>  篩選條件字串必須永遠擷取一個相符的資料列否則 XmlReaderParsingException 的 Oracle 資料庫配接器會擲回。 也為數值\<Stream\>項目必須是 base64Binary 型別。  

 UpdateLOB 作業的回應是：  

```  
<?xml version="1.0" encoding="utf-8"?>  
<UpdateLOBResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER"></UpdateLOBResponse>  
```  

 我們現在卸除 ReadLOB 作業讀取 UpdateLOB 作業更新資料的要求訊息。 要叫用 ReadLOB 作業 PHOTO 資料行上的特定客戶的要求訊息是：  

```  
<ReadLOB xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER">  
  <LOB_COLUMN>PHOTO</LOB_COLUMN>  
  <FILTER>NAME='Mindy Martin'</FILTER>  
</ReadLOB>  
```  

> [!NOTE]
>  篩選條件字串必須一律會擷取一個相符的資料列。 如果有多個相符的資料列，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]只會傳回第一個 （符合） 的資料列的 LOB 資料行。  

 ReadLOB 作業的回應是：  

```  
<?xml version="1.0" encoding="utf-8"?>  
<ReadLOBResponse mlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER">  
  <ReadLOBResult>YWJjZA==</ReadLOBResult>  
</ReadLOBResponse>  
```  

> [!NOTE]
>  ReadLOB 作業的回應可能無法驗證的 WSDL。 您必須執行某些工作來驗證對 WSDL ReadLOB。 如需詳細資訊，請參閱[疑難排解操作問題](https://msdn.microsoft.com/library/dd787883.aspx)。  

## <a name="possible-exceptions"></a>可能的例外狀況  
 可能會遇到執行包含 LOB 資料使用的資料表上的作業時的例外狀況的相關資訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 例外狀況和錯誤處理](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md)。  

## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 之後產生的繫結檔案時，您可以匯入的組態設定從檔案，讓您不需要建立傳送埠、 接收連接埠、 相同的協調流程等。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用的 Oracle 資料庫配接器繫結](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)。  

## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式的建置組塊，與 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)