---
title: Oracle E-business Suite 配接器常見問題集 |Microsoft Docs
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
ms.openlocfilehash: 496c18236c8c6a3fa02971cd17a9263e03167571
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007047"
---
# <a name="oracle-e-business-suite-adapter-faqs"></a>Oracle E-business Suite 配接器常見問題集
下列一些常見問題 (Faq) 的相關[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。 另請參閱[BizTalk Adapter Pack 的常見問題集](../../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.md)。
  

## <a name="how-can-i-use-the-oracle-e-business-adapter-to-communicate-with-oracle-e-business-suite"></a>如何使用 Oracle E-business 配接器與 Oracle E-business Suite 通訊？  
 您可以使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與 Oracle E-business Suite，藉由開發 BizTalk 應用程式，使用 WCF 服務模型，或使用 WCF 通道模型通訊。 如需詳細資訊，請參閱 <<c0> [ 概觀的 BizTalk 配接器 for Oracle E-business Suite](http://msdn.microsoft.com/library/4f18fa2e-4e97-4c28-b38d-fc39ac53789e)。  
  
## <a name="what-interfaces-are-supported-by-the-oracle-e-business-adapter-for-retrieving-metadata"></a>Oracle E-business 配接器支援哪些介面來擷取中繼資料？  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]來擷取中繼資料支援兩個介面：  
  
-   MetadataExchange WCF 所提供。 WCF 提供的中繼資料交換端點的所有 WCF 繫結，讓從 Oracle E-business Suite 取得中繼資料的用戶端。  
  
-   WCF LOB 配接器 SDK，支援的中繼資料瀏覽和搜尋功能的配接器所提供的 IMetadataRetrievalContract。  
  
## <a name="how-does-the-adapter-connect-to-oracle-e-business-suite"></a>配接器如何連接到 Oracle E-business Suite？  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]針對 Oracle 用戶端使用的 Oracle Access Components。 [支援 LOB 系統](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)列出用戶端版本。 若要連接到 Oracle E-business Suite，配接器用戶端必須提供連接字串[連線統一資源識別元 (URI)](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)。 就內部而言，配接器會將連線 URI 對應至連接到 Oracle E-business Suite 中的基礎資料庫的連接字串。 請參閱[建立 Oracle EBS 的連接](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)。  
  
## <a name="does-the-oracle-e-business-adapter-provide-a-secure-way-of-communicating-with-the-oracle-e-business-suite--are-there-any-best-practices-to-ensure-data-security"></a>Oracle E-business 配接器是否提供與 Oracle E-business Suite 通訊的安全方式？  是否有任何最佳作法，以確保資料安全性？  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援企業單一登入 (SSO)，它會建立與 Oracle E-business Suite 的連線在進行驗證。 SSO 使用資料庫和主要祕密來加密和儲存使用者認證。 它也會提供服務，以將 Microsoft Windows 帳戶對應到第二個用來存取後端系統的認證。  
  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]也會要求您輸入使用者名稱和密碼的認證來連接到 Oracle E-business Suite。 這些認證會用來驗證使用者，藉此提供的連線的授權層級。 Oracle E-business 配接器會提供多種方法讓您可以提供這些認證。 如需有關如何安全地提供 BizTalk 解決方案中的 Oracle 認證的資訊，請參閱[配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-oracle-ebs/security-with-the-oracle-e-business-suite-adapter-and-biztalk-server.md)。 如需有關如何安全地提供程式設計的方案中的 Oracle 認證的資訊，請參閱[安全使用 Oracle EBS 配接器程式設計](../../adapters-and-accelerators/adapter-oracle-ebs/secure-programming-with-the-oracle-ebs-adapter.md)。  
  
 如需詳細資訊：  
  
- 中的資料安全性[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 保護您的 Oracle EBS 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/secure-your-oracle-ebs-applications.md)。  
  
- 最佳作法，以確保資料安全性[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 安全性最佳作法](../../adapters-and-accelerators/adapter-oracle-ebs/best-practices-to-secure-the-oracle-e-business-suite-adapter.md)。  
  
## <a name="is-there-a-gui-provided-by-the-oracle-e-business-adapter-to-view-and-perform-operations-on-the-artifacts-in-oracle-e-business-suite"></a>有提供 Oracle E-business 配接器的 GUI 可用來檢視及 Oracle E-business Suite 中執行的構件上的作業嗎？  
 使用配接器服務 BizTalk 專案增益集和新增配接器服務參考 Visual Studio 外掛程式提供的對話方塊，您可以在其中檢視和 Oracle E-business Suite 中執行的構件上的作業。 如需有關所提供的 GUI [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 瀏覽、 搜尋及取得中繼資料的 Oracle EBS 作業](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。  
  
## <a name="what-are-binding-properties-in-the-oracle-e-business-adapter-where-can-i-find-information-about-all-the-binding-properties-in-the-oracle-e-business-adapter"></a>什麼 Oracle E-business 配接器中，繫結屬性？ 哪裡找到 Oracle E-business 配接器中的所有繫結內容的相關資訊？  
 配接器用戶端可以使用中的繫結屬性[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]來設定和控制配接器的行為。 針對所有的繫結屬性的相關資訊顯示在[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 使用的繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
## <a name="what-are-inbound-and-outbound-operations-in-the-oracle-e-business-adapter"></a>在 Oracle E-business 配接器的輸入和輸出作業有哪些？  
 在輸入的作業中，LOB 系統 (Oracle E-business Suite) 是用戶端而配接器用戶端服務，其中交易來自 Oracle E-business Suite。 比方說，「 輪詢 」 和 「 通知的作業。  
  
 在輸出的作業中，配接器用戶端的用戶端且 LOB 系統 (Oracle E-business Suite) 會變成的服務，其中交易來自配接器用戶端。 比方說，插入、 選取、 更新和刪除作業，在介面資料表、 預存程序和函式、 作業及複合作業。  
  
## <a name="where-can-i-find-information-about-the-oracle-data-types-that-are-supported-in-the-oracle-e-business-adapter"></a>哪裡可以找到 Oracle E-business 配接器中支援的 Oracle 資料類型的相關資訊？  
 如需支援的 Oracle 資料類型[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 基本 Oracle 資料型別](../../adapters-and-accelerators/adapter-oracle-ebs/basic-oracle-data-types2.md)。  
  
## <a name="what-is-applications-context-how-can-i-set-applications-context-for-various-oracle-artifacts-in-the-oracle-e-business-adapter"></a>什麼是應用程式內容？ 如何設定各種 Oracle 成品的應用程式內容中 Oracle E-business 配接器？  
 如需應用程式內容，以及如何將它設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
## <a name="which-approach-biztalk-server-wcf-service-model-or-wcf-channel-model-can-i-use-to-perform-various-operations-using-the-oracle-e-business-adapter"></a>若要使用 Oracle E-business 配接器執行各種作業可以使用哪種方法 （BizTalk Server、 WCF 服務模型或 WCF 通道模型）？  
 如需方法的詳細資訊，您可以使用執行各種作業，使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 開發您的 Oracle EBS 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)。  
  
## <a name="see-also"></a>另請參閱  
[BizTalk Adapter Pack 之常見問題](../../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.md)