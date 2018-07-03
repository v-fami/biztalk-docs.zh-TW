---
title: 使用 WCF 服務模型的 Oracle 資料庫中接收以輪詢為基礎的資料變更訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, receiving polling-based messages
- how to, receive polling-based message
- polling-based messages, receiving by using the WCF service model
ms.assetid: 0324e8bf-d9d1-46f5-b896-b9fc8e61d514
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cda98a1600df28fab476114e697cd47e24316251
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012599"
---
# <a name="receive-polling-based-data-changed-messages-in-oracle-database-using-the-wcf-service-model"></a>使用 WCF 服務模型的 Oracle 資料庫中接收以輪詢為基礎的資料變更訊息
您可以設定[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]接收以輪詢為基礎的資料已變更的訊息時所依據的 Oracle 資料表或檢視表。 若要接收的資料變更訊息，配接器會定期執行的 Oracle 資料表或檢視，後面接著選擇性的 PL/SQL 程式碼區塊的 SQL 查詢。 SQL 查詢的結果則會傳回由[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]做為強類型的結果，在輸入的 POLLINGSTMT 作業中設定您的應用程式。 如需有關用來設定，然後在 Oracle 上執行輪詢機制資料庫使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 在 Oracle 資料庫配接器接收以輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md)。 我們強烈建議您先閱讀本主題後再繼續。  
  
 若要接收 POLLINGSTMT 作業，當您使用 WCF 服務模型時，您必須：  
  
- POLLINGSTMT 作業從配接器所公開的中繼資料產生 WCF 服務合約 （介面）。 若要這樣做，您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe)。  
  
- 實作此介面的 WCF 服務。  
  
- 裝載此 WCF 服務，使用服務主機 (**System.ServiceModel.ServiceHost**)。  
  
  在本節中的主題會提供資訊和程序可協助您對 Oracle 資料庫資料表和檢視 WCF 服務模型中的輪詢。  
  
## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例使用 /SCOTT/ACCOUNTACTIVITY 資料表和 /SCOTT/Package/ACCOUNT_PKG/PROCESS_ACTIVITY 函式。 指令碼來產生這些成品隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]範例。 如需有關範例的詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
## <a name="configuring-polling-in-the-wcf-service-model"></a>在 WCF 服務模型中設定輪詢  
 您設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]進行輪詢 Oracle 資料庫資料表和檢視表，藉由設定繫結屬性和選擇性的連接屬性 （參數）。 其中部分屬性是必要項目，以及一些造成影響，必須在設計階段和執行階段設定。  
  
- 在設計階段，您設定連線參數和繫結屬性當您連接到 Oracle 資料庫產生的 WCF 服務合約。  
  
- 在執行階段中，您會設定繫結屬性 OracleDBBinding 物件您用來建立服務主機上。 當您將服務接聽程式新增至服務主機，您可以設定連線參數。  
  
  下列清單提供的繫結屬性和用以設定輪詢的連接參數的簡短概觀：  
  
- **PollingStatement**繫結屬性。 在設計階段和執行階段，您必須設定這個繫結屬性。  
  
- 選擇性的繫結屬性。 這些只需要在執行階段進行設定。  
  
- **AcceptCredentialsInUri**繫結屬性。 您必須將此繫結屬性 **，則為 true**期間執行-如果您想要啟用的連線 URI 中的認證。 使用者名稱和密碼必須要有的連線 URI 中當您將服務端點新增至服務主機。  
  
- **PollingId**查詢字串參數，在 連線 URI。 如果您想要變更 POLLINGSTMT 作業的命名空間，您必須設定此連接屬性，在設計階段和執行階段。  
  
  繫結屬性和連接參數，用來設定輪詢的完整說明，請參閱[在 Oracle 資料庫配接器接收以輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md)。  
  
