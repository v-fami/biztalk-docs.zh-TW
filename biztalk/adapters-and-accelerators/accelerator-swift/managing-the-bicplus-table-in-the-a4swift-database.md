---
title: "管理 Bicplus 資料庫中的資料表 A4SWIFT |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Bank Identifier Code (BIC), Bicplus table
- A4SWIFT database, Bicplus table
- Bicplus table
ms.assetid: a255cdea-5ed4-4481-97f1-8425877a76d6
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 730998918beb464b00b871f8ab04060a7cd59af6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-the-bicplus-table-in-the-a4swift-database"></a>管理 Bicplus 資料表 A4SWIFT 資料庫中
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]執行 BIC 驗證使用 BIC 項目的資料表。 這個資料表可以在任一個 Bicplus 資料表[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫或自訂資料庫中的資料表。  
  
 若要管理這個資料表，您必須使用來自 SWIFT BIC 值擴展。 如果您使用自訂資料庫，您也必須匯出中的 SQL 檢視[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]到自訂資料庫的資料庫。  
  
## <a name="importing-bic-data-from-the-swift-bicplus-database"></a>從 SWIFT Bicplus 資料庫匯入 BIC 資料  
 您必須填入來自 SWIFT BIC 值 （預設或自訂的資料表） 的 BIC 項目的資料表。 SWIFT BIC 資料均可在[!INCLUDE[btsExcel](../../includes/btsexcel-md.md)]試算表或每月更新的 Oracle 資料庫中。 如需有關 SWIFT BIC 資料的詳細資訊，請移至[http://go.microsoft.com/fwlink/?LinkId=27885](http://go.microsoft.com/fwlink/?LinkId=27885)。  
  
 如果您使用自訂資料庫，您必須從 SWIFT Bicplus 資料庫匯出 BIC 資料到自訂資料庫。 您必須  
  
 您可以將資料匯入從 BIC [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] SWIFT 所提供的 Bicplus 資料表的試算表[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫，因為它們彼此相容。 如果您匯入資料來自 SWIFT 的試算表非[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫時，請確定欄位和資料庫，特別是 BIC 資料行中的資料行是否相容 SWIFT 的試算表。  
  
 它會發行 SWIFT 資料表中的程式碼以更新目的地資料表時，匯入作業並不會移除任何未發行的 BIC 代碼。  
  
 Bicplus 資料表所做的變更[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫登入[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]記錄檔。  
  
#### <a name="to-import-bic-data-from-the-swift-bicplus-database"></a>從 SWIFT Bicplus 資料庫匯入 BIC 資料  
  
1.  按一下**啟動**，指向 **所有程式**，指向 inistalled 版本的 SQL Server，然後按一下**SQL Server Management Studio**。  
  
2.  在 連接到伺服器 對話方塊中，按一下 **連接**。  
  
3.  在 [Microsoft SQL Server Management Studio] 視窗中，展開伺服器節點，然後**資料庫**。  
  
4.  以滑鼠右鍵按一下**A4SWIFT**，指向 **工作**，然後按一下 **匯入資料**。  
  
5.  在 SQL Server 匯入和匯出精靈歡迎使用] 頁面中，按一下 [**下一步**。  
  
6.  在**選擇資料來源**頁面上，如果從 SWIFT Bicplus 匯入 BIC 資料[!INCLUDE[btsExcel](../../includes/btsexcel-md.md)]試算表，選取**Microsoft Excel**中**資料來源**文字方塊。 位置的試算表中，瀏覽並選取試算表中的檔案名稱**Excel 檔案路徑**文字方塊。 按一下 **[下一步]**。  
  
     如果匯入 BIC 資料，從 Oracle 資料庫，選取**Microsoft ODBC Driver for Oracle**中**資料來源**文字方塊。 輸入 Oracle 資料庫時，以及使用者名稱和密碼以連接到該伺服器，然後按一下所需的伺服器**下一步**。  
  
7.  在**選擇目的地**頁面上，確認**Microsoft OLE DB Provider for SQL Server**輸入**目的地**文字方塊中，且**使用Windows 驗證**已選取。 如果您在擴展 Bicplus 資料表中的[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫中，確認**A4SWIFT**輸入**資料庫**文字方塊。 如果您使用自訂資料庫，輸入該資料庫中的名稱**資料庫**文字方塊。 按一下 **[下一步]**。  
  
8.  在**選取資料表複製或查詢**頁面上，確認**從一或多個資料表或檢視表複製資料**已選取。 如果您要使用查詢來指定的資料，請選取**撰寫查詢來指定要傳送的資料**。 按一下 **[下一步]**。  
  
9. 在**選取來源資料表和檢視**頁面上，按一下**Bicplus**中**來源**資料行中，選取**Bicplus**中**目的地**資料行，然後再按一下**下一步**。  
  
10. 在**儲存並執行封裝**頁面上，輸入適當的排程資訊，然後按**下一步**。  
  
11. 在**完成精靈**頁面上，檢閱摘要，然後按一下**完成**。  
  
## <a name="importing-sql-views-from-the-a4swift-database-into-a-custom-database"></a>將匯入 SQL 檢視從 A4SWIFT 資料庫自訂資料庫  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式會安裝在兩個 SQL 檢視[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫。 一個檢視為 8 個字元 BICs 和另一個則用於 BICs 11 個字元。  
  
 如果您使用自訂的資料庫，而不是[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫，您必須將自訂資料庫匯入這些 SQL 檢視。 您藉由在 Query Analyzer 執行 CreateBICViews.sql 指令碼。 此指令碼位於\<*磁碟機*>: \Program Files\Microsoft BizTalk Accelerator for SWIFT/指令碼。  
  
#### <a name="to-import-sql-views-from-the-a4swift-database-into-a-custom-database"></a>若要從 A4SWIFT 資料庫的 SQL 檢視表匯入自訂資料庫  
  
1.  在 Windows 檔案總管 中，移至\<*磁碟機*>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\Scripts。 按兩下**CreateBICViews.sql**。  
  
2.  在 連接到伺服器 對話方塊中，按一下 **連接**。  
  
3.  在 [Microsoft SQL Server Management Studio] 視窗中，選取**A4SWIFT**資料庫文字方塊中。  
  
4.  在 [查詢] 窗格中，如果您儲存 BICs 名為"Bicplus"以外的資料表中，尋找**dbo。Bicplus**檢視中**dbo。Bic11**，並將它變更為適當的資料表名稱。 對檢視執行相同的**dbo。Bic8**。  
  
5.  如果您要將 BICs 儲存名為"BIC"以外的資料行中，尋找**BIC**中**選取**，**其中**，和**ORDER BY**子句，和請將它變更為適當的資料行名稱。  
  
6.  按一下 **[執行]**。  
  
## <a name="see-also"></a>另請參閱  
 [啟用驗證的銀行識別項代碼](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)