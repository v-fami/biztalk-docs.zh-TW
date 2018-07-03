---
title: SQL 配接器的 WCF 通道模型概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5e5f77c-c922-4039-92c7-38d2b7638459
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 819143bd7e65c9cea91232e2529b20cfab2c049d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003167"
---
# <a name="overview-of-the-wcf-channel-model-with-the-sql-adapter"></a><span data-ttu-id="8c9a9-102">SQL 配接器的 WCF 通道模型概觀</span><span class="sxs-lookup"><span data-stu-id="8c9a9-102">Overview of the WCF channel model with the SQL adapter</span></span>
<span data-ttu-id="8c9a9-103">在叫用作業[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]，您的程式碼做為 WCF 用戶端，並將傳出作業傳送至配接器。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-103">To invoke operations on the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)], your code acts as a WCF client and sends outbound operations to the adapter.</span></span> <span data-ttu-id="8c9a9-104">在 WCF 通道模型中，您的程式碼會叫用介面卡上的作業，透過通道傳送要求訊息。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-104">In the WCF channel model, your code invokes operations on the adapter by sending a request message over a channel.</span></span>  
  
 <span data-ttu-id="8c9a9-105">若要接收以輪詢為基礎的資料變更訊息使用配接器，您的程式碼做為 WCF 服務並接收傳入**輪詢**， **TypedPolling**，或**通知**從配接器的作業。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-105">To receive polling-based data-changed messages using the adapter, your code acts as a WCF service and receives the inbound **Polling**, **TypedPolling**, or **Notification** operation from the adapter.</span></span> <span data-ttu-id="8c9a9-106">換句話說，您的程式碼會透過通道從配接器接收 這些作業的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-106">In other words, your code receives a request message for these operations from the adapter over a channel.</span></span>  
  
 <span data-ttu-id="8c9a9-107">在本節中的主題提供使用的概觀[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-107">The topics in this section provide an overview of using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with the WCF channel model.</span></span>  
  
## <a name="wcf-channel-model-overview"></a><span data-ttu-id="8c9a9-108">WCF 通道模型概觀</span><span class="sxs-lookup"><span data-stu-id="8c9a9-108">WCF Channel Model Overview</span></span>  
 <span data-ttu-id="8c9a9-109">用戶端和服務交換的 SOAP 訊息來進行通訊。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-109">Clients and services communicate by exchanging SOAP messages.</span></span> <span data-ttu-id="8c9a9-110">WCF 通道模型是低層級的抽象概念，此訊息交換。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-110">The WCF channel model is a low-level abstraction of this message exchange.</span></span> <span data-ttu-id="8c9a9-111">它提供介面和類型，可讓您傳送和接收訊息所使用的是稱為通道堆疊的多層式通訊協定堆疊。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-111">It provides interfaces and types that enable you to send and receive messages by using a layered protocol stack called a channel stack.</span></span> <span data-ttu-id="8c9a9-112">堆疊的每個圖層由通道所組成，每一個色頻建立從 WCF 繫結。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-112">Each layer of the stack is composed of a channel, and each channel is created from a WCF binding.</span></span> <span data-ttu-id="8c9a9-113">最低層級是傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-113">At the lowest layer is the transport channel.</span></span> <span data-ttu-id="8c9a9-114">傳輸通道會實作服務和用戶端之間的基礎傳輸機制，並呈現較高的層級 （和最終取用的應用程式） 每個訊息**System.ServiceModel.Message**。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-114">The transport channel implements the underlying transport mechanism between a service and a client and presents each message to the higher layers (and ultimately the consuming application) as a **System.ServiceModel.Message**.</span></span> <span data-ttu-id="8c9a9-115">WCF**訊息**類別是抽象的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-115">The WCF **Message** class is an abstraction of a SOAP message.</span></span> <span data-ttu-id="8c9a9-116">WCF 提供數個通道介面，稱為通道形狀，模型的基本 SOAP 訊息交換模式，例如要求-回覆或單向。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-116">WCF provides several channel interfaces, called channel shapes, that model the basic SOAP message exchange patterns, such as request-reply or one-way.</span></span> <span data-ttu-id="8c9a9-117">WCF 傳輸繫結提供實作的其中一個或多個更新版本階層的通道形狀可用來傳送和接收訊息。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-117">A WCF transport binding provides an implementation of one or more channel shapes that higher layers can use to send and receive messages.</span></span> <span data-ttu-id="8c9a9-118">如需有關 WCF 通道模型的詳細資訊，請參閱 <<c0> [ 通道模型概觀](https://msdn.microsoft.com/library/ms729840.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-118">For more information about the WCF channel model, see [Channel Model Overview](https://msdn.microsoft.com/library/ms729840.aspx).</span></span>
  
 <span data-ttu-id="8c9a9-119">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]是 WCF 自訂傳輸繫結會公開為 WCF 服務的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-119">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is a WCF custom transport binding that exposes a SQL Server database as a WCF service.</span></span>  
  
## <a name="supported-channel-shapes-for-the-sql-server-adapter"></a><span data-ttu-id="8c9a9-120">SQL Server 配接器支援通道形狀</span><span class="sxs-lookup"><span data-stu-id="8c9a9-120">Supported Channel Shapes for the SQL Server Adapter</span></span>  
 <span data-ttu-id="8c9a9-121">配接器實作下列的 WCF 通道形狀：</span><span class="sxs-lookup"><span data-stu-id="8c9a9-121">The adapter implements the following WCF channel shapes:</span></span>  
  
- <span data-ttu-id="8c9a9-122">**IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**)。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-122">**IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**).</span></span> <span data-ttu-id="8c9a9-123">**IRequestChannel**介面會實作要求-回覆訊息交換的用戶端。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-123">The **IRequestChannel** interface implements the client side of a request-reply message exchange.</span></span> <span data-ttu-id="8c9a9-124">您可以使用**IRequestChannel**若要執行您要使用回應的作業，例如若要執行 SELECT 查詢的資料表上。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-124">You can use an **IRequestChannel** to perform operations for which you want to consume a response, for example to perform a SELECT query on a table.</span></span>  
  
