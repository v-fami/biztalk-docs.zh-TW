---
title: SQL 配接器的 WCF 服務模型的概觀 |Microsoft Docs
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
ms.openlocfilehash: 121b425abe1c7c34ba75e535799770031b931525
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997327"
---
# <a name="overview-of-the-wcf-service-model-with-the-sql-adapter"></a>SQL 配接器的 WCF 服務模型概觀
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]公開為 WCF 服務的 SQL Server 作業。 若要執行作業，在 SQL Server 成品，例如若要叫用預存程序中，您叫用的配接器，接著執行 SQL Server 上的作業上的作業。 您的程式碼因此會做為配接器所呈現之 WCF 服務的用戶端。  
  
 在 [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型，為.NET 介面，表示用戶端與服務之間存在的服務合約和作業會表示成此介面上的方法。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]和 WCF 提供的工具，可讓您從配接器所公開的中繼資料產生此介面為目標的作業。 這些工具也會建立可用來叫用作業的服務介面中公開的 WCF 用戶端類別。 用戶端應用程式可以呼叫來叫用作業的介面卡上的 WCF 用戶端類別的方法。 若要實作服務，以接收輸入的作業，從[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，實作的輸入作業產生的介面。  
  
 下一節會說明如何使用 WCF 服務模型叫用 WCF 用戶端的作業。  
  
## <a name="invoking-operations-on-the-sql-server-with-a-wcf-client"></a>針對 SQL Server 的 WCF 用戶端叫用作業  
 若要使用 WCF 服務模型上叫用作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您必須先產生 WCF 用戶端類別為目標的作業。 然後，您可以建立 WCF 用戶端，這個類別的執行個體，並呼叫其方法來執行這些作業，SQL Server 系統上。 本節將概述一般.NET 配接器用戶端應用程式看起來如何。 特定的主題提供有關如何執行不同的作業上使用配接器的 SQL Server 資料庫的詳細的說明。  
  
#### <a name="to-invoke-operations-on-the-sql-adapter"></a>若要叫用 SQL 配接器的作業  
  
1. 產生 WCF 用戶端類別和協助程式程式碼。 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]以產生 WCF 用戶端類別中，目標為您想要使用的 SQL Server 資料庫成品。 如需如何產生 WCF 用戶端的詳細資訊，請參閱[產生的 SQL Server 成品的 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。  
  
2. 建立 WCF 用戶端執行個體並設定 WCF 用戶端。 設定 WCF 用戶端包含指定的繫結和用戶端會使用的端點位址 （連線 URI）。 以命令方式在程式碼或是宣告式組態中，您可以這麼做。 下列程式碼會建立 WCF 用戶端為目標**選取 **上的作業**員工**SQL Server 資料庫中的資料表。 它也會設定 SQL Server 資料庫的認證。 WCF 用戶端會從組態初始化。  
  
   ```  
   TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient("SqlAdapterBinding_TableOp_dbo_Employee"); //picking the binding and address from the app.config  
  
   client.ClientCredentials.UserName.UserName = "myuser";  
   client.ClientCredentials.UserName.Password = "mypassword";  
   ```  
  
   > [!NOTE]
   >  您可以在程式碼中指定的用戶端繫結與端點位址，或宣告中的 app.config 組態檔。 上面的程式碼片段會使用後者。 如需有關如何使用任一種方法的詳細資訊，請參閱 <<c0> [ 設定 SQL 配接器的 用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)。  
  
3. 開啟 WCF 用戶端。  
  
   ```  
   client.Open();  
   ```  
  
4. 叫用 WCF 用戶端在上一個步驟中建立執行 SQL server 資料庫上的選取作業的方法。 下列程式碼會叫用 Select 方法的 WCF 用戶端來叫用 SQL Server 資料庫資料表上的 SELECT 陳述式。  
  
   ```  
   client.Select("*", "where [Name] = ‘John Smith’");  
   ```  
  
5. 關閉 WCF 用戶端。  
  
   ```  
   client.Close();  
   ```  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)