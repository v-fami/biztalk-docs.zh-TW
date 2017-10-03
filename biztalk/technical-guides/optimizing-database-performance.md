---
title: "最佳化資料庫效能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a95caf60-f1f5-458f-8a81-0aead88f07be
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe9148c5b14c5c915de9a8d16699856922e051a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-database-performance"></a>最佳化資料庫效能
BizTalk Server 是可能需要多達 13 個資料庫在 SQL Server 中建立的極大量資料庫的應用程式。 因為 BizTalk server 的主要設計目標之一是為了確保任何訊息都會遺失，BizTalk Server 會保存到磁碟的資料很棒的頻率和此外，這樣做，MSDTC 交易的內容中。 因此，資料庫效能極為重要的任何 BizTalk Server 解決方案的整體效能。  
  
 本章節描述一般的方法最大化的 SQL Server 效能，以及資料庫效能最大化 BizTalk Server 環境專用的方法。 如需 BizTalk 資料庫效能最佳化的詳細資訊，請參閱[BizTalk 資料庫最佳化白皮書](http://go.microsoft.com/fwlink/?LinkId=101578)(http://go.microsoft.com/fwlink/?LinkId=101578)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [預先設定資料庫 Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)  
  
-   [組態後資料庫 Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)  
  
-   [Databases2 最佳化檔案群組](../technical-guides/optimizing-filegroups-for-the-databases2.md)  
  
-   [BizTalk Server MessageBox 資料庫檔案群組的 SQL 指令碼](../technical-guides/biztalk-server-messagebox-database-filegroups-sql-script.md)  
  
-   [監視 SQL Server 效能](../technical-guides/monitoring-sql-server-performance.md)