---
title: 叫用函式，並使用 BizTalk Server 的 Oracle 資料庫中的記錄類型的程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccdc150e-055a-47df-af3e-64931946455d
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ee3a55907fe2528e411ca11447e19fce9e79958
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998751"
---
# <a name="invoke-functions-and-procedures-with-record-types-in-oracle-database-using-biztalk-server"></a>叫用函式和程序與使用 BizTalk Server 的 Oracle 資料庫中的記錄類型
Oracle 記錄類型用來代表階層式參數傳遞至 PL/SQL 函數與程序中的資訊。 [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現複雜的 XML 類型的記錄類型。 如需有關如何[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援記錄類型，請參閱[函式和程序的 Oracle 資料庫中的記錄類型的作業。](../../adapters-and-accelerators/adapter-oracle-database/operations-on-functions-and-procedures-with-record-types-in-oracle-database.md)。 記錄類型的 XML 結構的相關資訊，請參閱[記錄類型的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-record-types.md)。  
  
## <a name="how-to-invoke-functions-in-an-oracle-database"></a>如何叫用 Oracle 資料庫中的函式？  
 執行 Oracle 資料庫使用運算[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)。 叫用函式會傳回簡單和巢狀部署 Oracle 資料庫中的記錄類型，這些工作是：  
  
1. 建立 BizTalk 專案，並產生您想要叫用 Oracle 資料庫中的函式的結構描述。  
  
2. 建立傳送和接收訊息，從 Oracle 資料庫的 BizTalk 專案中的訊息。  
  
3. 建立協調流程叫用 Oracle 資料庫中的函式。  
  
4. 建置和部署 BizTalk 專案。  
  
5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 ，Func_RecordTypes，根據本主題也提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題中，以示範如何[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援叫用函式會傳回記錄型別我們將會叫用的參數：  
  
- GET_ACCOUNTADDRESS 函式會傳回簡單的記錄類型。  
  
- 傳回巢狀的記錄類型的 GET_ACCOUNTINFO 函式。  
  
  這些函式可建立執行 SQL 指令碼範例提供 ACCOUNT_PKG 的一部分。 若要深入了解的範例和 SQL 指令碼，請參閱[結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)。  
  
  因此，我們必須產生這兩個函式中，GET_ACCOUNTADDRESS 和 GET_ACCOUNTINFO，位於 SCOTT\Package\ACCOUNT_PKG 結構描述的結構描述。 請參閱[擷取 Oracle 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)如需有關如何產生結構描述。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 您必須連結產生的結構描述您的第一個步驟中的訊息從 BizTalk 專案的 [協調流程檢視] 視窗。  
  
 本主題中，您必須建立兩個要求-回應訊息集 — 一個要求-回應設定來叫用 GET_ACCOUNTADDRESS 函式，並接收回應，以叫用 GET_ACCOUNTINFO 函式，並接收回應，設定其他的要求-回應訊息。  
  
 執行下列步驟來建立訊息，並將它們連結至結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  
  
1.  如果它尚未開啟，請開啟 BizTalk 專案，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
2.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
3.  以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  
  
4.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**要求**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*Func_RecordTypes.OracleDBBindingSchema.GET_ACCOUNTINFO*，其中*Func_RecordTypes*名稱您BizTalk 專案。 *OracleDBBindingSchema*是 GET_ACCOUNTADDRESS 函式所產生的結構描述。|  
  
5.  重複上述步驟來建立三個的多個訊息。 在 **屬性**窗格中新的訊息，執行下列動作：  
  
    |若要設定識別項|若要設定訊息類型|  
    |-----------------------|-------------------------|  
    |回應|*Func_RecordTypes.OracleDBBindingSchema.GET_ACCOUNTINFOResponse*|  
    |要求 2|*Func_RecordTypes.OracleDBBindingSchema.GET_ACCOUNTADDRESS*|  
    |Response2|*Func_RecordTypes.OracleDBBindingSchema.GET_ACCOUNTADDRESSResponse*|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]的叫用函式會傳回簡單和複雜的記錄類型。 在此協調流程中，您已卸除兩個要求訊息：  
  
- 一個用於 GET_ACCOUNTADDRESS 函式會傳回簡單的記錄類型。  
  
- 一個用於 GET_ACCOUNTINFO 函式會傳回巢狀的記錄類型。  
  
  在接收位置會捨棄這些訊息。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]取用訊息，並將它們傳遞到 Oracle 資料庫中，透過 ODP。 從 Oracle 資料庫的回應會儲存到另一個位置。 因為協調流程會同時取得兩個要求，您需要在協調流程中包含 「 平行動作 」 圖形。 針對每個平行的動作，您必須包含傳送和接收圖形，將訊息傳送至 Oracle 資料庫，並接收回應，分別。 不過，您可以使用相同的連接埠來傳送和接收訊息的這兩項作業。 典型的協調流程，來同時執行兩項作業會包含：  
  
- 傳送和接收圖形以將訊息傳送至 Oracle 資料庫，並接收回應。  
  
- 單向接收埠以接收要求訊息傳送到 Oracle 資料庫。  
  
- 雙向傳送埠以傳送要求訊息到 Oracle 資料庫，並接收回應。  
  
- 若要從 Oracle 資料庫的回應傳送到資料夾的單向傳送埠。  
  
  範例協調流程如下所示：  
  
  ![在 Oracle 中使用記錄類型的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/6ee5e57b-48d5-435a-a16b-83bac878d0b7.gif "6ee5e57b-48d5-435a-a16b-83bac878d0b7")  
  
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
  
 因為您將會處理兩個要求和回應訊息使用這些連接埠，您必須建立每個連接埠，其中的每個作業都對應到一種訊息類型的兩個作業。 若要建立作業，以滑鼠右鍵按一下 連接埠圖形，然後選取**新的作業**。 名稱為每個連接埠的第一個作業**NestedRecType**和 每個連接埠做為第二項作業**SimpleRecType**。  
  
### <a name="using-correlations"></a>使用相互關聯  
 相互關聯是將內送訊息與適當協調流程執行個體相比對的程序。 在協調流程中您將會卸除這兩個要求訊息，一個用於每個多載。 使用相互關聯，您將建立關聯的要求訊息與正確的協調流程。 如需有關相互關聯的詳細資訊，請參閱[協調流程中使用的相互關聯](../../core/using-correlations-in-orchestrations.md)  
  
##### <a name="to-use-correlations"></a>若要使用的相互關聯  
  
1.  從每個函式所產生的結構描述升級屬性。 例如，升級的 GET_ACCOUNTADDRESS 函式; 結構描述的 CUSTNAME 屬性升級輔助屬性 GET_ACCOUNTINFO 函式的結構描述。 若要升級的屬性，以滑鼠右鍵按一下結構描述檢視中的屬性，指向**升階**，然後選取**快速升級**。 這會將 propertyschema.xsd 結構描述檔案加入至 BizTalk 專案中。  
  
     如需升級屬性的資訊，請參閱[升級屬性](../../core/promoting-properties.md)。  
  
2.  從協調流程 檢視中，以滑鼠右鍵按一下**相互關聯類型**，然後選取**新相互關聯類型**。  
  
3.  **相互關聯屬性**對話方塊會列出您在步驟 1 中升級的屬性。 選取的屬性，然後按一下**新增**。  
  
4.  按一下 [確定] 。  
  
5.  若要建立其他升級屬性的相互關聯類型，重複這些步驟。  
  
6.  重新命名要與其相關聯的屬性為基礎的相互關聯類型。 您可以重新命名的相互關聯型別*CorrelationType_CUSTNAME* （適用於 CUSTNAME 屬性中） 及*CorrelationType_AID* （適用於協助屬性）。  
  
7.  從協調流程 檢視中，以滑鼠右鍵按一下**相互關聯集**，然後選取**新相互關聯集**。  
  
8.  新加入的相互關聯集，以滑鼠右鍵按一下，然後按一下**屬性**。 在 [**屬性**] 窗格中，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |相互關聯類型|*Func_RecordTypes.CorrelationType_CUSTNAME*|  
    |識別碼|*Correlation_CUSTNAME*|  
  
9. 新增另一個相互關聯集，並指定下列屬性從**屬性**窗格。  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |相互關聯類型|*Func_RecordTypes.CorrelationType_AID*|  
    |識別碼|*Correlation_AID*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>為動作圖形指定訊息，並將其連接至連接埠  
 下表指定的屬性和指定動作圖形的訊息，並將它們連結至連接埠，您應該設定其值。 先前所述的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**初始化相互關聯集**到*Correlation_AID*<br />-設定**訊息**到*要求*<br />-設定**作業**到*FileIn.NestedRecType.Request*|  
|SendMessage|-設定**訊息**到*要求*<br />-設定**作業**到*LOBPort.NestedRecType.Request*|  
|ReceiveResponse|-設定**訊息**到*回應*<br />-設定**作業**到*LOBPort.NestedRecType.Response*|  
|SendResponse|-設定**訊息**到*回應*<br />-設定**作業**到*SaveResponse.NestedRecType.Request*|  
|ReceiveMessage2|-設定**初始化相互關聯集**到*Correlation_CUSTNAME*<br />-設定**訊息**到*要求 2*<br />-設定**作業**到*FileIn.SimpleRecType.Request*|  
|SendMessage2|-設定**訊息**到*要求 2*<br />-設定**作業**到*LOBPort.SimpleRecType.Request*|  
|ReceiveResponse2|-設定**訊息**到*Response2*<br />-設定**作業**到*LOBPort.SimpleRecType.Response*|  
|SendResponse2|-設定**訊息**到*回應*<br />-設定**作業**到*SaveResponse.SimpleRecType.Request*|  
  
 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程**在 BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應您在您在 BizTalk Server 管理主控台中的實體連接埠的協調流程中建立的連接埠。 此協調流程中，您必須：  
  
- 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息，其中每個多載程序。 BizTalk 協調流程將會取用的要求訊息，並將它傳送到 Oracle 資料庫。  
  
- 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程會放置回應訊息，其中每個函式，包含從 Oracle 資料庫回應的位置。  
  
  - 定義實體 Wcf-custom 或 Wcf-oracledb 傳送埠將訊息傳送至 Oracle 資料庫。 您也必須在傳送埠中指定的動作。 如需如何建立 Wcf-custom 或 Wcf-oracledb 連接埠的詳細資訊，請參閱[手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。 因為 Wcf-oracledb 的 Wcf-custom 傳送埠將和接收的訊息符合多個結構描述，會執行兩項作業，您必須設定兩個作業的動態動作。 如需有關動作的詳細資訊，請參閱[設定 Oracle 資料庫的 SOAP 動作](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md)。 此協調流程中，動作應該依下列方式設定：  
  
    ```  
    <BtsActionMapping>  
      <Operation Name="NestedRecType" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTINFO" />  
      <Operation Name="SimpleRecType" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTADDRESS" />  
    </BtsActionMapping>  
    ```  
  
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠設定動作的相關資訊的繫結檔案。 您可以從 BizTalk Server 管理主控台，來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫），以匯入此繫結檔案。 如需詳細資訊，請參閱 <<c0> [ 設定為使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。
  
## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式，來叫用 Oracle 資料庫資料表中的函式。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。  
  
 在這個階段，請確定：  
  
-   FILE 接收埠以接收要求訊息的協調流程正在執行。  
  
-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  
  
-   WCF 自訂] 或 [Wcf-oracledb 傳送埠將訊息傳送至 Oracle 資料庫正在執行。  
  
-   BizTalk 協調流程的作業正在執行。  
  
## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須卸除兩個檔案 （一個用於每個函式） 訊息接收位置的要求。 要求訊息的結構描述必須符合您稍早產生的函式的結構描述。 協調流程會使用要求訊息，並將它們傳送到 Oracle 資料庫。 從 Oracle 資料庫的回應會儲存在其他定義協調流程的一部分的檔案位置。  
  
 請參閱[函式和程序的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md)的詳細資訊的要求訊息結構描述叫用函式使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
 例如，要叫用 GET_ACCOUNINFO 函式的要求訊息是：  
  
```  
<GET_ACCOUNTINFO xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
  <AID>100000</AID>  
</GET_ACCOUNTINFO>  
```  
  
 同樣地，要叫用 GET_ACCOUNTADDRESS 函式的要求訊息是：  
  
```  
<GET_ACCOUNTADDRESS xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
  <CUSTNAME>Mindy Martin</CUSTNAME>  
</GET_ACCOUNTADDRESS>  
```  
  
 第一個要求訊息會叫用 GET_ACCOUNTINFO 函式會傳回巢狀的記錄型別。 叫用 GET_ACCOUNTINFO 函式的回應訊息是：  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<GET_ACCOUNTINFOResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
  <GET_ACCOUNTINFOResult>  
    <ACCT xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTINFO">  
      <ACCTID>100000</ACCTID>   
      <NAME>Kim Ralls</NAME>   
      <BALANCE>10000</BALANCE>   
    </ACCT>  
    <ADDRESS xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTINFO">  
      <STREET>1234 Main St.</STREET>   
      <CITY>Seattle</CITY>   
      <STATE>WA</STATE>   
    </ADDRESS>  
  </GET_ACCOUNTINFOResult>  
</GET_ACCOUNTINFOResponse>  
```  
  
 第二個要求訊息會叫用 GET_ACCOUNTADDRESS 函式會傳回簡單記錄型別。 叫用 GET_ACCOUNTADDRESS 函式的回應訊息是：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<GET_ACCOUNTADDRESSResponse mlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
  <GET_ACCOUNTADDRESSResult>  
    <ID xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTADDRESS">100004</ID>  
    <NAME xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTADDRESS">Mindy Martin</NAME>  
    <STREET xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTADDRESS">6789 Cherry St.</STREET>  
    <CITY xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTADDRESS">New York</CITY>  
    <STATE xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTADDRESS">NY</STATE>  
  </GET_ACCOUNTADDRESSResult>  
</GET_ACCOUNTADDRESSResponse>  
```  
  
## <a name="possible-exceptions"></a>可能的例外狀況  
 如需有關例外狀況資訊可能會遇到叫用函式或程序使用時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 例外狀況和錯誤處理 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 之後產生的繫結檔案時，您可以匯入的組態設定從檔案，讓您不需要建立傳送埠、 接收連接埠、 相同的協調流程等。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用的 Oracle 資料庫配接器繫結](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式的建置組塊，與 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)