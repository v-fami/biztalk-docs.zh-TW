---
title: 連接到 Oracle 資料庫使用 Windows 驗證 |Microsoft 文件
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
ms.openlocfilehash: 840435ce334863a4b76e6ac7da0d8dd64e7d4937
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961940"
---
# <a name="connect-to-the-oracle-database-using-windows-authentication"></a>連接到 Oracle 資料庫使用 Windows 驗證
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]可讓配接器用戶端使用 Windows 驗證來與 Oracle 資料庫建立連線。 若要使用 Windows 驗證，配接器用戶端必須指定"/"的使用者名稱與保留密碼空白。 如需有關如何連接到 Oracle 資料庫使用 Windows 驗證的詳細資訊，請參閱[連接到 Oracle 資料庫，在 Visual Studio 中使用 取用配接器服務](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md)。  
  
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
  
5.  若要啟用新建立的使用者，登入使用 Windows 驗證來存取 Oracle 資料庫成品中，您可以變更使用者的結構描述 SCOTT 結構描述。 您可以將下列 SQL 命令加入與 SCOTT 變更使用者的預設結構描述，當使用者登入的登入指令碼。  
  
    ```  
    alter session set current_schema=SCOTT;  
    ```  
  
6.  即使您變更使用者的結構描述為 SCOTT 結構描述時，您將仍然無法瀏覽及產生中繼資料使用時，請參閱 Oracle 資料庫成品[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 這是因為新建立的使用者沒有 SCOTT 結構描述的權限。 請確定您提供 SCOTT 結構描述權限給新建立的使用者。  
  
## <a name="see-also"></a>請參閱  
 [設定 Oracle 資料庫配接器的 Oracle 用戶端](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)   
[建立 Oracle 資料庫的連線](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)