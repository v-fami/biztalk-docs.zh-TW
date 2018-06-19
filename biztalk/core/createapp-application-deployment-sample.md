---
title: CreateApp （應用程式部署範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, examples
- deploying, .msi file
- deploying, exporting
- .msi files, deploying
- examples, deploying
ms.assetid: 825627ee-21d0-4505-9df4-1dadc51335b6
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 842683d2eec04d77bad2b7726af0d687fae12884
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969708"
---
# <a name="createapp-application-deployment-sample"></a>CreateApp (應用程式部署範例)
本主題說明如何使用 CreateApp 範例，此範例會示範如何使用 BTSTask 命令列工具來部署和解除部署 BizTalk 應用程式。 您可以使用此範例中的指令碼，將部署和解除部署 BizTalk 應用程式的夜間建置程序自動化。  
  
> [!IMPORTANT]
>  當您編寫部署指令碼時，應該永遠讓其以無訊息模式執行。 如果不這麼做，便會出現對話方塊要求使用者輸入內容。 這樣會停止部署程序，直到有人手動關閉對話方塊為止，如此會導致匯入程序停止進行。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例含有指定碼，可以將應用程式部署工作自動化。 若要執行這些工作，請執行會產生 BizTalk 專案和檔案的指令碼。 接著再執行會產生兩個 BizTalk 應用程式 .msi 檔案的指令碼，其中一個 .msi 檔案包含應用程式的所有成品，而另一個只包含應用程式的一個組件。 下一步您要執行另一個指令碼，這個指令碼會使用 .msi 檔案將應用程式匯入 BizTalk 群組，並將該應用程式安裝在本機電腦。 在安裝期間，應用程式所含的前置處理指令碼會建立應用程式所使用的資料夾，並在檔案中記錄其動作。 最後，再執行一個指令碼，刪除並解除安裝應用程式。 在解除安裝期間，應用程式所含的前置處理指令碼會移除安裝期間所建立的檔案和應用程式，並在檔案中記錄其動作。  
  
 此範例包含的指令碼如下：  
  
-   **Build.bat。** 會產生金鑰檔案、在 Visual Studio 中建置專案，以及簽署 .dll 檔案。  
  
-   **CreateFullAndPartialMSI.bat。** 依序採取下列動作：  
  
    1.  使用 BTSTask [AddApp 命令](../core/addapp-command.md)建立應用程式。  
  
    2.  使用 BTSTask [AddResource 命令](../core/addresource-command.md)將新增至應用程式三個 BizTalk 組件 Build.bat 產生的以及其他資源。  
  
    3.  使用 BTSTask [ExportApp 命令](../core/exportapp-command.md)應用程式的成品匯出至.msi 檔案 createapplicationsample.msi。  
  
    4.  使用 BTSTask [ListApp 命令](../core/listapp-command.md)產生名為 AppManifest.xml，列出所有應用程式中所包含的成品的應用程式資訊清單。  
  
    5.  使用 BTSTask [ExportApp 命令](../core/exportapp-command.md)匯出只至名為 CreateApplicationSamplePartial.msi.msi 檔案將協調流程組件。 只將協調流程組件匯出至 CreateApplicationSamplePartial.msi 檔案。 ResouceSpecPartial.xml 是 ResourceSpecComplete.xml 的已編輯版本，隨此範例提供。 這個檔案已經過編輯，因此只包含對協調流程組件的參考。 搭配這個參數時，BTSTask 只會匯出 ResourceSpecPartial.xml 檔案中所列的成品，在此例中是協調流程組件。  
  
    6.  從群組的「BizTalk 管理」資料庫移除應用程式。  
  
-   **CreateNewAppFromMSI.bat。** 使用 CreateFullAndPartialMSI.bat 產生的 CreateApplicationSample.msi，將名為 CreateApplicationSample 的應用程式安裝至本機電腦，並將應用程式匯入 BizTalk 群組。 在安裝期間，PreProcScript.bat 會自動執行 (稍後說明)。  
  
-   **RemoveApp.bat。** 依序採取下列動作：  
  
    1.  使用 BTSTask [RemoveApp 命令](../core/removeapp-command.md)從群組的 BizTalk 管理 」 資料庫刪除 CreateApplicationSample 應用程式。  
  
    2.  使用 BTSTask [UninstallApp 命令](../core/uninstallapp-command.md)從本機電腦解除安裝 CreateApplicationSample 應用程式。 在安裝期間，PreProcScript.bat 會自動執行 (如下所述)。  
  
