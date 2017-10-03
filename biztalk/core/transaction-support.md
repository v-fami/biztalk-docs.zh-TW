---
title: "交易支援 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataConnection object
- Business Rules Framework, code samples
- Business Rules Framework, programming
ms.assetid: 84faac2f-6229-4692-9d1a-bf62d87d69bb
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57fc1d7a1edd18663cb21a85037cf3e662948fc4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-support"></a>交易支援
一般而言，規則引擎不支援交易。 不過，使用以交易方式更新資料庫**DataConnection**物件中的下列步驟所示：  
  
1.  建立**SqlConnection**物件使用的連接字串，並開啟連接。  
  
    ```  
    SqlConnection connection = new SqlConnection("Initial Catalog=Northwind;Data Source=(local);Integrated Security=SSPI;");  
    connection.Open();  
    ```  
  
2.  建立**SqlTransaction**藉由呼叫物件**BeginTransaction**您在步驟 1 中建立的連線物件上的方法。  
  
    ```  
    SqlTransaction transaction = connection.BeginTransaction();  
    ```  
  
3.  建立**DataConnection**使用您在步驟 1 和 2 中建立的連線和交易物件的物件。  
  
    ```  
    DataConnection dc = new DataConnection(datasetName, tableName, connection, transaction);  
    ```  
  
4.  傳遞**DataConnection**物件當做事實連同任何其他事實您想要傳遞給原則，並執行原則。  
  
    ```  
    //Passing a .NET object as a fact along with the data connection  
    MyClass obj = new MyClass();  
    object[] facts = new object[2];  
    facts[0] = dc;  
    facts[1] = obj;  
    Policy pol = new Policy(policyName);  
    policy.Execute(facts);    
    ```  
  
5.  叫用**更新**資料連線物件上的方法。 執行原則時所有更新作業只是在記憶體中完成的。 您必須呼叫**更新**資料連線物件，以更新資料庫上的方法。  
  
    ```  
    dc.Update();  
    ```  
  
6.  現在，叫用**認可**或**復原**資料連線物件上根據您自己的邏輯。  
  
    ```  
    //Checking the value of PropertyA in .net object   
    //to decide whether to commit or rollback  
    if (obj.PropertyA == true)  
    transaction.Commit();  
    else  
    transaction.Rollback();  
  
    ```  
  
7.  關閉連線，並處置原則物件。  
  
    ```  
    sqlCon.Close();  
    policy.Dispose();  
    ```  
  
 以下是包含所有步驟的完整程式碼：  
  
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
  
## <a name="comments"></a>註解  
  
-   您也可以使用**OleDbConnection**和**OleDbTransaction**物件，而不要使用**SqlConnection**和**SqlTransaction**若要以交易方式執行資料庫更新的物件。  
  
-   從原則執行的所有修改作業都是在記憶體中完成的。 您必須叫用**更新**方法**DataConnection**更新資料庫的物件。  
  
-   您可以認可或回復交易叫用**認可**或**復原**方法**DataConnection**分別物件。