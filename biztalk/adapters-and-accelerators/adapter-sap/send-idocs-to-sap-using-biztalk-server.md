---
title: 傳送 Idoc 至 SAP 使用 BizTalk Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDOCs, sample for sending
- IDOCs, sending to SAP using BizTalk Server
- IDOCs, business scenarios for sending
ms.assetid: 92042623-ffbf-472f-9515-e9a77eb320fb
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ca8464af7002fe7863246dc440a4da27ee23e1f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970319"
---
# <a name="send-idocs-to-sap-using-biztalk-server"></a>傳送 Idoc 至 SAP 使用 BizTalk Server
所有 SAP IDOC 呼叫在內部會被都視為 tRFC 呼叫配接器做為 tRFC 用戶端，並呼叫 RFC，SAP 傳送 IDOC 中。 此章節提供的資訊使用傳送 Idoc 至 SAP[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現傳送 Idoc 的兩個不同的作業：  

- **傳送**作業可讓配接器用戶端傳送 Idoc 具有強型別結構描述。  

- **SendIdoc**作業可讓配接器用戶端傳送 Idoc 具有弱式型別結構描述。 使用這種情況，配接器用戶端可以傳送一般檔案 Idoc 至 SAP 系統。 整個的一般檔案 IDOC 是 SendIdoc XML 訊息中的節點值。  

  如需有關如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援傳送 Idoc 至 SAP 系統，請參閱[對 sap Idoc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)。 針對傳送 IDOC 訊息的 SOAP 結構的詳細資訊，請參閱[IDOC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md)。  

## <a name="biztalk-scenarios-for-sending-idocs-with-the-sap-adapter"></a>傳送 Idoc 與 SAP 配接器的 BizTalk 案例  
 下表提供重要的 BizTalk 案例傳送 Idoc 到 SAP 系統：  


|       輸入至 BizTalk        |                                                                                                                                                                                                                                                                                                                 BizTalk 處理                                                                                                                                                                                                                                                                                                                  | 輸出配接器 |
|-------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|
|        一般檔案 IDOC         |                                                         **中繼資料設計階段**<br /><br /> 1.設定繫結屬性 GenerateFlatFileCompatibleIdocSchema 來 **，則為 True**。<br />2.產生的結構描述**傳送**作業特定的 IDOC 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。<br /><br /> **協調流程設計階段**<br /><br /> 1.接收一般檔案 IDOC<br />2.您可以使用一般檔案解譯器將一般檔案 IDOC 轉換成使用剛才產生的結構描述的 XML IDOC。<br />3.將動作設定為**傳送**作業。                                                         |   傳送訊息    |
|        一般檔案 IDOC         | **中繼資料設計階段**<br /><br /> 1.設定繫結屬性 GenerateFlatFileCompatibleIdocSchema 來 **，則為 True**。<br />2.產生的結構描述**SendIdoc** IDOC 節點使用的作業[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。<br /><br /> **協調流程設計階段**<br /><br /> 1.接收一般檔案 IDOC<br />2.使用一般檔案解譯器將一般檔案 IDOC 轉換成 XML (在此案例中，包含 XML 訊息\<idocData\>節點，其中包含整個的一般檔案 Idoc 訊息) 使用剛才產生的結構描述。<br />3.將動作設定為**SendIdoc**作業。 | SendIdoc 訊息  |
|           XML IDOC            |                                                                                                                                                           **中繼資料設計階段**<br /><br /> 產生的結構描述**傳送**作業特定的 IDOC 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。<br /><br /> **協調流程設計階段**<br /><br /> 1.接收 XML IDOC。<br />2.將動作設定為**傳送**作業。                                                                                                                                                           |   傳送訊息    |
| XML 訊息中的一般檔案 IDOC |                                                                                                                                                      **中繼資料設計階段**<br /><br /> 產生的結構描述**SendIdoc** IDOC 節點使用的作業[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。<br /><br /> **協調流程設計階段**<br /><br /> 1.接收 XML 訊息。<br />2.將動作設定為**SendIdoc**作業。                                                                                                                                                      | SendIdoc 訊息  |

## <a name="how-to-send-an-idoc-to-an-sap-system"></a>如何傳送 IDOC 至 SAP 系統  
 執行 SAP 系統使用運算[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[建立 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)。 若要傳送 IDOC 到 SAP 系統，這些工作如下：  

1. 建立 BizTalk 專案，並產生您想要叫用 SAP 系統中 IDOC 的結構描述。 產生結構描述時請確定您設定必要的繫結的屬性上, 表中所示。 如需有關如何設定繫結屬性的指示，請參閱 <<c0> [ 設定 SAP 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md)。  

2. 建立傳送和接收訊息，從 SAP 系統的 BizTalk 專案中的訊息。  

3. 建立協調流程以傳送 IDOC 至 SAP 系統。  

4. 建置和部署 BizTalk 專案。  

5. 設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。  

6. 啟動 BizTalk 應用程式。  

   本主題提供執行這些工作的指示。  

## <a name="sample-based-on-this-topic"></a>根據本主題的範例  
 ，IDOCSend，根據本主題也提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 適用於 SAP 配接器範例](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md)。  

## <a name="generating-schema"></a>產生結構描述  
 本主題示範如何傳送 IDOC 至 SAP 系統中，所產生的結構描述*傳送*\IDOC\ORDERS\ORDERS05\ORDERS05 之下的作業。V3(620) IDOC。 請參閱[瀏覽、 搜尋和 get 中繼資料，在 SAP IDOC 作業的](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-idoc-operations-in-sap.md)如需有關如何產生特定的 IDOC 的結構描述。  

## <a name="defining-messages-and-message-types"></a>定義訊息和訊息類型  
 您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。 訊息通常是一個變數，要為其類型會定義對應的結構。 您必須連結您的第一個步驟中的訊息從產生的 BizTalk 專案的 [協調流程] 檢視的結構描述。  

 本主題中，您必須建立兩個訊息，一個用來傳送 IDOC 至 SAP 系統，另一個用於接收的回應。  

 執行下列步驟來建立訊息，並將它們連結至結構描述：  

#### <a name="to-create-messages-and-link-to-schema"></a>若要建立訊息，並連結至結構描述  

1.  開啟協調流程檢視 BizTalk 專案中，如果未開啟。 按一下 **檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。  

2.  在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  

3.  以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。  

4.  在 [**屬性**] 窗格**Message_1**，執行下列動作：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**IDOCSend**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*IDOCSend.SAPBindingSchema3*，其中*IDOCSend*是 BizTalk 專案的名稱。 *SAPBindingSchema3*為傳送作業產生的結構描述。|  

5.  重複上述步驟來建立新的訊息。 在 **屬性**窗格中的新訊息，執行下列動作：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |識別碼|型別**IDOCResponse**。|  
    |訊息類型|從下拉式清單中，依序展開**結構描述**，然後選取*IDOCSend.SAPBindingSchema4*。|  

## <a name="setting-up-the-orchestration"></a>設定協調流程  
 您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]傳送 Idoc 到 SAP 系統。 在此協調流程中，您將會卸除一般檔案 IDOC 在定義接收位置。 此檔案會轉換成 XML 要求訊息使用一般檔案解譯器。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會取用這個訊息，並將它傳遞到 SAP 系統。 包含 GUID 的回應從 SAP 接收，且會儲存在另一個位置。 您必須包含傳送和接收圖形傳送 Idoc 至 SAP 系統，並接收回應。 您也必須包含一般檔案解譯器將一般檔案轉換成 XML 檔案。 典型的協調流程傳送 IDOC 到 SAP 系統便會包含來：  

- 傳送和接收圖形以將訊息傳送至 SAP 系統，並接收回應。  

- 單向接收埠以接收要傳送至 SAP 系統的一般檔案 Idoc。  

- 要轉換成 XML 檔案的一般檔案 IDOC 一般檔案解譯器。  

- 雙向傳送埠以傳送 IDOC 到 SAP 系統，並接收回應。  

- 若要從 SAP 系統的回應傳送到資料夾的單向傳送埠。  

  範例協調流程看起來會如下所示：  

  ![傳送 Idoc 至 SAP 的協調流程](../../adapters-and-accelerators/adapter-sap/media/db1490c8-da52-4af3-8a4f-d93bd815025d.gif "db1490c8-da52-4af3-8a4f-d93bd815025d")  

### <a name="adding-message-shapes"></a>新增訊息圖形  
 請確定您針對每個訊息 圖形中指定下列屬性。 所列的名稱*圖形*資料行是訊息 圖形的名稱，上述協調流程中所示。  

|形狀圖|圖形類型|屬性|  
|-----------|----------------|----------------|  
|ReceiveFile|Receive|-設定**名稱**到*ReceiveFile*<br />-設定**啟用**到 *，則為 True*|  
|SendToLOB|Send|-設定**名稱**到*SendToLOB*|  
|ReceiveResponse|Receive|-設定**名稱**到*ReceiveResponse*<br />-設定**啟用**到*False*|  
|SendResponse|Send|-設定**名稱**到*SendResponse*|  

### <a name="adding-ports"></a>新增連接埠  
 請確定您針對每個邏輯連接埠中指定下列屬性。 所列的名稱*連接埠*資料行名稱就是連接埠在協調流程中所示。  

|通訊埠|屬性|  
|----------|----------------|  
|FileIn|-設定**識別碼**到*FileIn*<br />-設定**型別**到*FileInType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*接收*|  
|LOBPort|-設定**識別碼**到*LOBPort*<br />-設定**型別**到*LOBPortType*<br />-設定**通訊模式**到*要求-回應*<br />-設定**通訊方向**到*傳送接收*|  
|SaveResponse|-設定**識別碼**到*SaveResponse*<br />-設定**型別**到*SaveResponseType*<br />-設定**通訊模式**到*單向*<br />-設定**通訊方向**到*傳送*|  

### <a name="adding-a-flat-file-disassembler"></a>新增一般檔案解譯器  
 您必須將一般檔案解譯器新增至您要轉換成 XML 格式的一般檔案 IDOC 的協調流程。  

##### <a name="to-add-a-flat-file-disassembler"></a>若要加入一般檔案解譯器  

1.  以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後選取**新項目**。  

2.  從對話方塊中，執行下列作業：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |類別|管線檔案|  
    |Visual Studio 安裝的範本|接收管線|  
    |[屬性]|IDOCReceive|  

3.  這會開啟 「 管線設計師 」。 從**BizTalk 管線元件**工具箱，拖曳**一般檔案解譯器**管線元件**解譯**接收管線階段。  

4.  從**管線元件屬性**檢視中，為指定值**文件結構描述**屬性。 從下拉式清單，確定您選取的 IDOC 的傳送作業的對應結構描述。  

## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>為動作圖形指定訊息，並連接到連接埠  
 下表指定之屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。 所列的名稱*圖形*資料行是訊息 圖形的名稱，上述協調流程中所示。  

|形狀圖|屬性|  
|-----------|----------------|  
|ReceiveFile|-設定**訊息**到*IDOCSend*<br />-設定**作業**到*FileIn.SendIDOC.Request*|  
|SendToLob|-設定**訊息**到*IDOCSend*<br />-設定**作業**到*LOBPort.SendIDOC.Request*|  
|ReceiveResponse|-設定**訊息**到*IDOCResponse*<br />-設定**作業**到*LOBPort.SendIDOC.Response*|  
|SendResponse|-設定**訊息**到*IDOCResponse*<br />-設定**作業**到*SaveResponse.SendIDOC.Request*|  

 您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。  

 您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。

## <a name="configuring-the-biztalk-application"></a>設定 BizTalk 應用程式  
 您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程**在 BizTalk Server 管理主控台 窗格。 您必須使用 BizTalk Server 管理主控台來設定應用程式。 如需有關如何設定應用程式的詳細資訊，請參閱 <<c0> [ 如何設定應用程式](../../core/how-to-configure-an-application.md)。

 設定應用程式包含：  

- 選取應用程式主機。  

- 對應您在您在 BizTalk Server 管理主控台中的實體連接埠的協調流程中建立的連接埠。 此協調流程中，您必須：  

  - 定義位置上的硬碟和對應的檔案連接埠，您將會卸除要求訊息。 BizTalk 協調流程將會取用的要求訊息，並將它傳送到 SAP 系統。  

    > [!IMPORTANT]
    >  針對此連接埠的 XMLReceive 管線，請確定您選取***IDOCReceive***。 您已建立此管線的 BizTalk 專案的一部分。  

  - 定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含來自 SAP 系統的回應的回應訊息。  

  - 定義實體 WCF 自訂 」 或 「 WCF SAP 傳送埠將訊息傳送至 SAP 系統。 您也必須在傳送埠中指定的動作。 如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定 SAP 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)。

    > [!NOTE]
    >  您也可以設定*AutoConfirmSentIdocs*繫結會自動將認可 Idoc 到 SAP 系統的屬性。 如果您這樣做，您不需要明確地呼叫 RfcConfirmTransID 作業認可的 Idoc。 如需有關繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。 如需有關 RfcConfirmTransID 作業的詳細資訊，請參閱[對 sap 的 Trfc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。  
    > 
    > [!NOTE]
    >  產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠設定動作的相關資訊的繫結檔案。 您可以從 BizTalk 管理主控台來建立 （適用於輸出的呼叫） 的傳送埠或接收埠 （適用於輸入的呼叫），以匯入此繫結檔案。 如需詳細資訊，請參閱 <<c0> [ 設定的實體連接埠繫結使用的連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。

## <a name="starting-the-application"></a>啟動應用程式  
 您必須啟動 BizTalk 應用程式，以便傳送 IDOC 至 SAP 系統。 如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)，或[如何啟動應用程式](../../core/how-to-start-and-stop-a-biztalk-application.md)。

 在這個階段，請確定：  

-   FILE 接收埠以接收要求訊息的協調流程正在執行。  

-   FILE 傳送埠，以接收回應訊息從協調流程正在執行。  

-   WCF 自訂 」 或 「 WCF SAP 傳送埠將訊息傳送至 SAP 系統正在執行。  

-   BizTalk 協調流程的作業正在執行。  

## <a name="executing-the-operation"></a>執行作業  
 執行應用程式之後，您必須先卸除的協調流程的要求訊息。 針對此範例中，我們會在卸除一般檔案 IDOC 定義 FILE 接收位置。 之後您卸除要求訊息會發生下列動作：  

- 協調流程會挑選此一般檔案 IDOC，並將它轉換成它的結構描述符合您稍早產生的結構描述的 XML 要求訊息。  

- 如果您提供的要求訊息包含 GUID，配接器產生的交易識別碼 (TID)，並將它傳送到 SAP 系統。  

- 如果您提供的要求訊息不會包含一個 GUID，配接器會產生 GUID，並使用該 GUID 產生 TID。 TID 然後傳送到 SAP 系統。  

  在這兩種情況下，從 SAP 系統的回應訊息包含的 GUID。 比方說，ORDERS05 IDOC 的 Send 作業的回應訊息是：  

```  
<?xml version="1.0" encoding="utf-8"?>  
<SendResponse xmlns="http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS05//620/Send">  
  <guid>a5afe162-d5cc-47b0-bf6f-3b0bfe06a97e</guid>  
</SendResponse>  
```  

 您會收到 GUID 之後，您必須叫用**RfConfirmTransID**認可 TID 的作業。 如需詳細資訊**RfcConfirmTransID**作業，請參閱[對 sap 的 Trfc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。 您可以建立新的協調流程呼叫這項作業，或修改現有的協調流程。 如果您想要建立新的協調流程，它會類似於 SAP 系統上的任何其他協調流程。 如果您想要更新現有的協調流程，請參閱[叫用 Trfc SAP 使用 BizTalk Server 中的](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-biztalk-server.md)。 本主題中所述，叫用 tRFC，協調流程示範如何呼叫**RfcConfirmTransID**從相同的協調流程的作業。  

> [!NOTE]
>  需要您設定如果不叫用 RfcConfirmTransID 作業*AutoConfirmSentIdocs*屬性來繫結 **，則為 True**。  

## <a name="possible-exceptions"></a>可能的例外狀況  
 如需傳送 IDOC 至 SAP 系統，請使用 BizTalk Server 時可能發生的例外狀況資訊，請參閱[例外狀況和錯誤處理與 SAP 配接器](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md)。  

## <a name="best-practices"></a>最佳作法  
 您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。 之後產生的繫結檔案時，您可以匯入的組態設定從檔案，讓您不需要建立傳送埠、 接收連接埠、 相同的協調流程等。 如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用 SAP 配接器繫結](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)。

## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)