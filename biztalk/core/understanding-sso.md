---
title: 了解 SSO |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSO, about SSO
- Windows Integrated Single Sign-On
- Extranet Single Sign-On (Web SSO)
- Server-Based Intranet Single Sign-On
ms.assetid: 03f78a7b-4880-408f-9733-d07e19775d21
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 736fee720f2abf0dd051b1f754dd0fd6b8c42ab6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286982"
---
# <a name="understanding-sso"></a><span data-ttu-id="e1455-102">瞭解 SSO</span><span class="sxs-lookup"><span data-stu-id="e1455-102">Understanding SSO</span></span>
<span data-ttu-id="e1455-103">若要瞭解「企業單一登入」，看看今天提供的三種「單一登入」類型會有所幫助，即：Windows 整合、外部網路和內部網路。</span><span class="sxs-lookup"><span data-stu-id="e1455-103">To understand Enterprise Single Sign-On, it is useful to look at the three types of Single Sign-On services available today: Windows integrated, extranet, and intranet.</span></span> <span data-ttu-id="e1455-104">以下分別說明「企業單一登入」在這三類中的情形。</span><span class="sxs-lookup"><span data-stu-id="e1455-104">These are described below, with Enterprise Single Sign-On falling into the third category.</span></span>  
  
## <a name="windows-integrated-single-sign-on"></a><span data-ttu-id="e1455-105">Windows 整合的單一登入</span><span class="sxs-lookup"><span data-stu-id="e1455-105">Windows Integrated Single Sign-On</span></span>  
 <span data-ttu-id="e1455-106">這些服務可讓您在使用通用驗證機制的網路內連接多個應用程式。</span><span class="sxs-lookup"><span data-stu-id="e1455-106">These services enable you to connect to multiple applications within your network that use a common authentication mechanism.</span></span> <span data-ttu-id="e1455-107">在您登入網路後，這些服務會要求及驗證您的認證，並使用這些認證，依據您的使用者權限決定您可以執行的動作。</span><span class="sxs-lookup"><span data-stu-id="e1455-107">These services request and verify your credentials after you log into the network, and use your credentials to determine the actions that you can perform based on your user rights.</span></span> <span data-ttu-id="e1455-108">例如，若使用 Kerberos 整合應用程式，當系統驗證您的使用者認證後，您就可存取以 Kerberos 整合的網路中之任何資源。</span><span class="sxs-lookup"><span data-stu-id="e1455-108">For example, if applications integrate using Kerberos, after the system authenticates your user credentials you can access any resource in the network that is integrated with Kerberos.</span></span>  
  
## <a name="extranet-single-sign-on-web-sso"></a><span data-ttu-id="e1455-109">外部網路單一登入 (Web SSO)</span><span class="sxs-lookup"><span data-stu-id="e1455-109">Extranet Single Sign-On (Web SSO)</span></span>  
 <span data-ttu-id="e1455-110">這些服務可讓您只使用一組使用者認證在網際網路上存取資源。</span><span class="sxs-lookup"><span data-stu-id="e1455-110">These services enable you to access resources over the Internet by using a single set of user credentials.</span></span> <span data-ttu-id="e1455-111">使用者提供一組認證登入分屬不同公司的不同網站。</span><span class="sxs-lookup"><span data-stu-id="e1455-111">The user provides a set of credentials to log on to different Web sites that belong to different organizations.</span></span> <span data-ttu-id="e1455-112">這類「單一登入」的例子之一是以取用者為基礎之應用程式的 Windows Live ID。</span><span class="sxs-lookup"><span data-stu-id="e1455-112">An example of this type of Single Sign-On is Windows Live ID for consumer based applications.</span></span> <span data-ttu-id="e1455-113">至於聯合的實例，則為 Microsoft Active Directory Federation Services 啟用 Web SSO。</span><span class="sxs-lookup"><span data-stu-id="e1455-113">For federated scenarios, Microsoft Active Directory Federation Services enables Web SSO.</span></span>  
  
