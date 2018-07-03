---
title: 使用 WCF 通道模型的 SAP 系統上叫用作業 |Microsoft Docs
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
ms.openlocfilehash: 408d2ce053a30a4692b6e17a73087b13c648ab2a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997335"
---
# <a name="invoke-operations-on-the-sap-system-using-the-wcf-channel-model"></a><span data-ttu-id="f35a0-102">使用 WCF 通道模型的 SAP 系統上叫用作業</span><span class="sxs-lookup"><span data-stu-id="f35a0-102">Invoke Operations on the SAP System Using the WCF Channel Model</span></span>
<span data-ttu-id="f35a0-103">您在上叫用作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]利用**IRequestChannel**或**IOutputChannel**通道將訊息傳送至配接器的圖案。</span><span class="sxs-lookup"><span data-stu-id="f35a0-103">You invoke operations on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by using an **IRequestChannel** or **IOutputChannel** channel shape to send messages to the adapter.</span></span> <span data-ttu-id="f35a0-104">基本的模式是使用繫結建立通道處理站所需的通道形狀 (**SAPBinding**) 和建立的連線 URI 的端點。</span><span class="sxs-lookup"><span data-stu-id="f35a0-104">The basic pattern is to create a channel factory for the required channel shape by using a binding (**SAPBinding**) and an endpoint created from a connection URI.</span></span> <span data-ttu-id="f35a0-105">接著，您建立**訊息**表示 SOAP 訊息，以符合您目標的作業的訊息結構描述執行個體。</span><span class="sxs-lookup"><span data-stu-id="f35a0-105">You then create a **Message** instance that represents a SOAP message that conforms to the message schema for your target operation.</span></span> <span data-ttu-id="f35a0-106">您可以接著將傳送這**訊息**到[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用從通道處理站建立通道。</span><span class="sxs-lookup"><span data-stu-id="f35a0-106">You can then send this **Message** to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by using a channel created from the channel factory.</span></span> <span data-ttu-id="f35a0-107">如果您使用**IRequestChannel**，您會收到回應。</span><span class="sxs-lookup"><span data-stu-id="f35a0-107">If you are using an **IRequestChannel**, you receive a response.</span></span> <span data-ttu-id="f35a0-108">如果發生問題，執行 SAP 系統上執行的作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會擲回**Microsoft.ServiceModel.Channels.Common.TargetSystemException**。</span><span class="sxs-lookup"><span data-stu-id="f35a0-108">If there is a problem executing the operation on the SAP system, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] throws a **Microsoft.ServiceModel.Channels.Common.TargetSystemException**.</span></span>  
  
 <span data-ttu-id="f35a0-109">如需如何傳送作業使用的概觀**IRequestChannel**在 WCF 中，請參閱[用戶端通道層級程式設計](https://msdn.microsoft.com/library/ms788970.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f35a0-109">For an overview of how to send operations using an **IRequestChannel** in WCF, see [Client Channel-Level Programming](https://msdn.microsoft.com/library/ms788970.aspx).</span></span>  
  
 <span data-ttu-id="f35a0-110">本主題中的各節提供的資訊可協助您在上叫用作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="f35a0-110">The sections in this topic provide information to help you invoke operations on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] using the WCF channel model.</span></span>  
  
## <a name="supporting-bapi-transactions-in-the-wcf-channel-model"></a><span data-ttu-id="f35a0-111">支援的 WCF 通道模型中的 BAPI 異動</span><span class="sxs-lookup"><span data-stu-id="f35a0-111">Supporting BAPI Transactions in the WCF Channel Model</span></span>  
 <span data-ttu-id="f35a0-112">會叫用使用相同的 SAP 連線的所有 Bapi 都位於 SAP 系統的相同邏輯單元的工作 (LUW)-或--交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="f35a0-112">All BAPIs that are invoked using the same SAP connection are part of the same Logical Unit of Work (LUW) -- or transaction -- on the SAP system.</span></span> <span data-ttu-id="f35a0-113">每個 WCF 通道代表 SAP 系統的唯一連接。</span><span class="sxs-lookup"><span data-stu-id="f35a0-113">Each WCF channel represents a unique connection to the SAP system.</span></span> <span data-ttu-id="f35a0-114">若要支援 BAPI 交易使用 WCF 通道模型：</span><span class="sxs-lookup"><span data-stu-id="f35a0-114">To support BAPI transactions using the WCF channel model:</span></span>  
  