- <span data-ttu-id="8c9a9-125">**IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**)。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-125">**IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**).</span></span> <span data-ttu-id="8c9a9-126">此圖形會實作單向訊息交換的用戶端。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-126">This shape implements the client side of a one-way message exchange.</span></span> <span data-ttu-id="8c9a9-127">您可以使用**IOutputChannel**叫用作業，您不需要使用的回應，例如若要呼叫沒有傳回參數的程序。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-127">You can use an **IOutputChannel** to invoke an operation for which you do not need to consume a response, for example to call a procedure that has no return parameters.</span></span>  
  
  > [!IMPORTANT]
  >  <span data-ttu-id="8c9a9-128">所有基礎呼叫，配接器以 SQL Server 用戶端都是同步的。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-128">All underlying calls by the adapter to the SQL Server client are synchronous.</span></span> <span data-ttu-id="8c9a9-129">這包括 SQL Server 用戶端的呼叫是透過叫用作業的結果**IOutputChannel**。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-129">This includes calls to the SQL Server client that are the result of operations invoked over an **IOutputChannel**.</span></span> <span data-ttu-id="8c9a9-130">當您使用**IOutputChannel**，配接器會捨棄從 SQL Server 用戶端收到的回應。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-130">When you use an **IOutputChannel**, the adapter discards the response received from the SQL Server client.</span></span>  
  
- <span data-ttu-id="8c9a9-131">**IInputChannel** (**System.ServiceModel.Channels.IInputChannel**)。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-131">**IInputChannel** (**System.ServiceModel.Channels.IInputChannel**).</span></span> <span data-ttu-id="8c9a9-132">此圖形會實作服務端的單向訊息交換。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-132">This shape implements the service side of a one-way message exchange.</span></span> <span data-ttu-id="8c9a9-133">您使用**IInputChannel**接收訊息的輸入操作，例如**輪詢**或是**通知**，從配接器。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-133">You use an **IInputChannel** to receive messages for inbound operations, such as **Polling** or **Notification**, from the adapter.</span></span>  
  
  <span data-ttu-id="8c9a9-134">讓任何 WCF 繫結[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]用以提供應用程式程式碼的通道處理站模式。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-134">Like any WCF binding, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses a factory pattern to provide channels to application code.</span></span> <span data-ttu-id="8c9a9-135">您使用**Microsoft.Adapters.SQLBinding**建立的執行個體的物件：</span><span class="sxs-lookup"><span data-stu-id="8c9a9-135">You use a **Microsoft.Adapters.SQLBinding** object to create instances of:</span></span>  
  
- <span data-ttu-id="8c9a9-136">**System.ServiceModel.ChannelFactory\<IRequestChannel\>** 提供**IRequestChannel**通道可用來叫用的介面卡上的要求-回應作業。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-136">**System.ServiceModel.ChannelFactory\<IRequestChannel\>** to provide **IRequestChannel** channels you can use to invoke request-response operations on the adapter.</span></span>  
  
- <span data-ttu-id="8c9a9-137">**System.ServiceModel.ChannelFactory\<IOutputChannel\>** 提供**IOutputChannel**通道可用來叫用的介面卡上的單向作業。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-137">**System.ServiceModel.ChannelFactory\<IOutputChannel\>** to provide **IOutputChannel** channels you can use to invoke one-way operations on the adapter.</span></span>  
  
