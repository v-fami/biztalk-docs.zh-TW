---
title: 應用程式部署程序 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications, deploying
- deploying [applications], how to
ms.assetid: 29486c37-6aa7-46fd-a457-916fd235f448
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd88dbb730b31362042e68b3a25c4ccc66531882
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279734"
---
# <a name="the-application-deployment-process"></a>應用程式部署程序
下列圖表描述部署 BizTalk 應用程式所牽涉到的一般步驟。 相關工作的開發、 測試、 預備及實際執行階段的應用程式部署相關的詳細資訊，請參閱[應用程式部署工作](../core/application-deployment-tasks.md)。  
  
 ![應用程式部署程序](../core/media/appdeploymentprocess.gif "AppDeploymentProcess")  
  
1.  **從 Visual Studio 部署 BizTalk 解決方案中的組件。** 這樣便會建立組件，並將組件連同協調流程、管線、結構描述，以及這些所包含的對應 (稱為「成品」) 匯入到本機 BizTalk 管理資料庫。 部署也會使組件與您在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 內專案屬性中所指定的 BizTalk 應用程式產生關聯。 如需指示，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。 在部署解決方案以後，您便能夠從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台內，或是使用 BTSTask 命令列工具，來檢視和管理已部署的組件及其成品。 您可以個別管理成品，或是將其做為應用程式內的群組一起管理。  
  
2.  **新增和設定成品。** 您可以使用管理主控台或 BTSTask 將成品 (例如指令碼和讀我檔案) 新增至應用程式。 您也可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來設定成品，例如傳送和接收連接埠、接收位置和協調流程。 如需詳細資訊，請參閱[如何建立或新增成品](../core/how-to-create-or-add-an-artifact.md)。 另請參閱[管理成品](../core/managing-artifacts.md)。 如果要對可能會在其中匯入應用程式的不同環境套用不同的繫結，您也可以產生繫結檔案，並將這些新增到應用程式中。 如需詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
3.  **匯出至.msi 檔案的應用程式。** 您可以使用 [匯出 MSI 檔案精靈] 或 BTSTask 將應用程式成品匯出至 .msi 檔案，該檔案可用來將應用程式匯入至新的 BizTalk 群組，並將應用程式安裝到將會予以執行的電腦。 如需指示，請參閱[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。  
  
4.  **應用程式匯入另一個 BizTalk 群組，並將執行它的電腦上安裝應用程式。** 您可以使用 [匯入 MSI 精靈] 或 BTSTask，將 BizTalk 應用程式從步驟 3 所建立的 .msi 檔案匯入至另一個 BizTalk 群組，以便在新群組中建立應用程式及其成品。 然後，您會使用 .msi 檔案將應用程式安裝在將會予以執行的電腦上。 您必須完成這個動作後，才能執行該應用程式。 如果已經準備好要測試應用程式，您就可以將應用程式匯入到測試環境中的 BizTalk 群組，並且加以安裝。 如果應用程式已經可以執行或實際執行，您便可以將其匯入到這些環境之一並予以安裝。 如需指示，請參閱[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。 另請參閱[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)。  
  
5.  **啟動應用程式，並確認正常。** 您可以開始將應用程式從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中所述[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。 然後就可以測試應用程式中所述[BizTalk 應用程式部署的測試工作](../core/testing-tasks-for-biztalk-application-deployment.md)。  
  
## <a name="see-also"></a>另請參閱  
 [了解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md)   
 [什麼是 BizTalk 應用程式？](../core/what-is-a-biztalk-application.md)