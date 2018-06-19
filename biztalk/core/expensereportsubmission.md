---
title: ExpenseReportSubmission |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
ms.assetid: d0bacab3-7092-44b8-a1c6-6f574a2db8bd
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c450e2e39f2498722f9eb8d09430294927cb05f8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969764"
---
# <a name="expensereportsubmission"></a>ExpenseReportSubmission
ExpenseReportSubmission 範例說明如何透過如 Microsoft Excel 的多功能用戶端，將文件提交到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。  
  
 多功能的用戶端可以讓您在用戶端上執行資料驗證和初步計算等動作。 這有助於降低與後端伺服器的互動，相當適合只有低頻寬連線的情形。  
  
## <a name="prerequisites"></a>必要條件  
 您必須確定已設定和啟用您的開發環境來使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web 服務。 如需詳細資訊，請參閱[啟用 Web 服務](../core/enabling-web-services.md)。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例說明如何使用下列步驟，直接從 Excel 將費用報表提交到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]：  
  
1.  使用者執行 Excel 試算表中提供的手動範例步驟。  
  
2.  試算表中的巨集程式碼會將試算表資料轉換成可延伸標記語言 (XML) 格式，並且使用 HTTP 連線將 XML 訊息提交到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
3.  執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的電腦會擷取 XML 費用報表訊息、使用提供的結構描述驗證它的格式，然後將它放置到不同的資料夾。  
  
4.  在實際情況中 (這超出此範例的說明範圍)，其他如「企業資源規劃」(ERP) 系統的應用程式會擷取試算表檔案，並進行進一步的處理。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*範例路徑*\>\AdaptersUsage\ExpenseReportSubmission\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|Cleanup.bat|從全域組件快取 (GAC) 解除部署並移除組件；移除傳送和接收埠；視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|ExpenseReport.15.3.xls|Excel 試算表，含有費用報表配置、關聯的巨集以及可叫用巨集的按鈕。|  
|MessageExample.xml|XML 費用報表格式的範例。|  
|Setup.bat|建置並初始化此範例。|  
|在 \BTSExpenseDemo 資料夾中：<br /><br /> AssemblyInfo.cs、<br /><br /> BTSExpenseDemo.btproj、<br /><br /> BTSExpenseDemo.sln|提供此範例的專案、解決方案和關聯檔案。|  
|在 \BTSExpenseDemo 資料夾中：<br /><br /> BTSExpenseDemoBinding.xml|用於自動化安裝，例如連接埠繫結。|  
|在 \BTSExpenseDemo 資料夾中：<br /><br /> BTSExpenseOrchestration.odx|提供此範例的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。|  
|在 \BTSExpenseDemo 資料夾中：<br /><br /> SchemaExpenseReport.xsd|提供 XML 費用報表格式的結構描述。|  
  
