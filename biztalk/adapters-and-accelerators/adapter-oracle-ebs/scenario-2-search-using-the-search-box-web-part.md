---
title: '案例 2: 使用搜尋方塊 web 組件搜尋 |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a233772f-7577-4ac5-b55a-cb1ba2f464c7
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ac446f83af49d8d2faa06c7b43b1f59d343679b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991703"
---
# <a name="scenario-2--search-using-the-search-box-web-part"></a>案例 2： 搜尋使用搜尋方塊 web 組件
我們將在 Microsoft Office SharePoint Server 來設定使用您可以在同時執行全文檢索搜尋的搜尋應用程式中設定搜尋設定 Oracle E-business Suite 中的 MS_SAMPLE_EMPLOYEE 介面資料表。 稍後，我們會新增搜尋方塊 Web 組件若要從您可以在其中執行搜尋。  
  
 
  
##  <a name="Define"></a> 定義內容的來源  
 本節將討論如何定義內容的來源，從 Microsoft Office SharePoint Server 可以搜耙的資料。 這牽涉到將內容對應至方法的執行個體中建立 Id Enumerator[步驟 2： 建立 Oracle E-business Suite 成品的應用程式定義檔](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md)。  
  
#### <a name="to-define-a-content-source"></a>若要定義的內容來源  
  
1.  啟動 SharePoint 3.0 管理中心。 按一下 **開始**，指向**所有程式**，指向**Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在左側的導覽窗格中，按一下名稱的共用服務提供者 (SSP) 您要設定搜尋應用程式。  
  
3.  在 [首頁] 頁面中，在**搜尋**區段中，按一下**搜尋設定**。  
  
4.  在設定搜尋設定 頁面上，在左窗格的下**耙梳**，按一下**預設內容存取帳戶**指定編目內容時，使用做為預設帳戶的帳戶。  
  
