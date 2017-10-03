---
title: "何謂 Windows SharePoint Services 配接器？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, process flow
- Windows SharePoint Services adapters, receiving documents
- Windows SharePoint Services adapters, sending documents
- Windows SharePoint Services adapters, security
- Windows SharePoint Services adapters
- Windows SharePoint Services adapters, about Windows SharePoint Services adapters
ms.assetid: 1875ac85-46c2-4da5-ad16-8b078cb4cbd7
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a25bc378bdbb4c8bef34c3cff0140d03094faad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-windows-sharepoint-services-adapter"></a>何謂 Windows SharePoint Services 配接器？
Windows SharePoint Services 的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 配接器與 Windows SharePoint Services 和 Microsoft Office InfoPath 有更緊密的整合。 以下主題說明功能以及 Windows SharePoint Services 配接器運作方式概觀。  
  
## <a name="features-of-the-windows-sharepoint-services-adapter"></a>Windows SharePoint Services 配接器的功能  
 以下清單描述 Windows SharePoint Services 配接器的重要功能：  
  
-   傳送 BizTalk Server XML 及二進位訊息至 SharePoint 文件庫的能力。  
  
-   整合 InfoPath： 您可以將自動從 Windows SharePoint Services 網站開啟時，InfoPath 中開啟的外寄 BizTalk Server XML 訊息轉換。  
  
-   進入 Windows SharePoint Services 以便進行訊息的屬性升級。 以有關類似訊息的協調流程個體 ID、訊息 ID，或是從訊息擷取值的 BizTalk Server 中繼資料，最多可更新 16 個 SharePoint 資料行。  
  
-   檔案名稱定義是以訊息內容和 BizTalk Server 屬性為基礎。  
  
-   文件傳送到任意清單的能力 (而不是文件庫): 在此情況下，文件本身不會儲存在 Windows SharePoint Services，但是屬性升級仍如常進行因此建立新的清單項目，並擷取資料行值從訊息中。  
  
-   從任何文件庫的任何檢視接收訊息，並將訊息封存至使用指定檔案名稱的指定文件庫之能力。  
  
-   升級 BizTalk Server 中的 Windows SharePoint Services 配接器屬性： Windows SharePoint Services 檔案資訊可在 BizTalk Server 訊息內容屬性。 從管線、 協調流程等等，可以存取訊息內容屬性。透過 WSS，就可以存取自訂 SharePoint 資料行。InPropertiesXml 文件。  
  
-   完整支援動態連接埠： 傳送配接器可以支援靜態 URI 繫結 （由使用者建立的傳送埠時） 或動態 URI 繫結 （由協調流程傳送訊息時）。 所有組態資訊可透過訊息內容屬性定義，例如，動態傳送埠以及實體傳送埠的 WSS.Filename 和 WSS.ConfigTimeout。  
  
-   效能計數器  
  
## <a name="how-the-windows-sharepoint-services-adapter-works"></a>Windows SharePoint Services 配接器的運作方式  
 Windows SharePoint Services 的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 配接器是由三個主要元件組成：  
  
-   Windows SharePoint Services 配接器 Web 服務  
  
-   Windows SharePoint Services 接收配接器  
  
-   Windows SharePoint Services 傳送配接器  
  
 安裝在 Windows SharePoint Services 伺服器的 Web 服務 (BTSharePointAdapterWS.asmx) 提供 Windows SharePoint Services 程式庫和清單的存取。 Web 服務公佈從 SharePoint 程式庫取得、加入、刪除及封存文件的方法。 接收配接器從 Web 服務擷取檔案，而傳送配接器則將檔案公佈至 Web 服務。  
  
 下圖顯示提供這些功能的 Windows SharePoint Services 的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 配接器的主要元件。  
  
 ![](../core/media/bts-dev-adapters-wss-architecture.gif "BTS_Dev_Adapters_WSS_Architecture")  
  
### <a name="receiving-documents-from-windows-sharepoint-services"></a>從 Windows SharePoint Services 接收文件  
 接收配接器輪詢 Windows SharePoint Services 文件庫檢視。 它呼叫使用 Windows SharePoint Services 物件模組，Windows SharePoint Services 伺服器上的 Web 方法，瀏覽程文件庫、取出檔案及傳回檔案資料至配接器。 接著配接器提交檔案至 BizTalk Server MessageBox，並從 Windows SharePoint Services 呼叫另一種 Web 方法刪除或封存檔案。 為能篩選 Windows SharePoint Services 程式庫的檔案，配接器會透過 Windows SharePoint Services 檢視輪詢 Windows SharePoint Services 程式庫。  
  
 集中式的 (輪詢) 方法提供簡單的管理模型，組態會在此模型的 BizTalk 伺服器上完成。 由於允許訊息批次的事實也能提供更好的效能。  
  
 由於 Windows SharePoint Services、Web 服務和 BizTalk Server 之間無法使用平台層級的交易支援，因此使用取出機制可以使失敗情況相關的錯誤降至最低。 在特定情況下 (就是檔案成功地傳入 BizTalk Server MessageBox 資料庫，但是無法從 Windows SharePoint Service 刪除)，雖然檔案已經提交至 BizTalk Server，但是 Windows SharePoint Services 伺服器上的檔案仍會維持取出的狀態。 錯誤會記錄至 BizTalk 伺服器的事件日誌。  
  
