---
title: "密碼 Synchronization2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, passwords
- passwords, synchronizing [SSO]
- managing [SSO], synchronizing passwords
- Password Synchronization [SSO]
- Password Synchronization [SSO], about Password Synchronization
- SSO database, passwords
ms.assetid: 6d4970e0-ac73-4fca-ab8f-6c8a6f3a6ec0
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9c12bc9ff5190fe0a76c92b1cfee2233b9d206a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="password-synchronization"></a><span data-ttu-id="3b71c-102">密碼同步</span><span class="sxs-lookup"><span data-stu-id="3b71c-102">Password Synchronization</span></span>
<span data-ttu-id="3b71c-103">「密碼同步」的目的是簡化 SSO 資料庫的管理，以及讓使用者目錄的密碼同步。</span><span class="sxs-lookup"><span data-stu-id="3b71c-103">The purpose of Password Synchronization is to simplify administration of the SSO database, and to keep passwords in sync across user directories.</span></span>  
  
 <span data-ttu-id="3b71c-104">這兩個工作是透過使用密碼同步配接器來完成，本節主題描述用來建立和管理這些配接器的命令列公用程式。</span><span class="sxs-lookup"><span data-stu-id="3b71c-104">These two tasks are accomplished through the use of password synchronization adapters, and the topics in this section describe the command line utility for creating and managing those adapters.</span></span>  
  
 <span data-ttu-id="3b71c-105">密碼同步子功能有 3 種類型。</span><span class="sxs-lookup"><span data-stu-id="3b71c-105">There are three types of password synchronization sub-features.</span></span>  
  
 <span data-ttu-id="3b71c-106">第一種**Windows 至外部**(例如，Active Directory 至 RACF)。</span><span class="sxs-lookup"><span data-stu-id="3b71c-106">The first type is **Windows to External** (for example, Active Directory to RACF).</span></span> <span data-ttu-id="3b71c-107">在此情況中，會擷取 Windows 使用者的密碼變更，並傳送至被指定要從網域控制台接收密碼變更的企業單一登入伺服器。</span><span class="sxs-lookup"><span data-stu-id="3b71c-107">In this scenario, a Windows user's password change is captured and sent to the Enterprise SSO Server assigned to receive password changes from domain controllers.</span></span> <span data-ttu-id="3b71c-108">然後會將此密碼變更轉送至外部系統，同時 SSO 資料庫中的對應會與外部系統的變更保持同步。</span><span class="sxs-lookup"><span data-stu-id="3b71c-108">This then forwards the password change to an external system and the mapping in the SSO database is kept in sync with the change made on the external system.</span></span>  
  
 <span data-ttu-id="3b71c-109">第二個型別是**外部至 Windows-完整同步處理**。</span><span class="sxs-lookup"><span data-stu-id="3b71c-109">The second type is **External to Windows - Full synchronization**.</span></span> <span data-ttu-id="3b71c-110">在此情況中，會在外部系統擷取密碼，並傳送至為「密碼同步」指定的企業單一登入伺服器，然後更新 SSO 資料庫中的密碼，同時也更新 Active Directory 中的 Windows 使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="3b71c-110">In this scenario, a password is captured on the External system and sent to the Enterprise Single Sign-On server assigned for Password Synchronization which then updates the password in the SSO database, and also updates the Windows user's password in Active Directory.</span></span>  
  
 <span data-ttu-id="3b71c-111">第三種類型是**外部至 Windows-部分同步**。</span><span class="sxs-lookup"><span data-stu-id="3b71c-111">The third type is **External to Windows - Partial synchronization**.</span></span> <span data-ttu-id="3b71c-112">在此情況中，會在外部系統擷取密碼，並傳送至為「密碼同步」指定的企業單一登入伺服器，然後更新 SSO 資料庫中的密碼。</span><span class="sxs-lookup"><span data-stu-id="3b71c-112">In this scenario a password is captured on the External system and sent to the Enterprise Single Sign-On server assigned for Password Synchronization which then updates the password in the SSO database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3b71c-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="3b71c-113">In This Section</span></span>  
  
-   [<span data-ttu-id="3b71c-114">如何安裝密碼同步化</span><span class="sxs-lookup"><span data-stu-id="3b71c-114">How to Install Password Synchronization</span></span>](../core/how-to-install-password-synchronization.md)  
  
-   [<span data-ttu-id="3b71c-115">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="3b71c-115">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)  
  
-   [<span data-ttu-id="3b71c-116">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="3b71c-116">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  
  
-   [<span data-ttu-id="3b71c-117">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="3b71c-117">How to Manage Password Synchronization</span></span>](../core/how-to-manage-password-synchronization.md)