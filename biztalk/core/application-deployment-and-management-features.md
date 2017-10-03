---
title: "應用程式部署和管理功能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new, Installation Wizard
- what's new, BTSTask command-line tool
- what's new, Import Wizard
- deploying, what's new
- what's new, Export Wizard
- what's new, deploying
- applications, what's new
- what's new, applications
ms.assetid: 2d09d6b1-1003-406f-81da-14e21a1cbc81
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e0be112d97c5ef17c3d9d99fbb22ea59b17e482
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="application-deployment-and-management-features"></a>應用程式部署和管理功能
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包括可協助部署 BizTalk 商務解決方案的數項功能：  
  
-   **BizTalk 應用程式。** BizTalk 應用程式提供檢視和管理項目 (稱為「成品」) 的方式，這些成品組成 BizTalk 商務方案。 成品包含使商務方案運作的必要組件、協調流程、對應、結構描述、安全性憑證、商務規則原則、BAM 組態檔、繫結、指令碼等等。 您可以將成品新增到 BizTalk 應用程式，然後從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台內部，將應用程式成品的一切都當做單一實體，予以檢視、封裝、部署和管理。 您可以建立一個、兩個或多個 BizTalk 應用程式來管理商務方案中的成品。 您可以使用 [匯出精靈] 來匯出應用程式及其成品，然後再使用 [匯入精靈] 將 .msi 匯出到另一個 BizTalk 群組，以便在該處予以重新建立。 然後，您就能使用 [安裝精靈] 來安裝應用程式。 在本主題的稍後將會描述這些精靈。 在本文件中的每項部署程序，都有包含使用 [管理主控台] 的指示。 您也可以針對許多系統管理工作使用 BTSTask 命令列工具，而且本文件也包含使用 BTSTask 的程序。  
  
-   **匯入精靈。** 您使用匯入精靈，可從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，成品從.msi 檔案匯入到 BizTalk 應用程式。 如果指定的應用程式尚未存在，[匯入精靈] 便會建立該應用程式。 該精靈也會註冊成品，並將其存放在 BizTalk 管理資料庫的 .msi 檔案中。 如需使用匯入精靈匯入成品的詳細指示，請參閱[匯入 BizTalk 應用程式、 繫結和原則](../core/importing-biztalk-applications-bindings-and-policies.md)。  
  
-   **安裝精靈。** 您可以在 [匯入精靈] 的最後一個步驟中啟動 [安裝精靈]。 這個精靈會將應用程式安裝在本機電腦上，以便讓您能在本機電腦上執行應用程式。 如需指示，請參閱[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。 您也可以按兩下應用程式的 .msi 檔案以啟動 [匯入精靈]。 如需詳細資訊，請參閱[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)。  
  
-   **[匯出] 精靈。** 您也可以使用 [BizTalk Server 管理主控台] 所提供的 [匯出精靈]，從 BizTalk 應用程式產生 .msi 檔案。 然後，您就可以使用 [匯入精靈] 將 .msi 檔案匯入到不同的 BizTalk 群組中。 這樣讓您能夠輕鬆將資源新增到應用程式中，或是在新的 BizTalk 群組中自動建立應用程式。 如需有關使用 「 匯出精靈 」 的詳細資訊，請參閱[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。  
  
-   **BTSTask 命令列工具。** BTSTask 支援的應用程式部署功能[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，可讓您從命令列執行許多作業。 如需詳細資訊，請參閱[BTSTask 命令列參考](../core/btstask-command-line-reference.md)。  
  
 若要協助您熟悉這些應用程式部署功能，我們建議您執行中的步驟[逐步解說： 部署基本 BizTalk 應用程式](../core/walkthrough-deploying-a-basic-biztalk-application.md)。  
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md)