## <a name="the-wcf-service-contract-and-class"></a>類別與 WCF 服務合約  
 您可以使用任何一種[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來建立 WCF 服務合約 （介面），並支援 POLLINGSTMT 作業的類別。  
  
 當您連接到 Oracle 資料庫，使用這些工具來產生服務合約 POLLINGSTMT 作業：  
  
- 您必須指定**PollingStatement**繫結屬性。 配接器會使用此繫結屬性中的 SELECT 陳述式，來產生強型別結果集 POLLINGSTMT 作業所傳回正確的中繼資料。  
  
- 您可以選擇性地指定 PollingId 參數，在 連線 URI。 配接器會使用這個參數來產生 POLLINGSTMT 作業的命名空間。  
  
  在下列範例中：  
  
- **PollingStatement**設為"SELECT * 從 ACCOUNTACTIVITY FOR UPDATE"。  
  
- **PollingId**設為"AcctActivity 」。  
  
### <a name="the-wcf-service-contract-interface"></a>WCF 服務合約 （介面）  
 下列程式碼顯示 POLLINGSTMT 作業產生的 WCF 服務合約 （介面）。  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03", ConfigurationName="POLLINGSTMT_OperationGroup")]  
public interface POLLINGSTMT_OperationGroup {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity)  
    // of message POLLINGSTMT does not match the default value (http://Microsoft.LobServices.OracleDB/2007/03)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT")]  
    void POLLINGSTMT(POLLINGSTMT request);  
}  
```  
  
### <a name="the-message-contracts"></a>訊息合約  
 在 連線 URI PollingId 參數修改訊息合約命名空間。 要求訊息會傳回一組強型別的記錄。  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="POLLINGSTMT", WrapperNamespace="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity", IsWrapped=true)]  
public partial class POLLINGSTMT {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity", Order=0)]  
    public microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity.POLLINGSTMTRECORD[] POLLINGSTMTRECORD;  
  
    public POLLINGSTMT() {  
    }  
  
    public POLLINGSTMT(microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity.POLLINGSTMTRECORD[] POLLINGSTMTRECORD) {  
        this.POLLINGSTMTRECORD = POLLINGSTMTRECORD;  
    }  
}  
```  
  
### <a name="the-data-contract-namespace"></a>資料合約命名空間  
 資料合約是服務抽象地描述要交換資料的用戶端之間的正式合約。 也就是為了進行通訊，用戶端和服務就不必共用相同的類型，只有相同的資料合約。  
  
 發生資料變更訊息、 資料合約命名空間也修改 PollingId 參數 （如果有指定） 中的連線 URI。 資料合約是由表示強型別中的記錄查詢結果集的類別所組成。 在此範例中省略的類別定義的詳細資料。 此類別包含代表結果集中的資料行的屬性。  
  
 在下列範例中，會使用 PollingId"AcctActivity 」。  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity {  
    using System.Runtime.Serialization;  
  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute(Name="POLLINGSTMTRECORD", Namespace="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity")]  
    public partial class POLLINGSTMTRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {…}  
     }  
}  
```  
  
### <a name="wcf-service-class"></a>WCF 服務類別  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生已實作服務合約 （介面） 的 WCF 服務類別的虛設常式檔案。 OracleDBBindingService.cs 為檔案的名稱。 您可以插入處理 POLLINGSTMT 作業，直接將此類別的邏輯。 如果您使用 svcutil.exe 來產生服務合約介面時，您必須自行實作此類別。 下列程式碼會顯示所產生的 WCF 服務類別[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
```  
namespace OracleDBBindingNamespace {  
  
    public class OracleDBBindingService : POLLINGSTMT_OperationGroup {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity)   
        // of message POLLINGSTMT does not match the default value (http://Microsoft.LobServices.OracleDB/2007/03)  
        public virtual void POLLINGSTMT(POLLINGSTMT request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-the-pollingstmt-operation"></a>接收 POLLINGSTMT 作業  
  
#### <a name="to-receive-polling-data-from-the-oracle-database-adapter"></a>若要從 Oracle 資料庫配接器接收輪詢資料  
  
1. 使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或 svcutil.exe 產生 WCF 服務合約 （介面），並針對 POLLINGSTMT 作業的協助程式類別。 如需詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Oracle 資料庫解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。 至少，您必須設定**PollingStatement**繫結屬性，當您連接到配接器。 您可以選擇性地指定 PollingId 參數，在 連線 URI。 如果您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，您應該設定的所有繫結參數所需的組態。 這可確保它們已正確設定在產生的組態檔中。  
  
2. 實作 WCF 服務，從步驟 1 中所產生的介面和協助程式類別。 此類別的 POLLINGSTMT 方法可以擲回例外狀況處理從 POLLINGSTMT 作業; 接收的資料遇到錯誤時中止輪詢交易，否則方法沒有傳回任何項目。 WCF 服務類別必須屬性，如下所示：  
  
   ```  
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
   ```  
  
   1. 如果您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]若要產生的介面，您可以實作直接在您的邏輯**POLLINGSTMT**方法所產生**OracleDBBindingService**類別。 這個類別可以位於 OracleDBBindingService.cs。 此程式碼，在此範例中的子類別**OracleDBBindingService**類別。  
  