## <a name="server-based-intranet-single-sign-on"></a><span data-ttu-id="e1455-114">以伺服器為基礎的內部網路單一登入</span><span class="sxs-lookup"><span data-stu-id="e1455-114">Server-Based Intranet Single Sign-On</span></span>  
 <span data-ttu-id="e1455-115">這些服務可讓您整合企業環境內的多個異質應用程式和系統。</span><span class="sxs-lookup"><span data-stu-id="e1455-115">These services enable you to integrate multiple heterogeneous applications and systems within the enterprise environment.</span></span> <span data-ttu-id="e1455-116">這些應用程式及系統可能不是使用通用的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="e1455-116">These applications and systems may not use common authentication.</span></span> <span data-ttu-id="e1455-117">每個應用程式都有自己的使用者目錄存放區。</span><span class="sxs-lookup"><span data-stu-id="e1455-117">Each application has its own user directory store.</span></span> <span data-ttu-id="e1455-118">例如，在某家公司中，Windows 使用 Active Directory 目錄服務來驗證使用者，而大型主機則是使用 IBM 的 Resource Access Control Facility (RACF) 來驗證相同的使用者。</span><span class="sxs-lookup"><span data-stu-id="e1455-118">For example, in an organization, Windows uses Active Directory directory service to authenticate users, and mainframes use IBM's Resource Access Control Facility (RACF) to authenticate the same users.</span></span> <span data-ttu-id="e1455-119">在企業內，中介軟體應用程式會整合前端和後端應用程式。</span><span class="sxs-lookup"><span data-stu-id="e1455-119">Within the enterprise, middleware applications integrate the front-end and back-end applications.</span></span> <span data-ttu-id="e1455-120">「企業單一登入」讓企業中的使用者僅使用一組認證來連接前端與後端。</span><span class="sxs-lookup"><span data-stu-id="e1455-120">Enterprise Single Sign-On enables users in the enterprise to connect to both the front end and back end while using only one set of credentials.</span></span> <span data-ttu-id="e1455-121">這樣可讓「Windows 整合的單一登入」(其中初始要求是從 Windows 網域環境發出的) 以及「主控件初始的單一登入」(其中初始要求是從非 Windows 網域環境發出的) 都能存取 Windows 網域中的資源。</span><span class="sxs-lookup"><span data-stu-id="e1455-121">It enables both Windows Initiated Single Sign-On (in which the initial request is made from the Windows domain environment) and Host Initiated Single Sign-On (in which the initial request is made from a non-Windows domain environment) to access a resource in the Windows domain.</span></span>  
  
 <span data-ttu-id="e1455-122">此外，**密碼同步化**簡化 SSO 資料庫、 管理和密碼保持同步跨使用者目錄。</span><span class="sxs-lookup"><span data-stu-id="e1455-122">In addition, **Password Synchronization** simplifies administration of the SSO database, and keeps passwords in sync across user directories.</span></span> <span data-ttu-id="e1455-123">這個程序是使用密碼同步化配接器完成的，您可以使用「密碼同步」工具來設定及管理這些密碼。</span><span class="sxs-lookup"><span data-stu-id="e1455-123">This is done through the use of password synchronization adapters, which you can configure and manage using the Password Synchronization tools.</span></span>  
  
