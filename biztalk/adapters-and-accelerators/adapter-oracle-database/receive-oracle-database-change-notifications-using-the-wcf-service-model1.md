---
title: 接收使用 WCF 服務 Model1 Oracle 資料庫變更通知 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0f0e2bf-3e76-43cc-85dc-7483dbce1cb5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d980b13224918ae66d4ae35ec67f1bf3c3dba8ca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971087"
---
# <a name="receive-oracle-database-change-notifications-using-the-wcf-service-model1"></a>接收使用 WCF 服務 Model1 Oracle 資料庫變更通知
本主題示範如何設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]從 Oracle 資料庫接收查詢通知訊息。 為了示範通知，請考慮的資料表，ACCOUNTACTIVITY，「 處理 」 資料行。 此資料表插入新記錄時，[狀態] 欄的值設為 ' n '。 您可以設定要接收所使用的 SQL 陳述式會擷取所有記錄具有 「 處理 」 資料行做為註冊通知的通知的介面卡 ' n '。 則可以藉由指定的 SQL 陳述式**NotificationStatement**繫結屬性。 一旦配接器用戶端會收到通知，它可以包含執行的 Oracle 資料庫上的任何後續工作的邏輯。 在此範例中，為了簡單起見，配接器用戶端會列出 「 處理 」 資料行，做為資料表中的所有記錄 ' n '。  
  
## <a name="configuring-notifications-with-the-oracle-database-adapter-binding-properties"></a>使用 Oracle 資料庫配接器繫結屬性中設定通知  
 下表摘要說明[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結屬性，您用來設定從 Oracle 資料庫接收通知。 您必須執行.NET 應用程式，以接收通知時指定這些繫結屬性。  
  
|繫結屬性|描述|  
|----------------------|-----------------|  
|**InboundOperationType**|指定輸入您想要執行的作業。 若要接收通知訊息，將此設**通知**。|  
|**NotificationPort**|指定 ODP.NET 必須開啟以接聽從 Oracle 資料庫的資料庫變更通知的連接埠號碼。|  
|**NotificationStatement**|指定用來註冊查詢通知的 SELECT 陳述式。 配接器在結果集，指定 SELECT 陳述式變更時，才取得通知訊息。|  
|**NotifyOnListenerStart**|指定是否配接器傳送通知給配接器用戶端啟動接聽程式時。|  
  
 如需這些屬性的更完整說明，請參閱[Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。 如需完整的說明，如何使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]若要從 Oracle 資料庫接收通知，可深入閱讀。  
  
## <a name="configuring-notifications-using-the-wcf-service-model"></a>設定使用 WCF 服務模型的通知  
 若要接收通知使用 WCF 服務模型，您必須：  
  
- 產生的 WCF 服務合約 （介面），如**通知**從配接器所公開的中繼資料的作業。 若要這樣做，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
- 產生的 WCF 用戶端**選取**ACCOUNTACTIVITY 資料表上的執行作業。 若要這樣做，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
- 實作此介面的 WCF 服務。  
  
- 裝載此 WCF 服務，使用服務主機 (**System.ServiceModel.ServiceHost**)。  
  
## <a name="the-wcf-service-contract-and-class"></a>類別與 WCF 服務合約  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來建立 WCF 服務合約 （介面） 和支援類別**通知**作業。 如需有關如何產生 WCF 服務合約的詳細資訊，請參閱[產生 WCF 用戶端或 Oracle 資料庫解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。  
  
### <a name="the-wcf-service-contract-interface"></a>WCF 服務合約 （介面）  
 下列程式碼示範 WCF 服務合約 （介面） 產生**通知**作業。  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03", ConfigurationName="Notification_OperationGroup")]  
public interface Notification_OperationGroup {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.OracleDB/2007/03/Notification/) of message Notification  
    // does not match the default value (http://Microsoft.LobServices.OracleDB/2007/03)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="http://Microsoft.LobServices.OracleDB/2007/03/Notification")]  
    void Notification(Notification request);  
}  
```  
  
### <a name="the-message-contracts"></a>訊息合約  
 以下是通知作業的訊息合約。  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Notification", WrapperNamespace="http://Microsoft.LobServices.OracleDB/2007/03/Notification/", IsWrapped=true)]  
public partial class Notification {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03/Notification/", Order=0)]  
    public microsoft.lobservices.oracledb._2007._03.Notification.NotificationDetails[] Details;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03/Notification/", Order=1)]  
    public string Info;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03/Notification/", Order=2)]  
    public string[] ResourceNames;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03/Notification/", Order=3)]  
    public string Source;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03/Notification/", Order=4)]  
    public string Type;  
  
    public Notification() {  
    }  
  
    public Notification(microsoft.lobservices.oracledb._2007._03.Notification.NotificationDetails[] Details, string Info, string[] ResourceNames, string Source, string Type) {  
        this.Details = Details;  
        this.Info = Info;  
        this.ResourceNames = ResourceNames;  
        this.Source = Source;  
        this.Type = Type;  
    }  
}  
```  
  