5.  在預設內容的存取帳戶] 頁面上，指定使用者名稱和密碼認證，然後按一下 [**確定**。 您將返回 [搜尋] 頁面。  
  
6.  在左窗格的下**耙梳**，按一下**內容來源**。  
  
7.  在管理內容的來源 頁面上，按一下**新的內容來源**。  
  
8.  在管理內容的來源 頁面上，按一下**新的內容來源**。  
  
9. 在 [新增內容來源] 頁面中：  
  
    1.  型別`MS_SAMPLE_EMPLOYEE`中**名稱** 方塊中。  
  
    2.  在 **內容的來源類型**區域中，按一下**商務資料**。  
  
    3.  在**應用程式**區域中，按一下**搜耙選取應用程式**，然後選取**MS_SAMPLE_EMPLOYEE_Instance**核取方塊。  
  
    4.  在 **啟動完整搜耙**區域中，選取**此內容來源啟動完整搜耙**核取方塊，然後按一下**確定**。  
  
         ![新增內容來源](../../adapters-and-accelerators/adapter-oracle-ebs/media/27-add-content-source.gif "27_Add_Content_Source")  
  
10. 您會返回 [管理內容來源] 頁面，以加入新的內容來源。 內容的來源將 Oracle E-business Suite 中 MS_SAMPLE_EMPLOYEE 介面資料表中的資料進行編目。 等候編目完成。  
  
11. 在左窗格的下**耙梳**，按一下**搜耙記錄檔**，然後確認 記錄檔，以確保編目成功。  
  
##  <a name="Scope"></a> 定義編目的內容範圍  
  
1. 啟動 SharePoint 3.0 管理中心。 按一下 **開始**，指向**所有程式**，指向**Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2. 在左側的導覽窗格中，按一下名稱的共用服務提供者 (SSP) 您要設定搜尋應用程式。  
  
3. 在 [首頁] 頁面中，在**搜尋**區段中，按一下**搜尋設定**。  
  
4. 在設定搜尋設定 頁面上，在左窗格的下**查詢，並產生**，按一下**範圍**來定義資料的耙梳的範圍。  
  
5. 在 檢視領域 頁面中，按一下 **新的範圍**。  
  
6. 在 [建立領域] 頁面中，輸入`MS_SAMPLE_EMPLOYEE_Search`中**Title**方塊，然後再按一下**確定**。  
  
    ![建立領域](../../adapters-and-accelerators/adapter-oracle-ebs/media/28-create-scope.gif "28_Create_Scope")  
  
7. 您會回到檢視領域 頁面，以新增新範圍。 在 **更新狀態**資料行，新加入的範圍中，按一下**新增規則**連結。  
  
8. 在 新增範圍規則頁面上：  
  
   1.  在 **範圍規則類型**區域中，按一下**內容來源**。  
  
   2.  在 **內容的來源**清單中，按一下**MS_SAMPLE_EMPLOYEE**，然後按一下**確定**。  
  
        ![新增範圍規則](../../adapters-and-accelerators/adapter-oracle-ebs/media/29-add-scope-rule.gif "29_Add_Scope_Rule")  
  
9. 新增範圍規則，您會回到檢視領域 頁面。 在左窗格中，按一下**搜尋管理**。  
  
10. 在 [搜尋] 頁面，找出**需要更新的範圍**資料列，然後按一下**立即開始更新**連結。  
  
    **範圍的更新狀態**資料列都會顯示範圍更新的狀態。 等候更新完成。 更新完成後，範圍是已備妥可用。  
  
##  <a name="AddScope"></a> 將範圍新增至搜尋下拉式清單中  
 您已建立的搜尋範圍之後，您必須加入範圍在 Microsoft Office SharePoint Server 搜尋下拉式清單中，可以使用。  
  
#### <a name="to-add-the-scope-to-the-search-dropdown"></a>若要將範圍新增至搜尋下拉式清單中  
  
1.  啟動 SharePoint 3.0 管理中心。 按一下 **開始**，指向**所有程式**，指向**Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.  
  
2.  在左側的導覽窗格中，按一下名稱的共用服務提供者 (SSP) 您要設定搜尋應用程式。  
  
3.  在共用服務管理 頁面的右上角，按一下**站台動作**，然後按一下**站台設定**。  
  
4.  在站台設定 頁面中**網站集合管理**區段中，按一下**搜尋範圍**。  
  
5.  在 檢視領域 頁面中，按一下 **搜尋下拉式清單中**連結。  
  
     ![檢視範圍](../../adapters-and-accelerators/adapter-oracle-ebs/media/30-view-scope.gif "30_View_Scope")  
  
6.  在編輯範圍顯示群組 頁面上：  
  
    1.  在 **領域**區域中，選取**MS_SAMPLE_EMPLOYEE_Search**核取方塊。  
  
    2.  在 **預設範圍**區域中，按一下**MS_SAMPLE_EMPLOYEE_Search**中**預設範圍**清單，然後再按**確定**。  
  
         ![編輯範圍顯示群組頁面](../../adapters-and-accelerators/adapter-oracle-ebs/media/31-edit-scope-display-group.gif "31_Edit_Scope_Display_Group")  
  
7.  您會回到與 MS_SAMPLE_EMPLOYEE_Search 範圍搜尋下拉式清單中顯示群組中新增的檢視領域 頁面。  
  
##  <a name="SearchWebPart"></a> 新增搜尋方塊 Web 組件  
 若要啟用使用者執行 Oracle E-business Suite 的 MS_SAMPLE_EMPLOYEE 介面資料表的全文檢索搜尋，，您必須現在建立網頁組件，並在搜尋方塊 Web 組件加入。  
  
#### <a name="to-add-the-search-box-web-part"></a>若要新增搜尋方塊 Web 組件  
  
1.  建立一個稱為 網頁組件頁面**MS_SAMPLE_EMPLOYEE_Search**。 若要了解建立 Web 組件頁面的步驟，請參閱[案例 1： 使用商務資料清單 web 組件顯示資料](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md)中[案例 1： 使用商務資料清單 web 組件顯示資料](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md)。  
  
2.  在 MS_SAMPLE_EMPLOYEE_Search 頁面上，按一下**新增網頁組件**。  
  
3.  在**新增網頁組件**對話方塊中，於**搜尋**區段中，選取**搜尋方塊**核取方塊，然後按一下**新增**。  
  
     ![新增搜尋方塊 Web 組件](../../adapters-and-accelerators/adapter-oracle-ebs/media/32-search-web-part.gif "32_Search_Web_Part")  
  
4.  搜尋方塊 Web 組件會加入 MS_SAMPLE_EMPLOYEE_Search 頁面。  
  
     ![搜尋方塊 」 Web 組件](../../adapters-and-accelerators/adapter-oracle-ebs/media/33-search-web-part-final.gif "33_Search_Web_Part_Final")  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 建立 SharePoint 應用程式來擷取 Oracle E-business Suite 中的資料](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md)  
 [案例 1：使用商務資料清單 Web 組件顯示資料](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md)