---
title: "SSO 元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passwords, synchronizing [SSO]
- SSO, components
- SSO, password synchronization
- SSO, sub-services
ms.assetid: e29e68df-f770-4220-a9f8-cb9323403017
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1111f1a0dfac47412ae28b58f93ddc51e1f562b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sso-components"></a><span data-ttu-id="437e6-102">SSO 元件</span><span class="sxs-lookup"><span data-stu-id="437e6-102">SSO Components</span></span>
<span data-ttu-id="437e6-103">企業單一登入 (SSO) 服務的子服務如下：</span><span class="sxs-lookup"><span data-stu-id="437e6-103">The sub services of the Enterprise Single Sign-On (SSO) service are as follows:</span></span>  
  
-   <span data-ttu-id="437e6-104">**對應。**</span><span class="sxs-lookup"><span data-stu-id="437e6-104">**Mapping.**</span></span> <span data-ttu-id="437e6-105">此元件將 Windows 系統中的使用者帳戶對應至後端系統中的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="437e6-105">This component maps the user account in the Windows system to the user accounts in the back-end systems.</span></span>  
  
-   <span data-ttu-id="437e6-106">**查閱。**</span><span class="sxs-lookup"><span data-stu-id="437e6-106">**Lookup.**</span></span> <span data-ttu-id="437e6-107">此元件會尋查後端系統中 SSO 資料庫的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="437e6-107">This component looks up the user credentials in the SSO database in the back-end system.</span></span> <span data-ttu-id="437e6-108">這是 SSO 執行階段元件。</span><span class="sxs-lookup"><span data-stu-id="437e6-108">This is the SSO runtime component.</span></span>  
  
-   <span data-ttu-id="437e6-109">**系統管理。**</span><span class="sxs-lookup"><span data-stu-id="437e6-109">**Administration.**</span></span> <span data-ttu-id="437e6-110">此元件管理分支機構應用程式與每個分支機構應用程式的對應。</span><span class="sxs-lookup"><span data-stu-id="437e6-110">This component manages the affiliate applications and the mappings for each affiliate application.</span></span>  
  
-   <span data-ttu-id="437e6-111">**密碼。**</span><span class="sxs-lookup"><span data-stu-id="437e6-111">**Secret.**</span></span> <span data-ttu-id="437e6-112">此元件會產生主要密碼，然後將它分派至系統中的其他 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="437e6-112">This component generates the master secret and distributes it to the other SSO servers in the system.</span></span> <span data-ttu-id="437e6-113">它只在扮演主要密碼伺服器的單一登入伺服器上才有作用。</span><span class="sxs-lookup"><span data-stu-id="437e6-113">It is only active on the Single Sign-On server that is acting as the master secret server.</span></span>  
  
-   <span data-ttu-id="437e6-114">**密碼同步處理。**</span><span class="sxs-lookup"><span data-stu-id="437e6-114">**Password Synchronization.**</span></span> <span data-ttu-id="437e6-115">此元件簡化 SSO 資料庫的管理，維持跨使用者目錄的密碼同步。</span><span class="sxs-lookup"><span data-stu-id="437e6-115">This component simplifies administration of the SSO database, and keeps passwords in sync across user directories.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="437e6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="437e6-116">See Also</span></span>  
 <span data-ttu-id="437e6-117">[SSO 伺服器](../core/sso-server.md) </span><span class="sxs-lookup"><span data-stu-id="437e6-117">[SSO Server](../core/sso-server.md) </span></span>  
 [<span data-ttu-id="437e6-118">安裝 SSO</span><span class="sxs-lookup"><span data-stu-id="437e6-118">Installing SSO</span></span>](../core/installing-sso.md)