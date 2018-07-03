---
title: 保護您的 Oracle 資料庫應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapter, security
- authorization
- data protection
- adapter, data protection
- authentication
- security
ms.assetid: c5f18b0a-1c8e-44c6-ba7e-470fa186f636
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7f61e15b94d741e6bfc2a9f951655ff4358a001
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982911"
---
# <a name="secure-your-oracle-database-applications"></a>保護您的 Oracle 資料庫應用程式
## <a name="data-protection-and-security-overview"></a>資料保護與安全性概觀
資料庫通常會包含敏感性商務資訊，例如客戶帳戶詳細資料。 使用應用程式[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]來存取和修改這項資訊是在本機或分散式網路上可能會不小心公開它存取未經授權的動作項目，除非工作不會對保護，並保護期間的資料傳輸。 資料保護和安全性是通常視為以下列形式：  
  
- *授權*控制根據要求者的身分識別資源的存取權。  
  
- *驗證*提供機制來驗證要求者的身分識別。  
  
- *資料機密性*提供機制來保護透過加密的資料的隱私權。  
  
- *資料完整性*提供機制來數位簽署資料，讓接收者可以確保資料尚未改變傳輸中。  
  
  值得注意的另一個重要部分是使用者名稱密碼認證提供給[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 配接器會使用這些認證，以開啟 連線到 Oracle 資料庫。 在 連線 URI，可提供這些認證不過，因為使用者名稱和密碼是純文字、[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]提供替代的方法，可供您以更安全的方式提供這些認證。  
  
  在本節中的主題提供指導方針，以協助您保護您在開發與解決方案[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [Oracle 資料庫與配接器之間的安全性](../../adapters-and-accelerators/adapter-oracle-database/security-between-the-oracle-database-and-the-adapter.md)
  
-   [Oracle 資料庫配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md)  
  
-   [安全使用 Oracle 資料庫配接器進行程式設計](../../adapters-and-accelerators/adapter-oracle-database/secure-programming-with-the-oracle-database-adapter.md) 
  
-   [最佳做法](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)