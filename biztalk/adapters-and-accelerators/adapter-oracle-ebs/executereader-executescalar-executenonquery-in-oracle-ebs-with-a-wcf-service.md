---
title: ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業中使用 WCF 服務模型的 Oracle E-business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 54c42db1-9a4d-4003-af69-f75ff48b575a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0286de636c2ad9fb50fabafe73b5257d18cf70b2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993175"
---
# <a name="executereader-executescalar-or-executenonquery-operations-in-oracle-e-business-suite-using-the-wcf-service-model"></a>使用 WCF 服務模型的 Oracle E-business Suite 中的 ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會公開一般作業時，這類**ExecuteNonQuery**， **ExecuteReader**，和**ExecuteScalar**。 Oracle E-business Suite 上執行任何陳述式，您可以使用這些作業。 這些作業根據回應您取得陳述式的類型而有所不同。 如需配接器如何支援這些作業的詳細資訊，請參閱[支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。  
  
 本主題示範如何執行**ExecuteReader**作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用 WCF 服務模型。 您可以依照程序中執行本主題所述的同一組**ExecuteNonQuery**並**ExecuteScalar**作業。  
  
## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例會執行**ExecuteReader**執行 MS_SAMPLE_EMPLOYEE 介面資料表上的選取作業的作業。 執行提供的範例指令碼會建立資料表。 如需有關範例的詳細資訊，請參閱 < [Oracle EBS 配接器的範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。 範例中， **ExecuteReader**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 叫用泛型作業 （ExecuteNonQuery、 ExecuteReader、 ExecuteScalar） 使用或產生 WCF 用戶端的名稱[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會列在下表。  
  
|作業|WCF 用戶端名稱|  
|----------------|---------------------|  
|ExecuteNonQuery、 ExecuteReader 或 ExecuteScalar|GenericOperation_Client|  
  
### <a name="method-signature-for-invoking-generic-operations"></a>叫用泛型作業的方法簽章  
 下表來叫用泛型作業所公開的方法的簽章。  
  
|作業|方法簽章|  
|---------------|----------------------|  
|ExecuteNonQuery|int ExecuteNonQuery （字串查詢，string [] OutputRefCursorNames，System.Data.DataSet [] OutputRefCursors out）|  
|ExecuteReader|System.Data.DataSet ExecuteReader(string Query)|  
|ExecuteScalar|字串 ExecuteScalar(string Query)|  
  
 例如，泛型作業方法的簽章會顯示下列程式碼片段。  
  
```  
public partial class GenericOperation_Client : System.ServiceModel.ClientBase<GenericOperation_>, GenericOperation_ {  
  public int ExecuteNonQuery(string Query, string[] OutputRefCursorNames, out System.Data.DataSet[] OutputRefCursors);  
  public System.Data.DataSet ExecuteReader(string Query);  
  public string ExecuteScalar(string Query);  
}  
```  
  
 在此片段中，  
  
-   `GenericOperation_Client` 是類別的名稱。 這個類別用來建立用戶端來叫用泛型作業，也就是 ExecuteReader。  
  
-   `public System.Data.DataSet ExecuteReader(string Query)` 是您 MS_SAMPLE_EMPLOYEE 介面資料表上執行 SELECT 陳述式來叫用的方法。  
  
## <a name="creating-a-wcf-client-to-invoke-an-executereader-operation"></a>建立 WCF 用戶端來叫用 ExecuteReader 操作  
 一組標準的 Oracle E-business Suite 使用 WCF 用戶端上執行作業所需的動作牽涉到一組工作中所述[Oracle E-business Suite 配接器的 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md)。 本節說明如何建立 WCF 用戶端來叫用**ExecuteReader**作業。  
  
#### <a name="to-create-a-wcf-client-to-invoke-executereader-operation"></a>若要建立 WCF 用戶端叫用 ExecuteReader 操作  
  
1. Visual Studio 中建立 Visual C# 專案。 本主題中，建立主控台應用程式。  
  
2. 產生 WCF 用戶端類別，如**ExecuteReader**一般作業。 這項作業是可用的根節點下，當您連接到 Oracle E-business Suite 使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需有關如何產生 WCF 用戶端類別的詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Oracle E-business Suite 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  
  
   > [!IMPORTANT]
   >  在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。  
  
3. 在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`和`Microsoft.ServiceModel.Channels`。  
  
4. 開啟 Program.cs 檔案並新增下列命名空間：  
  
   -   `Microsoft.Adapters.OracleEBS`  
  
   -   `System.ServiceModel`  
  
5. 在 Program.cs 檔案中，建立用戶端，如下列程式碼片段中所述。  
  
   ```  
   OracleEBSBinding binding = new OracleEBSBinding();  
   EndpointAddress address = new EndpointAddress("oracleebs://ebs-72-11");  
   GenericOperation_Client client = new GenericOperation_Client(binding, address);  
   ```  
  
    在此片段中， `GenericOperation_Client` OracleEBSBindingClient.cs 中定義之 WCF 用戶端。 此檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
   > [!NOTE]
   >  在此片段中，您明確指定的繫結與端點位址在您的應用程式程式碼。 您可以使用這些值，從應用程式組態檔 app.config，也產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需指定用戶端繫結的不同方式的詳細資訊，請參閱[設定用戶端 for Oracle E-business Suite 繫結](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。  
  
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
  
9. 叫用**ExecuteReader**執行 MS_SAMPLE_EMPLOYEE 資料表上的選取作業的作業。 您可以叫用 ExecuteReader 操作之前，您必須新增`System.Data`您的程式碼的命名空間。  
  
    ```  
    string query = "SELECT * FROM MS_SAMPLE_EMPLOYEE";  
    DataSet ds = client.ExecuteReader(query);  
  
    Console.WriteLine("Invoking the SELECT statement using ExecuteReader");  
    Console.WriteLine("*****************************************************");  
    foreach (DataTable tab in ds.Tables)  
    {  
       foreach (DataRow row in tab.Rows)  
       {  
          Console.WriteLine("The details of the employee are: ");  
          for (int i = 0; i < tab.Columns.Count; i++)  
          {  
             Console.WriteLine(row[i]);  
          }  
          Console.WriteLine();  
       }  
    }  
    Console.WriteLine("*****************************************************");  
    Console.ReadLine();  
  
    ```  
  
10. 下列程式碼片段中所述，請關閉該用戶端：  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
11. 建置專案，然後執行它。 MS_SAMPLE_EMPLOYEE 資料表中的所有記錄會都顯示在主控台上。  
  
## <a name="see-also"></a>另請參閱  
 [開發 Oracle E-business Suite 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)