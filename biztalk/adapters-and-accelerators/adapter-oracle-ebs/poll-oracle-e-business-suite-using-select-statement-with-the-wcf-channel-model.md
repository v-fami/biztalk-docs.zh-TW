---
title: 使用 WCF 通道模型中的 SELECT 陳述式的輪詢 Oracle E-business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495b9010-856f-4782-bd19-1522bc3eb950
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 650a60b3a8a9484461edab432370e58cdd8eee70
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013775"
---
# <a name="poll-oracle-e-business-suite-using-select-statement-with-the-wcf-channel-model"></a>使用 WCF 通道模型中的 SELECT 陳述式的輪詢 Oracle E-business Suite
您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收定期的資料變更訊息，若要連續輪詢介面資料表使用 SELECT 陳述式，介面檢視、 資料表以及 Oracle E-business Suite 中的檢視。 您可以指定 SELECT 陳述式來輪詢 Oracle E-business Suite 會定期執行配接器輪詢陳述式。 您也可以指定後續輪詢 PL/SQL 程式碼區塊，配接器執行後輪詢陳述式。  

 若要啟用輪詢，您必須指定特定繫結屬性，本主題中所述。 如需配接器如何支援輪詢的詳細資訊，請參閱[支援的輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。  

## <a name="configuring-a-polling-operation-with-oracle-e-business-suite-adapter-binding-properties"></a>使用 Oracle E-business Suite 配接器繫結屬性中設定輪詢作業  
 下表摘要說明[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結屬性，您用來設定配接器接收資料變更訊息。 執行輪詢應用程式時，您必須指定這些繫結屬性。  


|         繫結屬性         |                                                                                                                                                                                                                            描述                                                                                                                                                                                                                             |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     **InboundOperationType**     |                                                                                                                                                                          指定是否要執行**輪詢**或是**通知**輸入作業。 預設值是**輪詢**。                                                                                                                                                                          |
| **PolledDataAvailableStatement** |                                                                                                             指定配接器執行，以判斷是否有任何資料可供輪詢 SQL 陳述式。 只有當可用的記錄時，SELECT 陳述式您指定的**PollingInput**屬性繫結將會執行。                                                                                                              |
|       **PollingInterval**        | 指定間隔 （秒），此時[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。 預設值是 30 秒。 輪詢間隔會決定後續輪詢間隔的時間間隔。 如果指定的間隔內執行的陳述式，則配接器會睡剩餘的時間間隔中。 |
|         **PollingInput**         |                         指定輪詢陳述式。 若要使用的 SELECT 陳述式進行輪詢，您必須指定這個繫結屬性的 SELECT 陳述式。 預設值是 null。<br /><br /> 您必須指定的值**PollingInput**繫結屬性，來啟用輪詢。 輪詢陳述式在沒有可供輪詢，取決於使用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。                          |
|        **PollingAction**         |                                                                                                                指定輪詢作業的動作。 您可以決定從產生的作業使用的服務介面的輪詢動作[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。                                                                                                                |
|      **PostPollStatement**       |                                                                                                                                                                  指定執行所指定的陳述式之後的陳述式區塊**PollingInput**屬性繫結會執行。                                                                                                                                                                  |
|      **PollWhileDataFound**      |                                    指定是否[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會忽略的輪詢間隔，並持續執行輪詢陳述式，如果資料可在所輪詢的資料表。 如果沒有資料可在資料表中，配接器會還原為執行指定的輪詢間隔輪詢陳述式。 預設值為 false。                                     |

 如需這些屬性的更完整說明，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 如需完整的說明，如何使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]若要輪詢 Oracle 資料庫，請參閱本主題的其餘部分。  

## <a name="how-this-topic-demonstrates-polling"></a>本主題將輪詢的示範  
 本主題中，以示範如何[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收資料的支援變更使用 SELECT 陳述式的訊息，請您輪詢**MS_SAMPLE_EMPLOYEE**中的介面資料表**應用程式物件程式庫**應用程式。 當您執行提供的範例，在 Oracle E-business Suite 中建立這些物件的 create_apps_artifacts.sql 指令碼時，會建立此資料表。  

 為了示範輪詢作業，我們執行下列作業：  

-   指定的 SELECT 陳述式**PolledDataAvailableStatement**繫結屬性，以判斷其中介面資料表輪詢 (MS_SAMPLE_EMPLOYEE) 有任何資料。 在此範例中，您可以設定為這個繫結屬性：  

    ```  
    SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE  
    ```  

     這可確保當配接器 MS_SAMPLE_EMPLOYEE 介面資料表有一些記錄時，才會執行輪詢陳述式。  

-   指定的 SELECT 陳述式**PollingInput**繫結屬性。 此陳述式擷取 MS_SAMPLE_EMPLOYEE 介面資料表中的所有資料列。 在此範例中，您可以設定為這個繫結屬性：  

    ```  
    SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE  
    ```  

    > [!NOTE]
    >  FOR UPDATE 子句用於 SELECT 陳述式的相關資訊，請參閱[從 Oracle E-business Suite 接收以輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-ebs/receive-polling-based-data-changed-messages-from-oracle-e-business-suite.md)。  

-   指定 DELETE 陳述式的一部分**PostPollStatement**繫結屬性。 此陳述式會從 MS_SAMPLE_EMPLOYEE 介面資料表刪除所有資料。 在此範例中，您可以設定為這個繫結屬性：  

    ```  
    DELETE FROM MS_SAMPLE_EMPLOYEE  
    ```  

     發生這種情況後下, 一次針對指定的陳述式**PollingInput**會執行，它不會擷取任何資料。  

-   更多資料新增至 MS_SAMPLE_EMPLOYEE 介面資料表之前則不會收到任何輪詢訊息讓您必須重新擴展 MS_SAMPLE_EMPLOYEE 介面資料表與新的記錄。 您可以執行 insert_apps_data.sql 指令碼提供範例來這麼做。 執行此指令碼之後下, 一個輪詢作業會擷取新記錄插入至資料表。  

## <a name="consuming-the-polling-request-message"></a>使用輪詢要求訊息  
 配接器會叫用您的程式碼，以輪詢 Oracle E-business Suite 的輪詢作業。 也就是配接器會傳送您所收到的輪詢要求訊息透過 IInputChannel 通道組織結構。 輪詢要求訊息包含所指定之查詢的結果集**PollingInput**繫結屬性。 您可以使用輪詢訊息中有兩種：  

-   若要取用使用節點值的資料流的訊息，您必須呼叫**WriteBodyContents**方法的回應訊息，並將它傳遞**XmlDictionaryWriter**實作資料流處理的節點值。  

-   若要取用使用節點資料流的訊息，您可以呼叫**GetReaderAtBodyContents**回應訊息，可取得**XmlReader**。  

## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例輪詢 MS_SAMPLE_EMPLOYEE 介面資料表。 若要產生資料表的指令碼會提供範例。 如需有關範例的詳細資訊，請參閱 < [Oracle EBS 配接器的範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。 範例中， **SelectPolling_ChannelModel**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。  

## <a name="receiving-inbound-messages-for-polling-operation-using-the-wcf-channel-model"></a>使用 WCF 通道模型的輪詢作業接收內送的訊息  
 本節說明如何撰寫.NET 應用程式 （通道模型），以接收輸入的輪詢訊息使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  

#### <a name="to-receive-polling-messages-from-the-adapter"></a>若要接收來自配接器的輪詢訊息  

1. Microsoft Visual C#® 中建立的專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 本主題中，建立主控台應用程式。  

2. 在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`， `Microsoft.ServiceModel.Channels`， `System.ServiceModel`，和`System.Runtime.Serialization`。  

3. 開啟 Program.cs 檔案並新增下列命名空間：  

   -   `Microsoft.Adapters.OracleEBS`  

   -   `System.ServiceModel`  

   -   `System.ServiceModel.Description`  

   -   `System.ServiceModel.Channels`  

   -   `System.Xml`  

4. 指定連線 URI。 如需配接器連線 URI 的詳細資訊，請參閱[建立 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)。  

   ```  
   Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
   ```  

5. 建立的執行個體**OracleEBSBinding**和設定必要設定輪詢的繫結屬性。 您必須設定至少**InboundOperationType**， **PolledDataAvailableStatement**， **PollingInput**，以及**PollingAction**繫結屬性。 如需有關用來設定輪詢的屬性繫結的詳細資訊，請參閱[支援的輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。  

   ```  
   OracleEBSBinding binding = new OracleEBSBinding();  
   binding.InboundOperationType = InboundOperation.Polling;  
   binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
   binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
   binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
   binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
   ```  

6. 因為您正在輪詢介面資料表，您也必須設定應用程式內容。 如需有關應用程式內容和設定應用程式內容所需的繫結屬性的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  

   ```  
   binding.OracleUserName = "<Enter user name here>";  
   binding.OraclePassword = "<Enter password here>";  
   binding.OracleEBSResponsibilityName = "<Enter responsibility here>";  
   ```  

7. 建立繫結參數集合，並設定認證。  

   ```  
   ClientCredentials credentials = new ClientCredentials();  
   credentials.UserName.UserName = "<Enter user name here>";  
   credentials.UserName.Password = "<Enter password here>";  

   BindingParameterCollection bindingParams = new BindingParameterCollection();  
   bindingParams.Add(credentials);  
   ```  

8. 建立通道接聽程式，然後開啟它。 您可以建立接聽程式所叫用**BuildChannelListener < IInputChannel\>** 方法**OracleEBSBinding**。  

   ```  
   IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
   listener.Open();  
   ```  

9. 取得**IInputChannel**藉由叫用的通道**AcceptChannel**接聽程式上的方法並將它開啟。  

    ```  
    IInputChannel channel = listener.AcceptChannel();  
    channel.Open();  
    ```  

10. 叫用**接收**從配接器取得下一個傳入的訊息的通道上。  

    ```  
    Message message = channel.Receive();  
    ```  

11. 使用輸入作業所傳回的結果集。 您可以使用使用訊息**XmlReader**該**XmlDictionaryWriter**。  

    ```  
    XmlReader reader = message.GetReaderAtBodyContents();  
    ```  

12. 當您完成處理要求，請關閉通道。  

    ```  
    channel.Close()  
    ```  

    > [!IMPORTANT]
    >  處理輸入的作業完成之後，您必須關閉通道。 若要關閉通道的失敗可能會影響您的程式碼的行為。  

13. 當您完成接收的資料變更訊息時，請關閉接聽程式。  

    ```  
    listener.Close()  
    ```  

    > [!IMPORTANT]
    >  關閉接聽程式不會關閉建立使用接聽程式通道。 您必須明確地關閉每一個色頻建立使用接聽程式。  

### <a name="example"></a>範例  
 下列範例會顯示輪詢 MS_SAMPLE_EMPLOYEE 介面資料表輪詢應用程式。 **PollingInput**屬性包含從 MS_SAMPLE_EMPLOYEE 資料表讀取所有資料的 select 陳述式和後輪詢陳述式會從相同的資料表刪除所有資料。 輪詢訊息會寫入`C:\PollingOutput.xml`。  

 更多資料新增至 MS_SAMPLE_EMPLOYEE 介面資料表之前，後續的輪詢訊息將不會包含任何記錄。 您可以執行 insert_apps_data.sql 指令碼提供範例來這麼做。 執行此指令碼之後下, 一個輪詢作業會擷取新記錄插入至資料表。 配接器將繼續輪詢，直到您按下關閉服務主機為止\<傳回\>。  

```  
using System;  
using Microsoft.Adapters.OracleEBS;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Xml;  

namespace SelectPolling_ChannelModel  
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

                OracleEBSBinding binding = new OracleEBSBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
                binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
                binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
                binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
                binding.OracleUserName = "<Enter user name here>";  
                binding.OraclePassword = "<Enter password here>";  
                binding.OracleEBSResponsibilityName = "<Enter responsibility here>";  

                Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name?");  

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
                Console.ReadLine();  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                    Console.ReadLine();  
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
 [開發 Oracle E-business Suite 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)