---
title: "附錄 b： 安裝 SharePoint 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f44c6e0a-dcce-4444-8cac-bd403c81a233
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d0766eabdad71546090b703e41a00f496629d83
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="appendix-b-install-the-microsoft-sharepoint-adapter"></a>附錄 B：安裝 Microsoft SharePoint 配接器
BizTalk Server 會包含 SharePoint 配接器可以接收訊息，或將訊息傳送至 SharePoint。 

[BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) 和 [BizTalk Server 2013 R2/2013](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) 的軟體需求會列出支援的 SharePoint 版本。

## <a name="sharepoint-adapter-in-biztalk-server-2016"></a>BizTalk Server 2016 中的 SharePoint 配接器

BizTalk Server 安裝程式會自動安裝 CSOM 可轉散發套件，就像 File 配接器、FTP 配接器以及其他非預設配接器一樣。 

SSOM 選項會予以移除，而且無法使用。


## <a name="sharepoint-adapter-in-biztalk-server-2013-and-r2"></a>BizTalk Server 2013 和 R2 中的 SharePoint 配接器
在 BizTalk Server 2013 R2 和 BizTalk Server 2013 中，有兩個 SharePoint 配接器的選項。

|SharePoint 物件模型|Description|  
|-------------------------|-----------------|  
|CSOM-SharePoint 配接器|**建議**。 BizTalk Server 安裝程式會自動安裝 CSOM 可轉散發套件，就像 File 配接器、FTP 配接器以及其他非預設配接器一樣。 <br/><br/>沒有 SharePoint 電腦的安裝需求。|  
|SSOM - SharePoint Web Service|**已取代**。 SharePoint 電腦上，執行 BizTalk Server 安裝程式和**只**選取 SharePoint 配接器。 這個安裝程式會安裝 IIS Web 服務，以處理與 BizTalk Server 上 SharePoint 配接器的通訊。 <br/><br/>在大部分的環境中，BizTalk Server 和 SharePoint 是在不同電腦上。|  

##  <a name="BKMK_Before"></a> 安裝之前  

*  SharePoint SSOM 和 CSOM 元件可以安裝 BizTalk Server 2013 R2 或 2013年和 SharePoint 安裝在同一部電腦上。  
  
* BAM 入口網站只能在 32 位元模式中執行。 如果 BAM 入口網站安裝在 64 位元電腦上，請確定已啟用 ASP.NET 2.0 32 位元，而且 IIS 應用程式集區處於 32 位元模式。 若要這樣做：  
  
    -   **ASP.NET**︰開啟 IIS 管理員中，並按一下 [BAM 入口網站] 網站，然後按兩下 [處理常式對應]。 在 [已啟用] 清單中，確認列出 [PageHandlerFactory-ISAPI-2.0]。  
  
    -   **應用程式集區**：開啟 IIS 管理員，並依序按一下 [應用程式集區]、[BAMAppPool] 和 [進階設定]。 在 **啟用 32 位元應用程式**, ，請選取 **True**。  
  
* 安裝 SharePoint 時，按一下**伺服器陣列**選項，即使當您建立單一伺服器的 BizTalk Server 和 SharePoint 安裝。 A**伺服器陣列**安裝可讓您設定 SharePoint 資料庫。  
* [CSOM: SharePoint Services 配接器](../core/csom-sharepoint-services-adapter.md)提供設定 SharePoint 接收位置和傳送埠的資訊。  
* BizTalk Server 2010 和舊版使用伺服器端物件模型 (SSOM) 連線到 SharePoint 2010。 

## <a name="csom-and-ssom-supported-versions"></a>CSOM 和 SSOM 支援的版本  
SharePoint 支援下表中列出：  
  
||支援 CSOM|支援 SSOM|  
|---|---|---|  
|SharePoint 2016|是|否|  
|SharePoint 2013|是|否|  
|SharePoint Online|是|否|  
|SharePoint 2010|是|是|  
|SharePoint 2007 |否|是|  
  
##  <a name="BKMK_CSOM"></a> 安裝 CSOM SharePoint 配接器  
  
