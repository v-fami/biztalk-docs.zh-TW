---
title: SQL Server 最佳化 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb735b54-595e-4dd0-9e4d-9a5e7a007a78
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36317d99387fde1d7b5e1c56b45255129daedb25
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
ms.locfileid: "29710801"
---
# <a name="sql-server-optimizations"></a>SQL Server 最佳化
BizTalk Server 是極資料庫密集的應用程式可能需要建立的 SQL Server 中的多達 13 個資料庫。 因為 BizTalk server 的主要設計目標之一是為了確保任何訊息都會遺失，BizTalk Server 會保存到磁碟的資料很棒的頻率和此外，這樣做，MSDTC 交易的內容中。 因此，資料庫效能極為重要的任何 BizTalk Server 解決方案的整體效能。  
  
本章節描述一般的方法最大化的 SQL Server 效能，以及資料庫效能最大化 BizTalk Server 環境專用的方法。 下列連結也是很好的資源： 

- [BizTalk Server： 安裝、 調整大小、 部署和維護解決方案的建議](https://social.technet.microsoft.com/wiki/contents/articles/666.biztalk-server-recommendations-for-installing-sizing-deploying-and-maintaining-a-solution.aspx)

- [BizTalk Server 效能最佳化指南](biztalk-server-2013-performance-optimization-guide.md)

  
## <a name="next-steps"></a>後續的步驟
  
-   [預先設定資料庫最佳化](../technical-guides/pre-configuration-database-optimizations1.md)  
  
-   [後置設定資料庫最佳化](../technical-guides/post-configuration-database-optimizations1.md)  
  
-   [最佳化資料庫的檔案群組](../technical-guides/optimizing-filegroups-for-the-databases1.md)