-   **PreProcScript.bat。** 會採取以下動作：  
  
    -   每次執行時，都會針對使用者所提供的組件設定公開金鑰 Token。  
  
    -   在應用程式安裝期間，會建立下列資料夾，CreateApplicationSample 應用程式會使用這些資料夾來存放訊息：  
  
         C:\CreateApplicationSample\Out  
  
         C:\CreateApplicationSample\In  
  
    -   在應用程式解除安裝期間，會刪除安裝期間所建立的檔案和資料夾， 也會解除安裝期間安裝在全域組件快取 (GAC) 中的所有組件，並在檔案中記錄其動作。 為了要解除安裝 GAC 中的組件，這個檔案必須參考使用者所提供的公開金鑰 Token。  
  
    -   在安裝和解除安裝期間，會在下列位置建立記錄檔：  
  
         C:\ScriptLog.txt  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 您可以在下列資料夾中找到範例檔案*\<範例路徑\>* \Application 部署\\:  
  
-   CreateApp (資料夾)  
  
    -   Build.bat  
  
    -   CreateFullAndPartialMSI.bat  
  
    -   CreateNewAppFromMSI.bat  
  
    -   RemoveApp.bat  
  
-   CreateApp\Bindings (資料夾)  
  
    -   CreateApplicationSampleBindings.xml  
  
-   CreateApp\Dlls (資料夾)  
  
    -   Empty  
  
-   CreateApp\ResourceSpecs (資料夾)  
  
    -   ResourceSpecPartial.xml  
  
    -   ResourceSpecComplete.xml  
  
-   CreateApp\Scripts (資料夾)  
  
    -   PreProcScript.bat  
  
-   CreateApp\HelloApplicationDeployment (資料夾)  
  
    -   HelloApplicationDeployment.suo  
  
    -   HelloApplicationDeployment.sln  
  
-   CreateApp\HelloApplicationDeployment\Maps (資料夾)  
  
    -   POToInvoice.btm  
  
    -   Maps.btproj  
  
-   CreateApp\HelloApplicationDeployment\Orchestrations (資料夾)  
  
    -   Orchestrations.btproj  
  
    -   HelloOrchestration.odx  
  
-   CreateApp\HelloApplicationDeployment\Schemas (資料夾)  
  
    -   Schemas.btproj  
  
    -   POSchema.xsd  
  
    -   InvoiceSchema.xsd  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 請根據下列程序來使用此範例。  
  
### <a name="to-use-the-sample"></a>若要使用範例  
  
1.  執行 Build.bat。 這個檔案會產生金鑰檔案、在 HelloApplicationDeployment 資料夾下建置專案、簽署所產生的 .dll 檔案，以及將 .dll 檔案置於 Dlls 資料夾中。  
  
2.  開啟 PreProcScript.bat 檔案，這個檔案位在 CreateApp\Scripts 資料夾中。 從下列程式碼行中移除 REM 並提供組件的公開金鑰 Token：  
  
     **REM 設定 PublicKeyToken =**  
  
     範例：  
  
     **設定 PublicKeyToken = 1234a5b6c1234567**  
  
3.  執行 CreateFullAndPartialMSI.bat。 這個檔案會建立兩個應用程式 .msi 檔案：CreateApplicationSample.msi 和 CreateApplicationSamplePartial.msi。  
  
4.  執行 CreateNewAppFromMSI.bat。 這個檔案會將 CreateApplicationSample 應用程式匯入 BizTalk 群組，並將該應用程式安裝到本機電腦。  
  
5.  檢查 C:\ScriptLog.txt 這個指令碼記錄檔，確認指令碼有記錄其安裝動作。  
  
6.  確認 [BizTalk Server 管理主控台] 和 [新增或移除程式] 中都有出現 CreateApplicationSample 應用程式。  
  
7.  執行 RemoveApp.bat。 這個檔案會從「BizTalk 管理」資料庫刪除 CreateApplicationSample，同時從本機電腦解除安裝此應用程式。  
  
8.  檢查 C:\ScriptLog.txt 這個指令碼記錄檔，確認指令碼有記錄其解除安裝動作。 這些動作的記錄位置應該在稍早安裝期間所記錄的安裝動作之後。  
  
9. 確認 [BizTalk Server 管理主控台] 和 [新增或移除程式] 中都不再出現 CreateApplicationSample 應用程式。  
  
10. 確認在安裝期間所建立的資料夾都已刪除。  
  
11. 確認已從 GAC 解除安裝組件。  
  
## <a name="see-also"></a>請參閱  
 [應用程式部署 （BizTalk Server 範例資料夾）](../core/application-deployment-biztalk-server-samples-folder.md)   
 [部署 BizTalk 應用程式](../core/deploying-biztalk-applications.md)