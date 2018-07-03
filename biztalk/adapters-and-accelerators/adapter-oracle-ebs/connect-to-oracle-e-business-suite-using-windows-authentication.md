---
title: 連接到使用 Windows 驗證的 Oracle E-business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0937dfd9-4a94-4d65-a42c-3c5019eefde2
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9563f754fd096efb4ab39192f1a8a21a7e6b2207
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009103"
---
# <a name="connect-to-oracle-e-business-suite-using-windows-authentication"></a>連接到 Oracle E-business Suite 使用 Windows 驗證
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器用戶端使用 Windows 驗證來建立與 Oracle E-business Suite 的連線。 若要使用 Windows 驗證配接器用戶端必須指定"/"的使用者名稱，並將密碼保持空白。 如需有關如何連接到 Oracle E-business Suite 使用 Windows 驗證的詳細資訊，請參閱 <<c0> [ 連接到 Oracle E-business Suite，在 Visual Studio 中](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)。  

## <a name="what-you-need-to-know"></a>您需要知道  
 若要使用 Windows 驗證，您必須執行下列作業：  
  
-   如果**ClientCredentialType**屬性設定為**資料庫**、 指定"/"的使用者名稱與保留密碼為空白來連接到 Oracle E-business Suite。  
  
-   如果**ClientCredentialType**屬性設定為**EBusiness**，指定要連接的 Oracle E-business Suite 認證。 此外，您必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。  

## <a name="enable-windows-authentication"></a>啟用 Windows 驗證  
 若要啟用使用 Windows 驗證來連接到 Oracle 資料庫配接器用戶端，您必須執行的 Oracle 資料庫的電腦上執行下列工作。  
  
1. 請確定`sqlnet.ora`上的用戶端和伺服器，可在檔案`ORACLE_BASE\ORACLE_HOME\network\admin\sqlnet.ora`，具有下列項目：  
  
   ```  
   SQLNET.AUTHENTICATION_SERVICES= (NTS)  
   ```  
  
2. 以 sysdba 身分連接到 Oracle 資料庫。  
  
3. 建立為 Oracle 資料庫中的外部使用者的 Windows 使用者。 請注意，使用者名稱必須是大寫。  
  
   ```  
   CREATE USER “OPS$<DOMAIN_NAME>\<USER_NAME\>” IDENTIFIED EXTERNALLY;  
   ```  
  
4. 授與權限給使用者。  
  
   ```  
   GRANT CONNECT,RESOURCE TO “OPS$<DOMAIN_NAME>\<USER_NAME\>”;  
   ```  
  
5. Oracle E-business Suite 成品可供使用的應用程式結構描述下。 啟用新建立的使用者，登入使用 Windows 驗證，來存取 Oracle E-business Suite 的成品，您必須變更使用者的結構描述，以應用程式結構描述。 您可以將下列 SQL 命令加入至應用程式變更使用者的預設結構描述，當使用者登入的登入指令碼。  
  
   ```  
   alter session set current_schema=APPS;  
   ```  
  
6. 即使您的應用程式結構描述變更的使用者結構描述，您將仍然無法查看同時瀏覽並產生中繼資料所使用的 Oracle E-business Suite 成品[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 這是因為新建立的使用者沒有權限的應用程式結構描述。 請確定您針對新建立的使用者提供應用程式結構描述權限。  
  
## <a name="see-also"></a>另請參閱  
[設定 Oracle 用戶端 E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md)   
[建立 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)  
 [建立 Oracle E-business Suite 的連線](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)