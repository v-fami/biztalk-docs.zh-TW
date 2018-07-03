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
# <a name="run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model"></a><span data-ttu-id="f2fb4-102">使用 WCF 服務模型的 Oracle 資料庫中執行 SQLEXECUTE 作業</span><span class="sxs-lookup"><span data-stu-id="f2fb4-102">Run SQLEXECUTE operation in Oracle Database using the WCF Service Model</span></span>
<span data-ttu-id="f2fb4-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現一組標準的 Oracle 資料庫成品的作業。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-103">The[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces a standard set of operations on Oracle database artifacts.</span></span> <span data-ttu-id="f2fb4-104">藉由使用這些作業，您可以執行如下呼叫的動作，Oracle 函式或程序，或執行基本 SQL 資料操作語言 (DML) 作業在資料表上。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-104">By using these operations, you can do things like call an Oracle function or procedure, or perform basic SQL data manipulation language (DML) operations on tables.</span></span> <span data-ttu-id="f2fb4-105">不過，有可能是由您的商務邏輯驅動的案例會要求您執行作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不會不會出現。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-105">However, there may be scenarios driven by your business logic that require you to perform operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not surface.</span></span> <span data-ttu-id="f2fb4-106">例如，您可能想要：</span><span class="sxs-lookup"><span data-stu-id="f2fb4-106">For example, you may want to:</span></span>  
  
- <span data-ttu-id="f2fb4-107">對資料庫成品是不會顯示所執行作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; 例如，取得 CURVAL 或 NEXTVAL 的 Oracle 序列。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-107">Perform an operation on database artifacts that are not surfaced by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; for example, get the CURVAL or NEXTVAL of an Oracle SEQUENCE.</span></span>  
  
- <span data-ttu-id="f2fb4-108">執行資料定義語言 」 作業;例如，建立資料表。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-108">Perform Data Definition Language operations; for example, create a table.</span></span>  
  
- <span data-ttu-id="f2fb4-109">在設計階段; 沒有為資料庫成品上執行作業比方說，更新您的商務邏輯所建立的暫存資料表中的記錄。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-109">Perform operations on a database artifact that was not present at design time; for example, update records in a temporary table that is created by your business logic.</span></span>  
  
- <span data-ttu-id="f2fb4-110">執行資料表上更複雜的 DML 作業，作業的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現; 比方說，若要執行的查詢包含聯結子句。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-110">Perform more complex DML operations on tables than the operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces; for example, to perform a query that includes a JOIN clause.</span></span>  
  
  <span data-ttu-id="f2fb4-111">這種情況下，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]呈現 SQLEXECUTE 作業。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-111">For these kinds of scenarios, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces the SQLEXECUTE operation.</span></span> <span data-ttu-id="f2fb4-112">藉由使用 SQLEXECUTE 作業，您可以執行的 Oracle 資料庫上的參數化的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-112">By using the SQLEXECUTE operation, you can perform a parameterized SQL statement on the Oracle database.</span></span> <span data-ttu-id="f2fb4-113">SQLEXECUTE 作業支援的輸入的參數區塊，可讓您執行一次的每一組相同的 SQL 陳述式的參數集所組成。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-113">The SQLEXECUTE operation supports an input parameter block comprised of parameter sets that enable you to execute the same SQL statement once for each set.</span></span> <span data-ttu-id="f2fb4-114">SQLEXECUTE 作業會傳回一組標準的記錄中的 SQL 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-114">The SQLEXECUTE operation returns the results of the SQL statement in a generic record set.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="f2fb4-115">有關使用本主題中的範例</span><span class="sxs-lookup"><span data-stu-id="f2fb4-115">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="f2fb4-116">本主題使用 Oracle 序列中的範例中，名為 TID_SEQ。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-116">The examples in this topic use an Oracle SEQUENCE named TID_SEQ.</span></span> <span data-ttu-id="f2fb4-117">指令碼來產生此序列被隨附的 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-117">A script to generate this SEQUENCE is supplied with the SDK samples.</span></span> <span data-ttu-id="f2fb4-118">如需有關 SDK 範例的詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-118">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="f2fb4-119">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="f2fb4-119">The WCF Client Class</span></span>  
 <span data-ttu-id="f2fb4-120">WCF 服務模型會產生專用的 WCF 用戶端**SQLEXECUTEClient**，SQLEXECUTE 作業。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-120">The WCF service model generates a dedicated WCF client, **SQLEXECUTEClient**, for the SQLEXECUTE operation.</span></span> <span data-ttu-id="f2fb4-121">下列程式碼示範**SQLEXECUTEClient**和您呼叫以叫用 SQLEXECUTE 操作的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-121">The following code shows the **SQLEXECUTEClient** and the signature of the method that you call to invoke the SQLEXECUTE operation.</span></span>  
  
