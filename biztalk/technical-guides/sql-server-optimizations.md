---
title: "SQL Server 最佳化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb735b54-595e-4dd0-9e4d-9a5e7a007a78
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3783c09b1155202ac8fe5a964d16c24d33082c26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sql-server-optimizations"></a>SQL Server 最佳化
BizTalk Server 是極資料庫密集的應用程式可能需要建立的 SQL Server 中的多達 13 個資料庫。 因為 BizTalk server 的主要設計目標之一是為了確保任何訊息都會遺失，BizTalk Server 會保存到磁碟的資料很棒的頻率和此外，這樣做，MSDTC 交易的內容中。 因此，資料庫效能極為重要的任何 BizTalk Server 解決方案的整體效能。  
  
 本章節描述一般的方法最大化的 SQL Server 效能，以及資料庫效能最大化 BizTalk Server 環境專用的方法。 如需有關最佳化 BizTalk 資料庫效能，請參閱在 BizTalk 資料庫最佳化 TechNet 文章[http://go.microsoft.com/fwlink/?LinkId=118001](http://go.microsoft.com/fwlink/?LinkId=118001)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [預先設定資料庫 Optimizations1](../technical-guides/pre-configuration-database-optimizations1.md)  
  
-   [組態後資料庫 Optimizations1](../technical-guides/post-configuration-database-optimizations1.md)  
  
-   [Databases1 最佳化檔案群組](../technical-guides/optimizing-filegroups-for-the-databases1.md)