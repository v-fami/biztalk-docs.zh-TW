---
title: 如何建立事實擷取器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IFactRetriever interface
- Business Rules Framework, bindings
- factsHandleIn object
- Business Rules Framework, code samples
- Business Rules Framework, fact retrievers
- UpdateFacts method
- Business Rules Framework, programming
ms.assetid: 503dc769-3ada-4099-a5fe-4dd03d995600
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20ea60356580ae7d5a6ac2be3336ec07314211f1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22250206"
---
# <a name="how-to-create-a-fact-retriever"></a>如何建立事實擷取器
「事實擷取器」 (Fact Retriever) 是一種元件，在其執行期間，可用於將長期事實的執行個體判斷提示到原則。 您可以實作**IFactRetriever**介面，並設定要在執行階段使用此實作以帶入長期事實執行個體的原則版本。 原則版本會叫用**UpdateFacts**上每個執行循環，如果事實擷取器針對該特定版本設定事實擷取器實作的方法。  
  
 您可以選擇性地實作**IFactRemover**事實擷取器元件上的介面。 規則引擎會叫用**UpdateFactsAfterExecution**方法**IFactRemover**介面處置原則時。 這樣便會提供您進行任何後執行工作的機會。例如認可任何資料庫變更，或是從規則引擎的工作記憶體中撤回任何物件執行個體。  
  
## <a name="to-specify-a-fact-retriever-for-a-policy"></a>指定原則的事實擷取器  
 您可以使用下列程式碼以便將規則集設定為使用 "MyAssembly" 組件中的 "Retriever" 類別作為事實擷取器。  
  
```  
RuleEngineComponentConfiguration fr = new RuleEngineComponentConfiguration("MyAssembly", "Retriever");  
RuleSet rs = new RuleSet("ruleset");  
// associate the execution configuration with a ruleset  
RuleSetExecutionConfiguration rsCfg = rs.ExecutionConfiguration;  
rsCfg.FactRetriever = factRetriever;  
```  
  
