---
title: 在 IDOC 作業的訊息結構描述在 BizTalk 我 SAP 配接器 |Microsoft 文件
description: 訊息作業、 結構和動作來傳送和接收 Idoc 使用 mySAP 配接器-BizTalk 配接器組件 (BAP)
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
ms.openlocfilehash: 53da14ff55d427e3507273af4c991072cff26bec
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "25967412"
---
# <a name="message-schemas-for-idoc-operations"></a>IDOC 作業的訊息結構描述
中繼文件 (IDOC) 是以非同步方式與 SAP 和非 SAP 系統通訊的 SAP 所支援的標準化的 EDI 類似文件。 IDOC 用來傳送和接收商務文件，例如銷售訂單與交易夥伴的 SAP 系統或外部程式。  
  
 雖然 SAP 系統支援傳送和接收 IDOC （例如，檔案連接埠或 CPIC 連接埠） 的連接埠類型的數字[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]支援傳送及接收 IDOC 利用 tRFC 連接埠。  
  
-   輸出 idoc，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]做為 tRFC 用戶端，並叫用來傳送 IDOC 到 SAP RFC。  
  
-   輸入 idoc，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]做為 tRFC 伺服器，並接受 tRFC 用戶端呼叫從 SAP 接收 IDOC。  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]介面可用來傳送和接收 IDOC 至 SAP 系統的 IDOC 節點之下的四個操作。  
  
-   **SendIdoc**。 以字串資料傳送至配接器的 IDOC。 這項作業會直接在 IDOC 根節點下顯示。 相同的作業適用於所有的 Idoc。  
  
-   **傳送**。 傳送 IDOC 至配接器，做為強型別資料。 這項作業的特定節點下顯示的每個 IDOC。  
  
-   **ReceiveIdoc**。 從配接器接收 IDOC，做為字串資料。 這項作業會直接在 IDOC 根節點下顯示。 相同的作業適用於所有的 Idoc。  
  
-   **接收**。 從配接器接收 IDOC，做為強型別資料。 這項作業的特定節點下顯示的每個 IDOC。  
  
> [!NOTE]
>  這些四個作業提供不同的方式，您的程式之間交換 Idoc 和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 配接器永遠會使用 RFC （如下一節所述） 來傳送或接收的 Idoc 到 SAP 系統。  
  
 除了使用四個 IDOC 作業的其中一個，也可以傳送或接收 IDOC，使用其中一種在內部使用的 Rfc[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]交換 Idoc 到 SAP 系統。 如需如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援 Idoc，請參閱[sap Idoc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)。  
  
 本主題包含的訊息結構描述和 IDOC 作業所使用的訊息動作的相關資訊。  
  
## <a name="rfcs-used-by-the-sap-adapter-to-send-and-receive-idocs"></a>SAP 配接器用來傳送和接收 Idoc 的 Rfc  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]交換 IDOC 到 SAP 系統在內部使用下列遠端函式呼叫 (Rfc)。 在輸出端 （至 SAP 系統的配接器），配接器會做為叫用 RFC tRFC 用戶端。 在傳入端 (SAP 配接器)，SAP 會叫用的介面卡可做為 tRFC 伺服器上的 RFC。  
  
|RFC|Description|  
|---------|-----------------|  
|IDOC_INBOUND_ASYNCHRONOUS|從 4.0 版及更新版本使用此函式模組。 它會處理 IDOC 中適用於 4.x 版本的記錄類型。 這可確保較長的 IDOC 區段名稱受支援。<br /><br /> 這個 RFC 的參數包括：<br /><br /> -idoc_control_rec_40 （SAP 結構是 EDI_DC40）<br /><br /> -idoc_data_rec_40 （SAP 結構是 EDI_DD40）<br /><br /> IDOC 控制記錄包含下列欄位：<br /><br /> - **Mestyp**。 邏輯的訊息類型。 轉送訊息的商業意義。 這是必要的欄位。<br /><br /> - **Idoctyp**。 IDOC 的基本結構。 此欄位會識別使用此訊息版面配置設定。 這是必要的欄位。<br /><br /> -                      **Cimtyp**。 客戶延伸模組的結構。 如果擴充 SAP 基本結構，客戶必須加入擴充功能的結構指定的名稱。 這是必要的欄位，如果客戶已進行的增強功能;否則初始。<br /><br /> - **夥伴欄位**。 這些是傳送端，而且接收端夥伴參數，例如協力廠商的型別、 夥伴數目、 夥伴函式。<br /><br /> IDOC 資料記錄包含下列欄位：<br /><br /> - **標頭欄位**。 區段標頭欄位，例如資料表名稱、 區段數目、 區段類型。 這些是必要欄位。<br /><br /> -                      **Sdata**。 1000 個位元組的字元 IDOC 所使用的資料欄位。這是必要欄位。|  
|INBOUND_IDOC_PROCESS|此函式模組用來發行至 4.0。 它會處理 IDOC 中適用於 3.x 發行記錄類型。 它也可在 4.x 中使用此函式模組。<br /><br /> 這個 RFC 的參數包括：<br /><br /> -idoc_control （SAP 結構是 EDI_DC）<br /><br /> -idoc_data （SAP 結構是 EDI_DD）|  
  
