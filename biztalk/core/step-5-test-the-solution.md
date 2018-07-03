---
title: 步驟 5： 測試解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5ca5301-2ee4-4024-a90a-396ed681d12a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33a51cda93a1c2cdd6f5a70ebd62bf1d9ce05a7e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020849"
---
# <a name="step-5-test-the-solution"></a>步驟 5： 測試方案
此解決方案的目標是在自動化程序傳送通知給[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，每次在 Salesforce 中關閉新的商機藉由設定為商機的階段**Closed Won**。 收到通知後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將查詢傳送到 Salesforce 擷取機會，相關的產品詳細資料，然後插入回應從 Salesforce 呼叫的 SQL Server 資料庫資料表**OrderDetails**. 因此，若要測試此解決方案，我們將更新的階段有機會**Closed Won** ，如此一來，您必須取得相關的記錄插入訂單資料庫中的 [OrderDetails] 資料表中。  
  
### <a name="to-test-the-solution"></a>測試方案  
  
1. 登入`https://login.salesforce.com/?lt=de`，使用 Salesforce 開發人員登入認證。  
  
2. 在導覽列中，按一下**機會**，然後按一下**客戶 1 的機會**。 您已建立在這個機會[步驟 2： 設定 Salesforce 系統](../core/step-2-set-up-the-salesforce-system.md)。  
  
3. 在 **機會詳細資料**區段中，記下中相關聯的產品**產品 （標準）** 一節。 此區段下您最後會插入至 SQL Server 資料庫中的值。 底下**機會詳細資料**區段中，按一下**編輯**按鈕，然後將值變更**階段**欄位**Closed Won**。 按一下 **[儲存]**。  
  
    ![編輯現有的機會](../core/media/bts-sf-edit-opp.jpg "BTS_SF_Edit_Opp")  
  
4. 在 SQL Server Management Studio 上執行查詢**OrderDetails**来選取所有資料列的資料表。  
  
    ![SQL 查詢的輸出](../core/media/bts-sf-sql-query.jpg "BTS_SF_SQL_Query")  
  
    請注意，它會列出有機會在您變更階段中所列的產品。  
  
    ![新增產品至商機](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")  
  
   您可以看到在其中輸入資料錄**OrderDetails**資料表對應到 Salesforce 中建立的一組指定的產品銷售良機。 您可以藉由建立新的商機，並將新的產品產生關聯的機會，重複這些步驟。