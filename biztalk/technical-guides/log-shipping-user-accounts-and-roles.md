---
title: 記錄傳送的使用者帳戶和角色 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2056ea90-5e9f-4501-95d6-18c905db4023
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3d82e9cd3f1ea942513319d0d68d528762ef35a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024484"
---
# <a name="log-shipping-user-accounts-and-roles"></a>記錄傳送的使用者帳戶和角色
BizTalk Server 記錄傳送還原的備份和記錄檔的程序自動化時由 SQL Server Agent 作業。 不正確的權限可能會導致執行失敗的 BizTalk Server 記錄傳送還原作業。 設定要還原資料庫的使用者帳戶必須具有裝載 BizTalk 管理資料庫的生產資料庫執行個體的存取。 在大部分情況下這表示，服務帳戶的驅動 BizTalk Server 記錄傳送作業的災害復原的 SQL Server Agent 作業[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體所需的登入和裝載生產資料庫執行個體上的權限[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理資料庫。 這是假設 SQL Server Agent 服務帳戶設定為作業擁有者。  

 BizTalk Server 包含名為 BTS_BACKUP_USERS，以便設定要還原資料庫的使用者帳戶不需要 SQL Server 系統管理員權限的 SQL Server 角色。  

 設定在 BizTalk Server 記錄傳送將會執行資料庫還原作業的使用者帳戶時，請確認下列項目：  

- 將 SQL Server Agent 服務設定為使用對應的使用者設定中執行的網域帳戶[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio (在**安全性**，**登入**) 在每個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體主機[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]還原資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送作業。  

- 設定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]登入帳戶對這個使用者而言，並將此使用者指派給每部伺服器上的 BizTalk BTS_BACKUP_USERS 的 SQL 角色。  

- 此將使用者指派至[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行的電腦上的系統管理員角色[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]所裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理資料庫。  

- 帳戶執行備份和還原作業必須具有讀取和寫入權限的 UNC 共用位置建立備份檔案。