1.  根據下列需求來使用 SharePoint 電腦︰  
  
    ||CSOM 支援|  
    |---|---|  
    |SharePoint 2016<br /><br /> [安裝 SharePoint 2016](https://technet.microsoft.com/library/cc262957(v=office.16).aspx)|是|  
    |SharePoint 2013<br /><br /> [安裝 SharePoint 2013](https://technet.microsoft.com/library/cc262957.aspx)|是|  
    |SharePoint Online<br /><br /> [SharePoint Online 管理](https://technet.microsoft.com/library/gg132908.aspx)|是|  
    |SharePoint 2010<br /><br /> [SharePoint Server 2010 的安裝和部署](https://technet.microsoft.com/library/cc262957(v=office.14).aspx)|是|  
    |SharePoint 2007 |否|  
  
2.  在 BizTalk 伺服器上，安裝 Windows Identity Foundation:  
  
    | 作業系統 | 資訊 |  
    |---|---|  
    |Windows 10、 Windows 8.1、 Windows Server 2016、 Windows Server 2012 和 Windows Server 2012 R2|Windows Identity Foundation 隨附於作業系統的 [開啟或關閉 Windows 功能] 功能之一。|  
    |Windows Vista SP1|可在 [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331) 下載。|  
  
3.  安裝 BizTalk Server:

    | |  |  
    |---|---|  
     | BizTalk Server 2016 | 執行 BizTalk 安裝程式。 |
    | BizTalk Server 2013 R2 | 執行 BizTalk 安裝程式，並**未**核取 [Windows SharePoint Services 配接器]。 |  
    | BizTalk Server 2013 | 執行 BizTalk 安裝程式，並**未**核取 [Windows SharePoint Services 配接器]。 |
  
##  <a name="BKMK_SSOM"></a> 安裝 SSOM SharePoint 配接器 (已取代)  
  
1.  使用下列 SSOM 需求為基礎的 SharePoint 電腦：  
  
    ||SSOM 支援|  
    |---|---|  
    |SharePoint 2016<br /><br /> [安裝 SharePoint 2016](https://technet.microsoft.com/library/cc262957(v=office.16).aspx)|否| 
    |SharePoint 2013<br /><br /> [安裝 SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)|否|  
    |SharePoint Online<br /><br /> [SharePoint Online 管理](https://technet.microsoft.com/library/gg132908.aspx)|否|  
    |SharePoint 2010<br /><br /> [SharePoint Server 2010 的安裝和部署](https://technet.microsoft.com/library/cc262957(v=office.14).aspx)|是|  
    |SharePoint 2007<br /><br /> [SharePoint Server 2007 的安裝](https://technet.microsoft.com/library/cc262957(v=office.12).aspx) |是|  
  
2.  SharePoint 電腦上，設定 SharePoint，及擴充預設的網站。 當您擴充網站時，會建立包含相同內容的個別 IIS 網站，同時提供一個唯一 URL 和驗證類型。  
  
     請參閱 [SharePoint 2010：擴充 Web 應用程式](http://go.microsoft.com/fwlink/p/?LinkId=259124)。  
  
3.  SharePoint 電腦上，執行 BizTalk Server 安裝和**只**檢查**Windows SharePoint Services 配接器**。 這會安裝 Web 服務。 **請不要執行 BizTalk 組態**。  
  
4.  在 BizTalk 伺服器上，安裝 BizTalk Server。 請**不**要核取 [Windows SharePoint Services 配接器]。  
  
5.  SharePoint Web 服務 (SSOM) 只會在 64 位元模式下執行。 SharePoint 電腦上的 ASP.NET 和 IIS 應用程式集區必須處於 64 位元模式，才能安裝 SharePoint。 若要這樣做：  
  
    -   **ASP.NET**︰開啟 IIS 管理員中，並按一下網站，然後按兩下 [處理常式對應]。 在 [已啟用] 清單中，確認列出 [PageHandlerFactory-ISAPI-2.0-64]。  
  
    -   **應用程式集區**：開啟 IIS 管理員，並按一下 [應用程式集區]，再選取應用程式集區，然後按一下 [進階設定]。 在 [啟用 32 位元應用程式] 中，選取 [False]。  

