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
# <a name="log-shipping-user-accounts-and-roles"></a><span data-ttu-id="1bef8-102">記錄傳送的使用者帳戶和角色</span><span class="sxs-lookup"><span data-stu-id="1bef8-102">Log Shipping User Accounts and Roles</span></span>
<span data-ttu-id="1bef8-103">BizTalk Server 記錄傳送還原的備份和記錄檔的程序自動化時由 SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="1bef8-103">BizTalk Server log shipping is driven by a SQL Server Agent job to automate the process of restoring backups and logs.</span></span> <span data-ttu-id="1bef8-104">不正確的權限可能會導致執行失敗的 BizTalk Server 記錄傳送還原作業。</span><span class="sxs-lookup"><span data-stu-id="1bef8-104">Incorrect permissions can cause restore operations performed by BizTalk Server log shipping to fail.</span></span> <span data-ttu-id="1bef8-105">設定要還原資料庫的使用者帳戶必須具有裝載 BizTalk 管理資料庫的生產資料庫執行個體的存取。</span><span class="sxs-lookup"><span data-stu-id="1bef8-105">The user account configured to restore databases must have access to the production database instance that hosts the BizTalk Management database.</span></span> <span data-ttu-id="1bef8-106">在大部分情況下這表示，服務帳戶的驅動 BizTalk Server 記錄傳送作業的災害復原的 SQL Server Agent 作業[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體所需的登入和裝載生產資料庫執行個體上的權限[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="1bef8-106">In most cases this means that the service account for the SQL Server Agent job driving the BizTalk Server log shipping job on the disaster recovery [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance requires a login and permissions on the production database instance that hosts the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management database.</span></span> <span data-ttu-id="1bef8-107">這是假設 SQL Server Agent 服務帳戶設定為作業擁有者。</span><span class="sxs-lookup"><span data-stu-id="1bef8-107">This assumes that the SQL Server Agent service account is configured as the job owner.</span></span>  

 <span data-ttu-id="1bef8-108">BizTalk Server 包含名為 BTS_BACKUP_USERS，以便設定要還原資料庫的使用者帳戶不需要 SQL Server 系統管理員權限的 SQL Server 角色。</span><span class="sxs-lookup"><span data-stu-id="1bef8-108">BizTalk Server includes a SQL Server role named BTS_BACKUP_USERS so that the user account configured to restore databases does not require SQL Server System Administrators permission.</span></span>  

 <span data-ttu-id="1bef8-109">設定在 BizTalk Server 記錄傳送將會執行資料庫還原作業的使用者帳戶時，請確認下列項目：</span><span class="sxs-lookup"><span data-stu-id="1bef8-109">When configuring the user account that will perform database restore operations as part of BizTalk Server log shipping, please verify the following:</span></span>  

- <span data-ttu-id="1bef8-110">將 SQL Server Agent 服務設定為使用對應的使用者設定中執行的網域帳戶[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio (在**安全性**，**登入**) 在每個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體主機[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]還原資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送作業。</span><span class="sxs-lookup"><span data-stu-id="1bef8-110">Configure the SQL Server Agent service to run under a domain account with a mapped user configured in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio (in **Security**, **Logins**) on each [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance that hosts [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases restored by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping jobs.</span></span>  

- <span data-ttu-id="1bef8-111">設定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]登入帳戶對這個使用者而言，並將此使用者指派給每部伺服器上的 BizTalk BTS_BACKUP_USERS 的 SQL 角色。</span><span class="sxs-lookup"><span data-stu-id="1bef8-111">Configure a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] login account for this user, and assign this user to the BizTalk BTS_BACKUP_USERS SQL role on each server.</span></span>  

- <span data-ttu-id="1bef8-112">此將使用者指派至[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行的電腦上的系統管理員角色[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]所裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="1bef8-112">Assign this user to the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] System Administrators role on the computer running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that houses the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management database.</span></span>  

- <span data-ttu-id="1bef8-113">帳戶執行備份和還原作業必須具有讀取和寫入權限的 UNC 共用位置建立備份檔案。</span><span class="sxs-lookup"><span data-stu-id="1bef8-113">The account that performs backup and restore operations must have Read and Write access to the UNC share where backup files are created.</span></span>
