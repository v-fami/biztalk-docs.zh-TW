---
title: 如何建立事實擷取器 |Microsoft Docs
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
ms.openlocfilehash: 3157eca412123556a6e9637e1ffa28a8da7daa19
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012319"
---
# <a name="how-to-create-a-fact-retriever"></a><span data-ttu-id="61dc9-102">如何建立事實擷取器</span><span class="sxs-lookup"><span data-stu-id="61dc9-102">How to Create a Fact Retriever</span></span>
<span data-ttu-id="61dc9-103">「事實擷取器」 (Fact Retriever) 是一種元件，在其執行期間，可用於將長期事實的執行個體判斷提示到原則。</span><span class="sxs-lookup"><span data-stu-id="61dc9-103">A fact retriever is a component that is used to assert instances of long-term facts into a policy during its execution.</span></span> <span data-ttu-id="61dc9-104">您可以實作**IFactRetriever**介面，並設定要在執行階段中使用此實作以帶入長期事實執行個體的原則版本。</span><span class="sxs-lookup"><span data-stu-id="61dc9-104">You can implement the **IFactRetriever** interface and configure a policy version to use this implementation at run time to bring in the long-term fact instances.</span></span> <span data-ttu-id="61dc9-105">原則版本會叫用**UpdateFacts**上每個執行循環，如果事實擷取器針對該特定版本設定事實擷取器實作的方法。</span><span class="sxs-lookup"><span data-stu-id="61dc9-105">The policy version invokes the **UpdateFacts** method of the fact retriever implementation on every execution cycle, if a fact retriever is configured for that particular version.</span></span>  
  
 <span data-ttu-id="61dc9-106">您可以選擇性地實作**IFactRemover**事實擷取器元件上的介面。</span><span class="sxs-lookup"><span data-stu-id="61dc9-106">You can optionally implement the **IFactRemover** interface on a fact retriever component.</span></span> <span data-ttu-id="61dc9-107">規則引擎會叫用**UpdateFactsAfterExecution**方法**IFactRemover**介面處置原則時。</span><span class="sxs-lookup"><span data-stu-id="61dc9-107">The rule engine invokes the **UpdateFactsAfterExecution** method of the **IFactRemover** interface when the policy is disposed.</span></span> <span data-ttu-id="61dc9-108">這樣便會提供您進行任何後執行工作的機會。例如認可任何資料庫變更，或是從規則引擎的工作記憶體中撤回任何物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="61dc9-108">This provides an opportunity to you to do any post-execution work such as committing any database changes or retracting any object instances from the rule engine's working memory.</span></span>  
  
## <a name="to-specify-a-fact-retriever-for-a-policy"></a><span data-ttu-id="61dc9-109">指定原則的事實擷取器</span><span class="sxs-lookup"><span data-stu-id="61dc9-109">To specify a fact retriever for a policy</span></span>  
 <span data-ttu-id="61dc9-110">您可以使用下列程式碼以便將規則集設定為使用 "MyAssembly" 組件中的 "Retriever" 類別作為事實擷取器。</span><span class="sxs-lookup"><span data-stu-id="61dc9-110">You could use the following code to configure the rule set to use a class named "Retriever" in the assembly named "MyAssembly" as the fact retriever.</span></span>  
  
```  
RuleEngineComponentConfiguration fr = new RuleEngineComponentConfiguration("MyAssembly", "Retriever");  
RuleSet rs = new RuleSet("ruleset");  
// associate the execution configuration with a ruleset  
RuleSetExecutionConfiguration rsCfg = rs.ExecutionConfiguration;  
rsCfg.FactRetriever = factRetriever;  
```  
  
