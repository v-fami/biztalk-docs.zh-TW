---
title: "步驟 1： 將 SAP 成品發佈為 WCF 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service, generating a
- WCF Adapter Service Development Wizard , using the
- WCF Adapter Service Development Wizard
- SAP artifacts, publishing as a WCF service
ms.assetid: bd3087b0-e20f-4b75-beef-a913336d767b
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f4f00c3071bfc67a888c3550edbf9c946bd4524
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-publish-the-sap-artifacts-as-a-wcf-service"></a>步驟 1： 將 SAP 成品發佈為 WCF 服務
![步驟 4 之 1](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：**您可以使用 WCF 配接器服務開發精靈來產生可裝載的 WCF 服務，例如網際網路資訊服務 (IIS) 或 Windows Process Activation Service (WAS) 裝載環境中。 本主題示範如何使用精靈來產生 WCF 服務檔案。  
  
## <a name="prerequisites"></a>必要條件  
 執行精靈之前，安裝下列項目：  
  
-   [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]不論是透過**完成**選項或**自訂**選項 (並選擇**工具**內此選項)。 這會安裝[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]WCF 配接器服務開發精靈的範本。  
  
-   [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]從[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。  
  
-   所需的 SAP 用戶端程式庫。  
  
 如需有關這些必要條件的詳細資訊，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝指南。 在一般安裝安裝指南 》\<安裝磁碟機 >: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。  
  
### <a name="to-publish-the-sap-artifacts-as-a-wcf-service"></a>若要將 SAP 成品發佈為 WCF 服務  
  
1.  啟動[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，然後建立專案。  
  
2.  在**新專案**對話方塊中，從**專案類型**窗格中，選取**Visual C#**。 從**範本**窗格中，選取**WCF 配接器服務**。  
  
     或者，從**專案類型**] 窗格中，展開 [ **Visual C#**，然後選取**Web**。 從**範本**窗格中，選取**WCF 配接器服務**。  
  
    > [!NOTE]
    >  如果您已安裝[!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]與 Web 程式開發的元件， **WCF 配接器服務**範本也會提供**新增網站**選項。  
  
3.  指定的名稱和位置的方案，然後再按一下**確定**。 WCF 配接器服務開發精靈隨即啟動。  
  
4.  在 歡迎使用 頁面上，按一下 **下一步**。  
  
5.  選擇 [作業] 頁面上指定的連接字串連接至 SAP 系統。 若要這樣做：  
  
    1.  在**選取繫結**清單中，按一下**sapBinding**，然後按一下 **設定**。  
  
    2.  在**設定配接器**對話方塊中，按一下 [**安全性**] 索引標籤。  
  
    3.  在**用戶端認證類型**清單中，選取**Username**，然後指定有效的 SAP 使用者名稱和密碼以連接到 SAP 系統。  
  
    4.  按一下**URI 屬性**索引標籤，然後再指定連線參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。  
  
        > [!NOTE]
        >  如果連接參數包含任何保留的字元 （例如 XML 特殊字元），您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 不過，如果您指定的 URI 中直接**設定 URI**方塊和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。  
  
    5.  按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。 在本教學課程，BAPI_SALESORDER_GETLIST RFC 會叫用來取得特定客戶的銷售訂單的清單。 銷售訂單資訊也可能包含日期資料行。 在擷取日期資料行的值時，我們建議您將設定**EnableSafeTyping**內容繫結至**True**產生中繼資料時。 如果設定這個屬性，SAP DATS 資料型別會呈現為字串。  
  
         如需有關如何將 SAP 資料類型對應至對等的.NET 類型的詳細資訊，請參閱[基本的 SAP 資料型別](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md)。  
  
         如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
    6.  按一下**確定**，然後按一下 **連接**。 建立連接之後，連線狀態會顯示為**Connected**。  
  
6.  在選擇 [作業] 頁面中**選取的合約型別**清單中，按一下**用戶端 （輸出作業）**。  
  
7.  在**選取類別目錄**方塊中，展開將 SAP 成品類型。 例如，展開  **RFC**節點，查看包含您要產生 WCF 服務的 RFC 功能群組。  
  
8.  在**可用的類別和作業**方塊中，選取您想要產生 WCF 服務，然後按一下的操作**新增**。 選取的作業中所列**加入的類別和作業**方塊。  
  
    > [!NOTE]
    >  您可以加入多個作業的每個成品。 您也可以加入不同 SAP 成品的作業。 例如，您可以加入一項作業，如 RFC，另一個用於 IDOC。 此外，您可以藉由搜尋運算式中指定萬用字元搜尋針對特定作業。 如需支援的特殊字元和節點層級，您可以搜尋作業的詳細資訊，請參閱[連接到 Visual Studio 使用新增配接器中繼資料精靈 」 中的 SAP](../../adapters-and-accelerators/adapter-sap/connecting-to-sap-in-visual-studio-using-add-adapter-metadata-wizard.md)  
  
     此範例中，會新增 SD_RFC_CUSTOMER_GET 和 BAPI_SALESORDER_GETLIST Rfc。  
  
    > [!NOTE]
    >  某些版本的 SAP 系統公開 （expose) 而不是 SD_RFC_CUSTOMER_GET RFC_CUSTOMER_GET RFC。  
  
     ![選取 SAP 成品](../../adapters-and-accelerators/adapter-sap/media/f944f9a0-7387-46cb-8eb6-337344d01d29.gif "f944f9a0-7387-46cb-8eb6-337344d01d29")  
  
9. 在 [選擇作業] 頁面上按一下**下一步**。  
  
10. 在設定服務與端點行為 頁面上，指定值來設定服務與端點行為。  
  
    1.  在**服務行為組態**方塊中，指定下列值：  
  
        |屬性|指定的值|  
        |----------------------|-----------------------|  
        |EnableMetadataExchange|將此設**True**建立中繼資料交換端點。 由這個設定設為**True**，您會讓服務中繼資料可供使用標準化的通訊協定，例如 WS 中繼資料交換 (MEX) 和 HTTP/GET 要求。<br /><br /> 預設值是**False**。|  
        |IncludeExceptionDetailsinFault|將此設**True**在傳回至用戶端以進行偵錯的 SOAP 錯誤的詳細資料中包含 managed 例外狀況資訊。 預設值是**False**。|  
        |名稱|服務行為組態名稱。|  
        |UseServiceCertificate|指定您是否想要使用 WCF 的訊息層級的安全性模式。 預設值是**True**。<br /><br /> 此教學課程中，您必須設定為**False**。|  
        |FindValue|字串，指定要在 X.509 憑證存放區中搜尋的值。<br /><br /> **注意：**指定的值為這個屬性才**UseServiceCertificate**設**True**。|  
        |StoreLocation|值，指定服務可用來驗證用戶端憑證的憑證存放區位置。<br /><br /> **注意：**指定的值為這個屬性才**UseServiceCertificate**設**True**。|  
        |StoreName|若要開啟的 X.509 憑證存放區的名稱。<br /><br /> **注意：**指定的值為這個屬性才**UseServiceCertificate**設**True**。|  
        |X509FindType|要執行 X.509 搜尋類型。<br /><br /> **注意：**指定的值為這個屬性才**UseServiceCertificate**設**True**。|  
  
        > [!NOTE]
        >  有關憑證和相關聯的屬性的詳細資訊，請參閱 < X509ClientCertificateCredentialsElement 屬性 >，網址[http://go.microsoft.com/fwlink/?LinkId=103771](http://go.microsoft.com/fwlink/?LinkId=103771)。  
  
    2.  在**端點行為組態**方塊中，指定下列值：  
  
        |屬性|指定的值|  
        |----------------------|-----------------------|  
        |驗證類型|-將此設**ClientCredentialUserNamePassword**讓用戶端可以使用 WCF 服務時，指定使用者名稱和密碼。<br /><br /> -將此設**HTTPUserNamePassword**可讓用戶端的 HTTP 標頭中指定使用者名稱和密碼。<br /><br /> -將此設**自動**先啟用 用戶端指定認證，透過**ClientCredential**介面。 如果失敗，用戶端才能將認證傳遞做為 HTTP 標頭的一部分。<br /><br /> 預設值是**自動**。Microsoft Office SharePoint Server 來取用 WCF 服務，您應該設定為**HTTPUserNamePassword**。|  
        |名稱|指定端點行為組態名稱。|  
        |UsernameHeader|使用者名稱標頭的名稱。 此範例中，指定**MyUserHeader**。 HTTP 標頭的詳細資訊，請參閱 < 支援的自訂 HTTP 和 SOAP 標頭 >，網址[http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692)。<br /><br /> **注意：**您必須指定此屬性的值，如果**驗證類型**設**HTTPUserNamePassword**。 如果**驗證類型**設**自動**，這是選擇性屬性。|  
        |PasswordHeader|密碼標頭的名稱。 此範例中，指定**MyPassHeader**。 HTTP 標頭的詳細資訊，請參閱 < 支援的自訂 HTTP 和 SOAP 標頭 >，網址[http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692)。<br /><br /> **注意：**您必須指定此屬性的值，如果**驗證類型**設**HTTPUserNamePassword**。 如果**驗證類型**設**自動**，這是選擇性屬性。|  
  
     下圖顯示 [設定服務與端點行為] 頁面，以指定的值。  
  
     ![設定服務與端點行為 頁面](../../adapters-and-accelerators/adapter-sap/media/0a286b0c-7f0d-46c5-9b56-29bef3a1deea.gif "0a286b0c-7f0d-46c5-9b56-29bef3a1deea")  
  
11. 在 設定服務與端點行為 頁面上，按一下 **下一步**。  
  
12. 在 設定服務端點繫結和位址的頁面上，**選取要設定的合約**方塊會列出您選取 選擇作業 頁面上的作業將 SAP 成品。  
  
     例如，如果您選取 RFC 和 IDOC，底下的成品**選取要設定的合約**列出 IDOC 和 RFC。 如果您選取只 RFC，方塊只會列出 RFC。  
  
13. **選取合約之作業**方塊會顯示您選取的每個成品，選擇 [作業] 頁面上的作業。  
  
14. 在**設定的位址和合約繫結**方塊中，指定下列值：  
  
    |屬性|指定的值|  
    |----------------------|-----------------------|  
    |繫結組態|此精靈只支援基本 HTTP 繫結。 因此，繫結設定欄位所自動填入*System.ServiceModel.Configuration.BasicHttpBindingElement*。<br /><br /> 按一下省略符號按鈕**（...）**變更 HTTP 繫結的屬性。 若要使用安全通訊通道，您都必須設定**模式**屬性**傳輸**。 精靈會設定的預設值為**模式**屬性做為**傳輸**。<br /><br /> 公開的其他繫結的詳細資訊，請參閱 < BasicHttpBindingElement 成員 >，網址[http://go.microsoft.com/fwlink/?LinkId=103773](http://go.microsoft.com/fwlink/?LinkId=103773)。|  
    |端點名稱|指定合約的端點名稱。|  
  
     此頁面上的其他欄位會自動填入您在先前頁面中指定的值。  
  
     按一下 **[套用]**。 執行這個步驟底下顯示的所有合約**選取要設定的合約**方塊。  
  
    > [!NOTE]
    >  如果您未指定任何值在此頁面上，預設值會接受所有合約。  
  
     下圖顯示的設定服務端點繫結和位址 頁面上以指定的值。  
  
     ![設定服務端點繫結與位址](../../adapters-and-accelerators/adapter-sap/media/356e297c-9893-494c-a834-9d0b8b42da2e.gif "356e297c-9893-494c-a834-9d0b8b42da2e")  
  
15. 在 設定服務端點繫結和位址的頁面上，按一下 **下一步**。  [摘要] 頁面會列出樹狀結構中的 SAP 成品，並且在所選取的每個成品的作業。  
  
16. 檢閱 [摘要]，然後按一下**完成**。  
  
17. 精靈會建立 WCF 服務，並加入下列檔案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案：  
  
    1.  .svc 檔案。 這是 WCF 服務檔案。 精靈會產生一個檔案，針對每個合約。  
  
    2.  Web.config 檔案。  
  
    3.  服務程式碼 （.cs 檔案）  
  
18. 發佈 WCF 服務。  
  
    1.  請確定 SSL 已啟用網際網路資訊服務 (IIS)。 如需有關如何啟用 iis 的 SSL 的指示，請參閱[http://go.microsoft.com/fwlink/?LinkId=197170](http://go.microsoft.com/fwlink/?LinkId=197170)。  
  
    2.  以滑鼠右鍵按一下方案總管 中的專案，然後按一下**發行**。  
  
    3.  在**發行 Web**對話方塊方塊中，指定 WCF 服務的 URL。 例如：  
  
        ```  
        https://<computer_name>/Customer_Order/  
        ```  
  
    4.  從**複製**方塊中，按一下**所有專案檔**。  
  
    5.  按一下 [發行]。  
  
19. 請確認已成功發行 WCF 服務。  
  
    1.  啟動 IIS Microsoft Management Console。 按一下**啟動**，指向 **系統管理工具**，然後按一下 **網際網路資訊服務 (IIS) 管理員**。  
  
    2.  瀏覽至您用來發行服務的節點。 如**Customer_Order**服務，請瀏覽至**Internet Information Services** > **\<電腦名稱 >**  >  **Web Sites** > **Default Web Site** > **Customer_Order**。  
  
    3.  在右窗格中，Rfc.svc 檔案，以滑鼠右鍵按一下，然後按一下 **瀏覽**。  
  
    4.  擷取 WSDL 的 URL 和一同顯示網頁。 您可能想要測試中繼資料擷取使用**svcutil**命令。 比方說，是擷取 Customer_Order 服務中繼資料的命令：  
  
        ```  
        svcutil.exe https://<computer_name>/Customer_Order/Rfc.svc?wsdl  
  
        ```  
  
## <a name="next-step"></a>下一個步驟  
 若要建立 SAP 成品的應用程式定義檔，請使用商務資料目錄定義編輯器。 請參閱[步驟 2： 建立應用程式定義檔 SAP 成品](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md)如需相關指示。 應用程式定義檔識別 LOB 資料的儲存位置，以及儲存它的格式。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1： 從 SharePoint 網站上的 SAP 系統中呈現資料](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)