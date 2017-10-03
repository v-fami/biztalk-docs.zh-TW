---
title: "在使用 WCF 通道模型的 Oracle 資料庫執行插入作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inserting data, using a channel
- WCF channel model, performing an Insert operation
- how to, perform an insert operation using a channel
- channel programming, performing an insert operation
- performing an insert operation, using a channel
ms.assetid: 85c44507-0166-42ef-a908-6098f7a683fc
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 540cd06f15ae95dba41636418be273a78c39f447
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model"></a><span data-ttu-id="419ac-102">在使用 WCF 通道模型的 Oracle 資料庫執行插入作業</span><span class="sxs-lookup"><span data-stu-id="419ac-102">Run an Insert Operation in Oracle Database using the WCF Channel Model</span></span>
<span data-ttu-id="419ac-103">本節說明如何使用通道，Oracle 資料庫中插入一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="419ac-103">This section shows how to insert a record into an Oracle database by using a channel.</span></span> <span data-ttu-id="419ac-104">當您傳送訊息時，您必須指定訊息本文和訊息動作。</span><span class="sxs-lookup"><span data-stu-id="419ac-104">You must specify both a message body and a message action when you send a message.</span></span>  
  
## <a name="the-insert-message"></a><span data-ttu-id="419ac-105">插入訊息</span><span class="sxs-lookup"><span data-stu-id="419ac-105">The Insert Message</span></span>  
 <span data-ttu-id="419ac-106">下列 XML 顯示 HR Insert 作業的訊息主體。EMPLOYEES 資料表。</span><span class="sxs-lookup"><span data-stu-id="419ac-106">The following XML shows a message body for an Insert operation on the HR.EMPLOYEES table.</span></span> <span data-ttu-id="419ac-107">記錄組包含單一位員工的記錄。</span><span class="sxs-lookup"><span data-stu-id="419ac-107">The record set consists of a single employee record.</span></span> <span data-ttu-id="419ac-108">插入訊息的結構描述的相關資訊，請參閱[基本 Insert、 Update、 Delete 和資料表和檢視表的選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)。</span><span class="sxs-lookup"><span data-stu-id="419ac-108">For more information about the schema of an Insert message, see [Message Schemas for the Basic Insert, Update, Delete, and Select Operations on Tables and Views](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).</span></span> <span data-ttu-id="419ac-109">這是範例中使用 Employee_Insert.xml 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="419ac-109">This is the contents of the Employee_Insert.xml file used in the example.</span></span>  
  
```  
\<!-- New namespace: http://Microsoft.LobServices.OracleDB/2007/03/HR/Table/EMPLOYEES -->  
<Insert xmlns="http://Microsoft.LobServices.OracleDB/2007/03/HR/Table/EMPLOYEES">  
    \<RECORDSET xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
        <EMPLOYEESRECORDINSERT>  
            <EMPLOYEE_ID>0</EMPLOYEE_ID>  
            <FIRST_NAME>Anton</FIRST_NAME>  
            <LAST_NAME>Kirilov</LAST_NAME>  
            <EMAIL></EMAIL>  
            <PHONE_NUMBER>555-0198</PHONE_NUMBER>  
            <HIRE_DATE>2007-03-01T00:00:00.0000000</HIRE_DATE>  
            <JOB_ID>FI_ACCOUNT</JOB_ID>  
            <SALARY>5000</SALARY>  
            <COMMISSION_PCT>0.15</COMMISSION_PCT>  
            <MANAGER_ID>108</MANAGER_ID>  
            <DEPARTMENT_ID>100</DEPARTMENT_ID>  
       </EMPLOYEESRECORDINSERT>  
    </RECORDSET>  
</Insert>  
```  
  
