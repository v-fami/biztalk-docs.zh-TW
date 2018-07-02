---
title: 在 SAP 中的提供者所使用的自訂 Rfc |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Z_EXTRACT_DATA_OO, limitations related to
- RFC, Z_EXTRACT_DATA_OO
- Z_EXTRACT_DATA_OO
- Z_EXTRACT_DATA_OO, best practice
- Z_EXTRACT_DATA_OO, security issue
ms.assetid: 95661f4c-0431-40ca-8a53-3fbe359b8afd
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36b359fc893b8616fd4fb7339e9efbc42d7d3e13
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992719"
---
# <a name="custom-rfcs-used-by-the-provider-in-sap"></a>在 SAP 中的提供者所使用的自訂 Rfc
[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]提供下列自訂 Rfc，在內部用來執行 SAP 系統上的作業。  
  
- **Z_EXTRACT_DATA_OO RFC**。 資料擷取 RFC，Z_EXTRACT_DATA_OO，會從資料表擷取資料或檢視中的 SAP R/3 系統、 將轉換的資料，並傳回同步中的 SQL Server 資料表的資料或傾印到一般檔案資料。 Z_EXTRACT_DATA_OO 用來執行與 WHERE 子句的 SELECT 作業。 這個 RFC 的效能是您 SAP 系統的硬體而定。  
  
   如需如何將.NET 和 SAP 資料型別對應的 Z_EXTRACT_DATA_OO RFC 資訊，請參閱[Data Type Mapping for 自訂 Rfc](../../adapters-and-accelerators/adapter-sap/data-type-mapping-for-custom-rfcs.md)。  
  
- **Z_EXECUTE_SAP_QUERY RFC**。 使用這個 RFC[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]來執行 SAP 系統中已定義的查詢。 這個 RFC 會在內部執行的 SAP RFC，RSAQ_REMOTE_QUERY_CALL。 SAP 查詢是以圖形方式建立所選取資料表、 資料行、 輸入的參數，結果集等的排序順序中使用 SAP GUI 的查詢。使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]您現在可以執行這類 SAP 查詢從 ADO.NET 用戶端。  
  
   EXECQUERY 作業所傳回的所有值都都屬於字串類型。  
  
## <a name="limitations-related-to-the-zextractdataoo-rfc"></a>有關 Z_EXTRACT_DATA_OO RFC 的限制  
  
-   Z_EXTRACT_DATA_OO RFC 支援滿足下列條件的資料表中讀取資料：  
  
    -   資料表的 TabClass 是 TRANSP、 叢集或集區。  
  
    -   TabClass 檢視而 ViewClass D 或 p。  
  
-   Z_EXTRACT_DATA_OO 不支援 HR 叢集資料表，例如 PCL1、 PCL2、 PCL3、 PCL4、 PCL5。  
  
-   可以由 Z_EXTRACT_DATA_OO 擷取的資料列數目取決於 SAP 伺服器上的硬體資源。  
  
-   主索引鍵的順序，會傳回所有擷取的資料。  
  
-   不支援資料表或檢視表包含字串、 SSTRING 和 RAWSTRING 可變長度資料類型。 無法擷取資料表或檢視表包含這些資料類型。  
  
-   Z_EXTRACT_DATA_OO 執行轉換結束已指派給他們的轉換結束的所有欄位。 在 SELECT 陳述式的 WHERE 子句中，就必須輸入產生的轉換的值。 也會傳回已轉換的值。 這可能會造成 Z_EXTRACT_DATA_OO 所傳回的結果中的 SAP 資料瀏覽器 (SE16) 傳回的結果之間的不一致。  
  
-   選取的資料表不能包含是 ABAP （例如，連線） 中的保留的名稱的欄位名稱。  
  
-   由於 SAP R/3 4.6c，版本型別的整數欄位的值中的查詢處理器中的限制 INT4 必須大於或等於-999999999 WHERE 子句中。 不論是否選取這個欄位包含值，將不會擷取 INT4 值小於-999999999 的資料列。  
  
-   SAP 系統 4.7 版或更新版本; 上執行時，會限制為 256 個字元的 WHERE 子句中的值的所有資料型別限制為在版本 4.6 c 的 70 個字元。 未經處理的資料類型值，這些限制會變成一半 128 到 35 個字元，以分別。 如此一來傳回時在 RAW 和 LCHR 資料類型長度上沒有任何限制。  
  
-   在 SAP R/3 4.6c，版本欄位的 where 子句限於 70 個字元。  
  
-   在 SAP R/3 4.6c 版本，無法擷取任何輸出長度大於 70 個字元的主索引鍵欄位的資料表。  
  
-   在 SAP R/3，版本 4.6 c，資料表和檢視表，包含可變長度資料類型 (`VARC`) 不支援，以及資料表和檢視包含不能從使用 Z_EXTRACT_DATA_OO 函式呼叫的資料來源中擷取這些資料類型。  
  
-   在檔案模式中，Z_EXTRACT_DATA_OO 函式呼叫不會檢查是否為目的地檔案已經開啟時，本身或其他應用程式。 因此，函式可以不正確地寫入開啟檔案時同時將資料附加到相同的檔案。 不會引發錯誤。  
  
-   在檔案模式中，Z_EXTRACT_DATA_OO 函式呼叫可覆寫現有檔案。 請確定使用 Z_EXTRACT_DATA_OO 的 SAP 使用者有限 S_DATASET 透過檔案系統存取。  
  
## <a name="security-considerations-with-the-custom-rfc"></a>自訂 rfc 的安全性考量  
  
-   `Security Issue`： 沒有可能公開 （expose） 如果您無法協助保護這些檔案會寫入至一般檔案的資料。  
  
     `Best practice`： 改進 Z_EXTRACT_DATA_OO 函式呼叫，在一般的檔案模式中的任何資料會寫入至其中的檔案共用的安全性。  
  
-   `Security Issue`： 沒有可能會覆寫任何會寫入至檔案模式中使用 Z_EXTRACT_DATA_OO 函式呼叫的共用上的檔案。 這可能會發生任何 SAP 網域帳戶有權存取的共用上的任何檔案。  
  
     `Best practice`： 致力於保護 SAP 網域帳戶有權存取的所有共用。  
  
-   `Security Issue`： 使用者能夠檢查 （或 「 探查 」） 資料從 SAP 應用程式伺服器到其目標檔案共用的傳輸期間在目標為不同的實體機器上時的情況下。  
  
     `Best practice`： 使用 IPsec 或另一個適當的方法來協助讓通訊更加安全 SAP 伺服器與目標之間。  
  
## <a name="see-also"></a>另請參閱  
 [關於 .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)