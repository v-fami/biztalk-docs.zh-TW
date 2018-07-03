---
title: 使用 WCF 服務模型的 SQL Server 從接收以輪詢為基礎的資料變更訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8713dd38-65ff-4d89-b23b-a93c06c5ff22
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47e7ddbd3270019fee68659cb36047f7084c356d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988415"
---
# <a name="receive-polling-based-data-changed-messages-from-sql-server-using-the-wcf-service-model"></a>使用 WCF 服務模型的 SQL Server 從接收以輪詢為基礎的資料變更訊息
您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收 SQL Server 資料表或檢視表的定期的資料變更訊息。 您可以指定要輪詢的資料庫執行的配接器的輪詢陳述式。 輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。  

 如需有關配接器如何支援輪詢的詳細資訊，請參閱[在使用 SQL 配接器的 SQL Server 中輪詢](../../adapters-and-accelerators/adapter-sql/polling-in-sql-server-using-the-sql-adapter.md)。  

> [!NOTE]
>  本主題示範如何使用**輪詢**輸入作業使用輪詢訊息。 輪詢作業的訊息是不強型別。 如果您想要取得強型別輪詢訊息時，您必須使用**TypedPolling**作業。 您也必須使用**TypedPolling**單一應用程式中有多個輪詢作業的作業。 如需有關如何執行**TypedPolling**作業，請參閱[接收強型別輪詢為基礎的資料變更訊息從 SQL Server 使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-sql-messages-with-wcf-service.md)。  

> [!IMPORTANT]
>  如果您想要在單一應用程式中有一個以上的輪詢作業，您必須指定**InboundID**一部分的連線 URI，使其成為唯一的連接屬性。 您指定的輸入的識別碼會新增至作業命名空間，使其成為唯一。  

## <a name="how-this-topic-demonstrates-polling"></a>本主題將輪詢的示範  
 本主題中，以示範如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援的接收資料變更訊息，建立.NET 應用程式，並產生的 WCF 服務合約**輪詢**作業。 如果您想要指定輪詢相關的屬性繫結產生 WCF 服務合約時，指定**PolledDataAvailableStatement**為：  

```  
SELECT COUNT(*) FROM Employee  
```  

 **PolledDataAvailableStatement**必須傳回含有包含正值的第一個儲存格的結果集。 如果第一個資料格不包含正值，配接器不會執行輪詢陳述式。  

 輪詢陳述式的一部分，執行下列作業：  

1. 從 [員工] 資料表中選取所有資料列。  

2. 執行預存程序 (MOVE_EMP_DATA) 將從 Employee 資料表的所有記錄都移至 EmployeeHistory 資料表。  

3. 執行預存程序 (ADD_EMP_DETAILS)，將新記錄新增至 [員工] 資料表。 此程序會接受員工名稱、 指定和薪資做為參數。  

   若要執行這些作業，您必須指定下列**PollingStatement**繫結屬性：  

