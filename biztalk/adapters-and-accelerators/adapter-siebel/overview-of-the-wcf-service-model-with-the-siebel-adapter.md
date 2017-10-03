---
title: "Siebel 配接器之 WCF 服務模型的概觀 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, invoke operations on the Siebel system with a WCF client
- WCF service model, overview of
ms.assetid: 0e812473-0f50-4972-8b07-ec8edc2ef000
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c638255b103a9c588f22d6ddcb2a75b81619b73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-wcf-service-model-with-the-siebel-adapter"></a>Siebel 配接器之 WCF 服務模型的概觀
[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]公開為 WCF 服務的 Siebel 系統。 在 Siebel 系統成品，例如若要叫用方法的 Siebel 商務服務上執行作業您叫用的配接器，接著執行 Siebel 系統上的作業上的作業。 您的程式碼因此可做為配接器所呈現之 WCF 服務的用戶端。  
  
 在[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型時，用戶端和服務之間存在的服務合約以.NET 介面和作業會表示為此介面上的方法。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]和 WCF 提供的工具，可讓您從配接器會公開的中繼資料產生此介面為目標的作業。 這些工具也會建立 WCF 用戶端類別，可用於叫用的服務介面中公開的作業。 用戶端應用程式可以呼叫 WCF 用戶端類別，來叫用的介面卡上的作業的方法。  
  
 下節說明如何使用 WCF 服務模型來叫用的 WCF 用戶端的作業。  
  
## <a name="invoking-operations-on-the-siebel-system-with-a-wcf-client"></a>叫用 WCF 用戶端在 Siebel 系統的作業  
 若要使用 WCF 服務模型上叫用作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，您必須先產生目標作業的 WCF 用戶端類別。 然後，您可以建立 WCF 用戶端，這個類別的執行個體，並呼叫其方法來 Siebel 系統上執行這些作業。  
  
#### <a name="to-invoke-operations-on-the-siebel-adapter"></a>若要在 Siebel 介面卡上叫用作業  
  
1.  產生 WCF 用戶端類別和協助程式程式碼。 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別為目標的 Siebel 系統成品想要使用。 如需如何產生 WCF 用戶端的詳細資訊，請參閱[Siebel 方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)。  
  
2.  建立 WCF 用戶端執行個體並設定 WCF 用戶端。 設定 WCF 用戶端包含指定繫結與用戶端會使用的端點位址 （連線 URI）。 您可以在程式碼中以命令方式或是宣告式組態。 如需如何設定 WCF 用戶端的詳細資訊，請參閱[設定 WCF 用戶端在 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md)。 下列程式碼會建立 WCF 用戶端為目標的時間戳記 Siebel 商務服務。 它也會設定 Siebel 系統的認證。 WCF 用戶端會從設定初始化。  
  
    ```  
    BusinessServices_TimeStamp_OperationClient client =  
        new BusinessServices_TimeStamp_OperationClient("SiebelBinding_BusinessServices_TimeStamp_Operation");  
  
    client.ClientCredentials.UserName.UserName = "YourUserName";  
    client.ClientCredentials.UserName.Password = "YourPassword";  
    ```  
  
3.  開啟 WCF 用戶端。  
  
    ```  
    client.Open();  
    ```  
  
4.  叫用 WCF 用戶端上步驟 2 中建立 Siebel 系統上執行作業的方法。 下列程式碼會叫用**Execute**方法叫用的 WCF 用戶端**Execute** Siebel 系統上的時間戳記商務服務的方法。  
  
    ```  
    // Create a parameter to hold the results and then invoke the Execute method of the TimeStamp business service.  
    microsoft.lobservices.siebel._2007._03.BusinessServices.TimeStamp.ExecuteResponseRecord er;  
    er = client.Execute();  
    ```  
  
5.  關閉 WCF 用戶端。  
  
    ```  
    client.Close();  
    ```  
  
 如需叫用 Siebel 商務服務方法的詳細資訊，請參閱[叫用商務服務方法使用 Siebel 配接器使用 WCF 服務模型](../../adapters-and-accelerators/adapter-siebel/run-business-service-methods-with-the-siebel-adapter-using-a-wcf-service.md) 
  
## <a name="see-also"></a>另請參閱  
 [開發 Siebel 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)