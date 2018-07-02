---
title: 插入、 更新、 刪除或選取 使用 WCF 服務模型的 Oracle 資料庫中的 作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, Delete operation
- WCF service model, Select operation
- WCF service model, Insert operation
- WCF service model, Update operation
ms.assetid: d1a9f44f-ea0b-4dd6-9489-fa0d963848c4
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91fa9b1828a8519dcbf7e1efba1db99ba84f1d0d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982447"
---
# <a name="insert-update-delete-or-select-operations-in-oracle-database-using-the-wcf-service-model"></a>插入、 更新、 刪除或選取 使用 WCF 服務模型的 Oracle 資料庫中的 作業
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現一組基本 Insert、 Update、 Delete 和 Oracle 資料庫資料表和檢視表的 Select 作業。 藉由使用這些作業，您可以執行簡單的 SQL INSERT、 UPDATE、 SELECT、 和 DELETE 陳述式 WHERE 子句的目標資料表或檢視上所限定。 若要執行更複雜的作業，例如 SQL SELECT 查詢，會使用 JOIN 運算子，您可以使用 SQLEXECUTE 作業。 如需有關 LEXECUTE 作業的詳細資訊，請參閱[Oracle Database 中的 WCF 服務模型執行 SQLEXECUTE 作業](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)。  
  
 下表摘要說明基本的 SQL 作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]資料表和檢視表的介面。 如需這些作業的完整說明，請參閱[基本 Insert、 Update、 Delete 和資料表和檢視表的選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)。  
  
|作業|描述|  
|---------------|-----------------|  
|Insert|插入作業支援多個記錄或大量插入到目標資料表或檢視表：<br /><br /> -多個記錄插入作業會將資料列插入資料表或檢視，根據提供的記錄集。<br />-在大量插入作業會將資料列插入資料表或檢視，以提供 SQL SELECT 查詢和資料行的清單。 查詢所傳回的記錄插入目標資料表資料行清單為基礎。|  
|Select|根據提供的清單之資料行名稱和篩選條件字串，指定 SQL WHERE 子句的目標資料表上執行 SQL SELECT 查詢。|  
|Update|目標資料表上執行更新。 所指定 SQL WHERE 子句的篩選字串指定要更新的記錄。 在範本的記錄中指定的更新值。|  
|DELETE|根據 SQL WHERE 子句的篩選條件字串中指定的目標資料表上執行刪除。|  
  
## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例使用 /SCOTT/ACCOUNTACTIVITY 資料表。 指令碼來產生此資料表會提供 SDK 範例。 如需有關 SDK 範例的詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 WCF 用戶端的基本的 SQL 作業產生的名稱，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]介面為基礎的資料表或檢視，如同下表的名稱。  
  
|Oracle 資料庫成品|WCF 用戶端名稱|  
|------------------------------|---------------------|  
|Table|[結構描述]表格 [TABLE_NAME] 用戶端|  
|檢視|[結構描述]檢視 [VIEW_NAME] 用戶端|  
  
 [SCHEMA] = 集合的 Oracle 成品、比方說，SCOTT。  
  
 [TABLE_NAME] = 資料表的名稱比方說，ACCOUNTACTIVITY。  
  
 [VIEW_NAME] = [] 檢視的名稱。  
  
 下表顯示在資料表上的基本 SQL 作業的方法簽章。 簽章也適用於檢視中，不同之處在於檢視命名空間和名稱取代的資料表。  
  
