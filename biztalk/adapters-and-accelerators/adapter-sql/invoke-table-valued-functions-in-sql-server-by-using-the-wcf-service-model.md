---
title: 使用 WCF 服務模型來叫用 SQL Server 中的資料表值函式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48688bcc-36b4-4cc1-b078-17e7a5e1cf8c
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a736a82e57f71568f8718a6e4d41e7b649004120
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224694"
---
# <a name="invoke-table-valued-functions-in-sql-server-by-using-the-wcf-service-model"></a>使用 WCF 服務模型來叫用 SQL Server 中的資料表值函式
您可以使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].NET 應用程式使用 WCF 服務模型來叫用 SQL Server 中的資料表值函式中。 配接器會將資料表值函式公開為可直接在 SQL Server 叫用的方法。 如需配接器如何支援純量函數的詳細資訊，請參閱[Execute Table-Valued 函式中使用 SQL 配接器的 SQL Server](../../adapters-and-accelerators/adapter-sql/execute-table-valued-functions-in-sql-server-using-the-sql-adapter.md)。  
  
 本主題示範如何叫用 SQL Server 資料庫中的 TVF_EMPLOYEE 函式。 TVF_EMPLOYEE 函式中的員工的指定**員工**資料表，並傳回員工的記錄。 TVF_EMPLOYEE 函式和**員工**執行範例所提供的 SQL 指令碼會建立資料表。 如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
## <a name="about-the-examples-used-in-this-topic"></a>關於本主題中使用的範例  
 本主題中的範例上叫用 TVF_EMPLOYEE 資料表值函式**員工**資料表。 TVF_EMPLOYEE 函式和**員工**執行範例所提供的 SQL 指令碼會建立資料表。 範例中， **TableFunction_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。 如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 叫用純量函數中使用 SQL Server 產生 WCF 用戶端的名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]列於下表。  
  
|SQL Server 資料庫成品|WCF 用戶端名稱|  
|----------------------------------|---------------------|  
|資料表值函式|TableValuedFunctions_ [SCHEMA] 用戶端|  
  
 [SCHEMA] = 集合 SQL Server 成品。例如，dbo。  
  
### <a name="method-signature-for-invoking-table-valued-functions"></a>方法簽章的叫用資料表值函式  
 下表顯示在資料表上的基本作業的方法簽章。 簽章是資料表的不相同的檢視，不同之處在於檢視命名空間和名稱取代。  
  
|作業|方法簽章|  
|---------------|----------------------|  
|資料表值函式名稱|公用 [命名空間] [FUNCTION_NAME] [] [FUNCTION_NAME] (參數 1，參數 2，...\)|  
  
 [命名空間] = 在命名空間，例如 schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE  
  
 [FUNCTION_NAME] = 資料表值函式的名稱。  
  
 例如，下列程式碼顯示的方法簽章產生 WCF 用戶端類別**TVF_EMPLOYEE** dbo 結構描述中，做為參數指定的員工，然後傳回員工的純量函數資料錄。  
  
```  
public partial class TableValuedFunctions_dboClient : System.ServiceModel.ClientBase<TableValuedFunctions_dbo>, TableValuedFunctions_dbo {      
    public schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE[] TVF_EMPLOYEE(string emp_desig);  
}  
```  
  
 在此程式碼片段， **TableValuedFunctions_dboClient**是 WCF 中的類別所產生的 SqlAdapterBindingClient.cs 名稱[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
### <a name="parameters-for-invoking-table-valued-functions"></a>叫用資料表值函式的參數  
 所公開的方法的參數[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]叫用資料表值函式會在 SQL Server 中的函式定義中定義的參數相同。 例如，叫用 TVF_EMPLOYEE 資料表值函式的參數是 emp_desig，會採用員工的指定。  
  
 同樣地，資料表值函式的傳回值是與 SQL Server 中的函式定義中所定義的傳回值相同。 比方說，TVF_EMPLOYEE 函式的傳回值是陣列的型別 schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE [] 的記錄。  
  
## <a name="creating-a-wcf-client-to-invoke-table-valued-functions"></a>建立 WCF 用戶端來叫用資料表值函式  
 使用 WCF 用戶端的 SQL Server 上執行作業所需的動作的泛型集合包含一組工作中所述[SQL 配接器的 WCF 服務模型概觀](overview-of-the-wcf-service-model-with-the-sql-adapter.md)。 本章節描述如何建立 WCF 用戶端來叫用**TVF_EMPLOYEE**資料表值函式。  
  
 
1.  Visual C# 中建立專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsVStudioNoVersion-md.md)]。 本主題中，建立主控台應用程式。  
  
2.  產生 WCF 用戶端類別**TVF_EMPLOYEE**純量函數。 如需產生 WCF 用戶端類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。  
  
3.  在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`和`Microsoft.ServiceModel.Channels`。  
  
4.  開啟 Program.cs，並建立用戶端，如以下程式碼片段中所述。  
  
    ```  
  
              TableValuedFunctions_dboClient client = new TableValuedFunctions_dboClient("SqlAdapterBinding_TableValuedFunctions_dbo");  
    client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     在此程式碼片段， `TableValuedFunctions_dboClient` SqlAdapterBindingClient.cs 中定義之 WCF 用戶端。 這個檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 `SqlAdapterBinding_TableValuedFunctions_dbo`用戶端端點組態的名稱，而定義在 app.config 中。這個檔案也會產生由[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，其中包含繫結屬性和其他組態設定。  
  
    > [!NOTE]
    >  在此片段中，您從組態檔使用的繫結和端點位址。 您可以同時也可以明確指定這些值，在程式碼中。 如需有關不同的方式，然後指定用戶端繫結的詳細資訊，請參閱[設定 SQL 配接器的用戶端繫結](configure-a-client-binding-for-the-sql-adapter.md)。  
  
5.  以下程式碼片段中所述，請開啟用戶端：  
  
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
  
6.  叫用**TVF_EMPLOYEE**函式可擷取具有 「 管理員 」 指定的所有員工記錄。  
  
    ```  
    Console.WriteLine("Invoking the TVF_EMPLOYEE function");  
    schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE[] emp_details;  
    string emp_designation = "Manager";  
  
    try  
    {  
        emp_details = client.TVF_EMPLOYEE(emp_designation);  
    }  
    catch (Exception e)  
    {  
        Console.WriteLine("Exception: " + e.Message);  
        throw;  
    }  
    Console.WriteLine("The details for the employee with the 'Manager' designation are:");  
    Console.WriteLine("*******************************************************************");  
    for (int i = 0; i < emp_details.Length; i++)  
    {  
        Console.WriteLine("Employee ID        : " + emp_details[i].Employee_ID);  
        Console.WriteLine("Employee Name      : " + emp_details[i].Name);  
        Console.WriteLine("Employee Desigation: " + emp_details[i].Designation);  
        Console.WriteLine("Employee Salary    : " + emp_details[i].Salary);  
        Console.WriteLine();  
    }  
    ```  
  
7.  以下程式碼片段中所述，請關閉用戶端：  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  建置專案，然後執行它。 員工識別碼、 名稱和具有 「 管理員 」 指定的所有員工的薪資，則會顯示應用程式。  
  
## <a name="see-also"></a>另請參閱  
[開發應用程式使用 WCF 服務模型](develop-sql-applications-using-the-wcf-service-model.md)