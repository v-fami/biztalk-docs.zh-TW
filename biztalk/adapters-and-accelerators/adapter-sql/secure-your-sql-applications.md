---
title: 保護您的 SQL 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b182593-fcca-4ebc-a2fd-7684b84cfb15
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eabb9c260ed835a7c4cac3183000327767bb9cd0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014511"
---
# <a name="secure-your-sql-applications"></a>保護您的 SQL 應用程式
## <a name="overview"></a>概觀
SQL Server 資料庫通常會包含敏感性商務資訊，例如客戶帳戶詳細資料。 使用應用程式[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]來存取和修改這項資訊是在本機或分散式網路上可能會不小心公開它存取未經授權的動作項目，除非工作不會對保護，並保護期間的資料傳輸。 資料保護和安全性是通常視為以下列形式：  
  
- *授權*控制根據要求者的身分識別資源的存取權。  
  
- *驗證*提供機制來驗證要求者的身分識別。  
  
- *資料機密性*提供機制來保護透過加密的資料的隱私權。  
  
- *資料完整性*提供機制來數位簽署資料，讓接收者可以確保資料尚未改變傳輸中。  
  
  值得注意的另一個重要部分是使用者名稱密碼認證提供給[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 配接器會使用這些認證，開啟與 SQL 系統的連線。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不允許的連線 URI 中提供的認證。 這可防止不小心取得公開認證。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]提供兩種替代方法，以更安全的方式提供這些認證：  
  
  整合式的安全性。 在此情況下，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用 Microsoft[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]認證。 您必須設定 SQL server，以接受這些認證，此方法才能運作。  
  
  企業單一登入 (SSO)。 如需使用 SSO 的詳細資訊，請參閱[SQL 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md)。  
  
  在本節中的主題提供指導方針，以協助您保護您在開發與解決方案[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SQL Server 與配接器之間的安全性](../../adapters-and-accelerators/adapter-sql/security-between-the-sql-server-and-the-adapter.md)
  
-   [SQL 配接器與 BizTalk Server 之間的安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md) 
  
-   [安全使用 SQL 配接器進行程式設計](../../adapters-and-accelerators/adapter-sql/secure-programming-with-the-sql-adapter.md)
  
-   [最佳做法](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)