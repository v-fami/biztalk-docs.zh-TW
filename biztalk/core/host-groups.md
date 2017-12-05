---
title: "主機群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host groups, privileges
- Windows groups, host groups
- host groups, Windows groups
- host groups, about host groups
- host groups
ms.assetid: 0d92478b-b3a2-4c5a-925e-5495ee481e82
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 98e3798e42442e1a6533e4f286d194c8e2474be6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="host-groups"></a>主控件群組
主控件群組是 Windows 群組 (預設名稱為「BizTalk 應用程式使用者」群組)，用於具有內含式 BizTalk 主控件 (BizTalk Server 中的主控件程序) 存取權的帳戶。 建議您在環境中對每個內含式主控件使用一個主控件群組。  
  
 只將一個 Windows 群組與主機相關聯 (稱為*主機群組*)。 主控件群組必須擁有所有相關的 BizTalk Server 資料庫中的 SQL Server 登入和權限。 建立主控件與主控件群組的關聯時，您就將主控件群組的權限授與主控件。  
  
 若是使用「組態精靈」建立主控件，而且指定本機 Windows 群組用於主控件，則「組態精靈」會自動建立兩個 Windows 群組。 這些群組的預設名稱為「BizTalk 應用程式使用者」群組及「BizTalk 外掛式主控件使用者」群組。  
  
 建立與主控件群組關聯之主控件的主控件執行個體時，此主控件執行個體即繼承了主控件群組的資料庫權限。  
  
 主控件群組是主控件 Windows Management Instrumentation (WMI) 物件的屬性。 若是主控件沒有主控件執行個體，則可變更主控件所屬的 Windows 群組。  
  
 建立主控件時可指定主控件所屬的主控件群組。 BizTalk WMI 提供者將主控件群組具有的權限授與主控件，例如，BizTalk Server 執行階段功能的權限，包括 SQL Server 登入和資料庫使用者存取。 建立主控件執行個體時必須指定正確的服務帳戶 (主控件)，如此 BizTalk Server WMI 提供者才能將主控件群組的權限授與主控件執行個體。  
  
> [!NOTE]
>  若是要建立本機主控件群組，可以建立本機 Windows 群組，並指定網域使用者為群組成員。 若指定本機 Windows 群組給主控件，則無論是網域或本機使用者的 Windows 群組成員都可以做為主控件執行個體登入使用者。  
  
 主控件群組需要下列權限：  
  
-   它在下列資料庫中必須是 BTS_HOST_USERS SQL Server 角色的成員：  
  
    -   BizTalk 管理資料庫 (在 [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 中是為組態資料庫)  
  
    -   MessageBox  
  
    -   規則引擎  
  
    -   追蹤  
  
    -   BAM 主要匯入  
  
-   它必須是成員的 BTS_<\<內含式主控件名稱\>（_u） MessageBox 資料庫的 SQL Server 角色  
  
-   在 BAM 主要匯入資料庫中必須是 BAM_EVENT_WRITER SQL Server 角色的成員。  
  
> [!NOTE]
>  若是指定主控件為追蹤主控件，「BizTalk Server 管理」會自動為「追蹤」資料庫移除 SQL Server 角色中的「BizTalk 主控件」群組。 您必須從「BizTalk 管理」資料庫和 MessageBox 資料庫的 SQL Server 角色中，手動移除 BizTalk 主控件群組。 如需將主控件指定為追蹤主控件的資訊，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。  
  
## <a name="see-also"></a>請參閱  
 [實體](../core/entities.md)