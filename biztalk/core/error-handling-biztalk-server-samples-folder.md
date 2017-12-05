---
title: "錯誤處理 （BizTalk Server 範例資料夾） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, errors
- errors, examples
- examples, messages
- messages, examples
- messages, errors
ms.assetid: b39791ed-277b-4625-b9a9-72480a1b6ff6
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 386e9729ac32cb08863e2ac3e0699ecda7890dbc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="error-handling-biztalk-server-samples-folder"></a>錯誤處理 (BizTalk Server Samples 資料夾)
此範例的目的是要建立「根據訊息內容決定路由」(CBR) 應用程式的錯誤處理功能。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行範例時，建議您將 Microsoft Office InfoPath 2010 或更新版本安裝。 若不使用 InfoPath，也可以執行範例，但是在此情況下，則無法透過 HTTP 配接器檢視經費支出報表或提交經費支出報表。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例會實作經費支出報表處理系統的一部分。 具體來說，本範例執行下列工作：  
  
1.  定義經費支出報表結構描述，其中包含經費支出報表和內含部門名稱的個別傳送者相關資訊。  
  
2.  提供透過目錄或使用 InfoPath 的 Web 服務提交經費支出報表的功能。  
  
3.  升級**部門**和**correlationID**訊息中的屬性文件，以便可以在連接埠篩選器中用來控制路由。  
  
4.  將屬於行銷部門的經費支出報表路由傳送至目錄中的檔案，模擬部門的後端系統傳遞作業。  
  
5.  針對非行銷部門的經費支出報表，產生失敗的訊息。 失敗的訊息包含錯誤資訊，包括錯誤碼和錯誤描述。  
  
6.  將失敗的訊息路由傳送至收件人 (商務使用者或應用程式操作人員) 來更正並重新提交。  
  
7.  根據上述部門，路由傳送重新提交的經費支出報表。  
  
 這項工作的大部分是透過 BizTalk 協調流程排程所完成。  
  
## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 其設計依賴 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的預設傳送和接收 XML 管線、屬性升級、訂閱篩選條件和協調流程排程來路由傳送訊息。 下表列出設計元素及其理由。  
  
|設計元素|已選取的原因|  
|--------------------|--------------------------|  
|預設 XML 接收管線|-XMLReceive 管線支援屬性升級;PassThruReceive 管線則否。<br />-輸入的訊息已經是 XML 格式，而且不需要基本解譯和合作對象解析之外的處理。|  
|失敗訊息的路由|接收連接埠擱置失敗的訊息，並產生負值通知預設。 啟用路由時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會嘗試將處理失敗的訊息路由傳送至訂閱應用程式 (例如其他接收埠或協調流程排程)。|  
|屬性升級|BizTalk Server 取決於屬性欄位來進行路由。 辨別欄位可用於協調流程，不能用於路由。|  
|訂閱篩選器|-訂用帳戶篩選會執行擷取符合根據屬性欄位的一或多個準則的訊息路由。|  
|BizTalk 協調流程排程|-提供機會將資訊加入失敗訊息。<br />-啟用路由傳送至專屬位置，讓人為介入的失敗訊息。<br />-處理重新提交的經費支出報表。|  
|XMLTransmit|-執行外寄 XML 訊息的基本組件。 PassThruTransmit 管線不會提供其他支援。|  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 此範例位於 <`Samples Path>`\Messaging\ErrorHandling\\。  
  
 下表包含此範例的檔案清單。  
  
|檔案|Description|  
|----------|-----------------|  
|Cleanup.bat|用來解除部署組件，以及將它從全域組件快取中移除。<br /><br /> 移除傳送埠和接收埠。<br /><br /> 視需要移除 Internet Information Services (IIS) 虛擬目錄。|  
|ErrorHandling.sln|此範例的 Visual Studio 方案檔案。|  
|ErrorHandlingBinding.xml|此範例的繫結檔案。|  
|Setup.bat|用來建置和初始化此範例。|  
|Expense Report – John Doe.xml|範例經費支出報表 InfoPath 文件。|  
|Invalid Expense Report – John Doe.xml|內含無效資料的範例經費支出報表 InfoPath 文件。|  
|在 ErrorHandler 資料夾中：<br /><br /> ErrorHandler.btproj|協調流程所使用的 BizTalk 專案。|  
|在 ErrorHandler 資料夾中：<br /><br /> ResubmitLogic.odx|訂閱失敗訊息的協調流程會將失敗訊息傳送至收件人來更正，然後重新提交已更正的訊息至伺服器來路由。|  
|在 ErrorHandler 資料夾中：<br /><br /> SuspendMessage.odx|協調流程，用於擱置無法在錯誤處理協調流程內處理的訊息。|  
|在 InfoPathForms 資料夾中：<br /><br /> Expense Report.xsn<br /><br /> Expense Report - Resubmit.xsn|經費支出報表 InfoPath 表單，以及用於檢視和重新提交失敗訊息的表單。|  
|在 PipelinesAndSchemas 資料夾中：<br /><br /> ExpenseReportSchema.xsd|經費支出報表文件的 XML 結構描述。|  
|在 PipelinesAndSchemas 資料夾中：<br /><br /> PipelinesAndSchemas.btproj|此範例所使用的 BizTalk 專案。|  
|在 PipelinesAndSchemas 資料夾中：<br /><br /> PropertySchema.xsd|此範例的屬性結構描述。|  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 以此範例做為起點，可讓您建立專屬錯誤處理程序。  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
  
