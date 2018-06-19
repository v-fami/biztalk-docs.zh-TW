---
title: SAP 配接器搭配使用自訂 Web 組件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b7fecd2-a385-4b2d-a01b-3bfd65ecff3a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37d364f78404b46fe60c705c33247ccb73ba1aa3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964300"
---
# <a name="use-a-custom-web-part-with-the-sap-adapter"></a>SAP 配接器搭配使用自訂 Web 組件
本節提供與 Microsoft Office SharePoint Server 中使用自訂的 Web 組件的相關資訊。 若要使用自訂的 Web 組件，您必須執行下列作業：  
  
1.  建立自訂的 Web 組件  
  
2.  將自訂 Web 組件部署到 SharePoint 入口網站  
  
3.  設定 SharePoint 入口網站使用自訂 Web 組件  
  
## <a name="before-you-begin"></a>開始之前  
 建立自訂的 Web 組件之前：  
  
-   將 SAP 成品發佈為 WCF 服務。 如需詳細資訊，請參閱[步驟 1： 發佈為 WCF 服務將 SAP 成品](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md)中[教學課程 1： 從 SharePoint 網站上的 SAP 系統的呈現資料](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)。  
  
-   建立 Microsoft Office SharePoint Server 中使用商務資料目錄將 SAP 成品的應用程式定義檔。 如需詳細資訊，請參閱[步驟 2： 建立應用程式定義檔 SAP 成品](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md)中[教學課程 1： 呈現的資料，從 SharePoint 網站上的 SAP 系統](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)。  
  
##  <a name="Create_a_Custom_Web_Part"></a>步驟 1： 建立自訂的 Web 組件  
 若要建立自訂的 Web 組件，使用 Visual Studio，執行下列作業：  
  
1.  啟動 Visual Studio，並再建立專案。  
  
2.  在**新專案**對話方塊中，從**專案類型**窗格中，選取**Visual C#**。 從**範本**窗格中，選取**類別庫**。  
  
3.  指定的名稱和位置的方案。 本主題中，指定`CustomWebPart`中**名稱**和**方案名稱**方塊。 指定的位置，然後按一下**確定**。  
  
