---
title: 完成使用 WCF 服務模型的 Oracle E-business Suite 中的大型資料類型的資料表作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93ba3191-d234-424a-b2da-dcf384df4985
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9869cd49ed09d80a866f3dcbb6f4b9429788339b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982559"
---
# <a name="complete-operations-on-tables-with-large-data-types-in-oracle-e-business-suite-using-the-wcf-service-model"></a>完成使用 WCF 服務模型的 Oracle E-business Suite 中的大型資料類型的資料表作業
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器用戶端來執行大型資料類型，例如 BLOB、 CLOB、 NCLOB、 和 BFILE 介面資料表和檢視表上的作業。  

- 類型的資料行 BLOB、 CLOB、 和 NCLOB，此配接器可以讀取，以及更新資料的用戶端。 配接器會公開 Read_\<*LOBColName* \>和 Update_\<*LOBColName* \>作業來讀取和更新資料，其中\<*LOBColName* \>是具有大型的資料類型的資料行的名稱。 如果沒有單一的介面資料表中的大型資料類型的多個資料行，配接器會公開為許多讀取和更新該介面資料表的作業。  

- 型別 BFILE 資料行，配接器用戶端只能讀取資料。 配接器會公開 Read_\<*LOBColName* \> BFILE 類型的資料行中讀取資料的作業。 如果沒有單一的介面資料表中的大型資料類型的多個資料行，配接器會公開為許多讀取作業的介面資料表。  

  如需有關這些作業的詳細資訊，請參閱 < [Interface Table、 介面檢視、 資料表和檢視表，包含 LOB 資料的作業](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)。  

## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例會更新客戶資料庫資料表中的 BLOB 資料行 （相片），並接著會從相同的資料行的擷取資料。 執行提供的範例指令碼會建立資料表。 如需有關範例的詳細資訊，請參閱 < [Oracle EBS 配接器的範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。 範例中， **LargeDataTypes_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。  

> [!NOTE]
>  本主題列出用於更新和讀取大型資料類型的基底資料庫資料表中的資料行的詳細的工作。 您必須執行同一組工作來更新和讀取在介面資料表中的大型資料類型的資料行。  

## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 WCF 用戶端中的資料表上作業，使用大型資料類型所產生的名稱[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]下表所示，根據資料表的名稱。  


