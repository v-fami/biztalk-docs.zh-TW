---
title: "連接到使用 Windows 驗證的 Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0937dfd9-4a94-4d65-a42c-3c5019eefde2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed71a893ef029e6524b7e71f68626c32f207f91e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="connect-to-oracle-e-business-suite-using-windows-authentication"></a>連接到 Oracle E-business Suite 使用 Windows 驗證
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器用戶端使用 Windows 驗證來建立與 Oracle E-business Suite 的連線。 若要使用 Windows 驗證配接器用戶端必須指定"/"的使用者名稱和密碼保持空白。 如需有關如何連接到 Oracle E-business Suite 的使用 Windows 驗證的詳細資訊，請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)。  

## <a name="what-you-need-to-know"></a>您需要知道  
 若要使用 Windows 驗證，您必須執行下列作業：  
  
-   如果**ClientCredentialType**屬性設定為**資料庫**、 指定"/"的使用者名稱與保留密碼空白來連接到 Oracle E-business Suite 的資訊。  
  
-   如果**ClientCredentialType**屬性設定為**EBusiness**，指定要連接的 Oracle E-business Suite 認證。 此外，您必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。  

## <a name="enable-windows-authentication"></a>啟用 Windows 驗證  
 若要讓配接器用戶端使用 Windows 驗證來連接到 Oracle 資料庫，您必須執行 Oracle 資料庫的電腦上執行下列工作。  
  
1.  請確定`sqlnet.ora`底下可用的伺服器和用戶端上的檔案`ORACLE_BASE\ORACLE_HOME\network\admin\sqlnet.ora`，有下列項目：  
  
    ```  
    SQLNET.AUTHENTICATION_SERVICES= (NTS)  
    ```  
  
2.  連接到 Oracle 資料庫，以 SYSDBA。  
  
3.  Oracle 資料庫中的外部使用者的身分建立的 Windows 使用者。 請注意，使用者名稱必須以大寫。  
  
    ```  
    CREATE USER “OPS$<DOMAIN_NAME>\<USER_NAME\>” IDENTIFIED EXTERNALLY;  
    ```  
  
4.  授與權限給使用者。  
  
    ```  
    GRANT CONNECT,RESOURCE TO “OPS$<DOMAIN_NAME>\<USER_NAME\>”;  
    ```  
  
5.  Oracle E-business Suite 成品可供使用的應用程式的結構描述下。 若要啟用新建立的使用者，登入使用 Windows 驗證，來存取 Oracle E-business Suite 成品，必須為應用程式的結構描述變更使用者的結構描述。 您可以將下列 SQL 命令加入應用程式變更使用者的預設結構描述，當使用者登入的登入指令碼。  
  
    ```  
    alter session set current_schema=APPS;  
    ```  
  
6.  即使您的應用程式的結構描述變更的使用者結構描述，您將仍然無法瀏覽及產生中繼資料使用時，請參閱 Oracle E-business Suite 成品[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 這是因為新建立的使用者沒有權限的應用程式的結構描述。 請確定您針對新建立的使用者提供應用程式的結構描述權限。  
  
## <a name="see-also"></a>請參閱  
[設定 Oracle E-business Suite 配接器用戶端](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md)   
[建立 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)  
 [建立 Oracle E-business Suite 連線](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)