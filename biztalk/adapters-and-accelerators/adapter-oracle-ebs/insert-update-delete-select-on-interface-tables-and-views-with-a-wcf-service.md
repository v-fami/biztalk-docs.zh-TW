---
title: 插入、 更新、 刪除或選取介面資料表和檢視表使用 WCF 服務模型的作業 |Microsoft 文件
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
ms.openlocfilehash: 4fc9e3968b760be10b428e39662ec3d09db490cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218142"
---
# <a name="insert-update-delete-or-select-operations-on-interface-tables-and-views-using-the-wcf-service-model"></a>插入、 更新、 刪除或選取介面資料表和檢視表使用 WCF 服務模型的作業
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]探索一組介面資料表的基本 Insert、 Select、 Update 和 Delete 作業。 藉由使用這些作業，您可以執行簡單的 Insert、 Select、 Update 和 Delete 陳述式 WHERE 子句的目標介面資料表上所限定。 本主題提供有關如何執行這些作業使用 WCF 服務模型的指示。  
  
> [!NOTE]
>  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]只支援選取的介面檢視上的作業。  
  
 如需配接器如何支援這些作業的詳細資訊，請參閱[介面資料表和檢視介面上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)。  
  
## <a name="about-the-examples-used-in-this-topic"></a>關於本主題中使用的範例  
 本主題中的範例執行 MS_SAMPLE_EMPLOYEE 介面資料表上的作業。 執行範例所提供的指令碼會建立資料表。 如需有關範例的詳細資訊，請參閱[Oracle EBS 配接器範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。 範例中， **Interface_Table_Ops**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 WCF 用戶端的基本作業產生的名稱，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會探索下表列出根據資料表或檢視表的名稱。  
  
|成品|WCF 用戶端名稱|  
|--------------|---------------------|  
|介面資料表|InterfaceTables_ [APP_NAME] _ [SCHEMA]\_[TABLE_NAME] 用戶端|  
|介面檢視|InterfaceViews_ [APP_NAME] _ [SCHEMA]\_[VIEW_NAME] 用戶端|  
  
 [APP_NAME] = Oracle E-business Suite 應用程式; 的實際名稱例如，尋找說明。  
  
 [SCHEMA] = 的成品、 集合例如，應用程式。  
  
 [TABLE_NAME] = 表格的名稱例如，MS_SAMPLE_EMPLOYEE。  
  
 [VIEW_NAME] = 檢視; 的名稱例如，MS_SAMPLE_EMPLOYEE_View。  
  
### <a name="method-signature-for-invoking-operations-on-tables"></a>叫用資料表上的作業的方法簽章  
 下表顯示在資料表上的基本作業的方法簽章。 簽章是資料表的不相同的檢視，不同之處在於檢視命名空間和名稱取代。  
  
|作業|方法簽章|  
|---------------|----------------------|  
|Insert|字串插入 (InsertRecord [資料錄集);|  
|Select|SelectRecord [] 選取 （字串 COLUMN_NAMES，字串篩選條件）。|  
|Update|字串更新 （UpdateRecord 資料錄集，篩選條件字串）;|  
|DELETE|刪除 （字串篩選;） 的字串|  
  
 例如，下列程式碼會示範產生 WCF 用戶端類別的方法簽章用於刪除、 插入、 選取和更新作業的預設應用程式結構描述在 MS_SAMPLE_EMPLOYEE 介面資料表上。  
  
```  
public partial class InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient : System.ServiceModel.ClientBase<InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE>, InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE {      
    public SelectRecord[] Select(string COLUMN_NAMES, string FILTER);  
  
    public string Insert(InsertRecord[] RECORDSET);  
  
    public string Update(UpdateRecord RECORDSET, string FILTER);  
  
    public string Delete(string FILTER);  
}  
```  
  
 在此程式碼片段， **InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient**是 WCF 中的類別所產生的 OracleEBSBindingClient.cs 名稱[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
### <a name="parameters-for-table-operations"></a>資料表作業的參數  
 本節提供每個資料表作業所需的參數  
  
 **選取作業**  
  
|COLUMN_NAMES|FILTER|  
|-------------------|------------|  
|目標; 中的資料行名稱以逗號分隔清單例如，"EMP_NO，指定"。 資料行清單中指定的目標所應傳回結果集中的資料行。 未指定資料行清單中的資料行會設定為其傳回的記錄組中的.NET 預設值。 Nillable 資料行，這個值是**null**。|WHERE 子句會指定查詢; 的目標資料列的內容比方說，「 名稱 = 'Manager' 」。 您可以將此參數設定為**null**傳回目標的所有資料列。|  
  
 選取作業的傳回值是強型別結果集，其中包含指定的資料行和資料列。  
  
 **插入作業**  
  
|插入作業類型|資料錄集|  
|---------------------------|---------------|  
|多個記錄|應插入至資料表的 INSERTRECORDS 的集合。|  
  
 插入作業的傳回值會是插入的資料列數目。  
  
 **更新作業**  
  
|資料錄集|FILTER|  
|---------------|------------|  
|應該在資料表中更新的記錄的集合。|WHERE 子句會指定查詢; 的目標資料列的內容比方說，「 名稱 = 'Manager' 」。 您可以將此參數設定為**null**傳回目標的所有資料列。|  
  
 更新作業的傳回值是更新的資料列數目。  
  
 **刪除作業**  
  
 刪除作業會輸入一個 WHERE 子句，指定要刪除的資料列。 刪除作業的傳回值是刪除的資料列數目。  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-interface-tables-and-interface-views"></a>建立 WCF 用戶端來叫用介面資料表上的作業和介面檢視  
 Oracle E-business Suite 使用 WCF 用戶端上執行作業所需動作的泛型集合會包含一組工作中所述[Oracle E-business Suite 配接器的 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md)。 本章節描述如何建立 WCF 用戶端來叫用基本 Insert、 Select、 Update 介面資料表上的刪除作業。  
  
#### <a name="to-create-a-wcf-client-to-perform-operations-on-tables"></a>若要建立 WCF 用戶端在資料表上執行作業  
  
1.  Visual Studio 中建立 Visual C# 專案。 本主題中，建立主控台應用程式。  
  
2.  產生 WCF 用戶端類別的 Insert、 Select、 Update 和刪除 MS_SAMPLE_EMPLOYEE 介面資料表上的作業。 如需產生 WCF 用戶端類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  
  
    > [!IMPORTANT]
    >  在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。  
  
3.  在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`和`Microsoft.ServiceModel.Channels`。  
  
4.  開啟 Program.cs 檔案並加入下列命名空間：  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
5.  開啟 Program.cs 檔案並建立用戶端，如以下程式碼片段中所述。  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
    InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient client = new InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient(binding, address);  
    ```  
  
     在此程式碼片段， `InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEEClient` OracleEBSBindingClient.cs 中定義之 WCF 用戶端。 這個檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
    > [!NOTE]
    >  在此片段中，您明確指定的繫結與端點位址的應用程式程式碼中。 您可以使用這些值從應用程式組態檔 app.config，也是由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需以不同的方式指定用戶端繫結的詳細資訊，請參閱[for Oracle E-business Suite 繫結的用戶端設定](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。  
  
6.  設定用戶端的認證。  
  
    ```  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
7.  因為您正在執行的介面資料表上的作業，您必須設定應用程式內容。 在此範例中，若要設定應用程式內容中，您指定**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。 如需應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
8.  以下程式碼片段中所述，請開啟用戶端：  
  
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
  
     您可以取代上述程式碼片段來執行 Select、 Update 或 Delete 作業，以及。 您也可以附加到單一應用程式的所有執行的程式碼片段。 如需如何執行這些作業程式碼片段，請參閱[選取作業](#BKMK_Select)，[更新作業](#BKMK_Update)，和[刪除作業](#BKMK_Delete)分別。  
  
10. 以下程式碼片段中所述，請關閉用戶端：  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
11. 建置專案，然後執行它。 應用程式 MS_SAMPLE_EMPLOYEE 資料表中插入記錄。  
  
###  <a name="BKMK_Select"></a>選取作業  
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
  
###  <a name="BKMK_Update"></a>更新作業  
 下列程式碼會示範 MS_SAMPLE_EMPLOYEE 介面資料表為目標的更新作業。  
  
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
  
###  <a name="BKMK_Delete"></a>刪除作業  
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