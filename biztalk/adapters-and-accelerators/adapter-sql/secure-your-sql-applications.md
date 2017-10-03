---
title: "保護 SQL 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b182593-fcca-4ebc-a2fd-7684b84cfb15
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d631bc3ad87e9a8ec8ac51850b7dbe1eb244c140
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="secure-your-sql-applications"></a>保護 SQL 應用程式
## <a name="overview"></a>概觀
SQL Server 資料庫通常會包含敏感性商務資訊，例如客戶帳戶詳細資料。 使用應用程式[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]來存取和修改這項資訊是在本機或分散式網路上可能會不小心公開以存取由未經授權的動作項目，除非工作所建立的保護，並保護期間的資料傳輸。 資料保護和安全性是通常視為以下列形式：  
  
-   *授權*控制存取資源，根據要求者的身分識別。  
  
-   *驗證*提供機制來驗證要求者的身分識別。  
  
-   *資料機密性*提供機制來保護透過加密資料的隱私權。  
  
-   *資料完整性*提供機制來數位簽署資料，讓接收者可以確認資料尚未改變傳輸中。  
  
 另一個值得注意的重要部分是使用者名稱密碼認證提供給[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 配接器會使用這些認證，開啟與 SQL 系統的連線。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不允許連線 URI 中所提供的認證。 這可防止不小心取得公開憑證。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]提供兩種替代方法，以更安全的方式提供這些認證：  
  
 整合式的安全性。 在此情況下，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]認證。 您必須設定 SQL server 來接受這些認證，此方法才能運作。  
  
 企業單一登入 (SSO)。 如需有關使用 SSO 的詳細資訊，請參閱[使用 SQL 配接器和 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md)。  
  
 此章節的主題提供指導方針來協助您更安全的解決方案，開發[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SQL Server 與配接器之間的安全性](../../adapters-and-accelerators/adapter-sql/security-between-the-sql-server-and-the-adapter.md)
  
-   [使用 SQL 配接器和 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md) 
  
-   [保護使用 SQL 配接器進行程式設計](../../adapters-and-accelerators/adapter-sql/secure-programming-with-the-sql-adapter.md)
  
-   [最佳作法](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)