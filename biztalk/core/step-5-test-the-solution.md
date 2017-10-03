---
title: "步驟 5： 測試方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ca5301-2ee4-4024-a90a-396ed681d12a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ce7edd1c1f1f8a063e2787cc2acecb3b57cca2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-test-the-solution"></a>步驟 5： 測試方案
此解決方案旨在自動化程序傳送通知給[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，每當在 Salesforce 中關閉新商機的設定當做商機的階段**Closed Won**。 在收到通知之後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]傳送查詢到 Salesforce 擷取與商機相關的產品詳細資料，然後將回應從 Salesforce 插入呼叫的 SQL Server 資料庫資料表**OrderDetails**. 因此，若要測試此解決方案，我們將更新的機會階段**Closed Won** ，如此一來，您必須取得相關的記錄插入 OrderDetails 資料表中 「 訂單 」 資料庫中。  
  
### <a name="to-test-the-solution"></a>測試方案  
  
1.  登入`https://login.salesforce.com/?lt=de`，使用 Salesforce 開發人員的登入認證。  
  
2.  在導覽列中，按一下**機會**，然後按一下 **客戶 1 的機會**。 您建立這個機會在[步驟 2： 設定 Salesforce 系統](../core/step-2-set-up-the-salesforce-system.md)。  
  
3.  在**機會詳細**區段中，記下中相關聯的產品的**產品 （標準）** > 一節。 您在這一節下最後取得插入的 SQL Server 資料庫的值。 在下**機會詳細**區段中，按一下**編輯**按鈕，然後將值變更**階段**欄位設為**Closed Won**。 按一下 **[儲存]**。  
  
     ![編輯現有的機會](../core/media/bts-sf-edit-opp.jpg "BTS_SF_Edit_Opp")  
  
4.  SQL Server Management Studio，在上執行的查詢**OrderDetails**来選取所有資料列的資料表。  
  
     ![SQL 查詢的輸出](../core/media/bts-sf-sql-query.jpg "BTS_SF_SQL_Query")  
  
     請注意，它會列出有機會在您變更此階段中所列的產品。  
  
     ![新增產品至商機](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")  
  
 您可以看到在其中輸入記錄**OrderDetails**資料表對應至在 Salesforce 中建立一組指定的產品銷售的機會。 您可以藉由建立新的機會，並將新的產品產生關聯的機會，重複這些步驟。