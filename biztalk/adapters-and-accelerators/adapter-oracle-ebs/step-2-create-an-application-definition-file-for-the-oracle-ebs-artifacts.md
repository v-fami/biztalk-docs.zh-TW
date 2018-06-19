---
title: 步驟 2： 建立 Oracle E-business Suite 成品的應用程式定義檔 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2665afde-0337-4795-ab4c-6223d39fdf9c
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ed4340893d351d8406212b585e6216de19c634c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22219302"
---
# <a name="step-2-create-an-application-definition-file-for-the-oracle-e-business-suite-artifacts"></a>步驟 2： 建立 Oracle E-business Suite 成品的應用程式定義檔
![步驟 4 之 2](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **若要完成的時間：** 15 分鐘  
  
 **目標：** Microsoft SharePoint Server 中的商務資料目錄功能會公開，並從的特定業務 (LOB) 應用程式的資料合併至入口網站。 將此資料合併到您的入口網站，您必須建立 Microsoft Office SharePoint Server 可以使用應用程式定義檔。  
  
 商務資料目錄定義編輯器工具，適用於 Microsoft Office SharePoint Server 2007 SDK，可讓您建立的商務資料目錄的應用程式定義檔。 此工具會自動產生定義檔的 XML 檔案，因此您不需要手動將檔案在編輯器中建立 XML。  
  
 您正在建立 Microsoft Office SharePoint Server 應用程式的用途是：  
  
-   使用商務資料清單網頁組件在 MS_SAMPLE_EMPLOYEE 介面資料表中員工的查詢會根據員工名稱。  
  
-   從 Microsoft Office SharePoint Server MS_SAMPLE_EMPLOYEE 介面資料表執行全文檢索搜尋。  
  
 針對每個這些需求，您必須完成一的組商務資料目錄定義編輯器工具中的工作。 本主題提供有關如何執行這些工作的指示。  
  
## <a name="prerequisites"></a>必要條件  
  
-   請確定您有商務資料目錄定義編輯器安裝 Microsoft Office SharePoint Server 2007 SDK 的一部分。 您可以下載從 SDK [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130)。  
  
-   發佈 WCF 服務中所述[步驟 1： 使用 Oracle E-business 配接器，以建立並發佈 WCF 服務](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md)。  
  

  
##  <a name="Connect"></a>連接到 WCF LOB 服務和建立實體  
 您必須連接至 WCF 服務，以擷取 Web 服務描述語言 (WSDL) 服務。 從 WSDL，商務資料目錄定義編輯器中擷取的方法。 這些方法可以用來建立實體。 此教學課程中，建立實體。  
  
#### <a name="to-connect-to-the-wcf-service-and-create-entities"></a>連接到 WCF 服務，並建立實體  
  
1.  啟動商務資料目錄定義編輯器。 在**啟動**功能表上，按一下  **Microsoft 商務資料目錄定義編輯器**。  
  
2.  在工具列上，按一下  **LOB 系統**。  
  
3.  在 [新增 LOB 系統] 視窗中，按一下**連接到 Webservice**。  
  
4.  在**URL**方塊中，輸入 WCF 服務的 URL。 此教學課程中，URL 將是：  
  
    ```  
    https://<COMPUTER_NAME>:<PORT_NUMBER>/MS_SAMPLE_EMPLOYEE/InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE.svc  
    ```  
  
     URL 在您測試是否成功中, 所述發行 WCF 服務時使用[步驟 1： 使用 Oracle E-business 配接器，以建立並發佈 WCF 服務](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md)。  
  
5.  按一下 **[連接]**。  
  
6.  若要查看您在 WCF 配接器服務開發精靈中選取的作業，請按一下**新增 Web 方法** 索引標籤。您會看到下列方法：**選取**。  
  
7.  拖曳**選取**至設計介面的方法。 當您將方法拖曳至設計介面，建立實體，並方法會成為該實體的一部分。  
  
     ![將選取的方法加入至設計介面](../../adapters-and-accelerators/adapter-oracle-ebs/media/05-add-lob-system.gif "05_Add_LOB_System")  
  
8.  按一下 **[確定]**。  
  
9. 在**輸入 LOB 系統的名稱**對話方塊內輸入名稱**LOB 系統名稱**方塊。 針對此範例中，呼叫它**MS_SAMPLE_EMPLOYEE**，然後按一下 **確定**。  
  
10. 在商務資料目錄定義編輯器中，新建立的實體會列為**Entity0**。 重新命名的實體**員工**。 執行下列步驟來重新命名實體：  
  
    1.  展開**MS_SAMPLE_EMPLOYEE**  節點，然後展開**實體**節點。  
  
    2.  選取**Entity0**節點。  
  
    3.  在 [屬性] 窗格中，輸入**員工**中**名稱**方塊。  
  
         ![重新命名實體](../../adapters-and-accelerators/adapter-oracle-ebs/media/06-entity-name.gif "06_Entity_Name")  
  
##  <a name="Headers"></a>指定使用者名稱和密碼標頭方法  
 建立 WCF 服務時 MS_SAMPLE_EMPLOYEE 介面資料表的 Select 作業 Oracle E-business Suite 中，您會指定使用者名稱和密碼標頭中的端點行為組態的一部分[步驟 1： 使用 OracleE-business 配接器來建立和發佈的 WCF 服務](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md)。 您必須指定相同屬性之值的 Select 方法。  
  
#### <a name="to-specify-user-name-and-password-headers-for-the-select-method"></a>若要指定使用者名稱和密碼標頭 Select 方法  
  
1.  在 中繼資料物件 窗格中，依序展開**員工** 節點，然後展開**方法**節點。  
  
2.  按一下**選取**] 節點，在 [屬性] 窗格中按一下 [省略符號 （...） 按鈕，針對**屬性**方塊。  
  
3.  在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**HttpHeaderUserName**如**名稱**方塊。 型別**MyUserHeader**如**PropertyValue**方塊。 選取**System.String**如**類型**方塊。  
  
4.  在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**HttpHeaderPassword**如**名稱**方塊。 同樣地，輸入**MyPasswordHeader**如**PropertyValue**方塊。 選取**System.String**如**類型**方塊。  
  
     ![將屬性加入](../../adapters-and-accelerators/adapter-oracle-ebs/media/07-propertviewcollection-editor.gif "07_PropertViewCollection_Editor")  
  
5.  按一下 **[確定]**。  
  
##  <a name="Scenario1"></a>使用商務資料清單網頁組件的員工的案例 1： 查詢  
 若要建立的應用程式定義檔可以用來搜尋員工從商務資料清單網頁組件，並根據員工的名稱，您必須執行下列工作集合。  
  
1.  在**選取**方法，建立篩選器，並將它對應至**篩選**參數。  
  
2.  建立**Finder**方法執行個體，如**選取**方法。 A **Finder**方法會擷取篩選條件的所有記錄的清單。  
  
#### <a name="to-create-a-filter-and-map-it-to-the-filter-parameter"></a>若要建立篩選器，並將其對應的 FILTER 參數  
  
1.  建立篩選。  
  
    1.  在 中繼資料物件 窗格中，依序展開**員工** 節點，然後展開**方法**節點。  
  
    2.  展開**選取**方法，以滑鼠右鍵按一下**篩選**，然後按一下 **加入篩選條件**。  
  
         ![將篩選加入至 SELECT 方法](../../adapters-and-accelerators/adapter-oracle-ebs/media/08-add-filter.gif "08_Add_Filter")  
  
    3.  在 [屬性] 窗格中，針對**FilterType**屬性選取**等於**。  
  
    4.  在 [屬性] 窗格中，輸入**員工姓名**中**名稱**方塊。  
  
         ![指定篩選屬性](../../adapters-and-accelerators/adapter-oracle-ebs/media/09-filter-properties.gif "09_Filter_Properties")  
  
2.  對應至篩選器**篩選**中的參數**選取**方法。  
  
    1.  在 中繼資料物件 窗格中，依序展開**員工** 節點，然後展開**方法**節點。  
  
    2.  展開**選取**方法，然後展開**參數**節點。  
  
    3.  展開**篩選** 節點，然後按一下第二個**篩選**節點。  
  
    4.  在 [屬性] 窗格中，選取**員工姓名**從**FilterDescriptor**清單。  
  
         ![對應至 Select 方法參數的篩選器](../../adapters-and-accelerators/adapter-oracle-ebs/media/10-map-filter.gif "10_Map_Filter")  
  
#### <a name="to-create-a-finder-method-instance-for-the-select-method"></a>若要建立 Finder 方法執行個體，如 Select 方法  
  
1.  在 中繼資料物件 窗格中，依序展開**員工** 節點，然後展開**方法**節點。  
  
2.  展開**選取**] 節點，以滑鼠右鍵按一下**執行個體**，然後按一下 [**新增方法執行個體**。  
  
     ![新增方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")  
  
3.  在 [建立方法執行個體] 視窗中，按一下**Finder**如**方法執行個體類型**。 選取**傳回**如**傳回 TypeDescriptor**。  
  
     ![建立 Finder 方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/12-create-method-instance.gif "12_Create_Method_Instance")  
  
4.  按一下 **[確定]**。  
  
5.  在 [屬性] 窗格中，輸入**Finder_Instance**中**名稱**方塊。  
  
     ![指定 Finder 方法執行個體的名稱](../../adapters-and-accelerators/adapter-oracle-ebs/media/13-instance-property.gif "13_Instance_Property")  
  
##  <a name="Scenario2"></a>案例 2： 從 Microsoft Office SharePoint Server MS_SAMPLE_EMPLOYEE 介面資料表上的全文檢索搜尋  
 若要建立可以用來執行全文檢索搜尋 MS_SAMPLE_EMPLOYEE 介面資料表，從 Microsoft Office SharePoint Server 上的應用程式定義檔，您必須執行下列工作集合。  
  
-   在**選取**方法，建立識別項，並將其對應的 FILTER 參數和傳回值，會儲存員工名稱。  
  
-   建立**特定搜尋工具**方法執行個體，如**選取**。 **特定搜尋工具**方法會尋找特定的記錄識別碼為基礎，也就是員工名稱。  
  
-   建立 ID Enumerator 方法執行個體。  
  
#### <a name="to-create-an-identifier-and-map-it-to-the-filter-parameter-and-employee-name-return-value"></a>建立識別項，並將其對應的篩選參數] 和 [員工名稱傳回值  
  
1.  建立識別碼**員工**實體。  
  
    1.  在 [中繼資料物件] 窗格中，依序展開**員工**節點。  
  
    2.  以滑鼠右鍵按一下**識別碼**節點，然後再選取**新增識別項**。  
  
         ![建立識別碼](../../adapters-and-accelerators/adapter-oracle-ebs/media/14-create-identifier.gif "14_Create_Identifier")  
  
    3.  在 [屬性] 窗格中，輸入**員工姓名**中**名稱**方塊。  
  
    4.  選取**System.String**如**類型**方塊。  
  
         ![指定識別碼屬性](../../adapters-and-accelerators/adapter-oracle-ebs/media/15-identifier-properties.gif "15_Identifier_Properties")  
  
2.  將識別碼對應至篩選參數，如**選取**方法。  
  
    1.  在 中繼資料物件 窗格中，依序展開**員工** 節點，然後展開**方法**節點。  
  
    2.  展開**選取**方法，然後展開**參數**節點。  
  
    3.  展開**篩選**參數，然後按一下第二個**篩選**節點。  
  
    4.  在 [屬性] 窗格中，選取**員工姓名 [員工]** 從**識別碼**清單。  
  
         ![設定 FILTER 參數的識別項](../../adapters-and-accelerators/adapter-oracle-ebs/media/16-set-identifier.gif "16_Set_Identifier")  
  
3.  將識別碼對應至員工名稱的傳回值。  
  
    1.  在 中繼資料物件 窗格中，依序展開**員工** 節點，然後展開**方法**節點。  
  
    2.  展開**選取**方法，然後展開**參數**節點。  
  
    3.  展開**傳回**節點，然後第二個**傳回** 節點，然後在**項目**節點，然後再按一下**名稱**節點。  
  
    4.  在 [屬性] 窗格中，選取**員工姓名 [員工]** 從**識別碼**清單。  
  
#### <a name="to-create-a-specific-finder-method-instance-for-the-select-method"></a>若要建立特定的 Finder 方法執行個體，如 Select 方法  
  
1.  在 中繼資料物件 窗格中，依序展開**員工** 節點，然後**方法**節點。  
  
2.  展開**選取** 節點，以滑鼠右鍵按一下**執行個體**，然後選取**新增方法執行個體**開啟 建立方法執行個體 視窗。  
  
     ![新增方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")  
  
3.  在 [建立方法執行個體] 視窗中，選取**特定搜尋工具**如**方法執行個體類型**。 選取**傳回**如**傳回 TypeDescriptor**。  
  
     ![新增 Specific Finder 方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/17-specific-finder.gif "17_Specific_Finder")  
  
4.  按一下 **[確定]**。  
  
5.  在 [屬性] 窗格中，輸入**SpeciFinder_Instance**如**名稱**方塊。  
  
#### <a name="to-create-an-id-enumerator-method-instance-for-the-select-method"></a>若要建立 Id Enumerator 方法執行個體的 Select 方法  
  
1.  在 中繼資料物件 窗格中，依序展開**員工** 節點，然後**方法**節點。  
  
2.  展開**選取** 節點，以滑鼠右鍵按一下**執行個體**，然後選取**新增方法執行個體**開啟 建立方法執行個體 視窗。  
  
     ![新增方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")  
  
3.  在 [建立方法執行個體] 視窗中，選取**Id Enumerator**如**方法執行個體類型**。 選取**傳回**如**傳回 TypeDescriptor**。  
  
     ![建立 Id Enumerator 方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/18-id-enumerator.gif "18_ID_Enumerator")  
  
4.  按一下 **[確定]**。  
  
5.  在 [屬性] 窗格中，輸入**IDEnumerator_Instance**如**名稱**方塊。  
  
##  <a name="Defaults"></a>設定方法的執行個體的預設參數  
 選取方法會要求您指定的資料行名稱。 因此，您需要指定預設值為**COLUMN_NAMES**稍早建立的搜尋、 特定的搜尋和 Id Enumerator 方法執行個體的參數。 此外，您也應該指定的預設值**篩選**Id Enumerator 方法執行個體的參數。  
  
#### <a name="to-set-the-default-parameters-for-the-method-instances"></a>若要設定的方法執行個體的預設參數  
  
1.  在 中繼資料物件 窗格中，依序展開**員工** 節點，然後展開**方法**節點。  
  
2.  展開**選取** 節點，然後展開**參數**節點。  
  
3.  展開**COLUMN_NAMES**節點，然後再選取**COLUMN_NAMES**參數。  
  
4.  在 屬性 窗格中，按一下 省略符號按鈕 （...），以針對**DefaultValues**方塊。  
  
5.  在**DefaultValueView 集合編輯器**對話方塊中，按一下 **新增**，然後在 屬性 窗格中，按一下**Finder_Instance**中**SelectMethodInstance**清單。  
  
     ![指定 Finder 執行個體的預設值](../../adapters-and-accelerators/adapter-oracle-ebs/media/19-finderinstance-defaults.gif "19_FinderInstance_Defaults")  
  
6.  型別`*`中**值**方塊。  
  
7.  同樣地，重複步驟 5 和 6，新增的預設值**SpecificFinder_Instance**和**IDEnumerator_Instance**方法執行個體。  
  
8.  在**DefaultValueView 集合編輯器**對話方塊中，按一下 **確定**。  
  
9. 接下來，新增的預設值**篩選**參數**IDEnumerator_Instance**方法執行個體。 展開**篩選**節點，然後再選取**篩選**參數。  
  
10. 在 屬性 窗格中，按一下 省略符號按鈕 （...），以針對**DefaultValues**方塊。  
  
11. 在**DefaultValueView 集合編輯器**對話方塊中，按一下 **新增**，然後在 屬性 窗格中，按一下**IDEnumerator_Instance**中**SelectMethodInstance**清單。  
  
12. 型別`%`中**值**方塊。  
  
     ![Id Enumerator 執行個體的預設值](../../adapters-and-accelerators/adapter-oracle-ebs/media/20-idenumeratorinstance-defaults.gif "20_IDEnumeratorInstance_Defaults")  
  
13. 在**DefaultValueView 集合編輯器**對話方塊中，按一下 **確定**。  
  
##  <a name="SSO"></a>連接到 Oracle E-business Suite 設定單一登入設定  
 執行本主題中的所有程序完成之後，您將建立可匯入 SharePoint 應用程式的應用程式定義檔。 從應用程式，您叫用的方法來擷取 Oracle E-business Suite 中的相關資料。 若要啟用此功能，您必須在 SharePoint 應用程式中建立 Oracle E-business Suite 中的使用者與使用者之間的對應。 您已匯入應用程式定義檔之後，您可以建立在 SharePoint 管理中心主控台中的此對應。  
  
 不過，若要建立對應您必須設定屬性**SecondarySsoApplicationId**中商務資料目錄定義編輯器。  
  
#### <a name="to-set-the-secondaryssoapplicationid-property"></a>若要設定 SecondarySsoApplicationId 屬性  
  
1.  在 中繼資料物件 窗格中，依序展開**MS_SAMPLE_EMPLOYEE**  節點，然後展開**執行個體**節點。  
  
2.  按一下**MS_SAMPLE_EMPLOYEE_Instance**，在 屬性 窗格中，按一下 省略符號 （...） 按鈕，針對**屬性**方塊。  
  
3.  在**PropertyView 集合編輯器**對話方塊中，按一下 **新增**，然後在 屬性 窗格中，輸入**SecondarySsoApplicationId**如**名稱**方塊。 同樣地，輸入**OracleSSO**如**PropertyValue**方塊。 選取**System.String**如**類型**方塊。  
  
     ![新增 SSO 屬性](../../adapters-and-accelerators/adapter-oracle-ebs/media/21-sso.gif "21_SSO")  
  
4.  按一下 **[確定]**。  
  
##  <a name="Export"></a>應用程式定義匯出至檔案  
 您現在已建立應用程式定義，其中包含 Oracle E-business Suite 執行個體中繼資料。 您必須將此定義匯出至 XML 檔案，可以匯入 Microsoft Office SharePoint Server。  
  
#### <a name="to-export-the-application-definition-to-a-file"></a>若要將應用程式定義匯出至檔案  
  
1.  在 [中繼資料物件] 窗格中，以滑鼠右鍵按一下**MS_SAMPLE_EMPLOYEE**節點，然後再按一下**匯出**。  
  
2.  將檔案儲存為 Employee.xml。  
  
## <a name="next-steps"></a>後續步驟  
 您現在必須建立 SharePoint 應用程式來擷取 Oracle E-business Suite 中的資料。 如需指示，請參閱[步驟 3： 建立 SharePoint 應用程式以擷取資料從 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程： 從 SharePoint 網站上的 Oracle E-business Suite 中呈現的資料](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)