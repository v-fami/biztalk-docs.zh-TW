---
title: 連接到 Oracle 資料庫使用 Windows 驗證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73b42a1b-1105-4278-bf8a-62cf0cffb08f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c984a62275c58f50b0c360a5f46040a6022b459
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007751"
---
# <a name="connect-to-the-oracle-database-using-windows-authentication"></a>連接到 Oracle 資料庫使用 Windows 驗證
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]可讓配接器用戶端使用 Windows 驗證來建立與 Oracle 資料庫的連線。 若要使用 Windows 驗證時，配接器用戶端必須指定"/"的使用者名稱與保留密碼空白。 如需有關如何連接到 Oracle 資料庫使用 Windows 驗證的詳細資訊，請參閱 <<c0> [ 連接到 Oracle 資料庫，在 Visual Studio 中使用 取用配接器服務](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md)。  
  
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
  
5. 若要啟用新建立的使用者，登入使用 Windows 驗證，來存取 Oracle 資料庫成品中，您可以變更使用者的結構描述 SCOTT 結構描述。 您可以將下列 SQL 命令加入 scott 變更使用者的預設結構描述，當使用者登入的登入指令碼。  
  
   ```  
   alter session set current_schema=SCOTT;  
   ```  
  
6. 即使您變更使用者的結構描述為 SCOTT 結構描述時，您將仍然無法查看同時瀏覽並產生中繼資料所使用的 Oracle 資料庫成品[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 這是因為新建立的使用者沒有 SCOTT 結構描述的權限。 請確定您提供給新建立的使用者，SCOTT 結構描述權限。  
  
## <a name="see-also"></a>另請參閱  
 [設定 Oracle 用戶端，Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)   
[建立 Oracle 資料庫的連線](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)