4.  將 System.Web 元件的參考加入至專案。 以滑鼠右鍵按一下專案名稱中的**方案總管] 中**，然後按一下 [**加入參考**。 在**加入參考**對話方塊中，選取**System.Web**中 **.NET**索引標籤，然後再按一下**確定**。 System.Web 元件包含 System.Web.UI.WebControls.WebParts 必要的命名的空間。  
  
5.  加入必要的程式碼，根據您在專案中的問題。 有關特定問題的程式碼範例，請參閱 「 問題涉及自訂 Web 組件 」，在[搭配 SharePoint 使用 SAP 配接器時的考量](../../adapters-and-accelerators/adapter-sap/considerations-when-using-the-sap-adapter-with-sharepoint.md)。  
  
6.  建置專案。 專案建置成功，將產生的.dll 檔案，CustomWebPart.dll，在\<專案資料夾 \> /bin/Debug 資料夾。  
  
7.  **僅適用於 64 位元電腦**： 之前執行下列步驟簽署為強式名稱的 CustomWebPart.dll 檔案。 否則，您將無法匯入，並因此使用中的 SharePoint 入口網站中的 CustomWebPart.dll 「 步驟 3： 設定 SharePoint 入口網站使用自訂 Web 組件。 」 請參閱[如何： 簽署為強式名稱組件](https://msdn.microsoft.com/library/xc31ft41.aspx)。
  
## <a name="step-2-deploy-the-custom-web-part-to-a-sharepoint-portal"></a>步驟 2： 將自訂 Web 組件部署到 SharePoint 入口網站  
 您必須執行下列命令來讓 CustomWebPart.dll 檔案 （自訂的 Web 組件） 中建立 「 步驟 1： 建立自訂的 Web 組件 」 的 SharePoint 入口網站上，您可以使用本主題：  
  
-   **CustomWebPart.dll 檔案複製到 SharePoint 入口網站的 bin 資料夾**: Microsoft Office SharePoint Server 建立入口網站下的\<根磁碟機\>: \Inetpub\wwwroot\wss\VirtualDirectories 資料夾。 資料夾會針對每個入口網站中，建立，而且可以識別的連接埠號碼。 您必須複製 CustomWebPart.dll 檔案建立在 「 步驟 1： 建立自訂的 Web 組件 」 本主題的\<根磁碟機\>: \Inetpub\wwwroot\wss\VirtualDirectories\\< Port_Number\>\bin 資料夾。 例如，如果您的 SharePoint 入口網站的通訊埠編號是 13614，您必須複製 CustomWebPart.dll 檔案\<根磁碟機\>: \Inetpub\wwwroot\wss\VirtualDirectories\13614\bin 資料夾。  
  
    > [!TIP]
    >  若要尋找您的 SharePoint 入口網站的資料夾位置的另一個方法是使用**網際網路資訊服務 (IIS) 管理員**視窗 (**啟動** > **執行** >  **inetmgr**)。 找出您的 SharePoint 入口網站中**網際網路資訊服務 (IIS) 管理員**視窗 ([電腦名稱] > 網站 > [入口網站名稱])，按一下滑鼠右鍵，然後再按一下**屬性**中快顯功能表。 在 屬性 對話方塊中的 SharePoint 入口網站，按一下 **主目錄**索引標籤，然後選取**本機路徑**方塊。  
  
-   **在 web.config 檔案中加入安全控制項項目**： 因為 CustomWebPart.dll 檔案將用於不同的電腦上並由多個使用者，您必須宣告為 「 安全 」。 檔案 若要這樣做，開啟 web.config 檔案位於位於入口網站的 SharePoint 資料夾\<根磁碟機\>: \Inetpub\wwwroot\wss\VirtualDirectories\\< Port_Number\>。 在下`<SafeControls>`> 一節的 web.config 檔案中，加入下列安全控制項項目：  
  
    -   **在 32 位元電腦：**  
  
        ```  
        <SafeControl Assembly="CustomWebPart" Namespace="CustomWebPart" TypeName="*" Safe="True" />  
        ```  
  
    -   **在 64 位元電腦：**  
  
        ```  
        <SafeControl Assembly="CustomWebPart, Version=1.0.0.0, Culture=neutral, PublicKeyToken=<PUBLICKKEYTOKEN_OF_CustomWebPart.dll>" Namespace="CustomWebPart" TypeName="*" Safe="True" />  
        ```  
  
     儲存 web.config 檔案中，，然後關閉它。  
  
## <a name="step-3-configure-the-sharepoint-portal-to-use-the-custom-web-part"></a>步驟 3： 設定 SharePoint 入口網站使用自訂 Web 組件  
 您需要將自訂 Web 組件新增至 Microsoft Office SharePoint Server Web 組件庫，以便您可以使用它在您的 SharePoint 入口網站上。 若要這樣做：  
  
1.  啟動 SharePoint 3.0 管理中心。 按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在左側瀏覽窗格中，按一下 共用服務提供者 (SSP) 的您要加入自訂 Web 組件的名稱。  
  
3.  在右上角的 共用服務管理 頁面上，按一下 **網站動作**，然後按一下 **建立**。  
  
4.  在站台設定] 頁面上，按一下 [ **Web 組件**下**圖庫**資料行。  
  
5.  在網頁組件庫 頁面上，若要將自訂 Web 組件新增至圖庫中，按一下**新增**。 此時不網頁組件庫頁面中，您可以使用自訂 Web 組件。  
  
6.  在新的 Web 組件] 頁面上，找出**CustomWebPart** （自訂的 Web 組件的名稱） 在清單中，選取左邊的核取方塊，然後按一下 [**擴展組件庫**的頁面頂端。 這會新增**CustomWebPart**網頁組件庫頁面中的項目。  
  
 現在您可以使用自訂 Web 組件 (**CustomWebPart**) 在您的 SharePoint 入口網站中建立 Web 組件。 自訂的 Web 組件 (**CustomWebPart**) 會出現在**其他**新增網頁組件頁面 區段中的。  
  
## <a name="see-also"></a>請參閱  
[搭配使用 SharePoint 與 SAP 配接器](../../adapters-and-accelerators/adapter-sap/use-the-sap-adapter-with-sharepoint.md)