---
title: ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業中使用 WCF 服務模型的 Oracle E-business Suite |Microsoft 文件
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
ms.openlocfilehash: eaffcdc59cd6093feababc8319c1f9f1964a0d05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217382"
---
# <a name="executereader-executescalar-or-executenonquery-operations-in-oracle-e-business-suite-using-the-wcf-service-model"></a>ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery Oracle E-business Suite 使用 WCF 服務模型中的作業
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開一般作業，例如**ExecuteNonQuery**， **ExecuteReader**，和**ExecuteScalar**。 您可以使用這些作業來執行 Oracle E-business suite 的任何陳述式。 這些作業根據回應您取得陳述式的類型而有所不同。 如需配接器如何支援這些作業的詳細資訊，請參閱[ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業支援](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。  
  
 本主題示範如何執行**ExecuteReader**作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用 WCF 服務模型。 您可以依照程序中執行本主題所述的同一組**ExecuteNonQuery**和**ExecuteScalar**作業。  
  
## <a name="about-the-examples-used-in-this-topic"></a>關於本主題中使用的範例  
 本主題中的範例執行**ExecuteReader**執行 MS_SAMPLE_EMPLOYEE 介面資料表上的選取作業的作業。 執行範例所提供的指令碼會建立資料表。 如需有關範例的詳細資訊，請參閱[Oracle EBS 配接器範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。 範例中， **ExecuteReader**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 叫用泛型作業 （ExecuteNonQuery、 ExecuteReader 或 ExecuteScalar） 使用產生 WCF 用戶端的名稱[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]列於下表。  
  
|作業|WCF 用戶端名稱|  
|----------------|---------------------|  
|ExecuteNonQuery、 ExecuteReader 或 ExecuteScalar|GenericOperation_Client|  
  
### <a name="method-signature-for-invoking-generic-operations"></a>叫用泛型作業的方法簽章  
 下表顯示公開的方法來叫用泛型作業簽章。  
  
|作業|方法簽章|  
|---------------|----------------------|  
|ExecuteNonQuery|int ExecuteNonQuery （string [] OutputRefCursorNames，System.Data.DataSet [] OutputRefCursors 出查詢字串）|  
|ExecuteReader|System.Data.DataSet ExecuteReader(string Query)|  
|ExecuteScalar|字串 ExecuteScalar(string Query)|  
  
 為例，下列程式碼片段顯示的一般操作方法的簽章。  
  
```  
public partial class GenericOperation_Client : System.ServiceModel.ClientBase<GenericOperation_>, GenericOperation_ {  
  public int ExecuteNonQuery(string Query, string[] OutputRefCursorNames, out System.Data.DataSet[] OutputRefCursors);  
  public System.Data.DataSet ExecuteReader(string Query);  
  public string ExecuteScalar(string Query);  
}  
```  
  
 在此片段中，  
  
-   `GenericOperation_Client`是類別的名稱。 這個類別用來建立用戶端來叫用泛型作業 ExecuteReader。  
  
-   `public System.Data.DataSet ExecuteReader(string Query)`是您在 MS_SAMPLE_EMPLOYEE 介面資料表上執行 SELECT 陳述式來叫用的方法。  
  
## <a name="creating-a-wcf-client-to-invoke-an-executereader-operation"></a>建立 WCF 用戶端來叫用 ExecuteReader 作業  
 Oracle E-business Suite 使用 WCF 用戶端上執行作業所需動作的泛型集合會包含一組工作中所述[Oracle E-business Suite 配接器的 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md)。 本章節描述如何建立 WCF 用戶端來叫用**ExecuteReader**作業。  
  
#### <a name="to-create-a-wcf-client-to-invoke-executereader-operation"></a>若要建立 WCF 用戶端來叫用 ExecuteReader 作業  
  
1.  Visual Studio 中建立 Visual C# 專案。 本主題中，建立主控台應用程式。  
  
2.  產生 WCF 用戶端類別**ExecuteReader**一般作業。 當您連接到 Oracle E-business Suite 使用這項作業是在根節點下，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需產生 WCF 用戶端類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  
  
    > [!IMPORTANT]
    >  在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。  
  
3.  在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`和`Microsoft.ServiceModel.Channels`。  
  
4.  開啟 Program.cs 檔案並加入下列命名空間：  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
5.  在 Program.cs 檔案中，建立用戶端，如以下程式碼片段中所述。  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs-72-11");  
    GenericOperation_Client client = new GenericOperation_Client(binding, address);  
    ```  
  
     在此程式碼片段， `GenericOperation_Client` OracleEBSBindingClient.cs 中定義之 WCF 用戶端。 這個檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
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
  
9. 叫用**ExecuteReader**執行 MS_SAMPLE_EMPLOYEE 資料表上的選取作業的作業。 您叫用 ExecuteReader 操作之前，您必須加入`System.Data`您的程式碼的命名空間。  
  
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
  
10. 以下程式碼片段中所述，請關閉用戶端：  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
11. 建置專案，然後執行它。 MS_SAMPLE_EMPLOYEE 資料表中的所有記錄會都顯示在主控台上。  
  
## <a name="see-also"></a>另請參閱  
 [開發 Oracle E-business Suite 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)