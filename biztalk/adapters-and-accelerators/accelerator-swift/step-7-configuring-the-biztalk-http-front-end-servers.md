---
title: 步驟 7： 設定 BizTalk HTTP 前端伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, HTTP servers
- HTTP server, configuring
ms.assetid: 6b7e0b48-bb20-42f4-84a5-092ff3a02741
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b6429ba6c753bac16874fd6fa81e13e91927b58
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989183"
---
# <a name="step-7-configuring-the-biztalk-http-front-end-servers"></a>步驟 7： 設定 BizTalk HTTP 前端伺服器
本節提供有關設定中的 Web 伺服器的指導方針您[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]部署。  
  
> [!NOTE]
>  在單一電腦部署中，此電腦是一個可進行傳訊和處理的同一部電腦。  
  
### <a name="to-configure-the-biztalk-http-front-end-servers"></a>若要設定 BizTalk HTTP 前端伺服器  
  
1. 安裝 Internet Information Services (IIS) 和 ASP.NET。  
  
2. 開啟 IIS 管理員並選取**網頁服務延伸**。 請確定 ASP.NET v1.1 和 ASP.NET v2.0 設定為**允許**。  
  
3. 請確認**Message Queuing**服務 (MSMQ) 與**路由支援**從 新增/移除安裝[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]下應用程式伺服器/訊息佇列的元件。  
  
4. 確定已啟用網路 DTC 存取在 [新增/移除[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]應用程式伺服器] 類別底下的元件。 上已啟用網路 DTC 用戶端存取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]先前步驟中的電腦。  
  
5. 在您部署中，實作安全通訊端層 (SSL) 通訊協定，如中所述[支援 Secure Sockets Layer (SSL)](../../adapters-and-accelerators/accelerator-swift/supporting-secure-sockets-layer-ssl.md)。  
  
6. 安裝和設定 Windows SharePoint Services 3.0 SP1。  
  
7. 安裝和設定[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]中所述[安裝和設定 BizTalk Accelerator for SWIFT HTTP 前端伺服器上](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-http-front-end-servers.md)。  
  
   此部分包含：  
  
-   [支援安全通訊端層 (SSL)](../../adapters-and-accelerators/accelerator-swift/supporting-secure-sockets-layer-ssl.md)  
  
-   [安裝和設定 BizTalk HTTP 前端伺服器](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-http-front-end-servers.md)  
  
-   [在 HTTP 前端伺服器上安裝和設定 BizTalk Accelerator for SWIFT](../../adapters-and-accelerators/accelerator-swift/install-and-configure-biztalk-accelerator-for-swift-on-http-front-end-servers.md)