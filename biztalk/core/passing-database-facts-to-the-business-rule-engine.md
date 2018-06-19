---
title: 將資料庫事實傳遞給 「 商務規則引擎 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62285bbe-ee64-4c26-b48e-55f666dc1304
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01ae35802263b71965698e0bb56d1ddbee9ae0a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264134"
---
# <a name="passing-database-facts-to-the-business-rule-engine"></a><span data-ttu-id="ad511-102">將資料庫事實傳入商務規則引擎資料庫</span><span class="sxs-lookup"><span data-stu-id="ad511-102">Passing Database Facts to the Business Rule Engine</span></span>
<span data-ttu-id="ad511-103">當您使用 「 商務規則編輯器 」 工具來測試原則，要求 DataConnection/TypedDataTable 物件當做事實時，DataConnection/TypedDataTable 物件是自動為您建立，並判斷提示至 「 商務規則引擎工作記憶體。</span><span class="sxs-lookup"><span data-stu-id="ad511-103">When you use the Business Rule Composer tool to test a policy that requires a DataConnection/TypedDataTable object as a fact, a DataConnection/TypedDataTable object is automatically created for you and asserted into the Business Rule Engine's working memory.</span></span> <span data-ttu-id="ad511-104">此外，也會自動認可由該原則更新的任何資料庫。</span><span class="sxs-lookup"><span data-stu-id="ad511-104">Additionally, any database updates by the policy are committed automatically.</span></span>  
  
 <span data-ttu-id="ad511-105">反之，當您叫用從協調流程的原則，使用 [呼叫規則] 圖形或以程式設計方式，DataConnection/TypedDataTable 物件不為您建立，而且資料庫更新並未經過認可自動。</span><span class="sxs-lookup"><span data-stu-id="ad511-105">In contrast, when you invoke the policy from an orchestration, either by using the Call Rules shape or programmatically, the DataConnection/TypedDataTable object is not created for you and the database updates are not committed automatically.</span></span> <span data-ttu-id="ad511-106">在此情況下，您應該建立 DataConnection/TypedDataTable 物件、 將它當做事實傳遞至規則引擎，並使用下列方法之一，以程式設計方式認可資料庫變更。</span><span class="sxs-lookup"><span data-stu-id="ad511-106">In this case, you should create a DataConnection/TypedDataTable object, pass it as a fact to the rule engine, and commit the database changes programmatically by using one of the following methods.</span></span>  
  
## <a name="passing-a-dataconnection-object-from-an-orchestration"></a><span data-ttu-id="ad511-107">從協調流程傳遞 DataConnection 物件</span><span class="sxs-lookup"><span data-stu-id="ad511-107">Passing a DataConnection Object from an Orchestration</span></span>  
 <span data-ttu-id="ad511-108">下列範例程式碼將示範如何在協調流程中建立 DataConnection 物件、設定 [呼叫規則] 圖形以便將 DataConnection 物件當做參數傳遞，並在執行原則之後認可任何資料庫更新。</span><span class="sxs-lookup"><span data-stu-id="ad511-108">The following sample code demonstrates how to create a DataConnection object in the orchestration, configure the Call Rules shape to pass the DataConnection object as a parameter, and commit any database updates after the policy is executed.</span></span>  
  
1.  <span data-ttu-id="ad511-109">在 [協調流程設計師] 中開啟協調流程時，使用 [協調流程檢視] 索引標籤建立下列變數。</span><span class="sxs-lookup"><span data-stu-id="ad511-109">Create the following variables using the Orchestration View tab with the orchestration open in the Orchestration Designer.</span></span>  
  
    ```  
    DataCon of type Microsoft.RuleEngine.DataConnection   
    SqlCon of type System.Data.SqlClient.SqlConnection   
    SqlTran of type System.Data.SqlClient.SqlTransaction   
    ```  
  
2.  <span data-ttu-id="ad511-110">在 [呼叫規則] 圖形之前 「 運算式 」 圖形，建立 DataConnection 物件。</span><span class="sxs-lookup"><span data-stu-id="ad511-110">In an Expression shape before the Call Rules shape, create a DataConnection object.</span></span> <span data-ttu-id="ad511-111">下列程式碼範例示範如何建立 DataConnection 物件。</span><span class="sxs-lookup"><span data-stu-id="ad511-111">The following code example demonstrates how to create a DataConnection object.</span></span>  
  
    ```  
    SqlCon.ConnectionString = "Data Source=(local);Initial Catalog=Test;Integrated Security=SSPI";   
    SqlCon.Open();   
    SqlTran = SqlCon.BeginTransaction();   
    DataCon = new Microsoft.RuleEngine.DataConnection("test", "FlagTable", SqlCon, SqlTran);    
    ```  
  
