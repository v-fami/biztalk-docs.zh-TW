---
title: "步驟 7： 設定 BizTalk HTTP 前端伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, HTTP servers
- HTTP server, configuring
ms.assetid: 6b7e0b48-bb20-42f4-84a5-092ff3a02741
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5840099816149265711744373e08d3a9a9d91cd0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-configuring-the-biztalk-http-front-end-servers"></a>步驟 7： 設定 BizTalk HTTP 前端伺服器
本節提供有關設定中的 Web 伺服器的指導方針您[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]部署。  
  
> [!NOTE]
>  在單一電腦部署中，此電腦是其中的訊息和處理的同一部電腦。  
  
### <a name="to-configure-the-biztalk-http-front-end-servers"></a>若要設定 BizTalk HTTP 前端伺服器  
  
1.  安裝 Internet Information Services (IIS) 和 ASP.NET。  
  
2.  開啟 IIS 管理員並選取**網頁服務延伸**。 請確定 ASP.NET 1.1 版與 ASP.NET 2.0 版設定為**允許**。  
  
3.  請確認**訊息佇列**服務 (MSMQ) 與**路由支援**從新增或移除安裝[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]下應用程式伺服器/訊息佇列的元件。  
  
4.  確定在 [新增/移除已啟用網路 DTC 存取[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]應用程式伺服器] 類別底下的元件。 已啟用網路 DTC 用戶端存取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]在先前步驟中的電腦。  
  
5.  中所述，在您的部署中實作安全通訊端層 (SSL) 通訊協定[支援安全通訊端層 (SSL)](../../adapters-and-accelerators/accelerator-swift/supporting-secure-sockets-layer-ssl.md)。  
  
6.  安裝和設定 Windows SharePoint Services 3.0 SP1。  
  
7.  安裝和設定[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]中所述[安裝和設定 BizTalk Accelerator for SWIFT HTTP 前端伺服器上](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-http-front-end-servers.md)。  
  
 此部分包含：  
  
-   [支援安全通訊端層 (SSL)](../../adapters-and-accelerators/accelerator-swift/supporting-secure-sockets-layer-ssl.md)  
  
-   [安裝和設定 BizTalk HTTP 前端伺服器](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-http-front-end-servers.md)  
  
-   [安裝和設定 BizTalk Accelerator for SWIFT HTTP 前端伺服器上](../../adapters-and-accelerators/accelerator-swift/install-and-configure-biztalk-accelerator-for-swift-on-http-front-end-servers.md)