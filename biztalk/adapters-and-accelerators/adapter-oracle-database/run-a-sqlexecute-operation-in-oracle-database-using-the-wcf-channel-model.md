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
ms.openlocfilehash: d5bb458af94d61ceb89a725f80606d8dda2af579
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model"></a>使用 WCF 通道模型的 Oracle 資料庫中執行 SQLEXECUTE 操作
本節說明如何透過通道執行 SQLEXECUTE 操作的 Oracle 資料庫。 您必須在 SOAP 訊息指定訊息和訊息動作。 如需 SQLEXECUTE 操作的詳細資訊，請參閱[在 Oracle 資料庫中使用 WCF 服務模型執行 SQLEXECUTE 操作](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)。  
  
## <a name="the-sqlexecute-message"></a>SQLEXECUTE 訊息  
 下列 XML 顯示 SQLEXECUTE 訊息傳回 Oracle 序列的下一個值。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- New Action: http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE -->  
<SQLEXECUTE xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE">  
    <SQLSTATEMENT>SELECT tid_seq.nextval id FROM dual</SQLSTATEMENT>  
</SQLEXECUTE>  
```  
  
 SQLEXECUTE 可以指定參數的結構描述項目與包含多個參數的資料集參數區塊。 顯示的訊息是指定的 SQL 陳述式中的單一引動過程，因此訊息本文中會省略指定的參數結構描述和參數區塊的項目。 SQLEXECUTE 操作訊息結構描述的相關資訊，請參閱[SQLEXECUTE 操作的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md)。  
  
## <a name="specifying-the-sqlexecute-action"></a>指定 SQLEXECUTE 動作  
 您必須指定訊息的動作。 下列程式碼摘錄示範如何指定 SQLEXECUTE 訊息的動作。  
  
```  
Message messageIn = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE", readerIn);  
```  
  
## <a name="sending-the-sqlexecute-message"></a>傳送 SQLEXECUTE 訊息  
 下列程式碼摘錄示範如何在通道上叫用 SQLEXECUTE 操作的 Oracle 資料庫。  
  
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
>  SQLEXECUTE 作業一律會傳回弱式類型的結果集。  
  
## <a name="see-also"></a>請參閱  
 [開發 Oracle 資料庫應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)  
 [建立通道使用 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md)