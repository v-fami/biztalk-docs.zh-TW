---
title: "保護您的 Oracle 資料庫應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapter, security
- authorization
- data protection
- adapter, data protection
- authentication
- security
ms.assetid: c5f18b0a-1c8e-44c6-ba7e-470fa186f636
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8601463c02e32221c369023f05ed2fd3731bb4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="secure-your-oracle-database-applications"></a>保護您的 Oracle 資料庫應用程式
## <a name="data-protection-and-security-overview"></a>資料保護與安全性概觀
資料庫通常會包含敏感性商務資訊，例如客戶帳戶詳細資料。 使用應用程式[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]來存取和修改這項資訊是在本機或分散式網路上可能會不小心公開以存取由未經授權的動作項目，除非工作所建立的保護，並保護期間的資料傳輸。 資料保護和安全性是通常視為以下列形式：  
  
-   *授權*控制存取資源，根據要求者的身分識別。  
  
-   *驗證*提供機制來驗證要求者的身分識別。  
  
-   *資料機密性*提供機制來保護透過加密資料的隱私權。  
  
-   *資料完整性*提供機制來數位簽署資料，讓接收者可以確認資料尚未改變傳輸中。  
  
 另一個值得注意的重要部分是使用者名稱密碼認證提供給[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 配接器會使用這些認證，以開啟 連線到 Oracle 資料庫。 這些認證可以提供在 連線 URI，不過，因為使用者名稱和密碼的純文字、[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]提供替代的方法可讓您以更安全的方式提供這些認證。  
  
 此章節的主題提供指導方針來協助您更安全的解決方案，開發[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [Oracle 資料庫與配接器之間的安全性](../../adapters-and-accelerators/adapter-oracle-database/security-between-the-oracle-database-and-the-adapter.md)
  
-   [使用 Oracle 資料庫配接器和 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md)  
  
-   [安全使用 Oracle 資料庫配接器進行程式設計](../../adapters-and-accelerators/adapter-oracle-database/secure-programming-with-the-oracle-database-adapter.md) 
  
-   [最佳作法](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)