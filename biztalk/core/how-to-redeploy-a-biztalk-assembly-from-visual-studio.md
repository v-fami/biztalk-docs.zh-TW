---
title: 如何重新部署 BizTalk 組件從 Visual Studio |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5c4bb627-48de-4874-bb25-af2c513dbc51
caps.latest.revision: 41
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1357cb936c0b6f7f830bf1cc77f3d1670cf326aa
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009495"
---
# <a name="how-to-redeploy-a-biztalk-assembly-from-visual-studio"></a>如何從 Visual Studio 重新部署 BizTalk 組件
在開發組件的程序中，您通常必須重複進行部署、測試、修改和重新部署。 在舊版的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，如果您想要重新部署組件，而不變更版本號碼，您首先需要以手動方式停止、 取消登錄和解除繫結中的組件中所包含的成品[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]然後再移除的組件BizTalk 管理 （組態） 資料庫。 此外之後重新部署組件，, 您需要繫結、 登錄和啟動成品[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
 使用 BizTalk Server 中，不過，當您啟用重新部署 選項[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會自動將所有的步驟，重新部署您的組件。 雖然可從專案層級重新部署組件 (例如在 [方案總管] 中以滑鼠右鍵按一下專案，然後按一下 [部署])，重新部署個別組件，但強烈建議您一定要從解決方案層級部署組件 (例如以滑鼠右鍵按一下解決方案，然後按一下 [部署])。 這會立即重新部署解決方案中的所有組件，並在相依性存在時處理所有相關步驟 (稍後說明)。  
  
> [!IMPORTANT]
>  雖然在少數情況下您可能需要在專案層級重新部署，但通常一定是在解決方案層級重新部署。  
  
 重新部署組件時，請牢記下列要點：  
  
-   **您必須在 GAC 中安裝新的組件。** 當您重新部署組件時，您必須一律安裝新版的組件在 gac、 中所述[如何在 GAC 中安裝組件](../core/how-to-install-an-assembly-in-the-gac.md)。 您可以在重新部署後執行此作業。  
  
-   **您應該永遠重新部署方案層級相依性時。** 如果解決方案中有多個組件，而且此解決方案中的一或多個組件相依於要重新部署的組件，則您必須在解決方案層級重新部署組件。 這是因為當您重新部署組件在專案層級[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將會停止、 取消登錄、 解除繫結，並移除所有成品，是取決於此組件的這個組件相依的所有組件中。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不會部署、 繫結、 登錄和啟動成品的其他步驟。 當您重新部署整個方案，不過，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會自動帶解除部署和重新部署所有的相依性為基礎的方案中的成品所需的步驟。  
  
-   **您可能需要手動重新部署相依組件。** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]固定會解除部署相依的組件，但在下列情況下，您必須採取其他步驟，部署、 繫結，並且登錄之後重新部署組件所依賴的組件的每個相依組件中的成品：  
  
    -   如果您在專案層級重新部署組件，而且相同解決方案中的另一個組件相依於此組件。  
  
    -   如果您在解決方案層級重新部署組件，但不同解決方案中存在相依組件。  
  
     例如，如果您只要重新部署下圖中的「組件 3」，在重新部署後，您還必須部署「組件 2」的成品、將其繫結和登錄，接著部署「組件 1」的成品、將其繫結和登錄。  
  
     ![具有相依性的組件](../core/media/assemblydependencies.gif "AssemblyDependencies")  
  
     另一個方法是為了避免不必要的部署中未變更的核心組件。  例如在上圖中，如果沒有其他相依於組件 2 和 3 的組件及兩者皆非的這些組件的組件已更新。  取消核取**部署**configuration manager 中的組件 2 和 3 的組件專案中的選項。 這種方式取決於它們的外部組件不會解除部署需要重新部署。 如需詳細資訊，請參閱[如何在 Visual Studio 中設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)。  
  
-   **您必須重新啟動主控件執行個體。** 當您重新部署包含協調流程的組件而不變更組件版本號碼時，BizTalk 管理資料庫中的現有組件會遭到覆寫。 不過，在變更生效之前，您必須重新啟動協調流程所繫結之主控件的每個主控件執行個體。 您可以指定選項，在重新部署組件時，自動重新啟動本機電腦上的所有主控件執行個體。 如需指示，請參閱[如何在 Visual Studio 中設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)。 您也可以手動停止並啟動中所述的每個主控件執行個體，[如何停止主控件執行個體](../core/how-to-stop-a-host-instance.md)和[如何啟動主控件執行個體](../core/how-to-start-a-host-instance.md)。  
  
> [!IMPORTANT]
>  因為 [重新部署] 選項會略過版本控制，因此建議只在開發期間使用。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組成員的帳戶登入。 此外，您的帳戶也必須有本機檔案系統和全域組件快取 (GAC) 的讀取/寫入權限。 本機電腦上的「系統管理員」帳戶具有這些權限。  
  
## <a name="to-redeploy-a-biztalk-solution"></a>若要重新部署 BizTalk 解決方案  
  
#### <a name="using-visual-studio-solution-explorer"></a>使用 Visual Studio 方案總管  
  
1.  請確定重新部署 選項已啟用在方案中，每個專案的部署屬性中所述[如何在 Visual Studio 中設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)。 此選項預設為啟用。  
  
2.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下 BizTalk 解決方案，然後**部署**。  
  
     解決方案中的組件隨即部署到指定的 BizTalk 應用程式中。 建置和部署程序的狀態會顯示在頁面左下角。  
  
#### <a name="using-the-visual-studio-command-prompt"></a>使用 Visual Studio 命令提示字元  
  
1.  請確定重新部署 選項已啟用在方案中，每個專案的部署屬性中所述[如何在 Visual Studio 中設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)。 此選項預設為啟用。  
  
2.  啟動**Visual Studio 命令提示字元**。  
  
3.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **devenv / 部署***SolnConfigName* *SolutionName*   
  
     範例：  
  
     **devenv / 部署發行"C:\Documents 和 Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 部署**|在建置或重建後部署解決方案。|  
    |*SolnConfigName*|解決方案組態名稱，用來建置在 SolutionName 中命名的解決方案。|  
    |*SolutionName*|解決方案檔案的完整路徑和名稱。|  
  
## <a name="see-also"></a>請參閱  
 [從 Visual Studio 將 BizTalk 組件部署到 BizTalk 應用程式](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)