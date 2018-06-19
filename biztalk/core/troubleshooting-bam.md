---
title: 疑難排解 BAM |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e63299a8-5c74-4337-ba20-3213e0c6ea1f
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12cd08ae9bee686946c8db14039504411506035f
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
ms.locfileid: "29710253"
---
# <a name="troubleshooting-bam"></a>疑難排解 BAM
本主題提供使用商務活動監控 (BAM) 時，可能會遇到的資訊可協助您疑難排解問題。  
  
## <a name="bam-deployment-failed"></a>BAM 部署失敗  
 如果您嘗試部署 BAM 定義，其中包含即時彙總 (RTA) 無法使用 SQL Server Analysis Services 時，Bm.exe 命令會顯示下列訊息︰  
  
 錯誤︰ BAM 部署失敗。 無法建立連接。 請確定該伺服器正在執行。 無法建立沒有連接，因為目標電腦主動拒絕連線 *\<IP 位址\>*。  
  
 這是因為 SQL Server Analysis Services 必須已安裝和設定，且必須執行，才能部署 BAM 定義，其中包含 RTA。  
  
## <a name="cannot-refresh-the-live-data-workbook"></a>無法重新整理的即時資料活頁簿  
 當您嘗試更新即時資料活頁簿中的資料時，Microsoft Office Excel 可能會顯示下列錯誤︰  
  
 `XML for Analysis parser: The CurrentCatalog XML/A property was not specified.`  
  
 這是因為 BAM 增益集尚未加入至 Excel。  
  
#### <a name="add-the-bam-add-in-to-excel"></a>將加入至 Excel 的 BAM 增益集  
  
1.  按一下  **啟動**, ，指向  **所有程式**, ，指向  **Microsoft Office**, ，然後按一下  **Microsoft Office Excel**。  
  
2.  按一下  **Microsoft Office 按鈕**, ，然後按一下  **Excel 選項**。  
  
3.  在 **Excel 選項** 對話方塊中，按一下  **增益集**。  
  
4.  在 **增益集** ] 窗格中，按一下 [ **移**。  
  
5.  在 **增益集** 對話方塊中，選取 **商務活動監控** 核取方塊，，然後按一下  **確定**。  
  
     ![新增 &#45; 增益集 對話方塊](../core/media/addins.gif "增益集")  
  
## <a name="errorobject-library-invalid-or-contains-references-to-object-definitions-that-could-not-be-found-with-bam-excel-add-in-in-office"></a>Office 的 BAM Excel 增益集發生錯誤：「物件程式庫無效或包含找不到的物件定義參照」。  
 升級為 Microsoft Excel 後，嘗試使用 BAM Excel 增益集時，可能會發生這個錯誤。  
  
 **解決方式︰** 因為 BAM 增益集使用了 ActiveX 控制項，您必須刪除下列目錄中的快取的.exd 的檔案︰  
  
-   C:\Documents and Settings\\< 使用者名稱\>\Application Data\Microsoft\Forms  
  
-   C:\Documents and Settings\\< 使用者名稱\>\AppData\Local\Temp\VBE  
  
## <a name="bam-portal-cannot-connect"></a>BAM 入口網站無法連線  
系統管理員身分執行 BAM 入口網站。  
  
#### <a name="run-the-bam-portal"></a>執行 BAM 入口網站
  
1.  按一下  **啟動**, ，指向  **所有程式**, ，以滑鼠右鍵按一下 **Internet Explorer**, ，然後按一下  **系統管理員身分執行**。  
  
2.  在 **使用者帳戶控制** 對話方塊中，按一下  **繼續**。  
  
3.  在 Internet Explorer 網址列中，輸入`http://<server>/BAM`，其中*\<伺服器\>* 執行 BAM 入口網站之電腦的名稱。  
  
## <a name="bam-portal-does-not-work-if-invalid-users-are-granted-permissions"></a>無效的使用者權限，如果 BAM 入口網站無法運作  
 如果從 AD 移除 AD 使用者擁有 BAM 檢視權限，則 BAM 入口網站未正確載入的任何使用者 （除了 DBO)。  
  
 若要解決此問題，請從對應的 bam_ {viewname} 檢視安全性角色中移除無效的使用者。  
  
## <a name="cannot-export-or-import-a-bam-definition-to-localhost"></a>無法匯出或匯入 BAM 定義為 localhost  
 當您匯出 BAM 定義為 XML 時，您就會看到下列錯誤訊息，如果您嘗試將匯出至 localhost:  
  
 `The system cannot find the path specified.`  
  
 不支援匯出 BAM 定義為 localhost。 同樣地，不支援從 localhost 匯入 BAM 定義。  
  
## <a name="alerts-do-not-work-after-upgrading-sql-server-editions"></a>升級 SQL Server 版本之後無法運作警示  
 如果您已經從一個版本的 SQL Server 升級到另一個版本 （例如，從 Enterprise 版本的 Standard Edition)，BAM 警示將不會重新啟動。 若要修正這個問題，請刪除 BAM 警示，和重新建立它們，或升級 SQL Server Notification Service。  
  
