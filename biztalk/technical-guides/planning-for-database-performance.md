---
title: 規劃資料庫效能 |Microsoft 文件
ms.custom: ''
ms.date: 11/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7212fa37-88e0-4b5f-af97-c72063357645
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 878320cf7c6a5762626087964033430afcf611cf
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009503"
---
# <a name="planning-for-database-performance"></a>規劃資料庫效能

## <a name="overview"></a>概觀
Microsoft BizTalk Server 是極資料庫密集的應用程式，可能需要多達 13 個不同的資料庫，Microsoft SQL Server 中建立。 BizTalk Server 資料庫大量本質，因為它是非常重要您選擇適當的版本和版本的 SQL Server 將裝載 BizTalk Server 資料庫。 執行 SQL Server 裝載 BizTalk Server 資料庫之電腦的效能最佳化，請遵循本主題中以及在建議[BizTalk Server 資料庫最佳化](optimizing-database-performance.md)。
  

> [!NOTE]  
>  雖然本指南針對 BizTalk Server 和 SQL Server 的其他版本所撰寫，您可能可以在較新版本，使用相同的建議。
  
## <a name="considerations-for-sql-server-editions"></a>SQL Server 版本的考量  
 BizTalk Server 資料庫應該設定為在專用 SQL Server 執行個體盡可能上執行。 BizTalk Server 資料庫大量應用程式，因此 BizTalk Server 電腦，明確劃分且包含 BizTalk Server 資料庫的 SQL Server 電腦將可改善效能，應該考量實際執行 BizTalk Server 中的最佳做法環境。  
  
 各種 SQL Server 版本提供不同功能可能會影響 BizTalk Server 環境的效能。 例如，在高負載情況下可用於 32 位元版本的 SQL Server 可用的資料庫鎖定數目可能會超過，即不利的 BizTalk 方案的效能。 請考慮罩上的 SQL Server 64 位元版本的 MessageBox 資料庫，如果您在測試環境中發生 「 鎖定不足 」 錯誤。 在 64 位元版本的 SQL Server 上，可用的鎖定數目大幅提高。  
  
 請考慮下的表決定 database engine 功能時，您必須針對您的 BizTalk 環境。 對於小型的解決方案，例如當執行 BizTalk Server Branch Edition 上，SQL Server Workgroup Edition 應已足夠裝載 BizTalk Server 資料庫。 大型的標尺，需要叢集支援，企業層級方案的 BizTalk 記錄傳送支援或 Analysis Services 支援部門，則需要 SQL Server Enterprise Edition 來主控資料庫。  
  
|SQL Server 版本|64 位元支援|多重執行個體的支援|叢集支援|Analysis Services|  
|---|---|---|---|---|  
|SQL Server Enterprise Edition|是|是|是|是|  
|SQL Server Standard Edition|是|是|是 （節點 2）|是|  
|SQL Server Workgroup Edition|是|是|否|否|  
  
> [!NOTE]  
>  BAM RTA 需要 SQL Server Enterprise Edition。  
  
 版本支援的功能完整清單，請參閱[支援的 SQL Server 的版本功能](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)。