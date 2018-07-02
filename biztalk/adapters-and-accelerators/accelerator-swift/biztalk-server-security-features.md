---
title: BizTalk Server 安全性功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- authentication
- security, authentication
- security, BizTalk Server
- security, security features
- BizTalk Server, security features
ms.assetid: db356439-1898-4c09-86de-458a9bd21b18
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45d541138d566eb6791385cdb23413187d2e68ba
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971127"
---
# <a name="biztalk-server-security-features"></a>BizTalk Server 安全性功能
財務服務應用程式和整合方案所使用的開發[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]都[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式和已受到原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安全性功能。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 應用程式通常會由組成的傳訊功能 (訊息處理、 轉換、 路由) 和工作流程自動化 （商務程序自動化、 商務規則和邏輯評估）。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 提供一般傳訊和工作流程自動化的安全性。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] 提供特定的保護使用者訊息項目、 修復、 核准和提交額外的安全性功能。 如需詳細資訊[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]-特定的安全性，請參閱 < [A4SWIFT Message Repair 和 New Submission 的安全性功能](../../adapters-and-accelerators/accelerator-swift/a4swift-security-features-for-message-repair-and-new-submission.md)。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 專為訊息事件模型 （置於 MessageBox 資料庫和發行者訂閱者設計模式） 的訊息和文件，以及與其互動的處理元件在 XML 與 Web 服務為基礎技術。 為了協助保護資訊、 參與者和程序所組成的任何系統的完整性，下列的主要需求引導安全性機制：  
  
- **保護隱私權的系統項目。** 保護隱私權的通訊中開啟的運算和網路環境是加密的函式。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 支援的加密透過公開金鑰基礎結構 (PKI)、 Secure Multipurpose Internet Mail Extensions (S/MIME) 和 Secure Sockets Layer (SSL) 通訊。 驗證和增強的訊息，隱私權保護[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會大量地使用數位簽章 （索引鍵）。  
  
   PKI 是授權的解決升級安全交換金鑰、 程序和階層的索引鍵和部署針對這些用途的演算法進行驗證方法的網際網路通訊協定的集合。  
  
   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 使用 S/MIME 通訊協定來加密和解密中多個步驟中，多合作對象的處理序與資料加密標準 (DES)、 3DES 和 RC2 加密演算法，可支援傳送和接收的訊息。 Web 用戶端與 Web 伺服器之間的加密的點對點通訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]使用 SSL 通訊協定。  
  
- **驗證資訊、 參與者，以及處理程序。** 驗證資訊、 參與者，以及處理程序[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]簽署憑證時，會依賴[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]驗證和擴充的實作[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]中的驗證[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]稱為 「 企業單一登入 (SSO)。 簽署的憑證是數位簽章 （或金鑰），識別兩個合作對象彼此訊息交換中的。 簽署的憑證也會決定，是否訊息遭人竄改傳輸中的位置。  
  
   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 可以使用預存的公用金鑰來數位簽署的內送訊息，解碼，並可以使用私密金鑰來簽署它所產生的輸出訊息。 SSO 是[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]延伸模組[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]可讓合作對象與訊息的事件會參與多步驟的驗證[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]來驗證本身，在任何處理序中的步驟的程序中的任何資源的程序，而不需要多個登入。  
  
- **授權的資源使用量。** 授權是系統的配置和管理資源的使用權限。 主要[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]授權機制是否[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]角色，[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]驗證和 MessageBox 資料庫。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 之前將它們傳送至協調流程處理序，以及協調流程會將訊息傳送至傳送管線之後，它的 MessageBox 資料庫中儲存所有內送和外寄訊息。 若要存取[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]資料庫和資源指派給系統管理員、 使用者，且主機帳戶使用[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]角色。  
  
  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安全性架構根據一組強大的機制，實作於整個[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]使用各種不同的方法可提高安全性。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]納入的安全性機制的元件會傳送和接收配接器、 管線、 MessageBox 資料庫、 協調流程，以及訊息安全性內容屬性。  
  
  這些元件會使用需要驗證管線，多個邏輯主控件和其 「 信任的驗證 」 的屬性，發行和訂閱/接收授權方法部署的安全性機制。 多重 facet 的安全性架構的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]提供許多選項，即可設計和執行多個可協助保護金融服務傳訊和工作流程自動化應用程式。