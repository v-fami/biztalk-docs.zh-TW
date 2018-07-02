---
title: 使用 Siebel 配接器的 WCF 服務模型的概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- how to, invoke operations on the Siebel system with a WCF client
- WCF service model, overview of
ms.assetid: 0e812473-0f50-4972-8b07-ec8edc2ef000
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f1b705b40cb5c7c78017f5a320a41ddb0cc1476
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969535"
---
# <a name="overview-of-the-wcf-service-model-with-the-siebel-adapter"></a>使用 Siebel 配接器的 WCF 服務模型概觀
[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]公開為 WCF 服務的 Siebel 系統。 若要執行作業在 Siebel 系統的成品，例如若要叫用方法的 Siebel 商務服務，您叫用的配接器，接著執行 Siebel 系統上執行的作業上的作業。 您的程式碼因此會做為配接器所呈現之 WCF 服務的用戶端。  
  
 在 [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型，為.NET 介面，表示用戶端與服務之間存在的服務合約和作業會表示成此介面上的方法。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]和 WCF 提供的工具，可讓您從配接器所公開的中繼資料產生此介面為目標的作業。 這些工具也會建立可用來叫用作業的服務介面中公開的 WCF 用戶端類別。 用戶端應用程式可以呼叫來叫用作業的介面卡上的 WCF 用戶端類別的方法。  
  
 下一節會說明如何使用 WCF 服務模型叫用 WCF 用戶端的作業。  
  
## <a name="invoking-operations-on-the-siebel-system-with-a-wcf-client"></a>針對 Siebel 系統與 WCF 用戶端叫用作業  
 若要使用 WCF 服務模型上叫用作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，您必須先產生 WCF 用戶端類別為目標的作業。 然後，您可以建立 WCF 用戶端，這個類別的執行個體，並呼叫其方法來執行這些作業在 Siebel 系統上。  
  
#### <a name="to-invoke-operations-on-the-siebel-adapter"></a>若要在 Siebel 介面卡上叫用作業  
  
1. 產生 WCF 用戶端類別和協助程式程式碼。 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 以產生 WCF 用戶端類別作為目標的 Siebel 系統成品與您想要使用。 如需如何產生 WCF 用戶端的詳細資訊，請參閱[Siebel 解決方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)。  
  
2. 建立 WCF 用戶端執行個體並設定 WCF 用戶端。 設定 WCF 用戶端包含指定的繫結和用戶端會使用的端點位址 （連線 URI）。 以命令方式在程式碼或是宣告式組態中，您可以這麼做。 如需如何設定 WCF 用戶端的詳細資訊，請參閱[Siebel 系統設定 WCF 用戶端](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md)。 下列程式碼會建立 WCF 用戶端為目標的時間戳記 Siebel 商務服務。 它也會設定針對 Siebel 系統的認證。 WCF 用戶端會從組態初始化。  
  
   ```  
   BusinessServices_TimeStamp_OperationClient client =  
       new BusinessServices_TimeStamp_OperationClient("SiebelBinding_BusinessServices_TimeStamp_Operation");  
  
   client.ClientCredentials.UserName.UserName = "YourUserName";  
   client.ClientCredentials.UserName.Password = "YourPassword";  
   ```  
  
3. 開啟 WCF 用戶端。  
  
   ```  
   client.Open();  
   ```  
  
4. 叫用 WCF 用戶端上步驟 2 中建立 Siebel 系統上執行作業的方法。 下列程式碼會叫用**Execute**方法來叫用的 WCF 用戶端**Execute** Siebel 系統上的時間戳記商務服務方法。  
  
   ```  
   // Create a parameter to hold the results and then invoke the Execute method of the TimeStamp business service.  
   microsoft.lobservices.siebel._2007._03.BusinessServices.TimeStamp.ExecuteResponseRecord er;  
   er = client.Execute();  
   ```  
  
5. 關閉 WCF 用戶端。  
  
   ```  
   client.Close();  
   ```  
  
   如需有關如何叫用 Siebel 商務服務方法的詳細資訊，請參閱[與 Siebel 配接器使用 WCF 服務模型中叫用商務服務方法](../../adapters-and-accelerators/adapter-siebel/run-business-service-methods-with-the-siebel-adapter-using-a-wcf-service.md) 
  
## <a name="see-also"></a>另請參閱  
 [開發使用 WCF 服務模型的 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)