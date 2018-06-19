---
title: 檢查清單： 監控 BizTalk Server 與 Operations Manager 2007 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2e1f7f57-1501-473f-af5f-15f3e1ddaf8e
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 810ede830f7142181c4bec1f727cbc496049ce03
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22300054"
---
# <a name="checklist-monitoring-biztalk-server-with-operations-manager-2007"></a>檢查清單： 監控 BizTalk Server 與 Operations Manager 2007
本主題列出當您準備監視，您可以遵循的高層級步驟您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
|步驟|參考|  
|----------|---------------|  
|請確定您有適當的權限，安裝及設定軟體在您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。|[最小安全性使用者權限](http://go.microsoft.com/fwlink/?LinkID=154374)(http://go.microsoft.com/fwlink/?LinkID=154374)|  
|Operations Manager 2007 代理程式安裝在每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您想要監視，並指向 Operations Manager 2007 伺服器電腦。|請參閱[部署 Operations Manager 2007](http://go.microsoft.com/fwlink/?LinkId=110030) (http://go.microsoft.com/fwlink/?LinkId=110030)|  
|下載並匯入下列管理組件的適當版本：<br /><br /> -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]（必要）<br />企業單一登入 （必要）<br />Windows 基底 OS （伺服器） （選擇性）<br />Microsoft Windows 伺服器叢集 （如果叢集使用的選擇性）<br />SQL Server 2008、 SQL Server 2005 （選擇性）<br />網際網路資訊服務 (IIS) 2008 中，IIS 2003 （選擇性）<br />訊息佇列 (MSMQ) 3.0 （選擇性）|-下載管理組件從[System Center 管理組件類別目錄](http://go.microsoft.com/fwlink/?LinkId=203227)(http://go.microsoft.com/fwlink/?LinkId=203227)。<br />-匯入管理組件依照指示在[如何匯入 Operations Manager 2007 管理組件](http://go.microsoft.com/fwlink/?LinkID=98348)(http://go.microsoft.com/fwlink/?LinkID=98348)。|  
|閱讀使用 Operations Manager 2010 監控的最佳作法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。|[使用 Operations Manager 2007 監視的最佳作法](../technical-guides/best-practices-for-monitoring-with-operations-manager-2007.md)|  
|啟用或停用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]規則視需要的管理組件。|[使用 Operations Manager 2007 監視的最佳作法](../technical-guides/best-practices-for-monitoring-with-operations-manager-2007.md)|  
|任何獨立企業單一登入 (SSO) 將電腦新增至 BizTalk Server 管理組件所監視的電腦清單。|[如何將企業單一登入 」 電腦新增至 BizTalk Server 管理組件所監視的電腦清單](http://go.microsoft.com/fwlink/?LinkId=157263)(http://go.microsoft.com/fwlink/?LinkId=157263)。|  
  
## <a name="see-also"></a>另請參閱  
 [監控 BizTalk Server 與 System Center Operations Manager 2007](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)