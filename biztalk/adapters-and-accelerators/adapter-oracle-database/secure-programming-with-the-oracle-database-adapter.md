---
title: 安全使用 Oracle 資料庫配接器程式設計 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- credentials
- adapter, security considerations when programming on
- credentials, setting in code
- credentials, protecting
- security
ms.assetid: 06213c14-42b8-4d4a-b238-0aedbc27ab6a
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dab171bf2eef81221e6dde15756dc7b011c7ee92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215054"
---
# <a name="secure-programming-with-the-oracle-database-adapter"></a>安全使用 Oracle 資料庫配接器進行程式設計
## <a name="how-do-i-protect-credentials-when-i-use-the-add-adapter-service-reference-visual-studio-plug-in"></a>如何執行保護認證時使用新增配接器服務參考 Visual Studio 外掛程式？  
 當您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]若要建立 WCF 用戶端，您必須提供使用者名稱和 Oracle 資料庫的密碼。 您應該只從執行此操作**安全性**索引標籤上**設定配接器** 對話方塊。 輸入 Oracle 認證從**安全性**而不是直接在索引標籤上**設定 URI**  欄位中，確定下列：  
  
-   認證不會顯示在**Uri**欄位[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]對話方塊可以存取您的電腦螢幕的任何人員讀取。  
  
-   認證不會出現在組態檔[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。  
  
 如需有關如何產生 WCF 用戶端使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，包括如何輸入 Oracle 資料庫使用者名稱和密碼，請參閱[取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)。  
  
## <a name="what-are-best-practices-for-setting-credentials-in-code"></a>在程式碼中設定憑證的最佳做法為何？  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供**ClientCredentials**類別，以協助您設定的認證，用戶端通訊物件，例如**ChannelFactory**，用來向服務驗證本身。 使用**ClientCredentials**類別，您確定 WCF 會採用物件的通道堆疊中指定任何驗證機制，並將其套用至您的用戶端和服務之間的交換。  
  
 因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]裝載內含式與它使用的應用程式，不一定要使用**ClientCredentials**類別來設定認證，用戶端上使用應用程式所使用的通訊物件。 不過，並非很好的作法。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]建議您使用**ClientCredentials**類別。 此屬性會指定是否接受使用者名稱和密碼連線 URI 中的 Oracle 資料庫配接器。 **AcceptCredentialsInUri**預設為**false**，這表示，配接器將會擲回例外狀況如果連線 URI 包含認證。 您可以設定**AcceptCredentialsInUri**至**true**提供連線 URI 中的認證。  
  
 下列範例示範如何使用**認證**屬性上設定 Oracle 資料庫的認證**ChannelFactory**。  
  
```  
// Create binding and endpoint  
OracleDBBinding binding = new OracleDBBinding();  
EndpointAddress endpointAddress = new EndpointAddress("oracleDB://Adapter");  
  
// Create the channel factory   
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, endpointAddress))  
  
// Set user name and password  
factory.Credentials.UserName.UserName = "SCOTT";  
factory.Credentials.UserName.Password = "TIGER";  
  
// Open the channel factory  
factory.Open();  
```  
  
 下列範例示範如何使用**ClientCredentials**類別來設定 WCF 用戶端上的 Oracle 資料庫的認證。  
  
```  
// Initialize a new client for the SQLEXECUTE operation from configuration   
SQLEXECUTEClient sqlExecuteClient = new SQLEXECUTEClient("OracleDBBinding_SQLEXECUTE");  
  
// Set user name and password  
sqlExecuteClient.ClientCredentials.UserName.UserName = "SCOTT";  
sqlExecuteClient.ClientCredentials.UserName.Password = "TIGER";  
  
// Open the client  
sqlExecuteClient.Open();  
```  
  
## <a name="how-can-i-provide-for-more-secure-data-exchange-across-process-boundaries"></a>如何可提供更安全的資料交換的跨處理序界限？  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]裝載同處理序的應用程式或服務，則是使用它。 因為配接器裝載同處理序的取用者，您就不必在取用者之間交換的訊息提供安全性和[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 不過，如果使用的應用程式或服務傳送包含跨處理序界限，另一個服務或用戶端機密的資料庫資訊的訊息，您應該採取措施，以提供適當的保護，此環境中的資料。 [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]提供許多選項協助保護用戶端與服務之間傳送的訊息。 如需有關協助保護用戶端與服務之間傳送的訊息[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，請參閱[保護服務和用戶端](https://msdn.microsoft.com/library/ms734736.aspx)。 如需一般資訊的安全性功能[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供，請參閱[Windows Communication Foundation 安全性](https://msdn.microsoft.com/library/ms732362.aspx)。 
  
## <a name="see-also"></a>另請參閱  
[保護您的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md)   
[最佳作法](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)