## <a name="operations-to-send-idocs"></a>傳送 Idoc 的作業  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]公開 （expose) 用戶端傳送 Idoc 到 SAP 系統的 Send 和 SendIdoc 作業。 傳送作業中，IDOC 被以強型別資料。SendIdoc 的操作，IDOC 被以字串資料。 這些作業，判斷 IDOC 資料配接器與您的應用程式之間的呈現方式。 配接器一定會傳送至 SAP Idoc 使用 IDOC_INBOUND_ASYNCHRONOUS 或 IDOC_INBOUND_PROCESS (t) RFC。 若要傳送 IDOC 到 SAP 系統，您可以使用 「 傳送 」 或 「 SendIdoc 」 作業，或您可以直接叫用適當的 RFC。  
  
### <a name="message-structures-for-idoc-client-operations"></a>IDOC 用戶端作業的訊息結構  
 下表顯示在傳送及 SendIdoc 作業的訊息結構。  
  
|運算|XML 結構|Description|  
|---------------|-------------------|-----------------|  
|Send|`<Send xmlns="[MSG_VERSION]/Idoc/[VERSION]/[IDOCTYP]/                    [CIMTYP]/[RELNO]/Send">   <idocData>     <[EDI_DC40/EDI_DC] xmlns="/Types/Idoc/      [VERSION]/[IDOCTYP]/[CIMTYP]/[RELNO]">       <EDIDC_FIELD1>value1</ EDIDC_FIELD1>       <EDIDC_FIELD2>value2</ EDIDC_FIELD2>       …     </EDI_DC40>     <[SEGMENT_DEFN]_1>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_1>     <[SEGMENT_DEFN]_2>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_2>     …     </[EDI_DC40/EDI_DC]>   </idocData>   <guid>guid</guid> </Send>`|傳送至 SAP 的強型別的 IDOC<br /><br /> -IDOC 結構描述是強型別。<br /><br /> -會公開控制記錄欄位。<br /><br /> -公開資料記錄的欄位，包括區段標頭和區段欄位。<br /><br /> [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]關聯 SAP 交易識別碼 (TID)，它會使用可傳送 IDOC 的 GUID。 您可以選擇是否要指定要求訊息中的 GUID。 如果未在要求訊息中包含 GUID[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會產生一個。 GUID 會傳回回應訊息中。|  
|傳送回應|`<SendResponse xmlns="[MSG_VERSION]/Idoc/[VERSION]/         [IDOCTYP]/[CIMTYP]/[RELNO]/Send">   <guid>guid</guid> </SendResponse>`|表示，已傳送 IDOC 至 SAP 系統。<br /><br /> 如果**AutoConfirmSentIdocs**繫結屬性是**true**、[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]自動確認 SAP 系統上的交易，您可以忽略在回應中傳回的 GUID。 如果**AutoConfirmSentIdocs**繫結屬性是**false**，您必須叫用**RfcConfirmTransID**所傳回的作業具有 GUID[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]至完成上 SAP 系統的異動。<br /><br /> 您可以叫用**SapAdapterUtilities.ConvertGuidToTid**方法，以取得 TID 相關聯的工作 (LUW) 邏輯單元。|  
|SendIdoc|`<SendIdoc xmlns="[MSG_VERSION]/Idoc">   <idocData>docDataString</idocData>   <guid>guid</guid> </SendIdoc>`|傳送弱型別的 IDOC 至 SAP。<br /><br /> -IDOC 結構描述是弱型別。<br /><br /> -公開 IDOC 為控制記錄和資料記錄所組成的單一字串欄位。<br /><br /> [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]關聯 SAP TID，用來傳送 IDOC 的 GUID。 您可以選擇是否要指定要求訊息中的 GUID。 如果未在要求訊息中包含 GUID[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]產生一個。 回應訊息中傳回 GUID|  
|SendIdoc 回應|`<SendIdocResponse xmlns="[MSG_VERSION]/Idoc">   <guid>guid</guid> </SendIdocResponse>`|表示，已傳送 IDOC 至 SAP 系統。<br /><br /> 如果**AutoConfirmSentIdocs**繫結屬性是**true**、[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]自動確認 SAP 系統上的交易，您可以忽略在回應中傳回的 GUID。 如果**AutoConfirmSentIdocs**繫結屬性是**false**，您必須叫用**RfcConfirmTransID**所傳回的作業具有 GUID[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]至完成上 SAP 系統的異動。<br /><br /> 您可以叫用**SapAdapterUtilities.ConvertGuidToTid**與 LUW 相關聯的方法，以取得 TID。|  
  
 [MSG_VERSION] = 訊息版本字串。例如， http://Microsoft.LobServices.Sap/2007/03。  
  
 [版本] = IDOC 發行版本 （2 或 3）。  
  
 [IDOCTYP] = IDOC 類型;例如，ORDERS05。  
  
 [CIMTYP] = Cimtype 的自訂 IDOC。  
  
 [RELNO] = 版次號碼;例如，620。  
  
 [EDI_DC40/EDI_DC] = EDI_DC40 版本發行的第 3 版 Idoc 與針對 EDI_DC version2 Idoc。  
  
 [EDIDC_FIELD] = 從屬 EDI_DC40/EDI_DC 控制記錄結構的欄位。  
  
 [SEGMENT_DEFN] = 區段定義名稱 （而非區段類型名稱）;例如，E2EDK01005。 請注意，片段定義節點區段群組 節點下，可能也會顯示根據 IDOC 的結構。  
  
 [DATAHEADERCOLUMN_(SEGHDR_FLD)] = 每個區段有一組標準的後面的區段資料的標頭欄位所組成的區段標頭。 區段資料包含的所有區段欄位和資料。 此節點表示的區段標頭欄位中。例如，DATAHEADERCOLUMN_SEGNAM。  
  
 [SEG_FIELD] = 從屬的特定區段定義 [SEGMENT_DEFN] 區段欄位名稱。  
  
 [guid] = GUID 參數。  
  
### <a name="message-actions-for-idoc-client-operations"></a>IDOC 用戶端作業的訊息動作  
 下表顯示在傳送及 SendIdoc 作業的訊息動作。  
  
|運算|動作|範例|  
|---------------|------------|-------------|  
|Send|[MESSAGE_VERSION]/Idoc/[VERSION] /[IDOCTYP]/[CIMTYP]/[RELNO]/Send|http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS05//620/Send|  
|傳送回應|[MESSAGE_VERSION]/Idoc/[VERSION] /[IDOCTYP]/[CIMTYP]/[RELNO]/Send/response|http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS05//620/Send/response|  
|SendIdoc|[MESSAGE_VERSION]/Idoc/SendIdoc|http://Microsoft.LobServices.Sap/2007/03/Idoc/SendIdoc|  
|SendIdoc 回應|[MESSAGE_VERSION] / Idoc/SendIdoc 回應|http://Microsoft.LobServices.Sap/2007/03/Idoc/SendIdoc/response|  
  
 [MESSAGE_VERSION] = 訊息版本字串。例如， http://Microsoft.LobServices.Sap/2007/03。  
  
 [版本] = IDOC 發行版本 （2 或 3）。  
  
 [IDOCTYP] = IDOC 類型;例如，ORDERS05。  
  
 [CIMTYP] = Cimtype 的自訂 IDOC。  
  
 [RELNO] = 版次號碼;例如，620。  
  
## <a name="operations-to-receive-idocs"></a>若要接收 Idoc 的作業  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]公開的應用程式從 SAP 系統接收 Idoc 的接收管線和 ReceiveIdoc 作業。 針對接收作業中，IDOC 被以強型別資料。ReceiveIdoc 的操作，IDOC 被以字串資料。  
  
 這些作業，判斷您的應用程式配接器發出 IDOC 資料的方式。 配接器永遠會接收從 SAP 系統的 Idoc IDOC_INBOUND_ASYNCHRONOUS 」 或 「 IDOC_INBOUND_PROCESS tRFC 當做。 您可以使用 「 接收 」 或 「 ReceiveIdoc 」 作業，或您可以在 RFC 格式接收 IDOC 資料。 您設定**ReceiveIdocFormat**內容繫結至指定的配接器會發出您的應用程式的 IDOC 資料的格式。 如需有關[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結屬性，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
### <a name="message-structures-for-idoc-receive-operations"></a>訊息結構 IDOC 的接收作業  
 下表顯示 「 接收 」 和 「 ReceiveIdoc 作業的訊息結構。  
  
|運算|XML 結構|Description|  
|---------------|-------------------|-----------------|  
|Receive|`<Receive xmlns="[MSG_VERSION]/Idoc/[VERSION]/[IDOCTYP]/                 [CIMTYP]/[RELNO]/Receive">   <idocData>     <[EDI_DC40/EDI_DC] xmlns="/Types/Idoc/      [VERSION]/[IDOCTYP]/[CIMTYP]/[RELNO]">       <EDIDC_FIELD1>value1</ EDIDC_FIELD1>       <EDIDC_FIELD2>value2</ EDIDC_FIELD2>       …     </EDI_DC40>     <[SEGMENT_DEFN]_1>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_1>     <[SEGMENT_DEFN]_2>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_2>     …     </[EDI_DC40/EDI_DC]>   </idocData> </Receive>`|從 SAP 接收強型別的 IDOC<br /><br /> -IDOC 結構描述是強型別。<br /><br /> -會公開控制記錄欄位。<br /><br /> -公開資料記錄的欄位，包括區段標頭和區段欄位。|  
|接收回應|`<ReceiveResponse xmlns="[MSG_VERSION]/Idoc/[VERSION]/[IDOCTYP]/         [CIMTYP]/[RELNO]/Receive"> </ReceiveResponse>`|表示，已從 SAP 系統接收 IDOC。|  
|ReceiveIdoc|`<ReceiveIdoc xmlns="[MSG_VERSION]/Idoc">   <idocData>docDataString</idocData> </ReceiveIdoc>`|從 SAP 接收弱型別的 IDOC。<br /><br /> -IDOC 結構描述是弱型別。<br /><br /> -公開 IDOC 為控制記錄和資料記錄所組成的單一字串欄位。|  
|ReceiveIdoc 回應|`<ReceiveIdocResponse xmlns="[MSG_VERSION]/Idoc"> </ReceiveIdocResponse>`|表示，已從 SAP 系統接收 IDOC。|  
  
 [MSG_VERSION] = 訊息版本字串。例如， http://Microsoft.LobServices.Sap/2007/03。  
  
 [版本] = IDOC 發行版本 （2 或 3）。  
  
 [IDOCTYP] = IDOC 類型;例如，ORDERS05。  
  
 [CIMTYP] = Cimtype 的自訂 IDOC。  
  
 [RELNO] = 版次號碼;例如，620。  
  
 [EDI_DC40/EDI_DC] = EDI_DC40 發行的第 3 版 Idoc 的 EDI_DC 版第 2 版 Idoc。  
  
 [EDIDC_FIELD] = 從屬 EDI_DC40/EDI_DC 控制記錄結構的欄位。  
  
 [SEGMENT_DEFN] = 區段定義名稱 （而非區段類型名稱）;例如，E2EDK01005。 區段定義節點也會出現之 IDOC 的結構為基礎的區段群組節點下。  
  
 [DATAHEADERCOLUMN_(SEGHDR_FLD)] = 每個區段有一組標準的後面的區段資料的標頭欄位所組成的區段標頭。 區段資料包含的所有區段欄位和資料。 此節點表示的區段標頭欄位中。例如，DATAHEADERCOLUMN_SEGNAM。  
  
 [SEG_FIELD] = 從屬的特定區段定義 [SEGMENT_DEFN] 區段欄位名稱。  
  
#### <a name="receiving-an-idoc-in-rfc-format"></a>RFC 格式接收 IDOC  
 您也可以接收 Idoc RFC 格式。 用來從 SAP 接收 Idoc 的 Rfc 如下：  
  
-   第 3 版 Idoc 的 IDOC_INBOUND_ASYNCHRONOUS。  
  
-   第 2 版 Idoc 的 INBOUND_IDOC_PROCESS。  
  
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
  
 [EDIDC_FIELD] = 從屬 EDI_DC40/EDI_DC 控制記錄結構的欄位  
  
 [SEG_HEADER_FIELD] = 每個區段有一組標準的後面的區段資料的標頭欄位所組成的區段標頭。 區段資料包含的所有區段欄位和資料。 此節點表示的區段標頭欄位中。例如，SEGNAM、 MANDT 和 DOCNUM。  
  
 TRFC 作業的格式的相關資訊，請參閱[tRFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md)。  
  
### <a name="message-actions-for-idoc-receive-operations"></a>IDOC 的訊息動作接收作業  
 下表顯示 「 接收 」 和 「 ReceiveIdoc 作業的訊息動作。  
  
|運算|動作|範例|  
|---------------|------------|-------------|  
|Receive|[MESSAGE_VERSION]/Idoc/[VERSION] /[IDOCTYP]/[CIMTYP]/[RELNO]/Receive|http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS05//620/Receive|  
|接收回應|[MESSAGE_VERSION]/Idoc/[VERSION] /[IDOCTYP]/[CIMTYP]/[RELNO]/Receive/response|http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS05//620/Receive/response|  
|ReceiveIdoc|[MESSAGE_VERSION]/Idoc/ReceiveIdoc|http://Microsoft.LobServices.Sap/2007/03/Idoc/ReceiveIdoc|  
|ReceiveIdoc 回應|[MESSAGE_VERSION] / Idoc/ReceiveIdoc 回應|http://Microsoft.LobServices.Sap/2007/03/Idoc/ReceiveIdoc/response|  
  