|     成品     |                     WCF 用戶端名稱                      |
|------------------|----------------------------------------------------------|
| 介面資料表 | InterfaceTables_[APP_NAME]*[SCHEMA]\\*[TABLE_NAME]Client |

 [APP_NAME>] = [Oracle E-business Suite 應用程式的實際名稱例如，尋找說明。  

 [SCHEMA] = 的成品、 集合例如，應用程式。  

 [TABLE_NAME] = 資料表的名稱比方說，MS_SAMPLE_EMPLOYEE。  

 [VIEW_NAME] = 檢視; 的名稱比方說，MS_SAMPLE_EMPLOYEE_View。  

### <a name="method-signature-for-invoking-operations-on-tables"></a>叫用資料表上的作業的方法簽章  
 下表顯示在資料表上的基本作業的方法簽章。 簽章也適用於檢視中，不同之處在於檢視命名空間和名稱取代的資料表。  

|作業|方法簽章|  
|---------------|----------------------|  
|Update_\<*column_name*\>|public void Update_\<*column_name*\>（字串篩選條件，byte [] 的資料;）|  
|Read_\<*column_name*\>|public System.IO.Stream Read_\<*column_name*\>(string FILTER);|  

 例如，下列的程式碼會示範針對 Update_PHOTO 和 Read_PHOTO 作業的應用程式結構描述在客戶資料庫資料表上所產生的 WCF 用戶端類別的方法簽章。  

```  
public partial class Tables_APPS_CUSTOMERClient : System.ServiceModel.ClientBase<Tables_APPS_CUSTOMER>, Tables_APPS_CUSTOMER {      

    public void Update_PHOTO(string FILTER, byte[] DATA);  

    public System.IO.Stream Read_PHOTO(string FILTER);  
}  
```  

 在此片段中， **Tables_APPS_CUSTOMERClient**是 WCF 中類別的名稱所產生 OracleEBSBindingClient.cs [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 Update_PHOTO Read_PHOTO 等可以叫用它來更新和讀取資料表中的大型資料類型的資料行的方法。  

### <a name="parameters-for-table-operations"></a>資料表作業的參數  
 本節提供 Update_ 所需的參數\<*column_name* \>和 Read_\<*column_name* \>作業。  

|作業名稱|參數|  
|--------------------|----------------|  
|Update_\<*column_name*\>|需要下列參數：<br /><br /> -   `string FILTER`. 這個參數必須包含 where 子句，表示具有更新之資料的記錄。 例如， `"WHERE Name='Mindy Martin'"`。<br />-   `byte[] DATA`. 包含要更新的大型資料類型資料行中資料的位元組陣列。|  
|Read_\<*column_name*\>|需要下列參數：<br /><br /> -   `string FILTER`. 這個參數必須包含 where 子句，表示來源的資料具有讀取的記錄。 例如， `"WHERE Name='Mindy Martin'"`。|  

## <a name="creating-a-wcf-client-to-invoke-operations-on-tables-with-columns-of-large-data-types"></a>建立 WCF 用戶端來叫用具有大型資料類型之資料行的資料表上的作業  
 一組標準的 Oracle E-business Suite 使用 WCF 用戶端上執行作業所需的動作牽涉到一組工作中所述[Oracle E-business Suite 配接器的 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md)。 本節說明如何建立 WCF 用戶端來叫用 Update_PHOTO 和 Read_PHOTO 客戶資料庫資料表上的作業。  

#### <a name="to-create-a-wcf-client"></a>若要建立的 WCF 用戶端  

1. Visual Studio 中建立 Visual C# 專案。 本主題中，建立主控台應用程式。  

2. 產生 WCF 用戶端類別，針對 Update_PHOTO 和 Read_PHOTO 作業會在客戶資料庫資料表。 如需有關如何產生 WCF 用戶端類別的詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Oracle E-business Suite 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  

   > [!IMPORTANT]
   >  在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。  

3. 在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`並`Microsoft.ServiceModel.Channels`， `System.Transactions`。  

4. 開啟 Program.cs 檔案並新增下列命名空間：  

   -   `Microsoft.Adapters.OracleEBS`  

   -   `System.ServiceModel`  

   -   `System.Transactions`  

   -   `System.IO`  

5. 開啟 Program.cs 檔案，並建立用戶端，如下列程式碼片段中所述。  

   ```  

             Tables_APPS_CUSTOMERClient client = new Tables_APPS_CUSTOMERClient("OracleEBSBinding_Tables_APPS_CUSTOMER");  

   client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
   client.ClientCredentials.UserName.Password = "<Enter password here>";  
   ```  

    在此片段中， `Tables_APPS_CUSTOMERClient` OracleEBSBindingClient.cs 中定義之 WCF 用戶端。 此檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  

   > [!NOTE]
   >  在此片段中，您可以使用的繫結和端點位址，從組態檔 app.config。您也可以明確指定這些值在您的程式碼。 如需有關指定用戶端繫結的不同方式的詳細資訊，請參閱[設定用戶端 for Oracle E-business Suite 繫結](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。  

6. 設定用戶端的認證。  

   ```  
   client.ClientCredentials.UserName.UserName = "myuser";  
   client.ClientCredentials.UserName.Password = "mypassword";  
   ```  

   > [!IMPORTANT]
   >  在此範例中，您要執行的資料庫資料表上的作業。 不過，如果您要執行在介面資料表上的作業，您必須設定應用程式內容指定適當的值，如**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。 開啟用戶端之前，您必須指定這些繫結屬性。 如需有關應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  

7. 下列程式碼片段中所述，請開啟用戶端：  

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

8. 叫用 Update_PHOTO 作業，在 CUSTOMER 資料表上。  

    Update_PHOTO 作業需要更新資料的位元組陣列。 在此程式碼片段中，您可以使用 FileStream 類別建立一張照片，SamplePhoto.jpg 的位元組陣列。 使用此應用程式，該檔案必須複製到專案的 bin 目錄。  

   > [!IMPORTANT]
   >  Update_PHOTO 作業只能在交易中，因此**UseAmbientTransaction**繫結屬性必須設定為 **，則為 true**和 Update_PHOTO 作業必須在中執行交易範圍。 您可以設定**UseAmbientTransaction** app.config 中或藉由明確將您的應用程式中將屬性繫結`binding.UseAmbientTransaction = true`。 請注意，是否您要在程式碼中明確指定的繫結屬性，您必須這麼做之前開啟用戶端。  

   ```  
   byte[] photo;  

   using (FileStream fs = new FileStream("SamplePhoto.jpg", FileMode.Open))  
   {  
       try  
       {  
           Console.WriteLine("Reading the photo");  
           int count = 0;  
           photo = new byte[fs.Length];  
           while ((count += fs.Read(photo, count, (int)(((fs.Length - count) > 4096) ? 4096 : fs.Length - count))) < fs.Length) ;  
       }  
       catch(Exception ex)  
       {  
           Console.WriteLine("Exception: " + ex.Message);  
           throw;  
       }  
   }  

   Console.WriteLine("Updating data for the 'PHOTO' column");  
   // Invoking the Update_PHOTO operation inside a transaction scope  
   using (TransactionScope tx = new TransactionScope())  
   {  
       string filter = "WHERE Name='Mindy Martin'";  
       client.Update_PHOTO(filter, photo);  
       tx.Complete();  
   }  

   ```  

9. 叫用 Read_PHOTO 作業，在 CUSTOMER 資料表上。  

     Read_PHOTO 提供 System.IO.Stream 的形式輸出。 配接器用戶端必須實作 FileStream 類別從 Read_PHOTO 作業讀取資料。 Read_PHOTO 作業完成之後，檔案 PhotoCopy.jpg 是會複製到專案的 bin 目錄下。  

    ```  
    using (FileStream fs = new FileStream("PhotoCopy.jpg", FileMode.Create))  
    {  
        Console.WriteLine("Reading photo data");  
        String ReadFilter = "WHERE NAME='Mindy Martin'";  
        Stream photoStream = client.Read_PHOTO(ReadFilter);  
        Console.WriteLine("Photo data read -- writing to PhotoCopy.jpg");  

        int count;  
        int length = 0;  
        byte[] buffer = new byte[4096];  
        while ((count = photoStream.Read(buffer, 0, 4096)) > 0)  
        {  
            fs.Write(buffer, 0, count);  
            length+=count;  
        }  
        Console.WriteLine("{0} bytes written to PhotoCopy.jpg", length);  
    }  

    Console.WriteLine("Photo updated and read back -- Hit <RETURN> to end");  
    Console.ReadLine();  
    ```  

10. 下列程式碼片段中所述，請關閉該用戶端：  

    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  

11. 建置專案，然後執行它。 應用程式更新 CUSTOMER 資料表的 PHOTO 資料行，然後再讀取 PHOTO 資料行的內容。  

## <a name="see-also"></a>另請參閱  
 [開發 Oracle E-business Suite 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)