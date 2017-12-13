---
title: "Siebel 配接器搭配使用自訂 Web 組件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3a6c04-6523-483c-bdf4-ce0ac47cda87
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ad29a3ad28fcea81b00b6b2e2dabf51f0962e79
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="use-a-custom-web-part-with-the-siebel-adapter"></a>Siebel 配接器搭配使用自訂 Web 組件
本節提供與 Microsoft Office SharePoint Server 中使用自訂的 Web 組件的相關資訊。 若要使用自訂的 Web 組件，您必須執行下列作業：  
  
1.  建立自訂的 Web 組件  
  
2.  將自訂 Web 組件部署到 SharePoint 入口網站  
  
3.  設定 SharePoint 入口網站使用自訂 Web 組件  
  
## <a name="before-you-begin"></a>開始之前  
 建立自訂的 Web 組件之前：  
  
-   將 Siebel 成品發佈為 WCF 服務。 如需詳細資訊，請參閱[步驟 1： 發佈為 WCF 服務的 Siebel 商務元件操作](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md)中[教學課程 1： 呈現的資料從 Siebel 系統的 SharePoint 網站上](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)。  
  
-   建立 Microsoft Office SharePoint Server 中使用商務資料目錄的 Siebel 成品的應用程式定義檔。 如需詳細資訊，請參閱[步驟 2： 建立應用程式定義檔的 Siebel 商務元件操作](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md)中[教學課程 1： 呈現的資料從 Siebel 系統的 SharePoint 網站上](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)。  
  
##  <a name="Create_a_Custom_Web_Part"></a>步驟 1： 建立自訂的 Web 組件  
 若要建立自訂的 Web 組件，使用 Visual Studio，執行下列作業：  
  
1.  啟動 Visual Studio，並再建立專案。  
  
2.  在**新專案**對話方塊中，從**專案類型**窗格中，選取**Visual C#**。 從**範本**窗格中，選取**類別庫**。  
  
3.  指定的名稱和位置的方案。 本主題中，指定`CustomWebPart`中**名稱**和**方案名稱**方塊。 指定的位置，然後按一下**確定**。  
  
4.  將 System.Web 元件的參考加入至專案。 以滑鼠右鍵按一下專案名稱中的**方案總管] 中**，然後按一下 [**加入參考**。 在**加入參考**對話方塊中，選取**System.Web**中**.NET**索引標籤，然後再按一下**確定**。 System.Web 元件包含 System.Web.UI.WebControls.WebParts 必要的命名的空間。  
  
5.  加入必要的程式碼，根據您在專案中的問題。 有關特定問題的程式碼範例，請參閱 「 問題涉及自訂 Web 組件 」，在[搭配 SharePoint 使用 Siebel 配接器時的考量](../../adapters-and-accelerators/adapter-siebel/considerations-when-using-the-siebel-adapter-with-sharepoint.md)。  
  
6.  建置專案。 專案建置成功，將產生的.dll 檔案，CustomWebPart.dll，在\<*專案資料夾* \> /bin/Debug 資料夾。  
  
## <a name="step-2-deploy-the-custom-web-part-to-a-sharepoint-portal"></a>步驟 2： 將自訂 Web 組件部署到 SharePoint 入口網站  
 您必須執行下列命令來讓 CustomWebPart.dll 檔案 （自訂的 Web 組件） 中建立 「 步驟 1： 建立自訂的 Web 組件 」 的 SharePoint 入口網站上，您可以使用本主題：  
  
-   **CustomWebPart.dll 檔案複製到 SharePoint 入口網站的 bin 資料夾**: Microsoft Office SharePoint Server 建立入口網站下的\<*根磁碟機*\>: \Inetpub\wwwroot\wss\VirtualDirectories 資料夾。 資料夾會針對每個入口網站中，建立，而且可以識別的連接埠號碼。 您必須複製 CustomWebPart.dll 檔案建立在 「 步驟 1： 建立自訂的 Web 組件 」 本主題的\<*根磁碟機*\>: \Inetpub\wwwroot\wss\VirtualDirectories\\ <*Port_Number*\>\bin 資料夾。 例如，如果您的 SharePoint 入口網站的通訊埠編號是 13614，您必須複製 CustomWebPart.dll 檔案\<*根磁碟機*\>: \Inetpub\wwwroot\wss\VirtualDirectories\13614\bin 資料夾。  
  
    > [!TIP]
    >  若要尋找您的 SharePoint 入口網站的資料夾位置的另一個方法是使用**網際網路資訊服務 (IIS) 管理員**視窗 (**啟動** > **執行** >  **inetmgr**)。 找出您的 SharePoint 入口網站中**網際網路資訊服務 (IIS) 管理員**視窗 ([*computer_name*] > 網站 > [*入口網站名稱*])，以滑鼠右鍵按一下，並然後按一下 **屬性**快顯功能表中。 在 屬性 對話方塊中的 SharePoint 入口網站，按一下 **主目錄**索引標籤，然後選取**本機路徑**方塊。  
  
-   **在 web.config 檔案中加入安全控制項項目**： 因為 CustomWebPart.dll 檔案將用於不同的電腦上並由多個使用者，您必須宣告為 「 安全 」。 檔案 若要這樣做，開啟 web.config 檔案位於位於入口網站的 SharePoint 資料夾\<*根磁碟機*\>: \Inetpub\wwwroot\wss\VirtualDirectories\\< Port_Number\>。 在下`<SafeControls>`> 一節的 web.config 檔案中，加入下列安全控制項項目：  
  
    ```  
    <SafeControl Assembly="CustomWebPart" Namespace="CustomWebPart" TypeName="*" Safe="True" />  
    ```  
  
     儲存 web.config 檔案中，，然後關閉它。  
  
## <a name="step-3-configure-the-sharepoint-portal-to-use-the-custom-web-part"></a>步驟 3： 設定 SharePoint 入口網站使用自訂 Web 組件  
 您需要將自訂 Web 組件新增至 Microsoft Office SharePoint Server Web 組件庫，以便您可以使用它在您的 SharePoint 入口網站上。 若要這樣做：  
  
1.  啟動 SharePoint 3.0 管理中心。 按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在左側瀏覽窗格中，按一下 共用服務提供者 (SSP) 的您要加入自訂 Web 組件的名稱。  
  
3.  在**共用服務管理**頁面上，在右上角，按一下**網站動作**，然後按一下 **建立**。  
  
4.  在**站台設定**頁面上，按一下**Web 組件**下**圖庫**資料行。  
  
5.  在**網頁組件庫**頁面上，將自訂 Web 組件新增至組件庫中，按一下**新增**。 此時不提供自訂的 Web 組件**網頁組件庫**頁面。  
  
6.  在**新的 Web 組件**頁面上，尋找**CustomWebPart** （自訂的 Web 組件的名稱） 在清單中，選取左邊的核取方塊，然後按一下 **擴展組件庫**頂端頁面。 這會新增**CustomWebPart**中的項目**網頁組件庫**頁面。  
  
 現在您可以使用自訂 Web 組件 (**CustomWebPart**) 在您的 SharePoint 入口網站中建立 Web 組件。 自訂的 Web 組件 (**CustomWebPart**) 會出現在**其他**一節中**新增網頁組件**頁面。  
  
## <a name="see-also"></a>請參閱  
 [搭配使用 SharePoint 與 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/use-the-siebel-adapter-with-sharepoint.md)