```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  

 執行輪詢陳述式之後，選取從 Employee 資料表的所有記錄，而且會在收到來自 SQL Server 的訊息。 MOVE_EMP_DATA 預存程序執行的配接器之後，所有的記錄會移至 EmployeeHistory 資料表。 然後，會執行 ADD_EMP_DETAILS 預存程序，將新記錄新增至 [員工] 資料表。 下一個輪詢執行只會傳回單一記錄。 此週期會持續直到您關閉服務主機。  

## <a name="configuring-a-polling-query-with-the-sql-adapter-binding-properties"></a>使用 SQL 配接器繫結屬性中設定輪詢查詢  
 下表摘要說明[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結屬性，您用來設定配接器接收資料變更訊息。 輪詢的.NET 應用程式的一部分，您必須指定這些繫結屬性。  


|         繫結屬性         |                                                                                                                                                                                                                                         描述                                                                                                                                                                                                                                          |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     **InboundOperationType**     |                                                                                                                                                                             指定是否要執行**輪詢**， **TypedPolling**，或**通知**輸入作業。 預設值是**輪詢**。                                                                                                                                                                              |
| **PolledDataAvailableStatement** |                                                                                       指定配接器執行，以判斷是否有任何資料可供輪詢 SQL 陳述式。 SQL 陳述式必須傳回的結果集資料列和資料行所組成。 如果可用的資料列，為指定的 SQL 陳述式僅**PollingStatement**屬性繫結將會執行。                                                                                       |
|   **PollingIntervalInSeconds**   |                         指定間隔 （秒），此時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。 預設值是 30 秒。 輪詢間隔會決定後續輪詢間隔的時間間隔。 如果指定的間隔內執行的陳述式，則配接器會等候剩餘的時間間隔中。                          |
|       **PollingStatement**       | 指定輪詢 SQL Server 資料庫資料表的 SQL 陳述式。 您可以指定簡單的 SELECT 陳述式或輪詢陳述式的預存程序。 預設值是 null。 您必須指定的值**PollingStatement**啟用輪詢。 輪詢陳述式在沒有可供輪詢，取決於使用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。 您可以指定任意數目的 SQL 陳述式以分號分隔。 |
|      **PollWhileDataFound**      |                            指定是否[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]忽略的輪詢間隔，並持續執行 SQL 陳述式指定**PolledDataAvailableStatement**繫結屬性，如果資料可在所輪詢的資料表。 如果沒有資料可在資料表中，配接器會還原為執行 SQL 陳述式，在指定的輪詢間隔。 預設值是**false**。                             |

 如需這些屬性的更完整說明，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 如需完整的說明，如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]輪詢 SQL Server，可深入閱讀。  

## <a name="configuring-polling-in-the-wcf-service-model"></a>在 WCF 服務模型中設定輪詢  
 若要接收**輪詢**作業使用 WCF 服務模型時，您必須：  

1. 產生的 WCF 服務合約 （介面），如**輪詢**從配接器所公開的中繼資料的作業。 若要這樣做，您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。  

2. 實作此介面的 WCF 服務。  

3. 裝載此 WCF 服務，使用服務主機 (**System.ServiceModel.ServiceHost**)。  

## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例輪詢 Employee 資料表。 此範例也會使用 MOVE_EMP_DATA 和 ADD_EMP_DETAILS 預存程序。 指令碼來產生這些成品會提供範例。 如需有關範例的詳細資訊，請參閱 < [SQL 配接器的範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。 範例中， **Polling_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。  

## <a name="the-wcf-service-contract-and-class"></a>類別與 WCF 服務合約  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來建立 WCF 服務合約 （介面） 和支援類別**輪詢**作業。 如需有關如何產生 WCF 服務合約的詳細資訊，請參閱[產生的 SQL Server 成品的 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。  

### <a name="the-wcf-service-contract-interface"></a>WCF 服務合約 （介面）  
 下列程式碼示範 WCF 服務合約 （介面） 產生**輪詢**作業。  

```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/", ConfigurationName="PollingOperation")]  
public interface PollingOperation {  

    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/Polling/) of message Polling  
    // does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="Polling")]  
    [System.ServiceModel.XmlSerializerFormatAttribute()]  
    void Polling(Polling request);  
}  
```  

### <a name="the-message-contracts"></a>訊息合約  
 訊息合約命名空間會修改**InboundID**中的連線 URI，如果指定的參數。 在此範例中，您未指定連線 URI 中的輸入的識別碼。 要求訊息中傳回的資料集。  

```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Polling", WrapperNamespace="http://schemas.microsoft.com/Sql/2008/05/Polling/", IsWrapped=true)]  
public partial class Polling {  

[System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/Polling/", Order=0)]  
    [System.Xml.Serialization.XmlArrayAttribute(IsNullable=true)]  
    [System.Xml.Serialization.XmlArrayItemAttribute("DataSet", Namespace="http://schemas.datacontract.org/2004/07/System.Data", IsNullable=false)]  
    public System.Data.DataSet[] PolledData;  

    public Polling() {  
    }  

    public Polling(System.Data.DataSet[] PolledData) {  
        this.PolledData = PolledData;  
    }  
}  
```  

### <a name="wcf-service-class"></a>WCF 服務類別  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生已實作服務合約 （介面） 的 WCF 服務類別的虛設常式檔案。 SqlAdapterBindingService.cs 為檔案的名稱。 您可以插入邏輯來處理**輪詢**直接將此類別的作業。 下列程式碼會顯示所產生的 WCF 服務類別[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  

```  
namespace SqlAdapterBindingNamespace {  

