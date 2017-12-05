---
title: "範本 （應用程式部署範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, examples
- scripts, deploying
- deploying, scripts
- examples, deploying
ms.assetid: 7e77ff8e-b2bc-4d38-b5fd-329d6d54221f
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 315a685f0e289d60e3db9dfbe77bae5a7e2b19f0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="template-application-deployment-sample"></a>範本 (應用程式部署範例)
本主題描述如何使用「範本」範例進行應用程式部署。  
  
 您可以建立並使用兩種類型的部署指令碼自訂 BizTalk 應用程式部署： 前置處理指令碼和後置處理指令碼。 前置處理指令碼的叫用時機為應用程式安裝及匯入開始前，以及完成解除安裝之後。 後置處理指令碼的叫用時機則為應用程式安裝及匯入完成後，以及解除安裝開始之前。  
  
 您可以撰寫前置及後置處理指令碼，讓上述每項作業都能叫用這些指令碼。 或者，您也可以設定指令碼，使其只在上述某項作業後執行。 如需有關撰寫指令碼的詳細資訊，請參閱[使用前置和後置處理指令碼，以自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)。  
  
 本主題將示範如何撰寫和部署指令碼，以便只在某項作業之前或之後叫用此指令碼。 若要這麼做，您可以撰寫指令碼來檢查三個環境 (Environment) 變數的值，判斷指令碼是在哪項作業的環境 (Context) 中受到呼叫。 指令碼會根據此環境 (Context) 繼續執行或中止執行。  
  
 本主題描述如何採取下列步驟：  
  
1.  設定記錄檔位置，以便產生指令檔作業的記錄檔。  
  
    > [!NOTE]
    >  您應該採用的最佳作法是一律產生記錄檔，如此就能驗證指令檔作業以及對問題進行疑難排解。  
  
2.  建立新的 BizTalk 應用程式，並且在其中加入範例指令碼。  
  
3.  匯出包含應用程式成品的 .msi 檔案。  
  
4.  從 BizTalk 群組刪除應用程式，如此您就可以將 .msi 檔案匯入回相同群組，並從 .msi 檔案安裝應用程式。  
  
5.  匯入應用程式，並檢查記錄檔，查看是否記錄了匯入作業。  
  
6.  安裝應用程式，並檢查記錄檔，查看安裝記錄是否附加到記錄檔中。  
  
7.  檢視記錄檔，注意指令碼執行了哪些作業，以及作業的執行時間。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 本範例提供的兩個 .bat 檔案包含匯入、安裝和解除安裝的環境 (Environment) 變數值。 SamplePreProcessing.bat 包含前置處理指令碼的變數。 SamplePostProcessing.bat 包含後置處理指令碼的變數。 這兩個檔案也會示範如何記錄指令碼的訊息。 您可以將這些檔案中的相關區段複製到您的指令碼中。  
  
> [!IMPORTANT]
>  指令碼檔案中的部分註解不正確，如下所示：  
>   
>  SamplePreProcessing.bat 中的指令碼註解 "Pre uninstall part of the script called for an existing application" (為現有應用程式呼叫之指令碼的前置解除安裝部分) 應該是 "Post uninstall part of the script called for an existing application" (為現有應用程式呼叫之指令碼的後置解除安裝部分)。  
>   
>  SamplePostProcessing.bat 中的指令碼註解 "Post uninstall part of the script called for an existing application" (為現有應用程式呼叫之指令碼的後置解除安裝部分) 應該是 "Pre uninstall part of the script called for an existing application" (為現有應用程式呼叫之指令碼的前置解除安裝部分)。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 此範例位於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝資料夾內，如下所示：  
  
 *\<範例路徑\>*\Application Deployment\Template  
  
 如前所述，此範例包含下列兩個檔案：  
  
-   SamplePreProcessing.bat  
  
-   SamplePostProcessing.bat  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 若要執行範例，請採取下列步驟。  
  
### <a name="to-set-the-logging-location"></a>若要設定記錄位置  
  
