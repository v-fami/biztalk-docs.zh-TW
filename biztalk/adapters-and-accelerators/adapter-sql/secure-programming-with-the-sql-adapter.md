---
title: 使用 SQL 配接器安全的程式設計 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5c84744a-6595-4d93-afe7-39a7ccf1b6a0
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e0c5e68eb1f07067a43995693cbb43bdcad76a4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002383"
---
# <a name="secure-programming-with-the-sql-adapter"></a>安全使用 SQL 配接器進行程式設計
## <a name="how-do-i-protect-credentials-when-i-use-the-add-adapter-service-reference-visual-studio-plug-in"></a>如何保護認證當我使用 新增配接器服務參考 Visual Studio 外掛程式？  
 當您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]若要建立的 WCF 用戶端，您可能必須提供使用者名稱和密碼的 SQL Server 資料庫。 您必須輸入認證，從**安全性**索引標籤上**設定配接器** 對話方塊。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不會提供選項來指定連線 URI 的一部分的使用者名稱和密碼。 這可確保：  
  
- 認證不會顯示在**設定 URI**欄位**新增配接器服務參考外掛程式**對話方塊，其中以您的電腦螢幕的存取權的任何人都可以讀取它們。  
  
- 認證不會出現在組態檔[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。  
  
  如需有關如何使用來產生 WCF 用戶端[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，包括如何為 SQL Server 資料庫中輸入使用者名稱和密碼，請參閱[取得中繼資料的 SQL Server 作業，在 Visual Studio 中使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).  
  
## <a name="what-are-best-practices-for-setting-credentials-in-code"></a>在程式碼中的 設定認證的最佳作法有哪些？  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] 提供**ClientCredentials**類別，以協助您設定用戶端通訊物件，例如認證**ChannelFactory**，用來向服務驗證本身。 藉由使用**ClientCredentials**類別，您確定 WCF 會在該物件的通道堆疊中指定任何的驗證機制，並將它們套用到您的用戶端與服務之間的交換。  
  
 因為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]裝載同處理序與其使用的應用程式，不一定需要使用**ClientCredentials**類別來設定認證，用戶端上使用應用程式所使用的通訊物件。 它是，不過，最佳做法進行此作業。  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]需要使用**ClientCredentials**類別以程式設計的方式傳遞認證。 **AcceptCredentialsInUri**繫結屬性會忽略[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以防止在 URI 中的傳遞認證。  
  
 下列範例示範如何使用**認證**屬性上設定 SQL Server 資料庫的認證**ChannelFactory**。  
  
```  
// Create binding and endpoint  
SqlAdapterBinding binding = new SqlAdapterBinding();  
EndpointAddress address = new EndpointAddress("mssql://mysqlserver//mydatabase?");  
  
// Create the channel factory   
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, endpointAddress))  
  
// Set user name and password  
factory.Credentials.UserName.UserName = "myuser";  
factory.Credentials.UserName.Password = "mypassword";  
  
// Open the channel factory  
factory.Open();  
```  
  
 下列範例示範如何使用**ClientCredentials**類別來設定 WCF 用戶端上的 SQL Server 資料庫的認證。  
  
```  
// Initialize a new client for the SELECT operation on the Employee table   
SqlAdapterBinding binding = new SqlAdapterBinding();  
EndpointAddress address = new EndpointAddress("mssql://mysqlserver//mydatabase?");  
TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient(binding,address);  
  
// Set user name and password  
client.ClientCredentials.UserName.UserName = "myuser";  
client.ClientCredentials.UserName.Password = "mypassword";  
  
// Open the client  
client.Open();  
```  
  
## <a name="how-can-i-provide-for-more-secure-data-exchange-across-process-boundaries"></a>如何跨處理序界限提供更安全的資料交換？  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]裝載同處理序的應用程式或取用它的服務。 因為配接器裝載同處理序與取用者，就不需要在取用者之間交換的訊息提供安全性和[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 不過，如果使用的應用程式或服務會傳送包含跨處理序界限，另一個服務或用戶端機密的資料庫資訊的訊息，您應該提供適當的保護，這項資料在您的環境中的量值。 [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] 提供許多選項來協助保護用戶端與服務之間傳送的訊息。 如需有關協助保護用戶端與服務之間傳送的訊息[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，請參閱 < [Securing Services and Clients](https://msdn.microsoft.com/library/ms734736.aspx)。 如需一般資訊的安全性功能[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供，請參閱 < [Windows Communication Foundation 安全性](https://msdn.microsoft.com/library/ms732362.aspx)。
  
## <a name="see-also"></a>另請參閱  
[保護您的 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)  
[若要保護的 SQL 配接器的最佳作法](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)