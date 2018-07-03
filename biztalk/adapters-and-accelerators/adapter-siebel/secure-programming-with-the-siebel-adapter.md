---
title: 安全使用 Siebel 配接器進行程式設計 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security considerations, when programming on the adapter
- credentials, best practices for setting in code
- credentials, protecting when using the Add Adapter Service Reference Visual Studio Plug-in
- security, best practices for setting credentials in code
ms.assetid: 8c2b6b36-7bd9-4678-a9c2-450e818f607a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e7c96feecec12fa3962982faf81311cc9162e09
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986967"
---
# <a name="secure-programming-with-the-siebel-adapter"></a>安全使用 Siebel 配接器進行程式設計
## <a name="how-do-i-protect-credentials-when-i-use-the-add-adapter-service-reference-visual-studio-plug-in"></a>如何保護認證當我使用 新增配接器服務參考 Visual Studio 外掛程式？  
 當您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]若要建立的 WCF 用戶端，您必須提供使用者名稱和 Siebel 系統的密碼。 您應該只做這**安全性**索引標籤上**設定配接器** 對話方塊。 輸入 Siebel 的認證從**安全性**按下 tab 鍵而不是直接**Uri**  欄位中，確認下列：  
  
- 認證不會顯示在**Uri**欄位[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]對話方塊，其中以您的電腦螢幕的存取權的任何人都可以讀取它們。  
  
- 認證不會出現在組態檔[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。  
  
  如需有關如何使用來產生 WCF 用戶端[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，包括如何輸入 Siebel 系統的使用者名稱和密碼，請參閱 <<c2> [ 取得 Siebel 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)。  
  
## <a name="what-are-best-practices-for-setting-credentials-in-code"></a>在程式碼中的 設定認證的最佳作法有哪些？  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] 提供**ClientCredentials**類別，以協助您設定用戶端通訊物件，例如認證**ChannelFactory**，用來向服務驗證本身。 藉由使用**ClientCredentials**類別，您確定 WCF 會在該物件的通道堆疊中指定任何的驗證機制，並將它們套用到您的用戶端與服務之間的交換。  
  
 因為[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]裝載同處理序與其使用的應用程式，不一定需要使用**ClientCredentials**類別來設定認證，用戶端上使用應用程式所使用的通訊物件。 它是，不過，最佳做法進行此作業。  
  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]建議您使用**ClientCredentials**類別透過**AcceptCredentialsInUri**繫結屬性。 此屬性指定配接器是否將接受的使用者名稱和 Siebel 系統連接 URI 中的密碼。 **AcceptCredentialsInUri**預設為**false**，這表示，配接器會擲回例外狀況的連線 URI 包含認證。 您可以設定**AcceptCredentialsInUri**要 **，則為 true**提供連線 URI 中的認證。 事實上，您必須這麼做在某些情況下，例如，當您使用 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別的 Siebel 系統成品。  
  
 下列範例示範如何使用**認證**類別上設定 Siebel 系統的認證**ChannelFactory**。  
  
```  
// Create binding and endpoint  
SiebelBinding binding = new SiebelBinding();  
EndpointAddress endpointAddress = new EndpointAddress("siebel://Siebel_server:1234?SiebelObjectManager=obj_mgr&SiebelEnterpriseServer=entserver&Language=enu ");  
  
// Create the channel factory   
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, endpointAddress))  
  
// Set user name and password  
factory.Credentials.UserName.UserName = "YourUserName";  
factory.Credentials.UserName.Password = "YourPassword";  
  
// Open the channel factory  
factory.Open();  
```  
  
 下列範例示範如何使用**ClientCredentials**類別來設定 WCF 用戶端上的 Siebel 系統的認證。  
  
```  
// Initialize a new client for the SQLEXECUTE operation from configuration   
BusinessObjects_Account_Account_OperationClient accountAccountClient = new BusinessObjects_Account_Account_OperationClient ("SiebelBinding_BusinessObjects_Account_Account_Operation");  
  
// Set user name and password  
accountAccountClient.ClientCredentials.UserName.UserName = "YourUserName";  
accountAccountClient.ClientCredentials.UserName.Password = "YourPassword";  
  
// Open the client  
accountAccountClient.Open();  
```  
  
## <a name="how-can-i-provide-for-more-secure-data-exchange-across-process-boundaries"></a>如何跨處理序界限提供更安全的資料交換？  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]裝載同處理序的應用程式或取用它的服務。 因為配接器裝載同處理序與取用者，就不需要在取用者之間交換的訊息提供安全性和[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 不過，如果使用的應用程式或服務會傳送包含跨處理序界限，另一個服務或用戶端機密的資料庫資訊的訊息，您應該提供適當的保護，這項資料在您的環境中的量值。 [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] 提供許多選項來協助保護用戶端與服務之間傳送的訊息。 如需有關協助保護用戶端與服務之間傳送的訊息[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，請參閱 < [Securing Services and Clients](https://msdn.microsoft.com/library/ms734736.aspx)。 如需一般資訊的安全性功能[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供，請參閱 < [Windows Communication Foundation 安全性](https://msdn.microsoft.com/library/ms732362.aspx)。
  
## <a name="see-also"></a>另請參閱  
 [保護您的 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/secure-your-siebel-applications.md)  
[若要保護 Siebel 配接器的最佳作法](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md)