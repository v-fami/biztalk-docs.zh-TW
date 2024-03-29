---
title: 使用 WCF 通道模型的 Oracle 資料庫中接收以輪詢為基礎的資料變更訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF channel model, receiving polling-based messages
- how to, receive polling-based messages by using the WCF channel model
ms.assetid: 13f501e4-cff7-497c-a9da-fdd6382c779f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03973baf5c55d4f6b5caa3ef28ce0e11b0cd4fa1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969671"
---
# <a name="receive-polling-based-data-changed-messages-in-oracle-database-using-the-wcf-channel-model"></a>使用 WCF 通道模型的 Oracle 資料庫中接收以輪詢為基礎的資料變更訊息
您可以設定[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]輪詢 Oracle 資料庫資料表或檢視之任何資料變更。 若要執行這類輪詢作業時，配接器會定期執行的 Oracle 資料表或檢視，後面接著選擇性的 PL/SQL 程式碼區塊的 SQL 查詢。 SQL 查詢的結果則會傳回由[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]為強型別中的結果集的輸入 POLLINGSTMT 作業程式碼。 如需有關用來設定，然後在 Oracle 上執行輪詢機制資料庫使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 在 Oracle 資料庫配接器接收以輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md)。 強烈建議您先閱讀本主題後再繼續。  
  
 您設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]輪詢和 Oracle 資料庫資料表或檢視的執行個體上設定繫結屬性**OracleDBBinding**。 在 WCF 通道模型中，您再使用此繫結來建置通道接聽程式，您可以從中取得**IInputChannel**通道以接收來自配接器的 POLLINGSTMT 作業。  
  
 如需如何接收作業使用的概觀**IInputChannel**在 WCF 中，請參閱[服務通道層級程式設計](https://msdn.microsoft.com/library/ms789029.aspx)。 
  
 本主題中的各節提供的資訊可協助您執行輪詢 Oracle 資料庫資料表和檢視使用 WCF 通道模型。  
  
## <a name="consuming-the-pollingstmt-request-message"></a>使用 POLLINGSTMT 要求訊息  
 配接器會叫用您的程式碼，以輪詢 Oracle 資料庫的 POLLINGSTMT 作業。 也就是說，配接器傳送 POLLINGSTMT 要求訊息，您會收到**IInputChannel**通道圖案。 POLLINGSTMT 要求訊息包含所指定之查詢的結果集**PollingStatement**繫結屬性。 您可以使用 POLLINGSTMT 訊息中有兩種：  
  
- 若要使用訊息使用節點值串流，您必須呼叫**WriteBodyContents**方法的回應訊息，並將它傳遞**XmlDictionaryWriter**實作資料流處理的節點值。  
  
- 若要取用使用節點資料流處理的訊息，您可以呼叫**GetReaderAtBodyContents**回應訊息，可取得**XmlReader**。  
  
  通常，您會使用節點值使用包含 Oracle LOB 資料行的結果集資料流。  
  
  如需有關 POLLINGSTMT 作業的訊息結構的詳細資訊，請參閱[輪詢作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md)。  
  
  如需有關如何[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援串流 LOB 資料，請參閱[串流大型物件資料類型在 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md)。  
  
  如需實作串流您的程式碼，以支援端對端 LOB 資料的資料流中的節點值的詳細資訊，請參閱[串流處理 Oracle 資料庫的 LOB 資料類型使用的 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)。  
  
## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例會使用 SCOTT。ACCOUNTACTIVITY 資料表與 SCOTT。ACCOUNT_PKG。PROCESS_ACTIVITY 函式。 指令碼來產生這些成品會提供範例。 此範例會執行下列作業：  
  
- 隨著輪詢陳述式的詳細資訊，請從 ACCOUNTACTIVITY 資料表並在主控台上的顯示選取的所有記錄。  
  
- 後輪詢陳述式的一部分，範例會叫用會 ACCOUNTACTIVITY 資料表中的所有記錄都移到 ACTIVITYHISTORY 資料表 PROCESS_ACTIVITY 函式。  
  
- 後續輪詢 ACCOUNTACTIVITY 資料表上的不會傳回任何記錄。 不過，如果您想要輪詢作業傳回多筆記錄的範例，您就必須 ACCOUNTACTIVITY 資料表中插入一些記錄。 您可以執行 more_activity_data.sql 指令碼提供範例來這麼做。  
  
  如需有關範例的詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
## <a name="how-do-i-poll-an-oracle-database-using-an-iinputchannel"></a>我要如何輪詢 Oracle 資料庫使用 IInputChannel？  
 若要輪詢的 Oracle 資料庫資料表或檢視，以接收使用 WCF 通道模型的資料變更訊息，請執行下列步驟。  
  
#### <a name="to-receive-data-changed-messages-using-an-iinputchannel"></a>若要接收資料變更的訊息使用 IInputChannel  
  
1. Visual C# 中建立的專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 本主題中，建立主控台應用程式。  
  
2. 在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleDB`， `Microsoft.ServiceModel.Channels`， `System.ServiceModel`，和`System.Runtime.Serialization`。  
  
3. 開啟 Program.cs 檔案並新增下列命名空間：  
  
   -   `Microsoft.Adapters.OracleDB`  
  
   -   `Microsoft.ServiceModel.Channels`  
  
   -   `System.ServiceModel`  
  
   -   `System.ServiceModel.Description`  
  
   -   `System.ServiceModel.Channels`  
  
   -   `System.Xml`  
  
   -   `System.Runtime.Serialization`  
  
   -   `System.IO`  
  
   -   `Microsoft.ServiceModel.Channels.Common`  
  
4. 建立的執行個體**OracleDBBinding**和設定必要設定輪詢的繫結屬性。 您必須設定至少**InboundOperationType**， **PollingStatement**，並**PollingInterval**繫結屬性。 為此範例中，您也可以設定**PostPollStatement**繫結屬性。 如需有關用來設定輪詢的屬性繫結的詳細資訊，請參閱[在 Oracle 資料庫配接器接收以輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md)。  
  
   ```  
   OracleDBBinding binding = new OracleDBBinding();  
   binding.InboundOperationType = InboundOperation.Polling;  
   binding.PollingInterval = 30;  
   binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
   binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;"  
   ```  
  
5. 建立繫結參數集合，並設定認證。  
  
   ```  
   ClientCredentials credentials = new ClientCredentials();  
   credentials.UserName.UserName = "SCOTT";  
   credentials.UserName.Password = "TIGER";  
  
   BindingParameterCollection bindingParams = new BindingParameterCollection();  
   bindingParams.Add(credentials);  
   ```  
  
6. 建立通道接聽程式，然後開啟它。 您可以建立接聽程式所叫用**BuildChannelListener < IInputChannel\>** 方法**OracleDBBinding**。 您可以修改 POLLINGSTMT 作業的目標命名空間中的連線 URI 設定 PollingId 屬性。 如需配接器連線 URI 的詳細資訊，請參閱[建立的 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。  
  
   ```  
   IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
   listener.Open();  
   ```  
  
7. 取得**IInputChannel**藉由叫用的通道**AcceptChannel**接聽程式上的方法並將它開啟。  
  
   ```  
   IInputChannel channel = listener.AcceptChannel();  
   channel.Open();  
   ```  
  
8. 叫用**接收**從配接器取得的下一個 POLLINGSTMT 訊息的通道上。  
  
   ```  
   Message message = channel.Receive();  
   ```  
  
9. 取用 POLLINGSTMT 作業所傳回的結果集。 您可以使用使用訊息**XmlReader**該**XmlDictionaryWriter**。  
  
    ```  
    XmlReader reader = message.GetReaderAtBodyContents();  
    ```  
  
10. 當您完成處理要求，請關閉通道。  
  
    ```  
    channel.Close()  
    ```  
  
    > [!IMPORTANT]
    >  處理 POLLINGSTMT 作業完成之後，您必須關閉通道。 若要關閉通道的失敗可能會影響您的程式碼的行為。  
  
11. 當您完成接收的資料變更訊息時，請關閉接聽程式。  
  
    ```  
    listener.Close()  
    ```  
  
    > [!IMPORTANT]
    >  關閉接聽程式不會關閉建立使用接聽程式通道。 您必須明確地關閉每一個色頻建立使用接聽程式。  
  
### <a name="example"></a>範例  
 下列範例示範如何設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]輪詢 Oracle 資料庫資料表和檢視表，並接收 POLLLINGSTMT 作業使用 WCF 通道模型。 POLLINGSTMT 作業中傳回的結果集就會寫入主控台中，使用**XmlReader**。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF LOB Adapter SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Add this namespace for channel model  
using System.ServiceModel.Channels;  
  
using System.Xml;  
using System.Runtime.Serialization;  
using System.IO;  
  
// Include this namespace for the WCF LOB Adapter SDK and Oracle exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
namespace OraclePollingCM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Uri connectionUri = new Uri("oracleDB://ADAPTER/");  
  
            IChannelListener<IInputChannel> listener = null;  
            IInputChannel channel = null;  
  
            // set timeout to receive POLLINGSTMT message  
            TimeSpan messageTimeout = new TimeSpan(0, 0, 30);  
  
            Console.WriteLine("Sample Started");  
  
            try  
            {  
                // Create a binding: specify the InboundOperationType, PollingInterval (in seconds), the           
                // PollingStatement,and the PostPollStatement.  
                OracleDBBinding binding = new OracleDBBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PollingInterval = 30;  
                binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
                binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
                // Create a binding parameter collection and set the credentials  
                ClientCredentials credentials = new ClientCredentials();  
                credentials.UserName.UserName = "SCOTT";  
                credentials.UserName.Password = "TIGER";  
  
                BindingParameterCollection bindingParams = new BindingParameterCollection();  
                bindingParams.Add(credentials);  
  
                Console.WriteLine("Opening listener");  
                // get a listener  from the binding  
                listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
                listener.Open();  
  
                Console.WriteLine("Opening channel");  
                // get a channel from the listener  
                channel = listener.AcceptChannel();  
                channel.Open();  
  
                Console.WriteLine("Channel opened -- waiting for polled data");  
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
  
                    // Write the TID, ACCOUNT, AMOUNT, and TRANSDATE for each record to the Console  
                    Console.WriteLine("\nPolling data received for request number {0}", i+1);  
                    Console.WriteLine("Tx ID\tACCOUNT\tAMOUNT\tTx DATE");  
  
                    while (reader.Read())  
                    {  
                        if (reader.IsStartElement())  
                        {  
                            switch (reader.Name)  
                            {  
                                case "POLLINGSTMTRECORD":  
                                    Console.Write("\n");  
                                    break;  
  
                                case "TID":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
  
                                case "ACCOUNT":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
                                case "AMOUNT":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
  
                                case "TRANSDATE":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
  
                                default:  
                                    break;  
                            }  
                        }  
                    }  
  
                    // return the cursor  
                    Console.WriteLine();  
  
                    // close the reader  
                    reader.Close();  
  
                    //            To save the polling data to a file you can REPLACE the code above with the following  
                    //  
                    //            XmlDocument doc = new XmlDocument();  
                    //            doc.Load(reader);  
                    //            using (XmlWriter writer = XmlWriter.Create("PollingOutput.xml"))  
                    //            {  
                    //                doc.WriteTo(writer);  
                    //            }  
                    message.Close();  
                }  
  
                Console.WriteLine("\nPolling done -- hit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the Oracle Database");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the Oracle Database");  
                Console.WriteLine(cex.InnerException.Message);  
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
 [開發使用 WCF 通道模型的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)