## <a name="specifying-the-message-action"></a><span data-ttu-id="419ac-110">指定的訊息動作</span><span class="sxs-lookup"><span data-stu-id="419ac-110">Specifying the Message Action</span></span>  
 <span data-ttu-id="419ac-111">當您傳送 SOAP 訊息時，您必須指定的訊息動作[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="419ac-111">You must specify a message action when you send a SOAP message to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="419ac-112">當您建立的訊息，如下列範例所示，您可以指定的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="419ac-112">You can specify the message action when you create the message as in the following example.</span></span>  
  
```  
Message messageIn2 = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.OracleDB/2007/03/HR/Table/EMPLOYEES/Insert", readerIn2);  
```  
  
 <span data-ttu-id="419ac-113">指定的訊息動作，在此範例中，「 / 小時/資料表/員工/插入 」，HR Insert 作業。是要執行的 EMPLOYEES 資料表</span><span class="sxs-lookup"><span data-stu-id="419ac-113">The message action in this example, "/HR/Table/EMPLOYEES/Insert", specifies that an Insert operation on the HR.EMPLOYEES table is to be performed</span></span>  
  
## <a name="sending-the-insert-message"></a><span data-ttu-id="419ac-114">將插入的訊息傳送</span><span class="sxs-lookup"><span data-stu-id="419ac-114">Sending the Insert Message</span></span>  
 <span data-ttu-id="419ac-115">這個範例示範如何透過通道執行 Oracle 資料表插入作業。</span><span class="sxs-lookup"><span data-stu-id="419ac-115">This example shows how to perform an Insert operation on an Oracle table over a channel.</span></span> <span data-ttu-id="419ac-116">程式碼會使用所公開的 SQLEXECUTE 操作[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]傳回 Oracle 序列的下一個值。</span><span class="sxs-lookup"><span data-stu-id="419ac-116">The code uses the SQLEXECUTE operation exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to return the next value of an Oracle SEQUENCE.</span></span> <span data-ttu-id="419ac-117">然後，此值會寫至 EMPLOYEE_ID 欄位中插入記錄。</span><span class="sxs-lookup"><span data-stu-id="419ac-117">This value is then written to the EMPLOYEE_ID field in the Insert record.</span></span> <span data-ttu-id="419ac-118">此模式可讓您將資料列插入具有自動產生主索引鍵值的資料庫。</span><span class="sxs-lookup"><span data-stu-id="419ac-118">This pattern enables you to insert rows into databases that have an auto-generated primary key value.</span></span> <span data-ttu-id="419ac-119">如需有關如何在通道上叫用 SQLEXECUTE 操作的詳細資訊，請參閱[使用 WCF 通道模型執行 SQLEXECUTE 操作](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="419ac-119">For more information about invoking the SQLEXECUTE operation over a channel, see [Run a SQLEXECUTE Operation by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md).</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Xml;  
using System.IO;  
  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
  
using Microsoft.ServiceModel.Adapters;  
using Microsoft.Adapters.OracleDB;  
  
namespace OracleDMLChannel  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Create Endpoint  
            EndpointAddress address = new EndpointAddress("oracledb://ADAPTER");  
  
            // Create Binding  
            OracleDBBinding binding = new OracleDBBinding();  
  
            // Create Channel Factory  
            ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
            factory.Credentials.UserName.UserName = "HR";  
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
  
            // Get Employee ID  
            string id = null;  
            XmlDocument doc = new XmlDocument();  
            doc.Load(readerOut);  
            XmlNodeList list = doc.GetElementsByTagName("ColumnValue");  
            if (list.Count > 0) id = list[0].InnerXml;  
  
            // Compose Insert XML  
            XmlDocument insertDoc = new XmlDocument();  
            insertDoc.Load("Employee_Insert.xml");  
  
            // Change Employee ID  
            XmlNodeList empidList = insertDoc.GetElementsByTagName("EMPLOYEE_ID");  
            XmlNode empidNode = empidList[0];  
            empidNode.InnerXml = id;  
  
            // Change email  
            XmlNodeList emailList = insertDoc.GetElementsByTagName("EMAIL");  
            XmlNode emailNode = emailList[0];  
            emailNode.InnerXml = "scotty" + id + "@microsoft.com";  
  
            // Change date  
            XmlNodeList dateList = insertDoc.GetElementsByTagName("HIRE_DATE");  
            XmlNode dateNode = dateList[0];  
            dateNode.InnerXml = "2007-03-01T00:00:00.0000000";  
  
            StringReader strReader = new StringReader(insertDoc.InnerXml);  
            XmlReader readerIn2 = XmlReader.Create(strReader);  
  
            // Send XML  
            Message messageIn2 = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.OracleDB/2007/03/HR/Table/EMPLOYEES/Insert ", readerIn2);  
            Message messageOut2 = channel.Request(messageIn2);  
  
            // Close the messages  
            messageOut.Close();  
            messageOut2.Close();  
  
            channel.Close();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="419ac-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="419ac-120">See Also</span></span>  
 <span data-ttu-id="419ac-121">[開發 Oracle 資料庫應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md) </span><span class="sxs-lookup"><span data-stu-id="419ac-121">[Develop Oracle Database applications Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md) </span></span>  
 <span data-ttu-id="419ac-122">[建立通道使用 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md) </span><span class="sxs-lookup"><span data-stu-id="419ac-122">[Create a channel using Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md) </span></span>  
 <span data-ttu-id="419ac-123">[使用 WCF 通道模型執行 SQLEXECUTE 操作](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md) </span><span class="sxs-lookup"><span data-stu-id="419ac-123">[Run a SQLEXECUTE Operation by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md) </span></span>  
 [<span data-ttu-id="419ac-124">叫用使用 WCF 通道模型的 Oracle 資料庫中的函式</span><span class="sxs-lookup"><span data-stu-id="419ac-124">Invoke a Function in Oracle Database Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)