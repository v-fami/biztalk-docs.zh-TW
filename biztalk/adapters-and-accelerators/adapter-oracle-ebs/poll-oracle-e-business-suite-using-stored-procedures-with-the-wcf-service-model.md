---
title: "使用 WCF 服務模型中的預存程序的輪詢 Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47dcb866-9161-4b28-9481-2761794ce805
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e27c6bc1c0d8578bc99e5e8665556cb69cc2f819
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-e-business-suite-using-stored-procedures-with-the-wcf-service-model"></a>輪詢 Oracle E-business Suite 使用 WCF 服務模型中的預存程序
您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]來使用預存程序，以定期輪詢 Oracle 資料庫接收定期的資料變更訊息。 您可以指定預存程序，為配接器執行定期輪詢 Oracle 資料庫的輪詢陳述式。  
  
 若要啟用輪詢，您必須指定特定繫結屬性，本主題中所述。  如需如何配接器支援在輪詢的詳細資訊，請參閱[支援輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。  
  
## <a name="configuring-a-polling-operation-with-oracle-e-business-adapter-binding-properties"></a>使用 Oracle E-business 配接器繫結屬性中設定輪詢作業  
 下表摘要說明[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結，您用來設定配接器來接收資料變更訊息的屬性。 執行輪詢應用程式時，您必須指定這些繫結屬性。  
  
|繫結屬性|Description|  
|----------------------|-----------------|  
|**InboundOperationType**|指定您是否要執行**輪詢**或**通知**輸入作業。 預設值是**輪詢**。|  
|**PolledDataAvailableStatement**|指定的 SQL 陳述式來判斷是否可用於輪詢的任何資料執行配接器。 只有當可用的記錄時，預存程序指定為**PollingInput**繫結屬性將會執行。|  
|**PollingInterval**|指定間隔，以秒為單位，此時[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。 預設值是 30 秒。 輪詢間隔會決定後續輪詢間隔時間。 如果指定的間隔內執行的陳述式，則配接器進入睡眠狀態的剩餘時間間隔中。|  
|**PollingInput**|指定輪詢陳述式。 若要輪詢使用預存程序，您必須指定這個繫結屬性的整個要求訊息。 要求訊息必須相同，您傳送給配接器叫用預存程序，做為輸出的作業。 預設值是 null。<br /><br /> 您必須指定的值**PollingInput**繫結內容來啟用輪詢。 輪詢陳述式在沒有進行輪詢，取決於可用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。|  
|**PollingAction**|指定輪詢作業的動作。 您可以決定產生的作業使用的服務介面的輪詢動作[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。|  
|**PostPollStatement**|指定執行所指定的陳述式之後的陳述式區塊**PollingInput**執行繫結屬性。|  
|**PollWhileDataFound**|指定是否[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]忽略的輪詢間隔，並持續執行輪詢陳述式，如果輪詢資料表中的可用資料。 如果沒有資料可在資料表中，配接器會還原為執行指定的輪詢間隔輪詢陳述式。 預設值為 false。|  
  
 如需這些屬性的更完整說明，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 如需完整的說明，如何使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]輪詢，請閱讀下列各節。  
  
## <a name="how-this-topic-demonstrates-polling"></a>本主題示範輪詢的方式  
 本主題中，以示範如何[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援接收訊息使用預存程序，使用 GET_ACTIVITYS 資料變更預存程序來輪詢 ACCOUNTACTIVITY 資料表 Oracle 資料庫中的。 這個預存程序可與 ACCOUNT_PKG 封裝。 您可以執行這些範例資料庫中建立這些物件提供的 SQL 指令碼。  
  
> [!NOTE]
>  此主題輪詢中 ACCOUNTACTIVITY 資料表，其中基底資料庫資料表建立執行範例所提供的指令碼的範例。 若要輪詢的任何其他資料表，包括介面資料表本主題中所述，您必須執行類似的程序。  
  
 若要示範輪詢作業，我們執行下列作業：  
  
-   指定 SELECT 陳述式**PolledDataAvailableStatement**繫結屬性，以判斷其中資料表輪詢 (ACCOUNTACTIVITY) 有任何資料。 在此範例中，您可以設定為這個繫結屬性：  
  
    ```  
    SELECT COUNT (*) FROM ACCOUNTACTIVITY  
    ```  
  
     這可確保當配接器 ACCOUNTACTIVITY 資料表具有一些記錄時才會執行輪詢陳述式。  
  
-   藉由提供要求訊息的一部分執行的預存程序 GET_ACTIVITYS， **PollingInput**繫結屬性。 這個預存程序會擷取 ACCOUNTACTIVITY 資料表中的所有資料列，您會從配接器收到回應訊息。  
  
-   執行一部分的 PL/SQL 區塊**PostPollStatement**繫結屬性。 這個陳述式會移動所有資料從 ACCOUNTACTIVITY 資料表在資料庫中的另一個資料表。 發生這種情況，在下一次之後**PollingInput**會執行，它將會不提取任何資料，因此 GET_ACTIVITYS 預存程序會傳回空白的回應訊息。  
  
-   更多資料加入至 ACCOUNTACTIVITY 資料表，直到您將會持續取得空的回應訊息，因此您必須重新擴展 ACCOUNTACTIVITY 資料表與新的記錄。 您可以藉由執行範例所提供的 more_activity_data.sql 指令碼。 執行這個指令碼之後下, 一個輪詢作業將會提取新的記錄插入至資料表。  
  
## <a name="configuring-polling-in-the-wcf-service-model"></a>在 WCF 服務模型中設定輪詢  
 若要輪詢使用預存程序[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與 WCF 服務模型中，您必須：  
  
-   使用您要輪詢的預存程序產生的 WCF 服務合約 （介面）。 此範例中，您必須產生的 WCF 服務合約**GET_ACTIVITYS**預存程序做為輸入的作業。 若要這樣做，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
-   實作這個介面從 WCF 服務。  
  
-   裝載此 WCF 服務，使用服務主機 (**system.servicemodel.servicehost 內**)。  
  
## <a name="about-the-examples-used-in-this-topic"></a>關於本主題中使用的範例  
 此主題輪詢使用 GET_ACTIVITYS ACCOUNTACTIVITY 資料庫資料表中的範例預存程序。 若要產生的資料表和預存程序的指令碼會提供範例。 如需這些範例的詳細資訊，請參閱[Oracle EBS 配接器範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。 範例中， **StoredProcPolling_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。  
  
## <a name="the-wcf-service-contract-and-class"></a>WCF 服務合約和類別  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]建立 WCF 服務合約 （介面） 和支援類別**GET_ACTIVITYS**輸入作業。 如需產生 WCF 服務合約的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  
  
### <a name="the-wcf-service-contract-interface"></a>WCF 服務合約 （介面）  
 下列程式碼顯示產生的 WCF 服務合約 （介面） **GET_ACTIVITYS**輸入作業。  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/", ConfigurationName="PollingPackageApis_APPS_ACCOUNT_PKG")]  
public interface PollingPackageApis_APPS_ACCOUNT_PKG {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/PollingPackageApis/APPS/ACCOUNT_PKG) of message GET_ACTIVITYS   
    // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="PollingPackageApis/APPS/ACCOUNT_PKG/GET_ACTIVITYS")]  
    void GET_ACTIVITYS(GET_ACTIVITYS request);  
}  
```  
  
### <a name="the-message-contracts"></a>訊息合約  
 以下是訊息合約**GET_ACTIVITYS**輸入作業。  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="GET_ACTIVITYS", WrapperNamespace="http://schemas.microsoft.com/OracleEBS/2008/05/PollingPackageApis/APPS/ACCOUNT_PK" +  
    "G", IsWrapped=true)]  
public partial class GET_ACTIVITYS {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/PollingPackageApis/APPS/ACCOUNT_PK" +  
        "G", Order=0)]  
    public schemas.microsoft.com.OracleEBS._2008._05.RecordTypes.APPS.ACCOUNT_PKG.GET_ACTIVITYS.OUTRECSRecord[] OUTRECS;  
  
    public GET_ACTIVITYS() {  
    }  
  
    public GET_ACTIVITYS(schemas.microsoft.com.OracleEBS._2008._05.RecordTypes.APPS.ACCOUNT_PKG.GET_ACTIVITYS.OUTRECSRecord[] OUTRECS) {  
        this.OUTRECS = OUTRECS;  
    }  
}  
```  
  
### <a name="wcf-service-class"></a>WCF 服務類別  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生虛設常式實作的服務合約 （介面） 的 WCF 服務類別的檔案。 檔案的名稱是 OracleEBSBindingService.cs。 您可以插入要處理邏輯**GET_ACTIVITYS**直接將這個類別的作業。 下列程式碼將示範所產生的 WCF 服務類別[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
```  
namespace OracleEBSBindingNamespace {  
  
    public class OracleEBSBindingService : PollingPackageApis_APPS_ACCOUNT_PKG {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/PollingPackageApis/APPS/ACCOUNT_PKG) of message GET_ACTIVITYS   
        // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
        public virtual void GET_ACTIVITYS(GET_ACTIVITYS request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-inbound-messages-for-polling-using-a-stored-procedure"></a>輪詢使用預存程序接收內送的訊息  
 本節說明如何撰寫.NET 應用程式來接收傳入的輪詢訊息使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
#### <a name="to-receive-polling-messages-using-a-stored-procedure"></a>若要接收的輪詢訊息使用預存程序  
  
1.  使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 服務合約 （介面） 和協助程式類別，如**GET_ACTIVITYS**輸入作業。 如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。 您可以選擇性地產生服務合約和協助程式類別時指定的繫結屬性。 這可確保它們已正確設定在產生的組態檔中。  
  
2.  實作 WCF 服務，從步驟 1 中所產生的介面和協助程式類別。 **GET_ACTIVITYS**這個類別的方法可以擲回例外狀況中止輪詢交易，處理從接收的資料發生錯誤**GET_ACTIVITYS**作業; 否則為此方法不會傳回任何項目。 您必須屬性 WCF 服務類別，如下所示：  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
     內**GET_ACTIVITYS**方法，您可以直接實作應用程式邏輯。 這個類別可以 OracleEBSBindingService.cs 中找到。 這段程式碼，在此範例中的子類別**OracleEBSBindingService**類別。 在此程式碼中，接收輪詢訊息，並寫入至主控台。  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : OracleEBSBindingNamespace.OracleEBSBindingService  
    {  
        public override void  GET_ACTIVITYS(GET_ACTIVITYS request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Tx Id\tAccount\tAmount\tProcessed");  
            for (int i = 0; i < request.OUTRECS.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.OUTRECS[i].TID,  
                request.OUTRECS[i].ACCOUNT,  
                request.OUTRECS[i].AMOUNT,  
                request.OUTRECS[i].PROCESSED);  
            }  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
        }  
    }  
    ```  
  
3.  您必須實作下列類別，以避免將認證傳遞做為 URI 的一部分。 在應用程式的第二個部分中，您會具現化這個類別，以傳遞的認證。  
  
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
  
4.  建立**OracleEBSBinding**和設定輪詢作業藉由指定的繫結屬性。 您可以在程式碼中明確或是宣告式組態。 最少，您必須指定**InboundOperationType**， **PolledDataAvailableStatement**， **PollingInput**，和**PollingAction**繫結屬性。  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM ACCOUNTACTIVITY";  
    binding.PollingInput = "\<GET_ACTIVITYS xmlns='http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/APPS/ACCOUNT_PKG'><INRECS>OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY</INRECS></GET_ACTIVITYS>";  
    binding.PollingAction = "PollingPackageApis/APPS/ACCOUNT_PKG/GET_ACTIVITYS";  
    binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
    ```  
  
    > [!NOTE]
    >  請注意，值**PollingInput**繫結屬性會包含要求訊息來叫用**GET_ACTIVITYS**預存程序做為輸出的作業。  
  
    > [!IMPORTANT]
    >  在此範例中，因為您正在輪詢資料庫資料表時，您不需要設定的應用程式內容。 不過，如果您已輪詢介面資料表，您必須設定應用程式內容藉由指定**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。 如需應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
5.  藉由執行個體化指定 Oracle E-business Suite 認證**PollingCredentials**您在步驟 3 中建立的類別。  
  
    ```  
    PollingCredentials credentials = new PollingCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
    ```  
  
6.  建立在步驟 2 中建立的 WCF 服務的執行個體。  
  
    ```  
    // create service instance  
    PollingService service = new PollingService();  
    ```  
  
7.  建立的執行個體**system.servicemodel.servicehost 內**使用 WCF 服務和基底的連線 URI。 如果指定基底的連線 URI 不能包含輸入的識別碼。 您也必須將認證傳遞這裡。  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("oracleebs://ebs_instance_name") };  
    ServiceHost serviceHost = new ServiceHost(service, baseUri);  
    serviceHost.Description.Behaviors.Add(credentials);  
  
    ```  
  
8.  將服務端點加入至服務主機。 若要這樣做：  
  
    -   使用步驟 4 中建立的繫結。  
  
    -   指定連線 URI，其中包含認證並在必要時輸入的識別碼。  
  
    -   為 「 PollingPackageApis_APPS_ACCOUNT_PKG"輪詢 MS_SAMPLE_EMPLOYEE 介面資料表中指定的合約。  
  
    ```  
    // Add service endpoint: be sure to specify PollingPackageApis_APPS_ACCOUNT_PKG as the contract  
    Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
    serviceHost.AddServiceEndpoint("PollingPackageApis_APPS_ACCOUNT_PKG", binding, ConnectionUri);  
    ```  
  
9. 若要收到輪詢資料，請開啟服務主機。 每當查詢會傳回結果集時，配接器會傳回資料。  
  
    ```  
    // Open the service host to begin polling  
    serviceHost.Open();  
    ```  
  
10. 若要終止輪詢，關閉服務主機。  
  
    > [!IMPORTANT]
    >  配接器將會繼續輪詢直到關閉服務主機。  
  
    ```  
    serviceHost.Close();  
    ```  
  
### <a name="example"></a>範例  
 下列範例會示範一個輪詢的應用程式，輪詢使用 GET_ACTIVITYS ACCOUNTACTIVITY 資料庫資料表的預存程序。 **PollingInput**繫結屬性包含要叫用從 ACCOUNTACTIVITY 資料表讀取所有資料 GET_ACTIVITYS 預存程序的要求訊息和後輪詢陳述式從 ACCOUNTACTIVITY 移動所有資料ACTIVITYHISTORY 資料表。  
  
 第一個輪詢訊息會說明 ACCOUNTACTIVITY 資料表中的所有記錄。 後續的輪詢訊息不會包含任何記錄，因為後輪詢陳述式會刪除的記錄。 更多資料加入到 ACCOUNTACTIVITY 資料表之前, 則不會收到任何輪詢訊息，您必須重新擴展 ACCOUNTACTIVITY 資料表與新的記錄。 您可以藉由執行範例所提供的 more_activity_data.sql 指令碼。  
  
 執行這個指令碼之後下, 一個輪詢作業將會提取新的記錄插入至資料表。 配接器將繼續輪詢直到按關閉服務主機`<RETURN>`。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.Adapters.OracleEBS;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Collections.ObjectModel;  
  
namespace StoredProcPolling_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : OracleEBSBindingNamespace.OracleEBSBindingService  
    {  
        public override void  GET_ACTIVITYS(GET_ACTIVITYS request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Tx Id\tAccount\tAmount\tProcessed");  
            for (int i = 0; i < request.OUTRECS.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.OUTRECS[i].TID,  
                request.OUTRECS[i].ACCOUNT,  
                request.OUTRECS[i].AMOUNT,  
                request.OUTRECS[i].PROCESSED);  
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
  
                OracleEBSBinding binding = new OracleEBSBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM ACCOUNTACTIVITY";  
                binding.PollingInput = "\<GET_ACTIVITYS xmlns='http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/APPS/ACCOUNT_PKG'><INRECS>OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY</INRECS></GET_ACTIVITYS>";  
                binding.PollingAction = "PollingPackageApis/APPS/ACCOUNT_PKG/GET_ACTIVITYS";  
                binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
  
                // This URI is used to initialize the ServiceHost. It cannot contain  
                // an InboundID; otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("oracleebs://ebs_instance_name") };  
  
                PollingCredentials credentials = new PollingCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                Console.WriteLine("Opening service host...");  
                PollingService service = new PollingService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("PollingPackageApis_APPS_ACCOUNT_PKG", binding, ConnectionUri);  
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
 [使用 WCF 服務模型輪詢 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-the-wcf-service-model.md)