    public class SqlAdapterBindingService : PollingOperation {  

        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/Polling/) of message Polling   
        // does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
        public virtual void Polling(Polling request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  

## <a name="receiving-inbound-messages-for-polling-operation"></a>輪詢作業接收內送的訊息  
 本節說明如何撰寫.NET 應用程式以接收輸入的輪詢訊息使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  

#### <a name="to-receive-polling-messages-from-the-sql-adapter"></a>若要從 SQL 配接器接收輪詢訊息  

1. 使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生的 WCF 服務合約 （介面） 和 helper 類別**輪詢**作業。 如需詳細資訊，請參閱 <<c0> [ 產生的 SQL Server 成品的 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。 產生服務合約和協助程式類別時，您可以選擇指定的繫結屬性。 這可確保它們已正確設定在產生的組態檔中。  

2. 實作 WCF 服務，從步驟 1 中所產生的介面和協助程式類別。 **輪詢**此類別的方法可以擲回例外狀況中止輪詢交易，處理從收到的資料時發生錯誤**輪詢**作業; 否則這個方法將沒有不傳回任何項目。 WCF 服務類別必須屬性，如下所示：  

   ```  
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
   ```  

    內**輪詢**方法中，您可以直接實作應用程式邏輯。 這個類別可以位於 SqlAdapterBindingService.cs。 此程式碼，在此範例中的子類別**SqlAdapterBindingService**類別。 在此程式碼，做為資料集所收到的輪詢訊息會寫入主控台。  

   ```  
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  

   public class PollingService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
   {  

   public override void Polling(Polling request)  
   {  
       Console.WriteLine("\nNew Polling Records Received");  
       Console.WriteLine("*************************************************");  
       DataSet[] dataArray = request.PolledData;  
       foreach (DataTable tab in dataArray[0].Tables)  
       {  
           foreach (DataRow row in tab.Rows)  
           {  
               for (int i = 0; i < tab.Columns.Count; i++)  
               {  
                   Console.WriteLine(row[i]);  
               }  
           }  
       }  
       Console.WriteLine("*************************************************");  
       Console.WriteLine("\nHit <RETURN> to stop polling");  
       }  
   }  
   ```  

3. 因為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]未接受認證的連線 URI 的一部分，您必須實作下列的類別，以 SQL Server 資料庫的認證。 在應用程式的後半部，您將會具現化這個類別，以在 SQL Server 認證。  

   ```  
   class PollingCredentials : ClientCredentials, IServiceBehavior  
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
           ClientCredentials clone = new PollingCredentials();  
           clone.UserName.UserName = this.UserName.UserName;  
           clone.UserName.Password = this.UserName.Password;  
           return clone;  
       }  
   }  
   ```  

4. 建立**SqlAdapterBinding**和設定輪詢作業藉由指定的繫結屬性。 在程式碼中明確或是宣告式組態中，您可以這麼做。 至少，您必須指定**InboundOperationType**， **PolledDataAvailableStatement**，並**PollingStatement**。  

   ```  
   SqlAdapterBinding binding = new SqlAdapterBinding();  
   binding.InboundOperationType = InboundOperation.Polling;  
   binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
   binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
   ```  

5. 指定 SQL Server 資料庫認證，藉由執行個體化**PollingCredentials**您在步驟 3 中建立的類別。  

   ```  
   PollingCredentials credentials = new PollingCredentials();  
   credentials.UserName.UserName = "<Enter user name here>";  
   credentials.UserName.Password = "<Enter password here>";  
   ```  

6. 建立在步驟 2 中建立的 WCF 服務的執行個體。  

   ```  
   // create service instance  
   PollingService service = new PollingService();  
   ```  

7. 建立的執行個體**System.ServiceModel.ServiceHost**使用 WCF 服務和基底的連線 URI。 如果指定，基底的連線 URI 不能包含的輸入的識別碼。 您也應該指定的認證。  

   ```  
   // Enable service host  
   Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
   ServiceHost serviceHost = new ServiceHost(service, baseUri);  
   serviceHost.Description.Behaviors.Add(credentials);  

   ```  

8. 將服務端點加入至服務主機。 若要這樣做：  

   -   使用在步驟 4 中建立的繫結。  

   -   指定連線 URI，其中包含認證並在必要時輸入的識別碼。  

   -   為 「 PollingOperation"指定的合約。  

   ```  
   // Add service endpoint: be sure to specify PollingOperation as the contract  
   Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
   serviceHost.AddServiceEndpoint("PollingOperation", binding, ConnectionUri);  
   ```  

9. 若要收到輪詢資料，請開啟服務主機。 每當查詢傳回結果集時，配接器會傳回資料。  

    ```  
    // Open the service host to begin polling  
    serviceHost.Open();  
    ```  

10. 若要終止輪詢，關閉服務主機。  

    > [!IMPORTANT]
    >  配接器將繼續輪詢直到關閉服務主機。  

    ```  
    serviceHost.Close();  
    ```  

### <a name="example"></a>範例  
 下列範例顯示在有輪詢查詢執行 [員工] 資料表。 輪詢陳述式會執行下列工作：  

1. 從 [員工] 資料表中選取所有記錄。  

2. 執行 MOVE_EMP_DATA 預存程序，以從 Employee 資料表的所有記錄都移至 EmployeeHistory 資料表。  

3. 執行 ADD_EMP_DETAILS 預存程序，將單一記錄新增至 [員工] 資料表。  

   第一次輪詢訊息會包含從 Employee 資料表的所有記錄。 後續輪詢訊息會包含只有 ADD_EMP_DETAILS 預存程序插入的最後一筆記錄。 配接器將繼續輪詢直到按關閉服務主機`<RETURN>`。  

```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  

using Microsoft.Adapters.Sql;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Collections.ObjectModel;  
using System.Data;  

namespace Polling_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  

    public class PollingService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
    {  

        public override void Polling(Polling request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            DataSet[] dataArray = request.PolledData;  
            foreach (DataTable tab in dataArray[0].Tables)  
            {  
                foreach (DataRow row in tab.Rows)  
                {  
                    for (int i = 0; i < tab.Columns.Count; i++)  
                    {  
                        Console.WriteLine(row[i]);  
                    }  
                }  
            }  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
        }  
    }  

    class PollingCredentials : ClientCredentials, IServiceBehavior  
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
            ClientCredentials clone = new PollingCredentials();  
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
                Console.WriteLine("Press any key to start polling...");  
                Console.ReadLine();  

                SqlAdapterBinding binding = new SqlAdapterBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
                binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
                Console.WriteLine("Binding properties assigned...");  

                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId (if any) that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  

                // This URI is used to initialize the ServiceHost. It cannot contain  
                // a query_string (InboundID); otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  

                PollingCredentials credentials = new PollingCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  

                Console.WriteLine("Opening service host...");  
                PollingService service = new PollingService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("PollingOperation", binding, ConnectionUri);  
                serviceHost.Open();  
                Console.WriteLine("Service host opened...");  
                Console.WriteLine("Polling started...");  
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
 [使用 WCF 服務模型中的 SQL 配接器的輪詢 SQL Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-wcf-service-model.md)