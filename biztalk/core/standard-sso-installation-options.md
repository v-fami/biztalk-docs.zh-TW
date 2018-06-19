---
title: 標準 SSO 安裝選項 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing, SSO
- SSO, installing
ms.assetid: 59aeb503-f369-4145-8a3c-ab60e9ed31a8
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26441ca5d63ebdb4cba807173f7e7068ff846bdf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279150"
---
# <a name="standard-sso-installation-options"></a>標準 SSO 安裝選項
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會利用「企業單一登入」(SSO) 功能安全地儲存認證，來啟用單一登入實例。  
  
 BizTalk Server 也使用 SSO，安全地儲存配接器的自訂組態資料。 若要執行，BizTalk Server 執行階段和管理功能會將 SSO 安裝為相依的功能。 BizTalk Server 的預設安裝會安裝「企業單一登入」。  
  
> [!NOTE]
>  在安裝「企業單一登入」(伺服器元件) 時，必須執行組態。 設定 SSO 系統的第一個步驟是設定主要密碼伺服器。 建議您設定獨立的主要密碼伺服器。 僅需從 BizTalk Server 安裝的自訂功能樹狀結構中選取「企業單一登入」即可達成。  
>   
>  同時，也建議在任何執行「企業單一登入」的電腦上執行時間同步服務。 如此可讓電腦時間與系統的其他部分同步，這是讓 SSO 票證服務正常運作的必要動作。  
  
 **安裝選項的清單**： 執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝程式。 選取**自訂安裝**，然後從下列清單中選取適當的選項：  
  
-   **企業單一登入管理 ―** 對應與連接到企業單一登入服務的系統管理和用戶端工具。  
  
-   **企業單一登入主要密碼伺服器 ―** 做為主要密碼伺服器，SSO 系統中。 這是 SSO 系統中必須部署的第一台伺服器，可讓您建立 SSO 資料庫。  
  
 您也可以等到安裝完成後，再使用 [新增或移除程式] 工具新增下列項目：  
  
-   **伺服器執行階段 ―** 核心服務，以啟用單一登入並安全地儲存/存取組態資料。  
  
-   **企業單一登入管理 ―** 對應與連接到企業單一登入服務的系統管理和用戶端工具。  
  
-   **企業單一登入服務的密碼同步化 ―** 服務以啟用 Enterprise SSO 系統中的密碼同步處理功能。 這些服務也和「Microsoft 密碼變更通知服務」整合。 安裝「企業單一登入」服務之後，您可以從 BizTalk Server 封裝啟動 \Platform\SSO\Setup.exe，然後選取「密碼同步」功能，來安裝「企業單一登入」的「密碼同步」功能。  
  
-   **軟體開發套件**程式設計及參考資訊。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何安裝 SSO 管理元件](../core/how-to-install-the-sso-administration-component.md)  
  
-   [如何安裝 SSO 用戶端公用程式](../core/how-to-install-the-sso-client-utility.md)