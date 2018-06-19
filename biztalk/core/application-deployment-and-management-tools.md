---
title: 應用程式部署和管理工具 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de85b52b-7eb7-4cf1-b8b4-41f7488b4d2f
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3dede31c82d79ac6c40ae087dfffb7f30c2402c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232190"
---
# <a name="application-deployment-and-management-tools"></a>應用程式部署和管理工具

## <a name="overview"></a>概觀
本主題簡要描述可用來部署及管理 BizTalk 應用程式的工具，然後摘要敘述每項工具所能執行的作業。 本主題結尾的表格摘要說明您可以使用執行的工作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台和 BTSTask。  
  
-   **BizTalk Server 管理主控台。** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，Microsoft Management Console (MMC)，是的主要管理工具[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 它提供圖形使用者介面，用以執行 BizTalk 應用程式的所有部署及管理作業。 例如，您可以從管理主控台啟動匯入、安裝和匯入精靈，以及新增和移除應用程式的成品，並對應用程式做其他修改。  
  
     也可以使用匯出 MSI 檔案精靈或 BTSTask (如下所述)，針對 BizTalk 應用程式產生 BizTalk .msi 檔案。 接下來可以從這個 .msi 檔案將應用程式安裝在電腦上，或從這個 .msi 檔案將應用程式匯入至另一個 BizTalk 群組。 如需管理主控台的詳細資訊，請參閱[使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)。  
  
-   **BTSTask 命令列工具。** BTSTask 可讓您從命令列執行許多應用程式管理工作。 如需有關如何使用 BTSTask 的詳細資訊，請參閱[BTSTask 命令列參考](../core/btstask-command-line-reference.md)。  
  
-   **指令碼和程式設計 Api**。 您可以使用 Microsoft Windows Management Instrumentation (WMI)，建立和執行可自動化許多應用程式管理工作的指令碼。 如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
-   **Visual Studio。** 開發人員可以建立 BizTalk 組件中的[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]並使用 [部署] 命令將會自動將它們部署到 BizTalk 應用程式。 如需詳細資訊，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。  
  
     執行個體時提供 SQL Server 登入。  
  
    > [!IMPORTANT]
    >  您絕對不要部署的組件[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]實際執行電腦上執行。 這可能會中斷正在執行的應用程式。 如需詳細資訊，請參閱[部署 BizTalk 應用程式的最佳作法](../core/best-practices-for-deploying-a-biztalk-application.md)。  

## <a name="tool-by-the-task"></a>工作的工具  
 下表摘要敘述可以使用管理主控台和 BTSTask 所執行的工作。  
  
|工作|工具|  
|----------|----------|  
|匯出應用程式 .msi 檔案|-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台 <br/>– 匯出 MSI 檔案精靈<br />-BTSTask|  
|匯入應用程式 .msi 檔案|-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台 <br/>– 匯入 MSI 精靈<br />-BTSTask|  
|建立或刪除應用程式|-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台<br />-BTSTask|  
|安裝應用程式|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台 <br/>– 安裝精靈 （或按兩下應用程式.msi 檔案）|  
|解除安裝應用程式|BTSTask (或使用 [控制台] 中的 [新增或移除程式])|  
|將成品新增至應用程式或從應用程式移除成品|-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台<br />-BTSTask|  
|匯入及匯出繫結和繫結檔案|-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台<br />-BTSTask|  
|匯入及匯出原則|-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台<br />-BTSTask|  
|啟動和停止應用程式|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台|  
|變更成品的狀態： 啟動、 停止、 啟用、 停用、 登錄和取消登錄|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台|  
|編輯成品屬性|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台|  
|建立傳送埠、傳送埠群組、接收位置或接收埠|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台|  
  
## <a name="see-also"></a>另請參閱  
[系統管理] 和 [效能工具](../core/administration-tools.md)  
 [了解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md)