#### <a name="to-build-and-initialize-the-compose-sample"></a>若要建置及初始化「編輯」範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     <`Samples Path`>**\Messaging\ErrorHandling**  
  
2.  執行**Setup.bat**，它會執行下列動作：  
  
    -   建立三個資料夾： **ExpenseReportIn**， **ExpenseReportOut**，和**ResubmittedReportIn**下列路徑底下：  
  
         <`Samples Path`>**\Messaging\ErrorHandling**  
  
    -   複製並發行 InfoPath 表單**Expense Report.xsn**和**Expense Report – Resubmit.xsn**到資料夾**C:\Temp\InfoPathForms**。  
  
    -   為此範例編譯 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  
  
    -   建立虛擬目錄稱為**ExpenseReports**。  
  
    -   建立新的 BizTalk 應用程式呼叫**Error Handling Sample**和部署範例組件。  
  
    -   建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。  
  
    -   登錄和啟動協調流程，啟用接收位置，並啟動傳送埠。  
  
         如果您選擇不執行 Setup.bat 就開啟和建置此範例中的專案，則必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 您可以使用此金鑰組簽署範例組件。  
  
3.  在嘗試執行此範例之前，請確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置或初始化的程序中報告任何錯誤。  
  
    > [!NOTE]
    >  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
4.  若是使用 Internet Information Services (IIS) 7.0，您必須執行額外的設定步驟，針對此範例所使用之 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP 接收位置的對應虛擬目錄來調整設定。 請執行下列動作來設定 IIS：  
  
    1.  使用 [IIS 7.0 管理員]，建立「BizTalk 外掛式主控件使用者」群組的新應用程式集區。  
  
    2.  將應用程式集區設定為以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 外掛式主控件」使用者的身分執行 (如果您已經為其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP 接收位置設定應用程式集區，可以略過這個步驟)。  
  
    3.  設定虛擬目錄**ExpenseReport**若要使用 HTTP 接收先前步驟中建立的應用程式集區。  
  
     如果您還沒有 BTSHTTPReceive.dll ISAPI 延伸模組的網頁伺服器延伸，請建立並將它的狀態設定為「允許」來啟用它。 您可以在 IIS 7.0 中使用 IIS 管理主控台 (請直接在**系統管理工具**或透過電腦管理主控台)，如下所示：  
  
    1.  展開**Internet Information Services 管理員**樹狀目錄中。  
  
    2.  按一下**網頁服務延伸**資料夾。  
  
    3.  在 [管理] 主控台的右窗格中，按一下**新增 Web 服務延伸**。  
  
    4.  在**新增網頁服務延伸**對話方塊中，按一下 **新增**。  
  
    5.  在**Add file**對話方塊中，按一下 **瀏覽**以選取的檔案 <`BizTalkInstallPath>`**\HttpReceive\BTSHTTPReceive.dll**，然後按一下 **確定**.  
  
    6.  設定虛擬目錄**ExpenseReport**為使用本機路徑[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HTTPReceive  
  
     如需詳細資訊，請參閱[如何設定 HTTP 接收位置的 IIS](../core/how-to-configure-iis-for-an-http-receive-location.md)。  
  
## <a name="running-the-sample"></a>執行範例  
 使用正確經費支出報表執行範例之前，請依照下列程序確認「沒有錯誤」案例的範例會正確執行。  
  
#### <a name="to-verify-that-the-no-errors-case-sample-works-correctly"></a>若要確認沒有錯誤案例的範例會正確執行  
  
1.  開啟 InfoPath 表單**Expense Report-John Doe.xml**。 查看**部門**欄位中的表單。 這個欄位應該設定為 [Marketing]。  
  
2.  在 InfoPath 視窗左上角，按一下**送出**或按一下**重新提交經費支出報表**。 等候確認視窗表示經費支出報表已成功重新提交。  
  
     -或-  
  
     複製並貼到這個檔案**ExpenseReportIn**資料夾。  
  
3.  您應該會看到新的檔案放入**ExpenseReportOut**資料夾。 這個檔案是上面步驟中所提交的相同經費支出報表。  
  
 確認「沒有錯誤」案例之後，請依照下列程序使用不正確的經費支出報表執行範例，以觸發錯誤處理功能。  
  
#### <a name="to-trigger-error-handling"></a>若要觸發錯誤處理  
  
1.  開啟 InfoPath 表單**Invalid Expense Report-John Doe.xml**。 查看**部門**欄位中的表單。 這個欄位是設定為某個無效值。  
  
2.  在 InfoPath 視窗左上角，按一下**送出**。 等候確認視窗表示經費支出報表已成功重新提交。  
  
     -或-  
  
     複製並貼到這個檔案**ExpenseReportIn**資料夾。  
  
3.  您應該會看到新的檔案，稱為**ErrorReport_\<***日期*_*時間***\>.xml**放入**ExpenseReportOut**資料夾。  
  
     開啟這個檔案，觀察這是上一個步驟中所提交，但是開頭包含錯誤資訊的經費支出報表。  
  
4.  錯誤的部門值取代為"Marketing"，然後**送出**InfoPath 視窗左上角。  
  
     -或-  
  
     複製並貼到這個檔案**ResubmittedReportIn**資料夾。  
  
5.  您應該會看到新的檔案中建立**ExpenseReportOut**資料夾。 這個檔案是更正後重新提交至伺服器的經費支出報表。  
  
## <a name="see-also"></a>請參閱  
 [使用失敗的訊息路由](../core/using-failed-message-routing.md)   
 [傳訊 (BizTalk Server Samples 資料夾)](../core/messaging-biztalk-server-samples-folder.md)