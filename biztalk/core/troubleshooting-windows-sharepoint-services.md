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
# <a name="troubleshooting-windows-sharepoint-services"></a>Windows SharePoint Services 配接器疑難排解
Microsoft [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 是由 Windows SharePoint Services 配接器使用。 本主題描述在使用 Windows SharePoint Services 時可能遇到的一些已知問題，以及這些問題的可能解決方法。  
  
## <a name="known-issues"></a>已知問題  
  
#### <a name="login-failed-for-user-nt-authoritynetwork-service-error-occurs-when-attempting-to-create-content-database"></a>當嘗試建立內容資料庫時，發生使用者 'NT AUTHORITY\NETWORK SERVICE' 的登入失敗錯誤  
  
##### <a name="problem"></a>問題  
 當您嘗試使用 SharePoint 管理中心網站建立內容資料庫時，會出現類似以下的錯誤：  
  
 使用者 'NT AUTHORITY\NETWORK SERVICE' 的登入失敗  
  
##### <a name="cause"></a>原因  
 當您要連接之資料庫的資料庫擁有者與執行 Windows SharePoint Services 所用的應用程式集區身分識別不同時，就會發生這個問題。  
  
##### <a name="resolution"></a>解決方案  
 若要解決這個問題，請執行下列其中一個動作：  
  
-   將 SQL Server 中的「資料庫建立」權限授與 NETWORK SERVICE 帳戶。  
  
-   將應用程式集區身分識別帳戶變更為在 SQL Server 中具有「資料庫建立」權限的帳戶。  
  
#### <a name="service-unavailable-error-occurs-when-accessing-the-sharepoint-central-administration-web-site"></a>當存取 SharePoint 管理中心網站時，發生服務無法使用錯誤  
  
##### <a name="problem"></a>問題  
 當您嘗試開啟 SharePoint 管理中心網站時，會出現類似以下的錯誤：  
  
 服務無法使用  
  
##### <a name="cause"></a>原因  
 這個錯誤的最常見原因是 SharePoint 管理中心網站的應用程式集區 (IIS 6.0 或 IIS 7.0) 或裝載 COM+ 應用程式 (IIS 5.x) 停止運作。 當使用了指定之使用者名稱及/或密碼無效的識別來設定應用程式集區或 COM+ 應用程式時，經常會發生這個錯誤。  
  
##### <a name="resolution"></a>解決方案  
 請依照下列主題的 「 設定 IIS 應用程式主機處理序識別 」 一節中的步驟[解決 IIS 權限問題的指導方針](../core/guidelines-for-resolving-iis-permissions-problems.md)設定適當的主機處理序身分識別。  
  
#### <a name="cannot-connect-to-the-configuration-database-error-occurs-when-attempting-to-extend-and-create-a-content-database"></a>當嘗試擴充及建立內容資料庫時，發生無法連線至設定資料庫錯誤  
  
##### <a name="problem"></a>問題  
 當您嘗試使用 SharePoint 管理中心網站來擴充及建立內容資料庫時，會出現類似以下的錯誤：  
  
 無法連線至設定資料庫  
  
##### <a name="cause"></a>原因  
 當執行 SharePoint 管理中心網站之應用程式集區所使用的帳戶沒有 SQL Server 資料庫的必要權限時，就會發生這個問題。  
  
##### <a name="resolution"></a>解決方案  
 若要解決這個問題，請執行下列其中一個動作：  
  
-   將 SQL Server 中的「資料庫建立」權限授與 SharePoint 管理中心網站之應用程式集區所使用的帳戶。  
  
-   將應用程式集區身分識別帳戶變更為在 SQL Server 中具有「資料庫建立」權限的帳戶。  
  
#### <a name="the-sharepoint-timer-service-service-failed-to-start-error-is-generated-in-the-application-log-after-rebooting-server"></a>當伺服器重新啟動之後，在應用程式日誌中產生啟動 SharePoint Timer Service 服務已經失敗的錯誤  
  
##### <a name="problem"></a>問題  
 當重新啟動伺服器之後，您會在事件日誌中看到下列錯誤：  
  
 啟動 SharePoint Timer Service 服務已經失敗  
  
 當您開啟 SharePoint 管理中心網站時，可能也會看到以下錯誤：  
  
 無法連線至 WSS 設定資料庫 STS_Config  
  
##### <a name="cause"></a>原因  
 當 SharePoint Timer 服務在重新啟動之後無法連接 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 資料庫時，就會發生這個錯誤。 SharePoint Timer 服務是用來傳送通知及執行 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 的排程工作。 SharePoint Timer 服務無法啟動的最常見原因，就是用來執行此服務的帳戶使用了不再有效之使用者名稱及/或密碼的識別來加以設定。  
  
##### <a name="resolution"></a>解決方案  
 確定為 SharePoint Timer 服務登入帳戶所指定的使用者名稱及密碼正確無誤，而且此服務已經啟動。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 Windows SharePoint Services 虛擬伺服器](http://support.microsoft.com/kb/832769)   
 [如何備份及還原 Windows SharePoint Services 使用 Microsoft SQL Server 2000 Desktop Engine (Windows) 的安裝](http://support.microsoft.com/kb/833797)   
 [當您連接到您的 Windows SharePoint Services 網站上，收到 「 無法連接到組態資料庫 」 錯誤訊息](http://support.microsoft.com/kb/823287)   
 [當您瀏覽 Windows SharePoint Services 網站時，收到 「 服務無法使用 」 錯誤訊息](http://support.microsoft.com/kb/823552)   
 [當您管理您的 Windows SharePoint Services 內容資料庫時，收到 「 資料庫 < 資料庫名稱 > 已經存在 」 錯誤訊息](http://support.microsoft.com/kb/828815)