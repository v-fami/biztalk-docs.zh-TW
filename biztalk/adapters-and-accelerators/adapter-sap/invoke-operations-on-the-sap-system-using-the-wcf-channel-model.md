---
title: 使用 WCF 通道模型的 SAP 系統上叫用作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF channel model, supporting BAPI transactions
- WCF channel model, invoking operations on the SAP system
ms.assetid: 80ed85ff-360d-4b7f-a119-cd2a99c21cf4
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1030e0a743a9b06d856bc593198f4afebc1ffa38
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965620"
---
# <a name="invoke-operations-on-the-sap-system-using-the-wcf-channel-model"></a>使用 WCF 通道模型的 SAP 系統上叫用作業
您在上叫用作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用**IRequestChannel**或**IOutputChannel**通道將訊息傳送至配接器的圖案。 基本模式是使用繫結建立通道處理站為必要的通道圖案 (**SAPBinding**) 和建立的連線 URI 的端點。 然後，您建立**訊息**表示 SOAP 訊息，並符合您目標的作業的訊息結構描述執行個體。 然後您可以傳送這**訊息**至[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用從通道處理站建立通道。 如果您使用**IRequestChannel**，您收到的回應。 如果沒有執行 SAP 系統上的操作問題[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會擲回**Microsoft.ServiceModel.Channels.Common.TargetSystemException**。  
  
 如需如何傳送作業使用的概觀**IRequestChannel**在 WCF 中，請參閱[用戶端通道層級程式設計](https://msdn.microsoft.com/library/ms788970.aspx)。  
  
 本主題中的各節提供的資訊可協助您在上叫用作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用 WCF 通道模型。  
  
## <a name="supporting-bapi-transactions-in-the-wcf-channel-model"></a>支援的 WCF 通道模型中的 BAPI 異動  
 使用相同的 SAP 連接叫用的所有 Bapi 都位於 SAP 系統的相同邏輯單元的工作 (LUW)-或--交易的一部分。 每個 WCF 通道代表 SAP 系統的唯一連接。 若要支援使用 WCF 的 BAPI 交易通道模型：  
  
-   請確定每個 BAPI 中 LUW （交易） 會透過相同的通道傳送。 這包括 BAPI_TRANSACTION 認可或 BAPI_TRANSACTION_ROLLBACK 作業。  
  
-   請確定您關閉之前您叫用下一個 BAPI 通道上的收到 BAPI 的任何回應訊息。 （您應該這麼做的每一作業; 但是更是特別重要的 Bapi。）  
  
 如需 BAPI 交易的詳細資訊，請參閱[SAP 中的 Bapi 作業](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)。  
  
## <a name="streaming-flat-file-idocs-to-the-sap-adapter"></a>資料流處理的一般檔案 Idoc 至 SAP 配接器  
 您可以使用 SendIdoc 作業傳送一般檔案 （字串） IDOC 至配接器。 IDOC 資料會以這項作業中的單一節點下的字串表示。 基於這個理由，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援節點值的資料流處理的要求訊息。 若要執行的節點值的資料流，您必須建立 SendIdoc 作業的要求訊息使用**System.ServiceModel.Channels.BodyWriter**能夠串流 IDOC 資料。 如需如何執行這項操作資訊，請參閱[SAP 使用 WCF 通道模型中的資料流處理一般檔案 Idoc](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md)。  
  
## <a name="how-do-i-invoke-an-operation-by-using-a-channel"></a>如何叫作業用使用通道？  
 若要使用叫用作業**IRequestChannel**，執行下列步驟。  
  
#### <a name="how-to-invoke-an-operation-by-using-an-instance-of-irequestchannel"></a>如何使用 IRequestChannel 的執行個體叫用作業  
  
1.  建置通道處理站 (**ChannelFactory\<IRequestChannel\>**)。 若要這樣做，您必須指定繫結 (**SAPBinding**) 以及端點位址。 以命令方式在您的程式碼或是宣告式組態中，您可以指定的繫結與端點位址。 您應該設定屬性的作業所需先開啟之處理站會傳送任何繫結。 如需如何在組態中指定的繫結和端點位址的詳細資訊，請參閱[建立通道使用 SAP](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md)。  
  
    ```  
    // Create a binding  
    SAPBinding binding = new SAPBinding();  
    // Create an endpoint address by using the connection URI  
    EndpointAddress endpointAddress = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
    // Create the channel factory  
    ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
    ```  
  
2.  設定使用者名稱密碼認證之通道處理站使用**ClientCredentials**屬性。  
  
    ```  
    factory.Credentials.UserName.UserName = "YourUserName";  
    factory.Credentials.UserName.Password = "YourPassword";  
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
  
5.  建立**訊息**目標作業的執行個體。 請務必確認已指定目標作業的訊息動作。 在此範例中，訊息本文會藉由建立**XmlReader**字串。 目標作業會叫用 SD_RFC_CUSTOMER_GET RFC，SAP 系統上。  
  
    ```  
    string inputXml = "\<SD_RFC_CUSTOMER_GET xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> <KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>";  
  
    //create an XML reader from the input XML  
    XmlReader reader = XmlReader.Create(new MemoryStream(Encoding.Default.GetBytes(inputXml)));  
  
    //create a WCF message from our XML reader  
    Message inputMessge = Message.CreateMessage(MessageVersion.Soap11, "http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET", reader);  
    ```  
  
6.  叫用**要求**方法來傳送訊息給在通道上的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]和接收回覆。 如果 SAP 系統遇到的例外狀況，配接器會擲回**TargetSystemException**。 （其他例外狀況可能會有非 SAP 例外狀況。）您可以取得錯誤的描述 SAP 從**InnerException.Message**屬性**TargetSystemException**。  
  
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
  
10.  
  
 您遵循相同的步驟，以傳送訊息，使用**IOutputChannel**圖形除外：  
  
-   您建立**ChannelFactory\<IOutputChannel\>** 步驟 1。  
  
-   您呼叫**傳送**步驟 6 中的通道上的方法。 `channel.Send(messageIn);`。  
  
-   不沒有傳回任何回應訊息**IOutputChannel**。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用叫用 RFC **IRequestChannel**通道。 這個範例會叫用來取得一份客戶名稱開頭為"AB"SD_RFC_CUSTOMER_GET RFC。 回應訊息由使用**XmlReader**和客戶編號及名稱，傳回每一位客戶會寫入至主控台。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.Xml;  
using System.IO;  
  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel.Channels;  
  
namespace SapRfcClientCM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            //create a binding  
            SAPBinding binding = new SAPBinding();  
  
            //set up an endpoint address.  
            EndpointAddress endpointAddress = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
            //create a channel factory, capable of sending a request to SAP and receiving a reply (IRequestChannel)  
            ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, endpointAddress);  
  
            // add credentials  
            factory.Credentials.UserName.UserName = "YourUserName";  
            factory.Credentials.UserName.Password = "YourPassword";  
  
            //open the factory  
            factory.Open();  
  
            //obtain a channel from the factory by specifying the address you want to connect to  
            IRequestChannel channel = factory.CreateChannel();  
  
            //open the channel  
            channel.Open();  
  
            //create an XML message to send to the SAP system  
            //We are invoking the SD_RFC_CUSTOMER_GET RFC.  
            //The XML below specifies that we want to search for customers with names starting with "AB"  
            string inputXml = "<SD_RFC_CUSTOMER_GET xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> <KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>";  
  
            //create an XML reader from the input XML  
            XmlReader readerOut = XmlReader.Create(new MemoryStream(Encoding.Default.GetBytes(inputXml)));  
  
            //create a WCF message from the XML reader  
            Message messageOut = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET", readerOut);  
  
            //send the message to SAP and obtain a reply  
            Message messageIn = channel.Request(messageOut);  
  
            // Write the KUNNR and NAME1 fields for each returned record to the Console  
            Console.WriteLine("Results of SD_RFC_CUSTOMER_GET");  
            Console.WriteLine("KUNNR\t\tNAME1");  
  
            XmlReader readerIn = messageIn.GetReaderAtBodyContents();  
  
            while (readerIn.Read())  
            {  
                if (readerIn.IsStartElement())  
                {  
                    switch (readerIn.Name)  
                    {  
                        case "RFCCUST":  
                            Console.Write("\n");  
                            break;  
  
                        case "KUNNR":  
                            readerIn.Read();  
                            Console.Write(readerIn.ReadString() + "\t");  
                            break;  
  
                        case "NAME1":  
                            readerIn.Read();  
                            Console.Write(readerIn.ReadString() + "\t");  
                            break;  
  
                        default:  
                            break;  
                    }  
                }  
            }  
  
            // return the cursor  
            Console.WriteLine();  
  
            // Close the input reader  
            readerIn.Close();  
  
            // Close the input message. You should do this for every message you   
            // send on the channel  
            messageIn.Close();  
  
            // close the channel when you are done using it.  
            channel.Close();  
  
            //close the factory  
            //note: closing the factory will close all of its channels.  
            factory.Close();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>請參閱  
[使用 WCF 通道模型開發應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)