- <span data-ttu-id="8c9a9-138">**System.ServiceModel.IChannelListener\<IInputChannel\>** 提供**IInputChannel**通道接收訊息的輸入操作，例如，您可以使用**輪詢**或是**通知**，從配接器。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-138">**System.ServiceModel.IChannelListener\<IInputChannel\>** to provide **IInputChannel** channels you can use to receive messages for inbound operations, such as **Polling** or **Notification**, from the adapter.</span></span>  
  
### <a name="creating-messages-for-the-sql-server-database-adapter-in-the-wcf-channel-model"></a><span data-ttu-id="8c9a9-139">正在建立的 WCF 通道模型中的 SQL Server 資料庫配接器訊息</span><span class="sxs-lookup"><span data-stu-id="8c9a9-139">Creating Messages for the SQL Server Database Adapter in the WCF Channel Model</span></span>  
 <span data-ttu-id="8c9a9-140">在 WCF **System.ServiceModel.Channels.Message**類別提供在記憶體中表示 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-140">In WCF the **System.ServiceModel.Channels.Message** class provides an in memory representation of a SOAP message.</span></span> <span data-ttu-id="8c9a9-141">您建立**訊息**執行個體，藉由叫用靜態**Message.Create**方法。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-141">You create a **Message** instance by invoking the static **Message.Create** method.</span></span>  
  
 <span data-ttu-id="8c9a9-142">有兩個重要的部分，您必須指定當您建立的 SOAP 訊息**訊息**執行個體來傳送至[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-142">There are two important parts to the SOAP message that you must specify when you create a **Message** instance to send to the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
- <span data-ttu-id="8c9a9-143">訊息的動作是屬於 SOAP 訊息標頭的字串。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-143">The message action is a string that is part of the SOAP message header.</span></span> <span data-ttu-id="8c9a9-144">[訊息] 動作會識別應該在資料庫叫用的作業。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-144">The message action identifies the operation that should be invoked on the database.</span></span> <span data-ttu-id="8c9a9-145">下面顯示來叫用 [員工] 資料表的 Select 作業指定的訊息動作： `TableOp/Select/dbo/Employee`。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-145">The following shows the message action specified to invoke the Select operation on the Employee table: `TableOp/Select/dbo/Employee`.</span></span>  
  
- <span data-ttu-id="8c9a9-146">訊息內文包含作業的參數資料。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-146">The message body contains the parameter data for the operation.</span></span> <span data-ttu-id="8c9a9-147">訊息內文由語式正確對應至所預期的訊息結構描述的 XML 組成[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]要求的作業。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-147">The message body is composed of well-formed XML that corresponds to the message schema expected by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] for the requested operation.</span></span> <span data-ttu-id="8c9a9-148">下列的訊息本文指定 [員工] 資料表上的選取作業 (選取 \* 從員工 WHERE Employee_ID = 10001)。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-148">The following message body specifies a Select operation on the Employee table (SELECT \* FROM Employee WHERE Employee_ID=10001).</span></span>  
  
  ```  
  <Select xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
    <Columns>*</Columns>  
    <Query>where Employee_ID=10001</Query>  
  </Select>  
  
  ```  
  
  <span data-ttu-id="8c9a9-149">如需[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]訊息結構描述和訊息作業的動作，請參閱[訊息和訊息結構描述，BizTalk adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-149">For information about the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] message schemas and message actions for operations, see [Messages and Message Schemas for BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).</span></span>  
  
  <span data-ttu-id="8c9a9-150">這**建立**方法多載，並提供許多不同的選項，來提供訊息內文。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-150">This **Create** method is overloaded and offers many different options for providing the message body.</span></span> <span data-ttu-id="8c9a9-151">下列程式碼示範如何建立**訊息**使用的執行個體**XmlReader**提供訊息內文。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-151">The following code shows how to create a **Message** instance by using an **XmlReader** to supply the message body.</span></span> <span data-ttu-id="8c9a9-152">在此程式碼，是從檔案讀取訊息主體。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-152">In this code, the message body is read from a file.</span></span>  
  
```  
XmlReader readerIn = XmlReader.Create("SelectInput.xml");  
Message messageIn = Message.CreateMessage(MessageVersion.Default,  
    "TableOp/Select/dbo/Employee",  
    readerIn);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="8c9a9-153">您必須提供中的訊息動作您**訊息**執行個體。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-153">You must provide a message action in your **Message** instance.</span></span> <span data-ttu-id="8c9a9-154">這通常是何時**訊息**建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="8c9a9-154">This is typically done when the **Message** instance is created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c9a9-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c9a9-155">See Also</span></span>  
[<span data-ttu-id="8c9a9-156">使用 WCF 通道模型開發應用程式</span><span class="sxs-lookup"><span data-stu-id="8c9a9-156">Develop applications using the WCF Channel model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)