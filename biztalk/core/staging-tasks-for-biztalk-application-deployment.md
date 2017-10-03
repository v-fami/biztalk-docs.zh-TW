---
title: "BizTalk 應用程式部署的暫存工作 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, staging
- deploying [applications], staging
- applications, deploying
- deploying [applications], tasks
ms.assetid: de60eddb-da13-412a-94f9-331387b5930e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f03d0cfd5db587a84a080d5963d6696e123ef2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="staging-tasks-for-biztalk-application-deployment"></a>BizTalk 應用程式部署的預備工作
以下是將 BizTalk 應用程式部署到執行環境所需到的步驟。  
  
1.  **將.msi 檔案複製到執行環境。** 中所述[BizTalk 應用程式部署的測試工作](../core/testing-tasks-for-biztalk-application-deployment.md)，當的 BizTalk 應用程式已完成測試且準備好執行，測試小組提供一個或多個.msi 檔案供暫存。 (完整的解決方案可能是由一或多個 BizTalk 應用程式所組成，所以您可能會接到數個用於執行的 .msi 檔案)。您可以將此 .msi 檔案複製到執行環境，然後如下一個步驟的描述，在執行環境中將 BizTalk 應用程式從 .msi 檔案匯入到 BizTalk 群組中。 您同時也會使用 .msi 檔案，將應用程式安裝在將執行該應用程式的電腦上  
  
2.  **從.msi 檔案，匯入應用程式。** 您可以使用 BizTalk Server 管理主控台提供的匯入精靈，在執行環境中將 .msi 檔案的內容匯入到 BizTalk 群組中的應用程式。 如需詳細資訊，請參閱[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。 如果指定的應用程式尚未存在，則匯入 .msi 檔案便會建立該應用程式。 接著，您可以從 BizTalk Server 管理主控台檢視該應用程式，並修改其組態和內容。 舉例來說，您可能需要這麼做，才能針對執行環境修改繫結。 如需詳細資訊，請參閱[建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)。 如果已將繫結檔案新增至具有適用於執行環境之正確繫結的應用程式，則可以在匯入程序期間套用繫結。 如需詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
3.  **匯出繫結檔案，並將其加入回應用程式 （選擇性）。** 若要在稍後應用程式發生變更或新增項目時，以更輕鬆的方式將應用程式匯入回執行環境，可以先匯出應用程式繫結，然後再指定繫結的執行目標環境，將繫結新增回應用程式。 稍後在執行環境中將應用程式 .msi 檔案匯入回 BizTalk Server 時，可以指定套用這些繫結。 如需詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
4.  **安裝應用程式。** 您現在可在將執行應用程式的所有電腦上安裝應用程式。 您可以使用安裝精靈來安裝應用程式，或者按兩下 .msi 檔案進行安裝。 如需詳細資訊，請參閱[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)。  
  
5.  **測試應用程式來確認組態和繫結。** 現在可以測試應用程式，確定它能在執行環境中如預期般運作。 在您或開發人員進行必要的變更後，就可以再次遵循步驟 1 到 4 執行。  
  
6.  **產生.msi 以部署到生產環境應用程式**。 一旦針對實際執行環境完成 BizTalk 應用程式的設定並進行過確認後，就可以將它部署到實際執行環境。 若要這樣做，您使用 「 匯出精靈 」 來產生新的.msi 檔案中所述[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。 接著可以將 .msi 檔案發給負責實際執行部署的 IT 系統管理員。 IT 系統管理員將會使用.msi 檔案匯入 BizTalk Server 的應用程式在生產電腦上，以及將執行它，在電腦上安裝中所述[實際執行工作，BizTalk 應用程式部署](../core/production-tasks-for-biztalk-application-deployment.md).  
  
## <a name="see-also"></a>另請參閱  
 [應用程式部署工作](../core/application-deployment-tasks.md)