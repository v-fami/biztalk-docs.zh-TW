---
title: "如何部署 BizTalk 組件從 Visual Studio |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69d70c52-3e71-4eb2-876e-b467c7ca24b7
caps.latest.revision: "39"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07810f513c3530b214eb1405462db1e6ac96ed84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-a-biztalk-assembly-from-visual-studio"></a>如何從 Visual Studio 部署 BizTalk 組件
本主題提供有關如何使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的「方案總管」或 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的命令提示字元，從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 將 BizTalk 組件部署至 BizTalk 應用程式的指示。 您可以選擇從專案層級部署單一組件 (例如以滑鼠右鍵按一下專案，然後按一下 [部署])，或從方案層級同時部署方案中的所有組件 (例如以滑鼠右鍵按一下方案，然後按一下 [部署])，但強烈建議從方案層級同時部署所有組件。  
  
 與舊版[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，如果您想要部署多個組件在解決方案中，而且任何組件都相依於任何其他組件，您必須個別部署組件及其相依性的相反。 例如，如果組件 1 相依於組件 2，您必須先部署組件 2，接著才可以部署組件 1。  
  
 現在當您從專案層級部署組件時，這個狀況仍然適用。 與[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，不過，當您部署組件從方案層級，而非專案層級，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會自動處理所有的部署步驟，包括部署組件，以正確的順序。 因此，為了簡化部署，當另一個組件相依於正在部署的組件時，您應該在方案層級部署組件。  
  
 當您選取部署專案或方案中的選項[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，組件或組件會自動建立並部署到本機 BizTalk 群組中指定的 BizTalk 應用程式。 如果應用程式尚未存在於群組中，則部署時也會建立該應用程式。 接著註冊組件及其所含成品，並且將其資料儲存在 BizTalk 群組的 BizTalk 管理 (組態) 資料庫中。 此外，如果在專案的部署屬性中指定相關選項，組件就會加入至全域組件快取 (GAC) 中。  
  
 「 成品 」 是 BizTalk 應用程式，包括您在中使用的資源中包含任何項目[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，例如組件和協調流程，以及您建立或部署應用程式之後再, 加入其他項目例如傳送和接收埠，憑證和指令碼。 部署組件之後，您可以檢視並管理其成品的應用程式節點中[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]主控台。 每個應用程式都會儲存在其專用資料夾中，並且子資料夾會顯示應用程式中的成品。 如需詳細資訊，請參閱[使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)。 如需有關建立和管理應用程式的詳細資訊，請參閱[部署和管理 BizTalk 應用程式](../core/deploying-and-managing-biztalk-applications.md)。  
  
 在部署組件之前，您必須執行下列步驟：  
  
-   建立強式名稱組件金鑰檔案，並指派至每一個專案中中, 所述[如何設定強式名稱組件金鑰檔案](../core/how-to-configure-a-strong-name-assembly-key-file.md)。  
  
-   設定專案的部署屬性中所述[如何在 Visual Studio 中設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)。  
  
-   如果您先前已部署組件，請啟用專案的重新部署選項。 如需指示和重新部署的其他重要資訊，請參閱[如何重新部署 BizTalk 組件從 Visual Studio](../core/how-to-redeploy-a-biztalk-assembly-from-visual-studio.md)。  
  
> [!IMPORTANT]
>  絕對不要在實際執行電腦中執行本主題中說明的工作。 在開發過程中，開發人員通常必須從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 重新部署組件。 為了重新部署，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]可能解除部署、 解除繫結、 停止及取消登錄存在於相同或不同的應用程式的成品。 雖然這在開發環境中是必要且適當的動作，但卻可能在實際執行環境中造成無法預期的嚴重後果。 此外，為了避免任何人嘗試在實際執行電腦上從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 部署組件的可能性，我們建議您不要在實際執行電腦上安裝 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
> [!NOTE]
>  .NET Framework 執行階段安全性原則預設會防止從網路共用部署組件。 如果您嘗試從網路共用部署組件時遇到困難，請洽詢 .NET Framework 安全性系統管理員，或參閱 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 組合集合中的＜安全性原則管理＞。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須記錄成員的帳戶[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。 如果在**部署**屬性，您已啟用的選項，將組件安裝至全域組件快取 (GAC)，那麼您也需要 GAC 的讀/寫權限。 本機電腦上的「系統管理員」帳戶具有這項權限。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-deploy-a-biztalk-assembly-or-assemblies"></a>若要部署 BizTalk 組件  
  
#### <a name="using-visual-studio-solution-explorer"></a>使用 Visual Studio 方案總管  
  
-   在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下 BizTalk 專案或方案，然後**部署**。  
  
     專案或方案中的組件就會部署到指定的 BizTalk 應用程式。 建置和部署程序的狀態會顯示在頁面左下角。  
  
#### <a name="using-the-visual-studio-command-prompt"></a>使用 Visual Studio 命令提示字元  
  
1.  啟動**Visual Studio 命令提示字元**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **devenv / 部署***SolnConfigName* *SolutionName* [**/專案** *ProjName*] [**//projectconfig** *ProjConfigName*]    
  
     範例：  
  
     **devenv / 部署發行"C:\Documents 和 Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"] / [專案 「 MyBizTalkApp\MyBizTalkApp.csproj"/projectconfig 版本**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 部署**|在建置或重建後部署解決方案。|  
    |*SolnConfigName*|解決方案組態名稱，用來建置在 SolutionName 中命名的解決方案。|  
    |*SolutionName*|解決方案檔案的完整路徑和名稱。|  
    |**/project***ProjName* |解決方案中專案檔的路徑和名稱。 您可以輸入從 SolutionName 資料夾到專案檔的相對路徑、專案的顯示名稱，或專案檔的完整路徑和名稱。|  
    |**/projectconfig***ProjConfigName* |要在建置專案時使用的專案建置組態名稱。|  
  
     第一次部署包含協調流程的組件時，您可能會收到警告訊息，指出協調流程未包含在繫結檔案中。 這是因為部署時協調流程不會自動繫結至主控件， 您必須手動執行此步驟。  
  
## <a name="see-also"></a>另請參閱  
 [部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)