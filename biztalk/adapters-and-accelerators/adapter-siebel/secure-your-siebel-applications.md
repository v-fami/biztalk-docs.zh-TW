---
title: 保護您的 Siebel 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security and protection
- data protection
ms.assetid: 8977cbd3-0025-48d4-8203-8e9e72ea7d26
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ad63e44e4d2dde5ffee743e0758a37e48a3d4d4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012055"
---
# <a name="secure-your-siebel-applications"></a>保護您的 Siebel 應用程式
Siebel 系統通常會包含敏感性商務資訊，例如客戶帳戶詳細資料。 使用應用程式[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]來存取和修改這項資訊是在本機或分散式網路上可能會不小心公開它存取未經授權的動作項目，除非工作不會對保護，並保護期間的資料傳輸。 資料保護和安全性是通常視為以下列形式：  
  
- *授權*控制根據要求者的身分識別資源的存取權。  
  
- *驗證*提供機制來驗證要求者的身分識別。  
  
- *資料機密性*提供機制來保護透過加密的資料的隱私權。  
  
- *資料完整性*提供機制來數位簽署資料，讓接收者可以確保資料尚未改變傳輸中。  
  
  值得注意的另一個重要部分是使用者名稱密碼認證提供給[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 配接器會使用這些認證，開啟與 Siebel 系統的連線。 在 連線 URI，可提供這些認證不過，因為使用者名稱和密碼是純文字、[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]提供替代的方法，可供您以更安全的方式提供這些認證。  
  
  在本節中的主題提供指導方針，以協助您保護您在開發與解決方案[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [Siebel 系統與配接器之間的安全性](../../adapters-and-accelerators/adapter-siebel/security-between-the-siebel-system-and-the-adapter.md)
  
-   [Siebel 配接器與 BizTalk Server 的安全性](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md)
  
-   [安全使用 Siebel 配接器進行程式設計](../../adapters-and-accelerators/adapter-siebel/secure-programming-with-the-siebel-adapter.md)
  
-   [若要保護 Siebel 配接器的最佳作法](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md)