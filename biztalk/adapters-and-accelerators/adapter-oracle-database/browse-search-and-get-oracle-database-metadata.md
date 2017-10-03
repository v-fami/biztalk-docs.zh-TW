---
title: "瀏覽、 搜尋及取得 Oracle 資料庫中繼資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MetadataExchange
- metadata, searching
- metadata, browsing
- POLLINGSTMT
- metadata, retrieving
- IMetadataRetrievalContract
- SQLEXECUTE
ms.assetid: 828d5a8e-f0a3-47b4-8298-5571cff64b52
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 765663d51fa1bab4f700aa3aff726085e5464716
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="browse-search-and-get-oracle-database-metadata"></a>瀏覽、 搜尋及取得 Oracle 資料庫中繼資料
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]介面中繼資料從 Oracle 資料庫與 Oracle 資料庫使用配接器通訊的訊息結構的描述。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援兩個介面來擷取中繼資料。  
  
-   所提供的中繼資料交換[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。 WCF 提供的中繼資料交換端點所有 WCF 繫結，讓用戶端從 Oracle 資料庫中取得中繼資料。  
  
-   所提供的 IMetadataRetrievalContract [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，可支援瀏覽和搜尋功能的介面卡的中繼資料。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]介面 Oracle 資料庫成品和配接器用戶端可以叫用的個別作業。 配接器也會提供諸如 SQLEXECUTE、 POLLINGSTMT 和通知作業可以用來執行的 Oracle 資料庫上的特定作業。 本主題稍後會討論這些作業。  
  
 配接器用戶端可以瀏覽、 搜尋及擷取中繼資料，藉由使用 WCF 通道模型，使用 WCF 服務模型，或在 Visual Studio 中建立的 BizTalk 專案。 使用 WCF 服務模型時，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 proxy 類別，對 Oracle 資料庫執行作業。 當使用 BizTalk 專案時，您必須使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生您想要在 Oracle 資料庫上執行作業的中繼資料。 如需有關瀏覽、 搜尋和擷取中繼資料使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，請參閱[取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)。  
  
## <a name="browsing-metadata"></a>瀏覽中繼資料  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]讓配接器用戶端來瀏覽資料庫資料表、 資料表檢視、 預存程序、 函數和 Oracle 資料庫中所提供的封裝。 中繼資料瀏覽作業的一部分，配接器也會提供諸如一概無法對 Oracle 資料庫中，包括配接器支援某些自訂作業的作業。 這些作業都是從[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現下列作業：  
  
 **輸出作業**  
  
 包含基礎的 Oracle 資料庫中的結構描述的清單。 展開結構描述 節點，請參閱下列成品：  
  
-   **資料表**： 結構描述中的所有資料表的清單。 選取資料表以檢視 Insert、 Select、 Update 和 Delete 作業。  
  
-   **程序**： 預存程序結構描述中公開為作業的清單。  
  
-   **函式**： 結構描述中公開為作業的函式的清單。  
  
-   **封裝**： 結構描述中的所有封裝的清單。 選取要檢視的程序和函數封裝內公開為作業的封裝。  
  
-   **檢視**： 結構描述中的所有檢視的清單。 選取檢視，以檢視 Insert、 Select、 Update 和 Delete 作業。  
  
 此外，即使[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]也會公開**SQLEXECUTE**可讓配接器在 Oracle 資料庫中執行的任何一般資料操作語言 (DML) 或預存程序的用戶端的輸出作業。 當您選取根節點 （/） 時使用 SQLEXECUTE 操作。 請注意，SQLEXECUTE 的輸出資料讀取器 （以陣列的一般記錄輸出） 的陣列。 如此一來，任何簡單的 out 參數不會顯示使用 SQLEXECUTE 操作。 如需作業的詳細資訊，請參閱[SQLEXECUTE 操作 Oracle 資料庫中](../../adapters-and-accelerators/adapter-oracle-database/sqlexecute-operation-in-oracle-database.md)。  
  
 **輸入的作業**  
  
 包含基礎的 Oracle 資料庫中的結構描述的清單。 展開結構描述 節點，請參閱下列成品：  
  
-   **程序**： 預存程序結構描述中公開為輪詢作業的清單。  
  
-   **函式**： 結構描述中公開為輪詢作業的函式的清單。  
  
-   **封裝**： 結構描述中的封裝清單。 選取要檢視的已封裝的程序和函式公開為輪詢作業的封裝。  
  
 此外，即使[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]也會公開**POLLINGSTMT**和**通知**輸入作業。 POLLINGSTMT 作業可讓配接器取得輸入的資料從 Oracle 資料庫輪詢機制配接器支援的查詢為基礎的用戶端。 通知作業可讓配接器的用戶端註冊通知查詢在資料庫上的 SELECT 陳述式，資料庫將通知傳送給配接器用戶端，並在結果集的 SELECT 陳述式變更時。 當您選取根節點 （/），可使用 POLLINGSTMT 和通知的作業。 如需作業的詳細資訊，請參閱[支援接收輪詢基礎資料變更的訊息](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md).md) 和[接收資料庫交換器通知使用 Oracle 資料庫配接器的考量](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md).  
  
 如需中繼資料的分類方式的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md)。  
  
## <a name="searching-metadata"></a>搜尋中繼資料  
 與[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，很可能在 Oracle 資料庫上執行搜尋查詢，使用 LIKE 運算子與相容的 Oracle 搜尋運算式。 例如，配接器用戶端可以使用搜尋的運算式，例如"EMP %"以取得開頭為 EMP 的資料表。 配接器會將此轉換下列 SQL 查詢：  
  
```  
SELECT TABLE_NAME FROM ALL_TABLES WHERE TABLE_NAME LIKE 'EMP%' AND OWNER = 'SCOTT'  
```  
  
 其中，SCOTT 會是 Oracle 資料庫成品集合與結構描述。  
  
 下表列出可用於搜尋和由其解譯的特殊字元[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|_ (底線)|完全符合一個字元<br /><br /> 例如，A_ 比對 AB、 AC、 AD。|  
|%（百分比）|比對零個或多個字元。<br /><br /> 例如，%比對 A，AB，ABC。|  
|\ （逸出）|逸出的特殊意義的 %和 _<br /><br /> 例如，A\\_km 符合 A_B。|  
  
> [!IMPORTANT]
>  在中繼資料的搜尋範圍僅限於正下方的節點，在其中執行搜尋作業層級。 例如，若要搜尋的函式，您必須搜尋下\\[Schema] \Functions。 不支援遞迴搜尋。  
  
## <a name="retrieving-metadata"></a>擷取中繼資料  
 擷取中繼資料時[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可以擷取下的結構描述，包括所有的中繼資料，或使用個別的物件和作業的參數物件的資料庫子集。 配接器會顯示從 Oracle 資料庫的實體當做 XML 中的項目名稱。 因為底線是只允許可以包含特殊字元，是使用底線來編碼所有其他特殊字元的元素名稱。 例如，`emp$name`編碼為`emp_x0024_name`。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle 資料庫的概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)   
 [瞭解 BizTalk Adapter for Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)   
[取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)