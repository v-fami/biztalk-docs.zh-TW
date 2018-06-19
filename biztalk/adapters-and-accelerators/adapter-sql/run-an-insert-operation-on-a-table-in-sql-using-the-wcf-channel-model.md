---
title: 在使用 WCF 通道模型的 SQL 執行插入作業的資料表上 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3df95d78-3a9c-48c0-81ab-1f3206c5e3f7
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7bceb236b660b80c1e46cb0410d799d994516c40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224406"
---
# <a name="run-an-insert-operation-on-a-table-in-sql-using-the-wcf-channel-model"></a><span data-ttu-id="80651-102">在使用 WCF 通道模型的 SQL 執行插入作業的資料表</span><span class="sxs-lookup"><span data-stu-id="80651-102">Run an Insert Operation on a Table in SQL using the WCF Channel Model</span></span>
<span data-ttu-id="80651-103">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會探索 SQL Server 資料庫資料表和檢視表的基本 Insert、 Select、 Update 和 Delete 作業的一組。</span><span class="sxs-lookup"><span data-stu-id="80651-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] discovers a set of basic Insert, Select, Update, and Delete operations on SQL Server database tables and views.</span></span> <span data-ttu-id="80651-104">藉由使用這些作業，您可以執行簡單的 SQL Insert、 Select、 Update 和 Delete 陳述式 Where 所限定的目標資料表或檢視上的子句。</span><span class="sxs-lookup"><span data-stu-id="80651-104">By using these operations, you can perform simple SQL Insert, Select, Update, and Delete statements qualified by a Where clause on a target table or view.</span></span> <span data-ttu-id="80651-105">本主題提供有關如何執行插入作業使用 WCF 通道模型的 SQL Server 資料庫資料表上的指示。</span><span class="sxs-lookup"><span data-stu-id="80651-105">This topic provides instructions on how to perform an Insert operation on a SQL Server database table using the WCF channel model.</span></span>  
  
 <span data-ttu-id="80651-106">如需有關配接器如何支援這些作業的詳細資訊，請參閱[Insert、 Update、 Delete 和選取資料表和檢視表與 SQL 配接器的作業](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="80651-106">For more information on how the adapter supports these operations, see [Insert, Update, Delete, and Select Operations on Tables and Views with the SQL adapter](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md).</span></span> <span data-ttu-id="80651-107">如需如何使用 WCF 通道模型的 SQL Server 上執行作業的詳細資訊，請參閱[SQL 配接器的 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="80651-107">For more information about how to perform operations on SQL Server using the WCF Channel model, see [Overview of the WCF channel model with the SQL adapter](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="80651-108">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="80651-108">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="80651-109">本主題中的範例上執行作業的員工資料表。</span><span class="sxs-lookup"><span data-stu-id="80651-109">The example in this topic performs operations on the Employee table.</span></span> <span data-ttu-id="80651-110">Employee 資料表會建立執行範例所提供的 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="80651-110">The Employee table is created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="80651-111">如需有關範例的詳細資訊，請參閱[SQL 配接器範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="80651-111">For more information about samples, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span></span> <span data-ttu-id="80651-112">範例中， **EmployeeInsertOp**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="80651-112">A sample, **EmployeeInsertOp**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-insert-message"></a><span data-ttu-id="80651-113">插入訊息</span><span class="sxs-lookup"><span data-stu-id="80651-113">The Insert Message</span></span>  
 <span data-ttu-id="80651-114">若要執行使用 WCF 通道模型的 SQL Server 資料庫上的作業，您必須使用特定作業的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="80651-114">To perform operations on the SQL Server database using the WCF channel model, you must have the request message specific to the operation.</span></span> <span data-ttu-id="80651-115">要執行 SQL Server 資料庫中的 Employee 資料表的插入作業的要求訊息如下所示：</span><span class="sxs-lookup"><span data-stu-id="80651-115">The request message to perform an Insert operation on the Employee table in the SQL Server database resembles the following:</span></span>  
  
```  
<Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
  <Rows>  
    <Employee xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
      <Name>Tom Smith</Name>  
      <Designation>Manager</Designation>  
      <Salary>500000</Salary>  
   </Employee>  
  </Rows>  
</Insert>  
```  
  
 <span data-ttu-id="80651-116">此要求訊息會插入記錄，詳細資料如下：</span><span class="sxs-lookup"><span data-stu-id="80651-116">This request message inserts a record with following details:</span></span>  
  
```  
Name = Tom Smith  
Designation = Manager  
Salary = 500000  
```  
  
 <span data-ttu-id="80651-117">您必須將訊息複製到檔案，例如 InsertRequest.xml。</span><span class="sxs-lookup"><span data-stu-id="80651-117">You must copy the message to a file, e.g. InsertRequest.xml.</span></span> <span data-ttu-id="80651-118">此檔案用於在此範例中將要求訊息傳送至 SQL Server 使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="80651-118">This file is used in this example to send the request message to SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="80651-119">如需資料表作業的訊息結構描述的詳細資訊，請參閱[Insert、 Update、 Delete 和資料表和檢視表的選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)。</span><span class="sxs-lookup"><span data-stu-id="80651-119">For more information about the message schema for operations on table, see [Message Schemas for Insert, Update, Delete, and Select Operations on Tables and Views](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).</span></span>  
  
## <a name="creating-a-wcf-channel-application"></a><span data-ttu-id="80651-120">建立 WCF 通道應用程式</span><span class="sxs-lookup"><span data-stu-id="80651-120">Creating a WCF Channel Application</span></span>  
 <span data-ttu-id="80651-121">本節提供有關如何建立 WCF 通道應用程式執行插入作業的 Employee 資料表上的指示。</span><span class="sxs-lookup"><span data-stu-id="80651-121">This section provides instructions on how to create a WCF channel application to perform an Insert operation on the Employee table.</span></span>  
  
#### <a name="to-create-a-wcf-channel-application-for-inserting-records-into-the-employee-table"></a><span data-ttu-id="80651-122">若要建立的 WCF 通道應用程式的 Employee 資料表中插入記錄</span><span class="sxs-lookup"><span data-stu-id="80651-122">To create a WCF channel application for inserting records into the Employee table</span></span>  
  
1.  <span data-ttu-id="80651-123">Visual Studio 中建立 Visual C# 專案。</span><span class="sxs-lookup"><span data-stu-id="80651-123">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="80651-124">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="80651-124">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="80651-125">在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`， `Microsoft.ServiceModel.Channels`， `System.ServiceModel`，和`System.Runtime.Serialization`。</span><span class="sxs-lookup"><span data-stu-id="80651-125">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, and `System.Runtime.Serialization`.</span></span>  
  
3.  <span data-ttu-id="80651-126">開啟 Program.cs 檔案並加入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="80651-126">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.Sql`  
  
    -   `Microsoft.ServiceModel.Channels`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
4.  <span data-ttu-id="80651-127">建立繫結和端點。</span><span class="sxs-lookup"><span data-stu-id="80651-127">Create the binding and endpoint.</span></span>  
  
    ```  
    SqlAdapterBinding binding = new SqlAdapterBinding();  
    EndpointAddress address = new EndpointAddress("mssql://mysqlserver//mydatabase?");  
  
    ```  
  
5.  <span data-ttu-id="80651-128">建立並開啟通道處理站。</span><span class="sxs-lookup"><span data-stu-id="80651-128">Create and open the channel factory.</span></span> <span data-ttu-id="80651-129">此應用程式將要求訊息傳送到 SQL Server，並接收回應，因此您必須實作 IRequestChannel 介面。</span><span class="sxs-lookup"><span data-stu-id="80651-129">This application sends request message to SQL Server and receives a response, hence you must implement the IRequestChannel interface.</span></span>  
  
    ```  
    ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
    factory.Credentials.UserName.UserName = "<Enter user name here>";  
    factory.Credentials.UserName.Password = "<Enter password here>";  
    factory.Open();  
    ```  
  
6.  <span data-ttu-id="80651-130">建立並開啟通道。</span><span class="sxs-lookup"><span data-stu-id="80651-130">Create and open the channel.</span></span>  
  
    ```  
    IRequestChannel channel = factory.CreateChannel();  
    channel.Open();  
    ```  
  
7.  <span data-ttu-id="80651-131">建立並傳送要求訊息。</span><span class="sxs-lookup"><span data-stu-id="80651-131">Create and send the request message.</span></span>  
  
    ```  
    XmlReader readerIn;  
    Console.WriteLine("Creating the message");  
    try  
    {  
       readerIn = XmlReader.Create("InsertRequest.xml");  
       Console.WriteLine("Reader created");  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
    Message messageIn = Message.CreateMessage(MessageVersion.Default, "TableOp/Insert/dbo/Employee", readerIn);  
    Message messageOut = channel.Request(messageIn);  
  
    ```  
  
     <span data-ttu-id="80651-132">在建立要求訊息時，您必須指定表示配接器會在 SQL Server 資料表執行的動作的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="80651-132">While creating the request message, you must specify the message action that indicates the action that the adapter performs on the SQL Server table.</span></span> <span data-ttu-id="80651-133">若要執行插入作業的員工資料表，是訊息動作`TableOp/Insert/dbo/Employee`。</span><span class="sxs-lookup"><span data-stu-id="80651-133">To perform an Insert operation on the Employee table, the message action is `TableOp/Insert/dbo/Employee`.</span></span> <span data-ttu-id="80651-134">如需如何判斷在資料表上的各種動作的訊息動作資訊，請參閱[Insert、 Update、 Delete 和資料表和檢視表的選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)。</span><span class="sxs-lookup"><span data-stu-id="80651-134">For information about how you can determine the message action for various operations on tables, see [Message Schemas for Insert, Update, Delete, and Select Operations on Tables and Views](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).</span></span>  
  
8.  <span data-ttu-id="80651-135">取得回應訊息。</span><span class="sxs-lookup"><span data-stu-id="80651-135">Get the response message.</span></span>  
  
    ```  
    XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
    XmlDocument doc = new XmlDocument();  
    doc.Load(readerOut);  
    doc.Save("C:\\Response.xml");  
    ```  
  
9. <span data-ttu-id="80651-136">關閉訊息、 通道和通道處理站。</span><span class="sxs-lookup"><span data-stu-id="80651-136">Close the message, channel, and channel factory.</span></span>  
  
    ```  
    messageOut.Close();  
    channel.Close();  
    factory.Close();  
    ```  
  
10. <span data-ttu-id="80651-137">建置專案。</span><span class="sxs-lookup"><span data-stu-id="80651-137">Build the project.</span></span> <span data-ttu-id="80651-138">建置專案之後, 您必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="80651-138">After building the project, you must perform the following tasks:</span></span>  
  
    -   <span data-ttu-id="80651-139">將複製的要求訊息，InsertRequest.xml，在您的專案可執行檔相同的位置。</span><span class="sxs-lookup"><span data-stu-id="80651-139">Copy the request message, InsertRequest.xml, at the same location as your project executable.</span></span> <span data-ttu-id="80651-140">一般而言，這個位置是專案目錄底下的 \bin\Debug\。</span><span class="sxs-lookup"><span data-stu-id="80651-140">Typically, this location is \bin\Debug\ under your project directory.</span></span>  
  
    -   <span data-ttu-id="80651-141">在此範例中使用的 「 員工 」 資料表具有點使用者定義型別 (UDT) 的資料行。</span><span class="sxs-lookup"><span data-stu-id="80651-141">The "Employee" table used in this example has a column of Point user-defined type (UDT).</span></span> <span data-ttu-id="80651-142">因此，然後再執行專案，您必須建立 Point UDT 的組件述[Creating User-Defined 類型](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types)。</span><span class="sxs-lookup"><span data-stu-id="80651-142">So, before running the project, you must create the assembly for the Point UDT as described at [Creating User-Defined Types](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types).</span></span> <span data-ttu-id="80651-143">您也必須複製的組件 DLL 做為可執行檔專案相同的位置。</span><span class="sxs-lookup"><span data-stu-id="80651-143">You must also copy the assembly DLL at the same location as the project executable.</span></span> <span data-ttu-id="80651-144">一般而言，這個位置是專案目錄底下的 \bin\Debug\。</span><span class="sxs-lookup"><span data-stu-id="80651-144">Typically, this location is \bin\Debug\ under your project directory.</span></span>  
  
11. <span data-ttu-id="80651-145">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80651-145">Run the application.</span></span> <span data-ttu-id="80651-146">回應訊息，Response.xml，會儲存您的應用程式中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="80651-146">The response message, Response.xml, is saved at the location you specified in the application.</span></span> <span data-ttu-id="80651-147">回應訊息包含新加入的員工識別碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="80651-147">The response message contains the ID of the newly added employee and resembles the following:</span></span>  
  
    ```  
    <InsertResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
      <InsertResult>  
        <long xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">10006</long>  
      </InsertResult>  
    </InsertResponse>  
    ```  
  
     <span data-ttu-id="80651-148">因為 Employee 資料表具有 Employee_ID 資料行做為身分識別資料行，插入作業會傳回新插入的資料錄的識別資料行的值。</span><span class="sxs-lookup"><span data-stu-id="80651-148">Because the Employee table has the Employee_ID column as the identity column, the Insert operation returns the value for the identity column of the newly inserted record.</span></span> <span data-ttu-id="80651-149">如果資料表沒有識別資料行，傳回值會是 NULL。</span><span class="sxs-lookup"><span data-stu-id="80651-149">If there is no identity column in a table, the return value is NULL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80651-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80651-150">See Also</span></span>  
[<span data-ttu-id="80651-151">開發 SQL 應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="80651-151">Develop SQL applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)