### <a name="to-build-and-initialize-this-sample"></a>若要建置並初始化這個範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*\>\AdaptersUsage\ExpenseReportSubmission  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   編譯此範例的 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案，並部署產生的組件。  
  
    -   建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送和接收埠。  
  
        > [!NOTE]
        >  此範例會在建立和繫結連接埠時顯示下列警告：  
        >   
        >  `Warning: Receive handler not specified for receive location "BTSExpenseReceiveLocation"; updating with first receive handler with matching transport type.`  
        >   
        >  `Warning: Host not specified for orchestration "Microsoft.Samples.BizTalk.BTSExpenseDemo.BTSOrchestration"; updating with first available host`。  
        >   
        >  您可以安全地忽略這些警告。 (繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。  
  
    -   啟用接收位置並啟動傳送埠。  
  
    -   設定 IIS。  
  
    -   繫結並啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。  
  
    -   將 HTTP 位址設定至 Excel 試算表預期的位置。  
  
    > [!NOTE]
    >  如需 BizTalk ISAPI 篩選器的詳細資訊，請參閱[如何設定 HTTP 接收位置的 IIS](../core/how-to-configure-iis-for-an-http-receive-location.md)。  
  
    > [!NOTE]
    >  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。  
  
    > [!NOTE]
    >  如果您在此範例中選擇開啟並建置專案，而不執行檔案 Setup.bat，必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 請使用這個金鑰組來簽署產生的組件。  
  
    > [!NOTE]
    >  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
3.  setup.bat 檔會設定此範例的虛擬目錄，以在與預設網站關聯的 IIS 應用程式集區中執行。  若要設定讓此範例中的使用者內容下執行的虛擬目錄**BizTalk Isolated Host Users**和**IIS_WPG**使用者群組，您應該設定執行新的虛擬目錄IIS 應用程式集區。  請依照下列步驟執行，將虛擬目錄設定為在新的 IIS 應用程式集區中執行：  
  
    > [!NOTE]
    >  如果您已經為其他 SDK 範例建立新的應用程式集區，則可以繼續執行下面最後一項步驟。  
  
    1.  按一下**啟動**，指向 **程式**，指向 **系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**.  
  
    2.  在**網際網路資訊服務 (IIS) 管理員**，瀏覽至**應用程式集區**資料夾。  
  
    3.  以滑鼠右鍵按一下**應用程式集區**資料夾，然後按一下**新增**，**應用程式集區...**  
  
    4.  輸入的名稱**應用程式集區識別碼：** （例如 biztalksdksamples），確認**新應用程式集區使用預設設定**選項已選取，然後按一下**確定**至建立新的應用程式集區。  
  
    5.  以滑鼠右鍵按一下新的應用程式集區，然後按一下 **屬性**。  
  
    6.  按一下**識別** 索引標籤的 屬性 對話方塊並變更這個應用程式集區執行使用者為成員的身分識別**BizTalk Isolated Host Users**使用者群組。  此使用者也應該屬於本機**IIS_WPG**使用者群組。  
  
    7.  設定這個 SDK 範例的虛擬目錄為在新的應用程式集區下執行。 **應用程式集區：** 設定位在**虛擬目錄**] 索引標籤的 [虛擬目錄的 [內容] 對話方塊。 此範例為建立的虛擬目錄**ExpenseReportSubmission**。  
  
4.  為 HTTPReceive.dll 將 Web 服務延伸模組新增至 IIS  
  
    1.  在**網際網路資訊服務 (IIS) 管理員**，瀏覽至**網頁服務延伸**資料夾。  
  
    2.  以滑鼠右鍵按一下**網頁服務延伸**資料夾，然後選取**新增新的 Web 服務延伸**顯示**新增網頁服務延伸** 對話方塊。  
  
    3.  輸入**ExpenseReportSubmission**如**延伸模組名稱：**  
  
    4.  按一下**新增**顯示**Add file**  對話方塊。  
  
    5.  按一下**瀏覽**顯示**開啟**對話方塊方塊中，並瀏覽至 *\<BizTalk Server 安裝資料夾\>* \HttpReceive\BTSHTTPReceive.dll，然後按一下**開啟**，然後按一下 **確定**。  
  
    6.  啟用選項，**設定延伸狀態成允許**按一下**確定**。  
  
## <a name="running-this-sample"></a>執行此範例  
 使用下列程序以執行 ExpenseReportSubmission 範例。  
  
> [!NOTE]
>  如果您使用 Microsoft Excel 的增強型安全性功能，試算表中的巨集可能會被停用。 如需有關如何執行來自信任來源的未簽署巨集的資訊，請參閱 Excel 所提供的指示。  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  開啟此範例所隨附的 Excel 檔 ExpenseReport.15.3.xls。  
  
2.  在試算表中變更範例資料，但不要變更它的格式 (選擇性)。  
  
3.  在 excel 中，按一下 **啟動**以執行本機計算。  
  
     從按鈕的文字變更**啟動**至**送出**。  
  
4.  在 excel 中，按一下 **送出**。  
  
5.  檢查所提交訊息的文字、資料表上背景為黃色的結果 (儲存格 C7)，以及右下方實際的傳回程式碼和文字描述 (儲存格 G23)。  
  
     如果提交失敗，請再試一次， 並請參閱＜註解＞一節中的疑難排解表格。  
  
## <a name="comments"></a>註解  
 例如現場銷售人員配備的舊版 Microsoft Windows 不支援 .NET Framework，且不具有升級為最新版 Windows 的條件，就可能會發生這樣的情況。  
  
 此範例展示的重要功能如下：  
  
-   透過多功能的用戶端 (非 .NET) 提交  
  
-   Microsoft Office 整合  
  
-   HTTP 接收連線  
  
-   簡易的協調流程  
  
-   File adapter (FILE 配接器)  
  
 下表說明一些可能發生的提交錯誤及其解決方案。  
  
|HTTP 錯誤碼|可能的動作|  
|---------------------|---------------------|  
|401 未經授權|允許匿名存取虛擬目錄。|  
|503 服務無法使用 (以及大部分在 400 和 500 範圍內的其他 HTTP 代碼)|確認主機正在執行，且服務已部署完成、繫結至正確的連接埠並已啟動。|  
  
## <a name="see-also"></a>請參閱  
 [配接器範例 - 用法](../core/adapter-samples-usage.md)