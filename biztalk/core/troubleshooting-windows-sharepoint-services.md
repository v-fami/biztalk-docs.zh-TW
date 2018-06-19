---
title: 疑難排解 Windows SharePoint Services |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9acf9a0d-2c92-4227-80f8-b2d0cca0c232
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51243216f2adb73454477252c7b54358df229610
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286990"
---
# <a name="troubleshooting-windows-sharepoint-services"></a><span data-ttu-id="1a78b-102">Windows SharePoint Services 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="1a78b-102">Troubleshooting Windows SharePoint Services</span></span>
<span data-ttu-id="1a78b-103">Microsoft [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 是由 Windows SharePoint Services 配接器使用。</span><span class="sxs-lookup"><span data-stu-id="1a78b-103">Microsoft [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] is used by the Windows SharePoint Services adapter.</span></span> <span data-ttu-id="1a78b-104">本主題描述在使用 Windows SharePoint Services 時可能遇到的一些已知問題，以及這些問題的可能解決方法。</span><span class="sxs-lookup"><span data-stu-id="1a78b-104">This topic describes some known issues that may be encountered with Windows SharePoint Services and possible resolutions to these issues.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="1a78b-105">已知問題</span><span class="sxs-lookup"><span data-stu-id="1a78b-105">Known Issues</span></span>  
  
#### <a name="login-failed-for-user-nt-authoritynetwork-service-error-occurs-when-attempting-to-create-content-database"></a><span data-ttu-id="1a78b-106">當嘗試建立內容資料庫時，發生使用者 'NT AUTHORITY\NETWORK SERVICE' 的登入失敗錯誤</span><span class="sxs-lookup"><span data-stu-id="1a78b-106">Login failed for user 'NT AUTHORITY\NETWORK SERVICE' error occurs when attempting to create content database</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="1a78b-107">問題</span><span class="sxs-lookup"><span data-stu-id="1a78b-107">Problem</span></span>  
 <span data-ttu-id="1a78b-108">當您嘗試使用 SharePoint 管理中心網站建立內容資料庫時，會出現類似以下的錯誤：</span><span class="sxs-lookup"><span data-stu-id="1a78b-108">When you attempt to create a content database using the SharePoint Central Administration Web site, an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="1a78b-109">使用者 'NT AUTHORITY\NETWORK SERVICE' 的登入失敗</span><span class="sxs-lookup"><span data-stu-id="1a78b-109">Login failed for user 'NT AUTHORITY\NETWORK SERVICE'</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="1a78b-110">原因</span><span class="sxs-lookup"><span data-stu-id="1a78b-110">Cause</span></span>  
 <span data-ttu-id="1a78b-111">當您要連接之資料庫的資料庫擁有者與執行 Windows SharePoint Services 所用的應用程式集區身分識別不同時，就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="1a78b-111">This issue occurs when the database owner of the database that you are connecting to is different from the application pool identity that Windows SharePoint Services is running under.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="1a78b-112">解決方案</span><span class="sxs-lookup"><span data-stu-id="1a78b-112">Resolution</span></span>  
 <span data-ttu-id="1a78b-113">若要解決這個問題，請執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="1a78b-113">To resolve this issue, do one of the following:</span></span>  
  
-   <span data-ttu-id="1a78b-114">將 SQL Server 中的「資料庫建立」權限授與 NETWORK SERVICE 帳戶。</span><span class="sxs-lookup"><span data-stu-id="1a78b-114">Grant the NETWORK SERVICE account "Database Creation" rights in SQL Server.</span></span>  
  
-   <span data-ttu-id="1a78b-115">將應用程式集區身分識別帳戶變更為在 SQL Server 中具有「資料庫建立」權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="1a78b-115">Change the application pool identity account to an account that has "Database Creation" rights in SQL Server.</span></span>  
  
#### <a name="service-unavailable-error-occurs-when-accessing-the-sharepoint-central-administration-web-site"></a><span data-ttu-id="1a78b-116">當存取 SharePoint 管理中心網站時，發生服務無法使用錯誤</span><span class="sxs-lookup"><span data-stu-id="1a78b-116">"Service Unavailable" error occurs when accessing the SharePoint Central Administration Web site</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="1a78b-117">問題</span><span class="sxs-lookup"><span data-stu-id="1a78b-117">Problem</span></span>  
 <span data-ttu-id="1a78b-118">當您嘗試開啟 SharePoint 管理中心網站時，會出現類似以下的錯誤：</span><span class="sxs-lookup"><span data-stu-id="1a78b-118">When you attempt to open the SharePoint Central Administration Web site, an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="1a78b-119">服務無法使用</span><span class="sxs-lookup"><span data-stu-id="1a78b-119">Service Unavailable</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="1a78b-120">原因</span><span class="sxs-lookup"><span data-stu-id="1a78b-120">Cause</span></span>  
 <span data-ttu-id="1a78b-121">這個錯誤的最常見原因是 SharePoint 管理中心網站的應用程式集區 (IIS 6.0 或 IIS 7.0) 或裝載 COM+ 應用程式 (IIS 5.x) 停止運作。</span><span class="sxs-lookup"><span data-stu-id="1a78b-121">The most common cause for this error is that the application pool (IIS 6.0 or IIS 7.0) or hosting COM+ application (IIS 5.x) for the SharePoint Central Administration Web site is stopped.</span></span> <span data-ttu-id="1a78b-122">當使用了指定之使用者名稱及/或密碼無效的識別來設定應用程式集區或 COM+ 應用程式時，經常會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="1a78b-122">This commonly occurs if the application pool or COM+ application is configured with an identity for which the specified user name and/or password is invalid.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="1a78b-123">解決方案</span><span class="sxs-lookup"><span data-stu-id="1a78b-123">Resolution</span></span>  
 <span data-ttu-id="1a78b-124">請依照下列主題的 「 設定 IIS 應用程式主機處理序識別 」 一節中的步驟[解決 IIS 權限問題的指導方針](../core/guidelines-for-resolving-iis-permissions-problems.md)設定適當的主機處理序身分識別。</span><span class="sxs-lookup"><span data-stu-id="1a78b-124">Follow the steps in the "Setting IIS Application Host Process Identity" section of the topic [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md) to set the appropriate host process identity.</span></span>  
  
#### <a name="cannot-connect-to-the-configuration-database-error-occurs-when-attempting-to-extend-and-create-a-content-database"></a><span data-ttu-id="1a78b-125">當嘗試擴充及建立內容資料庫時，發生無法連線至設定資料庫錯誤</span><span class="sxs-lookup"><span data-stu-id="1a78b-125">"Cannot connect to the configuration database" error occurs when attempting to extend and create a content database</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="1a78b-126">問題</span><span class="sxs-lookup"><span data-stu-id="1a78b-126">Problem</span></span>  
 <span data-ttu-id="1a78b-127">當您嘗試使用 SharePoint 管理中心網站來擴充及建立內容資料庫時，會出現類似以下的錯誤：</span><span class="sxs-lookup"><span data-stu-id="1a78b-127">When you attempt to extend and create a content database using the SharePoint Central Administration Web site, an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="1a78b-128">無法連線至設定資料庫</span><span class="sxs-lookup"><span data-stu-id="1a78b-128">Cannot connect to the configuration database</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="1a78b-129">原因</span><span class="sxs-lookup"><span data-stu-id="1a78b-129">Cause</span></span>  
 <span data-ttu-id="1a78b-130">當執行 SharePoint 管理中心網站之應用程式集區所使用的帳戶沒有 SQL Server 資料庫的必要權限時，就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="1a78b-130">This issue occurs when the account that is used by the application pool that is running the SharePoint Central Administration Web site does not have the required permissions to the SQL Server database.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="1a78b-131">解決方案</span><span class="sxs-lookup"><span data-stu-id="1a78b-131">Resolution</span></span>  
 <span data-ttu-id="1a78b-132">若要解決這個問題，請執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="1a78b-132">To resolve this issue, do one of the following:</span></span>  
  
-   <span data-ttu-id="1a78b-133">將 SQL Server 中的「資料庫建立」權限授與 SharePoint 管理中心網站之應用程式集區所使用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="1a78b-133">Grant the account that is used by the application pool for the SharePoint Central Administration Web site "Database Creation" rights in SQL Server.</span></span>  
  
-   <span data-ttu-id="1a78b-134">將應用程式集區身分識別帳戶變更為在 SQL Server 中具有「資料庫建立」權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="1a78b-134">Change the application pool identity account to an account that has "Database Creation" rights in SQL Server.</span></span>  
  
#### <a name="the-sharepoint-timer-service-service-failed-to-start-error-is-generated-in-the-application-log-after-rebooting-server"></a><span data-ttu-id="1a78b-135">當伺服器重新啟動之後，在應用程式日誌中產生啟動 SharePoint Timer Service 服務已經失敗的錯誤</span><span class="sxs-lookup"><span data-stu-id="1a78b-135">"The SharePoint Timer Service service failed to start" error is generated in the Application log after rebooting server</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="1a78b-136">問題</span><span class="sxs-lookup"><span data-stu-id="1a78b-136">Problem</span></span>  
 <span data-ttu-id="1a78b-137">當重新啟動伺服器之後，您會在事件日誌中看到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="1a78b-137">After restarting the server, you see the following error in the event logs:</span></span>  
  
 <span data-ttu-id="1a78b-138">啟動 SharePoint Timer Service 服務已經失敗</span><span class="sxs-lookup"><span data-stu-id="1a78b-138">The SharePoint Timer Service service failed to start</span></span>  
  
 <span data-ttu-id="1a78b-139">當您開啟 SharePoint 管理中心網站時，可能也會看到以下錯誤：</span><span class="sxs-lookup"><span data-stu-id="1a78b-139">You may also see the following error when you open the SharePoint Central Administration site:</span></span>  
  
 <span data-ttu-id="1a78b-140">無法連線至 WSS 設定資料庫 STS_Config</span><span class="sxs-lookup"><span data-stu-id="1a78b-140">Unable to connect to the WSS configuration database STS_Config</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="1a78b-141">原因</span><span class="sxs-lookup"><span data-stu-id="1a78b-141">Cause</span></span>  
 <span data-ttu-id="1a78b-142">當 SharePoint Timer 服務在重新啟動之後無法連接 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 資料庫時，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="1a78b-142">This error occurs when the SharePoint Timer service fails to contact the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] database after rebooting.</span></span> <span data-ttu-id="1a78b-143">SharePoint Timer 服務是用來傳送通知及執行 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 的排程工作。</span><span class="sxs-lookup"><span data-stu-id="1a78b-143">The SharePoint Timer service is used to send notifications and perform scheduled tasks for [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span></span> <span data-ttu-id="1a78b-144">SharePoint Timer 服務無法啟動的最常見原因，就是用來執行此服務的帳戶使用了不再有效之使用者名稱及/或密碼的識別來加以設定。</span><span class="sxs-lookup"><span data-stu-id="1a78b-144">The most common reason that the SharePoint Timer service fails to start is that the account used to run the service is configured with an identity for which the user name and/or password are no longer valid.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="1a78b-145">解決方案</span><span class="sxs-lookup"><span data-stu-id="1a78b-145">Resolution</span></span>  
 <span data-ttu-id="1a78b-146">確定為 SharePoint Timer 服務登入帳戶所指定的使用者名稱及密碼正確無誤，而且此服務已經啟動。</span><span class="sxs-lookup"><span data-stu-id="1a78b-146">Ensure that the user name and password specified for the SharePoint Timer service logon account are correct and that the service has been started.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a78b-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a78b-147">See Also</span></span>  
 <span data-ttu-id="1a78b-148">[如何設定 Windows SharePoint Services 虛擬伺服器](http://support.microsoft.com/kb/832769) </span><span class="sxs-lookup"><span data-stu-id="1a78b-148">[How to configure a Windows SharePoint Services virtual server](http://support.microsoft.com/kb/832769) </span></span>  
 <span data-ttu-id="1a78b-149">[如何備份及還原 Windows SharePoint Services 使用 Microsoft SQL Server 2000 Desktop Engine (Windows) 的安裝](http://support.microsoft.com/kb/833797) </span><span class="sxs-lookup"><span data-stu-id="1a78b-149">[How to back up and restore installations of Windows SharePoint Services that use Microsoft SQL Server 2000 Desktop Engine (Windows)](http://support.microsoft.com/kb/833797) </span></span>  
 <span data-ttu-id="1a78b-150">[當您連接到您的 Windows SharePoint Services 網站上，收到 「 無法連接到組態資料庫 」 錯誤訊息](http://support.microsoft.com/kb/823287) </span><span class="sxs-lookup"><span data-stu-id="1a78b-150">[You receive a "Cannot connect to the configuration database" error message when you connect to your Windows SharePoint Services Web site](http://support.microsoft.com/kb/823287) </span></span>  
 <span data-ttu-id="1a78b-151">[當您瀏覽 Windows SharePoint Services 網站時，收到 「 服務無法使用 」 錯誤訊息](http://support.microsoft.com/kb/823552) </span><span class="sxs-lookup"><span data-stu-id="1a78b-151">[You Receive a "Service Unavailable" Error Message When You Browse a Windows SharePoint Services Web Site](http://support.microsoft.com/kb/823552) </span></span>  
 [<span data-ttu-id="1a78b-152">當您管理您的 Windows SharePoint Services 內容資料庫時，收到 「 資料庫 < 資料庫名稱 > 已經存在 」 錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="1a78b-152">You receive a "Database <Database_Name> already exists" error message when you manage your Windows SharePoint Services content database</span></span>](http://support.microsoft.com/kb/828815)