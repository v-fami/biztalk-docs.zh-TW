---
title: 步驟 1： 將 SAP 成品發佈為 WCF 服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service, generating a
- WCF Adapter Service Development Wizard , using the
- WCF Adapter Service Development Wizard
- SAP artifacts, publishing as a WCF service
ms.assetid: bd3087b0-e20f-4b75-beef-a913336d767b
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4af261acd7d61ae49aef53a9f7f206fb8a597fbd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989375"
---
# <a name="step-1-publish-the-sap-artifacts-as-a-wcf-service"></a>步驟 1： 將 SAP 成品發佈為 WCF 服務
![步驟 4 之 1](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 您可以使用 WCF 配接器服務開發精靈來產生可裝載的 WCF 服務，例如 Internet Information Services (IIS) 或 Windows Process Activation Service (WAS) 裝載環境中。 本主題示範如何使用精靈來產生 WCF 服務檔案。  
  
## <a name="prerequisites"></a>必要條件  
 執行精靈之前，安裝下列項目：  
  
- [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] 不論是使用**完成**選項或**自訂**選項 (，然後選擇**工具**內此選項)。 這會安裝[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]WCF 配接器服務開發精靈的範本。  
  
- [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] 從[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。  
  
- 所需的 SAP 用戶端程式庫。  
  
  如需有關這些必要條件的詳細資訊，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝指南。 安裝指南通常安裝在\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。  
  
### <a name="to-publish-the-sap-artifacts-as-a-wcf-service"></a>若要將 SAP 成品發佈為 WCF 服務  
  
1. 啟動[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，然後建立專案。  
  
2. 在 [**新的專案**] 對話方塊中，從**專案類型**窗格中，選取**Visual C#**。 從**範本**窗格中，選取**WCF 配接器服務**。  
  
    或者，從**專案類型**窗格中，展開**Visual C#**，然後選取**Web**。 從**範本**窗格中，選取**WCF 配接器服務**。  
  
   > [!NOTE]
   >  如果您已安裝[!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]與網頁程式開發的元件**WCF 配接器服務**範本也會提供**新增網站**選項。  
  
3. 指定的名稱和方案和位置，然後按一下**確定**。 WCF 配接器服務開發精靈隨即啟動。  
  
4. 在 歡迎使用 頁面上，按一下**下一步**。  
  
5. 在選擇 [作業] 頁面中，指定連接字串來連接到 SAP 系統。 若要這樣做：  
  
   1. 在 **選取的繫結**清單中，按一下**sapBinding**，然後按一下**設定**。  
  
   2. 在 **設定介面卡** 對話方塊中，按一下**安全性** 索引標籤。  
  
   3. 在 **用戶端認證類型**清單中，選取**Username**，然後指定有效的 SAP 使用者名稱和密碼來連線到 SAP 系統。  
  
   4. 按一下  **URI 屬性**索引標籤，然後指定 連接參數的值。 如需有關連線 URI 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱 <<c2> [ 建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。  
  
      > [!NOTE]
      >  如果連接參數會包含任何保留的字元 （例如 XML 特殊字元），您必須指定為-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 不過，如果您指定直接在 URI**設定 URI**方塊和連接參數包含保留的字元，您必須指定下列連線參數，使用適當的逸出字元。  
  
   5. 按一下 **繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。 在本教學課程中，BAPI_SALESORDER_GETLIST RFC 會叫用來取得特定客戶的銷售訂單的清單。 銷售訂單資訊也可能包含日期資料行。 在擷取日期資料行的值時，我們建議您設定**EnableSafeTyping**繫結屬性 **，則為 True**時產生的中繼資料。 如果設定這個屬性，SAP DATS 資料類型會顯示為字串。  
  
       如需有關如何將 SAP 資料型別對應至對等的.NET 類型的詳細資訊，請參閱[基本 SAP 資料型別](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md)。  
  
       如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
   6. 按一下  **確定**，然後按一下**Connect**。 建立連線之後，連線狀態會顯示為**Connected**。  
  
6. 在選擇 [作業] 頁面中**選取合約類型**清單中，按一下**用戶端 （傳出作業）**。  
  
7. 在 **選取一個類別**方塊中，展開 將 SAP 成品類型。 例如，依序展開**RFC**節點以查看包含您要產生的 WCF 服務的 RFC 功能群組。  
  
8. 在 **可用的類別和作業**方塊中，選取您想要產生 WCF 服務，然後按的作業**新增**。 選取的作業都會列入**新增的類別和作業** 方塊中。  
  
   > [!NOTE]
   >  您可以新增一個以上的作業，每個成品。 您也可以加入不同的 SAP 成品的作業。 例如，您可以新增一項作業，如 RFC 和 IDOC 的另一個。 此外，您可以藉由搜尋運算式中指定萬用字元搜尋針對特定作業。 如需有關支援的特殊字元和節點層級處中，您可以搜尋作業的詳細資訊，請參閱[連接到 Visual Studio 使用新增配接器中繼資料精靈中的 SAP](../../adapters-and-accelerators/adapter-sap/connecting-to-sap-in-visual-studio-using-add-adapter-metadata-wizard.md)  
  
    此範例中，會新增 SD_RFC_CUSTOMER_GET 和 BAPI_SALESORDER_GETLIST Rfc。  
  
   > [!NOTE]
   >  某些版本的 SAP 系統公開 （expose) 而不是 SD_RFC_CUSTOMER_GET RFC_CUSTOMER_GET RFC。  
  
    ![選取 SAP 成品](../../adapters-and-accelerators/adapter-sap/media/f944f9a0-7387-46cb-8eb6-337344d01d29.gif "f944f9a0-7387-46cb-8eb6-337344d01d29")  
  
9. 在選擇 作業 頁面中，按一下**下一步**。  
  
10. 在 [設定服務與端點行為] 頁面中，指定值來設定服務和端點行為。  
  
    1. 在 **服務行為組態**方塊中，指定下列值：  
  
       |屬性|指定的值|  
       |----------------------|-----------------------|  
       |EnableMetadataExchange|將此設為 **，則為 True**建立中繼資料交換端點。 將它設定為 **，則為 True**，您會讓服務中繼資料可供使用標準化的通訊協定，例如 WS-中繼資料交換 (MEX) 和 HTTP/GET 要求。<br /><br /> 預設值是**False**。|  
       |IncludeExceptionDetailsinFault|將此設為 **，則為 True**包含 managed 例外狀況資訊傳回給用戶端以進行偵錯的 SOAP 錯誤詳細資料中。 預設值是**False**。|  
       |[屬性]|服務行為組態名稱。|  
       |UseServiceCertificate|指定您是否想要使用的 WCF 訊息層級的安全性模式。 預設值是 **，則為 True**。<br /><br /> 本教學課程中，您必須將這**False**。|  
       |FindValue|字串，指定要在 X.509 憑證存放區中搜尋的值。<br /><br /> **注意：** 指定的值為這個屬性只有當**UseServiceCertificate**設定為 **，則為 True**。|  
       |StoreLocation|值，指定服務可用來驗證用戶端憑證的憑證存放區位置。<br /><br /> **注意：** 指定的值為這個屬性只有當**UseServiceCertificate**設定為 **，則為 True**。|  
       |StoreName|若要開啟的 X.509 憑證存放區的名稱。<br /><br /> **注意：** 指定的值為這個屬性只有當**UseServiceCertificate**設定為 **，則為 True**。|  
       |X509FindType|若要執行的 X.509 搜尋類型。<br /><br /> **注意：** 指定的值為這個屬性只有當**UseServiceCertificate**設定為 **，則為 True**。|  
  
       > [!NOTE]
       >  更多有關憑證和相關聯的屬性的詳細資訊，請參閱 < X509ClientCertificateCredentialsElement 屬性 >，網址[ http://go.microsoft.com/fwlink/?LinkId=103771 ](http://go.microsoft.com/fwlink/?LinkId=103771)。  
  
    2. 在 **端點行為組態**方塊中，指定下列值：  
  
       |屬性|指定的值|  
       |----------------------|-----------------------|  
       |驗證類型|-將此設為**ClientCredentialUserNamePassword**來讓用戶端使用 WCF 服務時，指定使用者名稱和密碼。<br /><br /> -將此設為**HTTPUserNamePassword**讓用戶端使用者名稱和密碼指定 HTTP 標頭的一部分。<br /><br /> -將此設為**自動**先啟用 用戶端指定認證，透過**ClientCredential**介面。 如果失敗，用戶端可以將認證傳遞做為 HTTP 標頭的一部分。<br /><br /> 預設值是**自動**。Microsoft Office SharePoint server 來取用 WCF 服務，您應該設定為**HTTPUserNamePassword**。|  
       |[屬性]|指定端點行為組態的名稱。|  
       |UsernameHeader|使用者名稱標頭的名稱。 針對此範例中，指定**MyUserHeader**。 HTTP 標頭的詳細資訊，請參閱 「 支援的自訂 HTTP 和 SOAP 標頭 >，網址[ http://go.microsoft.com/fwlink/?LinkId=106692 ](http://go.microsoft.com/fwlink/?LinkId=106692)。<br /><br /> **注意︰** 您必須指定此屬性的值，如果**驗證類型**設定為**HTTPUserNamePassword**。 如果**驗證類型**設為**自動**，這是選擇性屬性。|  
       |PasswordHeader|密碼標頭的名稱。 針對此範例中，指定**MyPassHeader**。 HTTP 標頭的詳細資訊，請參閱 「 支援的自訂 HTTP 和 SOAP 標頭 >，網址[ http://go.microsoft.com/fwlink/?LinkId=106692 ](http://go.microsoft.com/fwlink/?LinkId=106692)。<br /><br /> **注意︰** 您必須指定此屬性的值，如果**驗證類型**設定為**HTTPUserNamePassword**。 如果**驗證類型**設為**自動**，這是選擇性屬性。|  
  
       下圖顯示具有指定之值的 [設定服務與端點行為] 頁面。  
  
       ![設定服務和端點行為 頁面](../../adapters-and-accelerators/adapter-sap/media/0a286b0c-7f0d-46c5-9b56-29bef3a1deea.gif "0a286b0c-7f0d-46c5-9b56-29bef3a1deea")  
  
11. 在 [設定服務與端點行為] 頁面中，按一下 [**下一步]**。  
  
12. 在 [設定服務端點繫結與位址] 頁面**選取要設定的合約**方塊會列出您選取的作業，選擇 [作業] 頁面上的 SAP 成品。  
  
     例如，如果您選取的 RFC 和 IDOC，底下的構件**選取要設定的合約**列出 RFC 和 IDOC。 如果您選取只 RFC，方塊只會列出 RFC。  
  
13. **下選取的合約作業**方塊會顯示您針對每個成品，選擇 [作業] 頁面上選取的作業。  
  
14. 在 **設定的位址和合約繫結**方塊中，指定下列值：  
  
    |屬性|指定的值|  
    |----------------------|-----------------------|  
    |繫結組態|此精靈只支援基本 HTTP 繫結。 因此，繫結組態 欄位會自動填入到*System.ServiceModel.Configuration.BasicHttpBindingElement*。<br /><br /> 按一下省略符號按鈕 **（...）** 變更 HTTP 繫結的屬性。 若要使用的安全通訊通道，您都必須設定**模式**屬性設**傳輸**。 精靈會設定的預設值**模式**屬性設為**傳輸**。<br /><br /> 公開的其他繫結的詳細資訊，請參閱 < BasicHttpBindingElement 成員 >，網址[ http://go.microsoft.com/fwlink/?LinkId=103773 ](http://go.microsoft.com/fwlink/?LinkId=103773)。|  
    |端點名稱|指定合約的端點名稱。|  
  
     此頁面上的其他欄位會自動填入您在先前頁面中指定的值為基礎。  
  
     按一下 **[套用]**。 執行此步驟中下方顯示的所有合約**選取要設定的合約** 方塊中。  
  
    > [!NOTE]
    >  如果您未指定任何值在此頁面上，所有合約接受預設值。  
  
     下圖顯示設定服務端點繫結與位址 頁面以指定的值。  
  
     ![設定服務端點繫結和位址](../../adapters-and-accelerators/adapter-sap/media/356e297c-9893-494c-a834-9d0b8b42da2e.gif "356e297c-9893-494c-a834-9d0b8b42da2e")  
  
15. 在 [設定服務端點繫結與位址] 頁面中，按一下 [**下一步]**。  [摘要] 頁面會列出樹狀結構的 SAP 成品，以及下，選取每個成品的作業。  
  
16. 檢閱 [摘要]，然後按**完成**。  
  
17. 精靈會建立 WCF 服務，並將下列檔案到[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案：  
  
    1.  .svc 檔案。 這是 WCF 服務檔案。 精靈會產生每個合約的一個檔案。  
  
    2.  Web.config 檔案。  
  
    3.  服務程式碼 （.cs 檔案）  
  
18. 發佈 WCF 服務。  
  
    1.  請確定 SSL 已啟用網際網路資訊服務 (IIS)。 如需有關如何啟用適用於 IIS 的 SSL 的指示，請參閱[ http://go.microsoft.com/fwlink/?LinkId=197170 ](http://go.microsoft.com/fwlink/?LinkId=197170)。  
  
    2.  以滑鼠右鍵按一下方案總管 中的專案，然後按一下**發佈**。  
  
    3.  在 **發佈 Web**對話方塊方塊中，指定 WCF 服務的 URL。 例如：  
  
        ```  
        https://<computer_name>/Customer_Order/  
        ```  
  
    4.  從**複製**方塊中，按一下**所有專案檔**。  
  
    5.  按一下 [發行]。  
  
19. 確認 WCF 服務發佈成功。  
  
    1.  啟動 IIS Microsoft Management Console。 按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。  
  
    2.  瀏覽至您用來發行服務的節點。 針對**Customer_Order**服務，請瀏覽至**Internet Information Services** > **\<電腦名稱\>**  > **Web Sites** > **Default Web Site** > **Customer_Order**。  
  
    3.  在右窗格中，請在 Rfc.svc 檔案，以滑鼠右鍵按一下，，然後按一下**瀏覽**。  
  
    4.  網頁上顯示的擷取 WSDL url。 您可能想要測試使用的中繼資料擷取**svcutil**命令。 例如，擷取 Customer_Order 服務中繼資料的命令是：  
  
        ```  
        svcutil.exe https://<computer_name>/Customer_Order/Rfc.svc?wsdl  
  
        ```  
  
## <a name="next-step"></a>下一個步驟  
 若要建立 SAP 成品的應用程式定義檔，使用 商務資料目錄定義編輯器。 請參閱[步驟 2： 建立 SAP 成品的應用程式定義檔](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md)如需相關指示。 LOB 資料的儲存位置並在其中儲存的格式，就會識別應用程式定義檔。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1：在 SharePoint 網站上呈現 SAP 系統的資料](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)