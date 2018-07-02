---
title: 瀏覽、 搜尋及取得 Oracle 資料庫中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e67a1b1357798333cef8ccdd37074482fb06a29
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966127"
---
# <a name="browse-search-and-get-oracle-database-metadata"></a>瀏覽、 搜尋及取得 Oracle 資料庫中繼資料
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]介面從 Oracle 資料庫中，說明與使用配接器的 Oracle 資料庫通訊的訊息結構的中繼資料。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援兩個介面，來擷取中繼資料。  
  
- 所提供的 MetadataExchange [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。 WCF 提供的中繼資料交換端點的所有 WCF 繫結，可讓用戶端取得中繼資料從 Oracle 資料庫。  
  
- 所提供的 IMetadataRetrievalContract [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，其支援的中繼資料瀏覽和搜尋功能的介面卡。  
  
  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]表面的 Oracle 資料庫成品和配接器用戶端可以叫用的個別作業。 配接器也會提供諸如 SQLEXECUTE、 POLLINGSTMT 和通知作業，可用來執行的 Oracle 資料庫上的特定作業。 本主題稍後討論這些作業。  
  
  配接器用戶端可以瀏覽、 搜尋及擷取中繼資料，使用 WCF 通道模型、 使用 WCF 服務模型，或在 Visual Studio 中建立的 BizTalk 專案。 使用 WCF 服務模型時，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來產生 proxy 類別時執行的 Oracle 資料庫上的作業。 BizTalk 專案時，您必須使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生您想要的 Oracle 資料庫上執行作業的中繼資料。 如需有關瀏覽、 搜尋和擷取中繼資料使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或是[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，請參閱[取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)。  
  
## <a name="browsing-metadata"></a>瀏覽中繼資料  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]讓配接器用戶端來瀏覽資料庫資料表、 資料表檢視、 預存程序、 函數和 Oracle 資料庫中所提供的套件。 中繼資料瀏覽作業的一部分，配接器也會呈現可以包括配接器支援某些自訂作業的 Oracle 資料庫執行的作業。 這些作業都是從[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現下列作業：  
  
 **輸出的作業**  
  
 包含基礎的 Oracle 資料庫中的結構描述的清單。 展開結構描述節點，請參閱下列成品：  
  
- **資料表**： 結構描述中的所有資料表的清單。 選取資料表以檢視的 Insert、 Select、 Update 和 Delete 作業。  
  
- **程序**： 預存程序結構描述中公開為作業的清單。  
  
- **函式**： 結構描述中公開為作業的函式的清單。  
  
- **封裝**： 結構描述中的所有套件清單。 選取要檢視的程序和函式在套件內公開為作業的封裝。  
  
- **檢視**： 結構描述中的所有檢視的清單。 選取 [檢視] 來檢視的 Insert、 Select、 Update 和 Delete 作業。  
  
  此外，即使[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]也會公開**SQLEXECUTE**輸出作業，因為它可讓配接器用戶端執行的 Oracle 資料庫中的任何一般資料操作語言 (DML) 或預存程序。 當您選取根節點 （/），可使用 SQLEXECUTE 作業。 請注意，SQLEXECUTE 的輸出資料讀取器 （輸出為陣列的一般記錄） 的陣列。 如此一來，任何簡單的 out 參數不會顯示使用 SQLEXECUTE 作業。 如需作業的詳細資訊，請參閱[SQLEXECUTE 操作 Oracle 資料庫中](../../adapters-and-accelerators/adapter-oracle-database/sqlexecute-operation-in-oracle-database.md)。  
  
  **輸入的作業**  
  
  包含基礎的 Oracle 資料庫中的結構描述的清單。 展開結構描述節點，請參閱下列成品：  
  
- **程序**： 預存程序的清單結構描述中公開以進行輪詢的作業。  
  
- **函式**： 結構描述中公開以進行輪詢作業的函式的清單。  
  
- **封裝**： 結構描述中的封裝清單。 選取要檢視封裝的程序和函式以進行輪詢作業所公開的封裝。  
  
  此外，即使[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]也會公開**POLLINGSTMT**並**通知**輸入作業。 POLLINGSTMT 作業可讓配接器取得輸入的資料從 Oracle 資料庫查詢，輪詢配接器支援機制為基礎的用戶端。 通知作業可讓配接器用戶端註冊通知查詢的資料庫上的 SELECT 陳述式，資料庫在配接器用戶端，並在結果集的 SELECT 陳述式變更時，會將傳送通知。 當您選取根節點 （/），可使用 POLLINGSTMT 和通知的作業。 如需作業的詳細資訊，請參閱 <<c0> [ 支援的接收輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md).md) 和[接收資料庫變更器通知使用 Oracle 資料庫配接器的考量](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md).  
  
  如需有關如何分類中繼資料的詳細資訊，請參閱[中繼資料節點識別碼](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md)。  
  
## <a name="searching-metadata"></a>搜尋中繼資料  
 使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，就可以執行的 Oracle 資料庫上的搜尋查詢，使用 LIKE 運算子與相容的 Oracle 搜尋運算式。 例如，配接器用戶端可以使用搜尋運算式，例如"EMP %"以取得開頭為 EMP 資料表。 配接器會將此轉換成下列 SQL 查詢：  
  
```  
SELECT TABLE_NAME FROM ALL_TABLES WHERE TABLE_NAME LIKE 'EMP%' AND OWNER = 'SCOTT'  
```  
  
 其中，SCOTT 會是 Oracle 資料庫成品集合與結構描述。  
  
 下表列出可用來搜尋和其解譯的特殊字元[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|_ (底線)|完全符合一個字元<br /><br /> 比方說，A_ 比對 AB、 AC、 AD。|  
|%（百分比）|比對零或多個字元。<br /><br /> 例如，%比對的 AB，ABC。|  
|\ （逸出）|逸出的特殊意義的 %和 _<br /><br /> 例如，A\\_km 符合 A_B。|  
  
> [!IMPORTANT]
>  中繼資料搜尋範圍僅限於在其中執行搜尋作業的節點下的層級。 例如，若要搜尋函式，您必須搜尋下\\[Schema] \Functions。 不支援遞迴搜尋。  
  
## <a name="retrieving-metadata"></a>擷取中繼資料  
 擷取中繼資料時[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可以擷取在結構描述，包括所有的中繼資料，或使用個別的物件和作業參數物件的資料庫的子集。 配接器會顯示從 Oracle 資料庫的實體當做 XML 中的項目名稱。 因為底線是只允許可以包含特殊字元，使用底線編碼中的項目名稱的其他所有特殊字元。 例如，`emp$name`編碼為`emp_x0024_name`。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle Database 的概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)   
 [了解 BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)   
[取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)