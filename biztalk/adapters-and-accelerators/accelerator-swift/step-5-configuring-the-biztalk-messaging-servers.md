---
title: 步驟 5： 設定 BizTalk 傳訊的伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, BizTalk Messaging servers
- BizTalk Messaging servers, configuring
ms.assetid: 598d336d-b006-4d02-9249-e9d6d9b6b7b5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e1aea1187417b77071f0821547869a5b84549c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214006"
---
# <a name="step-5-configuring-the-biztalk-messaging-servers"></a>步驟 5： 設定 BizTalk 傳訊的伺服器
此章節提供的指導方針設定 BizTalk 傳訊的伺服器。  
  
### <a name="to-configure-the-biztalk-messaging-servers"></a>若要設定 BizTalk 傳訊的伺服器  
  
1.  啟用從 [新增/移除選取的網路分散式交易協調器 (DTC) 存取[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]應用程式伺服器] 類別底下的元件。 已啟用網路 DTC 用戶端存取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]在先前步驟中的電腦。 請參閱下列知識庫文件[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]DTC 問題進行疑難排解的相關資訊的說明及支援 」 網站：  
  
    -   若要疑難排解 MS DTC 防火牆問題、 位於如何[http://go.microsoft.com/fwlink/?linkid=48870](http://go.microsoft.com/fwlink/?linkid=48870)。  
  
    -   如何使用 DTCTester 工具，位於[http://go.microsoft.com/fwlink/?linkid=48871](http://go.microsoft.com/fwlink/?linkid=48871)。  
  
    -   如果 DTC 位於防火牆後方，請參閱 「 設定[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]Distributed Transaction Coordinator (DTC) 通過防火牆的工作 」，位於[http://go.microsoft.com/fwlink/?linkid=48872](http://go.microsoft.com/fwlink/?linkid=48872)。  
  
2.  設定及驗證網路負載平衡上 BizTalk 接收伺服器中所述[步驟 2： 設定伺服器上的 NLB](../../adapters-and-accelerators/accelerator-swift/step-2-configuring-nlb-on-the-servers.md)。  
  
3.  安裝和設定[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]中所述[安裝和設定 BizTalk Accelerator for SWIFT 傳訊的伺服器上](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md)。  
  
 此部分包含：  
  
-   [安裝和設定 BizTalk Server 傳訊的伺服器上](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-messaging-server.md)  
  
-   [上安裝和設定 BizTalk Accelerator for SWIFT 訊息伺服器](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md)