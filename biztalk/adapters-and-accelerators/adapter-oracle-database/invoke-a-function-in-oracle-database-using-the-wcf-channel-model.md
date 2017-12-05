---
title: "叫用的函式在 Oracle 資料庫中使用 WCF 通道模型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- channel programming, executing a function
- WCF channel model, invoking a function
- how to, execute a function using a channel
- executing a function, using a channel
ms.assetid: 6c15c352-3086-44f6-b265-4c7a7aee47ff
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 115e7e2421ed31ed20db9cbec5abdaa26a3639e8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-a-function-in-oracle-database-using-the-wcf-channel-model"></a><span data-ttu-id="da95b-102">叫用使用 WCF 通道模型的 Oracle 資料庫中的函式</span><span class="sxs-lookup"><span data-stu-id="da95b-102">Invoke a Function in Oracle Database using the WCF Channel Model</span></span>
<span data-ttu-id="da95b-103">本節示範如何使用通道中建立 Oracle 資料庫中執行函式[建立使用 Oracle 資料庫的通道](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="da95b-103">This section demonstrates how to execute a function in an Oracle database using the channel created in [Create a Channel using Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md).</span></span>  
  
## <a name="executing-a-function-using-the-channel"></a><span data-ttu-id="da95b-104">執行使用通道函式</span><span class="sxs-lookup"><span data-stu-id="da95b-104">Executing a Function Using the Channel</span></span>  
 <span data-ttu-id="da95b-105">您可以在 Oracle 資料庫上執行函式，藉由傳遞的 XML 訊息[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="da95b-105">You can execute a function on an Oracle database by passing an XML message to [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span></span> <span data-ttu-id="da95b-106">輸入 XML 如下所示：</span><span class="sxs-lookup"><span data-stu-id="da95b-106">The input XML resembles the following:</span></span>  
  
```  
<CREATE_ACCOUNT xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG" xmlns:ns0="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT">  
  <REC xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
    <ns0:ID>1</ns0:ID>  
    <ns0:NAME>Scott</ns0:NAME>  
    <ns0:BANKNAME>CitiBank</ns0:BANKNAME>  
    <ns0:BRANCH>NY</ns0:BRANCH>  
    <ns0:ENABLED>Y</ns0:ENABLED>  
  </REC>  
</CREATE_ACCOUNT>  
```  
  
 <span data-ttu-id="da95b-107">下列程式碼摘錄示範如何使用通道 Oracle 資料庫中執行函式。</span><span class="sxs-lookup"><span data-stu-id="da95b-107">The following code excerpt demonstrates how to execute a function in an Oracle database using a channel.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Xml;  
  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
  
using Microsoft.ServiceModel.Adapters;  
using Microsoft.Adapters.OracleDB;  
  
namespace OraclePackageChannel  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Create Endpoint  
            EndpointAddress address = new EndpointAddress("oracledb:// ADAPTER");  
  
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
            System.Xml.XmlReader readerIn = System.Xml.XmlReader.Create("Create_Account.xml");  
  
            Message messageIn = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT", readerIn);  
            Message messageOut = channel.Request(messageIn);  
  
            // Get Response XML  
            XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
  
            // Get Employee ID  
            XmlDocument doc = new XmlDocument();  
            doc.Load(readerOut);  
            doc.Save("d:\\out.xml");  
  
            messageOut.Close();  
            channel.Close();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="da95b-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="da95b-108">See Also</span></span>  
 <span data-ttu-id="da95b-109">[使用 WCF 通道模型開發 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md) </span><span class="sxs-lookup"><span data-stu-id="da95b-109">[Develop Oracle Database Applications by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md) </span></span>  
 <span data-ttu-id="da95b-110">[使用 WCF 通道模型的 Oracle 資料庫中，執行插入作業](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md) </span><span class="sxs-lookup"><span data-stu-id="da95b-110">[Run an Insert Operation in Oracle Database Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md) </span></span>  
 [<span data-ttu-id="da95b-111">使用 WCF 通道模型執行 SQLEXECUTE 操作</span><span class="sxs-lookup"><span data-stu-id="da95b-111">Run a SQLEXECUTE Operation by Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)