> [!NOTE]
>  <span data-ttu-id="61dc9-111">如果您指定如 MyAssembly 的簡單組件名稱做為 RuleEngineComponentConfiguration 建構函式的第一個參數，BizTalk 規則引擎就會假設它是私用組件，並會在您的應用程式資料夾中尋找該組件。</span><span class="sxs-lookup"><span data-stu-id="61dc9-111">If you specify simple assembly name such as MyAssembly as the first parameter for RuleEngineComponentConfiguration constructor, the BizTalk rule engine assumes that it is a private assembly and looks for the assembly in your application folder.</span></span> <span data-ttu-id="61dc9-112">如果您指定完整格式組件名稱，例如**MyAssembly，version=1.0.0.0，Culture = neutral，PublicKeyToken = a310908b42c024fe**，規則引擎會假設它是共用的組件，並會在全域組件組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="61dc9-112">If you specify fully qualified assembly name such as **MyAssembly, Version=1.0.0.0, Culture=neutral, PublicKeyToken=a310908b42c024fe**, the rule engine assumes that it is a shared assembly and looks for the assembly in the global assembly cache (GAC).</span></span> <span data-ttu-id="61dc9-113">您可以找到簡單和完整的組件名稱，在定義[ http://go.microsoft.com/fwlink/?LinkId=64535 ](http://go.microsoft.com/fwlink/?LinkId=64535)。</span><span class="sxs-lookup"><span data-stu-id="61dc9-113">You can find the definitions of simple and fully qualified assembly names at [http://go.microsoft.com/fwlink/?LinkId=64535](http://go.microsoft.com/fwlink/?LinkId=64535).</span></span>  
  
 <span data-ttu-id="61dc9-114">您可以利用必要的應用程式特有邏輯將事實擷取器設計為連接到必要資料來源，判斷提示資料為長期事實到引擎中，並指定用於重新整理或判斷提示長期事實的新執行個體到引擎的邏輯。</span><span class="sxs-lookup"><span data-stu-id="61dc9-114">You can design the fact retriever with the required application-specific logic to connect to the required data sources, assert the data as long-term facts into the engine, and specify the logic for refreshing or asserting new instances of the long-term facts into the engine.</span></span> <span data-ttu-id="61dc9-115">直到更新前，最初判斷提示到引擎進而快取的值將用於後續的執行循環。</span><span class="sxs-lookup"><span data-stu-id="61dc9-115">Until updated, the values that are initially asserted into the engine and consequently cached will be used on subsequent execution cycles.</span></span> <span data-ttu-id="61dc9-116">事實擷取器實作會傳回類似 token 的物件，而且可用連同**factsHandleIn**物件來判斷是否要更新現有事實或判斷提示新事實。</span><span class="sxs-lookup"><span data-stu-id="61dc9-116">The fact retriever implementation returns an object that is analogous to a token and can be used along with the **factsHandleIn** object to determine whether to update existing facts or assert new facts.</span></span> <span data-ttu-id="61dc9-117">當原則版本第一次，呼叫其事實擷取器**factsHandleIn**物件一律是 null，然後在事實擷取器執行後會傳回物件的值。</span><span class="sxs-lookup"><span data-stu-id="61dc9-117">When a policy version calls its fact retriever for the first time, the **factsHandleIn** object is always null and then takes the value of the return object after the fact retriever's execution.</span></span>  
  
 <span data-ttu-id="61dc9-118">請注意，對於相同的規則引擎執行個體，長期事實只需要判斷提示一次。</span><span class="sxs-lookup"><span data-stu-id="61dc9-118">Note that for the same rule engine instance, a long-term fact only needs to be asserted once.</span></span> <span data-ttu-id="61dc9-119">例如，當您使用**呼叫規則**圖形在協調流程時，原則執行個體移至內部快取。</span><span class="sxs-lookup"><span data-stu-id="61dc9-119">For example, when you use the **Call Rules** shape in an orchestration, the policy instance is moved into an internal cache.</span></span> <span data-ttu-id="61dc9-120">此時，會撤回所有短期事實而保留長期事實。</span><span class="sxs-lookup"><span data-stu-id="61dc9-120">At this time, all short-term facts are retracted and long-term facts are kept.</span></span> <span data-ttu-id="61dc9-121">若再次呼叫相同的原則，無論是相同的協調流程執行個體或相同主控件內不同的協調流程執行個體，都會從快取中擷取此原則執行個體並重複使用。</span><span class="sxs-lookup"><span data-stu-id="61dc9-121">If the same policy is called again, either by the same orchestration instance or by a different orchestration instance in the same host, this policy instance is fetched from the cache and reused.</span></span> <span data-ttu-id="61dc9-122">在部分批次處理實例中，會建立相同原則的數個原則執行個體。</span><span class="sxs-lookup"><span data-stu-id="61dc9-122">In some batch processing scenarios, several policy instances of the same policy could be created.</span></span> <span data-ttu-id="61dc9-123">若建立新原則執行個體，則必須確保判斷提示正確的長期事實。</span><span class="sxs-lookup"><span data-stu-id="61dc9-123">If a new policy instance is created, you must ensure that the correct long-term facts are asserted.</span></span>  
  
 <span data-ttu-id="61dc9-124">此外，您需要撰寫自訂程式碼以實作下列策略：</span><span class="sxs-lookup"><span data-stu-id="61dc9-124">Additionally, you would need to write custom code to implement the following strategies:</span></span>  
  
- <span data-ttu-id="61dc9-125">瞭解何時更新長期事實</span><span class="sxs-lookup"><span data-stu-id="61dc9-125">Know when to update the long-term facts</span></span>  
  
- <span data-ttu-id="61dc9-126">應追蹤哪個規則引擎執行個體使用的哪個長期事實</span><span class="sxs-lookup"><span data-stu-id="61dc9-126">Keep track of which rule engine instance uses which long-term facts</span></span>  
  
  <span data-ttu-id="61dc9-127">以下範例程式碼顯示使用不同繫結類型的不同事實擷取器實作，這些實作與 [MyPolicy] 相關聯以判斷提示 [MyTableInstance] 為長期事實。</span><span class="sxs-lookup"><span data-stu-id="61dc9-127">The following sample code shows different fact retriever implementations, which are associated with MyPolicy to assert MyTableInstance as a long-term fact, using different binding types.</span></span>  
  
## <a name="datatable-binding"></a><span data-ttu-id="61dc9-128">DataTable 繫結</span><span class="sxs-lookup"><span data-stu-id="61dc9-128">DataTable binding</span></span>  
  
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
  
## <a name="datarow-binding"></a><span data-ttu-id="61dc9-129">DataRow 繫結</span><span class="sxs-lookup"><span data-stu-id="61dc9-129">DataRow binding</span></span>  
  
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
  
 <span data-ttu-id="61dc9-130">以下範例程式碼示範如何在事實擷取器實作中判斷提示 .NET 和 XML 事實。</span><span class="sxs-lookup"><span data-stu-id="61dc9-130">The following sample code demonstrates how to assert .NET and XML facts in a fact retriever implementation.</span></span>  
  
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
  
## <a name="dataconnection-binding"></a><span data-ttu-id="61dc9-131">DataConnection 繫結</span><span class="sxs-lookup"><span data-stu-id="61dc9-131">DataConnection Binding</span></span>  
  
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
  
 <span data-ttu-id="61dc9-132">請注意， **DataConnection**s 應該永遠重新判斷提示，提供從事實擷取器，上述程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="61dc9-132">Note that **DataConnection**s should always be reasserted, when provided from a fact retriever, as shown in the preceding code sample.</span></span> <span data-ttu-id="61dc9-133">引擎執行個體使用**DataConnection**查詢資料庫，根據規則條件，以及查詢所傳回的任何資料列判斷提示至引擎的工作記憶體作為**TypedDataRow**s。</span><span class="sxs-lookup"><span data-stu-id="61dc9-133">The engine instance uses the **DataConnection** to query the database based on the rule conditions, and any rows returned by the query would be asserted into the engine's working memory as **TypedDataRow**s.</span></span> <span data-ttu-id="61dc9-134">重新判斷提示 DataConnection ，可確保先前引擎執行的資料列已自記憶體中清除。</span><span class="sxs-lookup"><span data-stu-id="61dc9-134">Reasserting the DataConnection ensures that rows from a previous execution of the engine are cleared from memory.</span></span>  
  
 <span data-ttu-id="61dc9-135">事實上，還有判斷提示的一些好處**DataConnection**透過事實擷取器，它會提供外部化的資料來源的方式。</span><span class="sxs-lookup"><span data-stu-id="61dc9-135">In fact, there is little advantage to asserting a **DataConnection** through a fact retriever except that it provides a way to externalize the data source.</span></span>