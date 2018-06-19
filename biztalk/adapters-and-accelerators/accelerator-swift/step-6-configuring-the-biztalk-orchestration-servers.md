---
title: 步驟 6： 設定 BizTalk 協調流程伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestration server, configuring
- configuring, orchestration servers
ms.assetid: 1eb38fac-264d-4730-b16b-572dbb6fabd9
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e495be91cc80e072f58a1e8149feb64773f1e51
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005911"
---
# <a name="step-6-configuring-the-biztalk-orchestration-servers"></a>步驟 6： 設定 BizTalk 協調流程伺服器
本節提供設定的 BizTalk 協調流程伺服器上的指導方針。  
  
### <a name="to-configure-the-biztalk-orchestration-servers"></a>若要設定 BizTalk 協調流程伺服器  
  
1.  啟用從 [新增/移除選取的網路分散式交易協調器 (DTC) 存取[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]應用程式伺服器] 類別底下的元件。 已啟用網路 DTC 用戶端存取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]在先前步驟中的電腦。 請參閱下列知識庫文件[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]DTC 問題進行疑難排解的相關資訊的說明及支援 」 網站：  
  
    -   若要疑難排解 MS DTC 防火牆問題、 位於如何[http://go.microsoft.com/fwlink/?linkid=48870](http://go.microsoft.com/fwlink/?linkid=48870)。  
  
    -   如何使用 DTCTester 工具，位於[http://go.microsoft.com/fwlink/?linkid=48871](http://go.microsoft.com/fwlink/?linkid=48871)。  
  
    -   如果 DTC 位於防火牆後方，請參閱設定[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]Distributed Transaction Coordinator (DTC) 來工作透過防火牆，位於[http://go.microsoft.com/fwlink/?linkid=48872](http://go.microsoft.com/fwlink/?linkid=48872)。  
  
2.  安裝 BizTalk Server 的其他軟體必要元件，安裝並設定 BizTalk Server 中所述[安裝和設定 BizTalk Server 協調流程伺服器上](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-orchestration-servers.md)。  
  
3.  安裝和設定[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]安裝中所述，[安裝和設定 BizTalk Accelerator for SWIFT 傳訊的伺服器上](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md)。  
  
 此部分包含：  
  
-   [在協調流程伺服器上安裝和設定 BizTalk Server](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-orchestration-servers.md)  
  
-   [在協調流程伺服器上安裝和設定 BizTalk Accelerator for SWIFT](../../adapters-and-accelerators/accelerator-swift/install-and-configure-biztalk-accelerator-for-swift-on-orchestration-servers.md)