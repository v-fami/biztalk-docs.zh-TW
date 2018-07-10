---
title: 插入、 更新、 刪除或選取在介面資料表和檢視使用 WCF 服務模型的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae613c0e-4d9a-4c66-99e4-dd0443f1d495
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ed57328a925496449ddd73f3c363b32f60dc811
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983471"
---
# <a name="insert-update-delete-or-select-operations-on-interface-tables-and-views-using-the-wcf-service-model"></a>插入、 更新、 刪除或選取在介面資料表和檢視使用 WCF 服務模型的作業
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]探索一組介面資料表上的基本 Insert、 Select、 Update 和 Delete 作業。 藉由使用這些作業，您可以執行簡單的 Insert、 Select、 Update 和 Delete 陳述式 WHERE 子句的目標介面資料表上所限定。 本主題提供有關如何使用 WCF 服務模型執行這些作業的指示。  

> [!NOTE]
>  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援只選取介面檢視上的作業。  

 如需配接器如何支援這些作業的詳細資訊，請參閱[介面資料表和介面檢視上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)。  

## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例會執行 MS_SAMPLE_EMPLOYEE 介面資料表上的作業。 執行提供的範例指令碼會建立資料表。 如需有關範例的詳細資訊，請參閱 < [Oracle EBS 配接器的範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。 範例中， **Interface_Table_Ops**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。  

## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 WCF 用戶端的基本作業產生的名稱，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會探索下表所示，為基礎的資料表或檢視的名稱。  


