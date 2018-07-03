---
title: 了解 BizTalk Adapter for SQL Server |Microsoft Docs
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
ms.openlocfilehash: ea21a06ad5d87e94118aaa45e2f6f541627aae9b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996928"
---
# <a name="understand-biztalk-adapter-for-sql-server"></a>了解 BizTalk Adapter for SQL Server
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]啟用服務導向程式設計使得與外部系統互動的存取。 配接器用戶端提供下列優點：  
  
- **一致的設計階段經驗**。 配接器會提供一般和方便使用的設計階段經驗，針對瀏覽、 搜尋和擷取的 LOB 成品的中繼資料。  
  
- **各種程式設計選項**。 配接器會提供各種程式設計模型，包括 Windows Communication Foundation (WCF) 通道模型，WCF 服務模型中，ADO.NET 中，Web 服務，或 BizTalk 支援的模型。  
  
- **統一的體驗，跨 Lob**。 使用 WCF 配接器將標準化和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並因此提供一致的體驗的任何 LOB 系統的存取。  
  
  如前所述，配接器是以 WCF LOB 配接器 SDK 為基礎。 WCF LOB 配接器 SDK 建置可取用各種不同的用戶端應用程式，例如 BizTalk Server 和 Microsoft Office 的整合配接器提供的通用基礎。 WCF LOB 配接器 SDK 公開為 Windows Communication Foundation (WCF) 通道的整合配接器會將對齊配接器策略，Microsoft 服務策略。 如需有關 WCF LOB 配接器 SDK 的詳細資訊，請參閱 < [WCF LOB 配接器 SDK 文件](../../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md)。
  
  若要執行 SQL Server 資料庫上的作業，必須可以存取相關的資料表、 程序、 檢視、 純量函數，配接器用戶端，並將其資料表值函式中。 資料庫資料表會儲存在 SQL Server 資料庫中的基本單位。 外部應用程式，都可以選取、 插入、 刪除及更新資料表的資料使用 SQL 陳述式。 應用程式也可以使用程序、 檢視、 純量函數和資料表值函式中存取資料表中的資料。 使用[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]，配接器用戶端可以瀏覽成品，例如資料表、 程序、 檢視和 SQL Server 資料庫中的其他這類項目。 配接器用戶端可以選取解決方案，它們需要的成品，並擷取這些構件的中繼資料。 這可讓使用者存取和 SQL Server 資料庫中執行的構件上的作業。  
  
  本節列出的功能[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [BizTalk Adapter for SQL Server 概觀](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)  
  
-   [BizTalk Adapter for SQL Server 中的主要功能](../../adapters-and-accelerators/adapter-sql/key-features-in-biztalk-adapter-for-sql-server.md) 
  
-   [BizTalk Adapter for SQL Server 的限制](../../adapters-and-accelerators/adapter-sql/limitations-of-biztalk-adapter-for-sql-server.md)  
  
## <a name="see-also"></a>另請參閱  
[開始使用 BizTalk adapter for SQL](../../adapters-and-accelerators/adapter-sql/get-started-with-the-biztalk-adapter-for-sql.md)