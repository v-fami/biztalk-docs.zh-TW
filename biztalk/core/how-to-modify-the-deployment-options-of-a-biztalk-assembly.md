---
title: 如何修改 BizTalk 組件的部署選項 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- modifying, deploying
- managing [assemblies], modifying
- deploying, assemblies
- managing [assemblies], deploying
- assemblies, deploying
ms.assetid: d25e2f71-08bd-4786-ab6c-35ae4e88b8cc
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16ba9dc20893a2899f7fbed78aefb3d1a0bcfdb4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973583"
---
# <a name="how-to-modify-the-deployment-options-of-a-biztalk-assembly"></a>如何修改 BizTalk 組件的部署選項
本主題描述如何使用 BizTalk Server 管理主控台來修改 BizTalk 組件的部署選項。  
  
 您可以指定下列部署選項：  
  
-   **新增至全域組件快取新增資源 (gacutil) 上。** 如果選取此選項，將組件新增至應用程式時，便會將組件新增至本機電腦上的全域組件快取 (GAC) 中。 此外，如果您稍後重新整理之組件 (以滑鼠右鍵按一下它，然後按一下 **重新整理**)，組件加入至 GAC。 清除這個選項的核取方塊並不會從 GAC 移除該組件 (如果該組件目前在 GAC 中)。  
  
-   **新增至 MSI 檔案匯入 (gacutil) 的全域組件快取。** 在匯入應用程式 .msi 檔案時，將組件安裝到本機電腦的 GAC 中。  
  
-   **新增至 MSI 檔案安裝 (gacutil) 的全域組件快取。** 從 .msi 匯入應用程式時，將組件安裝到本機電腦的 GAC 中。  
  
-   **目的地位置：** 複製到其中的組件檔會在安裝應用程式的路徑。 如果沒有提供路徑，安裝時就不會將組件檔案複製到本機檔案系統。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 此外，如果您選取立即將組件新增至 GAC 的選項，您的帳戶也必須是本機「系統管理員」群組的成員。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-modify-the-deployment-options-of-a-biztalk-assembly"></a>若要修改 BizTalk 組件的部署選項  
  
1. 按一下 **開始**，按一下**程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，展開 [BizTalk Server 管理]，展開包含要為其修改部署選項的 BizTalk 組件的 BizTalk 群組，然後展開包含 BizTalk 組件的應用程式。  
  
3. 按一下 **資源**資料夾中，以滑鼠右鍵按一下 BizTalk 組件中，然後**修改**。  
  
4. 在 **選項**，選取您想要的部署選項的核取方塊。  
  
5. 必要時，在**目的地位置**編輯的路徑，其中的組件安裝應用程式時，將會複製，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk 組件](../core/managing-biztalk-assemblies.md)