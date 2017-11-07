---
title: "不是要變更 SQL Server 設定 |Microsoft 文件"
description: "Max Degree of Parallelism，自動建立統計資料自動更新統計資料，以及重建索引，在 BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b383bfb-c3d9-47d4-b294-f6be94302734
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32186bc9487dc71900c98467a45bc3e67e915f35
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="sql-server-settings-that-should-not-be-changed"></a>不應該變更的 SQL Server 設定
設定時[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]操作整備程序期間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您應該對下列設定進行變更。  
  
## <a name="sql-server-max-degree-of-parallelism"></a>SQL Server 平行處理原則的最大程度  
 最大程度的平行處理原則 (MDOP) 設定為"1"的組態期間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]如[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]instance(s) 裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫。 這是[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體層級設定。 從"1"的值不應該變更此設定。 將這變更為"1"以外的任何可能造成顯著負面影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]預存程序和效能。 如果變更的執行個體的平行處理原則設定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]必須正在執行的其他資料庫應用程式造成負面影響[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體，您應該建立個別的執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]專門用來裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
 平行查詢通常最適合批次處理和決策支援工作負載。 它們都是通常不需要在您具有許多簡短、 快速查詢以平行方式執行交易處理環境中。 此外，變更 MDOP 有時設定原因查詢計畫，以變更，這會導致查詢效能不佳或甚至使用死結[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]查詢。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]預存程序提供正確的聯結，以及可能的情況下才能讓查詢最佳化工具執行的工作量，以及變更計劃重試鎖定提示。 這些預存程序來建構查詢，使得查詢最佳化工具取自圖片盡量提供一致的查詢執行。  
  
 如需詳細資訊，請參閱[KB 899000: BizTalk Server 所使用的 SQL Server 執行個體的平行處理原則設定](https://support.microsoft.com/help/899000/the-parallelism-setting-for-the-instance-of-sql-server-when-you-config)。  
  
## <a name="sql-server-statistics-on-the-messagebox-database"></a>MessageBox 資料庫上的 SQL Server 統計資料  
 下列選項會根據預設，在關閉[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫建立時：  
  
-   自動建立統計資料  
  
-   自動更新統計資料  
  
 請勿啟用這些選項的 MessageBox 資料庫上。 啟用 「 自動建立統計資料 」 和 「 自動更新統計資料 」 選項可能會造成非預期的查詢執行延遲，尤其是在高負載的環境。  
  
 此外，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]預存程序有完全聯結和查詢中指定的鎖定提示。 這樣做可確保最佳查詢計劃由[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中的查詢[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 已知的分佈和預期的結果的查詢。已知傳回資料列的大約數目。 通常不需要統計資料。  
  
 如需詳細資訊，請參閱下列 Microsoft 知識庫文件：  
  
-   **912262**—[「 自動更新統計資料選項、 自動建立統計資料選項和平行處理原則設定關閉的裝載 BizTalk Server BizTalkMsgBoxDB 資料庫的 SQL Server 資料庫執行個體 」](https://support.microsoft.com/help/912262/the-auto-update-statistics-option-the-auto-create-statistics-option-an).  
  
-   **917845**—["您遇到封鎖，死結狀況或其他 SQL Server 問題，當您嘗試連接到 BizTalk Server 中的 BizTalkMsgBoxDb 資料庫"](https://support.microsoft.com/help/917845/you-experience-blocking--deadlock-conditions--or-other-sql-server-issu)。  
  
## <a name="changes-to-the-messagebox-database"></a>MessageBox 資料庫的變更  
 MessageBox 資料庫應該被視為非 Microsoft 應用程式的原始程式碼。 也就是，您應該不 「 調整 」 透過變更資料表、 索引、 預存程序，以及大多數的 SQL Server 資料庫設定 MessageBox 資料庫。 如需詳細資訊，請在 BizTalk 核心引擎的部落格，請參閱[哪些可以和無法與 MessageBox 資料庫伺服器進行](http://go.microsoft.com/fwlink/p/?LinkId=101577)。  
  
## <a name="default-settings-for-the-database-index-rebuilds-and-defragmentation"></a>資料庫索引會重建和重組的預設設定  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不支援索引重組。 「 DBCC INDEXDEFRAG"和"ALTER INDEX … 重新組織...」 不支援，因為它們使用頁面鎖定，這會導致封鎖和死結 （deadlock） 與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]未支援資料庫索引重建作業 （「 DBCC DBREINDEX"和"ALTER INDEX … REBUILD...")，但只應該執行的維護期間時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]未處理的資料。 索引重建時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]正在處理不支援資料。  
  
 如需詳細資訊，請參閱[KB 917845： 發生封鎖，死結狀況或其他 SQL Server 問題，當您嘗試連接到 BizTalk Server 中的 BizTalkMsgBoxDb 資料庫 」](https://support.microsoft.com/help/917845/you-experience-blocking--deadlock-conditions--or-other-sql-server-issu)。  
  
 索引片段不是最多的效能問題的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]因為它可以 DSS 系統或 OLTP 系統執行索引掃描。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]沒有謹慎選擇查詢與更新和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]預存程序不會導致資料表或索引掃描。  
  
 
## <a name="see-also"></a>另請參閱  
 [檢查清單：設定 SQL Server](~/technical-guides/checklist-configuring-sql-server.md)
