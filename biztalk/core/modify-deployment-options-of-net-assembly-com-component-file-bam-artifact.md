---
title: 如何修改.NET 組件、 COM 元件、 檔案或 BAM 成品的部署選項 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [.NET assemblies], deploying
- deploying, virtual directories
- managing [applications], deploying
- managing [applications], modifying
- definition files [BAM], modifying
- modifying, artifacts
- deploying, artifacts
- managing [certificates], deploying
- deploying, .NET assemblies
- COM components, deploying
- definition files [BAM], deploying
- virtual directories, deploying
- deploying, certificates
- modifying, deployment options
- virtual directories, modifying
- deploying, COM components
ms.assetid: 4955d420-d9ff-4d5a-82f4-fb16477a828c
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 641e955a5eed0bb18df90b170daa6b87feba0876
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992007"
---
# <a name="how-to-modify-the-deployment-options-of-a-net-assembly-com-component-file-or-bam-artifact"></a>如何修改 .NET 組件、COM 組件、檔案或 BAM 成品的部署選項
本主題描述如何使用 [BizTalk Server 管理主控台] 來修改下列資源成品的部署選項：  
  
- .NET 組件  
  
- COM 元件  
  
- 臨機操作檔案  
  
- BAM 成品  
  
  您可能要修改部署屬性，將目的地位置變更為當應用程式在本機電腦上安裝時，便會將成品檔案複製到其中的位置。 如果沒有提供路徑，在安裝時就不會將檔案複製到本機電腦。  
  
  此外，您可能要修改 .NET 組件的下列選項：  
  
- **新增至全域組件快取新增資源 (gacutil) 上。** 如果選取此選項，將組件新增至應用程式時，便會將組件新增至本機電腦上的全域組件快取 (GAC) 中。 此外，如果您稍後重新整理之組件 (以滑鼠右鍵按一下它，然後按一下 **重新整理**)，組件加入至 GAC。 清除這個選項的核取方塊並不會從 GAC 移除該組件 (如果該組件目前在 GAC 中)。  
  
- **新增至 MSI 檔案匯入 (gacutil) 的全域組件快取。** 選取此選項時，如果應用程式是匯出至 .msi 檔案，而 .msi 檔案又會匯出至 BizTalk 群組中，則匯出程序會將組件安裝在本機電腦上的 GAC 中。  
  
- **新增至 MSI 檔案安裝 (gacutil) 的全域組件快取。** 選取此選項時，如果應用程式是匯出至 .msi 檔案，再由 .msi 檔案將應用程式安裝在電腦上，則安裝程序會將組件安裝在本機電腦上的 GAC 中。  
  
- **讓 COM 元件看見 (regasm)。** 選取此選項時，如果應用程式是匯出至 .msi 檔案，而且應用程式是從 .msi 檔案安裝到電腦中，便會做為安裝程序的一部分，而將 Managed COM 組件新增至本機電腦中的 Windows 登錄中。 如果您指定這個選項，也就必須在 [目的] 中指定檔案的位置。  
  
- **註冊已服務元件 (regsvcs)。** 當您選取此選項時，如果應用程式匯出至.msi 檔案，並從.msi 檔案的電腦上安裝應用程式時，受管理的 COM + 組件新增至 Windows 登錄在本機電腦安裝程序的一部分。 如果您指定這個選項，也就必須在 [目的] 中指定檔案的位置。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 此外，如果您選取立即將組件新增至 GAC 的選項，您的帳戶也必須是本機「系統管理員」群組的成員。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-modify-the-deployment-properties-of-a-resource-artifact"></a>若要修改資源成品的部署屬性  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，展開包含要為其修改部署選項之成品的 BizTalk 群組，然後再展開包含該成品的應用程式。  
  
3. 按一下 **資源**資料夾中，以滑鼠右鍵按一下成品，然後**修改**。  
  
4. 在 **選項**索引標籤上，視情況下，需要修改部署選項，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [管理 .NET 組件、憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md)