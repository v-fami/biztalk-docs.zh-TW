---
title: "補償 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- compensations, examples
- examples, compensations
- compensations, orchestrations
ms.assetid: 9d10c7be-6a4c-44cc-bf29-78ecdf147bd1
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7d3e2e917f9ac0cc09117f3de83bbcc6166af1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="compensation-biztalk-server-sample"></a>補償 （BizTalk Server 範例）
補償範例示範如何使用**補償**使用協調流程。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例示範如何使用下列步驟順序補償在協調流程中已認可的交易。  
  
1.  在 InfoPath 表單中輸入客戶資料，然後將該資料提交到已公開為 Web 服務的協調流程。  
  
2.  協調流程有兩個平行的動作。 一個會傳回通知到 InfoPath 表單，另一個會更新 Northwind 和 BTSCompensationSampleMailingList 資料庫。  
  
3.  在第二個動作中，協調流程會將內送訊息對應至客戶關係管理 (CRM) 應用程式訊息格式，然後更新**客戶**Northwind 資料庫中的資料表。 這個動作完成後，BTSCompensationSampleMailingList 資料庫中的「郵寄清單」資料表就會更新。  
  
4.  如果這兩項更新其中一項失敗，就會呼叫外部組件將原始客戶資料寫回資料庫，來補償對 Northwind 資料庫所做的變更。  
  
## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 A**範圍**圖形主要用於交易執行以及例外狀況處理，包括補償。 範圍由兩個區塊組成。 第一個區塊是內容區塊，而第二個區塊可以是一或多個例外狀況處理或補償區塊。 這和 .NET 程式設計語言中的 try-catch 陳述式相似。 在 UpdateContact.odx 協調流程中，有兩個平行的動作。 在右邊的分支中，是在 try 區塊**範圍**圖形名為更新後端系統有長時間執行的交易類型以及 Upd_Backend 交易識別項。 在接下來的流程中，有一個 Catch 區塊，可取得一般例外狀況，並初始化補償。  
  
 如需有關**範圍**圖形，請參閱[範圍](../core/scopes.md)。 另請參閱[如何設定 「 範圍 」 圖形](../core/how-to-configure-the-scope-shape.md)。  
  
> [!NOTE]
>  協調流程本身必須為長時間執行的交易，您才能將交易類型設為「不可部分完成」或是「長時間執行」。  
  
 在 try 區塊中，有兩個範圍，名為**更新 CRM**和**更新郵件**。 這兩個範圍都是不可部分完成的交易。 在「更新 CRM」範圍中，有 try 區塊和補償區塊。 try 區塊會透過對外部組件的方法呼叫來更新 Northwind 資料庫。 補償區塊是補償動作發生的地方。 當「更新後端系統」範圍中發生例外狀況時，「復原 CRM 運算式」圖形會將記錄更新回其原始狀態。 這由觸發**補償**Catch 例外狀況區塊中的圖形。  
  
> [!NOTE]
>  不可部分完成的交易可保證任何部分更新在交易更新期間作業失敗時都會自動復原，且會清除交易的結果 (在交易中進行的任何 .NET 呼叫結果除外)。  
  
> [!NOTE]
>  當長時間執行的交易中的最後一個陳述式完成時，該交易就會被視為已認可。 在交易中止的情況下不會自動回復狀態。 您可透過此範例中示範的例外狀況和補償處理常式以程式設計方式達到這個結果。  
  
 在 catch 區塊中，有一個**延遲**圖形設定為 10 秒。 這會延遲補償動作。 另外還有**補償**初始化 Upd_Backend 交易的補償動作的圖形。  
  
 下列動作會在協調流程收到輸入訊息後發生：  
  
1.  UpdateCrm 組件會更新 Northwind 資料庫中的資料列。  
  
2.  UpdateMailingList 組件會更新 BTSCompensationSampleMailingList 資料庫中的相符記錄。  
  
3.  在更新 Northwind 資料庫時若作業失敗，會引發例外狀況，且協調流程會結束此程序。  
  
