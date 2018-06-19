---
title: 接收使用 WCF 服務 Model1 Oracle 資料庫的變更通知 |Microsoft 文件
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
ms.openlocfilehash: ed8723cef3351420cbe35e0f9fc85d2ba400b410
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217046"
---
# <a name="receive-oracle-database-change-notifications-using-the-wcf-service-model1"></a>接收使用 WCF 服務 Model1 Oracle 資料庫的變更通知
本主題示範如何設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]來從 Oracle 資料庫接收查詢通知訊息。 為了示範通知，請考慮的資料表，ACCOUNTACTIVITY，與 「 處理 」 資料行。 當新的記錄插入此資料表時，[狀態] 欄的值設定為 ' n '。 您可以設定要接收通知，請使用 SQL 陳述式可擷取所有記錄的 「 處理 」 資料行做為通知註冊配接器 ' n '。 您可以藉由指定的 SQL 陳述式**NotificationStatement**繫結屬性。 一旦配接器用戶端會收到通知，它可以包含執行的 Oracle 資料庫上的任何後續工作的邏輯。 在此範例中，為了簡單起見，配接器用戶端列出的 「 處理 」 資料行做為資料表中的所有記錄 ' n '。  
  
## <a name="configuring-notifications-with-the-oracle-database-adapter-binding-properties"></a>Oracle 資料庫配接器繫結屬性與設定通知  
 下表摘要說明[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結，您用來設定從 Oracle 資料庫接收通知的屬性。 您必須執行.NET 應用程式接收通知時指定這些繫結屬性。  
  
|繫結屬性|Description|  
|----------------------|-----------------|  
|**InboundOperationType**|指定輸入您想要執行的作業。 若要接收通知訊息，將此設**通知**。|  
|**NotificationPort**|指定 ODP.NET 必須開啟從 Oracle 資料庫的資料庫變更通知所接聽的通訊埠編號。|  
|**NotificationStatement**|指定用來註冊查詢通知的 SELECT 陳述式。 僅在結果集，指定 SELECT 陳述式變更時，配接器會取得通知訊息。|  
|**NotifyOnListenerStart**|指定是否配接器傳送通知給配接器用戶端啟動接聽程式時。|  
  
 如需這些屬性的更完整說明，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。 如需完整的說明，如何使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]進一步若要從 Oracle 資料庫接收通知，閱讀。  
  
## <a name="configuring-notifications-using-the-wcf-service-model"></a>設定通知使用 WCF 服務模型  
 若要接收通知使用 WCF 服務模型，您必須：  
  
-   產生 WCF 服務合約 （介面）**通知**從配接器所公開的中繼資料的作業。 若要這樣做，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
-   產生的 WCF 用戶端**選取**ACCOUNTACTIVITY 資料表上的作業。 若要這樣做，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
-   實作這個介面從 WCF 服務。  
  
-   裝載此 WCF 服務，使用服務主機 (**system.servicemodel.servicehost 內**)。  
  
## <a name="the-wcf-service-contract-and-class"></a>WCF 服務合約和類別  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]建立 WCF 服務合約 （介面） 和支援類別**通知**作業。 如需產生 WCF 服務合約的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 Oracle 資料庫方案成品](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。  
  
