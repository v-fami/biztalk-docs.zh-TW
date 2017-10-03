---
title: "案例 2: 使用搜尋方塊 」 web 組件搜尋 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a233772f-7577-4ac5-b55a-cb1ba2f464c7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03e536df00499e8965632a3952eb3ae50e3f83df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-2--search-using-the-search-box-web-part"></a>使用搜尋方塊 」 web 組件搜尋案例 2:
若要設定使用您可以在同時執行全文檢索搜尋的搜尋應用程式的 Microsoft Office SharePoint Server 中設定搜尋設定 Oracle E-business Suite 中的 MS_SAMPLE_EMPLOYEE 介面資料表。 稍後，我們會加入搜尋方塊網頁組件從您可以在其中執行搜尋。  
  
 
  
##  <a name="Define"></a>定義內容的來源  
 本節討論有關定義內容從 Microsoft Office SharePoint Server 可以搜耙的資料來源。 這牽涉到將內容對應至方法執行個體中建立 Id Enumerator[步驟 2： 建立 Oracle E-business Suite 成品的應用程式定義檔](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md)。  
  
#### <a name="to-define-a-content-source"></a>若要定義內容的來源  
  
1.  啟動 SharePoint 3.0 管理中心。 按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在左側瀏覽窗格中，按一下 共用服務提供者 (SSP) 的您要設定搜尋應用程式的名稱。  
  
3.  在首頁上，在**搜尋**區段中，按一下**搜尋設定**。  
  
