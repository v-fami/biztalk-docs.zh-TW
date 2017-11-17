---
title: "使用 WCF 通道模型的 Oracle 資料庫中執行 SQLEXECUTE 操作 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running a SQLEXECUTE statement, using a channel
- how to, run a SQLEXECUTE statement by using a channel
- WCF channel model, running a SQLEXECUTE statement
ms.assetid: e1af11ef-3f44-4726-99ca-d6961d79e651
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c7928affeafd40197401fa75d44658e0e975507
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model"></a><span data-ttu-id="6d155-102">使用 WCF 通道模型的 Oracle 資料庫中執行 SQLEXECUTE 操作</span><span class="sxs-lookup"><span data-stu-id="6d155-102">Run a SQLEXECUTE Operation in Oracle Database using the WCF Channel Model</span></span>
<span data-ttu-id="6d155-103">本節說明如何透過通道執行 SQLEXECUTE 操作的 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="6d155-103">This section shows how to perform a SQLEXECUTE operation on an Oracle database over a channel.</span></span> <span data-ttu-id="6d155-104">您必須在 SOAP 訊息指定訊息和訊息動作。</span><span class="sxs-lookup"><span data-stu-id="6d155-104">You must specify both a message and a message action on the SOAP message.</span></span> <span data-ttu-id="6d155-105">如需 SQLEXECUTE 操作的詳細資訊，請參閱[在 Oracle 資料庫中使用 WCF 服務模型執行 SQLEXECUTE 操作](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="6d155-105">For more information about the SQLEXECUTE operation, see [Run SQLEXECUTE operation in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
## <a name="the-sqlexecute-message"></a><span data-ttu-id="6d155-106">SQLEXECUTE 訊息</span><span class="sxs-lookup"><span data-stu-id="6d155-106">The SQLEXECUTE Message</span></span>  
 <span data-ttu-id="6d155-107">下列 XML 顯示 SQLEXECUTE 訊息傳回 Oracle 序列的下一個值。</span><span class="sxs-lookup"><span data-stu-id="6d155-107">The following XML shows a SQLEXECUTE message that returns the next value of an Oracle SEQUENCE.</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8" ?>  
\<!-- New Action: http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE -->  
<SQLEXECUTE xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE">  
    <SQLSTATEMENT>SELECT tid_seq.nextval id FROM dual</SQLSTATEMENT>  
</SQLEXECUTE>  
```  
  
 <span data-ttu-id="6d155-108">SQLEXECUTE 可以指定參數的結構描述項目與包含多個參數的資料集參數區塊。</span><span class="sxs-lookup"><span data-stu-id="6d155-108">The SQLEXECUTE can specify a parameter schema element and a parameter block that contains multiple sets of parameter data.</span></span> <span data-ttu-id="6d155-109">顯示的訊息是指定的 SQL 陳述式中的單一引動過程，因此訊息本文中會省略指定的參數結構描述和參數區塊的項目。</span><span class="sxs-lookup"><span data-stu-id="6d155-109">The message shown is for a single invocation of the specified SQL statement so the elements that specify the parameter schema and parameter block are omitted from the message body.</span></span> <span data-ttu-id="6d155-110">SQLEXECUTE 操作訊息結構描述的相關資訊，請參閱[SQLEXECUTE 操作的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="6d155-110">For information about the message schema for the SQLEXECUTE operation, see [Message Schemas for the SQLEXECUTE Operation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md).</span></span>  
  
## <a name="specifying-the-sqlexecute-action"></a><span data-ttu-id="6d155-111">指定 SQLEXECUTE 動作</span><span class="sxs-lookup"><span data-stu-id="6d155-111">Specifying the SQLEXECUTE Action</span></span>  
 <span data-ttu-id="6d155-112">您必須指定訊息的動作。</span><span class="sxs-lookup"><span data-stu-id="6d155-112">You must specify an action for the message.</span></span> <span data-ttu-id="6d155-113">下列程式碼摘錄示範如何指定 SQLEXECUTE 訊息的動作。</span><span class="sxs-lookup"><span data-stu-id="6d155-113">The following code excerpt shows how to specify the action for the SQLEXECUTE message.</span></span>  
  
```  
Message messageIn = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE", readerIn);  
```  
  
## <a name="sending-the-sqlexecute-message"></a><span data-ttu-id="6d155-114">傳送 SQLEXECUTE 訊息</span><span class="sxs-lookup"><span data-stu-id="6d155-114">Sending the SQLEXECUTE Message</span></span>  
 <span data-ttu-id="6d155-115">下列程式碼摘錄示範如何在通道上叫用 SQLEXECUTE 操作的 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="6d155-115">The following code excerpt demonstrates how to invoke a SQLEXECUTE operation on an Oracle database over a channel.</span></span>  
  
```  
// Create Endpoint  
EndpointAddress address = new EndpointAddress("oracledb://ADAPTER");  
  
// Create Binding  
OracleDBBinding binding = new OracleDBBinding();  
  
// Create Channel Factory  
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
factory.Credentials.UserName.UserName = "SCOTT";  
factory.Credentials.UserName.Password = "TIGER";  
factory.Open();  
  
// Create Request Channel  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
  
// Send Request  
System.Xml.XmlReader readerIn = System.Xml.XmlReader.Create("SQLExecute.xml");  
  
Message messageIn = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE", readerIn);  
Message messageOut = channel.Request(messageIn);  
  
// Get Response XML  
XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
  
// Get tid_seq SEQUENCE  
string id = null;  
XmlDocument doc = new XmlDocument();  
doc.Load(readerOut);  
XmlNodeList list = doc.GetElementsByTagName("ColumnValue");  
if (list.Count > 0) id = list[0].InnerXml;  
```  
  
> [!NOTE]
>  <span data-ttu-id="6d155-116">SQLEXECUTE 作業一律會傳回弱式類型的結果集。</span><span class="sxs-lookup"><span data-stu-id="6d155-116">The SQLEXECUTE operation always returns a weakly-typed result set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d155-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d155-117">See Also</span></span>  
 [<span data-ttu-id="6d155-118">開發 Oracle 資料庫應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="6d155-118">Develop Oracle Database applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)  
 [<span data-ttu-id="6d155-119">建立通道使用 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="6d155-119">Create a channel using Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md)