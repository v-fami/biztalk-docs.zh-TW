---
title: A4SWIFT Web 服務安全性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IIS security
- Web service [A4SWIFT]
- security, transport-level security
- security, message-level security
- ASP.NET security
- A4SWIFT, Web service
- A4SWIFT, security
- security, IIS
- security, ASP.NET
- security, Web service
- messages, security
ms.assetid: e6c7d275-569f-47f6-81fb-10bcd86ff417
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d484f3a28896528ac2ab9367a8a7a0bbe3604801
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006471"
---
# <a name="a4swift-web-service-security"></a>A4SWIFT Web 服務安全性
[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]Web 服務，依預設會安裝在高度安全的混合式安全性模型。 在 ASP.NET 模型中有 Web 服務之間的信任界限[!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]站台，而[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]資料庫。  
  
## <a name="iis-and-aspnet-security-settings"></a>IIS 和 ASP.NET 的安全性設定  
 進行呼叫以[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]IIS 網頁伺服器第一次驗證使用者使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]驗證。 Web 服務的 web.config 設定預設為使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]驗證不使用模擬，並驗證呼叫者是隸屬[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]Users 群組。 如果呼叫端的成員[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]Users 群組的應用程式集區的處理序識別下執行 Web 服務方法。 如[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]，這是預設應用程式集區[!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]。  
  
 如[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]Web service 來刪除 Web 方法呼叫者的收件匣中的訊息[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]Web 服務必須模擬呼叫端的**刪除**和**GetCheckedOutUser**方法。 這些是原始呼叫端的內容下執行的唯一方法。 因為[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]Web 服務會模擬呼叫者的這些 Web 方法，呼叫端必須擁有明確呼叫端之作用的 SharePoint 文件庫上設定的權限。  
  
## <a name="a4swift-secure-communication-settings"></a>A4SWIFT 安全的通訊設定  
[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]是注重保證的完整性與機密性的 Web 服務訊息從傳送時[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]至[!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]到在網路上的 BizTalk 應用程式。 若要提供最高層級的安全性[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]支援兩種應用程式之間的安全通訊層級： 傳輸層級與訊息層級。  
  
## <a name="transport-level-security"></a>傳輸層級安全性  
[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]支援之間的 SSL 通訊[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]、 [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] Web 服務， [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]，和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]傳輸訊息時，自動調整 MRSR 網站安全性設定。  
  
 網際網路通訊協定安全性 (IPSec) 也可以實作之間的通訊安全[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]。  
  
 如需有關實作之間的安全通訊的 IPSec[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]，請參閱 < 保護您部署的 BizTalk Server 「 BizTalk Server 說明中。  
  
  
## <a name="message-level-security"></a>訊息層級安全性  
[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]訊息層級安全性達成方式是以數位方式簽署訊息，以提供完整性。 登入訊息[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]中詳細說明[InfoPath 安全性](../../adapters-and-accelerators/accelerator-swift/infopath-security.md)。