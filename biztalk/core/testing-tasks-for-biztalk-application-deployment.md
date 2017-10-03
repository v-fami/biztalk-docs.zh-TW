---
title: "BizTalk 應用程式部署的測試工作 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [applications], testing
- testing, deploying
- testing, tasks
ms.assetid: fb043755-6d01-4ceb-b189-5a5f286c2b37
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bfd4385c4de076c8c89b409177204ee8fce5548b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="testing-tasks-for-biztalk-application-deployment"></a>BizTalk 應用程式部署的測試工作
以下是將 BizTalk 應用程式的成品部署到測試環境以進行測試和偵錯所牽涉的步驟。  
  
1.  **將.msi 檔案複製到您的測試環境。** 中所述[BizTalk 應用程式部署的開發工作](../core/development-tasks-for-biztalk-application-deployment.md)，當 BizTalk 應用程式時，準備進行測試，開發人員會將應用程式成品匯出至.msi 檔案。 完整的解決方案可能是由一或多個 BizTalk 應用程式所組成，所以您可能會接到數個用於測試的 .msi 檔案。 您可以將此 .msi 檔案複製到測試電腦，然後如下一個步驟的描述，將成品從 .msi 檔案匯入到 BizTalk Server 中。 您同時也可以使用 .msi 檔案，將應用程式安裝在將執行該應用程式的電腦上。  
  
2.  **從.msi 檔案，匯入應用程式。** ：您可以使用 BizTalk Server 管理主控台提供的匯入精靈，在目前的 BizTalk Server 執行個體上將 .msi 檔案中的成品匯入到應用程式。 如需詳細資訊，請參閱[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。 如果指定的應用程式尚未存在，則匯入程序會加以建立。 接著，您可以從 BizTalk Server 管理主控台檢視該應用程式，並修改其組態和內容。 舉例來說，您可能需要這麼做，才能針對測試環境修改繫結。 如需詳細資訊，請參閱[建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)。 如果已將具有適用於測試環境之正確繫結的繫結檔案新增至應用程式，則可以在匯入程序期間套用繫結。 如需詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
3.  **安裝應用程式。** ：您現在可在將執行應用程式的伺服器上安裝應用程式。 如果應用程式包含以檔案為基礎的成品，您還必須先安裝它之後才能開始運作。 您可以按兩下 .msi 檔案來安裝應用程式。 這樣會將應用程式的成品安裝及登錄在本機電腦上，讓應用程式可以執行。 如需詳細資訊，請參閱[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)。  
  
4.  **測試應用程式。** ：您現在可以測試應用程式。 在開發人員修正您所找到的任何錯誤，並提供更新的 .msi 檔案後，您就可以再次執行步驟 1、2 和 3。  
  
5.  **匯出繫結檔案，並將其加入回應用程式 （選擇性）。** ：若要在稍後測試變更或新增項目時，能以更輕鬆的方式將應用程式匯入回測試環境，可以先匯出應用程式繫結，然後再指定繫結的測試目標環境，將繫結新增回應用程式。 稍後在測試環境中將應用程式 .msi 檔案匯入回 BizTalk Server 時，可以指定套用這些繫結。 如需詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
6.  **產生.msi 以應用程式部署至預備環境**。 一旦完成 BizTalk 應用程式的測試後，就可以將它部署到執行環境。 若要這樣做，您使用 「 匯出精靈 」 來產生新的.msi 檔案，如稍早在步驟 2 中所述。 您可以再.msi 檔案遞交給負責預備環境部署的 IT 系統管理員。 IT 系統管理員將會使用.msi 檔案匯入 BizTalk Server 應用程式，執行電腦上，並將執行它，在電腦上安裝應用程式中所述[BizTalk 應用程式部署的暫存工作](../core/staging-tasks-for-biztalk-application-deployment.md).  
  
## <a name="see-also"></a>另請參閱  
 [應用程式部署工作](../core/application-deployment-tasks.md)