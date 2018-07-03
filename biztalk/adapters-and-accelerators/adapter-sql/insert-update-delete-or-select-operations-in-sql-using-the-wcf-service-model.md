---
title: 插入、 更新、 刪除或選取 使用 WCF 服務模型的 SQL 中的 作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340048ad-ce28-4acf-ae4e-f18bdb3b6f47
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dcf58b5ff9a379b7b28647e0d5b07475d08310db
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011165"
---
# <a name="insert-update-delete-or-select-operations-in-sql-using-the-wcf-service-model"></a>插入、 更新、 刪除或選取作業中使用 WCF 服務模型的 SQL
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]探索一組 SQL Server 資料庫資料表和檢視表的基本 Insert、 Select、 Update 和 Delete 作業。 藉由使用這些作業，您可以執行簡單 SQL Insert、 Select、 Update 和 Delete 陳述式的限定 Where 子句的目標資料表或檢視上。 本主題提供有關如何使用 WCF 服務模型執行這些作業的指示。  
  
 如需有關配接器如何支援這些作業的詳細資訊，請參閱[Insert、 Update、 Delete 與資料表和 SQL 配接器的檢視表的選取作業](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md)。  
  
> [!NOTE]
>  如果您正在執行具有使用者定義類型的資料行的資料表上的作業，請確定您參考[資料表和檢視與使用 SQL 配接器的使用者定義型別上的作業](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md)開始開發您的應用程式之前。  
  
## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例上執行作業的 Employee 資料表。 [員工] 資料表會建立執行 SQL 指令碼提供範例。 如需有關範例的詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。 範例中， **EmployeeBasicOps**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 WCF 用戶端的基本的 SQL 作業產生的名稱，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會探索下表所示，為基礎的資料表或檢視的名稱。  
  
|SQL Server 資料庫成品|WCF 用戶端名稱|  
|----------------------------------|---------------------|  
|Table|TableOp_[Schema]_[TABLE_NAME]Client|  
|檢視|ViewOp_[Schema]_[VIEW_NAME]Client|  
  
 [SCHEMA] = Collection 的 SQL Server 成品、比方說，dbo。  
  
 [TABLE_NAME] = 資料表的名稱例如，員工。  
  
 [VIEW_NAME] = 檢視; 的名稱比方說，Employee_View。  
  
### <a name="method-signature-for-invoking-operations-on-tables"></a>叫用資料表上的作業的方法簽章  
 下表顯示在資料表上的基本作業的方法簽章。 簽章也適用於檢視中，不同之處在於檢視命名空間和名稱取代的資料表。  
  
