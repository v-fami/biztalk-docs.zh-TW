---
title: 從使用 WCF 通道模型的 SAP 系統接收輸入的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF channel model, streaming inbound flat-file IDOCs
- WCF channel model, receiving inbound operations from the SAP system
- WCF channel model, raising an exception
ms.assetid: d71d0537-fda4-44ab-85dc-6e27aad23caf
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7c0c819372cf23842eb5311df8636e55e28c72a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969679"
---
# <a name="receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model"></a>從使用 WCF 通道模型的 SAP 系統接收輸入的作業
若要做為 RFC 伺服器，並接收 SAP 系統 （例如傳送 IDOC，或叫用 RFC） 叫用的作業，您必須建立可接聽來自 SAP 程式 ID 的訊息，透過的通道接聽程式**System.servicemodel.channels.ireplychannel 之**通道圖案。  
  
 通道接聽程式 (**System.ServiceModel.Channels.IChannelListener**) 是可用來從特定的 WCF 端點接收訊息的 WCF 通訊物件。 通道接聽程式做為您可以從中建立的叫用用戶端 (SAP system) 的訊息可以由您的服務接收的通道處理站。 建立通道接聽程式藉由從**Microsoft.Adapters.SAP.SAPBinding**藉由叫用的物件**BuildChannelListener**方法。 您提供的 SAP 連接指定的輸入的操作將會收到這個方法 SAP 程式 ID URI。  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援**IReplyChannel**通道圖案。 **IReplyChannel**通道支援輸入的要求-回應訊息交換模式。 也就是在其中一個外部程式會傳送要求訊息透過通道和程式的模式會傳回回應。  
  
 如需如何接收作業使用的概觀**IReplyChannel**在 WCF 中，請參閱[服務通道層級程式設計](https://msdn.microsoft.com/library/ms789029.aspx)。
  
 本節涵蓋的特定 SAP 系統從接收作業的下列主題：  
  
-   如何篩選針對特定作業使用的通道接聽程式。  
  
-   如何引發例外狀況於 SAP 系統。  
  
-   從 SAP 配接器的輸入的一般檔案 Idoc 的串流處理。  
  
-   如何從 SAP 系統接收作業。  
  
## <a name="how-do-i-filter-operations-using-the-channel-listener"></a>我要如何篩選作業使用的通道接聽程式？  
  
### <a name="using-an-inboundactioncollection-to-filter-operations"></a>若要篩選作業使用 InboundActionCollection  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供**Microsoft.ServiceModel.Channels.InboundActionCollection**類別可讓您篩選是由通道接聽程式接收，並傳遞至您的應用程式程式碼的作業。 若要篩選針對特定作業中,，您可以建立這個類別的執行個體使用接聽程式端點的 URI。 然後您加入至集合的每個目標作業 （要求） 訊息動作。 最後，您可以新增至輸入的動作集合**System.ServiceModel.Channels.BindingParameterCollection**物件，並接著將此繫結參數集合傳遞至建立通道接聽程式的呼叫。  
  
 如果 SAP 系統會叫用不是輸入的動作集合中的作業：  
  
- [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]回到呼叫端中的例外狀況的例外狀況，在 SAP 系統，並出現下列訊息: 「 未處理內送的 RFC 呼叫 [RFC_NAME] Rfc 伺服器上 」。 在此訊息中，[RFC_NAME] 是 RFC (比方說，IDOC_INBOUND_ASYNCHRONOUS) 的名稱。  
  
- 配接器會擲回**Microsoft.ServiceModel.Channels.Common.AdapterException**的訊息，指出已收到的作業。 如需如何使用這個例外狀況的範例，請參閱本主題結尾處的範例。  
  
  下列程式碼範例示範如何使用**InboundActionCollection**建立單一的 RFC，Z_RFC_MKD_DIV 篩選的通道接聽程式。  
  
```  
// The connection Uri must specify listener parameters (or an R-type destination in saprfc.ini)  
// and credentials.  
Uri listeneraddress =  
    new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGATEWAY&ListenerGwHost=YourSAPHost&ListenerProgramId=SAPAdapter");  
  
// Create a binding and set AcceptCredentialsInUri to true  
SAPBinding binding = new SAPBinding();  
binding.AcceptCredentialsInUri = true;  
  
// Create an InboundActionCollection and add the message actions to listen for,  
// only the actions added to the InboundActionCollection are received on the channel.  
// In this case a single action is specified: http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV  
InboundActionCollection actions = new InboundActionCollection(listeneraddress);  
actions.Add("http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV");  
  
// Create a BindingParameterCollection and add the InboundActionCollection  
BindingParameterCollection bpcol = new BindingParameterCollection();  
bpcol.Add(actions);  
  
// Create the channel listener by specifying the binding parameter collection (to filter for the Z_RFC_MKD_DIV action)  
listener = binding.BuildChannelListener<IReplyChannel>(listeneraddress, bpcol);  
```  
  
### <a name="manually-filtering-operations"></a>以手動方式篩選作業  
 如果您未指定輸入的動作集合之通道接聽程式，叫用的 SAP 系統的所有作業會被都傳送到您的程式碼。 您可以手動篩選這類作業，藉由檢查傳入要求的訊息動作。  
  
 也可能情況下您要篩選其內容為基礎的作業。 如果您收到的 Idoc 中的範例：  
  
- 字串格式 ( **ReceiveIDocFormat**屬性的繫結**字串**)，所有使用 ReceiveIdoc 作業接收 Idoc。  
  
- Rfc 格式 ( **ReceiveIDocFormat**屬性的繫結**Rfc**)，所有使用 IDOC_INBOUND_ASYNCHRONOUS RFC 或 INBOUND_IDOC_PROCESS RFC 接收 Idoc。  
  
  在此案例中您可能想要實作篩選基礎 （例如的 IDOC 類型） 特定的 IDOC 參數，在您的程式碼。  
  
  當您以手動方式篩選作業時，您可以傳回錯誤以[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]未處理的作業。 這會引發例外狀況例外狀況，呼叫端 SAP 系統上。 如果您不想要引發的例外狀況，在 SAP 上，您也可以傳回空的回應。  
  
  下列程式碼示範如何以手動方式篩選 Z_RFC_MKD_DIV 作業。  
  
```  
// Get the message from the channel  
RequestContext rc = channel.ReceiveRequest();  
Message reqMessage = rc.RequestMessage;  
  
// Filter based on the message action.  
if (reqMessage.Headers.Action == "http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV")  
{  
  
    // Process message and return response.  
    ...  
  
}  
else  
{  
    // If this isn't the correct message return an empty response or a fault message.  
    // This example returns an empty response.  
    rc.Reply(Message.CreateMessage(MessageVersion.Default, reqMessage.Headers.Action + "/response"));  
}  
```  
  
## <a name="how-do-i-raise-an-exception-on-the-sap-system"></a>如何提出 SAP 系統上的例外狀況？  
 表示呼叫端 SAP 系統，您可以回覆要求訊息的 SOAP 錯誤與錯誤。 當您傳回 SOAP 錯誤[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，配接器傳回給呼叫端 SAP 系統上的例外狀況的例外狀況。 例外狀況訊息會從 SOAP 錯誤的項目。  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] SAP 例外狀況，以根據下列優先順序的順序會建立訊息：  
  
1.  如果 SOAP 錯誤中包含詳細資料物件，此配接器會序列化為字串的詳細資料和例外狀況訊息設為這個字串。  
  
2.  如果 SOAP 錯誤中包含的原因，例外狀況訊息設為其值。  
  
3.  配接器的序列化，否則為**MessageFault**字串和例外狀況訊息的物件本身設為這個字串。  
  
> [!NOTE]
>  配接器只會將錯誤訊息使用建立於 SAP 系統; 所引發的例外狀況中傳回的例外狀況訊息因此，您要為這些實體的值完全是由您決定。  
  
 WCF 會提供**System.ServiceModel.Channels.MessageFault**類別來封裝 SOAP 錯誤的記憶體中表示。 您可以使用任何靜態多載**MessageFault.CreateFault**方法來建立新的 SOAP 錯誤，您可以從中再建立的錯誤訊息藉由叫用適當**Message.CreateMessage**多載。 WCF 也提供的多載**CreateMessage**所建立的錯誤訊息，而不使用**MessageFault**物件。  
  
 您使用**System.ServiceModel.Channels.RequestContext.Reply**方法，以傳回至配接器的錯誤訊息。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會忽略錯誤訊息的訊息動作，因此您可以設定任何值的訊息動作。  
  
 下列範例示範如何傳回錯誤訊息[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 這個範例省略了建立的通道接聽程式和通道的步驟。  
  
```  
RequestContext rc = channel.ReceiveRequest();  
…  
// Start processing the inbound message  
…  
// If an error is encountered return a fault to the SAP system  
// This example uses CreateMessage overload to create a fault message.  
// The overload takes a SOAP version, fault code, reason, and message action  
// The SAP adapter ignores the message action for a fault so you can set it to any value you want.   
Message faultMessage = Message.CreateMessage(MessageVersion.Default, new FaultCode("SAP Example Fault"), "Testing SAP Faults", rc.RequestMessage.Headers.Action + "/fault");  
  
rc.Reply(faultMessage);  
```  
  
## <a name="streaming-inbound-flat-file-idocs-from-the-sap-adapter"></a>SAP 配接器從資料流輸入的一般檔案 Idoc  
 您會收到一般檔案 （字串） 的 Idoc 輸入 ReceiveIdoc 作業中的配接器。 IDOC 資料是以這項作業中的單一節點下的字串表示。 基於這個理由，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援節點值的資料流處理的要求訊息。 若要執行串流處理的節點值，您必須透過 ReceiveIdoc 作業的要求訊息，藉由叫用**Message.WriteBodyContents**方法**System.Xml.XmlDictionaryWriter** ，可以串流 IDOC 的資料。 如需如何執行這項操作的資訊，請參閱[串流中使用 WCF 通道模型的 SAP 的一般檔案 Idoc](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md)。  
  
## <a name="how-do-i-receive-operations-from-a-sap-system-using-an-ireplychannel"></a>如何在使用 IReplyChannel 的 SAP 系統從接收作業？  
 若要使用的 WCF 通道模型，從 SAP 系統接收作業，執行下列步驟。  
  
#### <a name="to-receive-operations-from-the-sap-system-using-an-ireplychannel"></a>若要從 SAP 系統，請使用 IReplyChannel 接收作業  
  
1.  建立的執行個體**SAPBinding**並設定您想要接收作業所需的繫結屬性。 您必須設定至少**AcceptCredentialsInUri**繫結屬性為 true。 若要做為 tRFC 伺服器，您必須設定**TidDatabaseConnectionString**繫結屬性。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
    ```  
    SAPBinding binding = new SAPBinding();  
    binding.AcceptCredentialsInUri = true;  
    ```  
  
2.  建立**BindingParameterCollection**並加入**InboundActionCollection** ，其中包含您想要接收作業的動作。 配接器會傳回例外狀況至 SAP 系統的所有其他作業。 此步驟是選擇性的。 如需詳細資訊，請參閱 <<c0> [ 接收輸入作業使用 WCF 通道模型的 SAP 系統從](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)。  
  
    ```  
    InboundActionCollection actions = new InboundActionCollection(listeneraddress);  
    actions.Add("http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV");  
    BindingParameterCollection bpcol = new BindingParameterCollection();  
    bpcol.Add(actions);  
    ```  
  
3.  建立通道接聽程式，藉由叫用**BuildChannelListener < IReplyChannel\>** 方法**SAPBinding**並將它開啟。 您可以指定 SAP 連線 URI 做為其中一個此方法的參數。 連線 URI 必須包含在 SAP 系統的 RFC 目的地的參數。 如需有關 SAP 連線 URI 的詳細資訊，請參閱[建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。 如果您建立**BindingParameterCollection**在步驟 3 中，您也指定這當您建立通道接聽程式。  
  
    ```  
    Uri listeneraddress =  
        new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGATEWAY&ListenerGwHost=YourSAPHost&ListenerProgramId=SAPAdapter");  
    IChannelListener<IReplyChannel> listener = binding.BuildChannelListener<IReplyChannel>(connectionUri, bpcol);  
    listener.Open();  
    ```  
  
4.  取得**IReplyChannel**藉由叫用的通道**AcceptChannel**接聽程式上的方法並將它開啟。  
  
    ```  
    IReplyChannel channel = listener.AcceptChannel();  
    channel.Open();  
    ```  
  
5.  叫用**ReceiveRequest**從配接器取得下一項作業的要求訊息的通道上。  
  
    ```  
    RequestContext rc = channel.ReceiveRequest();  
    ```  
  
6.  使用配接器傳送要求訊息。 取得要求訊息從**RequestMessage**屬性**RequestContext**。 您可以使用使用訊息**XmlReader**該**XmlDictionaryWriter**。  
  
    ```  
    XmlReader reader = (XmlReader)rc.RequestMessage.GetReaderAtBodyContents();  
    ```  
  
7.  完成作業，藉由傳回至 SAP 系統的回應或錯誤：  
  
    1.  處理訊息，並將回應傳回給 SAP 系統的回應訊息傳回至配接器。 這個範例會傳回空的訊息。  
  
        ```  
        respMessage = Message.CreateMessage(MessageVersion.Default, rc.RequestMessage.Headers.Action + "/response");  
        rc.Reply(respMessage);  
        ```  
  
    2.  返回 SAP 系統的例外狀況的錯誤訊息傳回至配接器。 您可以使用任何值的訊息動作、 錯誤程式碼，以及原因。  
  
        ```  
        MessageFault fault = MessageFault.CreateFault(new FaultCode("ProcFault"), "Processing Error");  
        Message respMessage = Message.CreateMessage(MessageVersion.Default, fault, String.Empty);  
        rc.Reply(respMessage);  
        ```  
  
8.  您已送出訊息之後，請關閉要求內容。  
  
    ```  
    rc.Close();  
    ```  
  
9. 當您完成處理要求，請關閉通道。  
  
    ```  
    channel.Close()  
    ```  
  
    > [!IMPORTANT]
    >  處理作業完成之後，您必須關閉通道。 若要關閉通道的失敗可能會影響您的程式碼的行為。  
  
10. 當您完成從 SAP 系統接收作業時，請關閉接聽程式。  
  
    ```  
    listener.Close()  
    ```  
  
    > [!IMPORTANT]
    >  當您完成時，您必須明確地關閉接聽程式使用它;否則，您的程式可能無法正常運作。 關閉接聽程式不會關閉建立使用接聽程式通道。 您必須明確地關閉每一個色頻建立使用接聽程式。  
  
### <a name="example"></a>範例  
 下列範例接收 RFC，SAP 系統從 Z_RFC_MKD_DIV。 兩數相除這個 RFC。 在此範例實作會使用**InboundActionCollection**來接收訊息時，Z_RFC_MKD_DIV 作業和執行下列篩選：  
  
-   如果除數為非零，它會寫入主控台中的除法運算的結果的連線，並傳回至 SAP 系統。  
  
-   如果除數為零，它會將產生的例外狀況訊息寫入主控台的連線，並傳回錯誤至 SAP 系統。  
  
-   如果 SAP 系統傳送的任何其他作業，它會將訊息寫入主控台。 在此情況下，配接器本身會傳回錯誤至 SAP 系統。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.Runtime.Serialization;  
using System.Xml;  
using System.IO;  
  
// Add WCF, Adapter LOB SDK, and SAP Adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Add this namespace to use Channel Model   
using System.ServiceModel.Channels;  
  
// Include this namespace for Adapter LOB SDK and SAP exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// This sample demonstrates using the adapter as an rfc server over a channel.  
// The sample implements an RFC, Z_RFC_MKD_DIV that divides two numbers and returns the result  
// 1)  A SAPBinding instance is created and configured (AcceptCredentialsInUri is set true)  
// 2)  A binding parameter collection is created with an InboundAction collection that specifies  
//     target RFC (Z_RFC_MKD_DIV) so that only messages with this action will be received by the  
//     listener (and channel).  
// 3)  An <IReplyChannel> listener is created from the binding and binding parameter collection  
// 4)  A channel is created and opened to receive a request  
// 6)  When Z_RFC_MKD_DIV is received the two parameters are divided and the parameters and result  
//     are written to the console, then the result is returned to the adapter by using a template  
//     message.  
// 7)  If a divide by 0 occurs the exception message is written to the console and a  
//     fault is returned to the SAP system  
// 8)  If any other operation is received an error message is written to the console and the adapter  
///    returns a fault to the SAP system  
// 9)  IMPORTANT you must close the channel and listener to deregister them from the SAP Program ID.  
namespace SapRfcServerCM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Variables to hold the listener and channel  
            IChannelListener<IReplyChannel> listener = null;  
            IReplyChannel channel = null;  
  
            Console.WriteLine("Sample started");  
            Console.WriteLine("Initializing and creating channel listener -- please wait");  
            try  
            {  
  
                // The connection Uri must specify listener parameters (or an R-type destination in saprfc.ini)  
                // and also credentials.  
                Uri listeneraddress =  
                    new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGATEWAY&ListenerGwHost=YourSAPHost&ListenerProgramId=SAPAdapter");  
  
                // Create a binding -- set AcceptCredentialsInUri true  
                SAPBinding binding = new SAPBinding();  
                binding.AcceptCredentialsInUri = true;  
  
                // Create a binding parameter collection with a list of SOAP actions to listen on  
                // in this case: http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV  
                // This ensures that only these actions are received on the channel.  
                InboundActionCollection actions = new InboundActionCollection(listeneraddress);  
                actions.Add("http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV");  
                BindingParameterCollection bpcol = new BindingParameterCollection();  
                bpcol.Add(actions);  
  
                // Pass the Uri and the binding parameter collection (to specify the Z_RFC_MKD_DIV action)  
                listener = binding.BuildChannelListener<IReplyChannel>(listeneraddress, bpcol);  
  
                Console.WriteLine("Opening listener");  
                // Open the listener  
                listener.Open();  
  
                // Get an IReplyChannel  
                channel = listener.AcceptChannel();  
  
                Console.WriteLine("Opening channel");  
                // Open the channel  
                channel.Open();  
  
                Console.WriteLine("\nReady to receive Z_RFC_MKD_DIV RFC");  
  
                try  
                {  
                    // Get the message from the channel  
                    RequestContext rc = channel.ReceiveRequest();  
  
                    // Get the request message sent by SAP  
                    Message reqMessage = rc.RequestMessage;  
  
                    // get the message body  
                    XmlReader reader = reqMessage.GetReaderAtBodyContents();  
  
                    reader.ReadStartElement("Z_RFC_MKD_DIV");  
                    reader.ReadElementString("DEST");  
                    int x_in = int.Parse(reader.ReadElementString("X"));  
                    int y_in = int.Parse(reader.ReadElementString("Y"));  
                    reader.ReadEndElement();  
  
                    Console.WriteLine("\nRfc Received");  
                    Console.WriteLine("X =\t\t" + x_in);  
                    Console.WriteLine("Y =\t\t" + y_in);  
  
                    Message messageOut = null;  
  
                    try   
                    {  
                        int result_out = x_in/y_in;  
  
                        Console.WriteLine("RESULT =\t" + result_out.ToString());  
  
                        string out_xml = "<Z_RFC_MKD_DIVResponse xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"><RESULT>" + result_out + "</RESULT></Z_RFC_MKD_DIVResponse>";  
                        StringReader sr = new StringReader(out_xml);  
                        reader = XmlReader.Create(sr);  
  
                        // create a response message  
                        // be sure to specify the response action  
                        messageOut = Message.CreateMessage(MessageVersion.Default, reqMessage.Headers.Action + "/response", reader);  
  
                    }  
                    catch (DivideByZeroException ex)  
                    {  
                        Console.WriteLine();  
                        Console.WriteLine(ex.Message + " Returning fault to SAP");  
  
                        // Create a message that contains a fault  
                        // The fault code and message action can be any value  
  
                        messageOut = Message.CreateMessage(MessageVersion.Default, new FaultCode("Fault"), ex.Message, string.Empty);  
                    }  
  
                    // Send the reply  
                    rc.Reply(messageOut);  
  
                    // Close the request context  
                    rc.Close();  
  
                }  
                catch (AdapterException aex)  
                {  
                    // Will get here if the message received was not in the InboundActionCollection  
                    Console.WriteLine();  
                    Console.WriteLine(aex.Message);  
                }  
  
                // Wait for a key to exit  
                Console.WriteLine("\nHit <RETURN> to end");  
                Console.ReadLine();  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the SAP system");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the SAP system");  
                Console.WriteLine(tex.InnerException.Message);  
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
                // IMPORTANT: close the channel and listener to stop listening on the Program ID  
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
[使用 WCF 通道模型開發應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)