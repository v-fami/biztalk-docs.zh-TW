---
title: "完成 Oracle E-business Suite 使用 WCF 服務模型中的大型資料類型的資料表作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93ba3191-d234-424a-b2da-dcf384df4985
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 720da748059d3fe3da376ea42495a2587577f5ee
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="complete-operations-on-tables-with-large-data-types-in-oracle-e-business-suite-using-the-wcf-service-model"></a>完成 Oracle E-business Suite 使用 WCF 服務模型中的大型資料類型的資料表作業
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可讓配接器用戶端執行具有大型資料類型，例如 BLOB、 CLOB、 NCLOB、 和 BFILE 介面資料表和檢視表上的作業。  
  
-   類型的資料行 BLOB、 CLOB、 和 NCLOB，配接器可讓用戶端可以讀取，以及更新的資料。 配接器會公開 Read_\<*LOBColName* \>和 Update_\<*LOBColName* \>作業來讀取和更新資料，其中\<*LOBColName* \>是大型的資料類型資料行的名稱。 如果沒有與單一介面資料表中的大型資料類型的多個資料行，配接器會公開為許多的讀取和更新該介面資料表的作業。  
  
-   型別 BFILE 資料行，配接器用戶端可以只讀取資料。 配接器會公開 Read_\<*LOBColName* \> BFILE 類型的資料行中讀取資料的作業。 如果沒有與單一介面資料表中的大型資料類型的多個資料行，配接器會公開為許多讀取介面資料表的作業。  
  
 如需有關這些作業的詳細資訊，請參閱[介面資料表、 介面檢視、 資料表和檢視表，包含 LOB 資料的作業](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)。  
  
