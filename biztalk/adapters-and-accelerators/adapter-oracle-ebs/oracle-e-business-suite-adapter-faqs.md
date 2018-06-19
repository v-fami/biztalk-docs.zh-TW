---
title: Oracle E-business Suite 配接器常見問題集 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4f7fe4e0-ddd5-402f-bbbc-b320850eaf3b
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d576fa5dae04a43daa54f2d99e7f9c14d1341e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218054"
---
# <a name="oracle-e-business-suite-adapter-faqs"></a>Oracle E-business Suite 配接器常見問題集
下列是一些常見問題集 (Faq) 與相關[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。 另請參閱[BizTalk Adapter Pack 的常見問題集](../../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.md)。
  

## <a name="how-can-i-use-the-oracle-e-business-adapter-to-communicate-with-oracle-e-business-suite"></a>如何使用 Oracle E-business 配接器與 Oracle E-business Suite 通訊？  
 您可以使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與 Oracle E-business Suite 可以開發 BizTalk 應用程式、 使用 WCF 服務模型或使用 WCF 通道模型進行通訊。 如需詳細資訊，請參閱[概觀的 BizTalk 配接器 for Oracle E-business Suite](http://msdn.microsoft.com/library/4f18fa2e-4e97-4c28-b38d-fc39ac53789e)。  
  
## <a name="what-interfaces-are-supported-by-the-oracle-e-business-adapter-for-retrieving-metadata"></a>Oracle E-business 配接器支援哪些介面來擷取中繼資料？  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援兩個介面來擷取中繼資料：  
  
-   WCF 提供的中繼資料交換。 WCF 提供的中繼資料交換端點所有 WCF 繫結，讓用戶端從 Oracle E-business Suite 中取得中繼資料。  
  
-   IMetadataRetrievalContract WCF LOB 配接器 SDK，可支援的中繼資料瀏覽和搜尋功能的配接器所提供。  
  
## <a name="how-does-the-adapter-connect-to-oracle-e-business-suite"></a>配接器如何連接到 Oracle E-business Suite 的資訊？  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] Oracle 用戶端會使用 Oracle 資料存取元件。 [支援部署 LOB 系統](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)列出用戶端版本。 若要連接到 Oracle E-business Suite，配接器用戶端必須提供連接字串，[連接統一資源識別元 (URI)](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)。 就內部而言，配接器會將連線 URI 對應至連接到 Oracle E-business Suite 中的基礎資料庫的連接字串。 請參閱[建立連接至 Oracle EBS](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)。  
  
## <a name="does-the-oracle-e-business-adapter-provide-a-secure-way-of-communicating-with-the-oracle-e-business-suite--are-there-any-best-practices-to-ensure-data-security"></a>Oracle E-business 配接器是否提供 Oracle E-business Suite 與通訊的安全的方式？  是否有任何最佳作法，以確保資料安全性？  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]企業單一登入 (SSO) 支援的驗證與 Oracle E-business Suite，它會建立連線。 SSO 使用資料庫和主要密碼來加密和儲存使用者認證。 它也提供將 Microsoft Windows 帳戶對應到第二個認證，可用來存取後端系統的服務。  
  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]也會要求您輸入使用者名稱和密碼的認證以連接到 Oracle E-business Suite 的資訊。 這些認證可用來驗證使用者，並因此提供的授權的連線層級。 Oracle E-business 配接器會提供多種方法，您可以透過此提供這些認證。 如需如何安全地提供 BizTalk 方案中的 Oracle 認證資訊，請參閱[使用配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-oracle-ebs/security-with-the-oracle-e-business-suite-adapter-and-biztalk-server.md)。 如需如何安全地提供程式設計的方案中的 Oracle 認證資訊，請參閱[安全使用 Oracle EBS 配接器程式設計](../../adapters-and-accelerators/adapter-oracle-ebs/secure-programming-with-the-oracle-ebs-adapter.md)。  
  
 如需詳細資訊：＜＞  
  
-   中的資料安全性[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[安全應用程式 Oracle EBS](../../adapters-and-accelerators/adapter-oracle-ebs/secure-your-oracle-ebs-applications.md)。  
  
-   最佳作法，以確保資料安全性的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[安全性最佳作法](../../adapters-and-accelerators/adapter-oracle-ebs/best-practices-to-secure-the-oracle-e-business-suite-adapter.md)。  
  
## <a name="is-there-a-gui-provided-by-the-oracle-e-business-adapter-to-view-and-perform-operations-on-the-artifacts-in-oracle-e-business-suite"></a>有 Oracle E-business 配接器所提供 GUI 來檢視和執行 Oracle E-business Suite 中的成品上的作業嗎？  
 使用配接器服務 BizTalk 專案增益集及加入配接器服務參考 Visual Studio 外掛程式提供的對話方塊，您可以在此檢視，並在 Oracle E-business Suite 成品上執行作業。 如需有關所提供的 GUI [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[瀏覽、 搜尋和 Oracle EBS 作業的 get 中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。  
  
## <a name="what-are-binding-properties-in-the-oracle-e-business-adapter-where-can-i-find-information-about-all-the-binding-properties-in-the-oracle-e-business-adapter"></a>什麼在 Oracle E-business 配接器繫結屬性？ 其中尋找 Oracle E-business 配接器中的所有繫結內容的相關資訊？  
 配接器用戶端可以使用繫結屬性[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]來設定和控制配接器的行為。 所有繫結內容的相關資訊顯示在[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[使用的繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
## <a name="what-are-inbound-and-outbound-operations-in-the-oracle-e-business-adapter"></a>在 Oracle E-business 配接器的輸入和輸出作業有哪些？  
 在輸入的操作，LOB 系統 (Oracle E-business Suite) 是用戶端而且配接器用戶端服務，其中交易源自 Oracle E-business Suite。 例如，在輪詢及通知的作業。  
  
 在輸出作業中，配接器用戶端的用戶端且 LOB 系統 (Oracle E-business Suite) 變得的服務，其中交易來自配接器用戶端。 比方說，插入、 選取、 更新和刪除作業介面資料表、 預存程序和函式上的作業，以及複合作業。  
  
## <a name="where-can-i-find-information-about-the-oracle-data-types-that-are-supported-in-the-oracle-e-business-adapter"></a>何處可以找到支援 Oracle E-business 配接器中的 Oracle 資料類型的相關資訊？  
 如需有關支援的 Oracle 資料類型資訊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[基本的 Oracle 資料型別](../../adapters-and-accelerators/adapter-oracle-ebs/basic-oracle-data-types2.md)。  
  
## <a name="what-is-applications-context-how-can-i-set-applications-context-for-various-oracle-artifacts-in-the-oracle-e-business-adapter"></a>什麼是應用程式內容？ 如何設定各種不同的 Oracle 成品的應用程式內容中 Oracle E-business 配接器？  
 如需應用程式內容，以及如何將它設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
## <a name="which-approach-biztalk-server-wcf-service-model-or-wcf-channel-model-can-i-use-to-perform-various-operations-using-the-oracle-e-business-adapter"></a>若要執行各種作業，使用 Oracle E-business 配接器可以使用哪種方法 （BizTalk Server、 WCF 服務模型或 WCF 通道模型）？  
 針對方法的相關資訊，您可以使用執行各種作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[開發應用程式 Oracle EBS](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)。  
  
## <a name="see-also"></a>另請參閱  
[BizTalk Adapter Pack 的常見問題](../../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.md)