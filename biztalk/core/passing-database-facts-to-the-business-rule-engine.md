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
# <a name="passing-database-facts-to-the-business-rule-engine"></a>將資料庫事實傳入商務規則引擎資料庫
當您使用 「 商務規則編輯器 」 工具來測試原則，要求 DataConnection/TypedDataTable 物件當做事實時，DataConnection/TypedDataTable 物件是自動為您建立，並判斷提示至 「 商務規則引擎工作記憶體。 此外，也會自動認可由該原則更新的任何資料庫。  
  
 反之，當您叫用從協調流程的原則，使用 [呼叫規則] 圖形或以程式設計方式，DataConnection/TypedDataTable 物件不為您建立，而且資料庫更新並未經過認可自動。 在此情況下，您應該建立 DataConnection/TypedDataTable 物件、 將它當做事實傳遞至規則引擎，並使用下列方法之一，以程式設計方式認可資料庫變更。  
  
## <a name="passing-a-dataconnection-object-from-an-orchestration"></a>從協調流程傳遞 DataConnection 物件  
 下列範例程式碼將示範如何在協調流程中建立 DataConnection 物件、設定 [呼叫規則] 圖形以便將 DataConnection 物件當做參數傳遞，並在執行原則之後認可任何資料庫更新。  
  
1.  在 [協調流程設計師] 中開啟協調流程時，使用 [協調流程檢視] 索引標籤建立下列變數。  
  
    ```  
    DataCon of type Microsoft.RuleEngine.DataConnection   
    SqlCon of type System.Data.SqlClient.SqlConnection   
    SqlTran of type System.Data.SqlClient.SqlTransaction   
    ```  
  
2.  在 [呼叫規則] 圖形之前 「 運算式 」 圖形，建立 DataConnection 物件。 下列程式碼範例示範如何建立 DataConnection 物件。  
  
    ```  
    SqlCon.ConnectionString = "Data Source=(local);Initial Catalog=Test;Integrated Security=SSPI";   
    SqlCon.Open();   
    SqlTran = SqlCon.BeginTransaction();   
    DataCon = new Microsoft.RuleEngine.DataConnection("test", "FlagTable", SqlCon, SqlTran);    
    ```  
  
3.  設定要做為參數傳遞 DataCon 變數呼叫規則 」 圖形。 如需詳細資訊，請參閱[如何使用 [呼叫規則] 圖形](../core/how-to-use-the-call-rules-shape.md)。  
  
4.  在 [呼叫規則] 圖形之後的 [運算式] 圖形中，認可原則所做的資料庫變更。 下列程式碼範例將示範如何認可原則所做的資料庫變更。  
  
    ```  
    DataCon.Update();   
    SqlTran.Commit();  
    ```  
  
> [!NOTE]
>  您必須使用[SqlTransaction](http://msdn.microsoft.com/library/system.data.sqlclient.sqltransaction.aspx)物件在原則更新資料庫。  
  
## <a name="passing-a-dataconnection-object-from-a-fact-retriever"></a>從事實擷取器傳遞 DataConnection 物件  
 以下是從事實擷取器元件傳遞 DataConnection 物件所需的一般執行步驟。  
  
1.  建立事實擷取器元件，以建立並判斷提示 DataConnection 物件至規則引擎的工作記憶體中。 如需如何建立事實擷取器元件的詳細資訊，請參閱[如何建立事實擷取器](../core/how-to-create-a-fact-retriever.md)。  
  
2.  實作[IFactRemover](http://msdn.microsoft.com/library/Microsoft.RuleEngine.IFactRemover.aspx)介面上事實擷取器元件，以及認可資料庫變更從[UpdateFactsAfterExecution](http://msdn.microsoft.com/library/microsoft.ruleengine.ifactremover.updatefactsafterexecution.aspx)方法。 規則引擎會在完成執行原則之後呼叫這個方法。  
  
3.  使用「商務規則編輯器」工具將原則設定為使用事實擷取器元件。 如需詳細資訊，請參閱[如何設定原則的事實擷取器](../core/how-to-configure-a-fact-retriever-for-a-policy.md)。  
  
## <a name="see-also"></a>另請參閱  
 [商務規則引擎中的資料存取](../core/data-access-in-the-business-rule-engine.md)   
 [如何建立事實擷取器](../core/how-to-create-a-fact-retriever.md)   
 [如何設定原則的事實擷取器](../core/how-to-configure-a-fact-retriever-for-a-policy.md)