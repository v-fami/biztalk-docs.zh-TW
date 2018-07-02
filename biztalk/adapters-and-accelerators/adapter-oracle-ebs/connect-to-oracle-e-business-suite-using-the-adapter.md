---
title: 連接到 Oracle E-business Suite 使用配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80ff31d4-be4c-42d7-a321-8f01b40dd71e
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7ef5a7dc47b135cbeeec348c2af2d5054163d33
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980695"
---
# <a name="connect-to-oracle-e-business-suite-using-the-adapter"></a>連接到 Oracle E-business Suite 使用配接器
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]使用 ODP.NET 11.1.0.7 連接到 Oracle E-business Suite。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]要求配接器用戶端提供的連接字串，稱為 「 統一資源識別元 (URI)，連接到 Oracle E-business Suite 的連線。 就內部而言，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會連接到基礎的 Oracle 資料庫，透過 URI。 配接器用戶端可以使用的連線 URI，指定連線參數，以連接到外部系統。  

## <a name="connectivity-to-oracle-ebs"></a>連線到 Oracle EBS  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器用戶端連線到 Oracle E-business Suite 中的下列兩種方式：  
  
- **使用 tnsnames.ora**： 連線配接器用戶端所提供的 URI 包含只 tnsnames.ora 檔案中指定的網路服務名稱。 配接器會擷取在 tnsnames.ora 檔案中的 net 的服務名稱項目中的連接參數，例如伺服器名稱、 服務名稱和連接埠號碼。 若要使用這種方法，執行 Oracle 用戶端的電腦，必須設定為包含 tnsnames.ora 檔案中的 net 的服務名稱的 Oracle 資料庫中。  
  
  > [!IMPORTANT]
  >  執行 Oracle 用戶端的限制，因為**DataSourceName**中的參數 （net 的服務名稱）[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)不能包含超過 39 個字元，如果您要執行作業在交易中。 因此，請確定為指定的值**DataSourceName**參數是否小於或等於 39 個字元，如果您將會在交易中執行作業。  
  
- **不使用 tnsnames.ora**： 連線配接器用戶端所提供的 URI 包含連線參數，例如伺服器名稱、 服務名稱和連接埠號碼。 在此情況下，必須出現在用戶端電腦上不需要 tnsnames.ora 檔案，或實際 tnsnames.ora 檔案本身，net 的服務名稱。 當您有大量的使用者連接到 Oracle 資料庫，在您的組織，並新增/更新伺服器不會導致以手動方式新增/更新每個用戶端電腦上的 tnsnames.ora 檔案中的連線詳細資料，這是很有幫助。  
  
  > [!IMPORTANT]
  >  如果您要在交易中執行作業，則不支援這種連線模式。 這是因為 Oracle 用戶端的限制。  
  
  如需有關如何連接到 Oracle E-business Suite 的詳細資訊，請參閱 <<c0> [ 建立連線到 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)。  
  
  請確定您遵循安全性指導方針建立與 Oracle E-business Suite 的連線時。 請參閱[保護您的 Oracle EBS 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/secure-your-oracle-ebs-applications.md)。
  
## <a name="enter-client-credentials"></a>輸入用戶端認證  
 在  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您可以提供認證以連接到 Oracle E-business Suite，在下列兩個地方：  
  
- 在 [**安全性**索引標籤中**設定配接器**] 對話方塊。 您可以找到在此對話方塊[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
- 在**OracleUserName**並**OraclePassword**上的繫結屬性**繫結屬性**索引標籤中**設定配接器** 對話方塊。 您可以找到在此對話方塊[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 在此情況下，認證會儲存在繫結檔案中的純文字。  
  
  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開**ClientCredentialType**繫結可讓您指定一組用以連接到 Oracle E-business Suite 的認證 （Oracle E-business Suite 或 Oracle 資料庫） 的屬性。  
  
- 若要使用的 Oracle 資料庫的認證進行連接，指定**ClientCredentialType**繫結屬性設為**資料庫**，然後在**安全性**索引標籤上，指定資料庫中的認證**使用者名**並**密碼**文字方塊。  如果您將會執行作業上的任何 Oracle E-business Suite 成品 （介面資料表、 介面檢視、 並行處理程式，要求集或 Oracle E-business Suite PL/SQL Api），您也必須提供中的 Oracle E-business Suite 認證**OracleUserName**並**OraclePassword**繫結屬性。  
  
- 若要使用 Oracle E-business Suite 認證進行連接，指定**ClientCredentialType**繫結屬性當做**EBusiness**，然後指定 [Oracle E-business Suite 中的認證**使用者名稱**並**密碼**上的文字方塊**安全性**] 索引標籤。您也必須指定 Oracle 資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。  
  
  如需指定用戶端認證的詳細資訊，請參閱[for Oracle E-business Suite 中設定的登入認證](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-sign-in-credentials-for-the-oracle-e-business-suite.md)。  
  
## <a name="using-windows-authentication"></a>使用 Windows 驗證  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]時連接到 Oracle E-business Suite 支援 Windows 驗證。 使用 Windows 驗證時，配接器用戶端可以決定根據 Windows 登入認證，使用者的身分識別，並可以利用內建安全性的 Windows 環境。 如需有關使用 Windows 驗證連接到 Oracle E-business Suite 的資訊，請參閱[連接到 Oracle E-business Suite Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)。  
  
## <a name="see-also"></a>另請參閱  
[了解 BizTalk Adapter for Oracle E-business 花色](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)