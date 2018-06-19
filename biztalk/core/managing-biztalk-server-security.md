---
title: 管理 BizTalk Server 安全性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Server, security
- security, user accounts
- security, passwords
- certificates, security
- security, certificates
- security, BizTalk Server
- passwords, security
- user accounts, security
ms.assetid: adc89b0a-9846-4c99-b0fc-a32fc56ed769
caps.latest.revision: 31
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f31ef3483661b20ff62cadb0ec601282a05af9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262854"
---
# <a name="managing-biztalk-server-security"></a>管理 BizTalk Server 安全性
若要維護安全的 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境，您必須管理帳戶、憑證及密碼。 為了確保 BizTalk Server 所處理之商務文件的安全性，BizTalk Server 系統管理員必須管理下列帳戶及憑證：  
  
-   **BizTalk Server 系統管理員群組**。 對於透過 BizTalk 管理主控台或使用 Microsoft Windows Management Instrumentation (WMI) 提供者執行系統管理工作的使用者而言，他們必須在 Microsoft SQL Server 及 Microsoft Windows 被授與適當的權限。 如需系統管理工作的權限的詳細資訊，請參閱[最低安全性使用者權限](../core/minimum-security-user-rights.md)。  
  
     新增使用者至 BizTalk Server 系統管理員群組，或從 BizTalk Server 系統管理員群組移除使用者的相關資訊，請參閱[如何管理 BizTalk Server 系統管理員群組](../core/how-to-manage-the-biztalk-server-administrators-group.md)。  
  
     如需企業單一登入的詳細資訊，請參閱[使用 SSO](../core/using-sso.md)。  
  
-   **BizTalk Server 操作員群組**。 BizTalk Server 操作員是具有低層級權限的角色，只能存取監視和疑難排解動作。  
  
     BizTalk Server 操作員群組的成員可執行下列動作：  
  
    -   檢視服務狀態及訊息流程。  
  
    -   啟動或停止應用程式。  
  
    -   啟動或停止協調流程。  
  
    -   啟動或停止傳送埠或傳送埠群組。  
  
    -   啟用或停用接收位置。 在下一個 60 秒 (預設值) 的快取重新整理間隔之前，變更不會生效。 快取重新整理間隔視在 BizTalk Server 群組層級設定。  
  
    -   終止和繼續服務執行個體。  
  
     BizTalk Server 操作員群組的成員無法執行下列動作：  
  
    -   修改 BizTalk Server 的組態。  
  
    -   檢視分類為個人識別資訊 (PII) 的訊息內容屬性或訊息內文。  
  
    -   修改訊息路由過程，例如移除或新增新的訂閱到執行中的系統，包括將訊息發佈到 BizTalk Server 執行階段。  
  
    > [!NOTE]
    >  如果身為 BizTalk Server 操作員群組成員的使用者同時也是 BizTalk Server 電腦的本機系統管理員，則此使用者可存取這些電腦上之操作員群組角色外的資料。 如需詳細資訊，請參閱[最低安全性使用者權限](../core/minimum-security-user-rights.md)。  
  
    > [!NOTE]
    >  如果您要允許 BizTalk Server 操作員群組成員的使用者監視遠端 BizTalk Server，此使用這必須也是遠端電腦上之本機系統管理員群組的成員。  
  
-   **主機和服務帳戶**。 建立主控件及其關聯的主控件執行個體時，您必須提供主控件的 Windows 群組以及每個主控件執行個體的服務帳戶憑證。 您必須確定主控件執行個體服務帳戶為主控件的 Windows 群組成員。  
  
-   **簽署憑證**。 BizTalk 群組已指定簽章憑證 (私用金鑰憑證)。 這些憑證是選擇性的，BizTalk Server 系統管理員可隨時變更這些憑證。  
  
 如需更完整的 BizTalk Server 會使用 Windows 帳戶的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [管理 Windows 群組和使用者帳戶的最佳作法](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)  
  
-   [管理憑證的最佳作法](../core/best-practices-for-managing-certificates1.md)  
  
-   [管理 Windows 群組和使用者帳戶](../core/managing-windows-groups-and-user-accounts.md)