### <a name="the-wcf-service-contract-interface"></a>WCF 服務合約 （介面）  
 下列程式碼顯示產生的 WCF 服務合約 （介面）**通知**作業。  
  
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
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生虛設常式實作的服務合約 （介面） 的 WCF 服務類別的檔案。 檔案的名稱是 OracleDBBindingService.cs。 您可以插入要處理邏輯**通知**直接將這個類別的作業。 下列程式碼將示範所產生的 WCF 服務類別[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
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
  
1.  使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 用戶端**選取**作業**ACCOUNTACTIVITY**資料表。 您將使用此用戶端來接收通知訊息之後，執行 Select 作業。 加入新的類別，TableOperation.cs 至您的專案並加入下列程式碼片段來執行選取的作業。  
  
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
  
2.  使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 服務合約 （介面） 和協助程式類別，如**通知**作業。  
  
     如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 Oracle 資料庫方案成品](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。 您可以選擇性地產生服務合約和協助程式類別時指定的繫結屬性。 這可確保它們已正確設定在產生的組態檔中。  
  
3.  實作 WCF 服務，從步驟 2 中所產生的介面和協助程式類別。 **通知**這個類別的方法可以擲回例外狀況可中止此作業，處理從接收的資料發生錯誤**通知**作業; 否則方法會執行不會傳回任何項目。 您必須屬性 WCF 服務類別，如下所示：  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
     內**通知**方法，您可以直接實作應用程式邏輯。 這個類別可以 OracleDBBindingService.cs 中找到。 這段程式碼，在此範例中的子類別**OracleDBBindingService**類別。 在此程式碼中，接收的通知訊息會寫入主控台。 此外， **TableOp**方法內**TableOperation**類別會叫用來執行選取的作業。  
  
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
  
4.  您必須實作下列類別，以將 Oracle 資料庫的認證。 在應用程式的第二個部分中，您會具現化這個類別，以傳遞的認證。  
  
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
  
5.  建立**OracleDBBinding**和設定介面卡接收查詢通知所指定的繫結屬性。 您可以在程式碼中明確或是宣告式組態。 最少，您必須指定**InboundOperationType**和**NotificationStatement**繫結屬性。  
  
    ```  
    OracleDBBinding binding = new OracleDBBinding();  
    binding.InboundOperationType = InboundOperation.Notification;  
    binding.NotificationStatement = "SELECT TID,ACCOUNT,PROCESSED FROM APPS.ACCOUNTACTIVITY WHERE PROCESSED = 'n'";  
    binding.NotifyOnListenerStart = true;  
    binding.NotificationPort = 10;  
    ```  
  
    > [!IMPORTANT]
    >  值**NotificationPort**繫結屬性必須設定為相同的連接埠號碼，您必須已加入 Windows 防火牆例外清單。 如需如何將連接埠新增至 Windows 防火牆例外清單的指示，請參閱[http://go.microsoft.com/fwlink/?LinkId=196959](http://go.microsoft.com/fwlink/?LinkId=196959)。  
  
    > [!IMPORTANT]
    >  如果您未設定**NotificationPort**繫結屬性，配接器將假設使用預設值為-1，此繫結屬性。 在這種情況下，您必須完全停用 Windows 防火牆來接收通知訊息。  
  
6.  指定 Oracle 資料庫認證，藉由執行個體化**NotificationCredentials**您在步驟 4 中建立的類別。  
  
    ```  
    NotificationCredentials credentials = new NotificationCredentials();  
    credentials.UserName.UserName = "SCOTT";  
    credentials.UserName.Password = "TIGER";  
    ```  
  
7.  建立在步驟 3 中建立的 WCF 服務的執行個體。  
  
    ```  
    // create service instance  
    NotificationService service = new NotificationService();  
    ```  
  
8.  建立的執行個體**system.servicemodel.servicehost 內**使用 WCF 服務和基底的連線 URI。 您也必須指定的認證。  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("oracledb://adapter") };  
    ServiceHost serviceHost = new ServiceHost(service, baseUri);  
    serviceHost.Description.Behaviors.Add(credentials);  
  
    ```  
  
9. 將服務端點加入至服務主機。 若要這樣做：  
  
    -   使用步驟 5 中建立的繫結。  
  
    -   指定連線 URI，其中包含認證並在必要時輸入的識別碼。  
  
    -   為 「 Notification_OperationGroup"指定的合約。  
  
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
>  下列程式碼片段會具現化**TableOperation.cs**類別，並叫用**TableOp**方法。 在步驟 1 中描述的類別和方法。  
  
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