## <a name="the-enterprise-single-sign-on-system"></a><span data-ttu-id="e1455-124">企業單一登入系統</span><span class="sxs-lookup"><span data-stu-id="e1455-124">The Enterprise Single Sign-On System</span></span>  
 <span data-ttu-id="e1455-125">「企業單一登入」(SSO) 所提供的服務，可跨越本機與網路界限 (包含網域界限) 來儲存和傳輸加密的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="e1455-125">Enterprise Single Sign-On (SSO) provides services to store and transmit encrypted user credentials across local and network boundaries, including domain boundaries.</span></span> <span data-ttu-id="e1455-126">SSO 將認證儲存在 SSO 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="e1455-126">SSO stores the credentials in the SSO database.</span></span> <span data-ttu-id="e1455-127">因為 SSO 提供的是一般的單一登入解決方案，所以中介軟體應用程式和自訂配接器都能利用 SSO 安全地在整個環境內儲存及傳輸使用者認證。</span><span class="sxs-lookup"><span data-stu-id="e1455-127">Because SSO provides a generic single sign-on solution, middleware applications and custom adapters can leverage SSO to securely store and transmit user credentials across the environment.</span></span> <span data-ttu-id="e1455-128">一般使用者不用再記住各個應用程式的不同認證了。</span><span class="sxs-lookup"><span data-stu-id="e1455-128">End users do not have to remember different credentials for different applications.</span></span>  
  
 <span data-ttu-id="e1455-129">「單一登入」系統是由一個 SSO 資料庫、一個主要密碼伺服器，以及一或多個單一登入伺服器所組成。</span><span class="sxs-lookup"><span data-stu-id="e1455-129">The Single Sign-On system consists of an SSO database, a master secret server, and one or more Single Sign-On servers.</span></span>  
  
 <span data-ttu-id="e1455-130">SSO 系統包含了系統管理員所定義的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="e1455-130">The SSO system contains affiliate applications that an administrator defines.</span></span> <span data-ttu-id="e1455-131">分支機構應用程式是一個代表系統或子系統 (如主控件、後端系統或您使用「企業單一登入」連接的商務應用程式產品線) 的邏輯實體。</span><span class="sxs-lookup"><span data-stu-id="e1455-131">An affiliate application is a logical entity that represents a system or sub-system such as a host, back-end system, or line of business application to which you are connecting using Enterprise Single Sign-On.</span></span> <span data-ttu-id="e1455-132">每個分支機構應用程式都有多個使用者對應；例如，它在 Active Directory 中使用者的認證與對應的 RACF 憑證之間具有對應。</span><span class="sxs-lookup"><span data-stu-id="e1455-132">Each affiliate application has multiple user mappings; for example, it has the mappings between the credentials for a user in Active Directory and their corresponding RACF credentials.</span></span>  
  
 <span data-ttu-id="e1455-133">SSO 資料庫是儲存分支機構應用程式相關資訊的 SQL Server 資料庫，另外也儲存了所有分支機構應用程式的所有已加密使用者認證。</span><span class="sxs-lookup"><span data-stu-id="e1455-133">The SSO database is the SQL Server database that stores the information about the affiliate applications, as well as all the encrypted user credentials to all the affiliate applications.</span></span>  
  
 <span data-ttu-id="e1455-134">主要密碼伺服器是儲存主要密碼的「企業單一登入」伺服器。</span><span class="sxs-lookup"><span data-stu-id="e1455-134">The master secret server is the Enterprise Single Sign-On server that stores the master secret.</span></span> <span data-ttu-id="e1455-135">系統中所有其他「單一登入」伺服器會從主要密碼伺服器取得主要密碼。</span><span class="sxs-lookup"><span data-stu-id="e1455-135">All other Single Sign-On servers in the system get the master secret from the master secret server.</span></span>  
  
 <span data-ttu-id="e1455-136">SSO 系統也含有一或多個 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e1455-136">The SSO system also contains one or more SSO Servers.</span></span> <span data-ttu-id="e1455-137">這些伺服器會在 Windows 與後端認證間進行對應，在 SSO 資料庫中尋找認證，然後系統管理員會透過這些認證來維護 SSO 系統。</span><span class="sxs-lookup"><span data-stu-id="e1455-137">These servers do the mapping between the Windows and back-end credentials, look up the credentials in the SSO database, and administrators use them to maintain the SSO system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1455-138">您的 SSO 系統中只能有一個主要密碼伺服器及一個 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e1455-138">You can have only one master secret server and only one SSO database in your SSO system.</span></span> <span data-ttu-id="e1455-139">SSO 資料庫對主要密碼伺服器而言可以是遠端的。</span><span class="sxs-lookup"><span data-stu-id="e1455-139">The SSO database can be remote to the master secret server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1455-140">本節內容</span><span class="sxs-lookup"><span data-stu-id="e1455-140">In This Section</span></span>  
  
-   [<span data-ttu-id="e1455-141">SSO 使用者群組</span><span class="sxs-lookup"><span data-stu-id="e1455-141">SSO User Groups</span></span>](../core/sso-user-groups.md)  
  
-   [<span data-ttu-id="e1455-142">SSO 元件</span><span class="sxs-lookup"><span data-stu-id="e1455-142">SSO Components</span></span>](../core/sso-components.md)  
  
-   [<span data-ttu-id="e1455-143">SSO 伺服器</span><span class="sxs-lookup"><span data-stu-id="e1455-143">SSO Server</span></span>](../core/sso-server.md)  
  
-   [<span data-ttu-id="e1455-144">主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="e1455-144">Master Secret Server</span></span>](../core/master-secret-server.md)  
  
-   [<span data-ttu-id="e1455-145">SSO 分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="e1455-145">SSO Affiliate Applications</span></span>](../core/sso-affiliate-applications.md)  
  
-   [<span data-ttu-id="e1455-146">SSO 對應</span><span class="sxs-lookup"><span data-stu-id="e1455-146">SSO Mappings</span></span>](../core/sso-mappings.md)  
  
-   [<span data-ttu-id="e1455-147">SSO 票證</span><span class="sxs-lookup"><span data-stu-id="e1455-147">SSO Tickets</span></span>](../core/sso-tickets.md)  
  
-   [<span data-ttu-id="e1455-148">設定 SSO</span><span class="sxs-lookup"><span data-stu-id="e1455-148">Configuring SSO</span></span>](../core/configuring-sso.md)