---
title: "啟用 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, publishing
- hosts, isolated
- Web services, planning
- Web services, enabling
ms.assetid: 2a4681f6-9ded-423d-baa5-5831e6a85c61
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b7cd0b1694422caf04285206f0bd7411ff5de20
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-web-services"></a>啟用 Web 服務
若要發佈 Web 服務，您必須設定 Internet Information Services (IIS)、BizTalk 外掛式主控件，以及 Windows 使用者和群組帳戶。 本節討論如何啟用 IIS 中的 Web 服務。 如需有關啟用 Web 服務的詳細資訊，請參閱 IIS 文件。  
  
 **Internet Information Services**  
  
 您可以發佈 Web 服務，Windows 系統上有 IIS 與 ASP.NET 設定。 每部伺服器的所有 Web 服務都會在 ASP.NET 背景工作處理序內執行。  
  
 根據預設，ASP.NET 背景工作處理序會使用本機 ASPNET 帳戶。 IIS 用來處理 Web 服務要求的應用程式集區。  
  
 **BizTalk 外掛式主控件**  
  
 若要啟用 Web 服務，您必須至少在 BizTalk Server 中建立一個外掛式主控件。 外掛式主控的件代表外部處理序，例如 ISAPI 擴充程式及 BizTalk Server 不會建立或控制 ASP.NET 處理序。 這些類型的外部處理序必須裝載特定配接器，例如 HTTP/S 和 SOAP。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態管理員會建立 BizTalk 用來做為預設外掛式主控件的 BizTalkServerIsolatedHost。 BizTalk 外掛式主控件使用者群組是與這個主控件相關的 Windows 群組預設名稱。 如需主控件和主控件執行個體的詳細資訊，請參閱[管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)。  
  
 外掛式主控件執行個體只能執行一個配接器。 如果您使用單一外掛式主控件設定 HTTP 和 SOAP 配接器的接收處理常式，則必須建立兩個應用程式集區，讓每個配接器使用一個應用程式集區。  
  
 例如，如果您計劃設定兩個外掛式主控件，如下所示：  
  
|外掛式主控件名稱|接收位置|  
|------------------------|-----------------------|  
|外掛式主控的件 1|HTTP_ReceiveLocation1A<br /><br /> HTTP_ReceiveLocation1B<br /><br /> SOAP_ReceiveLocation1**附註：** **外掛式主控件 1**用於接收 SOAP 和 HTTP 配接器處理常式。|  
|外掛式主控件 2|HTTP_ReceiveLocation2|  
  
 您可以建立四個虛擬目錄，讓每一個接收位置使用一個目錄，如下所示：  
  
|接收位置|虛擬目錄|  
|----------------------|-----------------------|  
|HTTP_ReceiveLocation1A|IIS_Virtual_Directory1A|  
|HTTP_ReceiveLocation1B|IIS_Virtual_Directory1B|  
|SOAP_ReceiveLocation1|IIS_Virtual_Directory1C|  
|HTTP_ReceiveLocation2|IIS_Virtual_Directory2|  
  
 然後，您必須，如下所示建立至少三個應用程式集區的虛擬目錄：  
  
> [!NOTE]
>  您必須至少為每一個外掛式主控件建立一個應用程式集區。  
  
|虛擬目錄|應用程式集區|Description|  
|-------------------------|----------------------|-----------------|  
|IIS_Virtual_Directory1A<br /><br /> IIS_Virtual_Directory1B|AppPool_Host1_HTTP|您不需要其他應用程式集區，因為所有接收位置都有相同的外掛式主控件 (外掛式主控件 1)，和相同的通訊協定。|  
|IIS_Virtual_Directory1C|AppPool_Host1_SOAP|您不需要其他應用程式集區，因為接收位置使用的通訊協定 (SOAP) 與同一主控件 (外掛式主控件 1) 中其他接收位置不同。|  
|IIS_Virtual_Directory2|AppPool_Host2_HTTP|您需要另一個應用程式集區，因為接收位置不是在外掛式主控件 1 下執行。|  
  
> [!NOTE]
>  您必須將應用程式集區的使用者帳戶加入適當的本機或網域群組的外掛式主控件。 如需詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。  
  
> [!NOTE]
>  您必須根據上表，在外掛式主控件執行個體與對應的應用程式集區之間對應使用者帳戶。 如需外掛式主控的件執行個體和應用程式集區的使用者帳戶之間的關聯性的詳細資訊，請參閱[如何變更服務帳戶和密碼](../core/how-to-change-service-accounts-and-passwords.md)。  
  
 **單一伺服器安裝的資料庫存取**  
  
 如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 BizTalk 管理資料庫位於同一部伺服器上，則應該將 ASP.NET 背景工作處理序或 IIS 應用程式集區的使用者內容設定為本機 ASPNET 使用者帳戶，或是具備最低權限的本機或網域使用者帳戶。  
  
 **多個伺服器安裝的資料庫存取**  
  
 如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 BizTalk 管理資料庫位於不同的伺服器上，則應該將 ASP.NET 背景工作處理序或 IIS 應用程式集區的使用者內容變更為網域使用者帳戶。  
  
 實作多重伺服器部署時，BizTalk 資料庫伺服器所屬的網域上必須有外掛式主控件 Windows 群組。  
  
 **最小化帳戶權限和使用者權限**  
  
 請使用外掛式主控件，將與 BizTalk Server 互動時所需最低限度資源的存取權限，賦予給在外部處理序中執行的配接器。 為了部署安全起見，您應該給予外部處理序的使用者內容最低權限。  
  
 **BizTalk Web 服務發佈精靈的安全性建議**  
  
 BizTalk Web 服務發佈精靈建立的虛擬目錄將繼承父系虛擬目錄或網站的存取控制清單 (ACL) 和驗證需求。 如果父系虛擬目錄或網站允許匿名存取，則 BizTalk Web 服務發佈精靈將在建立虛擬目錄時移除該功能。  
  
 下列包含 [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)] 的安全性注意事項與建議。  
  
## <a name="next"></a>下一個
  
[如何啟用 ASP.NET 的已發佈的 Web 服務](../core/how-to-enable-asp-net-4-0-for-published-web-services.md)