      ```  
      [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
      public class PollingStmtService : OracleDBBindingService  
      {  
          public override void POLLINGSTMT(POLLINGSTMT request)  
          {  
              Console.WriteLine("\nNew Polling Records Received");  
              Console.WriteLine("Tx Id\tAccount\tAmount\tDate\t\t\tDescription");  
              for (int i = 0; i < request.POLLINGSTMTRECORD.Length; i++)  
              {  
                  Console.WriteLine("{0}\t{1}\t{2}\t{3}\t{4}", request.POLLINGSTMTRECORD[i].TID,  
                                      request.POLLINGSTMTRECORD[i].ACCOUNT,  
                                      request.POLLINGSTMTRECORD[i].AMOUNT,  
                                      request.POLLINGSTMTRECORD[i].TRANSDATE,  
                                      request.POLLINGSTMTRECORD[i].DESCRIPTION);  
              }  
          }  
      }  
      ```  
  
   2. 如果您使用 svcutil.exe 來產生介面時，您必須建立實作介面的 WCF 服務，並實作您的邏輯中**POLLINGSTMT**這個類別的方法。  
  
3. 建立在步驟 2 中建立的 WCF 服務的執行個體。  
  
   ```  
   // create service instance  
   PollingStmtService pollingInstance = new PollingStmtService();  
   ```  
  
4. 建立的執行個體**System.ServiceModel.ServiceHost**使用 WCF 服務和基底的連線 URI。 基底的連線 URI 不能包含 userinfoparams 或 query_string。  
  
   ```  
   // Enable service host  
   Uri[] baseUri = new Uri[] { new Uri("oracledb://Adapter") };  
   ServiceHost srvHost = new ServiceHost(pollingInstance, baseUri);  
   ```  
  
5. 建立**OracleDBBinding**和設定輪詢作業設定其繫結屬性。 在程式碼中明確或是宣告式組態中，您可以這麼做。 至少，您必須指定輪詢陳述式和輪詢間隔。 在此範例中，您指定的認證為 URI 的一部分，因此您也必須設定**AcceptCredentialsInUri**要 **，則為 true**。  
  
   ```  
   // Create and configure a binding for the service endpoint. NOTE: binding  
   // parameters are set here for clarity, but these are already set in the  
   // the generated configuration file  
   OracleDBBinding binding = new OracleDBBinding();  
  
   // The credentials are included in the connection URI, so set this property to true  
   binding.AcceptCredentialsInUri = true;  
  
   // Same as statement specified in Configure Adapter dialog box  
   binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
   binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
   // Be sure to set the interval long enough to complete processing before  
   // the next poll  
   binding.PollingInterval = 15;  
   // Polling is transactional; be sure to set an adequate isolation level   
   // for your environment  
   binding.TransactionIsolationLevel = TransactionIsolationLevel.ReadCommitted;  
   ```  
  
6. 將服務端點加入至服務主機。 若要這樣做：  
  
   -   使用步驟 5 中建立的繫結。  
  
   -   指定連線 URI，其中包含認證並在必要時，PollingId。  
  
   -   為 「 POLLINGSTMT_OperationGroup"指定的合約。  
  
   ```  
   // Add service endpoint: be sure to specify POLLINGSTMT_OperationGroup as the contract  
   Uri serviceUri = new Uri("oracledb://User=SCOTT;Password=TIGER@Adapter?PollingId=AcctActivity");  
   srvHost.AddServiceEndpoint("POLLINGSTMT_OperationGroup", binding, serviceUri);  
   ```  
  
7. 若要收到輪詢資料，請開啟服務主機。 每當查詢傳回結果集時，配接器會傳回資料。  
  
   ```  
   // Open the service host to begin polling  
   srvHost.Open();  
   ```  
  
8. 若要終止輪詢，關閉服務主機。  
  
   > [!IMPORTANT]
   >  配接器將繼續輪詢直到關閉服務主機。  
  
