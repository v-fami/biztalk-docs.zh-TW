---
title: 在 IDOC 作業的訊息結構描述在 BizTalk 中的我 SAP 配接器 |Microsoft Docs
description: 訊息作業、 結構和動作以傳送和接收 Idoc 使用 mySAP 配接器-BizTalk 配接器組件 (BAP)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 601aa9f9-e42f-47aa-b020-7a1eed4f0780
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45ef2f5de5a9e7e13eb2fb53918cb1208a0aeeee
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980023"
---
# <a name="message-schemas-for-idoc-operations"></a>IDOC 作業的訊息結構描述
中繼文件 (IDOC) 是支援 sap 以非同步方式與 SAP 和非 SAP 系統通訊的標準化的類似 EDI 的文件。 IDOC 用來傳送和接收商務文件，例如銷售訂單與交易夥伴的 SAP 系統或外部程式。  

 雖然 SAP 系統支援傳送和接收 IDOC （比方說，file 連接埠或 CPIC 連接埠） 連接埠類型的一些[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]支援傳送及接收 IDOC，使用一個 tRFC 連接埠。  

- 輸出 idoc，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]做為 tRFC 用戶端，並叫用來傳送 IDOC 到 SAP RFC。  

- 輸入 idoc，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]做為 tRFC 伺服器，並接受 tRFC 用戶端呼叫從 SAP 接收 IDOC。  

  [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現您可用來傳送和接收 IDOC 至 SAP 系統的 IDOC 節點下的四個作業。  

- **SendIdoc**。 傳送 IDOC 至配接器，做為字串資料。 這項作業會直接在 IDOC 根節點下顯示。 相同的作業用於所有的 Idoc。  

- **傳送**。 傳送 IDOC 至配接器，做為強型別資料。 這項作業特定的節點下顯示的每個 IDOC。  

- **ReceiveIdoc**。 從配接器接收 IDOC，做為字串資料。 這項作業會直接在 IDOC 根節點下顯示。 相同的作業用於所有的 Idoc。  

- **接收**。 從配接器接收 IDOC，做為強型別資料。 這項作業特定的節點下顯示的每個 IDOC。  

> [!NOTE]
>  這些四個作業提供不同的方式，您的程式之間交換 Idoc 和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 配接器一律會使用 RFC （下一節所述） 來傳送或接收 Idoc，與 SAP 系統。  

 除了使用四個 IDOC 作業的其中一個，您也可以傳送或接收 IDOC，方法是使用其中一種內部使用的 Rfc[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]交換與 SAP 系統的 Idoc。 如需如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援 Idoc，請參閱[對 sap Idoc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)。  

 本主題包含的訊息結構描述和用於 IDOC 作業的訊息動作的相關資訊。  

## <a name="rfcs-used-by-the-sap-adapter-to-send-and-receive-idocs"></a>SAP 配接器用來傳送和接收 Idoc 的 Rfc  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在內部用來與 SAP 系統交換 IDOC 的下列遠端函式呼叫 (Rfc)。 在輸出端 （SAP 系統的配接器），配接器可做為叫用 RFC 的 tRFC 用戶端。 在輸入端 (SAP 配接器)，SAP 叫用的介面卡可做為 tRFC 伺服器 RFC。  

|RFC|描述|  
|---------|-----------------|  
|IDOC_INBOUND_ASYNCHRONOUS|此函式模組用於從 4.0 和更新版本的版本。 它會處理 IDOC 中的記錄類型，適用於 4.x 版本。 這可確保較長的 IDOC 的區段名稱，並支援。<br /><br /> 這個 RFC 的參數包括：<br /><br /> - idoc_control_rec_40 (SAP structure is EDI_DC40)<br /><br /> -idoc_data_rec_40 （SAP 結構是 EDI_DD40）<br /><br /> IDOC 控制記錄是由下列欄位所組成：<br /><br /> - **Mestyp**。 邏輯的訊息類型。 傳遞訊息的商業意義。 這是必要的欄位。<br /><br /> - **Idoctyp**。 IDOC 的基本結構。 此欄位會識別使用這個訊息的配置集合。 這是必要的欄位。<br /><br /> -                      **Cimtyp**。 客戶延伸模組的結構。 如果要延伸的 SAP 的基本結構，客戶必須為擴充功能結構的名稱。 這是必要的欄位，如果客戶已進行一項增強功能;否則初始。<br /><br /> - **合作夥伴欄位**。 這些是傳送端，而且接收端夥伴參數，例如夥伴類型、 夥伴數目、 夥伴函式。<br /><br /> IDOC 資料記錄包含下列欄位：<br /><br /> - **標頭欄位**。 區段標頭欄位，例如資料表名稱、 區段數目、 區段類型。 這些是必要欄位。<br /><br /> -                      **Sdata**。 所使用的資料之 IDOC 的 1000年個位元組字元欄位。這是必要欄位。|  
|INBOUND_IDOC_PROCESS|此函式模組用於最新的 4.0。 它會處理 IDOC 中的記錄類型，適用於 3.x 發行。 它也可使用此函式模組 4.x 中。<br /><br /> 這個 RFC 的參數包括：<br /><br /> -idoc_control （SAP 結構是 EDI_DC）<br /><br /> -idoc_data （SAP 結構是 EDI_DD）|  

## <a name="operations-to-send-idocs"></a>傳送 Idoc 的作業  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會公開傳送和 SendIdoc 傳送 Idoc 至 SAP 系統的用戶端的作業。 傳送作業中，IDOC 被以強型別資料;SendIdoc 作業中，IDOC 會表示為字串資料。 這些作業判斷 IDOC 資料配接器與您的應用程式之間的呈現方式。 配接器一定會傳送至 SAP Idoc 使用 IDOC_INBOUND_ASYNCHRONOUS 或 IDOC_INBOUND_PROCESS (t) RFC。 若要傳送 IDOC 到 SAP 系統，您可以使用 「 傳送 」 或 「 SendIdoc 」 作業，或您可以直接叫用適當的 RFC。  

### <a name="message-structures-for-idoc-client-operations"></a>IDOC 用戶端作業的訊息結構  
 下表顯示 「 傳送 」 和 「 SendIdoc 作業的訊息結構。  


|     作業     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   XML 結構                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                                                                                                                                   描述                                                                                                                                                                                                                                                                                                                                                                   |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       Send        | `<Send xmlns="[MSG_VERSION]/Idoc/[VERSION]/[IDOCTYP]/                    [CIMTYP]/[RELNO]/Send">   <idocData>     <[EDI_DC40/EDI_DC] xmlns="/Types/Idoc/      [VERSION]/[IDOCTYP]/[CIMTYP]/[RELNO]">       <EDIDC_FIELD1>value1</ EDIDC_FIELD1>       <EDIDC_FIELD2>value2</ EDIDC_FIELD2>       …     </EDI_DC40>     <[SEGMENT_DEFN]_1>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_1>     <[SEGMENT_DEFN]_2>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_2>     …     </[EDI_DC40/EDI_DC]>   </idocData>   <guid>guid</guid> </Send>` |                                               將強型別的 IDOC 至 SAP<br /><br /> -IDOC 結構描述是強型別。<br /><br /> -會公開控制記錄的欄位。<br /><br /> -公開資料記錄的欄位，包括區段標頭和區段的欄位。<br /><br /> [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]關聯 SAP 交易識別碼 (TID)，用來傳送 IDOC 中的 GUID。 您可以選擇是否要在要求訊息中指定的 GUID。 如果 GUID 不包含在要求訊息中，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會產生一個。 GUID 會傳回回應訊息中。                                                |
|   傳送回應   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         `<SendResponse xmlns="[MSG_VERSION]/Idoc/[VERSION]/         [IDOCTYP]/[CIMTYP]/[RELNO]/Send">   <guid>guid</guid> </SendResponse>`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | 表示，已傳送 IDOC 至 SAP 系統。<br /><br /> 如果**AutoConfirmSentIdocs**屬性的繫結 **，則為 true**，則[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]自動確認 SAP 系統上的交易，您可以忽略回應中傳回的 GUID。 如果**AutoConfirmSentIdocs**屬性的繫結**false**，您必須叫用**RfcConfirmTransID**所傳回的作業具有 GUID[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]至完成 SAP 系統上的交易。<br /><br /> 您可以叫用**SapAdapterUtilities.ConvertGuidToTid**方法，以取得 TID 相關聯的工作 (LUW) 邏輯單元。 |
|     SendIdoc      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    `<SendIdoc xmlns="[MSG_VERSION]/Idoc">   <idocData>docDataString</idocData>   <guid>guid</guid> </SendIdoc>`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |                                                                   傳送弱型別的 IDOC 到 SAP。<br /><br /> -IDOC 結構描述是弱型別。<br /><br /> -公開 IDOC 為控制記錄和資料記錄所組成的單一字串欄位。<br /><br /> [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]關聯 SAP TID，用來傳送 IDOC 中的 GUID。 您可以選擇是否要在要求訊息中指定的 GUID。 如果 GUID 不包含在要求訊息中，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會產生一個。 回應訊息中傳回的 GUID 是                                                                    |
| SendIdoc 回應 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              `<SendIdocResponse xmlns="[MSG_VERSION]/Idoc">   <guid>guid</guid> </SendIdocResponse>`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |             表示，已傳送 IDOC 至 SAP 系統。<br /><br /> 如果**AutoConfirmSentIdocs**屬性的繫結 **，則為 true**，則[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]自動確認 SAP 系統上的交易，您可以忽略回應中傳回的 GUID。 如果**AutoConfirmSentIdocs**屬性的繫結**false**，您必須叫用**RfcConfirmTransID**所傳回的作業具有 GUID[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]至完成 SAP 系統上的交易。<br /><br /> 您可以叫用**SapAdapterUtilities.ConvertGuidToTid**與 LUW 相關聯的方法，以取得 TID。             |

 [MSG_VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.Sap/2007/03。  

 [VERSION] = （2 或 3） 的 IDOC 的發行版本。  

 [IDOCTYP] = IDOC 類型;比方說，ORDERS05。  

 [CIMTYP] = Cimtype 的自訂 IDOC。  

 [RELNO] = [版次號碼;比方說，620。  

 [EDI_DC40/EDI_DC] = EDI_DC40 發行的第 3 版 Idoc 和 EDI_DC for release version2 Idoc。  

 [EDIDC_FIELD] = 構成 EDI_DC40/EDI_DC 控制記錄結構的欄位。  

 [SEGMENT_DEFN] = 區段定義名稱 （此非區段類型名稱 」）;比方說，E2EDK01005。 請注意，區段定義節點區段群組 節點下，可能也會顯示根據 IDOC 的結構。  

 [DATAHEADERCOLUMN_(SEGHDR_FLD)] = 每個區段有一組標準的後面接著分割資料的標頭欄位所組成的區段標頭。 區段資料是由所有區段欄位和資料所都組成。 此節點所表示的區段標頭欄位中;比方說，DATAHEADERCOLUMN_SEGNAM。  

 [SEG_FIELD] = 構成的特定區段定義 [SEGMENT_DEFN] 的區段欄位名稱。  

 [guid] = GUID 參數。  

### <a name="message-actions-for-idoc-client-operations"></a>IDOC 用戶端作業的訊息動作  
 下表顯示 「 傳送 」 和 「 SendIdoc 作業的訊息動作。  


|     作業     |                                   動作                                   |                                   範例                                   |
|-------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------|
|       Send        |     [MESSAGE_VERSION]/Idoc/[VERSION] /[IDOCTYP]/[CIMTYP]/[RELNO]/Send      |     http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS05//620/Send      |
|   傳送回應   | [MESSAGE_VERSION]/Idoc/[VERSION] /[IDOCTYP]/[CIMTYP]/[RELNO]/Send/response | http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS05//620/Send/response |
|     SendIdoc      |                      [MESSAGE_VERSION]/Idoc/SendIdoc                       |           http://Microsoft.LobServices.Sap/2007/03/Idoc/SendIdoc            |
| SendIdoc 回應 |                  [MESSAGE_VERSION] / Idoc/SendIdoc 回應                  |       http://Microsoft.LobServices.Sap/2007/03/Idoc/SendIdoc/response       |

 [MESSAGE_VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.Sap/2007/03。  

 [VERSION] = （2 或 3） 的 IDOC 的發行版本。  

 [IDOCTYP] = IDOC 類型;比方說，ORDERS05。  

 [CIMTYP] = Cimtype 的自訂 IDOC。  

 [RELNO] = [版次號碼;比方說，620。  

## <a name="operations-to-receive-idocs"></a>若要接收 Idoc 的作業  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會公開從 SAP 系統接收 Idoc 的應用程式的接收和 ReceiveIdoc 作業。 針對接收作業，IDOC 被以強型別資料;ReceiveIdoc 作業中，IDOC 會表示為字串資料。  

 這些作業會決定如何 IDOC 資料，就會發出您的應用程式配接器。 配接器一律會收到從 SAP 系統的 Idoc 為 IDOC_INBOUND_ASYNCHRONOUS 」 或 「 IDOC_INBOUND_PROCESS tRFC。 您可以使用 「 接收 」 或 「 ReceiveIdoc 」 作業，或您可以在 RFC 格式接收 IDOC 的資料。 您設定**ReceiveIdocFormat**繫結屬性可指定配接器會發出您的應用程式的 IDOC 資料的格式。 如需詳細資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結屬性，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  

### <a name="message-structures-for-idoc-receive-operations"></a>訊息結構的 IDOC 接收作業  
 下表顯示 「 接收 」 和 「 ReceiveIdoc 作業的訊息結構。  

|作業|XML 結構|描述|  
|---------------|-------------------|-----------------|  
|Receive|`<Receive xmlns="[MSG_VERSION]/Idoc/[VERSION]/[IDOCTYP]/                 [CIMTYP]/[RELNO]/Receive">   <idocData>     <[EDI_DC40/EDI_DC] xmlns="/Types/Idoc/      [VERSION]/[IDOCTYP]/[CIMTYP]/[RELNO]">       <EDIDC_FIELD1>value1</ EDIDC_FIELD1>       <EDIDC_FIELD2>value2</ EDIDC_FIELD2>       …     </EDI_DC40>     <[SEGMENT_DEFN]_1>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_1>     <[SEGMENT_DEFN]_2>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_2>     …     </[EDI_DC40/EDI_DC]>   </idocData> </Receive>`|從 SAP 接收強型別的 IDOC<br /><br /> -IDOC 結構描述是強型別。<br /><br /> -會公開控制記錄的欄位。<br /><br /> -公開資料記錄的欄位，包括區段標頭和區段的欄位。|  
|接收回應|`<ReceiveResponse xmlns="[MSG_VERSION]/Idoc/[VERSION]/[IDOCTYP]/         [CIMTYP]/[RELNO]/Receive"> </ReceiveResponse>`|表示，已從 SAP 系統接收 IDOC。|  
|ReceiveIdoc|`<ReceiveIdoc xmlns="[MSG_VERSION]/Idoc">   <idocData>docDataString</idocData> </ReceiveIdoc>`|從 SAP 接收弱型別的 IDOC。<br /><br /> -IDOC 結構描述是弱型別。<br /><br /> -公開 IDOC 為控制記錄和資料記錄所組成的單一字串欄位。|  
|ReceiveIdoc 回應|`<ReceiveIdocResponse xmlns="[MSG_VERSION]/Idoc"> </ReceiveIdocResponse>`|表示，已從 SAP 系統接收 IDOC。|  

 [MSG_VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.Sap/2007/03。  

 [VERSION] = （2 或 3） 的 IDOC 的發行版本。  

 [IDOCTYP] = IDOC 類型;比方說，ORDERS05。  

 [CIMTYP] = Cimtype 的自訂 IDOC。  

 [RELNO] = [版次號碼;比方說，620。  

 [EDI_DC40/EDI_DC] = EDI_DC40 發行的第 3 版 Idoc 和 EDI_DC 的釋放第 2 版 Idoc。  

 [EDIDC_FIELD] = 構成 EDI_DC40/EDI_DC 控制記錄結構的欄位。  

 [SEGMENT_DEFN] = 區段定義名稱 （此非區段類型名稱 」）;比方說，E2EDK01005。 區段定義節點也會出現在 IDOC 的結構為基礎的區段群組節點下。  

 [DATAHEADERCOLUMN_(SEGHDR_FLD)] = 每個區段有一組標準的後面接著分割資料的標頭欄位所組成的區段標頭。 區段資料是由所有區段欄位和資料所都組成。 此節點所表示的區段標頭欄位中;比方說，DATAHEADERCOLUMN_SEGNAM。  

 [SEG_FIELD] = 構成的特定區段定義 [SEGMENT_DEFN] 的區段欄位名稱。  

#### <a name="receiving-an-idoc-in-rfc-format"></a>RFC 格式接收 IDOC  
 您也可以接收 Idoc RFC 格式。 用來從 SAP 接收 Idoc 的 Rfc 如下：  

- 第 3 版 Idoc 的 IDOC_INBOUND_ASYNCHRONOUS。  

- 第 2 版 Idoc 的 INBOUND_IDOC_PROCESS。  

  下列程式碼顯示 IDOC_INBOUND_ASYNCHRONOUS 作業以接收 IDOC 的結構。  

```  
<IDOC_INBOUND_ASYNCHRONOUS xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <IDOC_CONTROL_REC_40>  
    <EDI_DC40 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <EDIDC_FIELD1>field1</EDIDC_FIELD1>  
      <EDIDC_FIELD2>field2</EDIDC_FIELD2>  
      …  
    </EDI_DC40>  
  <IDOC_DATA_REC_40>  
    <EDI_DD40 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <[SEG_HEADER_FIELD1]>value1</[SEG_HEADER_FIELD1]>  
      <[SEG_HEADER_FIELD2]>value2</[SEG_HEADER_FIELD2]>  
      …  
      <SDATA>segment value</SDATA>  
    </EDI_DD40>  
    …  
  </IDOC_DATA_REC_40>  
</IDOC_INBOUND_ASYNCHRONOUS>  
```  

 [EDIDC_FIELD] = 構成 EDI_DC40/EDI_DC 控制記錄結構的欄位  

 [SEG_HEADER_FIELD] = 每個區段有一組標準的後面接著分割資料的標頭欄位所組成的區段標頭。 區段資料是由所有區段欄位和資料所都組成。 此節點所表示的區段標頭欄位中;比方說，SEGNAM、 MANDT 和 DOCNUM。  

 TRFC 作業的格式的相關資訊，請參閱[tRFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md)。  

### <a name="message-actions-for-idoc-receive-operations"></a>IDOC 的訊息動作接收作業  
 下表顯示 「 接收 」 和 「 ReceiveIdoc 作業的訊息動作。  


|      作業       |                                    動作                                     |                                    範例                                     |
|----------------------|-------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
|       Receive        |     [MESSAGE_VERSION]/Idoc/[VERSION] /[IDOCTYP]/[CIMTYP]/[RELNO]/Receive      |     http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS05//620/Receive      |
|   接收回應   | [MESSAGE_VERSION]/Idoc/[VERSION] /[IDOCTYP]/[CIMTYP]/[RELNO]/Receive/response | http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS05//620/Receive/response |
|     ReceiveIdoc      |                      [MESSAGE_VERSION]/Idoc/ReceiveIdoc                       |           http://Microsoft.LobServices.Sap/2007/03/Idoc/ReceiveIdoc            |
| ReceiveIdoc 回應 |                  [MESSAGE_VERSION] / Idoc/ReceiveIdoc 回應                  |       http://Microsoft.LobServices.Sap/2007/03/Idoc/ReceiveIdoc/response       |

