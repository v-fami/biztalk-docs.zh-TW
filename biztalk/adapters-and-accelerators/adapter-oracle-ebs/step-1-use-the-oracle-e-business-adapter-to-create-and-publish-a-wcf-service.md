---
title: 步驟 1： 使用 Oracle E-business 配接器來建立及發佈 WCF 服務 |Microsoft Docs
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
ms.openlocfilehash: 75bbbb57b633475d9973d187d61d6e698f6cadb2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981023"
---
# <a name="step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service"></a>步驟 1： 使用 Oracle E-business 配接器來建立及發佈 WCF 服務
![步驟 4 之 1](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")  
  
 **若要完成的時間：** 15 分鐘  
  
 **目標：** 您可以使用[!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)]可以裝載在例如 Internet Information Services (IIS) 或 Windows Process Activation Service (WAS) 裝載環境中 Oracle E-business Suite 成品從產生的 WCF 服務。 本主題示範如何使用精靈來產生 WCF 服務檔案。  
  
## <a name="prerequisites"></a>必要條件  
 執行精靈之前，安裝下列項目：  
  
- [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] 不論是使用**完成**選項或**自訂**選項 (，然後選擇**工具**內此選項)。 這會安裝[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]範本[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]。  
  
- [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] 從[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。  
  
  如需有關這些必要條件的詳細資訊，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝指南。 安裝指南通常安裝在\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。  
  
> [!NOTE]
>  您也必須執行 Microsoft Office SharePoint Server 的範例，以建立與所提供的 create_apps_artifacts.sql 指令碼**MS_SAMPLE_EMPLOYEE**中的介面資料表**應用程式物件程式庫**應用程式。 本教學課程會使用此介面資料表。  
  

  
##  <a name="Create_Service"></a> 建立 Oracle E-business 成品的作業的 WCF 服務  
 本節提供建立 WCF 服務 MS_SAMPLE 員工介面資料表的選取作業的步驟。  
  
#### <a name="to-create-a-wcf-service-for-the-select-operation-on-the-mssample-employee-interface-table"></a>若要建立 MS_SAMPLE 員工介面資料表的選取作業的 WCF 服務  
  
1. 啟動[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，然後建立專案。  
  
2. 在 [**新的專案**] 對話方塊中，從**專案類型**窗格中，選取**Visual C#**。 從**範本**窗格中，選取**WCF 配接器服務**。  
  
    或者，從**專案類型**窗格中，展開**Visual C#**，然後選取**Web**。 從**範本**窗格中，選取**WCF 配接器服務**。  
  
    ![[新增專案] 對話方塊](../../adapters-and-accelerators/adapter-oracle-ebs/media/01-new-project.gif "01_New_Project")  
  
   > [!NOTE]
   >  如果您已安裝[!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]與網頁程式開發的元件**WCF 配接器服務**範本也會提供**新的網站**選項 (**檔案** > **新** > **網站**)。  
   > 
   >  不過，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]只支援 檔案系統所建立的網站。 因此，在建立網站，在新的網站 對話方塊中，您必須按一下檔案系統位置 清單中。  
  
3. 指定的名稱和方案和位置，然後按一下**確定**。 WCF[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]啟動。  
  
4. 在 歡迎使用 頁面上，按一下**下一步**。  
  
5. 在選擇 [作業] 頁面中，指定連接字串來連接到 Oracle E-business Suite。 若要這樣做：  
  
   1. 在 **選取的繫結**清單中，按一下**oracleEBSBinding**，然後按一下**設定**。  
  
   2. 在 **設定介面卡** 對話方塊中，按一下**繫結屬性** 索引標籤。  
  
      1.  底下**一般**類別，如**ClientCredentialType**繫結屬性中，選取**EBusiness**。  
  
      2.  底下**OracleEBS**分類中，指定適當的值，如**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。 在此情況下，您需要提供資料庫認證**OracleUserName**並**OraclePassword**繫結屬性。  
  
      3.  底下**中繼資料**類別，如**EnableSafeTyping**繫結屬性中，選取 **，則為 True**。 如果您要擷取的日期資料行的值，我們建議您設定**EnableSafeTyping**屬性來繫結 **，則為 True**時產生的中繼資料。  
  
   3. 按一下  **URI 屬性**索引標籤，然後指定 連接參數的值。 如需有關連線 URI 的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 建立 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)。  
  
   4. 按一下 [**安全性**] 索引標籤，然後在**用戶端認證類型**清單中，選取**Username**。 指定有效的 Oracle E-business Suite 的使用者名稱和密碼以連接到 Oracle E-business Suite。  
  
   5. 按一下  **確定**以關閉 設定配接器 對話方塊中，然後按一下**Connect**。 Visual Studio 已成功建立與 Oracle E-business Suite 的連線之後，連線狀態會顯示為**Connected**。 您也可以查看顯示在 選擇 作業 頁面上的 Oracle E-business Suite 中繼資料。  
  
