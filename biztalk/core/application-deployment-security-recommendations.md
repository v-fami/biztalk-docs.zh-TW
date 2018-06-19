---
title: 應用程式部署的安全性建議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, applications
- best practices, applications
- best practices, security
- security, best practices
- applications, best practices
- applications, security
ms.assetid: 77902140-8b4c-437c-af4c-10a12b3bc950
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a0402ef23de70150d541dfd672d2af7efe3a924
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231950"
---
# <a name="application-deployment-security-recommendations"></a>應用程式部署的安全性建議
以下是將 BizTalk 應用程式部署在環境中的指導方針：  
  
-   當應用程式匯出至 .msi 檔案時，所有的判別存取控制清單 (DACL) 都會從檔案和資料夾中移除。 從 .msi 檔案安裝應用程式之後，您必須重新設定檔案和資料夾的所有安全性設定。  
  
-   基於安全性理由，當您匯出繫結檔案時，BizTalk Server 會從該檔案移除繫結的密碼。 匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。 您可以在 BizTalk Server 管理主控台的 [傳輸屬性] 對話方塊中，為傳送埠或接收位置設定密碼。 如需指示，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 另請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。 如需繫結檔案的詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
-   部署或解除部署屬性結構描述可能會公開機密資料，而之後可能會在追蹤期間公開機密資訊。 每當部署或解除部署包含屬性結構描述的組件時，事件檢視器會將事件記錄在 Windows 應用程式事件記錄中。 您應檢查事件日誌檔中的這些訊息，確保所有組件部署活動都符合任何機密資料的原則  
  
     在「事件日誌」中產生的部署訊息為：  
  
     **使用者"{1} 」 部署的組件"{0}"包含屬性結構描述。**  
  
     對解除部署之事件記錄產生的訊息為：  
  
     **使用者"{1}"已解除部署組件"{0}"包含屬性結構描述。**  
  
-   如果應用程式包含虛擬目錄，請注意虛擬目錄上的安全性設定，就是在應用程式匯出期間產生 .msi 檔案時生效的那些安全性設定。 如果您將應用程式部署到實際執行環境，則在匯出應用程式之前，應該驗證設定是否符合安全性需求。  
  
     如果您部署包含虛擬目錄的應用程式，而且目的地環境中已經有虛擬目錄存在，則現有虛擬目錄上的安全性設定將會生效。 這些設定不會為了要與您部署之虛擬目錄上的設定相符而變更。 您應該確認現有虛擬目錄的安全性設定是否符合安全性需求。  
  
    > [!CAUTION]
    >  如果虛擬目錄使用的是 HTTPS (超文字安全傳輸通訊協定) 通訊協定，則在匯出期間不會保留其安全性設定，而且在匯入時，虛擬目錄會繼承根目錄的安全性設定。 您應該驗證這些安全性設定是否符合您的需求。  
  
-   如果在匯入應用程式時為 Web 服務指定的應用程式集區不存在，則會使用預設的應用程式集區。 預設應用程式集區的安全性設定可能不適合您的安全性需求。 因此，建議您在匯入應用程式之前，先建立應用程式集區並設定適當的安全性設定，或驗證預設應用程式集區的安全性設定是否適當。  
  
-   確定您信任所部署 Windows Installer (.msi) 檔案的來源，以避免可能由惡意的 .msi 檔案建立者造成的安全性問題。 如需詳細資訊，請參閱[安全性和 Windows Installer](../core/security-and-windows-installer.md)。  
  
-   確定您具有部署應用程式的權限。 如需詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
-   確定只有 BizTalk 系統管理員才能存取組件、繫結檔案和原則檔案，因為它們可能包含重要的商務資料，例如連線和組態資訊。 如果您透過網路共用部署應用程式，請對網路共用設定判別存取控制清單 (DACL)，如此只有 BizTalk 系統管理員才能檢視其內容。 如需群組和使用者帳戶的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。  
  
-   當您執行部署作業時，BizTalk Server 會與 BizTalk 管理資料庫通訊。 如果它們之間有防火牆存在，您必須在處理、服務和資料網域之間的防火牆開啟適當的連接埠。 如需詳細資訊，請參閱[所需的 BizTalk Server 的連接埠](../core/required-ports-for-biztalk-server.md)。  
  
-   如果您指向可能包含機密資料之組件、繫結檔案或其他資源檔案的遠端位置，應該考慮來源電腦和執行部署的電腦之間的網路安全性。 如果這兩台電腦之間的網路未完全隔絕潛在攻擊者，您應該將目標檔案複製到卸除式媒體，再將它從卸除式媒體複製到執行部署的電腦上。  
  
## <a name="see-also"></a>另請參閱  
 [應用程式部署的安全性考量](../core/security-considerations-for-application-deployment.md)