### <a name="sending-documents-to-windows-sharepoint-services"></a>傳送文件至 Windows SharePoint Services  
 配接器透過呼叫 Windows SharePoint Services 伺服器上的 Web 方法，傳送文件至 Windows SharePoint Services。 配接器指定 Windows SharePoint Services 網站 URL、文件庫、或相對於網站的清單 URL，或清單項目及升級屬性，與此檔案產生關聯。  
  
 您可以將檔案名稱設為固定的字串或自文件的 XML 資料衍生的名稱。 衍生名稱對於強制標準命名慣例有很大的幫助。 配接器也可將檔案的升級屬性值設為資料行值。 如同檔案名稱，升級屬性可以固定或從文件的 XML 資料衍生。  
  
> [!IMPORTANT]
>  Windows SharePoint Services 配接器的升級屬性實體與 BizTalk Server 或 Windows SharePoint Services 的升級屬性不同。  
  
 在瀏覽 Windows SharePoint Services 表單庫時，可使用 Windows SharePoint Services 升級屬性使 XML 項目可見。 InfoPath 表單發佈至 Windows SharePoint Services 表單庫時，InfoPath 設定表單庫升級重要項目使其自動發生。 此功能只能在使用 InfoPath 表單程式庫時 (以相同 XSD 結構性描述和 InfoPath 解決方案儲存 InfoPath 表單的文件庫)，由 Windows SharePoint Services 提供使用。  
  
 含有不同結構性描述的文件儲存在相同文件庫時，Windows SharePoint Services 配接器屬性升級可讓使用者將屬性升級至 Windows SharePoint Services。  
  
 BizTalk Server 屬性升級是一種類似的概念，只有做為訊息屬性並可見於協調流程的屬性，而不是可見於 UI 使用者的屬性。 此外，屬性值存回文件後，BizTalk Server 支援屬性降級概念。  
  
 在使用含有 InfoPath 表單和表單庫的 Windows SharePoint Services 配接器時 (而非任意 XML 和文件庫)，您不需要透過傳送埠設定升級屬性。 反而，此文件可在協調流程內變更 (直接透過變更訊息變更或是間接透過降級屬性變更)。 此值由 Windows SharePoint Services 自動升級。  
  
## <a name="security-considerations-for-the-windows-sharepoint-services-adapter"></a>Windows SharePoint Services 配接器的安全性考量  
 Windows SharePoint Services 配接器是由子系統，在 Windows SharePoint Services 網站上執行的 BTSharePointAdapterWS Web 服務，以及在 BizTalk Server 主控件執行個體程序內，BizTalk Server 上執行的配接器執行階段所組成。 配接器執行階段叫用 BTSharePointAdapterWS Web 服務，該服務必須在 Windows SharePoint Services 內有執行特定工作的權限。 因為此元件做為呼叫者執行，所以權限需授與呼叫者。 這表示 BizTalk 主控件執行個體必須進行**參與者**SharePoint 網站，才能傳送和接收訊息，從該站台上。 可以叫用 BTSharePointAdapterWS Web 服務的成員只能由**SharePoint 啟用的主控件**群組。 若要讓 BizTalk 主控件執行個體，執行配接器執行階段與 Web 服務互動，主控件執行個體的 Windows 帳戶必須進行的成員**SharePoint 啟用的主控件**群組。 它是加入和移除此群組也讓主控件執行個體的帳戶管理員的責任帳戶成員 SharePoint**參與者**角色。  
  
|元件|程序識別|權限|  
|---------------|----------------------|----------------|  
|BTSharePointAdapterWS Web 服務|呼叫者身份|叫用授與啟用 SharePoint 的主控件群組的權限|  
|配接器執行階段|BizTalk 主控件的身份|不適用|  
|Windows SharePoint Services 物件模型|不適用|SharePoint 啟用的主控件群組必須是成員**參與者**SharePoint Services 角色。|  
  
 BizTalk Server 安裝程式會設定 BTSharePointAdapterWS Web 服務上的權限，讓只有帳戶，屬於**SharePoint 啟用的主控件**群組可以存取此 Web 服務。 如果您想要執行的 Windows SharePoint Services 配接器的主機時，系統管理員就必須將該主機與相關聯的 NT 群組**SharePoint 啟用的主控件**群組，並將**SharePoint 啟用的主控件**群組至 Windows SharePoint Services**參與者**角色。  
  
 Windows SharePoint Services 檔案、清單和文件庫權限限制使用 Windows SharePoint Services 安全性。 此訊息是從 Windows SharePoint Services 直接傳送至 BizTalk Server。 配接器執行階段與 Web 服務之間的通訊是在 HTTP 或 HTTPS 上進行。  
  
 此配接器假設 BTSharePointAdapterWS Web 服務使用的 HTTP 配置 (HTTP 或 HTTPS) 與 Windows SharePoint Services 網站相同。 這表示 Windows SharePoint Services 網站在安全 IIS 網站建立時，配接器會使用 HTTPS 與 BTSSharePointAdapterWS Web 服務通訊，或者 Windows SharePoint Services 網站是在沒有伺服器憑證的情況下在 IIS 網站建立時，配接器會使用 HTTP 與 BTSharePointAdapterWS Web 服務通訊。  
  
## <a name="see-also"></a>另請參閱  
 [設定和部署 Windows SharePoint Services 配接器](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md)   
 [設定 Windows SharePoint Services 配接器](../core/configuring-the-windows-sharepoint-services-adapter.md)   
 [Windows SharePoint Services 配接器逐步解說](../core/windows-sharepoint-services-adapter-walkthroughs.md)