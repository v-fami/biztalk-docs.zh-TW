---
title: 使用 Oracle 資料庫配接器的 WCF 服務模型的概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, overview
- invoking operations
- WCF service, creating and implementing
ms.assetid: 8ed765e5-b5e6-46bd-bcd6-282219caf75d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de5fff554249546244c59aed5c1dceff9a527411
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006063"
---
# <a name="overview-of-the-wcf-service-model-with-the-oracle-database-adapter"></a>使用 Oracle 資料庫配接器的 WCF 服務模型概觀
當您使用作業，[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]介面，您的程式碼做為用戶端或服務，配接器。 幾乎所有的作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]介面，您的程式碼是用戶端。 也就是您的應用程式叫用配接器上執行的作業例如，將記錄插入 Oracle 資料表的資訊。 唯一的作業，您的程式碼可做為服務，以[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]適用於 POLLINGSMT 作業。 在此情況下，配接器會傳送輪詢查詢作業的結果，您的應用程式。  
  
 在 [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型，為.NET 介面，表示用戶端與服務之間存在的服務合約和作業會表示成此介面上的方法。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]和 WCF 提供的工具，可讓您從配接器所公開的中繼資料產生此介面為目標的作業。 這些工具也會建立可用來叫用作業的服務介面中公開的 WCF 用戶端類別。 用戶端應用程式可以呼叫來叫用作業的介面卡上的 WCF 用戶端類別的方法。 若要實作服務，以接收來自 POLLINGSTMT 作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，實作 POLLINGSTMT 作業產生的介面。  
  
 下列各節將說明如何使用 WCF 服務模型，以建立用戶端與服務程式碼[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
## <a name="creating-and-invoking-operations-on-a-wcf-client-by-using-the-oracle-database-adapter"></a>建立和使用 Oracle 資料庫配接器叫用 WCF 用戶端上的作業  
 若要使用 WCF 服務模型上叫用作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須先產生 WCF 用戶端類別為目標的作業。 然後，您可以建立 WCF 用戶端，這個類別的執行個體，並呼叫其方法來執行的 Oracle 資料庫上的作業。  
  
#### <a name="to-invoke-operations-on-the-oracle-database-adapter"></a>若要叫用 Oracle 資料庫配接器上的作業  
  
1. 產生 WCF 用戶端類別和協助程式程式碼。 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 以產生 WCF 用戶端類別作為目標的 Oracle 資料庫成品與您想要使用。 如需如何產生 WCF 用戶端的詳細資訊，請參閱[產生的 Oracle 資料庫成品的 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。  
  
2. 指定用戶端繫結，以建立 WCF 用戶端執行個體。 指定用戶端繫結牽涉到指定的繫結和 WCF 用戶端將使用的端點位址。 以命令方式在程式碼或是宣告式組態中，您可以這麼做。 如需如何指定用戶端繫結的詳細資訊，請參閱[設定用戶端的 Oracle 資料庫繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-client-binding-for-the-oracle-database.md)。 下列程式碼會建立可用來執行資料操作語言 (DML) 作業，在 Oracle 資料庫資料表 （/SCOTT/ACCOUNTACTIVITY） 上的 WCF 用戶端。 它也會設定 Oracle 資料庫的認證。 WCF 用戶端會從組態初始化。  
  
   ```  
   SCOTTTableACCOUNTACTIVITYClient aaTableClient =   
       new SCOTTTableACCOUNTACTIVITYClient("OracleDBBinding_SCOTT.Table.ACCOUNTACTIVITY");  
  
   aaTableClient.ClientCredentials.UserName.UserName = "SCOTT";  
   aaTableClient.ClientCredentials.UserName.Password = "TIGER";  
   ```  
  
3. 開啟 WCF 用戶端。  
  
   ```  
   aaTableClient.Open();  
   ```  
  
4. 叫用 WCF 用戶端上步驟 2 中建立 Oracle 資料庫上執行作業的方法。 下列程式碼會叫用**選取 ** ACCOUNTACTIVITY 資料表上執行下列 SQL SELECT 查詢的 WCF 用戶端的方法： `SELECT * FROM ACCOUNTACTIVITY`。  
  
   ```  
   // create a record set parameter to hold the SELECT query result set and invoke the Select operation;  
   microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] selectRecords;  
   selectRecords = aaTableClient.Select("*", null);  
   ```  
  
5. 關閉 WCF 用戶端。  
  
   ```  
   aaTableClient.Close();  
   ```  
  
   如需執行資料表和檢視，包括與上面，使用選取的作業上的 DML 作業的詳細資訊，請參閱[執行基本的插入、 更新、 刪除和選取作業使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-in-oracle-db-using-a-wcf-service.md)。  
  
## <a name="creating-and-implementing-a-wcf-service-by-using-the-oracle-database-adapter"></a>建立和使用 Oracle 資料庫配接器實作的 WCF 服務  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可以執行的 Oracle 資料庫資料表或檢視表上的輪詢。 這項功能可讓您指定 SQL SELECT 查詢，將針對 Oracle 資料庫配接器應該定期執行。 此查詢的結果會傳回您的應用程式，透過一種特殊的作業，POLLINGSTMT 作業。 若要接收結果的輪詢查詢中，您的應用程式必須實作服務合約， [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] POLLINGSTMT 作業公開 （expose)。  
  
 若要實作服務，以接收 POLLINGSTMT 作業，您必須先產生代表服務合約所公開的.NET 介面 （也稱為 WCF 服務合約） [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] POLLINGSTMT 作業。 如需如何執行這項操作的詳細資訊，請參閱[產生的 Oracle 資料庫成品的 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。  
  
 然後您會藉由實作產生的介面實作的 WCF 服務。 這個類別包含的商務邏輯來處理 POLLINGSTMT 訊息，並將回應傳回給配接器。 接著，您使用的服務主機 (**System.ServiceModel.ServiceHost**) 來裝載此服務的執行個體。 如需詳細資訊，請參閱 <<c0> [ 使用 WCF 服務模型收到輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-service.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF 服務模型開發 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)