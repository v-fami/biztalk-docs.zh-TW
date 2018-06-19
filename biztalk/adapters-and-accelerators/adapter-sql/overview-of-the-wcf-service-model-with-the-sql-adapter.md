---
title: SQL 配接器的 WCF 服務模型的概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7641bcc7-3845-4914-9b1b-cb86b998ea6d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3afbf1822945f0a47b09a93b3ac3cc2f8ac8653d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222886"
---
# <a name="overview-of-the-wcf-service-model-with-the-sql-adapter"></a>SQL 配接器的 WCF 服務模型概觀
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]公開為 WCF 服務的 SQL Server 作業。 若要執行作業，SQL Server 成品，例如若要叫用預存程序，在您叫用的配接器，接著執行 SQL Server 上的作業上的作業。 您的程式碼因此可做為配接器所呈現之 WCF 服務的用戶端。  
  
 在[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型時，用戶端和服務之間存在的服務合約以.NET 介面和作業會表示為此介面上的方法。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]和 WCF 提供的工具，可讓您從配接器會公開的中繼資料產生此介面為目標的作業。 這些工具也會建立 WCF 用戶端類別，可用於叫用的服務介面中公開的作業。 用戶端應用程式可以呼叫 WCF 用戶端類別，來叫用的介面卡上的作業的方法。 若要實作服務以接收來自輸入的操作[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，實作的輸入作業所產生的介面。  
  
 下節說明如何使用 WCF 服務模型來叫用的 WCF 用戶端的作業。  
  
## <a name="invoking-operations-on-the-sql-server-with-a-wcf-client"></a>SQL Server 的 WCF 用戶端上叫用作業  
 若要使用 WCF 服務模型上叫用作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您必須先產生目標作業的 WCF 用戶端類別。 然後，您可以建立 WCF 用戶端，這個類別的執行個體，並呼叫其方法來執行這些作業的 SQL Server 系統上。 本章節提供一般的.NET 配接器用戶端應用程式看起來像外的框。 特定的主題會提供有關如何執行不同的作業上使用配接器的 SQL Server 資料庫的詳細的說明。  
  
#### <a name="to-invoke-operations-on-the-sql-adapter"></a>叫用 SQL 配接器的作業  
  
1.  產生 WCF 用戶端類別和協助程式程式碼。 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別針對您要使用的 SQL Server 資料庫成品。 如需如何產生 WCF 用戶端的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。  
  
2.  建立 WCF 用戶端執行個體並設定 WCF 用戶端。 設定 WCF 用戶端包含指定繫結與用戶端會使用的端點位址 （連線 URI）。 您可以在程式碼中以命令方式或是宣告式組態。 下列程式碼會建立 WCF 用戶端為目標**選取**作業**員工**SQL Server 資料庫中的資料表。 它也會設定 SQL Server 資料庫的認證。 WCF 用戶端會從設定初始化。  
  
    ```  
    TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient("SqlAdapterBinding_TableOp_dbo_Employee"); //picking the binding and address from the app.config  
  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
    > [!NOTE]
    >  您可以在程式碼中指定的用戶端繫結與端點位址，或宣告 app.config 組態檔中。 上述程式碼片段會使用後者。 如需有關如何使用任一種方法的詳細資訊，請參閱[設定 SQL 配接器的 用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)。  
  
3.  開啟 WCF 用戶端。  
  
    ```  
    client.Open();  
    ```  
  
4.  叫用 WCF 用戶端上一個步驟中建立執行 SQL server 資料庫上的選取作業的方法。 下列程式碼會叫用 Select 方法的 WCF 用戶端來叫用的 SQL Server 資料庫資料表上的 SELECT 陳述式。  
  
    ```  
    client.Select("*", "where [Name] = ‘John Smith’");  
    ```  
  
5.  關閉 WCF 用戶端。  
  
    ```  
    client.Close();  
    ```  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)