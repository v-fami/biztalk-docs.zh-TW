---
title: 瞭解 BizTalk Adapter for SQL Server |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 302a7f20-ffa2-49f1-a4c4-dd713adc23e1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3fc14b7d9da40edd56c4c4cc4fa6b795386518db
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965300"
---
# <a name="understand-biztalk-adapter-for-sql-server"></a>瞭解 BizTalk Adapter for SQL Server
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]可讓服務導向程式設計的存取方式讓您可以與外部系統互動。 配接器用戶端提供下列優點：  
  
-   **一致的設計階段經驗**。 配接器會提供一般和使用者易記的設計階段經驗，針對瀏覽、 搜尋和擷取的 LOB 成品的中繼資料。  
  
-   **各種程式設計選項**。 配接器提供選擇的程式設計模型包括 Windows Communication Foundation (WCF) 通道模型，WCF 服務模型中，ADO.NET 中，Web 服務，或 BizTalk 支援模型。  
  
-   **跨 Lob 統一經驗**。 標準化使用 WCF 配接器和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並因此提供一致的體驗的任何 LOB 系統的存取。  
  
 如所述，配接器會建立最上層的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供通用的基礎建置各種 BizTalk Server 和 Microsoft Office 等用戶端應用程式可以取用的整合配接器。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]對齊由公開為 Windows Communication Foundation (WCF) 通道整合配接器的 Microsoft 服務策略配接器的策略。 如需有關[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，請參閱[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]文件。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]連同安裝文件[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]通常下\<安裝磁碟機\>: \Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents。  
  
 若要執行 SQL Server 資料庫上的作業，配接器用戶端必須存取到相關資料表、 程序、 檢視、 純量函數，而且資料表值函式。 資料庫資料表會儲存在 SQL Server 資料庫中的基本單位。 外部應用程式，都可以選取、 插入、 刪除和使用 SQL 陳述式來更新資料表的資料。 應用程式也可以使用程序、 檢視、 純量函數和資料表值函式中存取資料表中的資料。 與[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]，配接器用戶端可以瀏覽成品，例如資料表、 程序、 檢視和 SQL Server 資料庫中的其他這類項目。 配接器用戶端可以選取方案，它們需要的成品，並擷取這些成品的中繼資料。 這可讓使用者存取，並執行 SQL Server 資料庫中的成品上的作業。  
  
 此區段會列出的功能[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [BizTalk Adapter for SQL Server 概觀](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)  
  
-   [BizTalk Adapter for SQL Server 中的重要功能](../../adapters-and-accelerators/adapter-sql/key-features-in-biztalk-adapter-for-sql-server.md) 
  
-   [BizTalk adapter for SQL Server 的限制](../../adapters-and-accelerators/adapter-sql/limitations-of-biztalk-adapter-for-sql-server.md)  
  
## <a name="see-also"></a>請參閱  
[開始使用 BizTalk adapter for SQL](../../adapters-and-accelerators/adapter-sql/get-started-with-the-biztalk-adapter-for-sql.md)