|     成品     |                     WCF 用戶端名稱                      |
|------------------|----------------------------------------------------------|
| 介面資料表 | InterfaceTables_[APP_NAME]*[SCHEMA]\\*[TABLE_NAME]Client |
| 介面檢視  |  InterfaceViews_[APP_NAME]*[SCHEMA]\\*[VIEW_NAME]Client  |

 [APP_NAME>] = [Oracle E-business Suite 應用程式的實際名稱例如，尋找說明。  

 [SCHEMA] = 的成品、 集合例如，應用程式。  

 [TABLE_NAME] = 資料表的名稱比方說，MS_SAMPLE_EMPLOYEE。  

 [VIEW_NAME] = 檢視; 的名稱比方說，MS_SAMPLE_EMPLOYEE_View。  

### <a name="method-signature-for-invoking-operations-on-tables"></a>叫用資料表上的作業的方法簽章  
 下表顯示在資料表上的基本作業的方法簽章。 簽章也適用於檢視中，不同之處在於檢視命名空間和名稱取代的資料表。  

|作業|方法簽章|  
|---------------|----------------------|  
|Insert|string Insert(InsertRecord[] RECORDSET);|  
|Select|SelectRecord[] Select(string COLUMN_NAMES, string FILTER);|  
|Update|string Update(UpdateRecord RECORDSET, string FILTER);|  
|DELETE|string Delete(string FILTER);|  

 例如，下列程式碼顯示產生的 WCF 用戶端類別的方法簽章用於刪除、 插入、 選取及更新的預設應用程式結構描述在 MS_SAMPLE_EMPLOYEE 介面資料表上的作業。  

```  
public partial class InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient : System.ServiceModel.ClientBase<InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE>, InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE {      
    public SelectRecord[] Select(string COLUMN_NAMES, string FILTER);  

    public string Insert(InsertRecord[] RECORDSET);  

    public string Update(UpdateRecord RECORDSET, string FILTER);  

    public string Delete(string FILTER);  
}  
```  

 在此片段中， **InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient**是 WCF 中類別的名稱所產生 OracleEBSBindingClient.cs [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  

### <a name="parameters-for-table-operations"></a>資料表作業的參數  
 本節提供每個資料表作業所需的參數  

 **選取作業**  

|COLUMN_NAMES|FILTER|  
|-------------------|------------|  
|目標; 中的資料行名稱的逗號分隔清單例如，"EMP_NO，指定"。 資料行清單中指定目標應該在結果集中傳回之資料的行。 未指定資料行清單中的資料行，將設為.NET 預設值在傳回的記錄集內。 Nillable 的資料行，這個值是**null**。|WHERE 子句，指定查詢; 的目標資料列的內容比方說，「 名稱 = 'Manager' 」。 您可以將此參數設定為**null**傳回目標的所有資料列。|  

 選取作業的傳回值是強型別結果集，其中包含指定的資料行和資料列。  

 **插入作業**  

|插入作業類型|資料錄集|  
|---------------------------|---------------|  
|多個記錄|應該插入至資料表的 INSERTRECORDS 的集合。|  

 插入作業的傳回值會是插入資料列數目。  

 **更新作業**  

|資料錄集|FILTER|  
|---------------|------------|  
|應該在資料表中更新的記錄的集合。|WHERE 子句，指定查詢; 的目標資料列的內容比方說，「 名稱 = 'Manager' 」。 您可以將此參數設定為**null**傳回目標的所有資料列。|  

 更新作業的傳回值已更新的資料列數目。  

 **刪除作業**  

 刪除作業會採用做為輸入 WHERE 子句，指定要刪除的資料列。 刪除作業的傳回值是已刪除的資料列數目。  

## <a name="creating-a-wcf-client-to-invoke-operations-on-interface-tables-and-interface-views"></a>建立 WCF 用戶端來叫用在介面資料表上的作業和介面檢視  
 一組標準的 Oracle E-business Suite 使用 WCF 用戶端上執行作業所需的動作牽涉到一組工作中所述[Oracle E-business Suite 配接器的 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md)。 本節說明如何建立 WCF 用戶端來叫用基本 Insert、 Select、 Update 介面資料表上的刪除作業。  

#### <a name="to-create-a-wcf-client-to-perform-operations-on-tables"></a>若要建立的 WCF 用戶端，在資料表上執行作業  

1. Visual Studio 中建立 Visual C# 專案。 本主題中，建立主控台應用程式。  

2. 為 Insert、 Select、 Update、 產生 WCF 用戶端類別，並刪除 MS_SAMPLE_EMPLOYEE 介面資料表上的作業。 如需有關如何產生 WCF 用戶端類別的詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Oracle E-business Suite 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  

   > [!IMPORTANT]
   >  在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。  

3. 在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`和`Microsoft.ServiceModel.Channels`。  

4. 開啟 Program.cs 檔案並新增下列命名空間：  

   -   `Microsoft.Adapters.OracleEBS`  

   -   `System.ServiceModel`  

5. 開啟 Program.cs 檔案，並建立用戶端，如下列程式碼片段中所述。  

   ```  
   OracleEBSBinding binding = new OracleEBSBinding();  
   EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
   InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient client = new InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient(binding, address);  
   ```  

    在此片段中， `InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient` OracleEBSBindingClient.cs 中定義之 WCF 用戶端。 此檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  

   > [!NOTE]
   >  在此片段中，您明確指定的繫結與端點位址在您的應用程式程式碼。 您可以使用這些值，從應用程式組態檔 app.config，也產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需有關指定用戶端繫結的不同方式的詳細資訊，請參閱[設定用戶端 for Oracle E-business Suite 繫結](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。  

6. 設定用戶端的認證。  

   ```  
   client.ClientCredentials.UserName.UserName = "myuser";  
   client.ClientCredentials.UserName.Password = "mypassword";  
   ```  

7. 因為您正在執行的介面資料表上的作業，您必須設定應用程式內容。 在此範例中，若要設定應用程式內容中，您指定**OracleUserName**， **OraclePassword**，並**OracleEBSResponsibilityName**繫結屬性。 如需有關應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  

   ```  
   binding.OracleUserName = "myOracleEBSUserName";  
   binding.OraclePassword = "myOracleEBSPassword";  
   binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
   ```  

8. 下列程式碼片段中所述，請開啟用戶端：  

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

9. 叫用 MS_SAMPLE_EMPLOYEE 資料表的 Insert 作業。  

    ```  
    Console.WriteLine("The application will insert a record in the MS_SAMPLE_EMPLOYEE interface table");  

    // The date values cannot contain time zone information. Hence, you must use  
    // DateTimeKind.Unspecified to not include the time zone information.  
    DateTime date = new DateTime(DateTime.Now.Ticks, DateTimeKind.Unspecified);  

    string result;  

    InsertRecord[] recordSet = new InsertRecord[1];  

    EMP_NO__COMPLEX_TYPE emp_no = new EMP_NO__COMPLEX_TYPE();  
    emp_no.Value = "10007";  

    NAME__COMPLEX_TYPE name = new NAME__COMPLEX_TYPE();  
    name.Value = "John Smith";  

    DESIGNATION__COMPLEX_TYPE desig = new DESIGNATION__COMPLEX_TYPE();  
    desig.Value = "Manager";  

    SALARY__COMPLEX_TYPE salary = new SALARY__COMPLEX_TYPE();  
    salary.Value = "500000";  

    JOIN_DATE__COMPLEX_TYPE doj = new JOIN_DATE__COMPLEX_TYPE();  
    doj.Value = date;  

    recordSet[0] = new InsertRecord();  
    recordSet[0].EMP_NO = emp_no;  
    recordSet[0].NAME = name;  
    recordSet[0].DESIGNATION = desig;  
    recordSet[0].SALARY = salary;  
    recordSet[0].JOIN_DATE = doj;  

    try  
    {  
       result = client.Insert(recordSet);   
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  

    Console.WriteLine("Number of records inserted= " + result);  
    Console.WriteLine("Press any key to continue...");  
    Console.ReadLine();  

    ```  

     您可以取代上述程式碼片段來執行 Select、 Update 或 Delete 作業，以及。 您也可以附加到在單一應用程式中執行所有作業的程式碼片段。 如需如何執行這些作業的程式碼片段，請參閱 <<c0> [ 選取作業](#BKMK_Select)，[更新作業](#BKMK_Update)，並[Delete 作業](#BKMK_Delete)分別。  

10. 下列程式碼片段中所述，請關閉該用戶端：  

    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  

11. 建置專案，然後執行它。 應用程式將 MS_SAMPLE_EMPLOYEE 資料表中插入一筆記錄。  

###  <a name="BKMK_Select"></a> 選取作業  
 下列程式碼會顯示目標 MS_SAMPLE_EMPLOYEE 介面資料表的選取作業。 選取的作業選取插入至資料表的最後一個記錄。 傳回的記錄會寫入至主控台。  

```  
Console.WriteLine("The application will now select the last inserted record");  
SelectRecord[] selectRecords;  
try  
{  
   selectRecords = client.Select("*", "WHERE EMP_NO LIKE 10007");  
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
   Console.WriteLine("Employee ID         : " + selectRecords[i].EMP_NO);  
   Console.WriteLine("Employee Name       : " + selectRecords[i].NAME);  
   Console.WriteLine("Employee Desigation : " + selectRecords[i].DESIGNATION);  
   Console.WriteLine("Employee Salary     : " + selectRecords[i].SALARY);  
   Console.WriteLine();  
}  
Console.WriteLine("********************************************");  
Console.WriteLine("Press any key to continue ...");  
Console.ReadLine();  
```  

###  <a name="BKMK_Update"></a> 更新作業  
 下列程式碼會顯示目標 MS_SAMPLE_EMPLOYEE 介面資料表的更新作業。  

```  
Console.WriteLine("The application will now update the employee name in the newly inserted record");  
string recordsUpdated;  
UpdateRecord updateRecordSet = new UpdateRecord();  
updateRecordSet.NAME = "Tom Smith";  
updateRecordSet.DESIGNATION = "Accountant";  

try  
{  
   recordsUpdated = client.Update(updateRecordSet, "WHERE EMP_NO LIKE 10007");  
}  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  

Console.WriteLine("No of records updated: " + recordsUpdated);  
Console.WriteLine("Press any key to continue...");  
Console.ReadLine();  
```  

###  <a name="BKMK_Delete"></a> 刪除作業  
 下列程式碼會顯示目標 MS_SAMPLE_EMPLOYEE 介面資料表的刪除作業。  

```  
Console.WriteLine("The sample will now delete the record that it first inserted");  
string deletedRecords;  
try  
{  
   deletedRecords = client.Delete("WHERE EMP_NO LIKE 10007");  
}  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
Console.WriteLine("No of records deleted: " + deletedRecords);  
Console.WriteLine("Press any key to exit...");  
Console.ReadLine();  
```  

## <a name="see-also"></a>另請參閱  
 [開發 Oracle E-business Suite 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)