---
title: "實際執行工作，BizTalk 應用程式部署 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [applications], assemblies
- applications, deploying
- assemblies, warnings
- deploying [applications], warnings
- deploying [applications], tasks
- assemblies, deploying
- deploying [applications], production
ms.assetid: e77d8921-42ef-4c51-aab2-66c086aad955
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 260afd4522d28bdd2a485a1a11edc045c7fde880
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="production-tasks-for-biztalk-application-deployment"></a>BizTalk 應用程式部署的實際執行工作
以下是將 BizTalk 應用程式部署到實際執行環境所牽涉到的步驟。  
  
> [!IMPORTANT]
>  絕對不要從在實際執行電腦上的 Visual Studio 部署組件。 為了重新部署，Visual Studio 可能解除部署、解除繫結、停止及取消登錄存在於相同或不同應用程式中的組件。 雖然這在開發環境中是必要且適當的動作，但卻可能在實際執行環境中造成無法預期的嚴重後果。 此外，為了避免任何人嘗試在實際執行電腦上從 Visual Studio 部署組件的可能性，我們建議您不要在實際執行電腦上安裝 Visual Studio。  
  
> [!IMPORTANT]
>  在實際執行環境中更新其他應用程式相依的應用程式時請小心，不要使其他正在執行的應用程式中斷。 如需詳細資訊，請參閱[更新應用程式的重要考量](../core/important-considerations-for-updating-applications.md)。  
  
1.  **將.msi 檔案複製到您的生產環境。** 中所述[BizTalk 應用程式部署的測試工作](../core/testing-tasks-for-biztalk-application-deployment.md)，當的 BizTalk 應用程式已完成執行，且可供生產環境中，負責執行組態的 IT 系統管理員提供的.msi 檔用於生產環境部署。 您可以將此 .msi 檔案複製到實際執行電腦，然後如下一個步驟的描述，將 BizTalk 應用程式從 .msi 檔案複製到 BizTalk Server 中。 您同時也會使用 .msi 檔案，將應用程式安裝在將執行該應用程式的電腦上 (完整的 BizTalk 解決方案可能是由一或多個應用程式而組成，所以您可能會接到數個用於部署的 .msi 檔案)。  
  
2.  **從.msi 檔案，匯入應用程式。** 您可以使用 BizTalk Server 管理主控台提供的匯入精靈，在目前的 BizTalk Server 執行個體上將 .msi 檔案的內容匯入到應用程式。 如需詳細資訊，請參閱[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。 如果指定的應用程式尚未存在，則匯入 .msi 檔案便會建立該應用程式。 接著，您可以從管理主控台檢視該應用程式，並修改其組態和內容。 舉例而言，您可能需要進行這項作業，以設定憑證和端點 (例如 URL)，並且修改實際執行環境的繫結。 如需詳細資訊，請參閱[建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)。 如果已將具有適用於實際執行環境之正確繫結的繫結檔案新增至應用程式，則可以在匯入程序期間套用繫結。 如需詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
3.  **安裝並啟動應用程式。** 您現在可在將執行應用程式的所有電腦上安裝應用程式，並在管理主控台中啟動應用程式。 您可以按兩下 .msi 檔案來安裝應用程式。 如需詳細資訊，請參閱[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)。  
  
4.  **匯出繫結檔案，並將其加入回應用程式 （選擇性）。** 若要在稍後應用程式發生變更或新增項目時，以更輕鬆的方式將應用程式匯入回實際執行環境，可以先匯出應用程式繫結，然後再指定繫結的實際執行目標環境，將繫結新增回應用程式。 稍後在實際執行環境中將應用程式 .msi 檔案匯入回 BizTalk Server 時，可以指定套用這些繫結。 如需詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
5.  **匯出到新的.msi 檔案 （選擇性） 應用程式。** 如果您進行組態變更或新增至應用程式，並想要的變更才會反映在.msi 檔案 （例如部署到其他 BizTalk 群組應用程式），您可以匯出新的.msi 檔案中所述[如何匯出BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。  
  
## <a name="see-also"></a>另請參閱  
 [應用程式部署工作](../core/application-deployment-tasks.md)