- <span data-ttu-id="f35a0-115">請確定每個 BAPI 中 LUW （交易） 會透過相同的通道傳送。</span><span class="sxs-lookup"><span data-stu-id="f35a0-115">Ensure that every BAPI in an LUW (transaction) is sent over the same channel.</span></span> <span data-ttu-id="f35a0-116">這包括 BAPI_TRANSACTION 認可或 BAPI_TRANSACTION_ROLLBACK 作業。</span><span class="sxs-lookup"><span data-stu-id="f35a0-116">This includes the BAPI_TRANSACTION COMMIT or the BAPI_TRANSACTION_ROLLBACK operations.</span></span>  
  
- <span data-ttu-id="f35a0-117">請確定您關閉之前叫用在通道上的下一個 BAPI BAPI 收到任何回應訊息。</span><span class="sxs-lookup"><span data-stu-id="f35a0-117">Ensure that you close any response message received for a BAPI before you invoke the next BAPI on the channel.</span></span> <span data-ttu-id="f35a0-118">（您應該這麼做的每一作業; 但就特別重要的 Bapi）。</span><span class="sxs-lookup"><span data-stu-id="f35a0-118">(You should do this for every operation; but it is especially important for BAPIs.)</span></span>  
  
  <span data-ttu-id="f35a0-119">如需有關 BAPI 交易的詳細資訊，請參閱[對 SAP 中的 Bapi 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="f35a0-119">For more information about BAPI transactions, see [Operations on BAPIs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span></span>  
  
## <a name="streaming-flat-file-idocs-to-the-sap-adapter"></a><span data-ttu-id="f35a0-120">串流一般檔案 Idoc 至 SAP 配接器</span><span class="sxs-lookup"><span data-stu-id="f35a0-120">Streaming Flat File IDOCs to the SAP Adapter</span></span>  
 <span data-ttu-id="f35a0-121">您可以使用 SendIdoc 作業來傳送一般檔案 （字串） IDOC，配接器。</span><span class="sxs-lookup"><span data-stu-id="f35a0-121">You use the SendIdoc operation to send a flat file (string) IDOC to the adapter.</span></span> <span data-ttu-id="f35a0-122">IDOC 資料是以這項作業中的單一節點下的字串表示。</span><span class="sxs-lookup"><span data-stu-id="f35a0-122">The IDOC data is represented as a string under a single node in this operation.</span></span> <span data-ttu-id="f35a0-123">基於這個理由，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援節點值的資料流處理的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="f35a0-123">For this reason, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports node-value streaming on the request message.</span></span> <span data-ttu-id="f35a0-124">若要執行串流處理的節點值，您必須建立 SendIdoc 作業的要求訊息，利用**System.ServiceModel.Channels.BodyWriter**能夠串流 IDOC 的資料。</span><span class="sxs-lookup"><span data-stu-id="f35a0-124">To perform node-value streaming, you must create the request message for the SendIdoc operation by using a **System.ServiceModel.Channels.BodyWriter** that is capable of streaming the IDOC data.</span></span> <span data-ttu-id="f35a0-125">如需如何執行這項操作的資訊，請參閱[串流中使用 WCF 通道模型的 SAP 的一般檔案 Idoc](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="f35a0-125">For information about how to do this, see [Streaming Flat-File IDOCs in SAP using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="how-do-i-invoke-an-operation-by-using-a-channel"></a><span data-ttu-id="f35a0-126">如何使用通道叫用的作業？</span><span class="sxs-lookup"><span data-stu-id="f35a0-126">How Do I Invoke an Operation by Using a Channel?</span></span>  
 <span data-ttu-id="f35a0-127">使用叫用作業**IRequestChannel**，執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="f35a0-127">To invoke an operation by using an **IRequestChannel**, perform the following steps.</span></span>  
  
#### <a name="how-to-invoke-an-operation-by-using-an-instance-of-irequestchannel"></a><span data-ttu-id="f35a0-128">如何使用 IRequestChannel 的執行個體叫用作業</span><span class="sxs-lookup"><span data-stu-id="f35a0-128">How to invoke an operation by using an instance of IRequestChannel</span></span>  
  
1. <span data-ttu-id="f35a0-129">建置通道處理站 (**ChannelFactory\<IRequestChannel\>**)。</span><span class="sxs-lookup"><span data-stu-id="f35a0-129">Build a channel factory (**ChannelFactory\<IRequestChannel\>**).</span></span> <span data-ttu-id="f35a0-130">若要這樣做，您必須指定繫結 (**SAPBinding**) 和端點位址。</span><span class="sxs-lookup"><span data-stu-id="f35a0-130">To do this, you must specify a binding (**SAPBinding**) and an endpoint address.</span></span> <span data-ttu-id="f35a0-131">以命令方式在您的程式碼或是宣告式組態中，您可以指定繫結與端點位址。</span><span class="sxs-lookup"><span data-stu-id="f35a0-131">You can specify the binding and endpoint address either imperatively in your code or declaratively in configuration.</span></span> <span data-ttu-id="f35a0-132">您應該設定屬性的作業所需先開啟之處理站會傳送任何繫結。</span><span class="sxs-lookup"><span data-stu-id="f35a0-132">You should set any binding properties required for the operations that you will send before you open the factory.</span></span> <span data-ttu-id="f35a0-133">如需如何在組態中指定的繫結和端點位址的詳細資訊，請參閱[建立通道，使用 SAP](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="f35a0-133">For more information about how to specify the binding and endpoint address in configuration, see [Create a channel using SAP](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md).</span></span>  
  
   ```  
   // Create a binding  
   SAPBinding binding = new SAPBinding();  
   // Create an endpoint address by using the connection URI  
   EndpointAddress endpointAddress = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
   // Create the channel factory  
   ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
   ```  
  
2. <span data-ttu-id="f35a0-134">使用設定的使用者名稱密碼認證之通道處理站**ClientCredentials**屬性。</span><span class="sxs-lookup"><span data-stu-id="f35a0-134">Set the user name password credentials for the channel factory by using the **ClientCredentials** property.</span></span>  
  
   ```  
   factory.Credentials.UserName.UserName = "YourUserName";  
   factory.Credentials.UserName.Password = "YourPassword";  
   ```  
  
3. <span data-ttu-id="f35a0-135">開啟通道處理站。</span><span class="sxs-lookup"><span data-stu-id="f35a0-135">Open the channel factory.</span></span>  
  
   ```  
   factory.Open();  
   ```  
  
4. <span data-ttu-id="f35a0-136">從 factory 取得的通道，然後開啟它。</span><span class="sxs-lookup"><span data-stu-id="f35a0-136">Get a channel from the factory and open it.</span></span>  
  
   ```  
   IRequestChannel channel = factory.CreateChannel();  
   channel.Open();  
   ```  
  
5. <span data-ttu-id="f35a0-137">建立**訊息**目標作業的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f35a0-137">Create a **Message** instance for the target operation.</span></span> <span data-ttu-id="f35a0-138">請務必確認已指定目標作業的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="f35a0-138">Be sure that the message action for the target operation is specified.</span></span> <span data-ttu-id="f35a0-139">在此範例中，藉由傳遞訊息內文**XmlReader**的字串。</span><span class="sxs-lookup"><span data-stu-id="f35a0-139">In this example, the message body is passed by creating an **XmlReader** over a string.</span></span> <span data-ttu-id="f35a0-140">目標作業叫用 SD_RFC_CUSTOMER_GET RFC，SAP 系統上。</span><span class="sxs-lookup"><span data-stu-id="f35a0-140">The target operation invokes the SD_RFC_CUSTOMER_GET RFC on an SAP system.</span></span>  
  
   ```  
   string inputXml = "\<SD_RFC_CUSTOMER_GET xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> <KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>";  
  
   //create an XML reader from the input XML  
   XmlReader reader = XmlReader.Create(new MemoryStream(Encoding.Default.GetBytes(inputXml)));  
  
   //create a WCF message from our XML reader  
   Message inputMessge = Message.CreateMessage(MessageVersion.Soap11, "http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET", reader);  
   ```  
  
6. <span data-ttu-id="f35a0-141">叫用**要求**方法來傳送訊息給在通道上的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]和接收回覆。</span><span class="sxs-lookup"><span data-stu-id="f35a0-141">Invoke the **Request** method on the channel to send the message to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] and receive the reply.</span></span> <span data-ttu-id="f35a0-142">SAP 系統遇到的例外狀況，如果配接器會擲回**TargetSystemException**。</span><span class="sxs-lookup"><span data-stu-id="f35a0-142">If the SAP system encounters an exception, the adapter throws a **TargetSystemException**.</span></span> <span data-ttu-id="f35a0-143">（其他例外狀況是可能的非 SAP 例外狀況）。您可以取得從 SAP 錯誤的描述**InnerException.Message**屬性**TargetSystemException**。</span><span class="sxs-lookup"><span data-stu-id="f35a0-143">(Other exceptions are possible for non SAP exceptions.) You can get a description of the SAP error from the **InnerException.Message** property of the **TargetSystemException**.</span></span>  
  
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
  
7. <span data-ttu-id="f35a0-144">處理回應。</span><span class="sxs-lookup"><span data-stu-id="f35a0-144">Process the response.</span></span> <span data-ttu-id="f35a0-145">在此範例中， **GetReaderAtBodyContents**来取得訊息內文的回應訊息上呼叫。</span><span class="sxs-lookup"><span data-stu-id="f35a0-145">In this example, **GetReaderAtBodyContents** is called on the response message to get the message body.</span></span>  
  
   ```  
   XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
   ```  
  
8. <span data-ttu-id="f35a0-146">當您完成處理回應訊息時，關閉讀取器和訊息。</span><span class="sxs-lookup"><span data-stu-id="f35a0-146">When you are done processing the response message, close the reader and the message.</span></span>  
  
   ```  
   readerOut.Close();  
   messageOut.Close();  
   ```  
  
9. <span data-ttu-id="f35a0-147">當您完成使用通道和通道處理站中，關閉它們。</span><span class="sxs-lookup"><span data-stu-id="f35a0-147">When you are done using the channel and the channel factory, close them.</span></span> <span data-ttu-id="f35a0-148">關閉處理站，將會關閉所有使用它所建立的通道。</span><span class="sxs-lookup"><span data-stu-id="f35a0-148">Closing the factory will close all channels that were created with it.</span></span>  
  
    ```  
    channel.Close()  
    factory.Close();  
    ```  
  
10. 
  
    <span data-ttu-id="f35a0-149">請遵循相同的步驟，以傳送訊息，使用**IOutputChannel**圖形除外：</span><span class="sxs-lookup"><span data-stu-id="f35a0-149">You follow the same steps to send a message using the **IOutputChannel** shape except:</span></span>  
  
-   <span data-ttu-id="f35a0-150">您建立**ChannelFactory\<IOutputChannel\>** 在步驟 1。</span><span class="sxs-lookup"><span data-stu-id="f35a0-150">You create a **ChannelFactory\<IOutputChannel\>** in step 1.</span></span>  
  
-   <span data-ttu-id="f35a0-151">您呼叫**傳送**步驟 6 中的通道上的方法。</span><span class="sxs-lookup"><span data-stu-id="f35a0-151">You call the **Send** method on the channel in step 6.</span></span> <span data-ttu-id="f35a0-152">`channel.Send(messageIn);`。</span><span class="sxs-lookup"><span data-stu-id="f35a0-152">`channel.Send(messageIn);`.</span></span>  
  
-   <span data-ttu-id="f35a0-153">不沒有傳回任何回應訊息**IOutputChannel**。</span><span class="sxs-lookup"><span data-stu-id="f35a0-153">There is no response message returned for an **IOutputChannel**.</span></span>  
  
### <a name="example"></a><span data-ttu-id="f35a0-154">範例</span><span class="sxs-lookup"><span data-stu-id="f35a0-154">Example</span></span>  
 <span data-ttu-id="f35a0-155">下列範例示範如何使用叫用 RFC **IRequestChannel**通道。</span><span class="sxs-lookup"><span data-stu-id="f35a0-155">The following example shows how to invoke an RFC by using an **IRequestChannel** channel.</span></span> <span data-ttu-id="f35a0-156">此範例會叫用 SD_RFC_CUSTOMER_GET RFC，以取得一份客戶名稱開頭為"AB"。</span><span class="sxs-lookup"><span data-stu-id="f35a0-156">This example invokes the SD_RFC_CUSTOMER_GET RFC to get a list of customers whose names start with "AB".</span></span> <span data-ttu-id="f35a0-157">回應訊息因使用而消耗**XmlReader**並傳回每個客戶的名稱與客戶編號會寫入至主控台。</span><span class="sxs-lookup"><span data-stu-id="f35a0-157">The response message is consumed by using an **XmlReader** and the customer number and name of each customer returned is written to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f35a0-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f35a0-158">See Also</span></span>  
[<span data-ttu-id="f35a0-159">使用 WCF 通道模型開發應用程式</span><span class="sxs-lookup"><span data-stu-id="f35a0-159">Develop applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)