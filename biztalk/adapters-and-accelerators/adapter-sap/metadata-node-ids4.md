---
title: 在 BizTalk Adapter Pack mySAP 配接器中繼資料節點識別碼 |Microsoft 文件
description: 中繼資料、 搜尋、 擷取節點型別和 mySAP 配接器-BizTalk 配接器組件 (BAP) 中公開的 SAP 元件中使用的識別碼
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46385060-f56a-4e06-9122-b75808776716
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 138e46b198df48348dcef35662589f6a3c2e317a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="node-types-and-ids-for-the-sap-adapter"></a>節點型別與 SAP 配接器的識別碼

## <a name="metadata-node-types-and-ids"></a>中繼資料節點類型和 Id
下表列出節點型別和 SAP 成品的節點識別碼，[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]介面。 節點識別碼是使用中節點的絕對路徑**IMetadataRetrievalContractBrowse**，**搜尋**，和**GetMetadata**方法。  
  
|成品的顯示名稱|節點類型|節點識別碼|  
|---------------------------|---------------|-------------|  
|RFC|類別目錄|[版本] / RFCSECTION|  
|[RFC_APPL_GROUP_NAME]|類別目錄|[VERSION]/RFCGROUP/[RFC_APPL_GROUP_ID]|  
|[RFC_NAME]|OPERATION|[VERSION]/Rfc/[RFC_NAME]|  
|RfcGetAttributes|OPERATION|[VERSION]/RfcApi/RfcGetAttributes|  
|TRFC|類別目錄|[VERSION]/TRFCSECTION|  
|[TRFC_APPL_GROUP_NAME]|類別目錄|[VERSION]/TRFCGROUP/[TRFC_APPL_GROUP_ID]|  
|[TRFC_NAME]|OPERATION|[VERSION]/TRfc/[TRFC_NAME]|  
|RfcConfirmTransID|OPERATION|[VERSION]/RfcApi/RfcConfirmTransID|  
|BAPI|類別目錄|[VERSION]/BAPISECTION/000001|  
|[BAPI_APPL_GROUP_NAME]|類別目錄|[VERSION]/BAPISECTION/[ BAPI_APPL_GROUP_NODE_ID]|  
|[BUSINESS_OBJECT_NAME]|類別目錄|[VERSION]/BAPIOBJ/[BUSOBJ_TYPE]|  
|[BUSINESS_OBJECT_METHOD]|OPERATION|[VERSION]/BAPIOBJ/[BUSOBJ_TYPE]/[BUSOBJ_METHOD]/[FUNCTION_MODULE]|  
|IDOC|類別目錄|[版本] / IDOCSECTION|  
|[IDOC_MSG_TYPE_NAME]|類別目錄|[VERSION]/IDOCMESTYP/[IDOC_MSG_TYPE_NAME]|  
|([IDOC_TYPE_NAME]) ([IDOC_CIMTYPE])|類別目錄|[VERSION]/IDOCCIMTYP/[IDOC_TYPE_NAME]/[IDOC_CIMTYPE]/[FIRST_IDOC_REL_NO]|  
|([IDOC_TYPE_NAME]。V[IDOC_VERSION]) ([IDOC_CIMTYPE]) ([IDOC_REL_NO])|類別目錄|[VERSION]/IDOCCIMVER/[IDOC_VERSION]/[IDOC_TYPE_NAME]/[IDOC_CIMTYPE]/[IDOC_REL_NO]|  
|Send|OPERATION|[VERSION]/Idoc/[IDOC_VERSION]/[IDOC_TYPE_NAME]/[IDOC_CIMTYPE]/[IDOC_REL_NO]/Send|  
|SendIdoc|OPERATION|[VERSION]/Idoc/SendIdoc|  
|Receive|OPERATION|[VERSION]/Idoc/[IDOC_VERSION]/[IDOC_TYPE_NAME]/[IDOC_CIMTYPE]/[IDOC_REL_NO]/Receive|  
|ReceiveIdoc|OPERATION|[VERSION]/Idoc/ReceiveIdoc|  
  
 [版本] = 版本字串。例如， http://Microsoft.LobServices.Sap/2007/03。  
  
 [RFC_APPL_GROUP_NAME] = 應用程式群組名稱;例如，銷售。  
  
 [RFC_APPL_GROUP_ ID] = SAP; 中的應用程式群組相關聯識別碼例如，V （用於 Sales)。  
  
 [RFC_NAME] = RFC; 的名稱例如，RFC_GET_SYSTEM_INFO。  
  
 [TRFC_APPL_GROUP_NAME] = 應用程式群組名稱;例如，銷售。 這是 Rfc 的應用程式群組的名稱。  
  
 [TRFC_APPL_GROUP_ ID] = SAP; 中的應用程式群組相關聯識別碼例如，V （用於 Sales)。 這是 Rfc 識別碼相同。  
  
 [TRFC_NAME] = tRFC; 的名稱例如，RFC_GET_SYSTEM_INFO。 這是 RFC 名稱相同。  
  
 [BAPI_APPL_GROUP_NAME] = 與 SAP 中的 BAPI explorer BAPI 群組的名稱。 例如，銷售和散發。  
  
 [BAPI_APPL_GROUP_NODE_ID] = SAP; 中的 BAPI 總管樹狀目錄中對應的節點相關聯識別碼例如，銷售及散發 3253。 請注意，可能是給定的 BAPI 群組節點下的其他群組節點。 例如，銷售和發佈節點有另一個群組節點下，稱為 Sales （節點識別碼 3375）。  
  
 [BUSINESS_OBJECT_NAME] = 商務物件; 的名稱例如，銷售訂單。  
  
 [BUSOBJ_TYPE] = SAP; 中的商務物件類型例如 BUS2032 銷售訂單的商務物件。  
  
 [BUSINESS_OBJECT_METHOD] = 商務物件方法的名稱例如，銷售訂單商務物件的 GETLIST。  
  
 [函式模組] = 針對商務物件方法; SAP 函式模組例如，BAPI_SALESORDER_GETLIST GETLIST 的銷售訂單的商務物件的方法。  
  
 [IDOC_MSG_TYPE_NAME] = IDOC 訊息類型; 的名稱例如，訂單。  
  
 [IDOC_TYPE_NAME] = 將 IDOC 類型的名稱例如，ORDERS05。  
  
 [IDOC_CIMTYPE] = IDOC CIM 類型 （副檔名）。例如，Z1ORDERS。  
  
 [FIRST_IDOC_REL_NO] = 針對特定的 IDOC 類型; 最小的 IDOC 版次號碼例如，在特定的 SAP 系統的 ORDERS05 46A。  
  
 [IDOC_VERSION] = IDOC 版本的版本號碼;2 個版本 2 的 IDOC 和 3 版本 3 IDOC 資料庫...  
  
 [IDOC_REL_NO] = IDOC 版本號碼;例如 46A 46B，或 620。  
  
