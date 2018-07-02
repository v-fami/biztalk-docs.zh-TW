---
title: 識別潛在的威脅 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- planning, security
- security, potential threats
- security, planning
ms.assetid: 1d70a0c1-6daf-47bb-af15-a4b35a7bafc2
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbd2feb0b6a09905efb7275b1cc6f0e6ef2b13d7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972567"
---
# <a name="identifying-potential-threats"></a>識別潛在的威脅
您可以使用 STRIDE 模型來識別 BizTalk Server 部署的潛在威脅。 STRIDE 是衍生自下列類別目錄的縮寫： *S*假冒識別*T*的資料，ampering *R*否認，*我*若資訊洩漏*D*拒絕服務，以及提高權限。 本節包含 BizTalk Server 環境潛在威脅的範例，以及如何減輕這些威脅的機制。  
  
 **偽造識別**  
  
- 若您在繫結檔案中儲存密碼，然後儲存這些繫結檔案，則未授權使用者可能可以讀取密碼，並使用它們來連接 BizTalk Server，進而造成損害。 您不應該在繫結檔案中儲存密碼，而應該使用判別存取控制清單 (DACL) 來限制存取可能含有敏感性資料的檔案。  
  
  **竄改資料**  
  
- 惡意使用者可以攔截夥伴送至 BizTalk Server 的訊息，並修改訊息的內容。 您可以使用數位簽章來防止惡意使用者篡改傳送中的訊息。  
  
  **不可否認性**  
  
- 您需要追蹤 BizTalk 傳送和接收的訊息。 您可以使用數位簽章來證明訊息確實是由您和您的夥伴所傳送。  
  
  **資訊洩漏**  
  
- 惡意使用者可以讀取 BizTalk Server 與 Microsoft SQL Server™ 之間的純文字通訊。 您可以使用網際網路通訊協定安全性 (IPSec) 或「安全通訊端層」(SSL) 來協助保護伺服器之間的通訊安全。 您可以使用防火牆來限制每部伺服器的存取。 也可以使用加密協助保障傳送中訊息的私密性。  
  
- 未經授權的使用者可能存取網路共用或目錄中的資訊。 您可以使用強式判別存取控制清單 (DACL) 來限制存取使用資源的帳戶。  
  
- 執行 BizTalk 主控件執行個體的電腦之 Windows 系統管理員有可能發生行為不當的情形，並執行不同層次的攻擊 (例如資訊洩露或拒絕服務)。 不過，在多數狀況下，您可以將這些攻擊限制在電腦遭到攻擊者危害的特定主控件。  
  
  **阻斷服務**  
  
- 惡意使用者可以傳送大量訊息至 BizTalk Server，讓 BizTalk 無法接收有效的訊息。 如需有關此威脅的防護技術的詳細資訊，請參閱[減少阻斷的服務攻擊](../core/mitigating-denial-of-service-attacks.md)。  
  
  **提高權限**  
  
- 提升權限的威脅通常發生於在信任的環境中執行不信任的程式碼時，或惡意使用者利用軟體或組態缺陷時。 您必須確定您信任要在環境中部署的組件與其他元件。 若要將提升權限攻擊的可能性降到最低，應該使用非重疊的最低權限帳戶，而且應該避免使用系統管理帳戶進行執行階段的服務和作業。 您還要將環境中執行的元件、應用程式與服務的數目降到最低。  
  
## <a name="see-also"></a>另請參閱  
 [減少阻斷服務攻擊](../core/mitigating-denial-of-service-attacks.md)   
 [BizTalk Server 部署的安全性建議](../core/security-recommendations-for-a-biztalk-server-deployment.md)   
 [安全性規劃](../core/planning-for-security.md)