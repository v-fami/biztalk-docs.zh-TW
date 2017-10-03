---
title: "記錄傳送的使用者帳戶和角色 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2056ea90-5e9f-4501-95d6-18c905db4023
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b19a7d7c87289e07c7ac7a26bacd0c96f9090c9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="log-shipping-user-accounts-and-roles"></a>記錄傳送的使用者帳戶和角色
[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]記錄傳送是由 SQL Server Agent 作業所驅動，若要還原的備份和記錄檔的程序自動化。 不正確的權限可能會造成還原作業所執行[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]記錄傳送失敗。 設定要還原資料庫的使用者帳戶必須具有裝載 BizTalk 管理資料庫的生產資料庫執行個體的存取。 在大部分情況下這表示服務帳戶的 SQL Server Agent 工作推動[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]災害復原的記錄傳送作業[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體所需的登入和權限的生產資料庫執行個體裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理資料庫。 這樣會假設 SQL Server Agent 服務帳戶設定為作業的擁有者。  
  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]包含名為 BTS_BACKUP_USERS，以便設定要還原資料庫的使用者帳戶不需要 SQL Server 系統管理員權限的 SQL Server 角色。  
  
 設定將會執行資料庫還原作業的一部分的使用者帳戶時[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]記錄傳送，請確認以下事項：  
  
-   SQL Server Agent 服務設定為使用中設定對應的使用者網域帳戶下執行[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio (在**安全性**，**登入**) 在每個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體主機[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫還原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送作業。  
  
-   設定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]登入帳戶對這個使用者而言，並將此使用者指派給每個伺服器上的 BizTalk BTS_BACKUP_USERS SQL 角色。  
  
-   這將使用者指派至[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行的電腦上的系統管理員角色[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理資料庫。  
  
-   帳戶執行備份和還原作業必須具有讀取和寫入權限 UNC 共用位置建立備份檔案。