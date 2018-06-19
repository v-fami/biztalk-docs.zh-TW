---
title: 單一登入支援 SOAP 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSO, SOAP adapters
- SOAP adapters, SharePoint Portal Server
- SOAP adapters, SSO
- SharePoint Portal server
ms.assetid: c7bf755c-c37d-4b19-9817-a7f42e1e9656
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b6e604eaf7e1b0a9b6144dc20f8bdd59d03932f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277550"
---
# <a name="single-sign-on-support-for-the-soap-adapter"></a>SOAP 配接器的單一登入支援
您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來設定「企業單一登入」(SSO) 搭配使用 SOAP 接收位置或傳送埠。 此主題描述 SSO 如何使用 SOAP 配接器。  
  
 **單一登入 」 支援 soap 接收位置**  
  
 SOAP 接收位置支援兩個 SSO 版本—[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Enterprise SSO 和 Microsoft SharePoint Portal Server SSO。 執行「BizTalk Web 服務發佈精靈」可啟用對 SharePoint Portal Server SSO 的支援。 如需有關如何啟用 SharePoint Portal Server SSO 的詳細資訊，請參閱[發佈 Web 服務](../core/publishing-web-services.md)。 使用 SOAP 接收位置的屬性頁面可啟用 BizTalk 企業單一登入。 如需有關為 SOAP 接收位置啟用 Enterprise SSO 的詳細資訊，請參閱[如何設定 SOAP 接收位置](../core/how-to-configure-a-soap-receive-location.md)。  
  
 **企業 SSO 支援 soap 接收位置**  
  
 Internet Information Services (IIS) 從 Web 用戶端接收 SOAP 要求，接著 IIS 會驗證使用者，並將安全性識別碼傳遞到 SOAP 配接器。 若 IIS 驗證方法是 [摘要] 驗證、[基本] 驗證或 [整合的 Windows 驗證]，SOAP 配接器會呼叫 SSO 認證存放區，根據已驗證使用者取得加密票證。 此票證會儲存為**SSOTicket**訊息內容屬性中的屬性。  
  
 在通過實例中，「BizTalk 傳訊引擎」會將訊息導向至 MessageBox 資料庫。 當傳送配接器從 MessageBox 資料庫接收訊息時，它會呼叫具有加密票證及應用程式名稱的 RedeemTicket 方法，從 SSO 存放區擷取應用程式的安全性認證。 接著傳送配接器使用外部認證連接至應用程式並處理要求。 如需分支機構應用程式的詳細資訊，請參閱[SSO 分支機構應用程式](../core/sso-affiliate-applications.md)。  
  
 在協調流程叫用傳送配接器的實例中，BizTalk 傳訊引擎會將訊息傳送到 MessageBox 資料庫。 協調流程應確保同時**SSOTicket**內容屬性和**Microsoft.BizTalk.XLANGs.BTXEngine.OriginatorSID**包含票證的訊息內容屬性維護。 當配接器從 MessageBox 資料庫接收此訊息時，配接器會呼叫具有加密票證的 RedeemTicket 方法，從 SSO 存放區擷取後端認證。 設計協調流程的使用者應該特別將這個屬性複製到訊息。  
  
 **SharePoint Portal Server SSO 支援 soap 接收位置**  
  
 與 SharePoint Portal Server 整合時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 只透過 SOAP 配接器支援使用 Microsoft SharePoint Portal Server SSO。 SharePoint Portal Server 會建立 SSO 票證，並傳送到 SOAP 要求之 SOAP 標頭中的 BizTalk Server。 當 SOAP 配接器接收包含 SSO 票證的要求時，票證會儲存為**SSOTicket**訊息內容屬性中的屬性。 這個相同的屬性會包含 Enterprise SSO 票證。 只有一個 SSO 票證可以與 BizTalk 訊息關聯。  
  
 在通過和協調流程實例中，處理從 SharePoint Portal Server 接收的 SSO 票證，與由使用 Enterprise SSO 之 SOAP 配接器建立的票證相同。 當傳送配接器接收訊息時，它會呼叫**RedeemTicket**方法具有加密票證的 SharePoint Portal Server 產生。 傳送埠不需要知道存在不同的 SSO 票證。 **RedeemTicket**方法會判斷哪個 SSO 系統產生票證，並將其兌換從適當的位置。  
  
 **同時使用 Enterprise SSO 與 SharePoint Portal Server SSO**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援同時使用這兩個 SSO 系統。 API 可以區分每個 SSO 產生的票證，並將它們從適當的 SSO 資料庫贖回。 如果您同時使用這兩個 SSO 系統，下列規則決定的 SSO 票證，SOAP 接收位置會提升至**SSOTicket**內容屬性：  
  
-   若沒有啟用任何一個 SSO，請勿升級票證。  
  
-   若啟用 Enterprise SSO，但是沒有啟用 SharePoint Portal Server SSO，請擷取並升級 Enterprise SSO 票證。  
  
-   若啟用 SharePoint Portal Server SSO，但是沒有啟用 Enterprise SSO，請升級現有的 SharePoint Portal Server SSO 票證。  
  
-   若啟用 Enterprise 和 SharePoint Portal Server SSO 兩者：  
  
    -   若已接收 SharePoint Portal Server SSO 票證，請升級該票證。  
  
    -   若沒有接收 SharePoint Portal Server SSO 票證，請擷取並升級 Enterprise SSO 票證。  
  
 **SOAP 傳送配接器的單一登入支援**  
  
 如果已啟用 SSO，當 SOAP 傳送埠收到的訊息**Secure**屬性 (**SSOTicket**)，它會呼叫 SSO 伺服器以驗證並贖回分支機構應用程式的票證。 分支機構應用程式的管理應用程式、分支機構系統管理員或 SSO 系統管理員可以呼叫 SSO 贖回票證。 接著 SSO 會解密票證並取得後端認證。 通過和協調流程案例是相同的 SOAP 傳送埠，主題的 「 企業 SSO 支援 SOAP 接收位置 」 一節中所述[SOAP 配接器的單一登入支援](../core/single-sign-on-support-for-the-soap-adapter.md)。  
  
 依照預設，SOAP 傳送埠不會啟用 SSO。 如需有關為 SOAP 傳送埠啟用 SSO 的詳細資訊，請參閱[如何設定 SOAP 傳送埠](../core/how-to-configure-a-soap-send-port.md)。