3.  <span data-ttu-id="ad511-112">設定要做為參數傳遞 DataCon 變數呼叫規則 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="ad511-112">Configure the Call Rules shape to pass the DataCon variable as a parameter.</span></span> <span data-ttu-id="ad511-113">如需詳細資訊，請參閱[如何使用 [呼叫規則] 圖形](../core/how-to-use-the-call-rules-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="ad511-113">For more information, see [How to Use the Call Rules Shape](../core/how-to-use-the-call-rules-shape.md).</span></span>  
  
4.  <span data-ttu-id="ad511-114">在 [呼叫規則] 圖形之後的 [運算式] 圖形中，認可原則所做的資料庫變更。</span><span class="sxs-lookup"><span data-stu-id="ad511-114">In an Expression shape after the Call Rules shape, commit the database changes made by the policy.</span></span> <span data-ttu-id="ad511-115">下列程式碼範例將示範如何認可原則所做的資料庫變更。</span><span class="sxs-lookup"><span data-stu-id="ad511-115">The following code example demonstrates how to commit the database changes made by the policy.</span></span>  
  
    ```  
    DataCon.Update();   
    SqlTran.Commit();  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="ad511-116">您必須使用[SqlTransaction](http://msdn.microsoft.com/library/system.data.sqlclient.sqltransaction.aspx)物件在原則更新資料庫。</span><span class="sxs-lookup"><span data-stu-id="ad511-116">You need to use a [SqlTransaction](http://msdn.microsoft.com/library/system.data.sqlclient.sqltransaction.aspx) object only if the policy updates the database.</span></span>  
  
## <a name="passing-a-dataconnection-object-from-a-fact-retriever"></a><span data-ttu-id="ad511-117">從事實擷取器傳遞 DataConnection 物件</span><span class="sxs-lookup"><span data-stu-id="ad511-117">Passing a DataConnection Object from a Fact Retriever</span></span>  
 <span data-ttu-id="ad511-118">以下是從事實擷取器元件傳遞 DataConnection 物件所需的一般執行步驟。</span><span class="sxs-lookup"><span data-stu-id="ad511-118">Here are the typical steps you need to implement to pass a DataConnection object from a fact retriever component.</span></span>  
  
1.  <span data-ttu-id="ad511-119">建立事實擷取器元件，以建立並判斷提示 DataConnection 物件至規則引擎的工作記憶體中。</span><span class="sxs-lookup"><span data-stu-id="ad511-119">Create a fact retriever component that creates and asserts a DataConnection object into the rule engine's working memory.</span></span> <span data-ttu-id="ad511-120">如需如何建立事實擷取器元件的詳細資訊，請參閱[如何建立事實擷取器](../core/how-to-create-a-fact-retriever.md)。</span><span class="sxs-lookup"><span data-stu-id="ad511-120">For more information about how to create a fact retriever component, see [How to Create a Fact Retriever](../core/how-to-create-a-fact-retriever.md).</span></span>  
  
2.  <span data-ttu-id="ad511-121">實作[IFactRemover](http://msdn.microsoft.com/library/Microsoft.RuleEngine.IFactRemover.aspx)介面上事實擷取器元件，以及認可資料庫變更從[UpdateFactsAfterExecution](http://msdn.microsoft.com/library/microsoft.ruleengine.ifactremover.updatefactsafterexecution.aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="ad511-121">Implement the [IFactRemover](http://msdn.microsoft.com/library/Microsoft.RuleEngine.IFactRemover.aspx) interface on fact retriever component, and commit the database changes from the [UpdateFactsAfterExecution](http://msdn.microsoft.com/library/microsoft.ruleengine.ifactremover.updatefactsafterexecution.aspx) method.</span></span> <span data-ttu-id="ad511-122">規則引擎會在完成執行原則之後呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="ad511-122">This method is called by the rule engine after it is done with executing the policy.</span></span>  
  
3.  <span data-ttu-id="ad511-123">使用「商務規則編輯器」工具將原則設定為使用事實擷取器元件。</span><span class="sxs-lookup"><span data-stu-id="ad511-123">Configure the policy to use the fact retriever component by using the Business Rule Composer tool.</span></span> <span data-ttu-id="ad511-124">如需詳細資訊，請參閱[如何設定原則的事實擷取器](../core/how-to-configure-a-fact-retriever-for-a-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="ad511-124">For more information, see [How to Configure a Fact Retriever for a Policy](../core/how-to-configure-a-fact-retriever-for-a-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad511-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad511-125">See Also</span></span>  
 <span data-ttu-id="ad511-126">[商務規則引擎中的資料存取](../core/data-access-in-the-business-rule-engine.md) </span><span class="sxs-lookup"><span data-stu-id="ad511-126">[Data Access in the Business Rule Engine](../core/data-access-in-the-business-rule-engine.md) </span></span>  
 <span data-ttu-id="ad511-127">[如何建立事實擷取器](../core/how-to-create-a-fact-retriever.md) </span><span class="sxs-lookup"><span data-stu-id="ad511-127">[How to Create a Fact Retriever](../core/how-to-create-a-fact-retriever.md) </span></span>  
 [<span data-ttu-id="ad511-128">如何設定原則的事實擷取器</span><span class="sxs-lookup"><span data-stu-id="ad511-128">How to Configure a Fact Retriever for a Policy</span></span>](../core/how-to-configure-a-fact-retriever-for-a-policy.md)