---
title: "SelectiveBindingImport （應用程式部署範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, importing
- examples, applications
- binding files, examples
- examples, importing
- applications, binding files
- applications, examples
- applications, importing
- deploying, scripts
- examples, binding files
ms.assetid: 963bfc80-8cc4-4d90-96b4-e85ae04405cf
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88e6a2aa02decf1e4ed9c4a9838077be0c3b97b2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="selectivebindingimport-application-deployment-sample"></a>SelectiveBindingImport (應用程式部署範例)
此主題說明如何使用 SelectiveBindingImport 範例。 將應用程式匯入不同的目的地環境時，您可以使用此範例指令碼，將不同的繫結套用至同一個應用程式。 希望從儲存在網路共用上的繫結檔案匯入繫結時，您可以使用這個方法。  
  
> [!NOTE]
>  如果應用程式匯入期間，不需要從網路共用自動匯入繫結檔案，可以將已指定不同目的地環境的不同繫結檔案加入至應用程式。 匯入應用程式時，您可以指定環境以及環境會自動套用的繫結。 如需詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
 BizTalk 應用程式通常會從開發、測試、執行，再移至實際執行環境。 通常不同環境所使用的繫結各異。 使用此範例，您可以為不同的環境套用繫結，如下所示：  
  
1.  將您想使用的所有繫結檔案置於網路共用。  
  
2.  將後置處理指令碼加入至應用程式，該應用程式會於應用程式匯入時，從這個位置為特定的目的地環境匯入正確的繫結檔案。 指令碼會讀取您在本機電腦上設定的 %ENVIRONMENT% 環境變數來偵測環境。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例說明如何使用 BizTalk 應用程式 .msi 檔內的後置處理指令碼，從網路共用選擇性匯入繫結檔案。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 下列範例資料夾和下的檔案，您可以找到*\<範例路徑\>*\Application Deployment\SelectiveBindingImport:  
  
-   Develop (資料夾)  
  
    -   Dev.xml  
  
-   Production (資料夾)  
  
    -   Production.xml  
  
-   Staging (資料夾)  
  
    -   Staging.xml  
  
-   Test (資料夾)  
  
    -   Test.xml  
  
-   SelectiveBindings.bat  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 請使用下列程序來執行此範例。  
  
### <a name="to-run-the-sample"></a>執行範例  
  
1.  執行**從 Build.Bat *\<範例路徑\>*\Application Deployment\CreateApp**目錄。 這會建立下列檔案中的*\<範例路徑\>*\Application Deployment\CreateApp\Dlls 資料夾： Schemas.dll、 Maps.dll 和 Orchestrations.dll。  
  
2.  **建立應用程式。** 在 BizTalk Server 管理主控台中，建立應用程式中所述[如何建立應用程式](../core/how-to-create-an-application.md)。  
  
3.  **加入第一個步驟中建立的.dll 檔案的應用程式。** 如需指示，請參閱[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。  
  
4.  **建立環境變數，如下所示：**  
  
    1.  在 [開始] 功能表中，以滑鼠右鍵按一下**我的電腦**按一下**屬性**。  
  
    2.  在**進階**索引標籤上，按一下 **環境變數**。  
  
    3.  在**使用者變數**區段中，按一下**新增**。  
  
    4.  在**變數名稱**，型別**環境**。  
  
    5.  在**變數值**，值型別上的下列環境：**開發**，**生產**，**臨時**，或**測試**。 這些值會區分大小寫。  
  
5.  按一下**確定**三次。  
  
6.  **將繫結檔案複製到檔案系統上的位置。** 從 [Develop]、[Test]、[Staging] 和 [Production] 資料夾，將繫結 .xml 檔複製至檔案系統上的位置。  
  
7.  **編輯後置處理指令碼。** 編輯 SelectiveBindings.bat，如下所示：  
  
    1.  **指定的繫結檔案的位置。** 刪除包含 BINDINGS_LOC 那一行的 REM，並提供您複製繫結檔案所在位置的路徑。  
  
         範例：  
  
         BINDINGS_LOC=C:\MyBindings  
  
    2.  **指定應用程式名稱。** 刪除包含 APPLICATION_NAME 那一行的 REM，並提供您想匯入繫結之應用程式的名稱。  
  
         範例：  
  
         APPLICATION_Name=SelectiveBindingImport  
  
8.  **將指令碼加入至應用程式做為後置處理指令碼。** 如需指示，請參閱[如何新增前置或後置處理指令碼至應用程式](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)。  
  
9. **匯出應用程式。** 如需指示，請參閱[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。  
  
10. **刪除應用程式。** 如需指示，請參閱[如何從 BizTalk 群組刪除 BizTalk 應用程式](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md)。  
  
11. **匯入應用程式。** 如需指示，請參閱[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。 您不需要指定目的地環境。  
  
12. **請確認已套用正確的繫結檔案。** 只要檢查接收位置的描述欄位即可確認，如下所示：  
  
    1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
    2.  在主控台樹狀結構中，展開 BizTalk 群組、BizTalk 應用程式和 [Receive Locations] 資料夾。  
  
    3.  在右窗格中，檢視接收位置的描述。  
  
13. **安裝應用程式。** 如需指示，請參閱[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)。  
  
## <a name="see-also"></a>請參閱  
 [應用程式部署 （BizTalk Server 範例資料夾）](../core/application-deployment-biztalk-server-samples-folder.md)   
 [部署 BizTalk 應用程式](../core/deploying-biztalk-applications.md)