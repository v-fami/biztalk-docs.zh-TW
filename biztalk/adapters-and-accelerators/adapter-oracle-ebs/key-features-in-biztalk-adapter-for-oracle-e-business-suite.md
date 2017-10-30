---
title: "金鑰功能在 BizTalk adapter for Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a43091ab-f81c-4c4f-bcc3-e6abe16d3d77
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d89da490f604e50924544e54cb5ffe7018a8724e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="key-features-in-biztalk-adapter-for-oracle-e-business-suite"></a>BizTalk adapter for Oracle E-business Suite 中的重要功能
此區段會列出中的主要功能[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。  
  
## <a name="technology-related-features"></a>技術相關功能  
  
|功能|註解|  
|-------------|-------------|  
|Windows Communication Foundation (WCF) 的使用|[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]建置最上層的[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] ([!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)])。 接著，[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]建置於 WCF 之上。 配接器會公開為 WCF 配接器用戶端的通道。 這可讓連線、 中繼資料交換和商務資料交換與外部系統。|  
|WCF 通道模型和 WCF 服務模型的支援|在 WCF*通道*配接器用戶端可以取用模型[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]透過直接傳送和接收 XML 訊息。<br /><br /> 在 WCF*服務*模型中，配接器用戶端可以產生.NET proxy 類別，從 Web 服務描述語言 (WSDL) 使用取得[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。|  
|ODP.NET 的使用|[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用 Oracle 資料提供者與 Oracle E-business Suite 介面的.NET (ODP.NET)。|  
|兩種方式連接到 Oracle E-business Suite 的|配接器用戶端可以連線至 Oracle E-business Suite tnsnames.ora 檔案中使用的網路服務名稱或直接指定連線參數，並因此不需要使用網路服務名稱或 tnsnames.ora 檔案。 不需要連接到 Oracle E-business Suite tnsnames.ora 檔案時，儲存您從之類的手動更新 連接參數 (net service name) tnsnames.ora 檔案，每個用戶端電腦上加入或更新中的 Oracle 伺服器程式環境。 如需詳細資訊，請參閱[設定連接到 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md)。|  
|支援 Windows 驗證|配接器用戶端可以使用 Windows 驗證來連接到 Oracle E-business Suite。 Windows 驗證可讓您判斷使用者的身分識別為基礎的 Windows 登入認證，並因此可協助您利用內建安全性的 Windows 環境。 如需有關在 Windows 驗證[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[連接到 Oracle E-business Suite Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)。|  
|支援使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與 Microsoft Office SharePoint Server (MOSS)|您可以使用配接器從 Oracle E-business Suite，MOSS 入口網站上呈現資料。 如需詳細資訊，請參閱[Oracle E-business 配接器使用 Microsoft Office SharePoint Server](https://msdn.microsoft.com/library/dd788485.aspx)。|  
  
## <a name="metadata-related-features"></a>中繼資料相關功能  
  
|功能|註解|  
|-------------|-------------|  
|批次擷取中繼資料|配接器用戶端可以瀏覽和搜尋 Oracle E-business Suite 和基礎資料庫所公開的所有成品的中繼資料。 成品會顯示根據連接的使用者認證，而是：<br /><br /> 每個 Oracle E-business Suite 成品的應用程式群組。<br />-依每個 Oracle E-business Suite 和基礎資料庫中的成品分組。<br />-依每個結構描述為基礎的資料庫成品分組。|  
  
## <a name="performance-related-features"></a>效能相關的功能  
  
|功能|註解|  
|-------------|-------------|  
|連接共用|[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓用戶端使用 ODP.NET 連接共用藉由設定**UseOracleConnectionPool**繫結屬性。 如需此繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。|  
|快取管理|[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓用戶端設定使用 ODP.NET 快取管理**StatementCachePurge**和**StatementCacheSize**繫結屬性。 如需此繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。|  
|對效能計數器支援|[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]以供配接器用戶端支援以 WCF 為基礎的效能計數器。 如需有關效能計數器的詳細資訊，請參閱[使用 SQL 配接器的效能計數器](../../adapters-and-accelerators/adapter-sql/use-performance-counters-with-the-sql-adapter.md)。|  
  
## <a name="operations-related-features"></a>與作業相關的功能  
  
|功能|註解|  
|-------------|-------------|  
|支援介面資料表和檢視介面上的作業|配接器用戶端可以執行基本 Insert、 Update、 Delete 和 Oracle E-business Suite 介面資料表上的 Select 作業。 只可以 Oracle E-business Suite 介面檢視上執行選取的作業。|  
|執行 PL/SQL Api 的支援|配接器用戶端可以執行 Oracle E-business Suite 中的 PL/SQL 應用程式開發介面。 PL/SQL 應用程式開發介面包含預存程序和函式在封裝內。|  
|支援執行並行程式|Oracle E-business Suite 中，配接器用戶端可以執行同時執行的程式。|  
|執行要求的支援|配接器用戶端可以執行 Oracle E-business Suite 中的要求。 要求組是一組並行程式，並可用來執行數個並行程式包含預先定義的參數。 階段中執行的要求。 如需要求設定的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=129539](http://go.microsoft.com/fwlink/?LinkId=129539)。|  
|支援用於插入作業中指定內嵌的值|您可以使用**InlineValue**插入作業，將計算的值插入介面資料表與 Oracle 中的資料庫資料表中的屬性。 這是選擇性的屬性，可用於插入作業中的所有簡單資料記錄。 如果您指定這個屬性的值，它會覆寫某筆記錄指定的值。 如需 InlineValue 屬性的詳細資訊，請參閱[介面資料表和檢視介面上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)。|  
|使用輪詢進行傳入呼叫時的支援|[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收 「 輪詢基礎 」 的資料變更的訊息指定的 SQL 陳述式、 預存程序、 函數或在封裝中，程序，於其中執行配接器支援擷取資料，並提供用戶端的結果。|  
|叫用函數和程序支援|函式和基礎的 Oracle 資料庫中的程序，可以叫用配接器用戶端。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]呈現函數和程序為基礎的 Oracle 資料庫可以執行的作業。|  
|複合作業的支援|[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器執行複合操作 Oracle E-business Suite 中的用戶端。 複合作業可以包含任意數目的下列作業，並以任何順序：<br /><br /> 介面資料表、 介面檢視、 資料表和檢視表上作業。<br />預存程序、 函數和程序，便會顯示封裝內做為配接器中的作業。|  
|執行任意的 SQL 陳述式區塊 PL/SQL 的支援|[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]讓配接器用戶端可以執行任意的 SQL 陳述式或使用 ExecuteReader、 ExecuteScalar 和 ExecuteNonQuery 作業的 PL/SQL 區塊。 如需有關這些作業的詳細資訊，請參閱[ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業支援](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。|  
|使用者定義型別 (Udt)、 布林值參數，以及支援 PL/SQL 資料表類型|配接器用戶端可以支援成品包含 Udt 中的作業和作業的預存程序和函數，其中包含布林值參數和 PL/SQL 資料表類型。 如需 UDT 的支援資訊，請參閱[支援 Oracle User-Defined 類型](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-oracle-user-defined-types2.md)。|  
|支援的輸入和輸出 REF CURSOR|配接器用戶端可以使用輸入和輸出的 REF CURSOR 程序和函式上操作。|  
|PL/SQL 記錄資料類型的支援|配接器用戶端可以使用記錄和預存程序和函式中的巢狀的記錄類型操作。|  
|支援多載函式和 PL/SQL API 中的程序|多載函式和 PL/SQL 應用程式開發介面中的程序，可以叫用配接器用戶端。 不過，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援使用強型別和弱式類型的 REF CURSOR 的多載程序使用。 就內部而言，配接器會將這兩個強型別和弱型別 REF 資料指標視為只 REF CURSOR。|  
|資料庫變更通知的支援|配接器用戶端可以接收來自根據觸發的 SELECT 陳述式的 Oracle 資料庫的資料庫變更通知。 通知會傳送 Oracle 資料庫配接器用戶端，以及當結果集的 SELECT 陳述式變更。 如需資料庫的變更通知的詳細資訊，請參閱[接收資料庫變更通知使用 ORacle 資料庫配接器的考量](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)。|  
|支援的同義字|配接器用戶端可以執行在針對資料表、 檢視、 預存程序、 函數和封裝建立的同義字上的作業。 如需有關同義字，以及您可以使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]執行在同義字上的作業，請參閱[同義字上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-synonyms2.md)。|  
  
## <a name="other-features"></a>其他功能  
  
|功能|註解|  
|-------------|-------------|  
|多語言支援 (MLS)|配接器用戶端可以使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]Oracle E-business Suite 和基礎資料庫具有多個語言套件安裝於執行作業。 這表示配接器用戶端可以執行的作業資料，以多種語言。 例如，您可以當地語系化 （非英文） 的資料檢視中檢視介面，或在資料表中插入當地語系化的資料。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援最多基礎 Oracle E-business Suite 安裝所支援的語言。<br /><br /> [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開**MlsSettings**繫結屬性可設定多個語言的支援功能。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。|  
  
## <a name="see-also"></a>另請參閱  
 [瞭解 BizTalk Adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)