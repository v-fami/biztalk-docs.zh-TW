---
title: 在 SQL 中使用 WCF 服務模型的 ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62f166af-b657-491b-b20d-1ae7886f27ce
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9dd50b3353aac683548f9220c441bef21776a37
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968831"
---
# <a name="executereader-executescalar-or-executenonquery-operations-in-sql-using-wcf-service-model"></a>在 SQL 中使用 WCF 服務模型的 ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業
[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會公開一般的 SQL Server 作業時，這類**ExecuteNonQuery**， **ExecuteReader**，和**ExecuteScalar**。 您可以使用這些作業上的 SQL Server 資料庫執行任何 SQL 陳述式。 這些作業根據回應您取得 SQL 陳述式的類型而有所不同。 如需配接器如何支援這些作業的詳細資訊，請參閱[支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。  

 本主題示範如何執行**ExecuteReader**作業使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用 WCF 服務模型。 您可以依照程序中執行本主題所述的同一組**ExecuteNonQuery**並**ExecuteScalar**作業。  

## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例會使用**ExecuteReader**作業執行 ADD_EMP_DETAILS 預存程序。 這個預存程序會將記錄加入 Employee 資料表，並傳回記錄的員工識別碼。 ADD_EMP_DETAILS 預存程序會建立執行 SQL 指令碼提供範例。 如需有關範例的詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。 範例中， **Execute_Reader**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。  

## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 叫用泛型作業 （ExecuteNonQuery、 ExecuteReader、 ExecuteScalar） 使用或產生 WCF 用戶端的名稱[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會列在下表。  

|作業|WCF 用戶端名稱|  
|----------------|---------------------|  
|ExecuteNonQuery、 ExecuteReader 或 ExecuteScalar|GenericTableOpClient|  

### <a name="method-signature-for-invoking-generic-operations"></a>叫用泛型作業的方法簽章  
 下表來叫用泛型作業所公開的方法的簽章。  

|作業|方法簽章|  
|---------------|----------------------|  
|ExecuteNonQuery|int ExecuteNonQuery （查詢字串）|  
|ExecuteReader|System.Data.DataSet [] ExecuteReader （查詢字串）|  
|ExecuteScalar|字串 ExecuteScalar(string Query)|  

 例如，泛型作業方法的簽章會顯示下列程式碼片段。  

```  
public partial class GenericTableOpClient : System.ServiceModel.ClientBase<GenericTableOp>, GenericTableOp {  
  public int ExecuteNonQuery(string Query);  
  public System.Data.DataSet[] ExecuteReader(string Query);  
  public string ExecuteScalar(string Query);  
}  
```  

 在此片段中，  

-   `GenericTableOpClient` 是類別的名稱。 在此範例中，您可以使用這個類別來建立用戶端來叫用泛型作業，也就是 ExecuteReader。  

-   `public System.Data.DataSet[] ExecuteReader(string Query)` 是，您可以叫用在此範例中叫用 ADD_EMP_DETAILS 方法預存程序。  

## <a name="creating-a-wcf-client-to-invoke-an-executereader-operation"></a>建立 WCF 用戶端來叫用 ExecuteReader 操作  
 一組標準的 SQL Server 使用 WCF 用戶端上執行作業所需的動作牽涉到一組工作中所述[SQL 配接器的 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md)。 本節特別說明如何建立 WCF 用戶端叫用**ExecuteReader**作業執行 ADD_EMP_DETAILS 預存程序。 這個預存程序會建立執行 SQL 指令碼提供每個範例。  

#### <a name="to-create-a-wcf-client-to-invoke-executereader-operation"></a>若要建立 WCF 用戶端叫用 ExecuteReader 操作  

1. Visual Studio 中建立 Visual C# 專案。 本主題中，建立主控台應用程式。  

2. 產生 WCF 用戶端類別，如**ExecuteReader**一般作業。 當您連接到 SQL Server 資料庫使用時，這項作業會位於根節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需有關如何產生 WCF 用戶端類別的詳細資訊，請參閱 <<c0> [ 產生的 SQL Server 成品的 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。  

   > [!IMPORTANT]
   >  在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。  

3. 在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`和`Microsoft.ServiceModel.Channels`。  

4. 開啟 Program.cs 檔案，並建立用戶端，如下列程式碼片段中所述。  

   ```  

           GenericTableOpClient client = new GenericTableOpClient("SqlAdapterBinding_GenericTableOp");  
   client.ClientCredentials.UserName.UserName = "<Enter username here>";  
   client.ClientCredentials.UserName.Password = "<Enter password here>";  
   ```  

    在此片段中， `GenericTableOpClient` SqlAdapterBindingClient.cs 中定義之 WCF 用戶端。 此檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 `SqlAdapterBinding_GenericTableOp` 是用戶端端點組態名稱，並在 app.config 中定義。此檔案也會產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，其中包含繫結屬性和其他組態設定。  

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

6. 叫用**ExecuteReader** ADD_EMP_DETAILS 作業預存程序。 您可以叫用 ExecuteReader 操作之前，您必須新增`System.Data`您的程式碼的命名空間。  

   ```  
   string query = "EXEC ADD_EMP_DETAILS 'Tom Smith', 'Manager', 500000";  
   DataSet[] dsArray = client.ExecuteReader(query);  

   Console.WriteLine("Invoking the ADD_EMP_DETAILS stored procedure using ExecuteReader");  
   Console.WriteLine("*****************************************************");  
   foreach (DataSet dataSet in dsArray)  
   {  
      foreach (DataTable tab in dsArray[0].Tables)  
      {  
          foreach (DataRow row in tab.Rows)  
          {  
             for (int i = 0; i < tab.Columns.Count; i++)  
             {  
                Console.WriteLine("The ID for the newly added employee is : " + row[i]);  
             }  
          }  
       }  
   }  
   Console.WriteLine("*****************************************************");  

   ```  

7. 下列程式碼片段中所述，請關閉該用戶端：  

   ```  
   client.Close();  
   Console.WriteLine("Press any key to exit...");  
   Console.ReadLine();  
   ```  

8. 建置專案，然後執行它。 新插入的員工的員工識別碼會顯示在主控台上。