## <a name="about-the-examples-used-in-this-topic"></a>關於本主題中使用的範例  
 本主題中的範例更新客戶資料庫資料表中的 BLOB 資料行 （相片），然後從相同的資料行中擷取資料。 執行範例所提供的指令碼會建立資料表。 如需有關範例的詳細資訊，請參閱[Oracle EBS 配接器範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。 範例中， **LargeDataTypes_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。  
  
> [!NOTE]
>  本主題列出用於更新和讀取大型資料類型的基底資料庫資料表中的資料行的詳細的工作。 您必須執行相同的工作集更新和讀取大型資料類型的介面資料表中的資料行。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 資料表上的作業，使用大型資料類型所產生的 WCF 用戶端名稱[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]如下所列於下表根據資料表的名稱。  
  
|成品|WCF 用戶端名稱|  
|--------------|---------------------|  
|介面資料表|InterfaceTables_ [APP_NAME] _ [SCHEMA]\_[TABLE_NAME] 用戶端|  
  
 [APP_NAME] = Oracle E-business Suite 應用程式; 的實際名稱例如，尋找說明。  
  
 [SCHEMA] = 的成品、 集合例如，應用程式。  
  
 [TABLE_NAME] = 表格的名稱例如，MS_SAMPLE_EMPLOYEE。  
  
 [VIEW_NAME] = 檢視; 的名稱例如，MS_SAMPLE_EMPLOYEE_View。  
  
### <a name="method-signature-for-invoking-operations-on-tables"></a>叫用資料表上的作業的方法簽章  
 下表顯示在資料表上的基本作業的方法簽章。 簽章是資料表的不相同的檢視，不同之處在於檢視命名空間和名稱取代。  
  
|作業|方法簽章|  
|---------------|----------------------|  
|Update_\<*column_name*\>|public void Update_\<*column_name*\>（字串篩選條件，byte [] 的資料;）|  
|Read_\<*column_name*\>|公用 System.IO.Stream Read_\<*column_name*\>（字串篩選條件）。|  
  
 例如，下列程式碼會示範 Update_PHOTO 和 Read_PHOTO 作業的應用程式的結構描述在客戶資料庫資料表上產生 WCF 用戶端類別的方法簽章。  
  
```  
public partial class Tables_APPS_CUSTOMERClient : System.ServiceModel.ClientBase<Tables_APPS_CUSTOMER>, Tables_APPS_CUSTOMER {      
  
    public void Update_PHOTO(string FILTER, byte[] DATA);  
  
    public System.IO.Stream Read_PHOTO(string FILTER);  
}  
```  
  
 在此程式碼片段， **Tables_APPS_CUSTOMERClient**是 WCF 中的類別所產生的 OracleEBSBindingClient.cs 名稱[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 Update_PHOTO 和 Read_PHOTO 是以更新和讀取資料表中的大型資料類型的資料行就可以叫用的方法。  
  
### <a name="parameters-for-table-operations"></a>資料表作業的參數  
 本節提供 Update_ 所需的參數\<*column_name* \>和 Read_\<*column_name* \>作業。  
  
|作業名稱|參數|  
|--------------------|----------------|  
|Update_\<*column_name*\>|需要下列參數：<br /><br /> -   `string FILTER`. 這個參數必須包含 where 子句，表示具有要更新之資料的記錄。 例如， `"WHERE Name='Mindy Martin'"`。<br />-   `byte[] DATA`. 包含要更新大型資料類型的資料行中資料的位元組陣列。|  
|Read_\<*column_name*\>|需要下列參數：<br /><br /> -   `string FILTER`. 這個參數必須包含 where 子句代表從中資料有要讀取的記錄。 例如， `"WHERE Name='Mindy Martin'"`。|  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-tables-with-columns-of-large-data-types"></a>建立 WCF 用戶端來叫用具有大型資料類型之資料行的資料表上的作業  
 Oracle E-business Suite 使用 WCF 用戶端上執行作業所需動作的泛型集合會包含一組工作中所述[Oracle E-business Suite 配接器的 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md)。 本章節描述如何建立 WCF 用戶端來叫用 Update_PHOTO 和 Read_PHOTO 客戶資料庫資料表上的作業。  
  
#### <a name="to-create-a-wcf-client"></a>若要建立 WCF 用戶端  
  
1.  Visual Studio 中建立 Visual C# 專案。 本主題中，建立主控台應用程式。  
  
2.  產生 Update_PHOTO 和 Read_PHOTO 作業客戶資料庫資料表上的 WCF 用戶端類別。 如需產生 WCF 用戶端類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  
  
    > [!IMPORTANT]
    >  在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。  
  
3.  在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`和`Microsoft.ServiceModel.Channels`， `System.Transactions`。  
  
4.  開啟 Program.cs 檔案並加入下列命名空間：  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
    -   `System.Transactions`  
  
    -   `System.IO`  
  
5.  開啟 Program.cs 檔案並建立用戶端，如以下程式碼片段中所述。  
  
    ```  
  
              Tables_APPS_CUSTOMERClient client = new Tables_APPS_CUSTOMERClient("OracleEBSBinding_Tables_APPS_CUSTOMER");  
  
    client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     在此程式碼片段， `Tables_APPS_CUSTOMERClient` OracleEBSBindingClient.cs 中定義之 WCF 用戶端。 這個檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
    > [!NOTE]
    >  在此片段中，您可以使用的繫結和端點位址，從組態檔 app.config。您可以同時也可以明確指定這些值，在程式碼中。 如需以不同的方式指定用戶端繫結的詳細資訊，請參閱[for Oracle E-business Suite 繫結的用戶端設定](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。  
  
6.  設定用戶端的認證。  
  
    ```  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
    > [!IMPORTANT]
    >  在此範例中，您執行資料庫資料表上的作業。 不過，如果您正在執行的介面資料表上的作業，您必須設定應用程式內容指定適當的值**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。 開啟用戶端之前，您必須指定這些繫結屬性。 如需應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
7.  以下程式碼片段中所述，請開啟用戶端：  
  
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
  
8.  叫用 Update_PHOTO 作業，在 CUSTOMER 資料表上。  
  
     Update_PHOTO 作業需要更新資料的位元組陣列。 在此程式碼片段中，您可以使用 FileStream 類別建立的相片，SamplePhoto.jpg 位元組陣列。 讓此應用程式運作，檔案必須複製到專案的 bin 目錄。  
  
    > [!IMPORTANT]
    >  Update_PHOTO 作業必須執行在交易中，所以**UseAmbientTransaction**繫結屬性必須設定為**true**和 Update_PHOTO 作業必須在執行交易範圍。 您可以設定**UseAmbientTransaction**在 app.config 中，或藉由明確設定為在應用程式中繫結屬性`binding.UseAmbientTransaction = true`。 請注意，是否您要在程式碼中明確指定的繫結屬性，您必須這樣做之前開啟用戶端。  
  
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
  
     Read_PHOTO 提供 System.IO.Stream 的形式輸出。 配接器用戶端必須實作 FileStream 類別 Read_PHOTO 作業中讀取資料。 Read_PHOTO 作業已完成之後，檔案 PhotoCopy.jpg 是會複製到專案的 bin 目錄下。  
  
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
  
10. 以下程式碼片段中所述，請關閉用戶端：  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
11. 建置專案，然後執行它。 應用程式更新客戶資料表的 PHOTO 欄，然後再讀取相片的資料行的內容。  
  
## <a name="see-also"></a>請參閱  
 [開發 Oracle E-business Suite 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)