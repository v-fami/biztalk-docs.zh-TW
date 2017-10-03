---
title: "在使用 WCF 通道模型的 SQL 執行插入作業的資料表上 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3df95d78-3a9c-48c0-81ab-1f3206c5e3f7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7bceb236b660b80c1e46cb0410d799d994516c40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="run-an-insert-operation-on-a-table-in-sql-using-the-wcf-channel-model"></a>在使用 WCF 通道模型的 SQL 執行插入作業的資料表
[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會探索 SQL Server 資料庫資料表和檢視表的基本 Insert、 Select、 Update 和 Delete 作業的一組。 藉由使用這些作業，您可以執行簡單的 SQL Insert、 Select、 Update 和 Delete 陳述式 Where 所限定的目標資料表或檢視上的子句。 本主題提供有關如何執行插入作業使用 WCF 通道模型的 SQL Server 資料庫資料表上的指示。  
  
 如需有關配接器如何支援這些作業的詳細資訊，請參閱[Insert、 Update、 Delete 和選取資料表和檢視表與 SQL 配接器的作業](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md)。 如需如何使用 WCF 通道模型的 SQL Server 上執行作業的詳細資訊，請參閱[SQL 配接器的 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md)。  
  
## <a name="about-the-examples-used-in-this-topic"></a>關於本主題中使用的範例  
 本主題中的範例上執行作業的員工資料表。 Employee 資料表會建立執行範例所提供的 SQL 指令碼。 如需有關範例的詳細資訊，請參閱[SQL 配接器範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。 範例中， **EmployeeInsertOp**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。  
  
## <a name="the-insert-message"></a>插入訊息  
 若要執行使用 WCF 通道模型的 SQL Server 資料庫上的作業，您必須使用特定作業的要求訊息。 要執行 SQL Server 資料庫中的 Employee 資料表的插入作業的要求訊息如下所示：  
  
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
  
 此要求訊息會插入記錄，詳細資料如下：  
  
```  
Name = Tom Smith  
Designation = Manager  
Salary = 500000  
```  
  
 您必須將訊息複製到檔案，例如 InsertRequest.xml。 此檔案用於在此範例中將要求訊息傳送至 SQL Server 使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 如需資料表作業的訊息結構描述的詳細資訊，請參閱[Insert、 Update、 Delete 和資料表和檢視表的選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)。  
  
## <a name="creating-a-wcf-channel-application"></a>建立 WCF 通道應用程式  
 本節提供有關如何建立 WCF 通道應用程式執行插入作業的 Employee 資料表上的指示。  
  
#### <a name="to-create-a-wcf-channel-application-for-inserting-records-into-the-employee-table"></a>若要建立的 WCF 通道應用程式的 Employee 資料表中插入記錄  
  
1.  Visual Studio 中建立 Visual C# 專案。 本主題中，建立主控台應用程式。  
  
2.  在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`， `Microsoft.ServiceModel.Channels`， `System.ServiceModel`，和`System.Runtime.Serialization`。  
  
3.  開啟 Program.cs 檔案並加入下列命名空間：  
  
    -   `Microsoft.Adapters.Sql`  
  
    -   `Microsoft.ServiceModel.Channels`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
4.  建立繫結和端點。  
  
    ```  
    SqlAdapterBinding binding = new SqlAdapterBinding();  
    EndpointAddress address = new EndpointAddress("mssql://mysqlserver//mydatabase?");  
  
    ```  
  
5.  建立並開啟通道處理站。 此應用程式將要求訊息傳送到 SQL Server，並接收回應，因此您必須實作 IRequestChannel 介面。  
  
    ```  
    ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
    factory.Credentials.UserName.UserName = "<Enter user name here>";  
    factory.Credentials.UserName.Password = "<Enter password here>";  
    factory.Open();  
    ```  
  
6.  建立並開啟通道。  
  
    ```  
    IRequestChannel channel = factory.CreateChannel();  
    channel.Open();  
    ```  
  
7.  建立並傳送要求訊息。  
  
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
  
     在建立要求訊息時，您必須指定表示配接器會在 SQL Server 資料表執行的動作的訊息動作。 若要執行插入作業的員工資料表，是訊息動作`TableOp/Insert/dbo/Employee`。 如需如何判斷在資料表上的各種動作的訊息動作資訊，請參閱[Insert、 Update、 Delete 和資料表和檢視表的選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)。  
  
8.  取得回應訊息。  
  
    ```  
    XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
    XmlDocument doc = new XmlDocument();  
    doc.Load(readerOut);  
    doc.Save("C:\\Response.xml");  
    ```  
  
9. 關閉訊息、 通道和通道處理站。  
  
    ```  
    messageOut.Close();  
    channel.Close();  
    factory.Close();  
    ```  
  
10. 建置專案。 建置專案之後, 您必須執行下列工作：  
  
    -   將複製的要求訊息，InsertRequest.xml，在您的專案可執行檔相同的位置。 一般而言，這個位置是專案目錄底下的 \bin\Debug\。  
  
    -   在此範例中使用的 「 員工 」 資料表具有點使用者定義型別 (UDT) 的資料行。 因此，然後再執行專案，您必須建立 Point UDT 的組件述[Creating User-Defined 類型](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types)。 您也必須複製的組件 DLL 做為可執行檔專案相同的位置。 一般而言，這個位置是專案目錄底下的 \bin\Debug\。  
  
11. 執行應用程式。 回應訊息，Response.xml，會儲存您的應用程式中指定的位置。 回應訊息包含新加入的員工識別碼，如下所示：  
  
    ```  
    <InsertResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
      <InsertResult>  
        <long xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">10006</long>  
      </InsertResult>  
    </InsertResponse>  
    ```  
  
     因為 Employee 資料表具有 Employee_ID 資料行做為身分識別資料行，插入作業會傳回新插入的資料錄的識別資料行的值。 如果資料表沒有識別資料行，傳回值會是 NULL。  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)