-   開啟這兩個指令碼範例，變更 LogFile 變數，讓其指向要寫入記錄檔的位置。 您必須提供完整路徑，包含檔案名稱。 如果路徑包含空格，您必須將它括在雙引號 (") 中。  
  
     範例：  
  
     設定記錄檔 ="*\<範例路徑\>*\ApplicationDeployment\Templates\SampleLogOut.txt"  
  
### <a name="to-create-a-new-application"></a>若要建立新的應用程式  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]並展開 BizTalk 群組。  
  
3.  以滑鼠右鍵按一下**應用程式**，然後按一下 **新增**。  
  
4.  在**應用程式名稱**，型別`SamplesTemplate`，然後按一下 **確定**。  
  
### <a name="to-add-the-scripts-to-the-application"></a>若要將指令碼加入至應用程式  
  
1.  展開您剛才建立的 SamplesTemplate 應用程式的資料夾，然後以滑鼠右鍵按一下**資源**的左窗格中。  
  
2.  指向**新增**按一下**前置處理指令碼**。  
  
3.  按一下**新增**並瀏覽至 SamplePreProcessing.bat。  
  
4.  選取檔案，然後按一下**開啟**。  
  
5.  在**檔案類型**，按一下  **system.biztalk: preprocessingscript**，然後按一下 **確定**。  
  
     SamplePreProcessing.bat 隨即加入至應用程式，而且會顯示在應用程式的 Resources 資料夾中。  
  
6.  資源上按一下滑鼠右鍵，指向**新增**，然後按一下 **後置處理指令碼**。  
  
7.  按一下**新增**並瀏覽至 SamplePostProcessing.bat。  
  
8.  選取檔案，然後按一下**開啟**。  
  
9. 在**檔案類型**，按一下  **system.biztalk: postprocessingscript**，然後按一下 **確定**。  
  
     SamplePostProcessing.bat 隨即加入至應用程式，而且會顯示在應用程式的 Resources 資料夾中。  
  
### <a name="to-export-an-msi-file"></a>若要匯出 .msi 檔案  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下 samplestemplate 應用程式，指向**匯出**，然後按一下  **MSI 檔案**。  
  
2.  在歡迎使用匯出精靈] 頁面中，按一下 [**下一步**。  
  
3.  在 選取資源頁面上，按一下 **下一步**。  
  
4.  在 指定 IIS 主控件頁面上，按一下 **下一步**。  
  
5.  相依性] 頁面上，按一下 [**下一步**。  
  
6.  在 [目的地] 頁面中**目的地應用程式名稱**，輸入應用程式名稱。  
  
7.  在**要產生的 MSI 檔案**，輸入 MSI 檔案的完整路徑，然後按一下**匯出**。 範例： C:\MSI\SamplesTemplate.msi  
  
8.  在 [摘要] 頁面上按一下**完成**。  
  
### <a name="delete-the-application"></a>刪除應用程式  
  
-   在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下 samplestemplate 應用程式，然後按一下 **刪除**。  
  
### <a name="to-import-the-msi-file"></a>若要匯入 .msi 檔案  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**應用程式**，指向 **匯入**，然後按一下  **MSI 檔案**。  
  
2.  在歡迎使用匯入精靈 頁面上，在**要匯入 MSI 檔案**，輸入您先前已匯出，然後再按一下的.msi 檔案的路徑**下一步**。 如果有必要，您可以瀏覽 MSI 檔案即可**（...）**  按鈕。  
  
3.  在應用程式設定 頁面中**應用程式名稱**下拉式清單中，選取應用程式名稱。  
  
4.  在**可用的應用程式將參考加入至**，選取要加入的參考，如果有的話，應用程式，然後按一下**下一步**。  
  
5.  在應用程式目標環境設定] 頁面上，按一下 [**下一步**。  
  
    > [!NOTE]
    >  您不必為此範例指定目標環境 (Environment)。 如需這項功能的背景資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。 如需新增繫結檔案的指示，請參閱[如何將繫結檔案新增至應用程式](../core/how-to-add-a-binding-file-to-an-application2.md)。  
  
6.  在匯入摘要] 頁面上，確認 [摘要資訊是否正確，，然後按一下**匯入**。  
  
7.  在 結果 頁面中，按一下 **完成**。  
  
8.  開啟在執行指令檔時所建立的記錄檔，確認是否記錄了匯入作業。  
  
### <a name="to-install-the-application"></a>若要安裝應用程式  
  
1.  按兩下 .msi 檔案並執行「安裝精靈」。  
  
2.  開啟記錄檔，確認安裝作業已加入至記錄資訊。  
  
### <a name="to-verify-that-the-scripts-functioned-correctly"></a>若要確認指令檔可正常運作  
  
-   開啟記錄檔，確認在指定的作業期間指令檔都有執行。  
  
## <a name="see-also"></a>請參閱  
 [應用程式部署 （BizTalk Server 範例資料夾）](../core/application-deployment-biztalk-server-samples-folder.md)   
 [部署 BizTalk 應用程式](../core/deploying-biztalk-applications.md)