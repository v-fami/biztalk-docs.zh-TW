---
title: 叫用弱型別預存程序在 SQL 中使用 WCF 服務模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aaf74a40-4c03-4a4a-9b91-c21babe154fa
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6cc2e477aaf5ee113f6479559c23d184e91d905f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012071"
---
# <a name="invoke-weakly-typed-stored-procedures-in-sql-using-the-wcf-service-model"></a>叫用弱型別預存程序中使用 WCF 服務模型的 SQL
當您叫用底下所列的程序**程序**中的節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，輸出是資料集陣列的形式。 本主題提供有關如何建立 WCF 用戶端來叫用傳回的資料集陣列的 SQL Server 中的預存程序的指示。  
  
> [!NOTE]
>  如果您正在執行具有使用者定義類型的資料行的資料表上的作業，請確定您參考[資料表和檢視與使用 SQL 配接器的使用者定義型別上的作業](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md)開始開發您的應用程式之前。  
  
## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例使用 GET_EMP_DETAILS 預存程序。 此預存程序會採用員工識別碼做為輸入參數，並傳回具有該識別碼之員工的所有對應的資料行 GET_EMP_DETAILS 預存程序會建立執行 SQL 指令碼提供範例。 如需有關範例的詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。 範例中， **Execute_StoredProc**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 叫用預存程序，在產生 WCF 用戶端的名稱**程序**節點使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會列在下表。  
  
|SQL Server 資料庫成品|WCF 用戶端名稱|  
|----------------------------------|---------------------|  
|程序 (底下**程序**節點)|Procedures_ [schema] 用戶端|  
  
 [結構描述] 是所屬的結構描述的程序;例如"dbo"時。  
  
### <a name="method-signature-for-invoking-stored-procedures"></a>叫用預存程序的方法簽章  
 下表顯示要叫用預存程序所公開的方法的簽章。  
  
|作業|方法簽章|  
|---------------|----------------------|  
|程序名稱|System.Data.DataSet [] [程序名稱] (參數 1，參數 2，...\)|  
  
 [程序名稱] 是程序; 名稱比方說 GET_EMP_DETAILS  
  
 例如，下列程式碼片段顯示 GET_EMP_DETAILS 程序的叫用方法的簽章。  
  
```  
public partial class Procedures_dboClient : System.ServiceModel.ClientBase<Procedures_dbo>, Procedures_dbo {  
  public System.Data.DataSet[] GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue);  
}  
```  
  
 在此片段中，  
  
-   `Procedures_dboClient` 是 WCF 用戶端類別的名稱。 在此範例中，您可以使用這個類別來建立用戶端來叫用預存程序。  
  
-   `public System.Data.DataSet[] GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue)` 是您在此範例中，叫用的方法來叫用預存程序。 這個預存程序會採用員工識別碼，並傳回資料集的陣列。  
  
## <a name="create-a-wcf-client-to-invoke-a-stored-procedure-in-sql-server"></a>建立 WCF 用戶端叫用 SQL Server 中的預存程序  
 一組標準的 SQL Server 使用 WCF 用戶端上執行作業所需的動作牽涉到一組工作中所述[配接器的 WCF 服務模型的概觀](overview-of-the-wcf-service-model-with-the-sql-adapter.md)。 本節特別說明如何建立 WCF 用戶端叫用預存程序的結果集資料集的陣列。 在本主題中，例如，您叫用 GET_EMP_DETAILS 預存程序。 這個預存程序會建立執行 SQL 指令碼提供每個範例。  
  
  
1. Visual Studio 中建立 Visual C# 專案。 本主題中，建立主控台應用程式。  
  
2. 產生 WCF 用戶端類別，如 GET_EMP_DETAILS 預存程序。 請確定您選取下的程序**程序**節點。 如需有關如何產生 WCF 用戶端類別的詳細資訊，請參閱 <<c0> [ 產生的 SQL Server 成品的 WCF 用戶端或 WCF 服務合約](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。  
  
   > [!IMPORTANT]
   >  在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。  
  
3. 在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`和`Microsoft.ServiceModel.Channels`。  
  
4. 開啟 Program.cs 檔案，並建立用戶端，如下列程式碼片段中所述。  
  
   ```  
  
             Procedures_dboClient client = new Procedures_dboClient("SqlAdapterBinding_Procedures_dbo");  
  
   client.ClientCredentials.UserName.UserName = "<Enter username here>";  
   client.ClientCredentials.UserName.Password = "<Enter password here>";  
   ```  
  
    在此片段中， `Procedures_dboClient` SqlAdapterBindingClient.cs 中定義之 WCF 用戶端。 此檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 `SqlAdapterBinding_Procedures_dbo` 是用戶端端點組態名稱，並在 app.config 中定義。此檔案也會產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，其中包含繫結屬性和其他組態設定。  
  
   > [!NOTE]
   >  在此片段中，您使用的繫結和端點位址從組態檔。 您也可以明確指定這些值在您的程式碼。 如需有關指定用戶端繫結的不同方式的詳細資訊，請參閱[設定 SQL 配接器的用戶端繫結](configure-a-client-binding-for-the-sql-adapter.md)。  
  
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
  
6. 叫用 GET_EMP_DETAILS 預存程序。 您可以叫用 GET_EMP_DETAILS 程序之前，您必須新增`System.Data`您的程式碼的命名空間。  
  
   ```  
   DataSet[] dataArray;  
   int returnCode;  
  
   try  
   {  
      Console.WriteLine("Calling a stored procedure...");  
      dataArray = client.GET_EMP_DETAILS(10001, out returnCode);  //Invoke the stored procedure  
   }  
   catch (Exception ex)  
   {  
      Console.WriteLine("Exception: " + ex.Message);  
      throw;  
   }  
   Console.WriteLine("The details for the employee with ID '10001' are:");  
   Console.WriteLine("*************************************************");  
  
   foreach (DataSet dataSet in dataArray)  
   {  
      foreach (DataTable tab in dataArray[0].Tables)  
      {  
         foreach (DataRow row in tab.Rows)  
         {  
            for (int i = 0; i < tab.Columns.Count; i++)  
            {  
               Console.WriteLine(row[i]);  
            }  
         }  
      }  
   }  
   Console.WriteLine("*************************************************");  
  
   ```  
  
7. 下列程式碼片段中所述，請關閉該用戶端：  
  
   ```  
   client.Close();  
   Console.WriteLine("Press any key to exit...");  
   Console.ReadLine();  
   ```  
  
8. 建置專案，然後執行它。 員工，為哪些您提取要求詳細資料
9. ovided 識別碼，會顯示在主控台上。  
  
## <a name="see-also"></a>另請參閱  
[使用 WCF 服務模型開發應用程式](develop-sql-applications-using-the-wcf-service-model.md)