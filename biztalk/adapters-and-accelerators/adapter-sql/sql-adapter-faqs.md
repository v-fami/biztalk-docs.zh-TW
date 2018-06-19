---
title: SQL 配接器常見問題集 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 25369e6b-d1f2-4abc-9ffc-4cb9aef1d3fb
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9dee4b402e548f55dd8eab4583215d879c98186b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224862"
---
# <a name="sql-adapter-faqs"></a>SQL 配接器常見問題集
下列是一些常見問題集 (Faq) 與相關[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]和[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]一般。  
  
## <a name="how-can-i-use-the-sql-adapter-to-communicate-with-the-sql-server-database"></a>如何使用 SQL 配接器與 SQL Server 資料庫通訊？  
 您可以使用 SQL 配接器與 SQL Server 資料庫可以開發 BizTalk 應用程式、 使用 WCF 服務模型或使用 WCF 通道模型進行通訊。 如需詳細資訊，請參閱[概觀的 BizTalk 配接器適用於 SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)。  
  
## <a name="what-interfaces-are-supported-by-the-sql-adapter-for-retrieving-metadata"></a>SQL 配接器支援哪些介面來擷取中繼資料？  
 SQL 配接器支援兩個介面來擷取中繼資料：  
  
-   WCF 提供的中繼資料交換。 WCF 提供的中繼資料交換端點所有 WCF 繫結，讓用戶端都可以從 SQL Server 資料庫取得中繼資料。  
  
-   IMetadataRetrievalContract WCF LOB 配接器 SDK，可支援的中繼資料瀏覽和搜尋功能的配接器所提供。  
  
## <a name="how-does-the-sql-adapter-support-high-availability-of-data"></a>SQL 配接器如何支援資料的高可用性？  
 指定同時[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)若要連接到 SQL Server 資料庫，SQL 配接器可讓您指定要連接至如果主要的 SQL Server 資料庫的容錯移轉 SQL Server 資料庫的名稱不是可以使用。 使用中的選擇性參數，FailoverPartner，連線 URI，指定容錯移轉 SQL Server 資料庫。  
  
## <a name="can-i-migrate-biztalk-projects-created-using-the-previous-version-of-the-sql-adapter-to-use-the-wcf-based-sql-adapter-how"></a>可以移轉使用舊版的 SQL 配接器使用 WCF 架構的 SQL 配接器所建立的 BizTalk 專案嗎？ 如何？  
 是的。 若要了解使用舊版的 SQL 配接器使用 WCF 架構的 SQL 配接器所建立的 BizTalk 專案移轉的步驟，請參閱[SQL 配接器教學課程](../../adapters-and-accelerators/adapter-sql/sql-adapter-tutorials.md)。  
  
## <a name="does-the-sql-adapter-provide-a-secure-way-of-communicating-with-the-sql-server-database--are-there-any-best-practices-to-ensure-security-of-data"></a>SQL 配接器是否提供與 SQL Server 資料庫通訊的安全方式？  是否有任何最佳作法，以確保資料的安全性？  
 SQL 配接器支援企業單一登入 (SSO) 和整合式安全性進行驗證，它會建立與 SQL Server 資料庫的連接上。 使用 SSO，這些認證會加密並儲存在登錄中。 系統會使用這些認證，來決定存取權限，而不需要使用者輸入，可能會看到它們由未經授權的動作項目。 整合式的安全性以存取 SQL server 使用登入的使用者的認證。 這也就不需要使用者輸入認證。 資料庫管理員必須設定 SQL 接受使用者的認證為整合式安全性，才能正確運作。  
  
 SQL 配接器也不允許您輸入時加入配接器服務參考 Visual Studio 外掛程式和使用配接器服務 BizTalk 專案增益集以避免 SQL Server 資料庫連線 URI 中的使用者認證出現在純文字認證。 此外，密碼不會寫入至組態檔 （由 新增配接器服務參考 Visual Studio 外掛程式所產生），繫結檔案 （使用配接器服務 BizTalk 專案增益集所產生）。  
  
 如需詳細資訊：  
  
-   中的資料安全性[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[安全 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)。  
  
-   最佳作法，以確保資料安全性的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[最佳作法來保護 SQL 配接器](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)。  
  
## <a name="is-there-a-gui-provided-by-the-sql-adapter-to-view-and-perform-operations-on-the-artifacts-in-my-underlying-sql-server-database"></a>是否有 SQL 配接器所提供 GUI 來檢視，並在基礎 SQL Server 資料庫上的成品執行作業？  
 使用配接器服務 BizTalk 專案增益集及加入配接器服務參考 Visual Studio 外掛程式提供的對話方塊，您可以在此檢視，並在基礎 SQL Server 資料庫上的成品執行作業。 如需有關 SQL 配接器所提供的 GUI 的詳細資訊，請參閱[瀏覽、 搜尋和使用 SQL 配接器的 SQL 作業的 get 中繼資料](../../adapters-and-accelerators/adapter-sql/browse-search-and-get-metadata-for-sql-operations-using-the-sql-adapter.md)。  
  
## <a name="what-are-binding-properties-in-the-sql-adapter-where-can-i-find-information-about-all-the-binding-properties-in-sql-adapter"></a>什麼 SQL 配接器中的繫結屬性？ 其中找到 SQL 配接器中的所有繫結內容的相關資訊？  
 配接器用戶端可以使用繫結屬性[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]來設定和控制配接器的行為。 所有繫結內容的相關資訊顯示在[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
## <a name="what-is-msdtc-do-i-need-to-bother-about-it-before-using-sql-adapter"></a>MSDTC 是什麼？ 需要使用 SQL 配接器之前理會嗎？  
 MSDTC 代表 Microsoft 分散式交易協調器。 MSDTC 協調多個資源管理員，例如資料庫、 檔案系統和訊息佇列之間的不同交易。 若要使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須啟用 MSDTC。 如需設定 MSDTC 的詳細資訊，請參閱[設定 SQL Server 和配接器的用戶端上的 MSDTC](../../adapters-and-accelerators/adapter-sql/configure-msdtc-on-sql-server-and-adapter-client.md)。  
  
## <a name="where-can-i-find-information-about-the-sql-server-data-types-that-are-supported-in-the-sql-adapter"></a>何處可以找到 SQL 配接器支援的 SQL Server 資料類型的相關資訊？  
 若要了解 SQL Server 資料類型所支援的 SQL 配接器，請參閱[基本的 SQL Server 資料類型](../../adapters-and-accelerators/adapter-sql/basic-sql-server-data-types.md)。  
  
## <a name="which-approach-biztalk-server-wcf-service-model-or-wcf-channel-model-can-i-use-to-perform-various-operations-using-the-sql-adapter"></a>若要執行各種作業，使用 SQL 配接器可以使用哪種方法 （BizTalk Server、 WCF 服務模型或 WCF 通道模型）？  
 若要了解您可用來執行各種作業，使用 SQL 配接器的方法，請參閱[開發應用程式 SQL](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)。  
  
 
## <a name="see-also"></a>另請參閱  
 [常見問題集](../../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.md)
 