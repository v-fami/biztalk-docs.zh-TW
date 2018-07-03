---
title: 使用 WCF 服務模型叫用 SQL Server 中的純量函式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a331e275-3c81-41a8-9ba1-3a801ebc259a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d26d2a7b13804f621b04484f2466af727b8fbf26
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998591"
---
# <a name="invoke-scalar-functions-in-sql-server-by-using-the-wcf-service-model"></a>使用 WCF 服務模型叫用 SQL Server 中的純量函式
您可以使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]在.NET 應用程式中使用 WCF 服務模型，來叫用 SQL Server 中的純量函式。 配接器會公開純量函式為可以直接在 SQL Server 叫用的方法。 如需配接器如何支援純量函式的詳細資訊，請參閱[執行 SQL Server 使用 SQL 配接器中的純量函式](../../adapters-and-accelerators/adapter-sql/execute-scalar-functions-in-sql-server-using-the-sql-adapter.md)。  

## <a name="how-this-topic-demonstrates-invoking-scalar-functions-using-the-wcf-service-model"></a>本主題示範叫用使用 WCF 服務模型的純量函式  
 本主題示範如何叫用 GET_EMP_ID 函式，SQL Server 資料庫中。 GET_EMP_ID 函式中的員工的表示法**員工**資料表，並傳回對應的員工識別碼。 GET_EMP_ID 函式和**員工**執行提供的範例 SQL 指令碼會建立資料表。 如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  

## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例會叫用 [員工] 資料表上的 GET_EMP_ID 純量函式。 GET_EMP_ID 函式和**員工**執行提供的範例 SQL 指令碼會建立資料表。 範例中， **ScalarFunction_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。 如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  

## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 叫用純量函式，在 SQL Server 中使用產生的 WCF 用戶端名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會列在下表。  

|SQL Server 資料庫成品|WCF 用戶端名稱|  
|----------------------------------|---------------------|  
|純量函數|ScalarFunctions_ [SCHEMA] 用戶端|  

 [SCHEMA] = Collection 的 SQL Server 成品、比方說，dbo。  

### <a name="method-signature-for-invoking-scalar-functions"></a>叫用純量函式的方法簽章  
 下表顯示在資料表上的基本作業的方法簽章。 簽章也適用於檢視中，不同之處在於檢視命名空間和名稱取代的資料表。  


|      作業       |                             方法簽章                             |
|----------------------|--------------------------------------------------------------------------|
| 純量函式名稱 | 公用 *< return_type >*<em>< scalar_function_name ></em>(參數 1，參數 2，...) |

 \<*retrun_type* \> = 函式定義中所定義的傳回型別  

 \<*scalar_function_name* \> = 純量函式的名稱。  

 例如，下列程式碼顯示的方法簽章產生 WCF 用戶端類別**GET_EMP_ID** dbo 結構描述，它會做為參數指定的員工，並傳回員工識別碼 （中的純量函式整數）。  

```  
public partial class ScalarFunctions_dboClient : System.ServiceModel.ClientBase<ScalarFunctions_dbo>, ScalarFunctions_dbo {      
    public System.Nullable<int> GET_EMP_ID(string emp_desig);  
}  
```  

 在此片段中， **ScalarFunctions_dboClient**是 WCF 中類別的名稱所產生 SqlAdapterBindingClient.cs [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  

### <a name="parameters-for-invoking-scalar-functions"></a>叫用純量函式的參數  
 所公開的方法的參數[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]叫用純量函式會在 SQL Server 中的純量函式定義中定義的參數相同。 例如，叫用 GET_EMP_ID 純量函式的參數是 emp_desig，而會採用員工的名稱。  

 同樣地，純量函式的傳回值，等於是在 SQL Server 純量函式定義中所定義的傳回值。 比方說，GET_EMP_ID 函式的傳回值是整數類型的員工識別碼。  

## <a name="creating-a-wcf-client-to-invoke-scalar-functions"></a>建立 WCF 用戶端來叫用純量函式  
 一組標準的 SQL Server 使用 WCF 用戶端上執行作業所需的動作牽涉到一組工作中所述[使用 SQL 配接器的 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md)。 本節說明如何建立 WCF 用戶端來叫用**GET_EMP_ID**純量函式。  

#### <a name="to-create-a-wcf-client"></a>若要建立的 WCF 用戶端  

1. Visual C# 中建立的專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 本主題中，建立主控台應用程式。  

2. 產生 WCF 用戶端類別，如**GET_EMP_ID**純量函式。 如需有關如何產生 WCF 用戶端類別的詳細資訊，請參閱 <<c0> [ 產生的 SQL Server 成品的 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。  

3. 在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`和`Microsoft.ServiceModel.Channels`。  

4. 開啟 Program.cs，並建立用戶端，如下列程式碼片段中所述。  

   ```  

             ScalarFunctions_dboClient client = new ScalarFunctions_dboClient("SqlAdapterBinding_ScalarFunctions_dbo");  
   client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
   client.ClientCredentials.UserName.Password = "<Enter password here>";  
   ```  

    在此片段中， `ScalarFunctions_dboClient` SqlAdapterBindingClient.cs 中定義之 WCF 用戶端。 此檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 `SqlAdapterBinding_ScalarFunctions_dbo` 是用戶端端點組態名稱，並在 app.config 中定義。此檔案也會產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，其中包含繫結屬性和其他組態設定。  

   > [!NOTE]
   >  在此片段中，您使用的繫結和端點位址從組態檔。 您也可以明確指定這些值在您的程式碼。 如需有關不同的方式，然後指定用戶端繫結的詳細資訊，請參閱[設定 SQL 配接器的用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)。  

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

6. 叫用**GET_EMP_ID**函式來擷取指定為 「 經理 」 的員工識別碼。  

   ```  
   Console.WriteLine("Invoking the GET_EMP_ID function");  
   string emp_designation = "Manager";  
   try  
   {  
         System.Nullable<int> emp_id = client.GET_EMP_ID(emp_designation);  
         Console.WriteLine("The Employee ID for the employee with 'Manager' designation is:" + emp_id);  
   }  
   catch (Exception e)  
   {  
         Console.WriteLine("Exception: " + e.Message);  
         throw;  
   }  
   ```  

   > [!NOTE]
   >  為了簡單起見，**員工**資料表有只有一個具有 「 管理員 」 指定的員工。 如果您的目標資料表具有相同名稱的更多員工，您必須據以定義函式。  

7. 下列程式碼片段中所述，請關閉該用戶端：  

   ```  
   client.Close();  
   Console.WriteLine("Press any key to exit...");  
   Console.ReadLine();  
   ```  

8. 建置專案，然後執行它。 應用程式會顯示具有 「 管理員 」 指定員工的員工識別碼。  

## <a name="see-also"></a>另請參閱  
[使用 WCF 服務模型開發應用程式](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)