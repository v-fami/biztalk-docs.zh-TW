---
title: 步驟 1： 使用 Oracle E-business 配接器來建立和發佈的 WCF 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cd76f6f-600f-4eb5-8eee-8f3604d0fef4
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ac179adbc2e49b767ecae2a68676c5692dcd385
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967796"
---
# <a name="step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service"></a>步驟 1： 使用 Oracle E-business 配接器來建立和發佈的 WCF 服務
![步驟 4 之 1](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")  
  
 **若要完成的時間：** 15 分鐘  
  
 **目標：** 您可以使用[!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)]產生從 Oracle E-business Suite 成品，例如網際網路資訊服務 (IIS) 或 Windows Process Activation Service (WAS) 裝載環境中可以裝載 WCF 服務。 本主題示範如何使用精靈來產生 WCF 服務檔案。  
  
## <a name="prerequisites"></a>必要條件  
 執行精靈之前，安裝下列項目：  
  
-   [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]不論是透過**完成**選項或**自訂**選項 (並選擇**工具**內此選項)。 這會安裝[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]範本[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]。  
  
-   [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]從[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。  
  
 如需有關這些必要條件的詳細資訊，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝指南。 在一般安裝安裝指南 》\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。  
  
> [!NOTE]
>  您也必須執行 create_apps_artifacts.sql 指令碼來建立 Microsoft Office SharePoint Server 範例隨附**MS_SAMPLE_EMPLOYEE**介面中的資料表**應用程式物件程式庫**應用程式。 此介面資料表會用於本教學課程。  
  

  
##  <a name="Create_Service"></a>建立 Oracle E-business 成品之操作的 WCF 服務  
 本節提供建立 WCF 服務 MS_SAMPLE 員工介面資料表的 Select 作業的步驟。  
  
#### <a name="to-create-a-wcf-service-for-the-select-operation-on-the-mssample-employee-interface-table"></a>若要建立 MS_SAMPLE 員工介面資料表的 Select 作業的 WCF 服務  
  
1.  啟動[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，然後建立專案。  
  
2.  在**新專案**對話方塊中，從**專案類型**窗格中，選取**Visual C#**。 從**範本**窗格中，選取**WCF 配接器服務**。  
  
     或者，從**專案類型**] 窗格中，展開 [ **Visual C#**，然後選取**Web**。 從**範本**窗格中，選取**WCF 配接器服務**。  
  
     ![新增專案對話方塊](../../adapters-and-accelerators/adapter-oracle-ebs/media/01-new-project.gif "01_New_Project")  
  
    > [!NOTE]
    >  如果您已安裝[!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]與 Web 程式開發的元件， **WCF 配接器服務**範本也會提供**新網站**選項 (**檔案** > **新** > **網站**)。  
    >   
    >  不過，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]僅支援檔案系統所建立的網站。 因此，在新的網站 對話方塊中建立的網站，您必須按一下檔案系統位置 清單中。  
  
3.  指定的名稱和位置的方案，然後再按一下**確定**。 WCF[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]啟動。  
  
4.  在 歡迎使用 頁面上，按一下 **下一步**。  
  
5.  選擇 [作業] 頁面上指定的連接字串連接到 Oracle E-business Suite。 若要這樣做：  
  
    1.  在**選取繫結**清單中，按一下**oracleEBSBinding**，然後按一下 **設定**。  
  
    2.  在**設定配接器**對話方塊中，按一下 [**繫結屬性**] 索引標籤。  
  
        1.  在下**一般**類別，如**ClientCredentialType**繫結屬性中，選取**EBusiness**。  
  
        2.  在下**OracleEBS**分類中，指定適當的值**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。 在此情況下，您需要提供資料庫認證**OracleUserName**和**OraclePassword**繫結屬性。  
  
        3.  下**中繼資料**類別，如**EnableSafeTyping**繫結屬性中，選取**True**。 如果擷取的日期資料行的值，我們建議您將設定**EnableSafeTyping**內容繫結至**True**產生中繼資料時。  
  
    3.  按一下**URI 屬性**索引標籤，然後再指定連線參數的值。 如需有關連線 URI 的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[建立 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)。  
  
    4.  按一下**安全性** 索引標籤，然後在**用戶端認證類型**清單中，選取**Username**。 指定有效的 Oracle E-business Suite 使用者名稱和密碼以連接到 Oracle E-business Suite。  
  
    5.  按一下**確定**以關閉 [設定配接器] 對話方塊中，然後按一下**連接**。 Visual Studio 已成功建立與 Oracle E-business Suite 連線之後，連線狀態會顯示為**Connected**。 您也可以查看會顯示在 [選擇作業] 頁面上的 Oracle E-business Suite 中繼資料。  
  
6.  在選擇 [作業] 頁面中**選取的合約型別**清單中，按一下**用戶端 （輸出作業）**。  
  
7.  在**選取類別目錄**方塊中，瀏覽至 MS_SAMPLE_EMPLOYEE 介面資料表中的應用程式物件程式庫應用程式。 如需瀏覽至配接器中的成品，請參閱[瀏覽、 搜尋及擷取 Oracle E-business 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。  
  
8.  在**可用的類別和作業**方塊中，選取**選取**作業，然後再按一下**新增**。 選取的作業加入至**加入的類別和作業**方塊。  
  
     ![新增選取作業](../../adapters-and-accelerators/adapter-oracle-ebs/media/02-msb-gui.gif "02_MSB_GUI")  
  
    > [!NOTE]
    >  您可以加入多個作業的每個成品。 您也可以加入不同的 Oracle E-business Suite 成品的作業。 例如，您可以加入介面資料表的一項作業，另一個用於並行處理的程式。 此外，您可以藉由搜尋運算式中指定萬用字元搜尋針對特定作業。 如需支援的特殊字元和節點層級，您可以搜尋作業的詳細資訊，請參閱[搜尋 Oracle E-business Suite 作業](../../adapters-and-accelerators/adapter-oracle-ebs/search-for-oracle-e-business-suite-operations.md)。  
  
9. 在 [選擇作業] 頁面上按一下**下一步**。  
  
10. 在設定服務與端點行為 頁面上，指定值來設定服務與端點行為。  
  
    1.  在**服務行為組態**方塊中，指定下列值：  
  
        |屬性|指定的值|  
        |----------------------|-----------------------|  
        |EnableMetadataExchange|將此設**True**建立中繼資料交換端點。 由這個設定設為**True**，您會讓服務中繼資料可供使用標準化的通訊協定，例如 WS 中繼資料交換 (MEX) 和 HTTP/GET 要求。 預設值是**False**。|  
        |IncludeExceptionDetailsinFault|將此設**True**在傳回至用戶端以進行偵錯的 SOAP 錯誤的詳細資料中包含 managed 例外狀況資訊。 預設值是**False**。|  
        |名稱|服務行為組態名稱。 此教學課程中，輸入**customServiceBehavior**。|  
        |UseServiceCertificate|指定您是否想要使用 WCF 的訊息層級的安全性模式。 預設值是**True**。 此教學課程中，您必須設定為**False**。|  
  
        > [!NOTE]
        >  因為我們不使用服務憑證，此教學課程中，您不需要提供值**FindValue**， **StoreLocation**， **StoreName**，和**X509FindType**屬性。 有關憑證和相關聯的屬性的詳細資訊，請參閱 < X509ClientCertificateCredentialsElement 屬性 >，網址[http://go.microsoft.com/fwlink/?LinkId=103771](http://go.microsoft.com/fwlink/?LinkId=103771)。  
  
    2.  在**端點行為組態**方塊中，指定下列值：  
  
        |屬性|指定的值|  
        |----------------------|-----------------------|  
        |驗證類型|Microsoft Office SharePoint Server 來取用 WCF 服務，您應該設定為**HTTPUserNamePassword**。 這可讓用戶端的 HTTP 標頭中指定使用者名稱和密碼。|  
        |名稱|指定端點行為組態名稱。 此教學課程中，輸入**customEndpointBehavior**。|  
        |UsernameHeader|使用者名稱標頭的名稱。 此範例中，指定**MyUserHeader**。 HTTP 標頭的詳細資訊，請參閱 < 支援的自訂 HTTP 和 SOAP 標頭 >，網址[http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692)。 **注意：** 您必須指定此屬性的值，如果**驗證類型**設**HTTPUserNamePassword**。 如果**驗證類型**設**自動**，這是選擇性屬性。|  
        |PasswordHeader|密碼標頭的名稱。 此範例中，指定**MyPassHeader**。 HTTP 標頭的詳細資訊，請參閱 < 支援的自訂 HTTP 和 SOAP 標頭 >，網址[http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692)。 **注意：** 您必須指定此屬性的值，如果**驗證類型**設**HTTPUserNamePassword**。 如果**驗證類型**設**自動**，這是選擇性屬性。|  
  
     下圖顯示 [設定服務與端點行為] 頁面，以指定的值。  
  
     ![設定服務與端點行為 頁面](../../adapters-and-accelerators/adapter-oracle-ebs/media/03-service-and-endpoint-behavior.gif "03_Service_and_EndPoint_Behavior")  
  
11. 在 設定服務與端點行為 頁面上，按一下 **下一步**。  
  
12. 在 設定服務端點繫結和位址的頁面上，**選取要設定的合約**會顯示您所設定的成品 (MS_SAMPLE_EMPLOYEE)。 **選取合約之作業**方塊會顯示**選取**您選取的成品，選擇 [作業] 頁面上的作業。  
  
13. 在**設定的位址和合約繫結**方塊中，指定下列值：  
  
    |屬性|指定的值|  
    |----------------------|-----------------------|  
    |繫結組態|此精靈只支援基本 HTTP 繫結。 因此，繫結設定欄位所自動填入*System.ServiceModel.Configuration.BasicHttpBindingElement*。<br /><br /> 按一下省略符號按鈕 **（...）** 變更 HTTP 繫結的屬性。 若要使用安全通訊通道，您都必須設定**模式**屬性**傳輸**。 精靈會設定的預設值為**模式**屬性做為**傳輸**。<br /><br /> 公開的其他繫結的詳細資訊，請參閱 < BasicHttpBindingElement 成員 >，網址[http://go.microsoft.com/fwlink/?LinkId=103773](http://go.microsoft.com/fwlink/?LinkId=103773)。|  
    |端點名稱|指定合約的端點名稱。|  
  
     此頁面上的其他欄位會自動填入您在先前頁面中指定的值。  
  
     按一下 **[套用]**。  
  
    > [!NOTE]
    >  如果您未指定任何值在此頁面上，預設值會接受所有合約。  
  
     下圖顯示的設定服務端點繫結和位址 頁面上以指定的值。  
  
     ![設定服務端點繫結與位址](../../adapters-and-accelerators/adapter-oracle-ebs/media/04-service-endpoint-binding.gif "04_Service_Endpoint_Binding")  
  
14. 在 設定服務端點繫結和位址的頁面上，按一下 **下一步**。  [摘要] 頁面會列出樹狀結構的 Oracle E-business Suite 成品以及成品所選取的作業。  
  
15. 檢閱 [摘要]，然後按一下**完成**。  
  
16. 精靈會建立 WCF 服務，並加入下列檔案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案：  
  
    1.  .svc 檔案。 這是 WCF 服務檔案。 精靈會產生一個檔案，針對每個合約。  
  
    2.  Web.config 檔案。  
  
    3.  服務程式碼 （.cs 檔案）  
  
##  <a name="cs"></a>修改.cs 檔案中  
 當您建立服務，以利用 Oracle E-business Suite 成品使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]而且想要使用商務資料清單網頁組件，在 Microsoft Office SharePoint Server 中，您應該提供完整的篩選子句開頭的 WHERE 子句. 例如，如果您想要搜尋名稱為"John"的員工，您需要提供下列篩選子句中商務資料清單網頁組件：  
  
```  
where NAME like ‘JOHN’  
```  
  
 不過，如果您想要只提供名稱做為輸入篩選子句而不實際一提的整個篩選子句的使用者，您可以加入程式碼在.cs 檔案中，以修改來自商務資料清單網頁組件，在 Microsoft Office 中的篩選子句 將它傳遞至 Oracle E-business WHERE 子句格式中的 SharePoint 伺服器。  
  
 例如，在此教學課程中，如果您想讓使用者輸入商務資料清單 Web 組件中 Microsoft Office SharePoint Server 中的員工姓名和擷取記錄的員工，您可以加入下列程式碼在.cs 檔案中：  
  
```  
SelectResponse InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE.Select(SelectRequest request)   
{  
     request.FILTER = "where NAME like '" + request.FILTER + "'"; // The code to avoid the users from specifying the WHERE clause in the filter from Business Data List Web Part.  
     return base.Channel.Select(request);  
}  
```  
  
##  <a name="Publish"></a>發佈 WCF 服務  
 請確定已為 IIS 啟用 SSL。 如需有關如何啟用 iis 的 SSL 的指示，請參閱[http://go.microsoft.com/fwlink/?LinkId=197170](http://go.microsoft.com/fwlink/?LinkId=197170)。  
  
 若要發佈的 WCF 服務：  
  
1.  以滑鼠右鍵按一下方案總管 中的專案，然後按一下**發行**。  
  
2.  在**發行 Web**對話方塊方塊中，指定 WCF 服務的 URL。 例如：  
  
    ```  
    https://<COMPUTER_NAME>:<PORT_NUMBER>/MS_SAMPLE_EMPLOYEE/  
    ```  
  
    > [!NOTE]
    >  您必須發佈 WCF 服務 SSL 已啟用的位置。 換句話說中的值**目標位置**方塊必須以"https://"開頭。 因為使用者認證會在 HTTP 標頭中傳遞，精靈會自動設定配接器的繫結行為，若要使用 「 傳輸 」 做為安全性模式，表示 SSL 加密。 您當然可以返回，並編輯 web.config 檔案，以變更的值**\<安全性模式\>** 參數，但使用 SSL 時，一定會更好的選項有純傳輸機密資訊HTTP 標頭中的文字。  
  
3.  從**複製**方塊中，按一下**所有專案檔**。  
  
4.  按一下 [發行]。  
  
5.  請確認已成功發行 WCF 服務。  
  
    1.  啟動 IIS Microsoft Management Console。 按一下**啟動**，指向 **系統管理工具**，然後按一下 **網際網路資訊服務 (IIS) 管理員**。  
  
    2.  瀏覽至您用來發行服務的節點。 如**MS_SAMPLE_EMPLOYEE**服務，請瀏覽至**Internet Information Services** > **\<電腦名稱\>**  > **Web Sites** > **Default Web Site** > **MS_SAMPLE_EMPLOYEE**。  
  
    3.  在右窗格中，InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE.svc 檔案，以滑鼠右鍵按一下，然後按一下 **瀏覽**。  
  
    4.  擷取 WSDL 的 URL 和一同顯示網頁。 您可能想要測試中繼資料擷取使用**svcutil**命令。 比方說，是擷取 MS_SAMPLE_EMPLOYEE 服務中繼資料的命令：  
  
        ```  
        svcutil.exe https://<COMPUTER_NAME>:<PORT_NUMBER>/MS_SAMPLE_EMPLOYEE/InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE.svc?wsdl  
  
        ```  
  
## <a name="next-step"></a>下一個步驟  
 若要建立 Oracle E-business Suite 成品的應用程式定義檔，請使用商務資料目錄定義編輯器。 如需指示，請參閱[步驟 2： 建立應用程式定義檔的 Oracle E-business Suite 成品](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md)。 應用程式定義檔識別 LOB 資料的儲存位置，以及儲存它的格式。  
  
## <a name="see-also"></a>請參閱  
 [教學課程： 從 SharePoint 網站上的 Oracle E-business Suite 中呈現的資料](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)