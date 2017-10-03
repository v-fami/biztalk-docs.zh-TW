---
title: "安全使用 Oracle EBS 配接器程式設計 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35b494f8-cb21-45c2-9bb4-097ba59ec52c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89a51a163c12a14fc58bdcefc5ffe6aab7df6d9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="secure-programming-with-the-oracle-ebs-adapter"></a>安全使用 Oracle EBS 配接器進行程式設計
## <a name="how-do-i-protect-credentials-when-i-use-the-add-adapter-service-reference-visual-studio-plug-in"></a>如何執行保護認證時使用新增配接器服務參考 Visual Studio 外掛程式？  
 當您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]若要建立 WCF 用戶端，您必須提供使用者名稱和密碼 for Oracle E-business Suite。 您應該只從執行此操作**安全性**索引標籤上**設定配接器** 對話方塊。 輸入 Oracle 認證從**安全性**而不是直接在索引標籤上**設定 URI**  欄位中，確定下列：  
  
-   認證不會顯示在**設定 URI**欄位[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]對話方塊可以存取您的電腦螢幕的任何人員讀取。  
  
-   認證不會出現在組態檔[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。  
  
 如需有關如何產生 WCF 用戶端使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，包括如何 for Oracle E-business Suite 中輸入使用者名稱和密碼，請參閱[取得 Visual Studio中的OracleE-businessSuite作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md).  
  
## <a name="what-are-best-practices-for-setting-credentials-in-code"></a>在程式碼中設定憑證的最佳做法為何？  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供**ClientCredentials**類別，以協助您設定的認證，用戶端通訊物件，例如**ChannelFactory**，用來向服務驗證本身。 使用**ClientCredentials**類別，您確定 WCF 會採用物件的通道堆疊中指定任何驗證機制，並將其套用至您的用戶端和服務之間的交換。  
  
 因為[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]裝載內含式與它使用的應用程式，不一定要使用**ClientCredentials**類別來設定認證，用戶端上使用應用程式所使用的通訊物件。 不過，並非很好的作法。  
  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]建議您使用**ClientCredentials**類別。 此屬性會指定是否接受使用者名稱和密碼連線 URI 中的 Oracle 資料庫配接器。 **AcceptCredentialsInUri**預設為**false**，這表示，配接器將會擲回例外狀況如果連線 URI 包含認證。 您可以設定**AcceptCredentialsInUri**至**true**提供 URI，在連接中的認證，視需要在用戶端應用程式。  
  
 下列範例示範如何使用**認證**屬性上設定 Oracle E-business Suite 認證**ChannelFactory**。  
  
```  
// Create binding and endpoint  
OracleEBSBinding binding = new OracleEBSBinding();  
EndpointAddress address = new EndpointAddress("oracleebs://ebs-instance");  
  
// Create the channel factory   
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
  
// Set user name and password  
factory.Credentials.UserName.UserName = "myuser";  
factory.Credentials.UserName.Password = "mypassword";  
  
// Open the channel factory  
factory.Open();  
```  
  
 下列範例示範如何使用**ClientCredentials** for Oracle E-business Suite 設定 WCF 用戶端認證類別。  
  
```  
// Initialize a new client for the SQLEXECUTE operation from configuration   
ConcurrentPrograms_ARClient client =   
  new ConcurrentPrograms_ARClient("OracleEBSBinding_ConcurrentPrograms_AR");  
  
// Set user name and password  
client.ClientCredentials.UserName.UserName = "myuser";  
client.ClientCredentials.UserName.Password = "mypassword";  
  
// Open the client  
client.Open();  
```  
  
## <a name="how-can-i-provide-for-more-secure-data-exchange-across-process-boundaries"></a>如何可提供更安全的資料交換的跨處理序界限？  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]裝載同處理序的應用程式或服務，則是使用它。 因為配接器裝載同處理序的取用者，您就不必在取用者之間交換的訊息提供安全性和[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 不過，如果使用的應用程式或服務傳送包含跨處理序界限，另一個服務或用戶端機密的資料庫資訊的訊息，您應該採取措施，以提供適當的保護，此環境中的資料。 [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]提供許多選項協助保護用戶端與服務之間傳送的訊息。 如需有關協助保護用戶端與服務之間傳送的訊息[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，請參閱 「 保護服務和用戶端 」，網址[http://go.microsoft.com/fwlink/?LinkId=89725](http://go.microsoft.com/fwlink/?LinkId=89725)。 如需一般資訊的安全性功能[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供，請參閱 < Windows Communication Foundation 安全性 >，網址[http://go.microsoft.com/fwlink/?LinkId=89726](http://go.microsoft.com/fwlink/?LinkId=89726)。  
  
## <a name="see-also"></a>另請參閱  
 [保護您的 Oracle EBS 應用程式](secure-your-oracle-ebs-applications.md)