   ```  
   srvHost.Close();  
   ```  
  
### <a name="example"></a>範例  
 下列範例顯示針對/SCOTT/ACCOUNTACTIVITY 資料表執行在有輪詢查詢。 後輪詢陳述式會叫用將已處理的記錄移至另一個資料表 /SCOTT/ACCOUNTHISTORY Oracle 函式。 修改 PollingId 將參數設定為"AccountActivity 」 中的連線 URI POLLINGSTMT 作業的命名空間。 在此範例中，WCF 服務 POLLINGSTMT 作業由分為子類別產生**OracleDBBindingService**類別; 不過，您可以直接在產生的類別中實作您的邏輯。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add these three references to use the Oracle adapter  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
using microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity;  
using OracleDBBindingNamespace;  
  
namespace OraclePollingSM  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingStmtService : OracleDBBindingService  
    {  
        public override void POLLINGSTMT(POLLINGSTMT request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("Tx Id\tAccount\tAmount\tDate\t\t\tDescription");  
            for (int i = 0; i < request.POLLINGSTMTRECORD.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}\t{4}", request.POLLINGSTMTRECORD[i].TID,  
                                    request.POLLINGSTMTRECORD[i].ACCOUNT,  
                                    request.POLLINGSTMTRECORD[i].AMOUNT,  
                                    request.POLLINGSTMTRECORD[i].TRANSDATE,  
                                    request.POLLINGSTMTRECORD[i].DESCRIPTION);  
  
            }  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
         }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost srvHost = null;  
  
            // This URI is used to specify the address for the ServiceEndpoint  
            // It must contain credentials and the PollingId (if any) that was used to generate  
            // the WCF service callback interface  
            Uri serviceUri = new Uri("OracleDb://User=SCOTT;Password=TIGER@Adapter?PollingId=AcctActivity");  
  
            // This URI is used to initialize the ServiceHost. It cannot contain  
            // userinfoparms (credentials) or a query_string (PollingId); otherwise,  
            // an exception is thrown when the ServiceHost is initialized.  
            Uri[] baseUri = new Uri[] { new Uri("OracleDb://Adapter") };  
  
            Console.WriteLine("Sample started, initializing service host -- please wait");  
  
            // create an instanc of the WCF service callback class  
            PollingStmtService pollingInstance = new PollingStmtService();  
  
            try  
            {  
                // Create a ServiceHost with the service callback instance and a base URI (address)  
                srvHost = new ServiceHost(pollingInstance, baseUri);  
  
                // Create and configure a binding for the service endpoint. Note: binding  
                // parameters are set here for clarity but these are already set in the  
                // generated configuration file  
                //  
                // The following properties are set  
                //    AcceptCredentialsInUri (true) to enable credentials in the connection URI for AddServiceEndpoint  
                //    PollingStatement  
                //    PostPollStatement calls PROCESS_ACTIVITY on Oracle. This procedure moves the queried records to  
                //                      the ACCOUNTHISTORY table  
                //    PollingInterval (15 seconds)  
                //    TransactionIsolationLevel   
  
                OracleDBBinding binding = new OracleDBBinding();  
  
                // The Credentials are included in the Connection Uri so set this property true  
                binding.AcceptCredentialsInUri = true;  
  
                // Same as statement specified in Configure Adapter dialog box  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
                binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
                // Be sure to set the interval long enough to complete processing before  
                // the next poll  
                binding.PollingInterval = 15;  
  
                // Polling is transactional, be sure to set an adequate isolation level   
                // for your environment  
                binding.TransactionIsolationLevel = TransactionIsolationLevel.ReadCommitted;  
  
                // Add service endpoint: be sure to specify POLLINGSTMT_OperationGroup as the contract  
                srvHost.AddServiceEndpoint("POLLINGSTMT_OperationGroup", binding, serviceUri);  
  
                Console.WriteLine("Opening the service host");  
                // Open the service host to begin polling  
                srvHost.Open();  
  
                // Wait to receive request  
                Console.WriteLine("\nPolling started. Returned records will be written to the console.");  
                Console.WriteLine("Hit <RETURN> to stop polling");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("Exception :" + e.Message);  
                Console.ReadLine();  
  
                /* If there is an Oracle Error it will be specified in the inner exception */  
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop polling  
                if (srvHost.State == CommunicationState.Opened)  
                    srvHost.Close();  
                else  
                    srvHost.Abort();  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [開發使用 WCF 服務模型的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)