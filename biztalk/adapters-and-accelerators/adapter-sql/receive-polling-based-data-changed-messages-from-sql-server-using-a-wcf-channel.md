---
title: "從 SQL Server 接收輪詢基礎資料變更的訊息，使用 WCF 通道模型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0f4af71-fb0c-433d-ba74-48ee6487eb1a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb785631d6fe00ea68f57f943dca11ebd1a84b1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-based-data-changed-messages-from-sql-server-by-using-the-wcf-channel-model"></a>從 SQL Server 接收輪詢基礎資料變更的訊息，使用 WCF 通道模型
您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收 SQL Server 資料表或檢視表的週期性的資料變更訊息。 您可以指定執行以輪詢資料庫配接器的輪詢陳述式。 輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。  
  
 如需有關如何配接器支援在輪詢的詳細資訊，請參閱[支援輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。  
  
> [!IMPORTANT]
>  如果您想要在單一應用程式中有一個以上的輪詢作業，您必須指定**InboundID**一部分連線 URI 成為唯一的連接屬性。 您指定的輸入的識別碼會加入至作業的命名空間，使它成為唯一。  
  
## <a name="how-this-topic-demonstrates-polling"></a>本主題示範輪詢的方式  
 本主題中，以示範如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援接收資料變更的訊息，請建立.NET 應用程式的**輪詢**作業。 本主題中，指定**PolledDataAvailableStatement**為：  
  
```  
SELECT COUNT(*) FROM Employee  
```  
  
 **PolledDataAvailableStatement**必須傳回一個結果集包含正值的第一個儲存格。 如果第一個資料格不包含正值，配接器不會執行輪詢陳述式。  
  
 輪詢陳述式的一部分，執行下列作業：  
  
1.  選取從 Employee 資料表的所有資料列。  
  
2.  執行預存程序 (MOVE_EMP_DATA) 會將所有的記錄從 Employee 資料表 EmployeeHistory 資料表。  
  
3.  執行預存程序 (ADD_EMP_DETAILS) Employee 資料表中加入新的記錄。 此程序會接受員工名稱、 指定和薪資做為參數。  
  
 若要執行這些作業，您必須指定下列**PollingStatement**繫結屬性：  
  
```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  
  
 執行輪詢陳述式之後，選取從 Employee 資料表的所有記錄，並收到來自 SQL Server 的訊息。 一旦執行 MOVE_EMP_DATA 預存程序之後，配接器，所有的記錄會移至 EmployeeHistory 資料表。 然後，ADD_EMP_DETAILS 預存程序會執行以將新記錄新增至 Employee 資料表。 下次輪詢執行只會傳回單一記錄。 這個循環會持續直到您關閉通道接聽程式。  
  
## <a name="configuring-a-polling-query-with-the-sql-adapter-binding-properties"></a>使用 SQL 配接器繫結屬性中設定輪詢查詢  
 下表摘要說明[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結，您用來設定配接器來接收資料變更訊息的屬性。 輪詢的.NET 應用程式的一部分，您必須指定這些繫結屬性。  
  
|繫結屬性|Description|  
|----------------------|-----------------|  
|**InboundOperationType**|指定您是否要執行**輪詢**， **TypedPolling**，或**通知**輸入作業。 預設值是**輪詢**。|  
|**PolledDataAvailableStatement**|指定的 SQL 陳述式來判斷是否可用於輪詢的任何資料執行配接器。 SQL 陳述式必須傳回的結果集資料列和資料行所組成。 只有一個資料列是否可用，SQL 陳述式指定**PollingStatement**繫結屬性將會執行。|  
|**PollingIntervalInSeconds**|指定間隔，以秒為單位，此時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。 預設值是 30 秒。 輪詢間隔會決定後續輪詢間隔時間。 如果指定的間隔內執行的陳述式，則配接器就會等候剩餘的時間間隔中。|  
|**PollingStatement**|指定輪詢 SQL Server 資料庫資料表的 SQL 陳述式。 您可以指定簡單的 SELECT 陳述式或預存程序輪詢陳述式。 預設值是 null。 您必須指定的值**PollingStatement**來啟用輪詢。 輪詢陳述式在沒有進行輪詢，取決於可用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。 您可以指定任意數目的 SQL 陳述式以分號分隔。|  
|**PollWhileDataFound**|指定是否[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]忽略的輪詢間隔，並為指定的 SQL 陳述式會持續執行**PolledDataAvailableStatement**如果輪詢資料表中的資料可繫結屬性。 如果沒有資料可在資料表中，配接器會還原為執行 SQL 陳述式，在指定的輪詢間隔。 預設值是**false**。|  
  
 如需這些屬性的更完整說明，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 如需完整的說明，如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]到輪詢 SQL Server，請閱讀本主題的其餘部分。  
  
## <a name="consuming-the-polling-request-message"></a>使用輪詢要求訊息  
 配接器會叫用**輪詢**對程式碼，以輪詢 SQL Server 資料庫的作業。 也就是說，配接器傳送輪詢要求訊息，您會收到透過 IInputChannel 通道形狀。 輪詢要求訊息包含 PollingStatement 繫結屬性所指定的查詢的結果集。 您可以使用輪詢訊息中有兩種：  
  
-   若要使用訊息使用的節點值的資料流您必須呼叫**WriteBodyContents**方法回應訊息，並將它傳遞**XmlDictionaryWriter**實作節點值的資料流。  
  
-   若要使用訊息使用節點資料流處理，您可以呼叫**GetReaderAtBodyContents**要取得的回應訊息上**XmlReader**。  
  
## <a name="about-the-examples-used-in-this-topic"></a>關於本主題中使用的範例  
 本主題中的範例輪詢 Employee 資料表。 此範例也會使用 MOVE_EMP_DATA 和 ADD_EMP_DETAILS 預存程序。 指令碼來產生這些成品隨附的範例。 如需這些範例的詳細資訊，請參閱[SQL 配接器範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。 範例中， **Polling_ChannelModel**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。  
  
## <a name="receiving-inbound-messages-for-polling-operation-using-the-wcf-channel-model"></a>使用 WCF 通道模型的輪詢作業接收內送的訊息  
 本節說明如何撰寫.NET 應用程式 （通道模型） 來接收傳入的輪詢訊息使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
#### <a name="to-receive-polling-messages-from-the-sql-adapter"></a>若要接收 SQL 配接器的輪詢訊息  
  
1.  Microsoft Visual C# 中建立專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 本主題中，建立主控台應用程式。  
  
2.  在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`， `Microsoft.ServiceModel.Channels`， `System.ServiceModel`，和`System.Runtime.Serialization`。  
  
3.  開啟 Program.cs 檔案並加入下列命名空間：  
  
    -   `Microsoft.Adapters.Sql`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Description`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
4.  指定連線 URI。 如需配接器的連線 URI 的詳細資訊，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。  
  
    ```  
    Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
    ```  
  
5.  建立的執行個體**SqlAdapterBinding**並設定繫結屬性才能設定輪詢。 您必須設定至少**InboundOperationType**， **PolledDataAvailableStatement**，和**PollingStatement**繫結屬性。 如需繫結屬性用來設定輪詢的詳細資訊，請參閱[支援輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。  
  
    ```  
    SqlAdapterBinding binding = new SqlAdapterBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
    binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
    ```  
  
6.  建立繫結參數集合，並設定認證。  
  
    ```  
    ClientCredentials credentials = new ClientCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
  
    BindingParameterCollection bindingParams = new BindingParameterCollection();  
    bindingParams.Add(credentials);  
    ```  
  
7.  建立通道接聽程式，並將它開啟。 您建立的接聽程式叫用**BuildChannelListener < IInputChannel\>** 方法**SqlAdapterBinding**。  
  
    ```  
    IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
    listener.Open();  
    ```  
  
8.  取得**IInputChannel**叫用的通道**AcceptChannel**接聽程式上的方法，並開啟它。  
  
    ```  
    IInputChannel channel = listener.AcceptChannel();  
    channel.Open();  
    ```  
  
9. 叫用**接收**從配接器取得下一個 POLLINGSTMT 訊息之通道上。  
  
    ```  
    Message message = channel.Receive();  
    ```  
  
10. 耗用 POLLINGSTMT 作業所傳回的結果集。 您可以使用訊息使用**XmlReader**或**XmlDictionaryWriter**。  
  
    ```  
    XmlReader reader = message.GetReaderAtBodyContents();  
    ```  
  
11. 當您完成處理要求，請關閉通道。  
  
    ```  
    channel.Close()  
    ```  
  
    > [!IMPORTANT]
    >  處理 POLLINGSTMT 作業完成之後，您必須關閉通道。 無法關閉通道可能會影響您的程式碼的行為。  
  
12. 當您完成接收的資料變更的訊息時，請關閉接聽程式。  
  
    ```  
    listener.Close()  
    ```  
  
    > [!IMPORTANT]
    >  關閉接聽程式不會關閉建立使用接聽程式通道。 您必須明確地關閉使用接聽程式所建立的每個通道。  
  
### <a name="example"></a>範例  
 下列範例會顯示執行 Employee 資料表的輪詢查詢。 輪詢陳述式會執行下列工作：  
  
-   選取從 Employee 資料表的所有記錄。  
  
-   執行將從 Employee 資料表的所有記錄移動到 EmployeeHistory 資料表 MOVE_EMP_DATA 預存程序。  
  
-   執行 ADD_EMP_DETAILS 預存程序加入 Employee 資料表的單一記錄。  
  
 輪詢訊息會儲存在`C:\PollingOutput.xml`。  
  
```  
using System;  
using Microsoft.Adapters.Sql;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
  
using System.Xml;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Console.WriteLine("Sample started. This sample will poll 5 times and will perform the following tasks:");  
            Console.WriteLine("Press any key to start polling...");  
            Console.ReadLine();  
            IChannelListener<IInputChannel> listener = null;  
  
            IInputChannel channel = null;  
  
            try  
            {  
                TimeSpan messageTimeout = new TimeSpan(0, 0, 30);  
  
                SqlAdapterBinding binding = new SqlAdapterBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
                binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
  
                Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
  
                ClientCredentials credentials = new ClientCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                BindingParameterCollection bindingParams = new BindingParameterCollection();  
                bindingParams.Add(credentials);  
  
                listener = binding.BuildChannelListener<IInputChannel>(ConnectionUri, bindingParams);  
                listener.Open();  
  
                channel = listener.AcceptChannel();  
                channel.Open();  
  
                Console.WriteLine("Channel and Listener opened...");  
                Console.WriteLine("\nWaiting for polled data...");  
                Console.WriteLine("Receive request timeout is {0}", messageTimeout);  
  
                // Poll five times with the specified message timeout   
                // If a timeout occurs polling will be aborted  
                for (int i = 0; i < 5; i++)  
                {  
                    Console.WriteLine("Polling: " + i);  
                    Message message = null;  
                    XmlReader reader = null;  
                    try  
                    {  
                        //Message is received so process the results  
                        message = channel.Receive(messageTimeout);  
                    }  
                    catch (System.TimeoutException toEx)  
                    {  
                        Console.WriteLine("\nNo data for request number {0}: {1}", i + 1, toEx.Message);  
                        continue;  
                    }  
  
                    // Get the query results using an XML reader  
                    try  
                    {  
                        reader = message.GetReaderAtBodyContents();  
                    }  
                    catch (Exception ex)  
                    {  
                        Console.WriteLine("Exception :" + ex);  
                        throw;  
                    }  
  
                    XmlDocument doc = new XmlDocument();  
                    doc.Load(reader);  
                    using (XmlWriter writer = XmlWriter.Create("C:\\PollingOutput.xml"))  
                    {  
                        doc.WriteTo(writer);  
                        Console.WriteLine("The polling response is saved at 'C:\\PollingOutput.xml'");  
                    }  
  
                    // return the cursor  
                    Console.WriteLine();  
  
                    // close the reader  
                    reader.Close();  
  
                    message.Close();  
                }  
                Console.WriteLine("\nPolling done -- hit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
            }  
            finally  
            {  
                // IMPORTANT: close the channel and listener to stop polling  
                if (channel != null)  
                {  
                    if (channel.State == CommunicationState.Opened)  
                        channel.Close();  
                    else  
                        channel.Abort();  
                }  
  
                if (listener != null)  
                {  
                    if (listener.State == CommunicationState.Opened)  
                        listener.Close();  
                    else  
                        listener.Abort();  
                }  
            }  
        }  
    }  
}  
  
```  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)