### <a name="wcf-service-class"></a>WCF 服務類別  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生已實作服務合約 （介面） 的 WCF 服務類別的虛設常式檔案。 OracleDBBindingService.cs 為檔案的名稱。 您可以插入邏輯來處理**通知**直接將此類別的作業。 下列程式碼會顯示所產生的 WCF 服務類別[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
```  
namespace OracleDBBindingNamespace {  
  
    public class OracleDBBindingService : Notification_OperationGroup {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.OracleDB/2007/03/Notification/) of message Notification  
        // does not match the default value (http://Microsoft.LobServices.OracleDB/2007/03)  
        public virtual void Notification(Notification request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-database-change-notifications-using-wcf-service-model"></a>使用 WCF 服務模型的接收資料庫變更通知  
 本節說明如何撰寫.NET 應用程式接收查詢通知使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
#### <a name="to-receive-query-notifications"></a>若要接收查詢通知  
  
1. 使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生的 WCF 用戶端**選取**上的作業**ACCOUNTACTIVITY**資料表。 您將使用此用戶端接收到通知訊息後執行的 Select 作業。 加入新的類別，TableOperation.cs 至您的專案，並新增下列程式碼片段來執行選取的作業。  
  
   ```  
   using System;  
   using System.Collections.Generic;  
   using System.Linq;  
   using System.Text;  
  
   namespace Notification_ServiceModel  
   {  
       class TableOperation  
       {  
           public void TableOp()  
           {  
               //////////////////////////////////////////////////////////////////////  
               // CREATING THE CLIENT AND SETTING CLIENT CREDENTIALS  
               //////////////////////////////////////////////////////////////////////  
  
               SCOTT_Table_ACCOUNTACTIVITYClient client = new SCOTT_Table_ACCOUNTACTIVITYClient("OracleDBBinding_SCOTT_Table_ACCOUNTACTIVITY");  
               client.ClientCredentials.UserName.UserName = "SCOTT";  
               client.ClientCredentials.UserName.Password = "TIGER";  
  
               ////////////////////////////////////////////////////////////////////  
               // OPENING THE CLIENT  
               //////////////////////////////////////////////////////////////////////  
               try  
               {  
                   Console.WriteLine("Opening the client ...");  
                   client.Open();  
               }  
               catch (Exception ex)  
               {  
                   Console.WriteLine("Exception: " + ex.Message);  
                   throw;  
               }  
  
               ////////////////////////////////////////////////////////////////////////////////////////  
               // SELECTING THE LAST INSERTED VALUE  
               ////////////////////////////////////////////////////////////////////////////////////////  
  
               Console.WriteLine("The application will now select the last inserted record");  
  
               microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] selectRecords;  
  
               try  
               {  
                   selectRecords = client.Select("*", "WHERE PROCESSED = 'n'");  
               }  
               catch (Exception ex)  
               {  
                   Console.WriteLine("Exception: " + ex.Message);  
                   throw;  
               }  
  
               Console.WriteLine("The details of the newly added records are:");  
               Console.WriteLine("********************************************");  
               for (int i = 0; i < selectRecords.Length; i++)  
               {  
                   Console.WriteLine("Transaction ID   : " + selectRecords[i].TID);  
                   Console.WriteLine("Account ID       : " + selectRecords[i].ACCOUNT);  
                   Console.WriteLine("Processed Status : " + selectRecords[i].PROCESSED);  
                   Console.WriteLine();  
               }  
               Console.WriteLine("********************************************");  
           }  
       }  
   }  
  
   ```  
  
2. 使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生的 WCF 服務合約 （介面） 和 helper 類別**通知**作業。  
  
    如需詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Oracle 資料庫解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。 產生服務合約和協助程式類別時，您可以選擇指定的繫結屬性。 這可確保它們已正確設定在產生的組態檔中。  
  
3. 實作 WCF 服務，從步驟 2 中所產生的介面和協助程式類別。 **通知**此類別的方法可以擲回例外狀況可中止此作業，處理從收到的資料時發生錯誤**通知**作業; 否則這個方法將沒有不傳回任何項目。 WCF 服務類別必須屬性，如下所示：  
  
   ```  
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
   ```  
  
    內**通知**方法中，您可以直接實作應用程式邏輯。 這個類別可以位於 OracleDBBindingService.cs。 此程式碼，在此範例中的子類別**OracleDBBindingService**類別。 在此程式碼中，收到的通知訊息會寫入至主控台。 此外， **TableOp**方法內**TableOperation**類別會叫用來執行選取作業。  
  
   ```  
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
       public class NotificationService : OracleDBBindingNamespace.OracleDBBindingService  
       {  
           public override void Notification(Notification request)  
           {  
               Console.WriteLine("\nNew Notification Received");  
               Console.WriteLine("*************************************************");  
               Console.WriteLine(request.Info);  
               Console.WriteLine(request.Source);  
               Console.WriteLine(request.Type);  
               Console.WriteLine("*************************************************");  
  
               TableOperation Ops = new TableOperation();  
               Ops.TableOp();  
  
           }  
       }  
   ```  
  
4. 您必須實作下列的類別，以將 Oracle 資料庫的認證。 在應用程式的後半部，您將會具現化這個類別，以傳遞的認證。  
  
   ```  
   class NotificationCredentials : ClientCredentials, IServiceBehavior  
   {  
       public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
       {  
           bindingParameters.Add(this);  
       }  
  
       public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
       { }  
  
       public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
       { }  
  
       protected override ClientCredentials CloneCore()  
       {  
           ClientCredentials clone = new NotificationCredentials();  
           clone.UserName.UserName = this.UserName.UserName;  
           clone.UserName.Password = this.UserName.Password;  
           return clone;  
       }  
   }  
   ```  
  
5. 建立**OracleDBBinding**和設定配接器接收查詢通知，藉由指定的繫結屬性。 在程式碼中明確或是宣告式組態中，您可以這麼做。 至少，您必須指定**InboundOperationType**並**NotificationStatement**繫結屬性。  
  
   ```  
   OracleDBBinding binding = new OracleDBBinding();  
   binding.InboundOperationType = InboundOperation.Notification;  
   binding.NotificationStatement = "SELECT TID,ACCOUNT,PROCESSED FROM APPS.ACCOUNTACTIVITY WHERE PROCESSED = 'n'";  
   binding.NotifyOnListenerStart = true;  
   binding.NotificationPort = 10;  
   ```  
  
   > [!IMPORTANT]
   >  值**NotificationPort**繫結屬性必須設為相同的連接埠號碼，您必須已加入的 Windows 防火牆例外清單。 如需如何將 Windows 防火牆例外清單中的連接埠的指示，請參閱 < [ http://go.microsoft.com/fwlink/?LinkId=196959 ](http://go.microsoft.com/fwlink/?LinkId=196959)。  
  
   > [!IMPORTANT]
   >  如果您未設定**NotificationPort**繫結屬性，配接器會假設為-1，此繫結屬性的預設值。 在此情況下，您必須完全停用 Windows 防火牆，以接收通知訊息。  
  
6. 指定 Oracle 資料庫認證，藉由執行個體化**NotificationCredentials**您在步驟 4 中建立的類別。  
  
   ```  
   NotificationCredentials credentials = new NotificationCredentials();  
   credentials.UserName.UserName = "SCOTT";  
   credentials.UserName.Password = "TIGER";  
   ```  
  
7. 建立在步驟 3 中建立的 WCF 服務的執行個體。  
  
   ```  
   // create service instance  
   NotificationService service = new NotificationService();  
   ```  
  
8. 建立的執行個體**System.ServiceModel.ServiceHost**使用 WCF 服務和基底的連線 URI。 您也必須指定的認證。  
  
   ```  
   // Enable service host  
   Uri[] baseUri = new Uri[] { new Uri("oracledb://adapter") };  
   ServiceHost serviceHost = new ServiceHost(service, baseUri);  
   serviceHost.Description.Behaviors.Add(credentials);  
  
   ```  
  
9. 將服務端點加入至服務主機。 若要這樣做：  
  
   - 使用步驟 5 中建立的繫結。  
  
   - 指定連線 URI，其中包含認證並在必要時輸入的識別碼。  
  
   - 為 「 Notification_OperationGroup"指定的合約。  
  
     ```  
     // Add service endpoint: be sure to specify Notification_OperationGroup as the contract  
     Uri ConnectionUri = new Uri("oracledb://adapter");  
     serviceHost.AddServiceEndpoint("Notification_OperationGroup", binding, ConnectionUri);  
     ```  
  
10. 若要收到通知訊息，請開啟服務主機。  
  
    ```  
    // Open the service host to begin receiving notifications  
    serviceHost.Open();  
    ```  
  
11. 若要停止接收通知，請關閉服務主機。  
  
    ```  
    serviceHost.Close();  
    ```  
  
### <a name="example"></a>範例  
 下列範例會示範.NET 應用程式來接收通知訊息 ACCOUNTACTIVITY 資料表。  
  
> [!NOTE]
>  下列程式碼片段會具現化**TableOperation.cs**類別，並叫用**TableOp**方法。 在步驟 1 中詳述的類別和方法。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.Adapters.OracleDB;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Collections.ObjectModel;  
  
namespace Notification_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class NotificationService : OracleDBBindingNamespace.OracleDBBindingService  
    {  
        public override void Notification(Notification request)  
        {  
            Console.WriteLine("\nNew Notification Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine(request.Info);  
            Console.WriteLine(request.Source);  
            Console.WriteLine(request.Type);  
            Console.WriteLine("*************************************************");  
  
            TableOperation Ops = new TableOperation();  
            Ops.TableOp();  
  
        }  
    }  
  
    class NotificationCredentials : ClientCredentials, IServiceBehavior  
    {  
        public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
        {  
            bindingParameters.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        protected override ClientCredentials CloneCore()  
        {  
            ClientCredentials clone = new NotificationCredentials();  
            clone.UserName.UserName = this.UserName.UserName;  
            clone.UserName.Password = this.UserName.Password;  
            return clone;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost serviceHost = null;  
            try  
            {  
                Console.WriteLine("Sample started...");  
                Console.WriteLine("Press any key to start receiving notifications...");  
                Console.ReadLine();  
  
                OracleDBBinding binding = new OracleDBBinding();  
                binding.InboundOperationType = InboundOperation.Notification;  
                binding.NotificationStatement = "SELECT TID,ACCOUNT,PROCESSED FROM APPS.ACCOUNTACTIVITY WHERE PROCESSED = 'n'";  
                binding.NotifyOnListenerStart = true;  
                binding.NotificationPort = 10;  
  
                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("oracledb://adapter");  
  
                // This URI is used to initialize the ServiceHost. It cannot contain  
                // an InboundID; otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("oracledb://adapter") };  
  
                NotificationCredentials credentials = new NotificationCredentials();  
                credentials.UserName.UserName = "SCOTT";  
                credentials.UserName.Password = "TIGER";  
  
                Console.WriteLine("Opening service host...");  
                NotificationService service = new NotificationService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("Notification_OperationGroup", binding, ConnectionUri);  
                serviceHost.Open();  
                Console.WriteLine("Service host opened...");  
                Console.WriteLine("Waiting for notification...");  
  
                Console.WriteLine("\nHit <RETURN> to stop receiving notification");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("Exception :" + e.Message);  
                Console.ReadLine();  
  
                /* If there is an error it will be specified in the inner exception */  
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop polling  
                if (serviceHost.State == CommunicationState.Opened)  
                    serviceHost.Close();  
                else  
                    serviceHost.Abort();  
            }  
  
        }  
    }  
}  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [開發使用 WCF 服務模型的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)