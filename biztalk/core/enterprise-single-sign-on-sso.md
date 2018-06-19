---
title: 企業單一登入 (SSO) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSO, about SSO
- SSO
ms.assetid: beab96f7-f026-4ae1-8462-a165ad76bbec
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f6cbc5f514d13cd8457cd9417be5ea5b78408e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240150"
---
# <a name="enterprise-single-sign-on-sso"></a><span data-ttu-id="a6dee-102">企業單一登入 (SSO)</span><span class="sxs-lookup"><span data-stu-id="a6dee-102">Enterprise Single Sign-On (SSO)</span></span>
<span data-ttu-id="a6dee-103">「企業單一登入」(SSO) 所提供的服務，可跨越本機與網路界限 (包含網域界限) 來儲存和傳輸加密的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="a6dee-103">Enterprise Single Sign-On (SSO) provides services to store and transmit encrypted user credentials across local and network boundaries, including domain boundaries.</span></span> <span data-ttu-id="a6dee-104">SSO 將認證儲存在 SSO 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="a6dee-104">SSO stores the credentials in the SSO database.</span></span> <span data-ttu-id="a6dee-105">因為 SSO 提供的是一般的單一登入解決方案，所以中介軟體應用程式和自訂配接器都能利用 SSO 安全地在整個環境內儲存及傳輸使用者認證。</span><span class="sxs-lookup"><span data-stu-id="a6dee-105">Because SSO provides a generic single sign-on solution, middleware applications and custom adapters can leverage SSO to securely store and transmit user credentials across the environment.</span></span> <span data-ttu-id="a6dee-106">一般使用者不用再記住各個應用程式的不同認證了。</span><span class="sxs-lookup"><span data-stu-id="a6dee-106">End users do not have to remember different credentials for different applications.</span></span>  
  
 <span data-ttu-id="a6dee-107">「單一登入」系統是由一個 SSO 資料庫、一個主要密碼伺服器，以及一或多個單一登入伺服器所組成。</span><span class="sxs-lookup"><span data-stu-id="a6dee-107">The Single Sign-On system consists of an SSO database, a master secret server, and one or more Single Sign-On servers.</span></span>  
  
 <span data-ttu-id="a6dee-108">SSO 系統包含*分支機構應用程式*系統管理員所定義。</span><span class="sxs-lookup"><span data-stu-id="a6dee-108">The SSO system contains *affiliate applications* that an administrator defines.</span></span> <span data-ttu-id="a6dee-109">*分支機構應用程式*是代表系統或子系統，例如主機、 後端系統或企業營運應用程式的邏輯實體您連接使用企業單一登入。</span><span class="sxs-lookup"><span data-stu-id="a6dee-109">An *affiliate application* is a logical entity that represents a system or sub-system such as a host, back-end system, or line of business application to which you are connecting using Enterprise Single Sign-On.</span></span> <span data-ttu-id="a6dee-110">每個分支機構應用程式都有多個使用者對應；例如，它在 Active Directory 中使用者的認證與對應的 RACF 憑證之間具有對應。</span><span class="sxs-lookup"><span data-stu-id="a6dee-110">Each affiliate application has multiple user mappings; for example, it has the mappings between the credentials for a user in Active Directory and their corresponding RACF credentials.</span></span>  
  
 <span data-ttu-id="a6dee-111">SSO 資料庫是儲存分支機構應用程式相關資訊的 SQL Server 資料庫，另外也儲存了所有分支機構應用程式的所有已加密使用者認證。</span><span class="sxs-lookup"><span data-stu-id="a6dee-111">The SSO database is the SQL Server database that stores the information about the affiliate applications, as well as all of the encrypted user credentials to all the affiliate applications.</span></span>  
  
 <span data-ttu-id="a6dee-112">*主要密碼伺服器*是儲存主要密碼的企業單一登入伺服器。</span><span class="sxs-lookup"><span data-stu-id="a6dee-112">The *master secret server* is the Enterprise Single Sign-On server that stores the master secret.</span></span> <span data-ttu-id="a6dee-113">系統中所有其他「單一登入」伺服器會從主要密碼伺服器取得主要密碼。</span><span class="sxs-lookup"><span data-stu-id="a6dee-113">All other Single Sign-On servers in the system get the master secret from the master secret server.</span></span>  
  
 <span data-ttu-id="a6dee-114">SSO 系統也含有一或多個 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a6dee-114">The SSO system also contains one or more SSO Servers.</span></span> <span data-ttu-id="a6dee-115">這些伺服器會進行 Microsoft Windows 及後端憑證的對應，以及查詢 SSO 資料庫中的憑證。</span><span class="sxs-lookup"><span data-stu-id="a6dee-115">These servers do the mapping between the Microsoft Windows and back-end credentials, and look up the credentials in the SSO database.</span></span> <span data-ttu-id="a6dee-116">系統管理員會使用它們來維護 SSO 系統。</span><span class="sxs-lookup"><span data-stu-id="a6dee-116">Administrators use them to maintain the SSO system.</span></span>  
  
 <span data-ttu-id="a6dee-117">更完整查詢在企業單一登入，請參閱[瞭解 SSO](../core/understanding-sso.md)。</span><span class="sxs-lookup"><span data-stu-id="a6dee-117">For more a complete look at Enterprise Single Sign-On, see [Understanding SSO](../core/understanding-sso.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6dee-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6dee-118">See Also</span></span>  
 [<span data-ttu-id="a6dee-119">執行階段架構</span><span class="sxs-lookup"><span data-stu-id="a6dee-119">Runtime Architecture</span></span>](../core/runtime-architecture.md)