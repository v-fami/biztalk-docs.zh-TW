---
title: 步驟 5： 設定 BizTalk 傳訊伺服器 |Microsoft Docs
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
ms.openlocfilehash: 9baea2c567148ead98abf6b3aca3f5cad8258e60
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979999"
---
# <a name="step-5-configuring-the-biztalk-messaging-servers"></a>步驟 5： 設定 BizTalk 傳訊伺服器
此章節提供指導方針設定 BizTalk 傳訊伺服器。  
  
### <a name="to-configure-the-biztalk-messaging-servers"></a>若要設定的 BizTalk 傳訊伺服器  
  
1. 選取 [新增/移除從啟用網路 Distributed Transaction Coordinator (DTC) 存取[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]應用程式伺服器] 類別底下的元件。 上已啟用網路 DTC 用戶端存取[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]先前步驟中的電腦。 疑難排解 DTC 問題的相關資訊的 Microsoft 說明及支援 」 網站上，請參閱下列知識庫文件：  
  
   - 若要疑難排解 MS DTC 防火牆問題，位於如何[ http://go.microsoft.com/fwlink/?linkid=48870 ](http://go.microsoft.com/fwlink/?linkid=48870)。  
  
   - 如何使用 DTCTester 工具，位於[ http://go.microsoft.com/fwlink/?linkid=48871 ](http://go.microsoft.com/fwlink/?linkid=48871)。  
  
   - 如果 DTC 位於防火牆後方，請參閱 「 設定 Microsoft 分散式交易協調器 (DTC) 來工作透過防火牆 」，位於[ http://go.microsoft.com/fwlink/?linkid=48872 ](http://go.microsoft.com/fwlink/?linkid=48872)。  
  
2. 設定並確認 網路負載平衡的 biztalk 接收伺服器中所述[步驟 2： 設定伺服器上的 NLB](../../adapters-and-accelerators/accelerator-swift/step-2-configuring-nlb-on-the-servers.md)。  
  
3. 安裝和設定[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]中所述[安裝和設定 BizTalk Accelerator for SWIFT 傳訊伺服器上](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md)。  
  
   此部分包含：  
  
-   [在傳訊伺服器上安裝和設定 BizTalk Server](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-messaging-server.md)  
  
-   [在傳訊伺服器上安裝和設定 BizTalk Accelerator for SWIFT](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md)