|作業|方法簽章|  
|---------------|----------------------|  
|Insert|long[] Insert([TABLE_NS].[TABLE_NAME][] Rows);|  
|Select|[TABLE_NS]。[名稱][] 選取 （字串資料行，查詢字串）;|  
|Update|int Update([TABLE_NS].[TABLE_NAME].RowPair[] Rows);|  
|DELETE|int Delete ([TABLE_NS]。 [TABLE_NAME] [] 資料列）;|  
  
 [TABLE_NS] = 資料表的命名空間的名稱比方說，schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee。  
  
 [TABLE_NAME] = 資料表的名稱例如，員工。  
  
 例如，下列的程式碼會示範下的預設值"dbo"結構描述的 Employee 資料表的 Delete、 Insert、 Select 和 Update 作業所產生的 WCF 用戶端類別的方法簽章。  
  
```  
public partial class TableOp_dbo_EmployeeClient : System.ServiceModel.ClientBase<TableOp_dbo_Employee>, TableOp_dbo_Employee {      
    public int Delete(schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] Rows);  
  
    public long[] Insert(schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] Rows);  
  
    public schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] Select(string Columns, string Query);  
  
    public int Update(schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair[] Rows);  
}  
```  
  
 在此片段中，TableOp_dbo_EmployeeClient 是 WCF 中類別的名稱所產生 SqlAdapterBindingClient.cs [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
### <a name="parameters-for-table-operations"></a>資料表作業的參數  
 本節提供每個資料表作業所需的參數  
  
 **插入作業**  
  
|插入作業類型|資料錄集|  
|---------------------------|---------------|  
|多個記錄|應該插入至資料表的 INSERTRECORDS 的集合。|  
  
 插入作業會傳回長整數資料類型的陣列，並將插入的資料列的識別值，如果有的話。 如果資料表沒有識別資料行，傳回的值會是 NULL。  
  
 **選取作業**  
  
|COLUMN_NAMES|QUERY|  
|-------------------|-----------|  
|目標; 中的資料行名稱的逗號分隔清單例如，"Employee_ID，指定"。 資料行清單中指定目標應該在結果集中傳回之資料的行。 未指定資料行清單中的資料行，將設為.NET 預設值在傳回的記錄集內。 Nillable 的資料行，這個值是**null**。|SQL WHERE 子句，指定查詢; 的目標資料列的內容比方說，「 名稱 = 'Manager' 」。 您可以將此參數設定為**null**傳回目標的所有資料列。|  
  
 選取作業的傳回值是強型別結果集，其中包含指定的資料行和資料列從目標資料表或檢視表。  
  
 **更新作業**  
  
|該配對的第一個資料列|該配對的第二個資料列|  
|---------------------------|----------------------------|  
|第一筆記錄，需要更新的新值相對應組的記錄亦即，它對應到 UPDATE 陳述式的 SET 子句。 這可以設定使用`RowPair.After`。|記錄組的第二個記錄對應到資料列的舊值，也就是它會對應到 UPDATE 陳述式的 WHERE 子句。 這可以設定使用`RowPair.Before`。|  
  
 更新作業的傳回值是 Int32 資料型別，並代表更新之資料列數目。  
  
> [!IMPORTANT]
>  同時指定必須更新的記錄，您必須針對所有資料行，提供值，即使未正確更新所有的值。 比方說，如果資料列都有五個資料行，而且更新作業更新只有 2 個資料行，做為 RowPair.Before 的一部分，您必須傳遞所有的 5 個資料行值。 不過，如 RowPair.After，您可以指定將更新的資料行。  
  
 **刪除作業**  
  
 刪除作業會為強型別之輸入陣列的記錄。 刪除作業的傳回值是 Int32 資料型別，並代表刪除資料列數目。  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-tables-and-views"></a>建立 WCF 用戶端來叫用資料表和檢視上的作業  
 一組標準的 SQL Server 使用 WCF 用戶端上執行作業所需的動作牽涉到一組工作中所述[使用 SQL 配接器的 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md)。 本節說明如何建立 WCF 用戶端來叫用基本 Insert、 Select、 Update 資料表上的刪除作業。  
  
#### <a name="to-create-a-wcf-client-to-perform-operations-on-tables"></a>若要建立的 WCF 用戶端，在資料表上執行作業  
  
1. Visual Studio 中建立 Visual C# 專案。 本主題中，建立主控台應用程式。  
  
2. 產生 WCF 用戶端類別的 Insert、 Select、 Update 和刪除員工資料表上的作業。 如需有關如何產生 WCF 用戶端類別的詳細資訊，請參閱 <<c0> [ 產生的 SQL Server 成品的 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。  
  
   > [!IMPORTANT]
   >  在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。  
  
3. 在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`和`Microsoft.ServiceModel.Channels`。  
  
4. 開啟 Program.cs 檔案，並建立用戶端，如下列程式碼片段中所述。  
  
   ```  
  
             TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient("SqlAdapterBinding_TableOp_dbo_Employee");  
   client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
   client.ClientCredentials.UserName.Password = "<Enter password here>";  
   ```  
  
    在此片段中， `TableOp_dbo_EmployeeClient` SqlAdapterBindingClient.cs 中定義之 WCF 用戶端。 此檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 `SqlAdapterBinding_TableOp_dbo_Employee` 是用戶端端點組態名稱，並在 app.config 中定義。此檔案也會產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，其中包含繫結屬性和其他組態設定。  
  
   > [!NOTE]
   >  在此片段中，您使用的繫結和端點位址從組態檔。 您也可以明確指定這些值在您的程式碼。 如需有關指定用戶端繫結的不同方式的詳細資訊，請參閱[設定 SQL 配接器的用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)。  
  
5. 下列程式碼片段中所述，請開啟用戶端：  
  
   ```  
   try  
   {  
      Console.WriteLine("Opening Client...");  
      client.Open();  
   }  
   catch (Exception ex)  
   {  
      Console.WriteLine("Exception: " + ex.Message);  
      throw;  
   }  
   ```  
  
6. 叫用 [員工] 資料表的 Insert 作業。  
  
   ```  
   long[] recordsInserted;  
  
   schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] insertRecord =  
   new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[1];  
  
   insertRecord[0] = new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee();  
   insertRecord[0].Name = "John Smith";  
   insertRecord[0].Designation = "Manager";  
   insertRecord[0].Salary = 500000;  
  
   try  
   {  
      Console.WriteLine("Inserting new table entry...");  
      recordsInserted = client.Insert(insertRecord);  
   }  
   catch (Exception ex)  
   {  
      Console.WriteLine("Exception: " + ex.Message);  
      throw;  
   }  
  
   Console.WriteLine("Record inserted");  
   Console.WriteLine("Press any key to continue ...");  
   Console.ReadLine();  
   ```  
  
    您可以取代上述程式碼片段來執行 Select、 Update 或 Delete 作業，以及。 您也可以附加到在單一應用程式中執行所有作業的程式碼片段。 如需如何執行這些作業的程式碼片段。  
  
7. 下列程式碼片段中所述，請關閉該用戶端：  
  
   ```  
   client.Close();  
   Console.WriteLine("Press any key to exit...");  
   Console.ReadLine();  
   ```  
  
8. 建置專案，然後執行它。 應用程式中的 Employee 資料表中插入記錄。  
  
###   <a name="select-operation"></a>選取作業  
 下列程式碼會顯示為目標的 Employee 資料表的選取作業。 選取的作業選取插入至資料表的最後一個記錄。 傳回的記錄會寫入至主控台。  
  
```  
schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] selectRecords;  
  
try  
{  
   Console.WriteLine("Selecting Row...");  
   selectRecords = client.Select("*", "where [Employee_ID] = (select IDENT_CURRENT('Employee'))");  
}  
  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
  
Console.WriteLine("The details of the newly added employee are:");  
Console.WriteLine("********************************************");  
for (int i = 0; i < selectRecords.Length; i++)  
{  
   Console.WriteLine("Employee ID        : " + selectRecords[i].Employee_ID);  
   Console.WriteLine("Employee Name      : " + selectRecords[i].Name);  
   Console.WriteLine("Employee Desigation: " + selectRecords[i].Designation);  
   Console.WriteLine();  
}  
Console.WriteLine("********************************************");  
Console.WriteLine("Press any key to continue ...");  
Console.ReadLine();  
```  
  
###   <a name="update-operation"></a>更新作業  
 下列程式碼會顯示為目標的 Employee 資料表的更新作業。  
  
```  
int result;  
  
schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair updateRecordPair =  
   new schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair();  
  
schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee updateRecord =   
   new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee();  
  
schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair[] updateArray =  
   new schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair[1];  
  
updateRecord = insertRecord[0];  
updateRecord.Name = "Jeff Smith";  
  
updateRecordPair.After = updateRecord;  
updateRecordPair.Before = selectRecords[0];  
  
updateArray[0] = updateRecordPair;  
  
try  
{  
   Console.WriteLine("Updating the database...");  
   result = client.Update(updateArray);  
}  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
  
Console.WriteLine("Updated Record for {0}", updateRecordPair.Before.Name);  
Console.WriteLine("The new name for the employee is {0}", updateRecordPair.After.Name);  
Console.WriteLine("Press any key to continue ...");  
Console.ReadLine();  
```  
  
###   <a name="delete-operation"></a>刪除動作  
 下列程式碼會顯示為目標的 Employee 資料表的刪除作業。  
  
```  
int deleteSuccess;  
  
schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] deleteRecords =  
   new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[1];  
  
deleteRecords = client.Select("*", "where [Employee_ID] = (select IDENT_CURRENT('Employee'))");  
  
Console.WriteLine("Following employees will be deleted from the database:");  
for (int i = 0; i < deleteRecords.Length; i++)  
{  
   Console.WriteLine("Name: {0}", deleteRecords[i].Name);  
}  
Console.WriteLine("Press any key to begin deletion...");  
Console.ReadLine();  
  
try  
{  
   Console.WriteLine("Deleting employee record...");  
   deleteSuccess = client.Delete(deleteRecords);  
}  
  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
[使用 WCF 服務模型開發應用程式](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)