```  
public partial class SQLEXECUTEClient : System.ServiceModel.ClientBase<SQLEXECUTE>, SQLEXECUTE {  
  
    ...  
  
    public microsoft.lobservices.oracledb._2007._03.GenRecordRow[] SQLEXECUTE(string SQLSTATEMENT, string PARAMETERSCHEMA, microsoft.lobservices.oracledb._2007._03.PARAMETERDATA[] PARAMETERSET);   
}  
```  
  
 <span data-ttu-id="f2fb4-122">SQLEXECUTE 作業會傳回一組標準的記錄。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-122">The SQLEXECUTE operation returns a generic record set.</span></span> <span data-ttu-id="f2fb4-123">此記錄集包含的值 （如果有的話） 所傳回的陳述式執行該 SQLEXECUTE 作業。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-123">This record set contains the values (if any) that are returned by the statements that the SQLEXECUTE operation executes.</span></span> <span data-ttu-id="f2fb4-124">SQLEXECUTE 作業 PARAMETERDATA 物件集合，其中每一個包含表示為字串的輸入參數的集合中，您可以傳遞輸入參數的集。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-124">You can pass sets of input parameters to the SQLEXECUTE operation in a collection of PARAMETERDATA objects, each of which contains a collection of input parameters represented as strings.</span></span> <span data-ttu-id="f2fb4-125">下列程式碼顯示 PARAMETERDATA 集的定義。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-125">The following code shows the definition of a PARAMETERDATA set.</span></span>  
  
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
  
## <a name="invoking-the-sqlexecute-operation"></a><span data-ttu-id="f2fb4-126">叫用 SQLEXECUTE 作業</span><span class="sxs-lookup"><span data-stu-id="f2fb4-126">Invoking the SQLEXECUTE Operation</span></span>  
 <span data-ttu-id="f2fb4-127">若要使用的 WCF 用戶端叫用 SQLEXECUTE 操作，執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-127">To invoke the SQLEXECUTE operation by using a WCF client, perform the following steps.</span></span>  
  
1. <span data-ttu-id="f2fb4-128">產生**SQLEXECUTEClient**目標資料表或檢視表的類別。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-128">Generate a **SQLEXECUTEClient** class for the target table or view.</span></span>  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="f2fb4-129">SQLEXECUTE 作業會顯示在根節點下 (**/**) 中**選取類別**窗格中的**新增配接器服務參考** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-129">The SQLEXECUTE operation is surfaced under the root node (**/**) in the **Select a category** pane in the **Add Adapter Service Reference** dialog box.</span></span>  
  
2. <span data-ttu-id="f2fb4-130">建立的執行個體**SQLEXECUTEClient**類別，並叫用**SQLEXECUTE**的 Oracle 資料庫上執行 SQL 陳述式的方法。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-130">Create an instance of the **SQLEXECUTEClient** class, and invoke the **SQLEXECUTE** method to execute SQL statements on the Oracle database.</span></span>  
  
   <span data-ttu-id="f2fb4-131">如需詳細資訊，有關如何建立 WCF 用戶端類別，並在叫用作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 < [Oracle 資料庫配接器的 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-131">For more detailed information about how to create a WCF client class and invoke operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Overview of the WCF service model with the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md).</span></span>  
  
   <span data-ttu-id="f2fb4-132">下列範例會使用**SQLEXECUTEClient**藉由執行下列 SQL 陳述式中取得 Oracle 序列，TID_SEQ，下一個值： `SELECT tid_seq.nextval id from DUAL`。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-132">The following example uses the **SQLEXECUTEClient** to get the next value of an Oracle SEQUENCE, TID_SEQ, by executing the following SQL statement: `SELECT tid_seq.nextval id from DUAL`.</span></span> <span data-ttu-id="f2fb4-133">然後，輸出會寫入至主控台。</span><span class="sxs-lookup"><span data-stu-id="f2fb4-133">The output is then written to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f2fb4-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2fb4-134">See Also</span></span>  
 [<span data-ttu-id="f2fb4-135">開發使用 WCF 服務模型的 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="f2fb4-135">Develop Oracle Database applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)