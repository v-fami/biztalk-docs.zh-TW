---
title: 針對服務安裝 AppFabric 連接 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1de3bf49-e3cc-4d3f-9883-9a2c472f3647
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3d10862a6a60d173cc68c25d0dcc463d2f16e38
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298686"
---
# <a name="installing-appfabric-connect-for-services"></a>安裝 AppFabric 服務連線
本指南提供如何安裝 BizTalk Server 2010 Feature Pack (年 10 月 2010) 的指示。 功能套件提供的增強功能的服務功能的安裝 BizTalk Server 2010 AppFabric Connect **BizTalk WCF 服務發佈精靈**和**WCF 配接器服務開發精靈**. 您已安裝此功能套件之後，您可以在內部的範圍延伸為 BizTalk Server 成品或 LOB 應用程式至雲端的 Windows Azure AppFabric 服務匯流排端點加入。  
  
## <a name="prerequisites"></a>必要條件  
 BizTalk Server 2010 功能套件提供增強功能 BizTalk WCF 服務發佈精靈和 WCF 配接器服務開發精靈。 使用 BizTalk Server 2010 的開發人員工具，您可以使用 BizTalk WCF 服務發佈精靈時，WCF 配接器服務開發精靈是適用於 BizTalk Adapter Pack 2010。 因此，安裝此功能套件之前，您必須擁有 BizTalk Server 2010 的開發人員工具或 BizTalk Adapter Pack 2010 或兩者。 如果您有這些安裝的其中之一，只適用於父產品安裝精靈將會更新功能套件安裝的一部分。  
  
 此外，有一些使用這些精靈的必要條件。 每個精靈的必要條件的完整清單會列中的主題描述如何使用精靈。 主題的連結會提供下[使用 AppFabric Connect 服務](../technical-guides/installing-appfabric-connect-for-services.md#BKMK_Using)。  
  
## <a name="installing-biztalk-server-2010-feature-pack"></a>安裝 BizTalk Server 2010 功能套件  
 執行下列步驟來安裝 AppFabric Connect 服務：  
  
#### <a name="to-install-the-feature-pack"></a>若要安裝此功能套件  
  
1.  下載服務可從安裝 AppFabric Connect [http://go.microsoft.com/fwlink/?LinkId=204701](http://go.microsoft.com/fwlink/?LinkId=204701)。 執行自動解壓縮 BizTalkServer2010_FeaturePack.exe 檔案以啟動功能套件安裝程式。  
  
2.  在**歡迎**頁面上，按一下**下一步**。  
  
3.  接受授權條款，然後按**下一步**然後在下面的畫面中按一下**下一步**一次。  
  
4.  在精靈完成功能套件安裝之後，請按一下**完成**。  
  
##  <a name="BKMK_Using"></a>使用 AppFabric Connect 服務  
 在安裝之後 AppFabric Connect 服務，您可以執行下列作業：  
  
-   使用**BizTalk WCF 服務發佈精靈**公開為 WCF 服務與 Azure AppFabric 服務匯流排上的轉送端點的 BizTalk 成品 （協調流程、 結構描述等）。 如需詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=204700](http://go.microsoft.com/fwlink/?LinkId=204700)。  
  
-   使用**WCF 配接器服務開發精靈**公開為 WCF 服務與 Azure AppFabric 服務匯流排上的轉送端點的 LOB 應用程式上的作業。 如需詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=204699](http://go.microsoft.com/fwlink/?LinkId=204699)。  
  
## <a name="uninstalling-biztalk-server-2010-feature-pack"></a>解除安裝 BizTalk Server 2010 功能套件  
 本節提供解除安裝 AppFabric Connect 服務的指示。  
  
#### <a name="to-uninstall-the-feature-pack"></a>若要解除安裝此功能套件  
  
1.  開啟 Windows Update，再按**檢視更新記錄**，然後按一下 **已安裝的更新**。  
  
2.  從已安裝的更新清單下**BizTalk Server 2010**類別，以滑鼠右鍵按一下**BizTalk Server 2010 Feature Pack (年 10 月 2010) LDR**，然後選取**解除安裝**. 在 [確認您是否要解除安裝此功能套件] 對話方塊，按一下**是**。  
  
3.  重新整理清單，以確認是否要解除安裝此功能套件。  
  
## <a name="copyright"></a>著作權  
 本文件支援軟體產品的初稿版本，該軟體在發行最終商業版本之前可能會持續變更。  本文件僅供資訊之用途。在本文件中 Microsoft 不做任何明示或默示的擔保。  本文件中的資訊，包括 URL 及其他網際網路網站參考資料，如有變更恕不另行通知。  使用本文件所產生之全部風險及後果，均由使用者承擔。  除非另有說明，否則此處範例所描述之公司、組織、產品、網域名稱、電子郵件地址、商標、人員地點及事件均屬虛構，  並非影射任何真實的公司、組織、產品、網域名稱、電子郵件地址、商標、人員、地點或事件。  遵守所有適用之著作權法係使用者的責任。  在不限制任何依著作權本得享有之權利，未經 Microsoft Corporation 書面許可， 貴用戶不得為任何目的使用任何形式或方法 (電子形式、機械形式、影印、記錄或其他方式) 複製或傳送本文件的任何部份，也不得將本文件的任何部份儲存或放入檢索系統 (a retrieval system)。  
  
 在本文件所提述之內容中，可能包括 Microsoft 的專利、申請專利案件、商標、著作權，或其他智慧財產權等。  除非於 Microsoft 提出的任何書面授權條約中明確規定者外，提供本文件並不表示賦予台端上述專利、商標、著作權或其他智慧財產權等之任何授權。  
  
 © 2010 Microsoft Corporation。  著作權所有，並保留一切權利。  
  
 Microsoft, Active Directory, ActiveX, BizTalk, Excel, InfoPath, JScript, IntelliSense, Internet Explorer, MSDN, Outlook, PivotChart, PivotTable, PowerPoint, SharePoint, Tahoma, Visio, Visual Basic, Visual C++, Visual C#, Visual SourceSafe, Visual Studio, Win32, Windows, Windows NT, Windows PowerShell, Windows Server, Windows Server System 及 Windows Server 係 Microsoft 集團的商標。  
  
 本文件中所提 SAP、R/3、mySAP、mySAP.com、xApps、xApp、SAP NetWeaver 和其他 SAP 產品與服務以及各相關標誌係 SAP AG 在德國及/或其他許多國家/地區的商標或註冊商標。 此處提及的所有其他產品和服務名稱分別是其所屬公司的商標。 本文件包含的資料僅供參考。 不同國家/地區 的產品規格可能有所不同。  
  
 所有其他商標為各所有人所有之商標。