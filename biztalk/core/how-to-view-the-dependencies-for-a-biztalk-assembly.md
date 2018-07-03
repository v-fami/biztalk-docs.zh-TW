---
title: 如何檢視 BizTalk 組件的相依性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- viewing, dependencies
- assemblies, dependencies
- managing [assemblies], dependencies
- assemblies, viewing
- viewing, assemblies
- managing [assemblies], viewing
ms.assetid: 872abc99-8248-4397-9fcb-24a0ba6f4757
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b02a773ff51c35de2505336137dfa6c4c11c0825
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001215"
---
# <a name="how-to-view-the-dependencies-for-a-biztalk-assembly"></a>如何檢視 BizTalk 組件的相依性
本主題描述如何使用「BizTalk Server 管理」主控台來檢視相依於 BizTalk 組件的成品清單。 如需相依性，以及它們如何影響應用程式部署的背景資訊，請參閱[相依性和應用程式部署](../core/dependencies-and-application-deployment.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組或「BizTalk 操作員」群組的成員帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-view-the-dependencies-of-a-biztalk-assembly"></a>檢視 BizTalk 組件的相依性  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 展開包含您要檢視相依性的 BizTalk 組件的 BizTalk 群組，然後再展開 包含的 BizTalk 組件的應用程式。  
  
3. 按一下 **資源**資料夾中，以滑鼠右鍵按一下 BizTalk 組件中，然後**修改**。  
  
4. 按一下 [**相依性**] 索引標籤。  
  
    此清單中顯示相依於此 BizTalk 組件之成品的名稱和狀態。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk 組件](../core/managing-biztalk-assemblies.md)