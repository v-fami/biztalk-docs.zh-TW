---
title: SQL Server 設定不會變更 |Microsoft Docs
description: Max Degree of Parallelism，自動建立統計資料自動更新統計資料，以及重建索引，在 BizTalk Server
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b383bfb-c3d9-47d4-b294-f6be94302734
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60479097dc9e56c2bc0c525d0de7d7a33afccaa5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978263"
---
# <a name="sql-server-settings-that-should-not-be-changed"></a>不應變更的 SQL Server 設定
設定時[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]的作業整備程序期間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您應該對下列設定進行變更。  
  
## <a name="sql-server-max-degree-of-parallelism"></a>SQL Server 平行處理原則的最大程度  
 最大程度的平行處理原則 (MDOP) 設定為"1"的組態期間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]for[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫。 這是[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體層級設定。 此設定不應該變更為"1"的值。 將這變更為"1"以外的任何項目可以有顯著的負面影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]預存程序和效能。 如果變更的執行個體的平行處理原則設定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]會有其他正在執行的資料庫應用程式造成不良的影響[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體，您應該建立個別的執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]專門用來裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
 平行查詢通常最適合用於批次處理，決策支援工作負載。 它們通常都不希望出現在您有許多簡短、 快速查詢以平行方式執行交易處理環境。 此外，變更 MDOP 有時設定會導致查詢計劃變更，這會導致查詢效能不佳，或甚至死結與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]查詢。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]預存程序提供正確的聯結，並盡可能試著讓查詢最佳化工具執行太多工作，並將方案變更鎖定提示。 這些預存程序會藉由建構查詢，使得查詢最佳化工具會從圖片盡可能提供一致的查詢執行。  
  
 如需詳細資訊，請參閱 < [KB 899000: BizTalk Server 所使用的 SQL Server 執行個體的平行處理原則設定](https://support.microsoft.com/help/899000/the-parallelism-setting-for-the-instance-of-sql-server-when-you-config)。  
  
## <a name="sql-server-statistics-on-the-messagebox-database"></a>MessageBox 資料庫的 SQL Server 統計資料  
 下列的選項為關閉狀態中的預設[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫建立時：  
  
- 自動建立統計資料  
  
- 自動更新統計資料  
  
  請勿啟用這些選項的 MessageBox 資料庫上。 啟用 「 自動建立統計資料 」 和 「 自動更新統計資料 」 選項可能會導致不想要的查詢延遲執行，尤其是一個高負載的環境。  
  
  颾魤 ㄛ[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]預存程序有確切的聯結和查詢上指定的鎖定提示。 這為了確保最佳的查詢計畫由[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中的查詢[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 已知的發行版本和預期之查詢的結果;已知傳回的資料列的近似數目。 通常不需要統計資料。  
  
  如需詳細資訊，請參閱下列 Microsoft 知識庫文件：  
  
- **912262**—[「 自動更新統計資料選項、 自動建立統計資料選項和平行處理原則設定關閉的裝載 BizTalk Server BizTalkMsgBoxDB 資料庫的 SQL Server 資料庫執行個體 」](https://support.microsoft.com/help/912262/the-auto-update-statistics-option-the-auto-create-statistics-option-an).  
  
- **917845**—[「 您遇到封鎖，死結狀況或其他 SQL Server 問題，當您嘗試連接到 BizTalk Server 中 BizTalkMsgBoxDb 資料庫 」](https://support.microsoft.com/help/917845/you-experience-blocking--deadlock-conditions--or-other-sql-server-issu)。  
  
## <a name="changes-to-the-messagebox-database"></a>MessageBox 資料庫的變更  
 MessageBox 資料庫應該被視為非 Microsoft 應用程式來源程式碼。 也就是您應該不 「 調整 」 透過變更資料表、 索引、 預存程序和大部分的 SQL Server 資料庫設定 MessageBox 資料庫。 如需詳細資訊，請在 BizTalk 核心引擎的部落格，請參閱[功能可以和無法使用的 MessageBox 資料庫伺服器](http://go.microsoft.com/fwlink/p/?LinkId=101577)。  
  
## <a name="default-settings-for-the-database-index-rebuilds-and-defragmentation"></a>資料庫索引重建和重組的預設設定  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不支援重組的索引。 「 DBCC INDEXDEFRAG"和"ALTER INDEX... 重新組織...」 由於它們使用頁面鎖定，這可能會造成封鎖和死結 （deadlock） 與不支援的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行支援資料庫索引重建 （「 DBCC DBREINDEX"和"ALTER INDEX... 重建..."），但只應進行的維護期間時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]未處理的資料。 索引重建時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]正在處理不支援的資料。  
  
 如需詳細資訊，請參閱 < [KB 917845： 您遇到封鎖，死結狀況或其他 SQL Server 問題，當您嘗試連接到 BizTalk Server 中 BizTalkMsgBoxDb 資料庫 「](https://support.microsoft.com/help/917845/you-experience-blocking--deadlock-conditions--or-other-sql-server-issu)。  
  
 索引片段不是最多的效能問題的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]就像在 DSS 系統或執行索引掃描的 OLTP 系統。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 未經過挑選的查詢和更新和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]預存程序不會導致資料表或索引掃描。  
  
 
## <a name="see-also"></a>另請參閱  
 [檢查清單：設定 SQL Server](~/technical-guides/checklist-configuring-sql-server.md)
