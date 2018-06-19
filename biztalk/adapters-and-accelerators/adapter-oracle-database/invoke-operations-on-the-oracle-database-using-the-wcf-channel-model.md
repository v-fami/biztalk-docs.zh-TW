---
title: 使用 WCF 通道模型之 Oracle 資料庫上叫用作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- invoking operations, using the WCF channel model
- WCF channel model, invoking operations
- invoking operations
- operations, invoking
ms.assetid: 6dd95c18-8f78-46d0-8845-b74890614c33
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65eb19845bf4e103b4abe2466e58fb09a96c23c9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25962780"
---
# <a name="invoke-operations-on-the-oracle-database-using-the-wcf-channel-model"></a>使用 WCF 通道模型之 Oracle 資料庫上叫用作業
您可以在叫用作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用**IRequestChannel**或**IOutputChannel**圖形以將訊息傳送至配接器。 基本模式是使用繫結建立通道處理站為必要的通道圖案 (**OracleDBBinding**) 和建立的連線 URI 的端點。 然後，您建立**訊息**表示 SOAP 訊息，並符合您目標的作業的訊息結構描述執行個體。 然後您可以傳送這**訊息**至[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用從通道處理站建立通道。 如果您使用**IRequestChannel**，您收到的回應。 如果沒有執行 Oracle 資料庫時，作業問題[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會擲回**Microsoft.ServiceModel.Channels.Common.TargetSystemException**。  
  
 如需如何傳送作業使用的概觀**IRequestChannel**在 WCF 中，請參閱 < Programming 用戶端通道層級 」，網址[http://go.microsoft.com/fwlink/?LinkId=106081](http://go.microsoft.com/fwlink/?LinkId=106081)。  
  
 本主題中的各節提供的資訊可協助您在上叫用作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 WCF 通道模型。  
  
## <a name="creating-and-consuming-messages-for-outbound-operations"></a>建立及取用訊息輸出作業  
 若要在叫用作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您將使用目標作業的要求訊息的傳送**IRequestChannel**或**IOutputChannel**。 如果您使用**IRequestChannel**配接器會傳回作業結果的回應訊息中。  
  
 如需詳細的要求和回應訊息結構描述和每個作業的訊息動作相關資訊，請參閱[訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)。  
  
 您建立的要求訊息和取用回應訊息的方式決定配接器會執行節點資料流或資料流處理的節點值。 這會依次決定是否執行支援的作業的 LOB 資料的端對端資料流。  
  
### <a name="creating-the-request-message"></a>建立要求訊息  
 您可以使用兩種方式之一來建立要求訊息：  
  
-   若要建立可用於節點值的訊息在串流處理您必須傳遞的訊息本文的**XmlBodyWriter**實作節點值的資料流。  
  
-   若要建立可用於節點的訊息在串流處理您可以傳遞的訊息本文的**XmlReader**。  
  
 您通常使用串流，以支援端對端的資料流的要求訊息中的 Oracle LOB 資料的節點值。 支援此功能的唯一作業是 UpdateLOB。  
  
### <a name="consuming-the-response-message"></a>取用回應訊息  
 您可以使用其中一種方式中的回應訊息：  
  
-   若要使用訊息使用的節點值的資料流您必須呼叫**WriteBodyContents**方法回應訊息，並將它傳遞**XmlDictionaryWriter**實作節點值的資料流。  
  
-   若要使用訊息使用節點資料流處理，您可以呼叫**GetReaderAtBodyContents**要取得的回應訊息上**XmlReader**。  
  
 您通常使用串流，以支援端對端的資料流的回應訊息中的 Oracle LOB 資料的節點值。 有許多作業都支援這項功能。  
  
### <a name="lob-data-and-message-streaming-support"></a>LOB 資料和訊息資料流支援  
 如需有關如何[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援資料流處理 LOB 資料，請參閱[串流處理大型物件資料類型在 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md)。  
  
 如需實作串流處理您的程式碼，以支援端對端 LOB 資料的資料流中的節點值的詳細資訊，請參閱[串流處理 Oracle 資料庫的 LOB 資料類型使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)。  
  
## <a name="transaction-support-on-outbound-operations-in-the-wcf-channel-model"></a>在 WCF 通道模型輸出作業上的交易支援。  
 配接器會執行您在專用的 Oracle 資料庫上交易內叫用每個作業。 您可以設定來控制這些交易的隔離等級**TransactionIsolationLevel**繫結屬性。  
  
## <a name="about-the-examples-used-in-this-topic"></a>關於本主題中使用的範例  
 本主題中的範例使用 SCOTT。ACCOUNTACTIVITY 資料表。 指令碼來產生這些成品隨附於 SDK 範例。 如需 SDK 範例的詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。  
  
## <a name="how-do-i-invoke-an-operation-by-using-a-channel"></a>如何叫作業用使用通道？  
 若要使用叫用作業**IRequestChannel**，執行下列步驟。  
  
#### <a name="how-to-invoke-an-operation-by-using-an-instance-of-irequestchannel"></a>如何使用 IRequestChannel 的執行個體叫用作業  
  
1.  建置通道處理站 (**ChannelFactory\<IRequestChannel\>**)。 若要這樣做，您必須指定繫結 (**OracleDBBinding**) 以及端點位址。 以命令方式在您的程式碼或是宣告式組態中，您可以指定的繫結與端點位址。 如需如何在組態中指定的繫結和端點位址的詳細資訊，請參閱[建立使用 Oracle 資料庫的通道](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md)。  
  
    ```  
    // Create a binding  
    OracleDBBinding binding = new OracleDBBinding();  
    // Create an endpoint address by using the connection URI  
    EndpointAddress address = new EndpointAddress("oracledb://ADAPTER");  
    // Create the channel factory  
    ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
    ```  
  
2.  設定使用者名稱密碼認證之通道處理站使用**ClientCredentials**屬性。  
  
    ```  
    factory.Credentials.UserName.UserName = "SCOTT";  
    factory.Credentials.UserName.Password = "TIGER";  
    ```  
  
3.  開啟通道處理站。  
  
    ```  
    factory.Open();  
    ```  
  
4.  取得從原廠的通道，然後開啟它。  
  
    ```  
    IRequestChannel channel = factory.CreateChannel();  
    channel.Open();  
    ```  
  
5.  建立**訊息**目標作業的執行個體。 請務必確認已指定目標作業的訊息動作。 在此範例中，訊息本文會藉由建立**XmlReader**透過 file。 目標作業是 SCOTT/EMP 資料表上的選取作業。  
  
    ```  
    XmlReader readerIn = XmlReader.Create("SelectAllActivity.xml");  
    Message messageIn = Message.CreateMessage(MessageVersion.Default,  
        "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select",  
        readerIn);  
    ```  
  
6.  叫用**要求**方法來傳送訊息給在通道上的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]和接收回覆。 如果 Oracle 資料庫中發生例外狀況，配接器會擲回**TargetSystemException**。 （其他例外狀況可能會有非 Oracle 例外狀況。）您可以取得描述來自 Oracle 錯誤**InnerException.Message**屬性**TargetSystemException**。  
  
    ```  
    try  
    {  
        Message messageOut = channel.Request(messageIn);  
    }  
    catch (Exception ex)  
    {  
        // handle exception  
    }  
    ```  
  
7.  處理回應。 在此範例中， **GetReaderAtBodyContents**来取得訊息本文的回應訊息上呼叫。  
  
    ```  
    XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
    ```  
  
8.  當您完成處理回應訊息時，關閉讀取器和訊息。  
  
    ```  
    readerOut.Close();  
    messageOut.Close();  
    ```  
  
9. 當您完成使用通道和通道處理站，將它們關閉。 關閉處理站會關閉所有使用它所建立的通道。  
  
    ```  
    channel.Close()  
    factory.Close();  
  
    ```  
  
 您遵循相同的步驟，以傳送訊息，使用**IOutputChannel**圖形除外：  
  
-   您建立**ChannelFactory\<IOutputChannel\>** 步驟 1。  
  
-   您呼叫**傳送**步驟 6 中的通道上的方法。 `channel.Send(messageIn);`。  
  
-   不沒有傳回任何回應訊息**IOutputChannel**。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用叫用選取的作業**IRequestChannel**通道。 選取回應訊息由使用**XmlReader**而傳回的記錄數目會寫入至主控台。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
using System.Xml;  
using System.IO;  
using System.Runtime.Serialization;  
  
namespace RequestChanneSample  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The Select operation request message  
            const string selectRequestString =  
                "\<Select xmlns=\"http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY\"\>" +  
                    "<COLUMN_NAMES>*</COLUMN_NAMES>" +  
                    "<FILTER>ACCOUNT = 100002</FILTER>" +  
                "</Select>";  
            try  
            {  
                // Create binding -- specify binding properties before you open the factory.  
                OracleDBBinding odbBinding = new OracleDBBinding();  
  
                // Create address.  
                EndpointAddress odbAddress = new EndpointAddress("oracledb://ADAPTER/");  
  
                // Create channel factory from binding and address.  
                ChannelFactory<IRequestChannel> factory =   
                    new ChannelFactory<IRequestChannel>(odbBinding, odbAddress);  
  
                // Specify credentials   
                factory.Credentials.UserName.UserName = "SCOTT";  
                factory.Credentials.UserName.Password = "TIGER";  
  
                // Open the factory.  
                factory.Open();  
  
                // Get a channel.  
                IRequestChannel channel = factory.CreateChannel();  
  
                // Open the channel.  
                channel.Open();  
  
                // Create the request message from the string  
                StringReader strReader = new StringReader(selectRequestString);  
                XmlReader readerIn = XmlReader.Create(strReader);  
  
                Message requestMessage = Message.CreateMessage(MessageVersion.Default,  
                    "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select",  
                    readerIn);  
  
                Send the message and get a respone  
                Message responseMessage = channel.Request(requestMessage);  
  
                // Get an XmlReader from the message  
                XmlReader readerOut = (XmlReader) responseMessage.GetReaderAtBodyContents();  
  
                // Count the number of records returned and write to the console.  
                readerOut.MoveToContent();  
                int numberOfRecordsReturned = 0;  
                while (readerOut.Read())  
                {  
                    if (readerOut.NodeType == XmlNodeType.Element && readerOut.Name == "ACCOUNTACTIVITYRECORDSELECT")  
                        numberOfRecordsReturned++;  
                }  
  
                Console.WriteLine("{0} records returned.", numberOfRecordsReturned);  
  
                // Close the output reader and message  
                readerOut.Close();  
                responseMessage.Close();  
  
                //Close channel  
                channel.Close();  
  
                //Close the factory  
                factory.Close();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex.Message);  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [開發 Oracle 資料庫應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)