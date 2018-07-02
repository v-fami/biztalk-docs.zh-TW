---
title: 瀏覽、 搜尋及取得 Oracle E-business Suite 中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b516c6e9-dbb3-4977-bb27-aa039e021912
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28a22fa00b859a6ee44505a008b2c1912097a568
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976303"
---
# <a name="browse-search-and-get-oracle-e-business-suite-metadata"></a>瀏覽、 搜尋及取得 Oracle E-business Suite 中繼資料
中繼資料， [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] Oracle E-business Suite 與基礎的 Oracle 資料庫的介面描述與 Oracle E-business Suite 使用配接器通訊的訊息結構。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援兩個介面，來擷取中繼資料。  
  
- 所提供的 MetadataExchange [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。 WCF 提供的中繼資料交換端點的所有 WCF 繫結，讓從 Oracle E-business Suite 取得中繼資料的用戶端。  
  
- 所提供的 IMetadataRetrievalContract [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，其支援的中繼資料瀏覽和搜尋功能的介面卡。  
  
  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]瀏覽 Oracle E-business Suite 的基礎資料庫成品和配接器用戶端可以叫用的個別作業。 本主題稍後討論這些作業。  
  
  您可以使用配接器用戶端來瀏覽、 搜尋及擷取中繼資料：  
  
- 在 Visual Studio 中建立的 BizTalk 專案  
  
- 使用 WCF 通道模型  
  
- 使用 WCF 服務模型  
  
  BizTalk 專案時，您必須使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生您想要執行 Oracle E-business Suite 中作業的中繼資料。 使用 WCF 服務模型時，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 proxy 類別，針對執行 Oracle E-business Suite 中的作業。 如需有關瀏覽、 搜尋和擷取中繼資料使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或是[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[取得 Visual Studio 中的 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)。  
  
## <a name="browsing-metadata"></a>瀏覽中繼資料  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器用戶端瀏覽介面資料表、 介面檢視、 同時執行的程式，並要求中 Oracle E-business Suite 和資料表、 檢視、 預存程序、 函式和基礎資料庫中的套件集。 中繼資料瀏覽作業的一部分，配接器也會呈現可以包括配接器支援某些自訂作業的 Oracle 資料庫執行的作業。 這些作業都是從[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]呈現的大部分作業下的下列三個節點：  
  
1. **應用程式為基礎的檢視**： 包含每個應用程式的 Oracle E-business Suite 成品分組的作業。  
  
2. **成品的檢視形式**： 包含依 Oracle E-business Suite 和基礎資料庫中的成品類型 （例如介面資料表、 介面檢視等等） 的作業。  
  
3. **結構描述為基礎的檢視**： 包含依每個結構描述為基礎的資料庫成品的作業。  
  
   有根層級公開一些適用於這兩個節點的一般作業。 此外，不同的作業會顯示作業的類型為基礎： 傳出或傳入。  
  
   下表列出由顯示的傳出和傳入作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]:  
  
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            輸出的作業                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                                                                                                                                                     輸入的作業                                                                                                                                                                                                                                                                                                                                                                      |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **應用程式為基礎的檢視**:<br /><br /> 包含一份基礎 Oracle E-business Suite 中的 Oracle 應用程式。 展開 Oracle 應用程式節點，以查看下列成品：<br /><br /> <ul><li>**介面資料表**： 介面的所有資料表的清單。 選取的介面資料表，以檢視的 Insert、 Select、 Update 和 Delete 作業。</li><li>**介面檢視**： 所有介面檢視的清單。 選取介面檢視來檢視選取的作業。</li><li>**並行程式**： 並行程式執行下列作業：<br /><br /> <ul><li>所有的並行程式 Oracle 應用程式特定的公開為作業的一組。</li><li>Get_Status 的作業，以取得在並行程式的狀態。</li><li>要等候的要求完成，才傳回狀態的 Wait_For_Request 作業。</li><li>若要呼叫或藉由指定的並行處理程式執行所需的參數執行並行處理程式 Submit_Request 作業。</li></ul></li><li>**要求集**： 所有要求的一組設定 Oracle 應用程式特定的公開為作業。</li></ul> |                                                 **應用程式為基礎的檢視**:<br /><br /> 包含一份基礎 Oracle E-business Suite 中的 Oracle 應用程式。 展開 Oracle 應用程式節點，以查看下列成品：<br /><br /> -   **介面資料表**： 配接器支援查詢輪詢機制為基礎的介面資料表輪詢作業可取得輸入的資料從 Oracle E-business Suite 配接器用戶端。<br />-   **介面檢視**： 配接器支援查詢輪詢機制為基礎的介面檢視的輪詢作業可取得輸入的資料從 Oracle E-business Suite 配接器用戶端。                                                  |
|                                                                                                                                                                                                                                                                    **成品的檢視形式**:<br /><br /> 包含 Oracle E-business Suite 和基礎資料庫中的所有成品。 展開的成品節點，請參閱 Oracle 應用程式或根據成品 （應用程式或資料庫） 的來源結構描述的清單。 例如， **Interface Table**節點會顯示一份 Oracle 應用程式，而**資料表**節點會顯示資料庫結構描述的清單。<br /><br /> **成品的檢視形式**顯示底下所列的成品**應用程式為基礎的檢視**並**結構描述為基礎的檢視**。 每個成品節點會列出 Oracle 應用程式或資料庫結構描述相關的作業。                                                                                                                                                                                                                                                                     |            **成品的檢視形式**:<br /><br /> 同時執行的程式和要求集，除了包含 Oracle E-business Suite 中的所有成品和基礎資料庫中的所有成品。 展開的成品節點，請參閱 Oracle 應用程式或根據成品 （應用程式或資料庫） 的來源結構描述的清單。 例如， **Interface Table**節點會顯示一份 Oracle 應用程式，而**資料表**節點會顯示資料庫結構描述的清單。<br /><br /> **成品的檢視形式**顯示底下所列的成品**應用程式為基礎的檢視**並**結構描述為基礎的檢視**。 每個成品節點會列出 Oracle 應用程式或資料庫結構描述相關的作業。             |
|                                                                                                                                                                                                                                       **結構描述為基礎的檢視**:<br /><br /> 包含基礎的 Oracle 資料庫中的結構描述的清單。 展開結構描述節點，查看下列成品：<br /><br /> -   **PL/SQL Api**： 一份所有 PL/SQL Api。 選取的 PL/SQL API 來檢視封裝的程序和函式公開為作業。<br />-   **程序**： 結構描述中公開為作業的程序的清單。<br />-   **函式**： 結構描述中公開為作業的函式的清單。<br />-   **資料表**： 所有資料表的清單。 選取資料表以檢視的 Insert、 Select、 Update 和 Delete 作業。<br />-   **檢視**： 一份所有檢視。 選取 [檢視] 來檢視選取的作業。                                                                                                                                                                                                                                       | **結構描述為基礎的檢視**:<br /><br /> 包含基礎的 Oracle 資料庫中的結構描述的清單。 展開結構描述節點，查看下列成品：<br /><br /> -   **PL/SQL Api**： 一份所有 PL/SQL Api。 選取的 PL/SQL API 來檢視封裝的程序和函式公開以進行輪詢的作業。<br />-   **程序**： 結構描述中公開以進行輪詢作業的程序的清單。<br />-   **函式**： 結構描述中公開以進行輪詢作業的函式的清單。<br />-   **資料表**： 所有資料表的清單。 選取要檢視資料表輪詢作業的資料表。<br />-   **檢視**： 一份所有檢視。 選取要檢視輪詢作業檢視的檢視。 |
|                                                                                                                                                                                                                                                                                                                                                              [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]也會公開下列泛型輸出作業的根層級： ExecuteReader、 ExecuteScalar 和 ExecuteNonQuery。 如需這些作業的資訊，請參閱[支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。                                                                                                                                                                                                                                                                                                                                                               |                                                                                                             [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]也會公開在根層級，可讓從 Oracle E-business Suite 接收資料庫變更通知訊息的配接器用戶端通知作業。 如需通知作業的詳細資訊，請參閱[接收資料庫變更通知的考量](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)。                                                                                                             |
  
 如需有關如何分類中繼資料的詳細資訊，請參閱[瀏覽、 搜尋及擷取 Oracle E-business 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。  
  
## <a name="searching-metadata"></a>搜尋中繼資料  
 使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您可以執行 Oracle E-business Suite 中的搜尋查詢，然後使用 Oracle 的基礎 Oracle 資料庫上搜尋 相容與 LIKE 運算子的運算式。 例如，配接器用戶端可以使用搜尋運算式，例如"EMP %"以取得開頭為 EMP 資料表。 配接器會將此轉換成下列 SQL 查詢：  
  
```  
SELECT TABLE_NAME FROM ALL_TABLES WHERE TABLE_NAME LIKE 'EMP%' AND OWNER = 'SCOTT'  
```  
  
 其中，SCOTT 會是 Oracle 資料庫成品集合與結構描述。  
  
 下表列出可用來搜尋和其解譯的特殊字元[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|_ (底線)|完全符合一個字元<br /><br /> 比方說，A_ 比對 AB、 AC 和廣告。|  
|%（百分比）|比對零或多個字元。<br /><br /> 例如，%比對的 AB，ABC。|  
|\ （逸出）|逸出 %和 _ 的特殊的意義。 \ （逸出） 字元是萬用字元之前用來指示萬用字元的字元應該解譯成正規字元。<br /><br /> 例如，A\\_km 符合 A_B。|  
  
> [!IMPORTANT]
> - 搜尋字串會區分大小寫。  
>   -   搜尋以不同的檢視 （應用程式為基礎的檢視、 成品為基礎的檢視和結構描述為基礎的檢視） 的運作方式。 若要知道如何您可以搜尋成品和每個檢視底下的作業，請參閱 < 在不同的檢視搜尋 > 中[搜尋 Oracle E-business Suite 作業](../../adapters-and-accelerators/adapter-oracle-ebs/search-for-oracle-e-business-suite-operations.md)。  
>   -   若要搜尋應用程式中，您可以指定好記的名稱或應用程式的簡短名稱。 例如，若要搜尋**應收帳款**應用程式，您可以為指定搜尋字串**接收 %** 或是**AR**。 AR 是應用程式的簡短名稱。  
>   -   要搜尋的並行程式中，您可以指定好記的名稱或並行處理程式的實際名稱。 例如，若要搜尋**客戶介面**並行處理程式，您可以為指定的搜尋字串**客戶介面 %** 或是**RACUST %**。 RACUST 是並行處理程式的實際名稱。 此外，搜尋結果永遠包含標準的並行程式，不論其名稱是否符合指定的搜尋字串。  
  
## <a name="retrieving-metadata"></a>擷取中繼資料  
 擷取中繼資料時[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可以擷取在結構描述，包括所有的中繼資料，或使用個別的物件和作業參數物件的資料庫的子集。 配接器會顯示實體從 Oracle E-business Suite 和基礎的 Oracle 資料庫當做 XML 中的項目名稱。 因為底線是只允許可以包含特殊字元，使用底線編碼中的項目名稱的其他所有特殊字元。 例如，`emp$name`編碼為`emp_x0024_name`。 如需詳細資訊，請參閱 <<c0> [ 取得 Visual Studio 中使用 SQL 配接器中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk Adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)   
 [瀏覽、 搜尋和擷取 Oracle E-business 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)   
 [取得 Visual Studio 中的 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)