---
title: 檢查清單： 部署 BizTalk 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- checklists, deploying
- applications, deploying
- deploying [applications], checklists
- checklists, applications
- applications, checklists
ms.assetid: 0f936475-eea7-49b0-a4ea-9488b4ce3847
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c52644743a418a65abf3815f97a510b94773fca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009991"
---
# <a name="checklist-deploy-a-biztalk-application"></a>檢查清單： 部署 BizTalk 應用程式

|                                                                                                                                                                                                             步驟                                                                                                                                                                                                             |                                                                                                                                                                                          參考                                                                                                                                                                                          |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                                      瞭解 BizTalk 應用程式部署的各項功能。 您可能也要考慮如何使用繫結檔案，讓應用程式部署進行得更快速、更輕鬆。                                                                                                                      |                                                                           [了解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md)，[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)                                                                            |
|                                                                                                                                                                           確定您具有適當的權限可執行該部署。                                                                                                                                                                            |                                                                                                                  [部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)                                                                                                                  |
| 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，設定 BizTalk 方案中每個專案的部署屬性。 這些屬性包括群組的資料庫伺服器名稱和 BizTalk 管理資料庫的名稱，以及目的地 BizTalk 應用程式的名稱。 您也可以啟用重新部署，並指定選項，以便在重新部署時自動重新啟動主控件執行個體。 |                                                                                                                                      [如何在 Visual Studio 中設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)                                                                                                                                      |
|                                                                                                                                         從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 將 BizTalk 組件部署到目的地應用程式。                                                                                                                                          |                                                                                                                                    [如何部署 BizTalk 組件從 Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)                                                                                                                                    |
|                                                                               完成 BizTalk 應用程式 (例如，透過新增 .NET 組件、讀我檔案、環境特定繫結檔案和指令碼等)，並設定連接埠和接收位置。 此外，新增基礎結構 (例如，檔案放置位置) 至主控件電腦。                                                                               |                                                                                           [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)，[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)                                                                                            |
|                                                                                                                將 BizTalk 應用程式匯出至 .msi 檔案，您會使用這個檔案將應用程式匯入至另一個 BizTalk 群組，並將應用程式安裝到執行的電腦。                                                                                                                 |                                                                                                                                                    [如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)                                                                                                                                                    |
|                                                                                                      匯入 .msi 檔案，在目的地 BizTalk 群組中建立 BizTalk 應用程式。 如果您已經新增環境特定繫結檔案至應用程式，則可以選取要在匯入時套用的繫結。                                                                                                       |                                                                                                                                                    [如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)                                                                                                                                                    |
|                   對應用程式進行任何其他修改，以便在目的地環境中執行，例如變更連接埠組態。 如果您做了任何變更，請將應用程式匯出至 .msi 檔案，您會使用這個檔案，將應用程式安裝到執行的電腦。 您也可以將應用程式匯入至您要部署到的其他 BizTalk 群組中。                    | [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)，[如何將繫結檔案新增至應用程式](../core/how-to-add-a-binding-file-to-an-application2.md)，[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)，[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md) |
|                                                                                             使用 .msi 檔案，將應用程式安裝到將會執行它的所有電腦，然後從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台啟動該應用程式。                                                                                             |                                                                                                                                                   [如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)                                                                                                                                                   |

## <a name="see-also"></a>另請參閱  
 [BizTalk 應用程式部署和管理檢查清單](../core/biztalk-application-deployment-and-management-checklists.md)