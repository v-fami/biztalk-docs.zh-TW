---
title: 如何變更服務帳戶和密碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dff53d6b-c262-4b66-b822-1c61f54ae105
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77ce9dc143765f9db49c5880da4fa4202e26c0f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248886"
---
# <a name="how-to-change-service-accounts-and-passwords"></a>如何變更服務帳戶和密碼
設定 BizTalk Server 之後，組織通常需要依據帳戶原則 (例如，密碼原則和帳戶鎖定原則) 變更服務帳戶或密碼。 如需有關帳戶原則的詳細資訊，請參閱 Microsoft TechNet 網站，網址[http://go.microsoft.com/fwlink/?LinkId=62172](http://go.microsoft.com/fwlink/?LinkId=62172)。  
  
 變更服務帳戶或密碼時，您必須執行下列動作：  
  
1.  建立新服務帳戶，或變更現有帳戶的密碼。  
  
2.  確定服務帳戶是必要 Windows 群組的成員。 您必須將服務帳戶加入其中的本機或網域群組的相關資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。  
  
    > [!NOTE]
    >  在網域群組環境中，您要使用 [Active Directory 使用者及電腦] 主控台。 在本機群組環境中，您要使用 [電腦管理] 主控台。  
  
3.  視服務帳戶類型而定，執行下列工作。  
  
    |服務或帳戶|如何變更使用者帳戶|變更使用者帳戶之後的必要工作|如何變更密碼|變更密碼之後的必要工作|  
    |------------------------|---------------------------------|-------------------------------------------------|-----------------------------|---------------------------------------------|  
    |主要密碼伺服器上的企業單一登入 (SSO) 服務|1.請確定您具有主要密碼的備份。 如需詳細資訊，請參閱[如何重新設定主要密碼](../core/how-to-back-up-the-master-secret.md)。<br />2.使用 [服務] 主控台變更服務帳戶。<br />3.還原主要密碼。 如需詳細資訊，請參閱[如何還原主要密碼](../core/how-to-restore-the-master-secret.md)。|重新啟動服務|使用 [服務] 主控台變更帳戶密碼。|重新啟動服務|  
    |企業單一登入服務|使用 [服務] 主控台變更服務帳戶。|重新啟動服務|使用 [服務] 主控台變更帳戶密碼。|重新啟動服務|  
    |BizTalk 主控件執行個體|使用 BizTalk Server 管理主控台變更服務帳戶|重新啟動 BizTalk 主控件執行個體。|使用 [BizTalk Server 管理] 主控台或 [服務] 主控台變更帳戶的密碼。|重新啟動 BizTalk 主控件執行個體|  
    |BizTalk 外掛式主控件執行個體以及裝載 SOAP 接收配接器的對應應用程式集區|1.使用 BizTalk Server 管理主控台變更服務帳戶<br />2.變更使用 IIS 管理主控台應用程式集區帳戶**附註：** 應用程式集區的服務帳戶應該符合對應的外掛式主控件服務帳戶。|1.使用 [IIS 管理] 主控台變更對應應用程式集區的服務帳戶。<br />2.使用 [IIS 管理] 主控台重新啟動應用程式集區。|變更執行應用程式集區之帳戶的密碼。 使用 IIS 管理主控台**附註：** 您不需要變更密碼之後變更 BizTalk Server 管理主控台中的密碼。|1.使用 [IIS 管理] 主控台變更執行對應應用程式集區之帳戶的密碼。<br />2.使用 [IIS 管理] 主控台重新啟動應用程式集區。|  
    |規則引擎更新服務|使用 [組態管理員] 或 [服務] 主控台變更服務帳戶。<br /><br /> 「組態管理員」會自動重新啟動服務。|如果您使用 [服務] 主控台，則必須手動重新啟動服務。|使用 [組態管理員] 或 [服務] 主控台變更帳戶的密碼。<br /><br /> 「組態管理員」會自動重新啟動服務。|如果您使用 [服務] 主控台，則必須手動重新啟動服務。|  
    |BAM Notification Services|1.將新帳戶新增至安裝 BAM Notification Service 所在的 SQL Server。<br />2.將權限授與新帳戶。 如需必要權限的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)<br />3.使用 [服務] 主控台變更服務帳戶。|重新啟動服務|使用 [服務] 主控台變更帳戶的密碼|重新啟動服務|  
    |BAM 管理 Web 服務|1.將新的帳戶新增至適當的 SQL server，並授與的權限中[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。<br />2.使用 [組態管理員] 變更使用者帳戶。||使用 [組態管理員] 變更使用者帳戶密碼。||  
    |BAM 應用程式集區|使用 [組態管理員] 變更應用程式集區的服務帳戶。<br /><br /> 「組態管理員」會自動回收應用程式集區。||使用 [組態管理員] 變更帳戶密碼。<br /><br /> 「組態管理員」會自動回收應用程式集區。||  
  
 下列程序說明如何使用 [組態管理員] 變更服務帳戶及密碼。  
  
### <a name="to-change-service-accounts-and-passwords-using-configuration-manager"></a>使用組態管理員變更服務帳戶及密碼  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 組態**。  
  
2.  在**Microsoft BizTalk Server 組態**，按一下 **檢視**，按一下 **服務帳戶**，然後變更服務帳戶和密碼的**服務帳戶** 對話方塊。 如需 Configuration Manager 的詳細資訊，請參閱[匯入和匯出 BizTalk Server 組態](../install-and-config-guides/import-and-export-biztalk-server-configuration.md)。  
  
    > [!NOTE]
    >  組態管理員不會提供用來控制多部電腦的集中位置。 如果您在多部電腦上安裝 Microsoft BizTalk Server，您就必須變更每部執行階段電腦上的服務帳戶和密碼。  
  
## <a name="see-also"></a>另請參閱  
 [Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)   
 [設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)   
 [管理 BizTalk Server 安全性](../core/managing-biztalk-server-security.md)   
 [管理 Windows 群組和使用者帳戶的最佳作法](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)   
 [管理主控件和服務帳戶](../core/managing-hosts-and-service-accounts.md)