4.  在更新 BTSCompensationSampleMailingList 資料庫時若作業失敗，會引發例外狀況，且在將原始客戶資料重新寫回 Northwind 資料庫之前，每十秒會產生一次延遲。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*範例路徑*> \Orchestrations\Compensation\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|Cleanup.bat|用來解除安裝範例的批次檔案。|  
|CompensationOrchestration.btproj|協調流程專案。|  
|CompensationSample.sln|範例方案。|  
|CompensationSampleBinding.xml|繫結協調流程的資料 (用於安裝期間)。|  
|ContactInfo.xsd|連絡人資訊訊息結構描述。|  
|ContactInfo.xsx|協調流程設計師配置檔案。|  
|CreateSQLDataStore.sql|建立和填入範例資料庫的 SQL 指令碼。|  
|CrmSchema.xsd|CRM 更新訊息結構描述。|  
|MailingListSchema.xsd|郵件清單訊息更新結構描述。|  
|RemoveVirDir.vbs|Microsoft Visual Basic Scripting Edition (VBScript) 指令碼，可移除 Web 服務虛擬和實體目錄 (用於解除安裝期間)。|  
|Request2Crm.btm|從要求 (連絡人資訊) 解譯到 CRM 更新訊息的訊息對應。|  
|Request2MailingList.btm|從要求 (連絡人資訊) 解譯到郵件清單資訊的訊息對應。|  
|Setup.bat|安裝此範例的批次檔案。|  
|UpdateContact.odx|協調流程檔案。|  
|UpdateRequest2UpdateResponse.btm|從要求 (連絡人資訊) 解譯到回應訊息的訊息對應。|  
|UpdateResponse.xsd|回應訊息結構描述。|  
|InfoPath\Contact Info Update.xsn|用來提交表單至協調流程 Web 服務的 Microsoft InfoPath 檔案。|  
|UpdateCrm\AssemblyInfo.cs|UpdateCrm 組件的組件資訊來源檔案。 (UpdateCrm 組件會更新 Northwind 資料庫。)|  
|UpdateCrm\UpdateCrm.cs|UpdateCrm 組件的主要原始程式碼。|  
|UpdateCrm\UpdateCRM.csproj|UpdateCrm 專案檔。|  
|UpdateMailingList\AssemblyInfo.cs|UpdateMailingList 組件的組件資訊來源檔案。 (UpdateMailingList 組件會更新範例資料庫。)|  
|UpdateMailingList\UpdateMailingList.cs|UpdateMailingList 組件的主要原始程式碼。|  
|UpdateMailingList\UpdateMailingList.csproj|UpdateMailingList 專案檔案。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
  
#### <a name="to-build-and-initialize-the-compensation-sample"></a>建置和初始化補償範例  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*> \Orchestrations\Compensation\  
  
2.  執行 Setup.bat，這會執行下列動作：  
  
    -   建置和部署範例組件。  
  
    -   當 BizTalk Web 服務發佈精靈啟動時，請手動執行下列動作：  
  
    1.  在**歡迎使用 BizTalk Web 服務發佈精靈**頁面上，按一下**下一步**。  
  
    2.  在**建立 Web 服務**頁面上，選取**BizTalk 協調流程發佈為 web 服務**，然後按一下 **下一步**。  
  
    3.  在**BizTalk 組件**頁面上，瀏覽並選取\<*範例路徑*> \Orchestrations\Compensation\bin\Release\CompensationOrchestration.dll，然後再按一下**下一步**。  
  
    4.  在**協調流程和連接埠**頁面上，按一下**下一步**。  
  
    5.  在**Web 服務屬性**頁面上，於**web 服務目標命名空間**，型別**http://Microsoft.BizTalk.Samples.Compensation/**，然後按一下  **下一步**。  
  
    6.  在**Web 服務專案**頁面上，於**位置**，型別**http://localhost/CompensationOrchestrationWebServiceProxy**。  
  
    7.  選取**允許匿名存取 web 服務**核取方塊。  
  
    8.  選取**建立 BizTalk 接收位置，在下列應用程式中**核取方塊。  
  
    9. 在**建立 BizTalk 接收位置，在下列應用程式中**下拉式選單中，選取**BizTalk Application 1**從下拉式清單，然後按一下**下一步**。  
  
    10. 在**Web 服務專案摘要**頁面上，按一下**建立**。  
  
    11. 在**完成 BizTalk Web 服務發佈精靈**頁面上，按一下**完成**。  
  
