---
title: "步驟 3： 設定網域控制站 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, domain controller
- domain controller
ms.assetid: 1c513225-378b-4e57-ba29-7532b6cbcc9a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad3cdf84f5a392a8d5f836e78c57f782e14d0639
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-configuring-the-domain-controller"></a>步驟 3： 設定網域控制站
本章節描述如何設定網域控制站，在您[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]部署。 具體來說，本章節描述如何安裝及設定[!INCLUDE[btsAD](../../includes/btsad-md.md)]執行下列步驟：  
  
-   安裝 Active Directory 和 DNS  
  
-   建立所需的帳戶  
  
-   若要加入網域  
  
## <a name="installing-active-directory-and-dns"></a>安裝 Active Directory 和 DNS  
 使用[!INCLUDE[btsAD](../../includes/btsad-md.md)]安裝精靈，以簡化設定網域控制站的程序。 安裝 Active Directory 之後, 建立網域名稱系統 (DNS) 反向對應區域。 接著建立，並將主機新增至 正向和反向對應區域。  
  
## <a name="creating-the-required-accounts"></a>建立所需的帳戶  
 下表提供有關如何建立全域安全性群組的詳細資料。 建立下列**全域安全性群組**群組和使用者使用您自己的命名慣例的網域控制站上。 以下提供的範例可用於簡化。 將建立的群組清單中指定的成員。  
  
 建立群組時，選取**Global**群組領域和**安全性**群組類型。  
  
|帳戶或群組名稱|類型|Description|成員|  
|---------------------------|----------|-----------------|-------------|  
|管理|使用者|所有的 BizTalk 電腦、 網域控制站及執行 SQL Server 的所有電腦的本機系統管理帳戶。<br /><br /> 這是用於安裝應用程式網域使用者帳戶 ([!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]， [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]，和 SQL Server) 和設定 BizTalk Accelerator for A4SWIFT，在設計階段期間。 沒有具有網域系統管理員權限來執行 A4SWIFT 安裝。 系統管理員使用者帳戶必須是 Domain Users 群組及網域 BizTalk Server 系統管理員群組中，本機 Administrators 群組的成員||  
|SQLSvc|使用者|執行 SQL Server 服務帳戶||  
|SSOSvc|使用者|執行單一登入 (SSO) 服務帳戶||  
|HostSvc|使用者|執行 BizTalk 主控件服務帳戶||  
|IsolatedSvc|使用者|執行 BizTalk 外掛式主控服務帳戶||  
|BAMSvc|使用者|所需的 BAMPortal BAMAlerts 及 BAMTools 的 BizTalk Server 組態||  
|BRESvc|使用者|執行規則引擎更新服務服務帳戶||  
|Domain Admins|網域群組|網域系統管理員的通用網域群組帳戶||  
|BizTalk 外掛式主控件使用者|網域群組|全域網域群組帳戶與外掛式 BizTalk 主控件 （主機處理序並未執行 BizTalk Server 中，例如 HTTP 和 SOAP） 存取權。|\<IsolatedSvc >， \<HostSvc >|  
|BizTalk Server 系統管理員|網域群組|具有執行組態架構精靈中所含的系統管理工作，以及管理 BizTalk Server 所需的最低權限的全域網域群組帳戶。|\<系統管理員 >|  
|BizTalk 應用程式使用者|網域群組|BizTalk 應用程式使用者的全域網域群組帳戶。|\<HostSvc >|  
|BizTalk Server 操作員|網域群組|具有執行工作所需的安裝後操作 BizTalk Server 環境所需的最低權限的群組。||  
|啟用 SharePoint 的主控件|網域群組|Windows 群組具有呼叫 Windows SharePoint Services 配接器 Web 服務的權限。|\<HostSvc >|  
|SSO 系統管理員|網域群組|SSO 系統管理員的通用網域群組帳戶。|\<系統管理員 >， \<SSOSvc >|  
|SSO 分支機構系統管理員|網域群組|全域網域群組帳戶，sso 分支機構系統管理員|\<系統管理員 >|  
|A4SWIFT 使用者|網域群組|具有 A4SWIFT 中執行基本的工作所需的最低權限的全域網域群組帳戶。|\<HostSvc >、 其他網路使用者|  
|A4SWIFT 系統管理員|網域群組|全域網域群組具有管理 A4SWIFT 所需的最低權限的帳戶。|\<系統管理員 >|  
  
> [!NOTE]
>  全域安全性帳戶和不是本機網域帳戶，應該是所有的群組帳戶。 如果使用本機網域群組帳戶 （使用 net localgroup 建立），安裝程式的[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]無法驗證特定[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]網域使用者。  
  
## <a name="joining-the-domain"></a>若要加入網域  
 在建立定義域，並重新啟動網域控制站之後，將每一部伺服器加入網域。