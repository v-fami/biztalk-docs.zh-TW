---
title: 使用 WCF 服務模型的 Oracle 資料庫中執行 SQLEXECUTE 作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, performing a SQLEXECUTE operation
- SQLEXECUTE operation, performing a
- how to, invoke the SQLEXECUTE operation
ms.assetid: d3f61e5f-4453-4a76-9bc6-40d91cb58224
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2aedcd9874682ed71af774db72979c152836ab3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004853"
---
# <a name="run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model"></a>使用 WCF 服務模型的 Oracle 資料庫中執行 SQLEXECUTE 作業
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現一組標準的 Oracle 資料庫成品的作業。 藉由使用這些作業，您可以執行如下呼叫的動作，Oracle 函式或程序，或執行基本 SQL 資料操作語言 (DML) 作業在資料表上。 不過，有可能是由您的商務邏輯驅動的案例會要求您執行作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不會不會出現。 例如，您可能想要：  
  
- 對資料庫成品是不會顯示所執行作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; 例如，取得 CURVAL 或 NEXTVAL 的 Oracle 序列。  
  
- 執行資料定義語言 」 作業;例如，建立資料表。  
  
- 在設計階段; 沒有為資料庫成品上執行作業比方說，更新您的商務邏輯所建立的暫存資料表中的記錄。  
  
- 執行資料表上更複雜的 DML 作業，作業的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現; 比方說，若要執行的查詢包含聯結子句。  
  
  這種情況下，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現 SQLEXECUTE 作業。 藉由使用 SQLEXECUTE 作業，您可以執行的 Oracle 資料庫上的參數化的 SQL 陳述式。 SQLEXECUTE 作業支援的輸入的參數區塊，可讓您執行一次的每一組相同的 SQL 陳述式的參數集所組成。 SQLEXECUTE 作業會傳回一組標準的記錄中的 SQL 陳述式的結果。  
  
## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題使用 Oracle 序列中的範例中，名為 TID_SEQ。 指令碼來產生此序列被隨附的 SDK 範例。 如需有關 SDK 範例的詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 WCF 服務模型會產生專用的 WCF 用戶端**SQLEXECUTEClient**，SQLEXECUTE 作業。 下列程式碼示範**SQLEXECUTEClient**和您呼叫以叫用 SQLEXECUTE 操作的方法簽章。  
  
```  
public partial class SQLEXECUTEClient : System.ServiceModel.ClientBase<SQLEXECUTE>, SQLEXECUTE {  
  
    ...  
  
    public microsoft.lobservices.oracledb._2007._03.GenRecordRow[] SQLEXECUTE(string SQLSTATEMENT, string PARAMETERSCHEMA, microsoft.lobservices.oracledb._2007._03.PARAMETERDATA[] PARAMETERSET);   
}  
```  
  
 SQLEXECUTE 作業會傳回一組標準的記錄。 此記錄集包含的值 （如果有的話） 所傳回的陳述式執行該 SQLEXECUTE 作業。 SQLEXECUTE 作業 PARAMETERDATA 物件集合，其中每一個包含表示為字串的輸入參數的集合中，您可以傳遞輸入參數的集。 下列程式碼顯示 PARAMETERDATA 集的定義。  
  
```  
namespace microsoft.lobservices.oracledb._2007._03 {  
    using System.Runtime.Serialization;  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class PARAMETERDATA : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        ...  
  
        private string[] PARAMETERField;  
  
        ...  
  
        [System.Runtime.Serialization.DataMemberAttribute()]  
        public string[] PARAMETER {  
            get {  
                return this.PARAMETERField;  
            }  
            set {  
                this.PARAMETERField = value;  
            }  
        }  
    }  
}  
```  
  
## <a name="invoking-the-sqlexecute-operation"></a>叫用 SQLEXECUTE 作業  
 若要使用的 WCF 用戶端叫用 SQLEXECUTE 操作，執行下列步驟。  
  
1. 產生**SQLEXECUTEClient**目標資料表或檢視表的類別。  
  
   > [!IMPORTANT]
   >  SQLEXECUTE 作業會顯示在根節點下 (**/**) 中**選取類別**窗格中的**新增配接器服務參考** 對話方塊。  
  
2. 建立的執行個體**SQLEXECUTEClient**類別，並叫用**SQLEXECUTE**的 Oracle 資料庫上執行 SQL 陳述式的方法。  
  
   如需詳細資訊，有關如何建立 WCF 用戶端類別，並在叫用作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 < [Oracle 資料庫配接器的 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md)。  
  
   下列範例會使用**SQLEXECUTEClient**藉由執行下列 SQL 陳述式中取得 Oracle 序列，TID_SEQ，下一個值： `SELECT tid_seq.nextval id from DUAL`。 然後，輸出會寫入至主控台。  
  
```  
using (SQLEXECUTEClient sqlClient = new SQLEXECUTEClient("OracleDBBinding_SQLEXECUTE"))  
{  
    sqlClient.ClientCredentials.UserName.UserName = "SCOTT";  
    sqlClient.ClientCredentials.UserName.Password = "TIGER";  
    try  
    {  
        sqlClient.Open();  
    }  
    catch (Exception ex)  
    {  
        Console.WriteLine("Error opening SQL client " + ex.Message);  
        throw;  
    }  
    microsoft.lobservices.oracledb._2007._03.GenRecordRow[] sequenceRec =   
        new microsoft.lobservices.oracledb._2007._03.GenRecordRow[0];  
  
    try  
    {  
        sequenceRec = sqlClient.SQLEXECUTE("SELECT tid_seq.nextval id from DUAL", null, null);  
    }  
    catch (Exception ex)  
    {  
        Console.WriteLine("Error executing SQL client " + ex.Message);  
        throw;  
    }  
  
    if (sequenceRec.Length > 0)  
    {  
        Console.WriteLine("TID_SEQUENCE value is {0}", sequenceRec[0].GenRecordColumn[0].ColumnValue);  
    }  
    else  
    {  
    Console.WriteLine("Couldn't get next TID_SEQUENCE value");  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [開發使用 WCF 服務模型的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)