3.  安裝程式會建立和繫結連接埠、建立此範例的後端資料庫，並新增 C# 組件至全域組件快取。  
  
    > [!NOTE]
    >  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。  
  
## <a name="running-this-sample"></a>執行此範例  
 建置和初始化此範例後，請考慮下列事項後再執行它：  
  
-   如果您執行此範例[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]，您必須建立 IIS 應用程式集區，並將其識別為屬於 BizTalk 應用程式使用者 Windows 群組成員的帳戶。 此外，您需要更新協調流程 Web 服務虛擬目錄，才可在此應用程式集區中執行。  
  
-   將 ASPNET 帳戶新增至 BizTalk 外掛式主控件使用者群組。  
  
-   授與 BizTalk 應用程式使用者群組 db_owner 權限**BTSCompensationSampleMailingList**和**Northwind**資料庫。  
  
-   如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]未安裝在預設位置 (磁碟機： files\microsoft BizTalk Server\<版本 >\\)，您必須發佈 Contact Info Update.xsn 表單後才能使用它。 若要這樣做，請執行以下動作：  
  
    #### <a name="to-publish-the-infopath-form"></a>若要發佈 InfoPath 表單  
  
    1.  在 Internet Explorer 上**工具**功能表上，按一下 **網際網路選項**。  
  
    2.  在**安全性**索引標籤上，按一下 **網際網路**，然後按一下 **自訂層級**。  
  
    3.  在**其他**區段中，確定**跨網域存取資料來源**設定已啟用，然後再按一下**確定**。 需要有此設定 InfoPath 使用者介面方案指令碼處理程式碼才能執行。  
  
    4.  在 Windows 檔案總管，瀏覽至\<*範例路徑*> \Orchestrations\Compensation\InfoPath，以滑鼠右鍵按一下**Contact Info Update.xsn** ，然後按一下 **設計**.  
  
    5.  InfoPath Contact Info Update 方案就會以設計模式開啟。  
  
    6.  在 InfoPath Contact Info Update 應用程式上**檔案**功能表上，按一下 **發行**。  
  
    7.  會顯示 [組態精靈]。  
  
    8.  選取**到此電腦上或在網路上的共用資料夾**及發佈方案至路徑\<*範例路徑*> \Orchestrations\Compensation\InfoPath\Contact Info Update.xsn。  
  
    9. 關閉設計模式 InfoPath。  
  
-   您已準備好執行這個範例。  
  
    #### <a name="to-run-the-compensation-sample"></a>若要執行補償範例  
  
    1.  按兩下**Contact Info Update.xsn**在 InfoPath 中開啟它。  
  
    2.  為同時存在這兩個資料庫中的帳戶填寫表單。 例如，使用 Northwind Customers 資料表內的現有帳戶識別碼 "ALFKI"。  
  
    3.  在**檔案**功能表上，選取**送出**，然後按一下**送出**。  
  
    4.  回應文件應該會出現在\<*範例路徑*> \Orchestrations\Compensation\Out 資料夾，而 Northwind 和 BTSCompensationSampleMailingList 資料庫應與新更新InfoPath 表單中的資料。  
  
        > [!NOTE]
        >  您可以中斷連線 BTSCompensationSampleMailingList 資料庫或讓它離線，以測試協調流程所執行的補償動作。 請注意，會先更新 Northwind 資料庫內的記錄。 接著，協調流程嘗試更新 BTSCompensationSampleMailingList 資料庫會失敗，因為該資料庫已中斷連線。 因此會引發例外狀況，而且在補償動作開始將原始客戶資料寫回 Northwind 資料庫之前，會產生十秒延遲。  
  
        > [!NOTE]
        >  您可能會得到「使用者 'IIS APPPOOL\DefaultAppPool' 的登入失敗」錯誤。 這可能是因為以權杖為基礎的伺服器存取驗證失敗。 若要解決這個錯誤，請建立新的應用程式集區，並在其中使用系統管理員帳戶。  
  
## <a name="uninstalling-this-sample"></a>解除安裝這個範例  
  
#### <a name="to-uninstall-the-compensation-sample"></a>解除安裝補償範例  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*> \Orchestrations\Compensation\  
  
2.  執行 Cleanup.bat。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程 （BizTalk Server 範例資料夾）](../core/orchestrations-biztalk-server-samples-folder.md)