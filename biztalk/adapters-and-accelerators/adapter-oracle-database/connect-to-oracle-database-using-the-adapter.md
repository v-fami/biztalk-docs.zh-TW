---
title: 使用連接到 Oracle 資料庫配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection string
- uniform resource identifier
- Oracle database, connecting to
- URI
- connection URI
ms.assetid: 5d5598e5-aba0-4c73-8e97-9156475b93c4
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a645ae3a2db79e9e2b5b4e46c758e37dfb0a1a6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004319"
---
# <a name="connect-to-oracle-database-using-the-adapter"></a>使用連接到 Oracle 資料庫配接器
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]使用 ODP.NET 11.1.0.7 連接到 Oracle 資料庫。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]要求配接器用戶端提供的連接字串，稱為 「 統一資源識別元 (URI)，來連接到 Oracle 資料庫的連接。 就內部而言，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]將 URI 對應至連接到 Oracle 資料庫的資料庫連接字串。 配接器用戶端可以使用的連線 URI，指定連線參數，以連接到外部系統。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓配接器用戶端連接到 Oracle 資料庫中下列兩種方式：  
  
- **使用 tnsnames.ora**： 連線配接器用戶端所提供的 URI 包含只 tnsnames.ora 檔案中指定的網路服務名稱。 配接器會擷取在 tnsnames.ora 檔案中的 net 的服務名稱項目中的連接參數，例如伺服器名稱、 服務名稱和連接埠號碼。 若要使用這種方法，執行 Oracle 用戶端的電腦，必須設定為包含 tnsnames.ora 檔案中的 net 的服務名稱的 Oracle 資料庫中。  
  
  > [!IMPORTANT]
  >  執行 Oracle 用戶端的限制，因為**DataSourceName**中的參數 （net 的服務名稱）[設定 Oracle 資料庫配接器的連線 URI](../../adapters-and-accelerators/adapter-oracle-database/configure-the-connection-uri-for-the-oracle-database-adapter.md)不能包含超過 39 個字元，如果您在交易中執行的作業。 因此，請確定為指定的值**DataSourceName**參數是否小於或等於 39 個字元，如果您將會在交易中執行作業。  
  
- **不使用 tnsnames.ora**： 連線配接器用戶端所提供的 URI 包含連線參數，例如伺服器名稱、 服務名稱和連接埠號碼。 在此情況下，必須出現在用戶端電腦上不需要 tnsnames.ora 檔案，或實際 tnsnames.ora 檔案本身，net 的服務名稱。 當您有大量的使用者連接到 Oracle 資料庫，在您的組織，並新增/更新伺服器不會導致以手動方式新增/更新每個用戶端電腦上的 tnsnames.ora 檔案中的連線詳細資料，這是很有幫助。  
  
  > [!IMPORTANT]
  >  如果您要在交易中執行作業，則不支援這種連線模式。 這是因為 Oracle 用戶端的限制。  
  
  如需有關如何連接到 Oracle 資料庫的詳細資訊，請參閱 <<c0> [ 建立 Oracle 資料庫的連接](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)。  
  
  請確定您遵循安全性指導方針建立與 Oracle 資料庫的連接時。 如需有關安全性指導方針的詳細資訊，請參閱[保護您的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md)。  
  
## <a name="windows-authentication"></a>Windows 驗證  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援 Windows 驗證連接到 Oracle 資料庫。 使用 Windows 驗證時，配接器用戶端可以決定根據 Windows 登入認證，使用者的身分識別，並可以利用內建安全性的 Windows 環境。 如需使用 Windows 驗證連接到 Oracle 資料庫的資訊，請參閱[連接到 Oracle Database Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle Database 概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)