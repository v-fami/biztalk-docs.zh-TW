---
title: 交易支援 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DataConnection object
- Business Rules Framework, code samples
- Business Rules Framework, programming
ms.assetid: 84faac2f-6229-4692-9d1a-bf62d87d69bb
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57fc1d7a1edd18663cb21a85037cf3e662948fc4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279422"
---
# <a name="transaction-support"></a><span data-ttu-id="a8e5a-102">交易支援</span><span class="sxs-lookup"><span data-stu-id="a8e5a-102">Transaction Support</span></span>
<span data-ttu-id="a8e5a-103">一般而言，規則引擎不支援交易。</span><span class="sxs-lookup"><span data-stu-id="a8e5a-103">The rule engine does not support transactions in general.</span></span> <span data-ttu-id="a8e5a-104">不過，使用以交易方式更新資料庫**DataConnection**物件中的下列步驟所示：</span><span class="sxs-lookup"><span data-stu-id="a8e5a-104">However, you can update a database in a transactional manner by using the **DataConnection** object as shown in the following steps:</span></span>  
  
1.  <span data-ttu-id="a8e5a-105">建立**SqlConnection**物件使用的連接字串，並開啟連接。</span><span class="sxs-lookup"><span data-stu-id="a8e5a-105">Create a **SqlConnection** object by using a connection string, and open the connection.</span></span>  
  
    ```  
    SqlConnection connection = new SqlConnection("Initial Catalog=Northwind;Data Source=(local);Integrated Security=SSPI;");  
    connection.Open();  
    ```  
  
2.  <span data-ttu-id="a8e5a-106">建立**SqlTransaction**藉由呼叫物件**BeginTransaction**您在步驟 1 中建立的連線物件上的方法。</span><span class="sxs-lookup"><span data-stu-id="a8e5a-106">Create a **SqlTransaction** object by calling the **BeginTransaction** method on the connection object you created in step 1.</span></span>  
  
    ```  
    SqlTransaction transaction = connection.BeginTransaction();  
    ```  
  
3.  <span data-ttu-id="a8e5a-107">建立**DataConnection**使用您在步驟 1 和 2 中建立的連線和交易物件的物件。</span><span class="sxs-lookup"><span data-stu-id="a8e5a-107">Create a **DataConnection** object by using the connection and transaction objects you created in steps 1 and 2.</span></span>  
  
    ```  
    DataConnection dc = new DataConnection(datasetName, tableName, connection, transaction);  
    ```  
  
4.  <span data-ttu-id="a8e5a-108">傳遞**DataConnection**物件當做事實連同任何其他事實您想要傳遞給原則，並執行原則。</span><span class="sxs-lookup"><span data-stu-id="a8e5a-108">Pass the **DataConnection** object as a fact along with any other facts you want to pass to the policy, and execute the policy.</span></span>  
  
    ```  
    //Passing a .NET object as a fact along with the data connection  
    MyClass obj = new MyClass();  
    object[] facts = new object[2];  
    facts[0] = dc;  
    facts[1] = obj;  
    Policy pol = new Policy(policyName);  
    policy.Execute(facts);    
    ```  
  
5.  <span data-ttu-id="a8e5a-109">叫用**更新**資料連線物件上的方法。</span><span class="sxs-lookup"><span data-stu-id="a8e5a-109">Invoke the **Update** method on the data connection object.</span></span> <span data-ttu-id="a8e5a-110">執行原則時所有更新作業只是在記憶體中完成的。</span><span class="sxs-lookup"><span data-stu-id="a8e5a-110">All the updates done while executing the policy are done only in memory.</span></span> <span data-ttu-id="a8e5a-111">您必須呼叫**更新**資料連線物件，以更新資料庫上的方法。</span><span class="sxs-lookup"><span data-stu-id="a8e5a-111">You must call the **Update** method on the data connection object to update the database.</span></span>  
  
    ```  
    dc.Update();  
    ```  
  
6.  <span data-ttu-id="a8e5a-112">現在，叫用**認可**或**復原**資料連線物件上根據您自己的邏輯。</span><span class="sxs-lookup"><span data-stu-id="a8e5a-112">Now, invoke **Commit** or **Rollback** on the data connection object based on your own logic.</span></span>  
  
    ```  
    //Checking the value of PropertyA in .net object   
    //to decide whether to commit or rollback  
    if (obj.PropertyA == true)  
    transaction.Commit();  
    else  
    transaction.Rollback();  
  
    ```  
  
7.  <span data-ttu-id="a8e5a-113">關閉連線，並處置原則物件。</span><span class="sxs-lookup"><span data-stu-id="a8e5a-113">Close the connection, and dispose the policy object.</span></span>  
  
    ```  
    sqlCon.Close();  
    policy.Dispose();  
    ```  
  
 <span data-ttu-id="a8e5a-114">以下是包含所有步驟的完整程式碼：</span><span class="sxs-lookup"><span data-stu-id="a8e5a-114">The following code is the complete code with all the steps:</span></span>  
  
```  
SqlConnection connection = new SqlConnection("Initial Catalog=Northwind;Data Source=(local);Integrated Security=SSPI;");  
connection.Open();  
SqlTransaction transaction = connection.BeginTransaction();  
DataConnection dc = new DataConnection(datasetName, tableName, connection, transaction);  
MyClass obj = new MyClass();  
object[] facts = new object[2];  
facts[0] = dc;  
facts[1] = obj;  
Policy pol = new Policy(policyName);  
policy.Execute(facts);    
dc.Update();  
if (obj.PropertyA == true)  
transaction.Commit();  
else  
transaction.Rollback();  
sqlCon.Close();  
policy.Dispose();  
```  
  
## <a name="comments"></a><span data-ttu-id="a8e5a-115">註解</span><span class="sxs-lookup"><span data-stu-id="a8e5a-115">Comments</span></span>  
  
-   <span data-ttu-id="a8e5a-116">您也可以使用**OleDbConnection**和**OleDbTransaction**物件，而不要使用**SqlConnection**和**SqlTransaction**若要以交易方式執行資料庫更新的物件。</span><span class="sxs-lookup"><span data-stu-id="a8e5a-116">You can also use the **OleDbConnection** and **OleDbTransaction** objects instead of using the **SqlConnection** and **SqlTransaction** objects to perform database updates in a transactional manner.</span></span>  
  
-   <span data-ttu-id="a8e5a-117">從原則執行的所有修改作業都是在記憶體中完成的。</span><span class="sxs-lookup"><span data-stu-id="a8e5a-117">All the modifications done from the policy are done in memory.</span></span> <span data-ttu-id="a8e5a-118">您必須叫用**更新**方法**DataConnection**更新資料庫的物件。</span><span class="sxs-lookup"><span data-stu-id="a8e5a-118">You must invoke the **Update** method on the **DataConnection** object to update the database.</span></span>  
  
-   <span data-ttu-id="a8e5a-119">您可以認可或回復交易叫用**認可**或**復原**方法**DataConnection**分別物件。</span><span class="sxs-lookup"><span data-stu-id="a8e5a-119">You can either commit or roll back the transaction by invoking the **Commit** or **Rollback** method of the **DataConnection** objects respectively.</span></span>