> [!NOTE]
>  如果您指定如 MyAssembly 的簡單組件名稱做為 RuleEngineComponentConfiguration 建構函式的第一個參數，BizTalk 規則引擎就會假設它是私用組件，並會在您的應用程式資料夾中尋找該組件。 如果您指定完整格式組件名稱，例如**MyAssembly，Version = 1.0.0.0，Culture = neutral，PublicKeyToken = a310908b42c024fe**，規則引擎會假設它是共用的組件，並尋找在全域組件組件快取 (GAC)。 您可以尋找簡單和完整的組件名稱，在定義[http://go.microsoft.com/fwlink/?LinkId=64535](http://go.microsoft.com/fwlink/?LinkId=64535)。  
  
 您可以利用必要的應用程式特有邏輯將事實擷取器設計為連接到必要資料來源，判斷提示資料為長期事實到引擎中，並指定用於重新整理或判斷提示長期事實的新執行個體到引擎的邏輯。 直到更新前，最初判斷提示到引擎進而快取的值將用於後續的執行循環。 事實擷取器實作會傳回類似 token 的物件，而且可用連同**factsHandleIn**物件來判斷是否要更新現有事實或判斷提示新事實。 當原則版本第一次，呼叫其事實擷取器**factsHandleIn**物件一律為 null，且再事實擷取器執行後才會傳回物件的值。  
  
 請注意，對於相同的規則引擎執行個體，長期事實只需要判斷提示一次。 例如，當您使用**呼叫規則**圖形在協調流程時，原則執行個體移至內部快取。 此時，會撤回所有短期事實而保留長期事實。 若再次呼叫相同的原則，無論是相同的協調流程執行個體或相同主控件內不同的協調流程執行個體，都會從快取中擷取此原則執行個體並重複使用。 在部分批次處理實例中，會建立相同原則的數個原則執行個體。 若建立新原則執行個體，則必須確保判斷提示正確的長期事實。  
  
 此外，您需要撰寫自訂程式碼以實作下列策略：  
  
-   瞭解何時更新長期事實  
  
-   應追蹤哪個規則引擎執行個體使用的哪個長期事實  
  
 以下範例程式碼顯示使用不同繫結類型的不同事實擷取器實作，這些實作與 [MyPolicy] 相關聯以判斷提示 [MyTableInstance] 為長期事實。  
  
## <a name="datatable-binding"></a>DataTable 繫結  
  
```  
using System;  
using System.Xml;  
using System.Collections;  
using Microsoft.RuleEngine;  
using System.IO;  
using System.Data;  
using System.Data.SqlClient;  
namespace MyBizTalkApplication.FactRetriever  
{  
   public class myFactRetriever:IFactRetriever  
   {  
      public object UpdateFacts(RuleSetInfo rulesetInfo, Microsoft.RuleEngine.RuleEngine engine, object factsHandleIn)  
      {  
         object factsHandleOut;  
         if (factsHandleIn == null)   
  
         {  
            SqlDataAdapter dAdapt = new SqlDataAdapter();  
            dAdapt.TableMappings.Add("Table", "CustInfo");  
            SqlConnection conn = new SqlConnection("Initial Catalog=Northwind;Data Source=(local);Integrated Security=SSPI;");  
            conn.Open();  
            SqlCommand myCommand = new SqlCommand("SELECT * FROM CustInfo", conn);  
            myCommand.CommandType = CommandType.Text;  
            dAdapt.SelectCommand = myCommand;  
            DataSet ds = new DataSet("Northwind");  
            dAdapt.Fill(ds);  
            TypedDataTable tdt = new TypedDataTable(ds.Tables["CustInfo"]);  
            engine.Assert(tdt);  
            factsHandleOut = tdt;  
         }  
  
         else  
            factsHandleOut = factsHandleIn;  
         return factsHandleOut;  
      }  
   }  
}  
```  
  
## <a name="datarow-binding"></a>DataRow 繫結  
  
```  
using System;  
using System.Xml;  
using System.Collections;  
using Microsoft.RuleEngine;  
using System.IO;  
using System.Data;  
using System.Data.SqlClient;  
namespace MyBizTalkApplication.FactRetriever  
{  
   public class myFactRetriever:IFactRetriever  
   {  
  
      public object UpdateFacts(RuleSetInfo rulesetInfo, Microsoft.RuleEngine.RuleEngine engine, object factsHandleIn)  
      {  
         object factsHandleOut;  
         if (factsHandleIn == null)   
  
         {  
            SqlDataAdapter dAdapt = new SqlDataAdapter();  
            dAdapt.TableMappings.Add("Table", "CustInfo");  
            SqlConnection conn = new SqlConnection("Initial Catalog=Northwind;Data Source=(local);Integrated Security=SSPI;");  
            conn.Open();  
            SqlCommand myCommand = new SqlCommand("SELECT * FROM CustInfo", conn);  
            myCommand.CommandType = CommandType.Text;  
            dAdapt.SelectCommand = myCommand;  
            DataSet ds = new DataSet("Northwind");  
            dAdapt.Fill(ds);  
            TypedDataTable tdt = new TypedDataTable(ds.Tables["CustInfo"]);  
  
            // binding to the first row of CustInfo table  
            TypedDataRow tdr = new TypedDataRow(ds.Tables["CustInfo"].Rows[0],tdt);  
            engine.Assert(tdr);  
            factsHandleOut = tdr;     
         }  
         else  
            factsHandleOut = factsHandleIn;  
         return factsHandleOut;  
      }  
   }   
}  
```  
  
 以下範例程式碼示範如何在事實擷取器實作中判斷提示 .NET 和 XML 事實。  
  
```  
using System;  
using System.Xml;  
using System.Collections;  
using Microsoft.RuleEngine;  
using System.IO;  
using System.Data;  
using System.Data.SqlClient;  
namespace MyBizTalkApplication.FactRetriever  
{  
   public class myFactRetriever:IFactRetriever  
   {  
      public object UpdateFacts(RuleSetInfo rulesetInfo, Microsoft.RuleEngine.RuleEngine engine, object factsHandleIn)  
      {  
         object factsHandleOut;  
         if (factsHandleIn == null)   
         {  
            //create .NET object instances  
            bookInstance = new Book();  
            magazineInstance = new Magazine();              
  
            //create an instance of the XML object  
            XmlDocument xd = new XmlDocument();  
  
            //load the document  
            xd.Load(@"..\myXMLInstance.xml");  
  
            //create and instantiate an instance of TXD  
            TypedXmlDocument doc = new TypedXmlDocument("mySchema",xd1);  
  
            engine.Assert(bookInstance);  
            engine.Assert(magazineInstance);  
            engine.Assert(doc);  
            factsHandleOut = doc;  
         }  
         else  
            factsHandleOut = factsHandleIn;  
         return factsHandleOut;  
      }  
   }  
}  
```  
  
## <a name="dataconnection-binding"></a>DataConnection 繫結  
  
```  
using System;  
using System.Xml;  
using System.Collections;  
using Microsoft.RuleEngine;  
using System.IO;  
using System.Data;  
using System.Data.SqlClient;  
namespace MyBizTalkApplication.FactRetriever  
{  
   public class myFactRetriever:IFactRetriever  
   {  
      public object UpdateFacts(RuleSetInfo rulesetInfo, Microsoft.RuleEngine.RuleEngine engine, object factsHandleIn)  
      {  
         object factsHandleOut;  
  
         {   
            string strCmd = "Initial Catalog=Northwind;Data Source=(local);Integrated Security=SSPI;";  
            SqlConnection conn = new SqlConnection(strCmd);  
            DataConnection dc = new DataConnection("Northwind", "CustInfo", conn);  
  
            engine.Assert(dc);  
            factsHandleOut = dc;           
         }  
         return factsHandleOut;  
      }  
   }  
}  
```  
  
 請注意， **DataConnection**s 應該永遠重新判斷提示，如上述程式碼範例所示，從事實擷取器提供時。 引擎執行個體使用**DataConnection**查詢資料庫，根據規則條件，以及查詢所傳回的任何資料列判斷提示至引擎的工作記憶體作為**TypedDataRow**s。 重新判斷提示 DataConnection ，可確保先前引擎執行的資料列已自記憶體中清除。  
  
 事實上，還有判斷提示的一些好處**DataConnection**透過事實擷取器，只是它會提供外部化的資料來源的方法。