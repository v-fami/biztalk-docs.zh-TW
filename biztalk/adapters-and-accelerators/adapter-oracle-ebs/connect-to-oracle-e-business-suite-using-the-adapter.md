---
title: 連接到 Oracle E-business Suite 使用配接器 |Microsoft 文件
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
ms.openlocfilehash: 7c8551c0f09d65d50b87248a6b0dc4030a612fc7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217862"
---
# <a name="connect-to-oracle-e-business-suite-using-the-adapter"></a>連接到 Oracle E-business Suite 使用配接器
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]使用 ODP.NET 11.1.0.7 連接到 Oracle E-business Suite。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]需要配接器用戶端提供的連接字串，呼叫統一資源識別元 (URI)，連接到 Oracle E-business Suite 的連線。 就內部而言，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會連接到基礎的 Oracle 資料庫，透過的 URI。 使用 連線 URI，配接器用戶端可以指定連線參數，以連接到外部系統。  

## <a name="connectivity-to-oracle-ebs"></a>連接到 Oracle EBS  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器用戶端連接到 Oracle E-business Suite 中的下列兩種方式：  
  
-   **使用 tnsnames.ora**： 連線配接器用戶端所提供的 URI 包含只 tnsnames.ora 檔案中指定的網路服務名稱。 配接器從 tnsnames.ora 檔案中的網路服務名稱的項目中擷取連接參數，例如伺服器名稱、 服務名稱和連接埠號碼。 若要使用這種方法，執行 Oracle 用戶端的電腦必須設定要在 tnsnames.ora 檔案中包含之 Oracle 資料庫的網路服務名稱。  
  
    > [!IMPORTANT]
    >  由於 Oracle 用戶端的限制， **DataSourceName**中的參數 (net service name)[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)不能包含超過 39 個字元，如果您正在執行作業在交易中。 因此，請確定為指定的值**DataSourceName**參數為小於或等於 39 個字元，如果您將在交易中執行的作業。  
  
-   **不使用 tnsnames.ora**： 配接器用戶端所提供的 URI 的連接包含連接參數，例如伺服器名稱、 服務名稱和連接埠號碼。 在此情況下，網路服務名稱在 tnsnames.ora 檔案或實際 tnsnames.ora 檔案本身，無須任何存在於用戶端電腦上。 當您有大量使用者連接到 Oracle 資料庫，在您的組織，並新增/更新伺服器不會導致以手動方式新增/更新每個用戶端電腦上 tnsnames.ora 檔案中的連線詳細資料，這是很有幫助。  
  
    > [!IMPORTANT]
    >  如果您在交易中執行作業，則不支援這種連線模式。 這是因為 Oracle 用戶端的限制。  
  
 如需有關如何連接到 Oracle E-business Suite 的詳細資訊，請參閱[建立 Oracle E-business Suite 連線](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)。  
  
 請確定您遵循安全性指導方針建立與 Oracle E-business Suite 連線時。 請參閱[保護應用程式 Oracle EBS](../../adapters-and-accelerators/adapter-oracle-ebs/secure-your-oracle-ebs-applications.md)。
  
## <a name="enter-client-credentials"></a>輸入用戶端認證  
 在[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您可以提供認證以連接到 Oracle E-business Suite，在下列兩個地方：  
  
-   在**安全性**索引標籤中**設定配接器** 對話方塊。 您可以找到此對話方塊在[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
-   在**OracleUserName**和**OraclePassword**上的繫結屬性**繫結屬性**索引標籤中**設定配接器**對話方塊。 您可以找到此對話方塊在[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 在此情況下，認證會儲存在繫結檔案中的純文字。  
  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開**ClientCredentialType**繫結可讓您指定一組將用來連接到 Oracle E-business Suite 的認證 （Oracle E-business Suite 或 Oracle 資料庫） 的屬性。  
  
-   若要使用的 Oracle 資料庫的認證進行連接，指定**ClientCredentialType**繫結屬性做為**資料庫**，然後在**安全性**索引標籤上，指定資料庫中的認證**使用者名**和**密碼**文字方塊。  如果您將會執行作業的任何 Oracle E-business Suite 成品 （介面資料表、 介面檢視、 並行程式，要求組或 Oracle E-business Suite PL/SQL 應用程式開發介面），您也必須提供中的 Oracle E-business Suite 認證**OracleUserName**和**OraclePassword**繫結屬性。  
  
-   若要使用 Oracle E-business Suite 認證進行連接，指定**ClientCredentialType**繫結屬性做為**EBusiness**，然後指定 [Oracle E-business Suite 中的認證**使用者名稱**和**密碼**文字方塊上**安全性**] 索引標籤。您也必須指定 Oracle 資料庫認證**OracleUserName**和**OraclePassword**繫結屬性。  
  
 如需指定用戶端憑證的詳細資訊，請參閱[for Oracle E-business Suite 中設定的登入認證](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-sign-in-credentials-for-the-oracle-e-business-suite.md)。  
  
## <a name="using-windows-authentication"></a>使用 Windows 驗證  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]同時支援 Windows 驗證連接到 Oracle E-business Suite。 使用 Windows 驗證時，配接器用戶端可以判斷使用者的身分識別為基礎的 Windows 登入認證，並可以利用內建安全性的 Windows 環境。 如需使用 Windows 驗證連接到 Oracle E-business Suite 的資訊，請參閱[連接到 Oracle E-business Suite Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)。  
  
## <a name="see-also"></a>另請參閱  
[瞭解 BizTalk Adapter for Oracle E-business 花色](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)