4.  在設定搜尋設定] 頁面上，在左窗格中**耙梳**，按一下 [**預設內容存取帳戶**指定編目內容時使用的預設帳戶的帳戶。  
  
5.  在 [預設內容存取帳戶] 頁面上指定的使用者名稱和密碼認證，然後按一下**確定**。 您將會回到 [搜尋] 頁面。  
  
6.  在左窗格下**耙梳**，按一下 **內容來源**。  
  
7.  在 管理內容來源 頁面上，按一下 **新的內容來源**。  
  
8.  在 管理內容來源 頁面上，按一下 **新的內容來源**。  
  
9. 在新增內容來源 頁面上：  
  
    1.  型別`MS_SAMPLE_EMPLOYEE`中**名稱**方塊。  
  
    2.  在**內容的來源類型**區域中，按一下 **商務資料**。  
  
    3.  在**應用程式**區域中，按一下 **搜耙已選取應用程式**，然後選取**MS_SAMPLE_EMPLOYEE_Instance**核取方塊。  
  
    4.  在**啟動完整搜耙**區域中，選取**啟動完整搜耙的這個內容來源**核取方塊，然後**確定**。  
  
         ![新增內容來源](../../adapters-and-accelerators/adapter-oracle-ebs/media/27-add-content-source.gif "27_Add_Content_Source")  
  
10. 您將會回到 [管理內容來源] 頁面，以加入新的內容來源。 內容來源將 Oracle E-business Suite 中 MS_SAMPLE_EMPLOYEE 介面資料表中的資料進行編目。 等候編目完成為止。  
  
11. 在左窗格中**耙梳**，按一下 **搜耙記錄檔**，然後確認記錄檔，以確保耙梳成功。  
  
##  <a name="Scope"></a>建立編目內容的範圍定義為  
  
1.  啟動 SharePoint 3.0 管理中心。 按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在左側瀏覽窗格中，按一下 共用服務提供者 (SSP) 的您要設定搜尋應用程式的名稱。  
  
3.  在首頁上，在**搜尋**區段中，按一下**搜尋設定**。  
  
4.  在設定搜尋設定] 頁面上，在左窗格中**查詢和結果**，按一下 [**範圍**來定義資料的耙梳的範圍。  
  
5.  在檢視領域] 頁面上，按一下 [**新領域**。  
  
6.  在建立領域 頁面中，輸入`MS_SAMPLE_EMPLOYEE_Search`中**標題**方塊，然後再按一下**確定**。  
  
     ![建立領域](../../adapters-and-accelerators/adapter-oracle-ebs/media/28-create-scope.gif "28_Create_Scope")  
  
7.  您將會回到檢視範圍頁面，以加入新的範圍。 在**更新狀態**資料行，新加入的範圍中，按一下**新增規則**連結。  
  
8.  在 新增範圍規則頁面上：  
  
    1.  在**範圍規則類型**區域中，按一下 **內容來源**。  
  
    2.  在**內容來源**清單中，按一下**MS_SAMPLE_EMPLOYEE**，然後按一下 **確定**。  
  
         ![新增範圍規則](../../adapters-and-accelerators/adapter-oracle-ebs/media/29-add-scope-rule.gif "29_Add_Scope_Rule")  
  
9. 您將會回到檢視範圍頁面與新增範圍規則。 在左窗格中，按一下 **搜尋管理**。  
  
10. 在 [搜尋] 頁面，找出**需要更新的範圍**資料列，然後按一下**立即開始更新**連結。  
  
 **範圍更新狀態**資料列都會顯示範圍更新的狀態。 等候更新完成。 已更新完成後，範圍是可供使用。  
  
##  <a name="AddScope"></a>將範圍新增至搜尋下拉式清單中  
 您已建立的搜尋範圍之後，您必須加入範圍中 Microsoft Office SharePoint Server 搜尋下拉式清單中，使其可以用它。  
  
#### <a name="to-add-the-scope-to-the-search-dropdown"></a>將範圍新增至搜尋下拉式清單中  
  
1.  啟動 SharePoint 3.0 管理中心。 按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在左側瀏覽窗格中，按一下 共用服務提供者 (SSP) 的您要設定搜尋應用程式的名稱。  
  
3.  在右上角的 共用服務管理 頁面上，按一下 **網站動作**，然後按一下 **站台設定**。  
  
4.  在站台設定 頁面中**網站集合管理**區段中，按一下**搜尋範圍**。  
  
5.  在檢視領域] 頁面上，按一下 [**搜尋下拉式清單中**連結。  
  
     ![檢視範圍](../../adapters-and-accelerators/adapter-oracle-ebs/media/30-view-scope.gif "30_View_Scope")  
  
6.  在編輯範圍顯示群組 頁面上：  
  
    1.  在**範圍**區域中，選取**MS_SAMPLE_EMPLOYEE_Search**核取方塊。  
  
    2.  在**預設範圍**區域中，按一下  **MS_SAMPLE_EMPLOYEE_Search**中**預設範圍**清單，然後再按**確定**。  
  
         ![編輯範圍顯示群組頁面](../../adapters-and-accelerators/adapter-oracle-ebs/media/31-edit-scope-display-group.gif "31_Edit_Scope_Display_Group")  
  
7.  您將會回到檢視範圍頁面與 MS_SAMPLE_EMPLOYEE_Search 範圍搜尋下拉式清單中顯示群組中加入。  
  
##  <a name="SearchWebPart"></a>新增搜尋方塊 」 Web 組件  
 若要啟用 Oracle E-business Suite 中 MS_SAMPLE_EMPLOYEE 介面資料表上執行全文檢索搜尋使用者，您必須現在建立 Web 組件頁面，並加入搜尋方塊 」 Web 組件。  
  
#### <a name="to-add-the-search-box-web-part"></a>若要新增搜尋方塊 」 Web 組件  
  
1.  建立一個 Web 組件稱為**MS_SAMPLE_EMPLOYEE_Search**。 若要知道建立 Web 組件頁面的步驟，請參閱[案例 1： 使用商務資料清單網頁組件顯示資料](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md)中[案例 1： 使用商務資料清單網頁組件顯示資料](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md)。  
  
2.  在 MS_SAMPLE_EMPLOYEE_Search] 頁面上，按一下 [**新增網頁組件**。  
  
3.  在**新增網頁組件**對話方塊中，於**搜尋**區段中，選取**搜尋方塊**核取方塊，然後**新增**。  
  
     ![新增搜尋方塊 」 Web 組件](../../adapters-and-accelerators/adapter-oracle-ebs/media/32-search-web-part.gif "32_Search_Web_Part")  
  
4.  搜尋方塊 」 Web 組件加入至 MS_SAMPLE_EMPLOYEE_Search 頁面。  
  
     ![搜尋方塊 」 Web 組件](../../adapters-and-accelerators/adapter-oracle-ebs/media/33-search-web-part-final.gif "33_Search_Web_Part_Final")  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 建立 SharePoint 應用程式來擷取 Oracle E-business Suite 中的資料](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md)  
 [案例 1： 使用商務資料清單網頁組件的顯示資料](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md)