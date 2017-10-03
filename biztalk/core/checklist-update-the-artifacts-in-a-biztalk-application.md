---
title: "檢查清單： 更新 BizTalk 應用程式中的成品 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, redeploying
- updating, applications
- redeploying
- checklists, applications
- updating, checklists
- updating
- applications, updating
- applications, redeploying
- applications, checklists
- checklists, redeploying
ms.assetid: 07ea4a2b-4ada-4d04-9eec-604b63b77415
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 321ef2c6c9bbd522c54f5d9352995788d8843455
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-update-the-artifacts-in-a-biztalk-application"></a>檢查清單： 更新 BizTalk 應用程式中的成品
如果您想要變更或更新已部署應用程式中的一或多個成品，然後重新部署該應用程式，請依照這份檢查清單中的步驟執行。  
  
|步驟|參考|  
|----------|---------------|  
|檢視更新應用程式內成品時的重要考量。|[更新應用程式的重要考量](../core/important-considerations-for-updating-applications.md)|  
|確定您具有適當的權限可執行該部署。|[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)|  
|對 Visual Studio 中的組件進行任何必要的變更。 如果您正在更新執行於實際執行環境的組件，您應該隨時遞增組件版本號碼。 如需背景資訊，請參閱[更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)。 然後，將組件從 Visual Studio 部署至開發環境中的 BizTalk 應用程式。|[如何部署 BizTalk 組件從 Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)|  
|測試任何新成品或已變更的成品，此外也務必測試任何可能相依於新成品或已變更成品的成品。 測試時，請務必要考慮可能存在於此應用程式與其他應用程式之間的相依性。|[BizTalk 應用程式部署的測試工作](../core/testing-tasks-for-biztalk-application-deployment.md)|  
|視需要在應用程式中新增、移除或重新設定成品。|[如何建立或新增成品](../core/how-to-create-or-add-an-artifact.md)，[如何從應用程式移除成品](../core/how-to-remove-an-artifact-from-an-application.md)，[管理成品](../core/managing-artifacts.md)|  
|將包含新成品或已變更成品的應用程式匯出至 .msi 檔案。 您可以匯出應用程式中的所有成品，或者只限於您想要加入或更新的成品。 請注意，檔案成品可能會被覆寫。 如果您匯出檔案成品，請確定它是您想要在應用程式中使用的版本。|[匯出 BizTalk 應用程式、 繫結和原則](../core/exporting-biztalk-applications-bindings-and-policies.md)|  
|如果更新會影響執行中的應用程式，請先停止您要更新的應用程式。 如果您是以新版本來更新組件，就不需要重新啟動應用程式。 **注意：**雖然不需要停止應用程式，才能更新成品或安裝應用程式，我們建議您一律停止應用程式，當您更新成品。|[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)|  
|將已變更的或更新的成品從 .msi 檔案匯入至要更新的應用程式。 請務必指定覆寫現有成品的選項。|[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)|  
|將已更新的應用程式或成品從 .msi 檔案安裝到執行該應用程式的所有電腦，以及任何執行相依於此應用程式之應用程式的電腦。 如果您是更新 BizTalk 組件，請檢查是否已在每台要執行該組件之電腦的全域組件快取 (GAC) 中安裝新版的組件。 如果尚未安裝，請在每一個 GAC 中安裝該組件。|[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)，[如何在 GAC 中安裝組件](../core/how-to-install-an-assembly-in-the-gac.md)|  
|啟動應用程式。|[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)|  
|在匯入包含協調流程的組件之後，如果您要匯入的目的應用程式已經包含具有相同名稱、公開金鑰 Token 與版本的組件，請停止再啟動協調流程所繫結之主控件的主控件執行個體。 這可以確保 BizTalk Server 會使用新版本的組件。|[如何停止主控件執行個體](../core/how-to-stop-a-host-instance.md)，[如何啟動主控件執行個體](../core/how-to-start-a-host-instance.md)|  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk 應用程式部署和管理檢查清單](../core/biztalk-application-deployment-and-management-checklists.md)   
 [更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)