#### <a name="upgrade-the-sql-server-notification-service"></a>升級 SQL Server Notification 服務  
  
1.  按一下  **啟動**, ，按一下  **所有程式**, ，按一下  **Microsoft SQL Server 2005**, ，然後按一下  **通知服務的命令提示字元**。  
  
2.  在命令提示字元中輸入下列命令︰  
  
     `nscontrol.exe upgrade -name <instanceName>`  
  
## <a name="objectdisposedexception-exception"></a>ObjectDisposedException 例外狀況  
 如果您的應用程式使用 BAM WF 3.5 攔截器，您可能會收到下列錯誤訊息︰ **System.ObjectDisposedException︰ 無法存取已處置的物件**。 如需有關此錯誤訊息的詳細資訊，請參閱[ObjectDisposedException 例外狀況](https://support.microsoft.com/help/960754)。 

若要解決此問題，請安裝[hotfix 960754](https://support.microsoft.com/help/960754)。 
  
## <a name="workbook-has-lost-its-vba-project-activex-controls-and-other-programmability-related-features"></a>活頁簿已遺失 VBA 專案、 ActiveX 控制項和其他相關的可程式性功能  
 當嘗試在 Microsoft Excel 中使用 BAM.xla 時，可能會出現下列錯誤︰  
  
 `This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.`  
  
 若要解決此問題，請安裝 **應用程式的 Visual Basic** 底下 **Office 共用功能** 與 Microsoft Office。  
  
## <a name="pivot-table-fails-to-get-the-data"></a>無法取得資料的樞紐分析表  
 您有權限以存取 BAM 資料庫，以及角色和權限所部署的檢視。 [活動搜尋] 頁面如預期般運作，而且您看得到資料。 但是，樞紐分析表中顯示下列錯誤：  
  
```  
Failed to get data.  If available, errors returned from the provider are listed below.  
* The following system error occurred:  No connection could be made because the target machine actively refused it.  
```  
  
 若要解決此問題，請分別新增下列 DNS 設定：  
  
1.  按一下  **啟動** 並移至 **控制台**。  
  
2.  按一下  **網路和網際網路** 然後按一下  **網路連線**。  
  
3.  以滑鼠右鍵按一下網路連線 （例如 區域連線），然後選取 **屬性**。  
  
4.  在 **區域連線** 頁面上，選取 **網際網路通訊協定第 4 版 (TCP/IPv4)**, ，然後按一下 **屬性**。  
  
5.  按一下 **[進階]**。 在 **進階 TCP/IP 設定** 頁面上，按一下 **DNS**  索引標籤。  
  
6.  選取 **附加這些 DNS 尾碼** ，然後新增必要的 DNS 尾碼。  
  
7.  按一下  **確定** 並關閉所有開啟的視窗。  
  
## <a name="pivot-table-view-shows-all-values-as-0"></a>樞紐分析表檢視將所有的值都顯示為 “0”  
 當您部署 BAM 入口網站時，[活動搜尋] 頁面會顯示預期的結果。 但是，樞紐分析表檢視卻將所有的值都顯示為 “0”。 顯示的錯誤如下：  
  
```  
Failed to get data.  If available, errors returned from the provider are listed below.  
* Safety settings on this machine prohibit accessing a data source on another domain.  
```  
  
 若要解決此問題，請將網站新增至區域中，如下所示：  
  
1.  在 Internet Explorer 視窗中，按一下  **工具**, ，然後按一下  **網際網路選項**。 按一下  **安全性** 索引標籤，然後選取 **信任的網站** 區域。  
  
2.  按一下  **自訂層級** 設定區域的安全性層級。  
  
3.  在 **設定** ] 頁面的 [ **跨網域存取資料來源** 選項，請按一下 **提示**。 您將會在有元件需要此權限時收到提示。  
  
## <a name="see-also"></a>另請參閱  
 [使用商務活動監控](../core/using-business-activity-monitoring.md)