6. 在選擇 [作業] 頁面中**選取合約類型**清單中，按一下**用戶端 （傳出作業）**。  
  
7. 在 **選取一個類別**方塊中，瀏覽至 MS_SAMPLE_EMPLOYEE 介面資料表中的應用程式物件程式庫應用程式。 如需瀏覽至配接器中的成品，請參閱[瀏覽、 搜尋及擷取 Oracle E-business 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。  
  
8. 在 **可用的類別和作業**方塊中，選取**選取**操作時，，然後按一下 **新增**。 選取的作業加入至**新增的類別和作業** 方塊中。  
  
    ![新增選取的作業](../../adapters-and-accelerators/adapter-oracle-ebs/media/02-msb-gui.gif "02_MSB_GUI")  
  
   > [!NOTE]
   >  您可以新增一個以上的作業，每個成品。 您也可以加入不同的 Oracle E-business Suite 成品的作業。 例如，您可以新增介面資料表的一項作業，而另一個並行處理程式。 此外，您可以藉由搜尋運算式中指定萬用字元搜尋針對特定作業。 如需有關支援的特殊字元和節點層級處中，您可以搜尋作業的詳細資訊，請參閱[搜尋 Oracle E-business Suite 作業](../../adapters-and-accelerators/adapter-oracle-ebs/search-for-oracle-e-business-suite-operations.md)。  
  
9. 在選擇 作業 頁面中，按一下**下一步**。  
  
10. 在 [設定服務與端點行為] 頁面中，指定值來設定服務和端點行為。  
  
    1. 在 **服務行為組態**方塊中，指定下列值：  
  
       |屬性|指定的值|  
       |----------------------|-----------------------|  
       |EnableMetadataExchange|將此設為 **，則為 True**建立中繼資料交換端點。 將它設定為 **，則為 True**，您會讓服務中繼資料可供使用標準化的通訊協定，例如 WS-中繼資料交換 (MEX) 和 HTTP/GET 要求。 預設值是**False**。|  
       |IncludeExceptionDetailsinFault|將此設為 **，則為 True**包含 managed 例外狀況資訊傳回給用戶端以進行偵錯的 SOAP 錯誤詳細資料中。 預設值是**False**。|  
       |[屬性]|服務行為組態名稱。 本教學課程中，輸入**customServiceBehavior**。|  
       |UseServiceCertificate|指定您是否想要使用的 WCF 訊息層級的安全性模式。 預設值是 **，則為 True**。 本教學課程中，您必須將這**False**。|  
  
       > [!NOTE]
       >  因為我們不使用服務憑證，本教學課程中，您不需要提供的值**FindValue**， **StoreLocation**， **StoreName**，以及**X509FindType**屬性。 更多有關憑證和相關聯的屬性的詳細資訊，請參閱 < X509ClientCertificateCredentialsElement 屬性 >，網址[ http://go.microsoft.com/fwlink/?LinkId=103771 ](http://go.microsoft.com/fwlink/?LinkId=103771)。  
  
    2. 在 **端點行為組態**方塊中，指定下列值：  
  
       |屬性|指定的值|  
       |----------------------|-----------------------|  
       |驗證類型|Microsoft Office SharePoint server 來取用 WCF 服務，您應該設定為**HTTPUserNamePassword**。 這可讓用戶端指定的 HTTP 標頭的一部分的使用者名稱和密碼。|  
       |[屬性]|指定端點行為組態的名稱。 本教學課程中，輸入**customEndpointBehavior**。|  
       |UsernameHeader|使用者名稱標頭的名稱。 針對此範例中，指定**MyUserHeader**。 HTTP 標頭的詳細資訊，請參閱 「 支援的自訂 HTTP 和 SOAP 標頭 >，網址[ http://go.microsoft.com/fwlink/?LinkId=106692 ](http://go.microsoft.com/fwlink/?LinkId=106692)。 **注意︰** 您必須指定此屬性的值，如果**驗證類型**設定為**HTTPUserNamePassword**。 如果**驗證類型**設為**自動**，這是選擇性屬性。|  
       |PasswordHeader|密碼標頭的名稱。 針對此範例中，指定**MyPassHeader**。 HTTP 標頭的詳細資訊，請參閱 「 支援的自訂 HTTP 和 SOAP 標頭 >，網址[ http://go.microsoft.com/fwlink/?LinkId=106692 ](http://go.microsoft.com/fwlink/?LinkId=106692)。 **注意︰** 您必須指定此屬性的值，如果**驗證類型**設定為**HTTPUserNamePassword**。 如果**驗證類型**設為**自動**，這是選擇性屬性。|  
  
       下圖顯示具有指定之值的 [設定服務與端點行為] 頁面。  
  
       ![設定服務和端點行為 頁面](../../adapters-and-accelerators/adapter-oracle-ebs/media/03-service-and-endpoint-behavior.gif "03_Service_and_EndPoint_Behavior")  
  
11. 在 [設定服務與端點行為] 頁面中，按一下 [**下一步]**。  
  
12. 在 [設定服務端點繫結與位址] 頁面**選取要設定的合約**會顯示您所設定的成品 (MS_SAMPLE_EMPLOYEE)。 **作業所選的契約義務**方塊會顯示**選取**您選取的成品，選擇 [作業] 頁面上的作業。  
  
13. 在 **設定的位址和合約繫結**方塊中，指定下列值：  
  
    |屬性|指定的值|  
    |----------------------|-----------------------|  
    |繫結組態|此精靈只支援基本 HTTP 繫結。 因此，繫結組態 欄位會自動填入到*System.ServiceModel.Configuration.BasicHttpBindingElement*。<br /><br /> 按一下省略符號按鈕 **（...）** 變更 HTTP 繫結的屬性。 若要使用的安全通訊通道，您都必須設定**模式**屬性設**傳輸**。 精靈會設定的預設值**模式**屬性設為**傳輸**。<br /><br /> 公開的其他繫結的詳細資訊，請參閱 < BasicHttpBindingElement 成員 >，網址[ http://go.microsoft.com/fwlink/?LinkId=103773 ](http://go.microsoft.com/fwlink/?LinkId=103773)。|  
    |端點名稱|指定合約的端點名稱。|  
  
     此頁面上的其他欄位會自動填入您在先前頁面中指定的值為基礎。  
  
     按一下 **[套用]**。  
  
    > [!NOTE]
    >  如果您未指定任何值在此頁面上，所有合約接受預設值。  
  
     下圖顯示設定服務端點繫結與位址 頁面以指定的值。  
  
     ![設定服務端點繫結和位址](../../adapters-and-accelerators/adapter-oracle-ebs/media/04-service-endpoint-binding.gif "04_Service_Endpoint_Binding")  
  
14. 在 [設定服務端點繫結與位址] 頁面中，按一下 [**下一步]**。  [摘要] 頁面會列出樹狀結構的 Oracle E-business Suite 成品以及成品選取的作業。  
  
15. 檢閱 [摘要]，然後按**完成**。  
  
16. 精靈會建立 WCF 服務，並將下列檔案到[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案：  
  
    1.  .svc 檔案。 這是 WCF 服務檔案。 精靈會產生每個合約的一個檔案。  
  
    2.  Web.config 檔案。  
  
    3.  服務程式碼 （.cs 檔案）  
  
##  <a name="cs"></a> 修改.cs 檔案中  
 當您建立的服務，從 Oracle E-business Suite 成品使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]而且想要使用的商務資料清單 Web 組件在 Microsoft Office SharePoint Server，您應該提供完整的篩選子句開頭的 WHERE 子句. 例如，如果您想要搜尋名稱為"John"的員工，您需要提供下列篩選子句中商務資料清單 Web 組件：  
  
```  
where NAME like ‘JOHN’  
```  
  
 不過，如果您希望使用者只提供名稱做為輸入的篩選子句未實際討論整個篩選子句時，您可以加入程式碼在.cs 檔案中，以修改來自商務資料清單 Web 組件，Microsoft Office 中的篩選子句 若要將它的 WHERE 子句格式傳遞到 Oracle E-business 的 SharePoint 伺服器。  
  
 比方說，在此教學課程中，如果您想讓使用者輸入商務資料清單 Web 組件在 Microsoft Office SharePoint Server 中的員工名稱，然後擷取記錄該員工，您可以新增下列程式碼在.cs 檔案中：  
  
```  
SelectResponse InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE.Select(SelectRequest request)   
{  
     request.FILTER = "where NAME like '" + request.FILTER + "'"; // The code to avoid the users from specifying the WHERE clause in the filter from Business Data List Web Part.  
     return base.Channel.Select(request);  
}  
```  
  
##  <a name="Publish"></a> 發佈 WCF 服務  
 請確定 IIS 啟用 SSL。 如需有關如何啟用適用於 IIS 的 SSL 的指示，請參閱[ http://go.microsoft.com/fwlink/?LinkId=197170 ](http://go.microsoft.com/fwlink/?LinkId=197170)。  
  
 若要發佈的 WCF 服務：  
  
1.  以滑鼠右鍵按一下方案總管 中的專案，然後按一下**發佈**。  
  
2.  在 **發佈 Web**對話方塊方塊中，指定 WCF 服務的 URL。 例如：  
  
    ```  
    https://<COMPUTER_NAME>:<PORT_NUMBER>/MS_SAMPLE_EMPLOYEE/  
    ```  
  
    > [!NOTE]
    >  您必須將 WCF 服務發佈到啟用 SSL 的位置。 換句話說中的值才**目標位置**方塊必須以"https://"開頭。 因為 HTTP 標頭中傳遞使用者認證，精靈會自動設定做為安全性模式，這表示 SSL 加密中使用 「 傳輸 」 配接器的繫結行為。 您當然可以返回，並編輯 web.config 檔案，若要變更的值**\<安全性模式\>** 參數，但使用 SSL 時一定會更好的選項有以純文字傳輸機密資訊HTTP 標頭中的文字。  
  
3.  從**複製**方塊中，按一下**所有專案檔**。  
  
4.  按一下 [發行]。  
  
5.  確認 WCF 服務發佈成功。  
  
    1.  啟動 IIS Microsoft Management Console。 按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。  
  
    2.  瀏覽至您用來發行服務的節點。 針對**MS_SAMPLE_EMPLOYEE**服務，請瀏覽至**Internet Information Services** > **\<電腦名稱\>**  > **Web Sites** > **Default Web Site** > **MS_SAMPLE_EMPLOYEE**。  
  
    3.  在右窗格中，請在 InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE.svc 檔案，以滑鼠右鍵按一下，，然後按一下**瀏覽**。  
  
    4.  網頁上顯示的擷取 WSDL url。 您可能想要測試使用的中繼資料擷取**svcutil**命令。 例如，擷取 MS_SAMPLE_EMPLOYEE 服務中繼資料的命令是：  
  
        ```  
        svcutil.exe https://<COMPUTER_NAME>:<PORT_NUMBER>/MS_SAMPLE_EMPLOYEE/InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE.svc?wsdl  
  
        ```  
  
## <a name="next-step"></a>下一個步驟  
 若要建立 Oracle E-business Suite 成品的應用程式定義檔，使用 商務資料目錄定義編輯器。 如需相關指示，請參閱 <<c0> [ 步驟 2： 建立應用程式定義檔的 Oracle E-business Suite 成品](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md)。 LOB 資料的儲存位置並在其中儲存的格式，就會識別應用程式定義檔。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程： 將資料呈現從 SharePoint 網站上的 Oracle E-business Suite](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)