## <a name="metadata-search-node-ids"></a>搜尋中繼資料的節點識別碼  
 中繼資料搜尋是功能強大功能[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]介面的一部分其**IMetadataRetrievalContract**介面。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]為支援搜尋下列 SAP 成品會使用這項功能。  
  
|成品的顯示名稱|節點識別碼|Description|  
|---------------------------|-------------|-----------------|  
|/RFC|[版本] / RFCSECTION|傳回所有符合搜尋運算式的 RFC 作業。|  
|/RFC/[RFC_APPL_GROUP_NAME]|[VERSION]/RFCGROUP/[RFC_APPL_GROUP_NAME]|傳回 RFC 作業的應用程式群組中符合搜尋運算式。|  
|/TRFC|[VERSION]/TRFCSECTION|傳回所有符合搜尋運算式的 RFC 作業。|  
|/TRFC/[TRFC_APPL_GROUP_NAME]|[VERSION]/TRFCGROUP/[TRFC_APPL_GROUP_NAME]|傳回 RFC 作業的應用程式群組中符合搜尋運算式。|  
|/BAPI|[版本] / BAPISECTION|傳回所有符合搜尋運算式的 Bapi。|  
|/IDOC|[版本] / IDOCSECTION|傳回所有符合搜尋運算式的 Idoc。|  
  
 下表列出中的萬用字元，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援在搜尋運算式中。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|加號 （+）|比對一個字元。<br /><br /> 例如，A + 比對 AB、 AC、 AD、 等等。|  
|星號 （*）|比對零個或多個字元。例如，"A *"符合"A"、"AB"，"ABC"，等等。|  
  
## <a name="metadata-retrieval-node-ids"></a>中繼資料擷取節點識別碼  
 下表摘要說明所傳回的中繼資料特性[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
|成品|中繼資料的特性|  
|--------------|------------------------------|  
|RFC|-   RFC name.<br />-RFC 匯入、 匯出、 變更及資料表參數。<br />-RFC 參數資料類型。<br />的對應至 facet maxLength RFC 參數欄位長度<br />-RFC 強制參數對應至 facet minOccurs = 1<br />-RFC 選擇性參數對應至 facet minOccurs = 0<br />-RFC 參數 NULL 條件約束對應至 facet isNillable = true。 這表示配接器應該將此參數傳遞至 SAP 系統。<br />-RFC 本身是的作業。|  
|TRFC|除了 RFC 相同<br /><br /> -RFC 匯入參數便不會顯示。 因為 tRFC 是非同步的便會不顯示任何輸出參數。|  
|BAPI|的商務物件名稱<br />名稱的商務物件方法<br />-與 RFC 特性相同，|  
|IDOC|IDOC 類型<br /><br /> CIMType<br /><br /> IDOC 版次號碼<br /><br /> IDOC 版本<br /><br /> IDOC 控制記錄欄位對應至 EDI_DC 複雜類型<br /><br /> IDOC 資料記錄區段和區段欄位對應至 EDI_DD 複雜型別<br /><br /> 區段父子式關聯性<br /><br /> IDOC 區段強制參數對應至 minOccurs = 1<br /><br /> IDOC 區段的選擇性參數對應至 minOccurs = 0<br /><br /> IDOC 區段標頭欄位名稱<br /><br /> IDOC 區段標頭欄位資料型別<br /><br /> IDOC 區段欄位名稱<br /><br /> IDOC 區段欄位資料類型<br /><br /> IDOC 區段欄位值列舉<br /><br /> IDOC 區段欄位最小值、 最大值 （範圍）**附註：**時 IDOC 區段欄位包含最小值的清單，它會呈現為列舉型別。 如果 IDOC 區段欄位包含最小和最大值，它會顯示為不含任何列舉型別或範圍建構字串。|  
  
 中繼資料的格式的詳細資訊，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]公開特定成品和作業在 SAP 系統上，請參閱[訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)。  
  
