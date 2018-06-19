---
title: 在 BizTalk Server 中的安全性功能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Server, security
- Master Secret server, security
- security, Master Secret server
- security, runtime
- security, data
- deploying, security
- security, configuring
- runtime, security
- security, security features
- security, messages
- security, access control
- security, about security
- access control
- security, deploying
- data, security
- messages, security
ms.assetid: 5ab15023-fa71-439e-b3aa-420fe28806fa
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50371f0b0c5d5a56fc9f7c392e4ee8d69e637b47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269902"
---
# <a name="security-features-in-biztalk-server"></a>BizTalk Server 中的安全性功能
Microsoft® BizTalk® Server 提供標準閘道，可以同時在內部網路中以及透過網際網路來傳送和接收文件。 由於往返 BizTalk Server 所傳送的訊息可能在商務上具有重大性質，請務必考量因應措施，在這些訊息的傳輸過程中，以及在 BizTalk Server 加以處理和儲存時，協助保護訊息及其所含資訊的安全性。 本節將提供有關 BizTalk Server 安全性功能的詳細資訊，以及如何使用這些功能協助保護資料和環境的安全。  
  
 BizTalk Server 使用下列措施協助您保護輸入和輸出訊息的安全、保護執行階段和組態資訊的安全，以及與其他應用程式和系統安全地整合在一起：  
  
 **訊息安全性**  
  
-   驗證訊息傳送者。 BizTalk Server 可以驗證訊息的傳送者 (使用憑證資訊或 Windows 整合安全性)，以驗證訊息傳送者的識別。 如需詳細資訊，請參閱[輸入訊息驗證](../core/inbound-message-authentication.md)。  
  
-   訊息接收器的授權。 在 BizTalk Server 收到訊息之後，BizTalk Server 就可以判斷哪些程序和使用者具有接收訊息的權限。 如需詳細資訊，請參閱[授權訊息接收器](../core/authorizing-the-receiver-of-a-message.md)。  
  
 **執行階段和組態安全性**  
  
-   **存取控制和保護資料。** BizTalk Server 使用存取控制來確保 BizTalk Server 程序有其適當限制，以及管控重大商務資訊的存取活動。 也就是說，BizTalk Server 可以確保使用者和帳戶僅具有足以執行其工作的最低使用者權限。 如需詳細資訊，請參閱[存取控制與資料安全性](../core/access-control-and-data-security.md)。  
  
 **整合式的安全性**  
  
-   企業單一登入。 BizTalk Server 使用「企業單一登入」(SSO) 來確保完善加密配接器、傳送位置和接收位置所需的機密組態資訊，從而協助確保 BizTalk Server 能夠以安全的方式來儲存及傳輸這些資訊。 如需詳細資訊，請參閱[使用 SSO](../core/using-sso.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設計 BizTalk Server 的系統架構](../core/designing-the-system-architectures-for-biztalk-server.md)   
 [實作企業單一登入](../core/implementing-enterprise-single-sign-on.md)   
 [規劃訊息安全性](../core/planning-message-security.md)   
 [存取控制與資料安全性](../core/access-control-and-data-security.md)   
