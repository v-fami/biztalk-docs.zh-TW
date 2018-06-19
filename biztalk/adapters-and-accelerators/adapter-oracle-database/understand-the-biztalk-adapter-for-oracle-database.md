---
title: 瞭解 BizTalk Adapter for Oracle 資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF LOB Adapter SDK
- features of Oracle database adapter
- table
- adapter client
- service model
- WCF
- artifacts
- database tables
- adapters, features
- Windows Communication Foundation
- adapter features
- channel model
ms.assetid: a8691957-0430-4cba-83f8-b60c21a86849
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb2d3603bb6d7c64d355c88420167344f564ddd8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961172"
---
# <a name="understand-the-biztalk-adapter-for-oracle-database"></a>瞭解 BizTalk Adapter for Oracle 資料庫
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]啟用服務導向程式設計的存取，以便與外部系統互動。 配接器用戶端提供下列優點：  
  
-   **一致的設計階段經驗**。 配接器會提供一般和使用者易記的設計階段經驗，針對瀏覽、 搜尋和擷取的 LOB 成品的中繼資料。  
  
-   **各種程式設計選項**。 配接器提供選擇的程式設計模型包括 Windows Communication Foundation (WCF) 通道模型，WCF 服務模型中，ADO.NET 中，Web 服務，或 BizTalk 支援模型。  
  
-   **跨 Lob 統一經驗**。 標準化使用 WCF 配接器和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並因此提供一致的體驗的任何 LOB 系統的存取。  
  
 如所述，配接器會建立最上層的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供通用的基礎建置各種 BizTalk Server 和 Microsoft Office 等用戶端應用程式可以取用的整合配接器。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]對齊由公開為 Windows Communication Foundation (WCF) 通道整合配接器的 Microsoft 服務策略配接器的策略。 如需有關[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，請參閱[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]文件。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]連同安裝文件[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]通常下\<安裝磁碟機\>: \Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents。  
  
 若要執行的 Oracle 資料庫作業，配接器用戶端必須存取相關的資料表、 函數和程序。 資料庫資料表是 Oracle 資料庫中儲存的基本單位。 外部應用程式可以新增或移除資料表中的資料，使用 SQL 陳述式。 應用程式也可以使用檢視、 函數和程序來存取資料表中的資料。 與[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]，配接器用戶端可以瀏覽成品，例如資料表、 程序、 封裝、 檢視和 Oracle 資料庫中的其他這類項目。 配接器用戶端可以選取他們為其方案所需，並擷取中繼資料，這些成品的成品。 這可讓使用者存取，並執行的 Oracle 資料庫中的成品上的作業。  
  
 此區段會列出的功能[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [BizTalk Adapter for Oracle Database 概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)  
  
-   [BizTalk Adapter for Oracle 資料庫中的重要功能](../../adapters-and-accelerators/adapter-oracle-database/key-features-in-biztalk-adapter-for-oracle-database.md)  
  
-   [Oracle Database 的 BizTalk 配接器的限制](../../adapters-and-accelerators/adapter-oracle-database/limitations-of-biztalk-adapter-for-oracle-database.md)  
  
## <a name="see-also"></a>請參閱  
[BizTalk Server 使用者入門](../../core/getting-started-with-biztalk-server.md)