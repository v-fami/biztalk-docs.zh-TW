---
title: "叫用中使用 WCF 服務模型的 SQL 強型別的預存程序 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d56df5f6-b046-4fe4-a5b4-b29906093beb
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 591dd1c42913f44e148cb0c68a084d55f78c4d93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-strongly-typed-stored-procedures-in-sql-using-wcf-service-model"></a>叫用中使用 WCF 服務模型的 SQL 強型別的預存程序
當您叫用底下所列的程序**Strongly-Typed 程序**節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，輸出為強型別之結果集的格式。 本主題提供有關如何建立 WCF 用戶端來叫用傳回強型別之結果集在 SQL Server 預存程序的指示。  
  
> [!NOTE]
>  如果您正在執行具有使用者定義類型的資料行的資料表上的作業，請確定您參考[資料表和檢視表與使用者定義型別上的作業](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md)開始開發應用程式之前。  
  
## <a name="about-the-examples-used-in-this-topic"></a>關於本主題中使用的範例  
 本主題中的範例使用 GET_EMP_DETAILS 預存程序。 這個預存程序會採用員工識別碼當做輸入參數和傳回對應的資料行之員工的該識別碼。 GET_EMP_DETAILS 預存程序會建立執行範例所提供的 SQL 指令碼。 如需有關範例的詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。 範例中， **Execute_TypedStoredProcedure**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 叫用預存程序，在產生 WCF 用戶端的名稱**Strongly-Typed 程序**節點使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]列於下表。  
  
|SQL Server 資料庫成品|WCF 用戶端名稱|  
|----------------------------------|---------------------|  
|程序 (底下**Strongly-Typed 程序**節點)|TypedProcedures_ [schema] 用戶端|  
  
 [結構描述] 是所屬的結構描述的程序。例如"dbo"時。  
  
### <a name="method-signature-for-invoking-stored-procedures"></a>叫用預存程序的方法簽章  
 下表顯示公開的方法來叫用預存程序的簽章。  
  
|作業|方法簽章|  
|---------------|----------------------|  
|程序名稱|[PROC_NS][m](參數 1，參數 2，...\)|  
  
 [PROC_NS] 為程序的命名空間;例如 schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0]  
  
 [m] 是程序; 名稱例如 GET_EMP_DETAILS  
  
 例如，下列程式碼片段顯示 GET_EMP_DETAILS 程序的叫用方法的簽章。  
  
```  
public partial class TypedProcedures_dboClient : System.ServiceModel.ClientBase<TypedProcedures_dbo>, TypedProcedures_dbo{  
public schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0[]   
  GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue);  
}  
```  
  
 在此片段中，  
  
-   `TypedProcedures_dboClient`是類別的名稱。 在此範例中，您可以使用這個類別來建立用戶端叫用預存程序。  
  
-   `public schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0[] GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue)`您在此範例中，叫用的方法來叫用預存程序。 這個預存程序會採用員工識別碼，並傳回強型別之結果集。  
  
## <a name="creating-a-wcf-client-to-invoke-a-stored-procedure-in-sql-server"></a>建立 WCF 用戶端叫用 SQL Server 中的預存程序  
 使用 WCF 用戶端的 SQL Server 上執行作業所需的動作的泛型集合包含一組工作中所述[SQL 配接器的 WCF 服務模型概觀](overview-of-the-wcf-service-model-with-the-sql-adapter.md)。 本節特別說明如何建立 WCF 用戶端叫用預存程序的結果集是強型別。 在本主題中，例如，您叫用 GET_EMP_DETAILS 預存程序。 這個預存程序會建立執行每個範例提供的 SQL 指令碼。  
  
1.  Visual Studio 中建立 Visual C# 專案。 本主題中，建立主控台應用程式。  
  
2.  產生 WCF 用戶端類別，GET_EMP_DETAILS 預存程序。 請確定您選取在程序**Strongly-Typed 程序**節點。 如需產生 WCF 用戶端類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。  
  
    > [!IMPORTANT]
    >  在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。  
  
3.  在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`和`Microsoft.ServiceModel.Channels`。  
  
4.  開啟 Program.cs 檔案並建立用戶端，如以下程式碼片段中所述。  
  
    ```  
  
              TypedProcedures_dboClient client = new TypedProcedures_dboClient("SqlAdapterBinding_TypedProcedures_dbo");  
    client.ClientCredentials.UserName.UserName = "<Enter username here>";  
    client.ClientCredentials.UserName.Password = "<Enter username here>";  
    ```  
  
     在此程式碼片段， `TypedProcedures_dboClient` SqlAdapterBindingClient.cs 中定義之 WCF 用戶端。 這個檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 `SqlAdapterBinding_TypedProcedures_dbo`用戶端端點組態的名稱，而定義在 app.config 中。這個檔案也會產生由[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，其中包含繫結屬性和其他組態設定。  
  
    > [!NOTE]
    >  在此片段中，您從組態檔使用的繫結和端點位址。 您可以同時也可以明確指定這些值，在程式碼中。 如需以不同的方式指定用戶端繫結的詳細資訊，請參閱[設定 SQL 配接器的用戶端繫結](configure-a-client-binding-for-the-sql-adapter.md)。  
  
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
  
6.  以下程式碼片段中所述的 GET_EMP_DETAILS 預存程序來叫用。  
  
    ```  
    // Create array of type as specified in the method signature  
    schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0[] resultSet =  
       new schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0[1];  
    int returnCode;  
  
    try  
    {  
       Console.WriteLine("Calling a stored procedure...");  
       resultSet = client.GET_EMP_DETAILS(10001, out returnCode);  //Invoke the stored procedure  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
    Console.WriteLine("The details for the employee with ID '10001' are:");  
    Console.WriteLine("*************************************************");  
  
    for (int i = 0; i < resultSet.Length; i++)  
       {  
          Console.WriteLine("Employee Name        : " + resultSet[i].Name);  
          Console.WriteLine("Employee Designation : " + resultSet[i].Designation);  
          Console.WriteLine("Employee Salary      : " + resultSet[i].Salary);  
       }  
  
    Console.WriteLine("*************************************************");  
  
    ```  
  
7.  以下程式碼片段中所述，請關閉用戶端：  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  建置專案，然後執行它。 在主控台上顯示名稱、 指定和薪資的員工識別碼。  
  
## <a name="see-also"></a>另請參閱  
[開發應用程式使用 WCF 服務模型](develop-sql-applications-using-the-wcf-service-model.md)