---
title: 設定 IIS 的外掛式 WCF 接收配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive adapters, WCF services
- WCF services, receive adapters
- IIS, configuring [WCF receive adapters]
ms.assetid: 1c6f1561-a7ba-4eb0-8878-bf213ebcd6a6
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1515a69ab6a9150668db4f3415f0483dd1ce4e7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233366"
---
# <a name="configuring-iis-for-the-isolated-wcf-receive-adapters"></a>針對外掛式 WCF 接收配接器設定 IIS
若要使用 BizTalk WCF 服務發佈精靈來發佈 WCF 服務，您必須設定 Internet Information Services (IIS)、BizTalk 外掛式主控件和 Windows 使用者群組帳戶。 本節討論的問題與設定 IIS 以外掛式 WCF 接收配接器 (例如 WCF-BasicHttp 接收配接器、WCF-WSHttp 接收配接器和 WCF-CustomIsolated 配接器) 發佈 WCF 服務有關。 一般 WCF 服務裝載在 IIS 的詳細資訊，請參閱 < 裝載於 IIS >，網址[http://go.microsoft.com/fwlink/?LinkId=75700](http://go.microsoft.com/fwlink/?LinkId=75700)。  
  
## <a name="considerations-when-configuring-iis"></a>設定 IIS 的考量  
 **Internet Information Services 7.0 和 7.5**  
  
 您可以使用以 ASP.NET 4.0 設定的 IIS 7.0 和 7.5，利用外掛式 WCF 接收配接器來發佈 WCF 服務。  
  
 IIS 7.0 (適用於 Windows Server 2008 SP2) 和 IIS 7.5 (適用於 Windows Server 2008 R2) 會使用 IIS 應用程式集區來處理 Web 服務要求。 IIS 7.0 支援多個應用程式集區。 每個應用程式集區處理序都可以在不同的使用者環境下執行。  
  
 **BizTalk 外掛式主控件**  
  
 若要以外掛式 WCF 接收配接器裝載 WCF 服務，您必須在 BizTalk Server 中建立至少一個外掛式主控件。 如需如何設定 BizTalk 外掛式主控件的詳細資訊，請參閱 「 BizTalk 外掛式主控件 」 中[啟用 Web 服務](../core/enabling-web-services.md)。  
  
 **多個伺服器安裝的資料庫存取**  
  
 如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 BizTalk 管理資料庫位於不同的伺服器上，則應該將 IIS 應用程式集區的使用者內容變更為網域使用者帳戶。  
  
 實作多重伺服器部署時，BizTalk 資料庫伺服器所屬的網域上必須有外掛式主控件 Windows 群組。  
  
 **最小化帳戶權限和使用者權限**  
  
 請使用外掛式主控件，將與 BizTalk Server 互動時所需最低限度資源的存取權限，賦予給在外部處理序中執行的配接器。 為了部署安全起見，您應該給予外部處理序的使用者內容最低權限。  
  
 **BizTalk Web 服務發佈精靈的安全性建議**  
  
 BizTalk WCF 服務發佈精靈建立的虛擬目錄繼承了父系虛擬目錄或網站的存取控制清單 (ACL)。  
  
## <a name="see-also"></a>另請參閱  
 [發佈 WCF 服務](../core/publishing-wcf-services.md)