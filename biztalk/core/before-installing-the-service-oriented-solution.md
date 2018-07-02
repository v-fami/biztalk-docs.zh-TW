---
title: 安裝服務導向解決方案之前 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service solution tutorial, deployment prerequisites
ms.assetid: 865bd21c-e49a-4647-af91-fefee07ee806
caps.latest.revision: 36
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3a735ed832051c24e5ccd253df61c42c07ed6e6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982383"
---
# <a name="before-installing-the-service-oriented-solution"></a>安裝服務導向解決方案之前
必須具備下列必要條件才能在單一電腦上安裝服務導向解決方案的虛設常式版本：  
  
- [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)]。  
  
- [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)] 支援的軟體。  
  
- 最新版本的 IBM WebSphere MQ Client for Windows  
  
  > [!NOTE]
  >  MQSeries Server 不是解決方案的虛設常式版本之必要項目。  
  
  > [!NOTE]
  >  您可以從 IBM 網站下載 IBM WebSphere MQ Client for Windows。  
  
  在單一電腦上安裝服務導向解決方案的內嵌與配接器版本：  
  
- [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)]。  
  
  > [!NOTE]
  >  必須要有網域帳戶以對應「企業單一登入」(SSO) 認證。 建議在 BizTalk 服務和 ENTSSO 服務帳戶使用網域帳戶。  
  
- [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)] 支援的軟體。  
  
- 本機電腦上的 MQSeries Server，或存取執行 MQSeries Server 的電腦。 在內嵌版本中，MQSeries 用戶端 API 必須可以在執行解決方案之協調流程的 BizTalk Server 上使用。  
  
  > [!NOTE]
  >  MQSeries Server 的版本必須符合 BizTalk Server MQSeries 配接器所需的版本。 這可以包括 IBM WebSphere MQ for Windows Version 5.3 搭配 Fix Pack 10 (CSD10) 或更新的版本。  
  
  > [!NOTE]
  >  當使用 MQSeries 這類會對伺服器進行「分散式元件物件模型」(Distributed Component Object Model，DCOM) 呼叫的功能時，請確定您並未啟用「網路位址轉譯」(Network Address Translation，NAT) 架構的防火牆。 用戶端必須能以伺服器的實際 IP 位址來存取伺服器，而 NAT 架構的防火牆會將此位址轉譯為用戶端無法辨識的位址。  
  
- 若您使用需要大型主機的其他解決方案，則需要 IBM Mainframe 搭配 CICS 與 Transaction X。 在這種情況下，必須在大型主機和 Microsoft Host Integration Server (HIS) 上安裝 CICS 應用程式 (COBOL 程式碼) 才能存取大型主機。  
  
   若您的解決方案沒有大型主機，可以修改連接埠繫結以使用虛設常式 Web 服務來進行擱置交易。 Web 服務會在本機產生交易，以模擬大型主機交易。 如需如何修改虛設常式擱置交易 Web 服務的連接埠繫結的詳細資訊，請參閱[如何安裝內嵌和配接器版本的服務導向解決方案](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md)。  
  
- 連接大型主機必須要有 Host Integration Server。  
  
  > [!NOTE]
  >  Host Integration Server 是 BizTalk Server 的一部分。  
  
- 以 HTTPS 連線憑證設定的 Web 伺服器。  
  
## <a name="see-also"></a>另請參閱  
 [How to Install 虛設常式版本的服務導向解決方案](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md)   
 [如何安裝內嵌和配接器版本的服務導向解決方案](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md)   
 [如何執行服務導向解決方案](../core/how-to-run-the-service-oriented-solution.md)   
 [服務導向解決方案的開發人員電腦設定](../core/developer-machine-setup-for-the-service-oriented-solution.md)