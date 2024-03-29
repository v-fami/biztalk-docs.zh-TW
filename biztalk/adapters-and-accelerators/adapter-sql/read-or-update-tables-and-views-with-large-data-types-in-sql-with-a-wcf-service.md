---
title: 具有大型的資料型別在 SQL 中使用 WCF 服務模型的資料表和檢視表執行作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7d33e17c-e09e-4a57-9acc-43095e67ed8c
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2bfb30c01113e868bd6a662d004639645e29746
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992479"
---
# <a name="run-operations-on-tables-and-views-with-large-data-types-in-sql-using-the-wcf-service-model"></a>具有大型的資料型別在 SQL 中使用 WCF 服務模型的資料表和檢視表執行作業
[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]啟用讀取和更新的大型資料類型資料行中的資料，也就是配接器用戶端、 varchar （max）、 nvarchar （max） 或 varbinary （max）。 若要從這類資料行中讀取資料，配接器用戶端可以使用選取的作業。 若要插入或更新資料到這類資料行，配接器會公開一組\<*column_name* \>作業，其中\< *column_name* \>名稱類型 varchar （max）、 nvarchar （max），或 varbinary （max） 資料行。  
  
 此外，在 SQL Server 中，您可以儲存非結構化的資料，例如文字文件和影像 varbinay(max) 資料行。 這類非結構化的資料就會呼叫 FILESTREAM 資料。 FILESTREAM 資料可以儲存為檔案系統上的檔案。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓用戶端將輸入資料行類型 varbinary （max） FILESTREAM 資料。 [FILESTREAM 儲存體](https://docs.microsoft.com/sql/relational-databases/blob/filestream-sql-server)有詳細資訊。 
  
 本主題提供您必須執行特定工作的相關資訊的電腦上執行 SQL Server 和執行配接器用戶端能夠插入或更新 FILESTREAM 資料的電腦。 本主題也提供指示執行 Set\<*column_name* \>插入 FILESTREAM 資料的作業。  
  
> [!NOTE]
>  如果您正在執行具有使用者定義類型的資料行的資料表上的作業，請確定您參考[資料表和檢視與使用 SQL 配接器的使用者定義型別上的作業](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須執行 SQL Server 的電腦和執行配接器用戶端電腦上執行下列工作。  
  
- **執行 SQL Server 的電腦上**  
  
  -   您必須在 SQL Server 執行個體上啟用 FILESTREAM。 請參閱[啟用及設定 FILESTREAM](https://docs.microsoft.com/sql/relational-databases/blob/enable-and-configure-filestream)。
  
  -   您必須建立啟用 FILESTREAM 的資料庫。 請參閱[建立啟用 FILESTREAM 的資料庫](https://docs.microsoft.com/sql/relational-databases/blob/create-a-filestream-enabled-database)。
  
  -   您必須擁有儲存 FILESTREAM 資料的資料表。 請參閱[建立儲存 FILESTREAM 資料的資料表](https://docs.microsoft.com/sql/relational-databases/blob/create-a-table-for-storing-filestream-data)，
  
- **在電腦上執行 配接器用戶端**  
  
  -   您必須安裝 SQL 用戶端連接性 SDK。 您可以安裝 SQL 用戶端連接性 SDK，以執行 SQL Server 安裝程式，然後選取**SQL 用戶端連接性 SDK**中**特徵選取**精靈頁面。 配接器會使用 sqlncli10.dll，安裝 SQL 用戶端連接性 SDK，與用於執行 FILESTREAM 操作。  
  
  您已完成這些工作之後，您為所有設定為插入或更新 SQL Server 資料庫資料表中的 FILESTREAM 資料。  
  
## <a name="how-this-topic-demonstrates-operations-on-large-data-types"></a>本主題將大型資料類型上的作業的示範  
 若要示範如何執行資料集\<*column_name* \>大型資料類型的資料表作業需要資料表**記錄**，具有資料行**識別碼**並**文件**:  
  
-   **記錄**資料表，且所有的資料，由執行 SQL 指令碼提供範例。 如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
-   **識別碼**類型 uniqueidentifier 的資料行，並取用 GUID。 假設**識別碼**資料行已經有一個 GUID '`438B7B4C-5491-409F-BCC1-78817C399EC3`'。  
  
-   **文件**sloupec je typu varbinary （max)。 若要更新**文件**資料行中，配接器會公開**SetDocument**作業。  
  
> [!NOTE]
>  SQL Server，來示範 FILESTREAM 作業，假設**文件**資料行可儲存 FILESTREAM 資料。  
  
## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例上執行作業**記錄**資料表。 **記錄**執行 SQL 指令碼提供範例來建立資料表。 如需有關範例的詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。 範例中， **Records_FILESTREAM_Op**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 大型資料的作業產生 WCF 用戶端的名稱類型[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]探索下, 表所示，為基礎的資料表或檢視的名稱。  
  
|SQL Server 資料庫成品|WCF 用戶端名稱|  
|----------------------------------|---------------------|  
|Table|TableOp_[Schema]_[TABLE_NAME]Client|  
|檢視|ViewOp_[Schema]_[VIEW_NAME]Client|  
  
 [SCHEMA] = Collection 的 SQL Server 成品、比方說，dbo。  
  
### <a name="method-signature-for-invoking-operations-on-columns-of-large-data-types"></a>針對大型資料類型的資料行叫用作業的方法簽章  
 下表顯示在資料表上的基本作業的方法簽章。 簽章也適用於檢視中，不同之處在於檢視命名空間和名稱取代的資料表。  
  
|作業|方法簽章|  
|---------------|----------------------|  
|設定\<*column_name*\>|public void 組\<*column_name*\>（字串篩選條件，byte [] 的資料;）|  
  
 \<*column_name* \> = 大型資料類型的資料行名稱。  
  
 例如，下列程式碼顯示的方法簽章產生 WCF 用戶端類別**SetDocument**上的作業**記錄**下預設"dbo"的結構描述的資料表。  
  
```  
public partial class TableOp_dbo_RecordsClient : System.ServiceModel.ClientBase<TableOp_dbo_Records>, TableOp_dbo_Records {      
    public void SetDocument (string Filter, byte[] Data);  
}  
```  
  
 在此片段中， **TableOp_dbo_RecordsClient**是 WCF 中類別的名稱所產生 SqlAdapterBindingClient.cs [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
### <a name="parameters-for-operations-on-columns-of-large-data-types"></a>在大型資料類型的資料行上作業的參數  
 本節提供設定所需的參數\<*column_name* \>作業。  
  
|參數名稱|描述|  
|--------------------|-----------------|  
|字串篩選條件|指定 WHERE 子句可讓您根據所在的介面卡更新大型資料類型的資料行的記錄。|  
|byte [] 的資料|指定必須更新大型資料類型資料行的值。|  
  
 集合\<*column_name* \>作業不會傳回任何值。  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-columns-of-large-data-types"></a>建立 WCF 用戶端來叫用的大型資料類型資料行上的作業  
 一組標準的 SQL Server 使用 WCF 用戶端上執行作業所需的動作牽涉到一組工作中所述[使用 SQL 配接器的 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md)。 本節說明如何建立 WCF 用戶端來叫用**SetDocument**上的作業**記錄**資料表。 配接器會公開**SetDocument**更新大型資料類型的資料行中的資料作業。  
  
#### <a name="to-create-a-wcf-client"></a>若要建立的 WCF 用戶端  
  
1. Visual Studio 中建立 Visual C# 專案。 本主題中，建立主控台應用程式。  
  
2. 產生 WCF 用戶端類別，如**SetDocument**上的作業**記錄**資料表。 如需有關如何產生 WCF 用戶端類別的詳細資訊，請參閱 <<c0> [ 產生的 SQL Server 成品的 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。  
  
3. 在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`， `Microsoft.ServiceModel.Channels`，和`System.Transactions`。  
  
4. 開啟 Program.cs 檔案並新增`System.Transactions`命名空間。  
  
5. 在 Program.cs 中，建立用戶端，如下列程式碼片段中所述。  
  
   ```  
  
             TableOp_dbo_RecordsClient client = new TableOp_dbo_RecordsClient("SqlAdapterBinding_TableOp_dbo_Records");  
   client.ClientCredentials.UserName.UserName = "";  
   client.ClientCredentials.UserName.Password = "";  
  
   ```  
  
    在此片段中， `TableOp_dbo_RecordsClient` SqlAdapterBindingClient.cs 中定義之 WCF 用戶端。 此檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 `SqlAdapterBinding_TableOp_dbo_Records` 是用戶端端點組態名稱，並在 app.config 中定義。此檔案也會產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，其中包含繫結屬性和其他組態設定。  
  
   > [!CAUTION]
   >  為了執行 FILESTREAM 資料上的作業，您一律必須連接到 SQL Server 使用 Windows 驗證。 若要使用 Windows 驗證進行連接，您必須提供空的使用者名稱和密碼，如上述程式碼片段所示。 此外，在之前使用 Windows 驗證連接到 SQL Server，您必須執行中所述的步驟[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  
  
   > [!NOTE]
   >  在此片段中，您使用的繫結和端點位址從組態檔。 您也可以明確指定這些值在您的程式碼。 如需有關指定用戶端繫結的不同方式的詳細資訊，請參閱[設定 SQL 配接器的用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)。  
  
6. 下列程式碼片段中所述，請開啟用戶端：  
  
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
  
7. 叫用**SetDocument**上的作業**記錄**資料表。  
  
   > [!CAUTION]
   >  集合<em>< column_name ></em>一律必須在交易中執行作業。 為了確保功效，集合<em>< column_name ></em>必須在異動範圍內叫用作業並**UseAmbientTransaction**繫結屬性必須設定為**true**的 app.config 中。  
  
   ```  
   using (TransactionScope tx = new TransactionScope())  
   {  
       string filter = "WHERE Id='438B7B4C-5491-409F-BCC1-78817C399EC3'";  
       byte[] data = ASCIIEncoding.ASCII.GetBytes("Sample data");  
       client.SetDocument(filter, data);  
       tx.Complete();  
   }  
   ```  
  
    應用程式在這裡，將 「 範例資料 」 的字串轉換成 base64 編碼字串，並更新符合篩選準則的記錄中。  
  
8. 下列程式碼片段中所述，請關閉該用戶端：  
  
   ```  
   client.Close();  
   Console.WriteLine("Press any key to exit...");  
   Console.ReadLine();  
   ```  
  
9. 建置專案，然後執行它。 應用程式會更新**文件**中的資料行**記錄**資料表。  
  
## <a name="see-also"></a>另請參閱  
[使用 WCF 服務模型開發應用程式](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)