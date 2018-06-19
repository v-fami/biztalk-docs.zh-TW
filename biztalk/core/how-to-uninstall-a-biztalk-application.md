---
title: 如何解除安裝 BizTalk 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [applications], uninstalling
- applications, uninstalling
- uninstalling, applications
- undeploying, uninstalling
ms.assetid: ab721c6e-194e-4b8a-bfd1-d0139d284373
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cba0c5f4ea8340612bb42c4a15257acd449848d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256838"
---
# <a name="how-to-uninstall-a-biztalk-application"></a>如何解除安裝 BizTalk 應用程式
本主題描述如何使用 [新增或移除程式] 控制台或 BTSTask 命令列工具來解除安裝 BizTalk 應用程式。 只支援使用這兩個方法解除安裝應用程式。 如果您為這個應用程式安裝了多個 .msi 檔案 (例如，為了更新此應用程式)，則按兩下 .msi 檔案或使用 msiexec 可能不會完全解除安裝此應用程式，因此，這些是不支援的解除安裝方法。  
  
> [!CAUTION]
>  當 BizTalk 應用程式正在執行時將它解除安裝，可能會在此應用程式中產生錯誤。 若要避免這個問題，最佳作法是，我們建議您確認有都沒有執行服務應用程式的執行個體中所述[如何搜尋所有服務執行個體](../core/how-to-search-for-all-service-instances.md)。 如果有必要，您可以停止應用程式使用完全停止 選項來完全停止所有執行的執行個體，如下所示[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。 請注意，當您這樣做時，內含式訊息將不會完成。  
  
 前置或後置處理指令碼應該包含在應用程式的 .msi 檔案中，解除安裝應用程式時，才會移除與它相關的所有檔案和設定。 如果未包含前置或後置處理指令碼，本主題中的程序將會從本機檔案系統移除應用程式的檔案和設定，但下列幾個情況例外。  
  
-   如果應用程式包含虛擬目錄，將會刪除該虛擬目錄和它的檔案，除非在安裝應用程式後已在虛擬目錄中加入檔案。 在此情況下，將不會刪除該虛擬目錄和加入的檔案。 如果您想要刪除此虛擬目錄和加入的檔案，您必須明確加以刪除。  
  
-   會刪除前置和後置處理指令碼，但是不會刪除這些指令碼在安裝或解除安裝期間加入的任何檔案，也不會復原這些指令碼所採取的任何動作。 如果您想要刪除指令碼加入的檔案或復原其動作，您必須明確加以刪除或復原。  
  
    > [!NOTE]
    >  在解除安裝期間，只有在匯入應用程式時，已在部署屬性中指定目的地位置的前置或後置處理指令碼才會執行。 如需詳細資訊，請參閱[如何新增前置或後置處理指令碼至應用程式](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)。  
  
-   當您解除安裝 BizTalk 應用程式時，絕對不會刪除憑證。 如果您想要刪除憑證，您必須明確加以刪除。 此外，不會從 Windows 登錄中移除元件，也不會從全域組件快取 (GAC) 中移除 BizTalk 組件。 如果您想要移除它們，您必須明確加以移除。 如需詳細資訊，請參閱[如何移除其他檔案和設定 BizTalk 應用程式](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md)。  
  
 如果您在解除安裝作業完成之前將其取消，BizTalk Server 會回復解除安裝，但在作業取消之前由前置或後置處理指令碼所執行的任何動作除外。 若要將應用程式還原成解除安裝開始之前的狀態，請按兩下 .msi 檔案，然後重新安裝應用程式。 如果您已經為這個應用程式安裝了多個 .msi 檔案，您應該在每一個 .msi 檔案上按兩下 (依據這些 .msi 檔案原本安裝的順序) 來重新安裝應用程式。  
  
 如需後置處理指令碼的詳細資訊，請參閱[使用前置和後置處理指令碼，以自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)。  
  
> [!NOTE]
>  若要完全解除部署 BizTalk 應用程式，您也必須刪除它從 [BizTalk 群組] 中所述[如何從 BizTalk 群組刪除 BizTalk 應用程式](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題的程序，您必須以適當的使用權限登入。 如需詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="to-uninstall-a-biztalk-application"></a>若要解除安裝 BizTalk 應用程式  
  
#### <a name="using-uninstall-or-change-a-program"></a>使用解除安裝或變更程式  
  
1.  在電腦上執行應用程式，按一下 **啟動**，按一下**控制台**，然後按兩下**程式和功能**。  
  
2.  在**解除安裝或變更程式**頁面上，以滑鼠右鍵按一下 BizTalk 應用程式，以移除，然後按一下**解除安裝**。  
  
     Windows Installer 就會移除指定的應用程式。  
  
3.  如果此應用程式在多部電腦上執行，請在每一部電腦上重複這些步驟。  
  
#### <a name="using-the-command-line"></a>使用命令列  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。  
  
2.  輸入下列命令，並以適當的值替代，如下表所述：  
  
     **BTSTask UninstallApp** [**/ApplicationName:***值*]  
  
     範例：  
  
     **BTSTask UninstallApp /applicationname: myapplication**  
  
    |參數|值|  
    |---------------|-----------|  
    |**/ 應用程式名稱**|要解除安裝的 BizTalk 應用程式的名稱。 如果名稱包含空格，您必須將它括在雙引號 (") 中。|  
  
## <a name="see-also"></a>另請參閱  
 [解除部署 BizTalk 應用程式](../core/undeploying-biztalk-applications.md)   
 [UninstallApp 命令](../core/uninstallapp-command.md)