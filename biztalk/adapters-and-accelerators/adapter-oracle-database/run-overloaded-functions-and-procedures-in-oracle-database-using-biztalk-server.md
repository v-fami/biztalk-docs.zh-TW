---
title: 叫用多載函式，並使用 BizTalk Server 的 Oracle 資料庫中的程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- overloaded functions and procedures, invoking by using BizTalk Server
ms.assetid: a3d76361-6b0c-415a-b4f9-31939abfdc36
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2cbe1db96bf6b1c65c77c67c639a3f6ac65a43d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005343"
---
# <a name="invoke-overloaded-functions-and-procedures-in-oracle-database-using-biztalk-server"></a>叫用多載函式，並使用 BizTalk Server 的 Oracle 資料庫中的程序
預存程序和函式可以多載 Oracle 資料庫中。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援多載的函式和程序變更作業的目標命名空間。 例如，兩個多載程序的訊息結構看起來像：  
  
```  
Stored Procedure Overload 1:  
<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/overload1">    
  <[PRM1_NAME]>value1</[PRM1_NAME]>  
  <[PRM2_NAME]>value1</[PRM2_NAME]>  
  …  
</[SP_NAME]>  
  
Stored Procedure Overload 2:  
<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/overload2">    
  <[PRM1_NAME]>value1</I_[PRM1_NAME]>  
  <[PRM2_NAME]>value1</I_[PRM2_NAME]>  
  …  
</[SP_NAME]>  
```  
  
 SOAP 訊息結構和 SOAP 動作叫用所需的多載函式或程序類似於叫用函式和程序，如底下所述[函式和程序的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md)。  
  
 叫用多載的程序是類似於叫用其他函式，如中所述[叫用函式和 Oracle 資料庫使用 BizTalk Server 中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md)。 不過，若要區別多載函式，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]將唯一的字串附加至的節點識別碼，它會呈現多載的成品的命名空間。 此字串會是第一個多載而言，「 overload2""overload1 」 下, 一個多載，依此類推。  
  
