---
title: "當您部署的組件 Visual Studio 時，會發生什麼情況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 421df529-1ddb-4f49-a40a-c06f2a434ffc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66454d80d702cc6b3ca20708b07fd64cdfcb00d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-happens-when-you-deploy-an-assembly-from-visual-studio"></a>當您從 Visual Studio 部署組件時發生哪些狀況
本主題描述當您從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 將組件部署到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上的 BizTalk 應用程式時，會發生哪些狀況。  
  
 您可以個別部署專案，或是在同時部署方案中的所有專案。 部署專案前, 分開或是做為方案一部分您指定要在其中部署組件專案屬性中的應用程式中所述[如何在 Visual Studio 中設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)。 當您在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中部署專案或方案時，便會自動建置組件，並會將其部署到指定的應用程式中。 如果本機 BizTalk 群組中的現有應用程式與專案屬性中指定的應用程式具有相同名稱，組件就會部署至現有應用程式。否則，便會建立具有指定名稱的新應用程式，而且會將組件部署至其中。 做為此程序的一部分，組件連同協調流程、管線、結構描述，以及其所包含的對應 (稱為「成品」) 都會匯入到本機 BizTalk 管理資料庫，並會在資料庫中與指定的應用程式建立關聯。  
  
 即使當您同時在方案中部署這些專案時，也可以在方案中將專案部署到相同的 BizTalk 應用程式，或是部署到不同的 BizTalk 應用程式。 下圖說明在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，將 BizTalk 方案所包含的三個組件部署至兩個不同的 BizTalk 應用程式。  
  
 ![部署 BizTalk 組件](../core/media/visualstudiodeploy.gif "VisualStudioDeploy")  
  
 在部署專案或方案以後，您便能夠從 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 內，或是使用 BTSTask 命令列工具，來檢視和管理組件及其成品。  
  
## <a name="destination-locations"></a>目的地位置  
 從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 部署組件時，組件的目的地位置預設為組件的來源位置。 從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 安裝或匯出組件時，如果 "from" 和 "to" 環境並不相同，安裝便會失敗。 例如，如果來源位置是 D:[path]/[filename]，目標電腦的安裝電腦卻沒有 "D" 磁碟機，安裝便會失敗。  
  
 這項行為與使用 [BizTalk 系統管理員] 新增資源形成對比。在該種情況下，預設的目的地位置是 %BTAD_InstallDir%。 此環境變數會展開為安裝期間所指定的安裝目錄。  
  
 若要因應這個問題，請使用下列程序：  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中部署組件。  
  
2.  在部署組件以後，開啟 [BizTalk 系統管理員]。  
  
3.  適當地修改目的地位置。 例如，將目的地位置變更為 %BTAD_InstallDir%。  
  
 一旦修改過目的地位置後，這個新位置便會被用來做為相同組件之後續重新部署的預設值。  
  
 如需詳細資訊，請參閱[如何部署 BizTalk 組件從 Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)。  
  
## <a name="deploying-solutions-vs-projects"></a>部署方案 vs。專案  
 我們強烈建議您永遠部署方案而非個別的專案。 當您在部署個別的專案，而且在您所部署的某個組件與另一個組件之間有相依性時，您就必須採取數個手動步驟來完成部署。 然而，當您部署方案時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會自動採取管理組件之間相依性的所有必要步驟。 如需詳細資訊，請參閱[如何重新部署 BizTalk 組件從 Visual Studio](../core/how-to-redeploy-a-biztalk-assembly-from-visual-studio.md)。  
  
 下圖說明當您部署方案時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 用來重新部署具有相依性之組件的步驟。  
  
 ![部署方案中的組件](../core/media/deployassemblies.gif "DeployAssemblies")  
  
## <a name="see-also"></a>另請參閱  
 [部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)