|作業|方法簽章|  
|---------------|----------------------|  
|Insert|長時間插入 ([TABLE_NS]。 [TABLE_NAME] RECORDINSERT [資料錄集，字串 COLUMN_NAMES，查詢字串);|  
|Select|[TABLE_NS]。[名稱]RECORDSELECT [] 選取 （字串 COLUMN_NAMES，篩選條件的字串）;|  
|Update|長時間更新 ([TABLE_NS]。 [TABLE_NAME] RECORDUPDATE 資料錄集，篩選條件的字串）;|  
|DELETE|長時間刪除 （字串篩選條件）;|  
  
 [TABLE_NS] = 資料表的命名空間的名稱比方說，microsoft.lobservices.oracledb._2007._03.SCOTT。Table.ACCOUNTACTIVITY。  
  
 [TABLE_NAME] = 資料表的名稱比方說，ACCOUNTACTIVITY。  
  
 Insert、 Update 和 Select 作業所使用的記錄類型都定義在資料表或檢視的命名空間。  
  
 下列程式碼示範 WCF 用戶端類別的方法簽章為 Delete、 Insert、 Select 和 Update 產生/SCOTT/ACCOUNTACTIVITY 資料表上的作業。  
  
```  
public partial class SCOTTTableACCOUNTACTIVITYClient : System.ServiceModel.ClientBase<SCOTTTableACCOUNTACTIVITY>, SCOTTTableACCOUNTACTIVITY {  
  
    public long Delete(string FILTER);  
  
    public long Insert(microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[] RECORDSET, string COLUMN_NAMES, string QUERY);  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] Select(string COLUMN_NAMES, string FILTER);  
  
    public long Update(microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE RECORDSET, string FILTER);  
}  
```  
  
## <a name="invoking-the-basic-sql-operations"></a>叫用基本的 SQL 作業  
 若要使用的 WCF 用戶端叫用資料表或檢視表的基本 SQL 作業，執行下列步驟。  
  
1. 產生 WCF 用戶端類別，針對目標資料表或檢視。 這個類別應該包含您將會在目標成品叫用作業的方法。  
  
2. 建立 WCF 用戶端類別的執行個體，並叫用其方法來執行資料表或檢視表上的作業。  
  
   如需詳細資訊，有關如何建立 WCF 用戶端類別，並在叫用作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 的 Oracle 資料庫配接器使用 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md)。  
  
   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]的 Oracle 資料庫上執行每個作業在交易內。 您可以設定來控制此交易的隔離等級**TransactionIsolationLevel**繫結屬性。 如需詳細資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結屬性，請參閱[使用 BizTalk Adapter for Oracle 資料庫繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。  
  
   下列各節提供有關如何叫用每個基本的 SQL 作業，在您的程式碼的詳細資料。  
  
###  <a name="BKMK_InsertOperation"></a> 插入作業  
 下表顯示如何設定多個記錄插入的參數和大量插入作業。  
  
|插入作業類型|資料錄集|COLUMN_NAMES|QUERY|  
|---------------------------|---------------|-------------------|-----------|  
|多個記錄|應插入至目標的 INSERTRECORDS 的集合。|null|null|  
|大量|null|目標; 中的資料行名稱的逗號分隔清單例如，"TID，帳戶 」。 資料行清單中指定查詢結果應該會放置在每個插入的資料列中的資料行。 查詢必須傳回符合指定的數目和類型的資料行清單中的資料行的結果集。|在資料庫資料表或檢視傳回的結果集要插入至目標; 上的 SQL SELECT 查詢比方說，「 從 NEW_TRANSACTIONS WHERE 帳戶選取 （帳戶中的 TID） = 100001"。 結果集必須符合在數目和類型的資料行清單。|  
  
 插入作業傳回記錄插入至目標的數目。  
  
> [!IMPORTANT]
>  在 WCF 服務模型中，用於插入作業的記錄集是強型別。 您可以設定要 nillable 資料行的值**null**排除該資料行插入作業; 從記錄中不過，您無法設定的值非 nill 的資料行**null**。 這表示，在多個記錄插入作業中，您必須提供每個記錄中的所有非 nill 的資料行值。 此外，沒有資料流支援基本的 SQL 作業時使用 WCF 服務模型。 如果您的多個記錄插入作業牽涉到大型的記錄集，這可能是很重要的考量。 如需詳細資訊，請參閱 <<c0> [ 叫用使用 WCF 服務模型的基本的 SQL 作業的限制](#BKMK_LimitationsInvoking)。  
  
 下列程式碼顯示的多個記錄插入作業 （兩筆記錄） 為目標的 ACCOUNTACTIVITY 資料表。  
  
```  
// Insert records  
                using (SCOTTTableACCOUNTACTIVITYClient aaTableClient =   
                    new SCOTTTableACCOUNTACTIVITYClient("OracleDBBinding_SCOTT.Table.ACCOUNTACTIVITY"))  
                {  
                    long recsInserted;  
  
                    aaTableClient.ClientCredentials.UserName.UserName = "SCOTT";  
                    aaTableClient.ClientCredentials.UserName.Password = "TIGER";  
  
                    try  
                    {  
                        aaTableClient.Open();  
                    }  
                    catch (Exception ex)  
                    {  
                        // handle exception  
                        Console.WriteLine("Exception: " + ex.Message);  
                        throw;  
                    }  
  
                    // Do a multiple record Insert of 2 records for account 100001  
  
                    microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[] insertRecs =  
                        new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[2];  
  
                                  TID__COMPLEX_TYPE tid = new TID__COMPLEX_TYPE();  
                                  tid.InlineValue = "tidSequence.NextVal()";  
  
                                  ACCOUNT__COMPLEX_TYPE account = new ACCOUNT__COMPLEX_TYPE();  
                                  account.Value = 100001;  
  
                    AMOUNT__COMPLEX_TYPE amount = new AMOUNT__COMPLEX_TYPE();  
                    amount.Value = 400;  
  
                    TRANSDATE__COMPLEX_TYPE transdate = new TRANSDATE__COMPLEX_TYPE();  
                    transdate.Value = DateTime.Now.Date;  
  
                    PROCESSED__COMPLEX_TYPE processed = new PROCESSED__COMPLEX_TYPE();  
                    processed.Value = "n";  
  
                    DESCRIPTION__COMPLEX_TYPE description1 = new DESCRIPTION__COMPLEX_TYPE();  
                    description1.Value = "Inserted Record #1";  
  
                    DESCRIPTION__COMPLEX_TYPE description2 = new DESCRIPTION__COMPLEX_TYPE();  
                    description2.Value = "Inserted Record #2";  
  
                    insertRecs[0] =   
                        new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT();  
                    insertRecs[0].TID = tid;  
                    insertRecs[0].ACCOUNT = account;  
                    insertRecs[0].AMOUNT = amount;  
                    insertRecs[0].TRANSDATE = transdate;  
                    insertRecs[0].DESCRIPTION = description1;  
                    insertRecs[0].PROCESSED = processed;  
  
                    insertRecs[1] =   
                        new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT();  
                    insertRecs[1].TID = tid;  
                    insertRecs[1].ACCOUNT = account;  
                    insertRecs[1].AMOUNT = amount;  
                    insertRecs[1].TRANSDATE = transdate;  
                    insertRecs[1].DESCRIPTION = description2;  
                    insertRecs[1].PROCESSED = processed;  
  
                    try  
                    {  
                        recsInserted = aaTableClient.Insert(insertRecs, null, null);  
                    }  
                    catch (Exception ex)  
                    {  
                        // handle exception  
                        Console.WriteLine("Exception: " + ex.Message);  
                        throw;  
                    }  
  
                    Console.WriteLine("Insert Done: {0} records inserted", recsInserted);  
```  
  
### <a name="select-operation"></a>選取作業  
 下表顯示所選取的作業參數。  
  
|COLUMN_NAMES|FILTER|  
|-------------------|------------|  
|目標; 中的資料行名稱的逗號分隔清單例如，"TID，帳戶 」。 資料行清單中指定目標應該在結果集中傳回之資料的行。 未指定資料行清單中的資料行，將設為.NET 預設值在傳回的記錄集內。 Nillable 的資料行，這個值是**null**。|SQL WHERE 子句，指定查詢; 的目標資料列的內容例如，"描述 = '插入記錄 #1' 」。 您可以將此參數設定為**null**傳回目標的所有資料列。|  
  
 選取的作業會傳回強型別記錄集的目標資料列型別為基礎。  
  
> [!IMPORTANT]
>  當您使用 WCF 服務模型時，沒有資料流支援基本的 SQL 作業。 如果您的查詢傳回大量的記錄集，您可以使用 WCF 通道模型來改善效能。 如需詳細資訊，請參閱 <<c0> [ 叫用使用 WCF 服務模型的基本的 SQL 作業的限制](#BKMK_LimitationsInvoking)。  
  
 下列程式碼會顯示目標 ACCOUNTACTIVITY 資料表的選取作業。 傳回的記錄會寫入至主控台。  
  
```  
// Declare a variable to hold the result set  
microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] selectRecords;  
  
// Select all records and write them to the console  
try  
{  
    selectRecords = aaTableClient.Select("*", null);  
}  
catch (Exception ex)  
{  
    // handle exception  
}  
  
Console.WriteLine("ACCOUNTACTIVITY before any operations");  
for (int i = 0; i \< selectRecords.Length; i++)  
{  
    Console.WriteLine("{0}\t{1}\t{2}\t{3}\t{4}", selectRecords[i].TID,  
    selectRecords[i].ACCOUNT,  
    selectRecords[i].AMOUNT,  
    selectRecords[i].TRANSDATE,  
    selectRecords[i].DESCRIPTION);  
}  
```  
  
> [!NOTE]
>  此程式碼省略了建立、 設定及開啟 WCF 用戶端執行個體的步驟。 如需包含下列步驟的範例，請參閱 < [Insert 作業](#BKMK_InsertOperation)。  
  
### <a name="update-operation"></a>更新作業  
 下表顯示更新作業的參數。  
  
|資料錄集|FILTER|  
|---------------|------------|  
|強型別範本記錄，根據目標的資料列型別。 範本記錄指定的目標資料列的更新值。 Nillable 的資料列的資料行，您可以指定 null 值，指出資料行不會更新目標資料列中。|SQL WHERE 子句，指定要更新的資料列在目標中的內容。 例如，"描述 = 'Inserted Record #1' 」。|  
  
 更新作業會傳回從目標刪除的資料列數目。  
  
> [!IMPORTANT]
>  在 WCF 服務模型中，更新作業所使用的範本記錄會是強型別。 如果 nillable 資料行，您可以省略更新作業的資料行，其值設定為**null**在範本記錄中; 不過，如果資料行不為 nillable，然後您必須設定其範本記錄中的值。 比方說，如果資料行是主索引鍵，它必須包含值。 如需詳細資訊，請參閱 <<c0> [ 叫用使用 WCF 服務模型的基本的 SQL 作業的限制](#BKMK_LimitationsInvoking)。  
  
 下列程式碼會顯示目標 ACCOUNTACTIVITY 資料表的更新作業。  
  
```  
long recsUpdated;  
  
...  
  
// Create updated template. The TID, TIME, AMOUNT, and DESCRIPTION fields will be updated  
microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE updateRecord =  
    new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE();  
        updateRecord.TID = tidSequence.NextVal();  
        updateRecord.ACCOUNT = null;  
        updateRecord.AMOUNT = 300;  
        updateRecord.TRANSDATE = DateTime.Now.Date;  
        updateRecord.DESCRIPTION = "Updated Record #2";  
        updateRecord.PROCESSED = null;  
  
// Set filter string to specify the target record by using the DESCRIPTION field  
string filter = "DESCRIPTION = 'Inserted Record #2'";  
  
try  
{  
    recsUpdated = aaTableClient.Update(updateRecord, filter);  
}  
catch (Exception ex)  
{  
    // handle exception  
    ...  
}  
  
Console.WriteLine("{0} records updated", recsUpdated);  
```  
  
> [!NOTE]
>  此程式碼省略了建立、 設定及開啟 WCF 用戶端執行個體的步驟。 如需包含下列步驟的範例，請參閱 < [Insert 作業](#BKMK_InsertOperation)。  
  
### <a name="delete-operation"></a>刪除動作  
 下表顯示刪除作業的參數。  
  
|FILTER|  
|------------|  
|SQL WHERE 子句，指定要從目標刪除的資料列的內容。 例如，"描述 = 'Inserted Record #1' 」。|  
  
 刪除作業會傳回從目標刪除的資料列數目。 下列程式碼顯示目標 ACCOUNTACTIVITY 資料表的刪除作業。  
  
```  
// Set filter string equal to the DESCRIPTION field of the target record  
string filter = "DESCRIPTION = 'Inserted Record #1'";  
  
try  
{  
    recsDeleted = aaTableClient.Delete(filter);  
}  
catch (Exception ex)  
{  
    // handle exception  
  
    ...  
}  
Console.WriteLine("{0} records deleted", recsDeleted);  
```  
  
> [!NOTE]
>  此程式碼省略了建立、 設定及開啟 WCF 用戶端執行個體的步驟。 如需包含下列步驟的範例，請參閱 < [Insert 作業](#BKMK_InsertOperation)。  
  
##  <a name="BKMK_LimitationsInvoking"></a> 使用 WCF 服務模型叫用的基本 SQL 作業的限制  
 當您使用 WCF 用戶端叫用的基本的 SQL 作業時，就會有下列限制：  
  
- **插入作業。** 多個記錄插入作業所用的記錄集是強型別，並因此包括所有的資料列資料行。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]解譯為 null 的值來表示記錄中，資料行應該排除插入作業; 不過，非 nill 的資料行無法排除，因為您不能設為 null 的值。 因此，您必須指定非 nill 的資料行的值，當您執行多個記錄插入作業。  
  
- **插入作業。** [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]解譯**DbNull** nillable 的資料行來表示應該從多個記錄插入作業中排除資料行中的值。 這表示您無法將 nillable 的資料行設定為**DbNull** Oracle 資料庫中的多個記錄插入作業。  
  
- **插入作業。** 沒有資料流支援多個記錄插入作業牽涉到大型的記錄集。  
  
- **更新作業。** 在更新作業中使用的範本記錄為強型別，並因此包括所有的資料列資料行。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]解譯來表示此記錄中的 null 值，應該從更新作業中排除資料行; 不過，非 nill 的資料行無法排除，因為無法為 null 值。 因此，您必須指定非 nill 的資料行的值，當您執行更新作業。  
  
- **更新作業。** [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]解譯**DbNull** nillable 資料資料行中的範本記錄来表示應該從作業中排除資料行的值。 這表示您無法將 nillable 的資料行設定為**DbNull**使用更新作業的 Oracle 資料庫上。  
  
- **選取作業。** 沒有資料流支援傳回大型的記錄集的 SELECT 查詢。  
  
  這些限制其中呈現挑戰的情況下，您可以使用 WCF 通道模型，因為叫用作業：  
  
- 藉由使用 WCF 通道模型，您可以排除特定的資料行 Update 和 Insert 作業。  
  
- WCF 通道模型提供節點層級的資料流支援基本的 SQL 作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 （expose)。  
  
  如需有關使用使用的 WCF 通道模型[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 開發 Oracle 資料庫應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)。  
  
## <a name="see-also"></a>另請參閱  
 [開發使用 WCF 通道模型的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)