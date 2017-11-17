---
title: "實作企業單一登入 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, about SSO
- EAI
- 64-bit environments, SSO support
- SSO, 64-bit support
- SSO
- SSO, service accounts
ms.assetid: 155a62fc-5dc5-4aee-9602-b970067c1bf2
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dfd4aaf39456c68c744384aa05ff5664e781aa3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="implementing-enterprise-single-sign-on"></a><span data-ttu-id="6840f-102">實作企業單一登入</span><span class="sxs-lookup"><span data-stu-id="6840f-102">Implementing Enterprise Single Sign-On</span></span>
<span data-ttu-id="6840f-103">「企業單一登入」(SSO) 為企業應用程式整合 (EAI) 解決方案提供一般使用者的單一登入服務。</span><span class="sxs-lookup"><span data-stu-id="6840f-103">Enterprise Single Sign-On (SSO) provides services to enable single sign-on to end users for enterprise application integration (EAI) solutions.</span></span> <span data-ttu-id="6840f-104">SSO 系統將 Microsoft Windows 帳戶對應至後端認證。</span><span class="sxs-lookup"><span data-stu-id="6840f-104">The SSO system maps Microsoft Windows accounts to back-end credentials.</span></span> <span data-ttu-id="6840f-105">SSO 簡化了使用者識別碼和密碼 (包括使用者和管理員) 的管理程序。</span><span class="sxs-lookup"><span data-stu-id="6840f-105">SSO simplifies the management of user IDs and passwords, both for users and administrators.</span></span> <span data-ttu-id="6840f-106">它讓使用者只需登入一次 Windows 網路，即可存取後端系統與應用程式。</span><span class="sxs-lookup"><span data-stu-id="6840f-106">It enables users to access back-end systems and applications by logging on only once to the Windows network.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6840f-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="6840f-107">In This Section</span></span>  
  
-   [<span data-ttu-id="6840f-108">瞭解 SSO</span><span class="sxs-lookup"><span data-stu-id="6840f-108">Understanding SSO</span></span>](../core/understanding-sso.md)  
  
-   [<span data-ttu-id="6840f-109">安裝 SSO</span><span class="sxs-lookup"><span data-stu-id="6840f-109">Installing SSO</span></span>](../core/installing-sso.md)  
  
-   [<span data-ttu-id="6840f-110">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="6840f-110">Using SSO</span></span>](../core/using-sso.md)  
  
-   [<span data-ttu-id="6840f-111">保護 SSO 部署的</span><span class="sxs-lookup"><span data-stu-id="6840f-111">Securing Your Deployment of SSO</span></span>](../core/securing-your-deployment-of-sso.md)  
  
-   [<span data-ttu-id="6840f-112">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="6840f-112">Password Synchronization</span></span>](../core/password-synchronization2.md)  
  
-   [<span data-ttu-id="6840f-113">SSO 安全性建議</span><span class="sxs-lookup"><span data-stu-id="6840f-113">SSO Security Recommendations</span></span>](../core/sso-security-recommendations.md)