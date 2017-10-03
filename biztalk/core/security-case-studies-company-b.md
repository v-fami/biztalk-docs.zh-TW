---
title: "安全性個案研究： 公司 B |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, examples
- security, architecture
- architecture, security
- security, case studies
ms.assetid: 48bbb347-919a-435e-b7b1-34a4c0e65e59
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef0e37d4acda263822a2cf06095f2c8fd9989afe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="security-case-studies-company-b"></a>安全性個案研究： 公司 B
公司 B 是一家軟體公司。 其商務模型需仰賴與重要客戶與供應商的電子交易。 公司 B 使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 實作來進行交易。  
  
 公司 B 使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來管理內部與外部應用程式之間的交易和通訊。 公司 B 會和大約 85 個內部應用程式及 2300 個交易夥伴通訊。 它目前每個月處理約二百五十萬份文件，估計在 2007 年終每月將處理六百萬份文件。  
  
## <a name="potential-threats-and-security-concerns"></a>潛在威脅與安全性考量  
 公司 B 想要確定它只會接收和處理來自已驗證來源的訊息。 公司 B 也要確定它可以儘可能安全地接收和擷取企業網路外部的文件。 隔開公司 B 企業網路與網際網路的防火牆只可讓從連接埠 80 和 443 的流量通過。 防火牆會拒絕所有其他流量。  
  
## <a name="security-architecture"></a>安全性架構  
 下圖顯示公司 B 使用的架構。 公司 B 使用 BizTalk Server 當做訊息仲介來溝通內部應用程式，以及用來處理、傳送和接收來自供應商與客戶的格式正確的訊息。 公司 B 必須以不同格式處理內部和外部文件。 這包括一般檔案與 XML 文件。  
  
 **圖 1 公司 B 安全性架構**  
  
 ![公司 B 的架構](../core/media/bpi-cp-pc-company-b.gif "BPI_CP_PC_COMPANY_B")  
  
 公司 B 使用單一防火牆來隔開企業電腦與網際網路。 公司 B 在企業網路中的所有公司伺服器和工作站之間還加入了網際網路通訊協定安全性 (IPsec) 通訊，做為額外的安全性階層。 公司 B 使用 IPsec 來加密內部網域中的所有通訊。  
  
 公司 B 使用檔案共用伺服器來接收一般檔案。 此檔案共用伺服器位於企業網路與網域的外部。 防火牆隔開檔案共用伺服器與企業網路。 公司 B 的外部夥伴將其一般檔案文件張貼在這個檔案共用伺服器，而且他們會透過加密的點對點通道通訊協定 (PPTP) 管線，與檔案共用伺服器通訊。 公司 B 透過每 30 天就會過期的夥伴密碼，來保護檔案共用伺服器的存取。  
  
 公司 B 已經建立自訂的檔案移動應用程式，可從檔案共用伺服器擷取一般檔案文件，並將它們傳送到 BizTalk Server 進行其他處理。 公司 B 的內部應用程式也使用自訂檔案移動應用程式，將一般檔案傳送到 BizTalk Server。 BizTalk Server 會轉換這些文件，再將它們傳送給公司 B 的交易夥伴。  
  
 在 BizTalk Server 將夥伴資料轉換成內部應用程式格式之前，它會驗證其中有傳送者、收件者，以及文件類型。 若 BizTalk Server 收到的訊息沒有傳送者、收件者或文件類型，BizTalk Server 就會拒絕該訊息，而公司 B 的作業團隊會檢視該訊息。 內部應用程式以許多格式來傳送訊息，包括 EDIFACT、一般檔案、XML 及 ANSI X12。  
  
 公司 B 也透過 HTTPS 從內部與外部來源接收文件。 外部夥伴將他們的文件張貼到企業網路外部的 Web 伺服器。 防火牆會隔開 Web 伺服器與企業網路。 自訂的檔案移動應用程式也會擷取透過 HTTPS 張貼的文件。 公司 B 使用協力廠商產品，來加密和簽署傳送給交易夥伴的訊息。 公司 B 還會對所有伺服器執行夜間稽核，來確定它們都有正確的安全性設定，以做為額外的安全性保障措施。 公司 B 會記錄所有例外狀況，以供檢視。  
  
## <a name="see-also"></a>另請參閱  
 
 [小型與中型公司的安全性案例研究](../core/security-case-studies-for-small-to-medium-sized-companies.md)   
 
 [小型與中型公司的範例架構](../core/sample-architectures-for-small-medium-sized-companies.md)