---
title: 使用 SAP 配接器的 WCF 服務模型的概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, overview of using
ms.assetid: 02a4b43e-ade0-4dba-b8f6-074bca7cbe5c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd204cc7ad0b588a778fdbbbb6e4a61d884da231
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967480"
---
# <a name="overview-of-the-wcf-service-model-with-the-sap-adapter"></a>SAP 配接器使用 WCF 服務模型的概觀
當您使用作業，[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]介面，您的程式碼做為用戶端或服務，配接器。  
  
 您的程式碼做為用戶端來叫用下列類型的 SAP 系統上的作業：  
  
- 叫用遠端函式呼叫 (RFC)。  
  
- 叫用交易式遠端函式呼叫 (tRFC)。  
  
- 叫用的程式設計介面 」 (BAPI) 的商務應用程式。  
  
- 傳送的中繼文件 (IDOC)  
  
  您的程式碼做為服務，以接收下列種類的作業：  
  
- 接收的 RFC （RFC 伺服器）  
  
- 接收 tRFC （tRFC 伺服器）  
  
- 接收 IDOC。  
  
> [!NOTE]
>  因為 Bapi 是位於商務物件存放庫 (BOR) 中的商務物件中的 SAP 系統所公開的方法，您就無法接收 Bapi。  
  
 在 [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型，為.NET 介面，表示用戶端與服務之間存在的服務合約和作業會表示成此介面上的方法。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]和 WCF 提供的工具，可讓您從配接器所公開的中繼資料產生此介面為目標的作業。 這些工具也會建立可用來叫用作業的服務介面中公開的 WCF 用戶端類別。 用戶端應用程式可以呼叫來叫用作業的介面卡上的 WCF 用戶端類別的方法。 若要實作服務，以接收來自作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，實作目標作業產生的介面。  
  
 下列各節將說明如何使用 WCF 服務模型，以建立用戶端與服務程式碼[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="creating-a-wcf-client-and-invoking-operations-on-sap"></a>建立 WCF 用戶端和針對 SAP 叫用作業  
 若要使用 WCF 服務模型上叫用作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，您必須先產生 WCF 用戶端類別為目標的作業。 然後，您可以建立 WCF 用戶端，這個類別的執行個體，並呼叫其方法來執行 SAP 系統上的作業。  
  
#### <a name="to-invoke-operations-on-the-sap-adapter"></a>若要叫用 SAP 配接器上的作業  
  
1. 產生 WCF 用戶端類別和協助程式程式碼。 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 以產生 WCF 用戶端類別作為目標的 SAP 系統成品與您想要使用。 如需如何產生 WCF 用戶端的詳細資訊，請參閱[產生 WCF 用戶端或 SAP 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
2. 指定用戶端繫結，以建立 WCF 用戶端執行個體。 指定用戶端繫結牽涉到指定的繫結和 WCF 用戶端將使用的端點位址。 以命令方式在程式碼或是宣告式組態中，您可以這麼做。 如需如何指定用戶端繫結的詳細資訊，請參閱[設定用戶端繫結 SAP 系統的](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md)。 下列程式碼會建立可用來叫用 RFC，SAP 系統上的 WCF 用戶端。 它也會設定 SAP 系統的認證。 WCF 用戶端會從組態初始化。  
  
   ```  
   RfcClient rfcClient = new RfcClient("SAPBinding_Rfc");  
  
   rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
   rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
   ```  
  
3. 開啟 WCF 用戶端。  
  
   ```  
   rfcClient.Open();  
   ```  
  
4. 叫用 WCF 用戶端上步驟 2 中建立 SAP 系統上執行作業的方法。 下列程式碼會叫用**SD_RFC_CUSTOMER_GET**叫用 RFC，SAP 系統上的 WCF 用戶端的方法。  
  
   ```  
   microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] customers =   
       new microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[0];  
  
   rfcClient.SD_RFC_CUSTOMER_GET(string.Empty, "AB*", ref customers);  
   ```  
  
5. 關閉 WCF 用戶端。  
  
   ```  
   rfcClient.Close();  
  
   ```  
  
## <a name="creating-and-implementing-a-wcf-service-by-using-the-sap-adapter"></a>建立和使用 SAP 配接器實作的 WCF 服務  
 接收從作業中使用 WCF 服務模型[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，您必須先產生代表服務合約所公開的.NET 介面 （也稱為 WCF 服務合約）[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]作業。 如需如何執行這項操作的詳細資訊，請參閱[產生 WCF 用戶端或 SAP 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
 然後，您會實作 WCF 服務藉由實作產生的介面。 這個類別包含的商務邏輯來處理作業，並將回應傳回給配接器。 接著，您使用的服務主機 (**System.ServiceModel.ServiceHost**) 來裝載此服務的執行個體。  
  
#### <a name="to-create-and-implement-a-wcf-service"></a>建立和實作的 WCF 服務  
  
1. 產生 WCF 服務合約和協助程式類別。 使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或 svcutil.exe 產生您想要使用的 SAP 系統成品適用對象的 WCF 服務合約 （介面）。 如需如何產生 WCF 用戶端的詳細資訊，請參閱[產生 WCF 用戶端或 SAP 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
2. 實作 WCF 服務，從步驟 1 中所產生的介面和協助程式類別。 如果處理作業的資料時發生錯誤，處理該作業的方法可以擲回例外狀況到部署 SAP 系統; 會傳回錯誤否則此方法必須傳回作業的適當 （產生） 的回應類別的執行個體。 WCF 服務類別必須屬性，如下所示：  
  
   ```  
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
   ```  
  
   1. 如果您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]若要產生的介面，您可以直接在適當的方法，在產生實作您的邏輯**SAPBindingService**類別。 這個類別可以位於 SAPBindingService.cs。 下列程式碼的子類別**SAPBindingService**類別。  
  
      ```  
      [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single,UseSynchronizationContext = false)]  
      class RfcServerClass : SAPBindingNamespace.SAPBindingService  
      {  
          public override Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request)  
          {  
              // If either parameter is null throw an exception   
              if (request.X == null || request.Y == null)  
                  throw new System.ArgumentNullException();  
  
              // Add the two operands  
              int result = (int) (request.X + request.Y);  
  
              return new Z_RFC_MKD_ADDResponse(result);  
          }  
      }  
      ```  
  
   2. 如果您使用 svcutil.exe 來產生介面時，您必須建立可實作介面的類別，並在這個類別的 appropriatemethod 中實作您的邏輯。  
  
3. 建立在步驟 2 中建立的 WCF 服務的執行個體。  
  
   ```  
   // create service instance  
   RfcServerClass rfcServerInstance = new RfcServerClass();  
   ```  
  
4. 建立的執行個體**System.ServiceModel.ServiceHost**使用 WCF 服務和基底的連線 URI。 基底的連線 URI 不能包含 userinfoparams 或 query_string。  
  
   ```  
   // Enable service host  
   Uri[] baseUri = new Uri[] { new Uri("sap://a/YourSAPHost/00") };  
   ServiceHost srvHost = new ServiceHost(pollingInstance, baseUri);  
   ```  
  
5. 建立**SAPBinding**並將它設定作業中，藉由設定其繫結屬性。 在程式碼中明確或是宣告式組態中，您可以這麼做。 至少，您必須設定**AcceptCredentialsInUri**要 **，則為 true**。  
  
   ```  
   // Create and configure a binding for the service endpoint. NOTE: binding  
   // parameters are set here for clarity, but these are already set in the  
   // the generated configuration file  
   SAPBinding binding = new SAPBinding();  
  
   // The credentials are included in the connection URI, so set this property to true  
   binding.AcceptCredentialsInUri = true;  
   ```  
  
6. 將服務端點加入至服務主機。 若要這樣做：  
  
   -   使用步驟 5 中建立的繫結。  
  
   -   指定連線 URI，包含認證，而且指定的接聽程式連接 （SAP 閘道，閘道服務和程式識別碼） query_string 中。 如需有關 SAP 連線 URI 的詳細資訊，請參閱[建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。  
  
   -   指定服務合約。 這是代表 WCF 服務合約介面的名稱。 Rfc，對於 「 Rfc"。  
  
   ```  
   // Add service endpoint   
   // NOTE: The contract for the service endpoint is "Rfc".  
   //       This is the generated WCF service contract (interface) -- see SAPBindingInterface.cs.  
   Uri serviceUri = new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGW00&ListenerGwHost=YourSapHost&ListenerProgramId=SAPAdapter");  
   srvHost.AddServiceEndpoint("Rfc", binding, serviceUri);  
   ```  
  
7. 若要從 SAP 系統接收作業，開啟服務主機。 您的 WCF 服務就會叫用 SAP 系統會叫用程式 ID 和步驟 6 中的服務 URI 中指定的系統的作業。  
  
   ```  
   // Open the service host to begin receiving the operation.  
   srvHost.Open();  
   ```  
  
8. 若要停止接收作業，關閉服務主機。  
  
   > [!IMPORTANT]
   >  配接器會繼續接收作業，直到關閉服務主機。 當您不再想要接收作業時，應該一律會關閉服務主機。  
  
   ```  
   srvHost.Close();  
   ```  
  
## <a name="see-also"></a>另請參閱  
[開發使用 WCF 服務模型的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)