## <a name="how-to-invoke-overloaded-functions-and-procedures"></a>如何叫用多載函式和程序？  
 執行 Oracle 資料庫使用運算[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及中所述的程序性工作[開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)。 要叫用 Oracle 資料庫中的函式，這些工作如下：  
  
1. 建立 BizTalk 專案，並產生您想要叫用 Oracle 資料庫中的多載函式的結構描述。  
  
2. 建立傳送和接收訊息，從 Oracle 資料庫的 BizTalk 專案中的訊息。 您必須建立每個多載的訊息。  
  
3. 建立協調流程叫用 Oracle 資料庫中的多載函式。  
  
4. 建置和部署 BizTalk 專案。  
  
5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  
  
6. 啟動 BizTalk 應用程式。  
  
   本主題提供執行這些工作的指示。  
  
## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 ，InvokeOverloadedProc，根據本主題也提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
## <a name="generating-schema"></a>產生結構描述  
 本主題中，示範如何叫用多載函式或程序中，我們會叫用 SCOTT\Package\ACCOUNT_PKG 結構描述在 GET_ACCOUNT 程序。 此封裝在執行 SQL 指令碼範例提供 SCOTT 結構描述下建立。 這是一個多載程序位置：  
  
- 其中一個多載會採用做為 IN 參數的帳戶識別碼，並做為 OUT 參數，則會傳回帳戶 %資料列型別。  
  
- 第二個多載會使用帳戶名稱做為 IN 參數，並做為 OUT 參數，則會傳回帳戶 %資料列型別。  
  
  若要深入了解的範例和 SQL 指令碼，請參閱[結構描述範例](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md)。  
  
  要叫用多載的函式，我們會產生兩個多載程序，GET_ACCOUNT.1 和 GET_ACCOUNT.2 的結構描述。 請參閱[擷取 Oracle 資料庫作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)如需有關如何產生結構描述。  
  
## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 您必須連結產生的結構描述您的第一個步驟中的訊息從 BizTalk 專案的 [協調流程檢視] 視窗。  
  
 本主題中，您必須建立兩個要求-回應訊息集 — 一個要求-回應設定的第一個多載的程序和第二個要求-回應設定的第二個多載程序。  
  
 執行下列步驟來建立訊息，並將它們連結至結構描述。  
  
#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  
  
1.  如果它尚未開啟，請開啟 BizTalk 專案，[協調流程檢視] 視窗。 若要這樣做，請按一下**檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  
  
2.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
3.  以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。  
  
4.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**要求**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*InvokeOverloadedProc.OracleDBBindingSchema.GET_ACCOUNT*，其中*InvokeOverloadedProc*的名稱您的 BizTalk 專案。 *OracleDBBindingSchema*是 GET_ACCOUNT 程序所產生的結構描述。|  
  
5.  重複上述步驟來建立三個的多個訊息。 在 **屬性**窗格中新的訊息，執行下列動作：  
  
    |若要設定識別項|若要設定訊息類型|  
    |-----------------------|-------------------------|  
    |回應|*InvokeOverloadedProc.OracleDBBindingSchema.GET_ACCOUNTResponse*|  
    |要求 2|*InvokeOverloadedProc.OracleDBBindingSchema1.GET_ACCOUNT*|  
    |Response2|*InvokeOverloadedProc.OracleDBBindingSchema1.GET_ACCOUNTResponse*|  
  
## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]叫用 Oracle 資料庫中的多載程序。 在此協調流程中，卸除兩個要求訊息，各自對應到每個多載的程序，在定義接收位置。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]取用訊息，並將它們傳遞到 Oracle 資料庫中，透過 ODP。 從 Oracle 資料庫的回應會儲存到另一個位置。  
  
 因為協調流程會同時取得兩個要求，您需要在協調流程中包含 「 平行動作 」 圖形。 針對每個平行的動作，您必須包含傳送和接收圖形，將訊息傳送至 Oracle 資料庫，並接收回應。 不過，您可以使用相同的連接埠來傳送和接收訊息的這兩項作業。 典型的協調流程叫用的多載程序時，同時會包含：  
  
- 傳送和接收圖形以將訊息傳送至 Oracle 資料庫，並接收回應。  
  
- 單向接收埠以接收要求訊息傳送到 Oracle 資料庫。  
  
- 雙向傳送埠以傳送要求訊息到 Oracle 資料庫，並接收回應。  
  
- 若要從 Oracle 資料庫的回應傳送到資料夾的單向傳送埠。  
  
  範例協調流程叫用 GET_ACCOUNT 程序的第一個和第二個多載，如下所示：  
  
  ![多載套件的協調流程叫用](../../adapters-and-accelerators/adapter-oracle-database/media/f8e4ad6f-9140-43b1-b931-28c9ba11cc8e.gif "f8e4ad6f-9140-43b1-b931-28c9ba11cc8e")  
  
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
 請確定您針對每個邏輯連接埠，指定下列屬性。 協調流程中所示，連接埠資料行中所列的名稱會是連接埠的名稱。  
  
|通訊埠|屬性|  
|----------|----------------|  
|FileIn|-設定**識別碼**到*FileIn*<br />-設定**型別**到*FileInType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*接收*|  
|LOBPort|-設定**識別碼**到*LOBPort*<br />-設定**型別**到*LOBPortType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*|  
|SaveResponse|-設定**識別碼**到*SaveResponse*<br />-設定**型別**到*SaveResponseType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*傳送*|  
  
 因為您將會處理兩個要求和回應訊息使用這些連接埠，您必須建立每個連接埠，其中的每個作業都對應到一種訊息類型的兩個作業。 若要建立作業，以滑鼠右鍵按一下 連接埠圖形，然後按**新的作業**。 名稱為每個連接埠的第一個作業**Overload1**和 每個連接埠做為第二項作業**Overload2**。  
  
### <a name="using-correlation"></a>使用相互關聯  
 相互關聯是將內送訊息與適當協調流程執行個體相比對的程序。 在協調流程中您將會卸除這兩個要求訊息，一個用於每個多載。 使用相互關聯，您將建立關聯的要求訊息與正確的協調流程。 如需有關相互關聯的詳細資訊，請參閱 <<c0> [ 協調流程中使用的相互關聯](../../core/using-correlations-in-orchestrations.md)。  
  
##### <a name="to-use-correlations"></a>若要使用的相互關聯  
  
1.  從每個多載函式所產生的結構描述升級屬性。 例如，從第一個多載; 結構描述升級輔助工具屬性第二個多載的結構描述升級 ANAME 屬性。 若要升級的屬性，以滑鼠右鍵按一下結構描述檢視中的屬性，指向**升階**，然後選取**快速升級**。 這會將 propertyschema.xsd 結構描述檔案加入至 BizTalk 專案中。  
  
     如需升級屬性的資訊，請參閱[升級屬性](../../core/promoting-properties.md)。  
  
2.  從協調流程 檢視中，以滑鼠右鍵按一下**相互關聯類型**，然後選取**新相互關聯類型**。  
  
3.  **相互關聯屬性**對話方塊會列出您在步驟 1 中已升級的屬性。 選取的屬性，然後按一下**新增**。  
  
4.  按一下 [確定] 。  
  
5.  若要建立其他升級屬性的相互關聯類型，重複這些步驟。  
  
6.  重新命名要與其相關聯的屬性為基礎的相互關聯類型。 您可以重新命名的相互關聯型別*CorrelationType_AID* （適用於 協助 屬性中） 及*CorrelationType_ANAME* （適用於 ANAME 屬性中）。  
  
7.  從協調流程 檢視中，以滑鼠右鍵按一下**相互關聯集**，然後選取**新相互關聯集**。  
  
8.  新加入的相互關聯集，以滑鼠右鍵按一下，然後按一下**屬性**。 在 [屬性] 窗格中執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |相互關聯類型|*InvokeOverloadedProc.CorrelationType_AID*|  
    |識別碼|*Correlation_AID*|  
  
9. 新增另一個相互關聯集，並指定下列屬性從 [屬性] 窗格。  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |相互關聯類型|*InvokeOverloadedProc.CorrelationType_ANAME*|  
    |識別碼|*Correlation_ANAME*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>為動作圖形指定訊息，並將其連接至連接埠  
 下表指定的屬性和屬性來指定動作圖形的訊息，以及連結至連接埠的訊息，您應該設定的值。 先前所述的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。  
  
|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveMessage|-設定**初始化相互關聯集**到*Correlation_AID*<br />-設定**訊息**到*要求*<br />-設定**作業**到*FileIn.Overload1.Request*|  
|SendMessage|-設定**訊息**到*要求*<br />-設定**作業**到*LOBPort.Overload1.Request*|  
|ReceiveResponse|-設定**訊息**到*回應*<br />-設定**作業**到*LOBPort.Overload1.Response*|  
|SendResponse|-設定**訊息**到*回應*<br />-設定**作業**到*SaveResponse.Overload1.Request*|  
|ReceiveMessage2|-設定**初始化相互關聯集**到*Correlation_ANAME*<br />-設定**訊息**到*要求 2*<br />-設定**作業**到*FileIn.Overload2.Request*|  
|SendMessage2|-設定**訊息**到*要求 2*<br />-設定**作業**到*LOBPort.Overload2.Request*|  
|ReceiveResponse2|-設定**訊息**到*Response2*<br />-設定**作業**到*LOBPort.Overload2.Response*|  
|SendResponse2|-設定**訊息**到*Response2*<br />-設定**作業**到*SaveResponse.Overload2.Request*|  
  
 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  
  
 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。  
  
## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程**在 BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。
  
 設定應用程式包含：  
  
- 選取應用程式主機。  
  
- 對應您在您在 BizTalk Server 管理主控台中的實體連接埠的協調流程中建立的連接埠。 此協調流程中，您必須：  
  
  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息，其中每個多載程序。 BizTalk 協調流程將會取用的要求訊息，並將它傳送到 Oracle 資料庫。  
  
  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程會放置回應訊息，其中每個多載程序，包含從 Oracle 資料庫回應的位置。  
  
  - 定義實體 Wcf-custom 或 Wcf-oracledb 傳送埠將訊息傳送至 Oracle 資料庫。 您也必須在傳送埠中指定的動作。 如需如何建立 Wcf-custom 或 Wcf-oracledb 連接埠的詳細資訊，請參閱[手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。 因為 Wcf-oracledb 的 Wcf-custom 傳送埠將和接收的訊息符合多個結構描述，會執行兩項作業，您必須設定兩個作業的動態動作。 如需有關動作的詳細資訊，請參閱[設定 Oracle 資料庫的 SOAP 動作](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md)。 此協調流程中，動作應該依下列方式設定：  
  
    ```  
    <BtsActionMapping>  
      <Operation Name="Overload1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT/overload1" />  
      <Operation Name="Overload2" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT/overload2" />  
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
 執行應用程式之後，您必須卸除兩個檔案 （一個用於每個多載程序） 訊息接收位置的要求。 要求訊息的結構描述必須符合您稍早產生的程序的結構描述。 請參閱[函式和程序的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md)的詳細資訊的要求訊息結構描述叫用函式使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
 例如，要叫用 GET_ACCOUNT 程序的第一個多載的要求訊息是：  
  
```  
<GET_ACCOUNT xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT/overload1">  
  <AID>100001</AID>  
</GET_ACCOUNT>  
```  
  
 同樣地，要叫用 GET_ACCOUNT 程序的第二個多載的要求訊息是：  
  
```  
<GET_ACCOUNT xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT/overload2">  
  <ANAME>Mindy Martin</ANAME>  
</GET_ACCOUNT>  
```  
  
 第一個要求訊息會叫用來擷取記錄的帳戶 id 等於 100020 GET_ACCOUNT 程序。 第二個要求訊息會叫用 GET_ACCOUNT 程序，來擷取帳戶名稱與"John Smith"的記錄。  
  
 協調流程會使用要求訊息，並將它們傳送到 Oracle 資料庫。 從 Oracle 資料庫的回應會儲存在其他定義協調流程的一部分的檔案位置。 例如，叫用第一個多載程序的回應是：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<GET_ACCOUNTResponse mlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT/overload1">  
 <ACCT>  
  <ACCTID>100001</ACCTID>  
  <NAME>Ty Carlson</NAME>  
  <BALANCE>9000</BALANCE>  
 </ACCT>  
</GET_ACCOUNTResponse>  
```  
  
## <a name="possible-exceptions"></a>可能的例外狀況  
 可能會遇到時叫用負載的封裝使用的例外狀況的相關資訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 例外狀況和錯誤處理](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md)。  
  
## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 之後產生的繫結檔案時，您可以匯入的組態設定從檔案，讓您不需要建立傳送埠、 接收連接埠、 相同的協調流程等。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用的 Oracle 資料庫配接器繫結](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式的建置組塊，與 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)