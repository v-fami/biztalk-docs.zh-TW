---
title: "部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: accef4b8-acdf-4043-8fd7-2db9ea752074
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1165fb461d5d54419ea56a42f7fe428ab027089
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application"></a>從 Visual Studio 將 BizTalk 組件部署到 BizTalk 應用程式
部署及重新部署 BizTalk 組件從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]到 BizTalk 應用程式。 這樣做的目的，可能是為了測試您所開發之組件的功能，並封裝這些組件來遞交。  

## <a name="overview"></a>概觀  
 BizTalk 應用程式提供檢視和管理項目，稱為 「 成品 」 組成 BizTalk 商務方案的方式。 成品包括 BizTalk 組件 （包含協調流程、 結構描述、 對應和管線），您可以部署到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。 成品也會包含項目，例如.NET 組件、 憑證、 指令碼、 讀我檔案和原則，您將新增到 BizTalk 應用程式使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台或 BTSTask 命令列工具。 然後，解決方案開發人員或 IT 管理員可以將應用程式和它的成品當做單一實體來檢視、封裝、部署和管理。 如需有關建立的詳細資訊，請部署及管理 BizTalk 應用程式，請參閱[部署和管理 BizTalk 應用程式](../core/deploying-and-managing-biztalk-applications.md)。  
  
 您可以建立和部署 BizTalk 組件之前，您必須建立的專案中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]並建立或加入您想要包含在組件中的項目。 您可以建立的方案中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]包含多個專案然後建置並部署到相同應用程式或不同的應用程式，同時其組件。 如需執行這些工作的指示，請參閱[如何建立 BizTalk 專案](../core/how-to-create-biztalk-projects.md)。  
  
 當完成這些工作之後，您可以採取下列步驟來建置、部署及解除部署 BizTalk 組件，如本章節的各個主題所述：  
  
-   每個設定強式名稱組件金鑰檔案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]專案。  
  
-   為專案設定部署屬性，包括設定 [重新部署] 選項，以便輕鬆地重新部署組件。  
  
-   使用中的 [部署] 命令[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]建置方案所包含的 BizTalk 組件，並將其部署到 BizTalk 應用程式。 另外，您也可以使用 [部署] 命令將組件建置及部署到單一專案中，但是我們不建議您這樣做。  
  
-   測試應用程式，並進行必要的變更之後, 使用中的 [部署] 命令[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]重建並重新部署組件。  
  
-   必要時，將該組件安裝到全域組件快取 (GAC) 中，或是從 GAC 中移除該組件。  
  
-   解除部署組件。  
  
 將一或多個組件部署到 BizTalk 應用程式之後，您可以完成應用程式的組態，並將它部署到測試及實際執行環境。 如需詳細資訊，請參閱[BizTalk 應用程式部署的開發工作](../core/development-tasks-for-biztalk-application-deployment.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [當您部署的組件 Visual Studio 時，會發生什麼事](../core/what-happens-when-you-deploy-an-assembly-from-visual-studio.md)  
  
-   [組件安裝在 GAC 中](../core/assembly-installation-in-the-gac.md)  
  
-   [如何設定強式名稱組件金鑰檔案](../core/how-to-configure-a-strong-name-assembly-key-file.md)  
  
-   [如何在 Visual Studio 中設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)  
  
-   [如何部署 BizTalk 組件從 Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)  
  
-   [如何重新部署 BizTalk 組件從 Visual Studio](../core/how-to-redeploy-a-biztalk-assembly-from-visual-studio.md)  
  
-   [如何安裝或解除安裝 GAC 中的組件](../core/how-to-install-an-assembly-in-the-gac.md)  