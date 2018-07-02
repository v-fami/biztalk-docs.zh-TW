---
title: 步驟 2： 建立 Oracle E-business Suite 成品的應用程式定義檔 |Microsoft Docs
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
ms.openlocfilehash: f0bd73da129e978bfe2d4ad5af2b4f26fb9bcc16
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970751"
---
# <a name="step-2-create-an-application-definition-file-for-the-oracle-e-business-suite-artifacts"></a>步驟 2： 建立 Oracle E-business Suite 成品的應用程式定義檔
![步驟 4 之 2](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **若要完成的時間：** 15 分鐘  
  
 **目標：** Microsoft SharePoint Server 中的商務資料目錄 」 功能會公開，並併入入口網站中的資料列的商務 (LOB) 應用程式。 若要併入您的入口網站中的這項資料，您必須建置可取用 Microsoft Office SharePoint Server 的應用程式定義檔。  
  
 Business Data Catalog Definition Editor 工具，適用於 Microsoft Office SharePoint Server 2007 SDK，可讓您的商務資料目錄中建立應用程式定義檔案。 此工具會自動產生 XML 檔案定義檔，因此您不需要手動建立檔案的 xml 編輯器。  
  
 Microsoft Office SharePoint Server 應用程式所建立的目的是：  
  
- 使用商務資料清單 Web 組件 MS_SAMPLE_EMPLOYEE 介面資料表中員工的查詢會根據員工名稱。  
  
- 從 Microsoft Office SharePoint Server 對 MS_SAMPLE_EMPLOYEE 介面資料表的全文檢索搜尋。  
  
  針對每個這些需求，您必須完成一的組 「 商務資料目錄定義編輯器 」 工具中的工作。 本主題提供有關如何執行這些工作的指示。  
  
## <a name="prerequisites"></a>必要條件  
  
-   請確定您已安裝 Microsoft Office SharePoint Server 2007 SDK 的一部分為商務資料目錄定義編輯器。 您可以下載從 SDK [ http://go.microsoft.com/fwlink/?LinkId=104130 ](http://go.microsoft.com/fwlink/?LinkId=104130)。  
  
-   發佈 WCF 服務中所述[步驟 1： 使用 Oracle E-business 配接器，來建立及發佈 WCF 服務](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md)。  
  

  
##  <a name="Connect"></a> 連線到 WCF LOB 服務並建立實體  
 您必須連接至 WCF 服務，以擷取 Web 服務描述語言 (WSDL) 服務。 商務資料目錄定義編輯器會根據 WSDL、 擷取方法。 這些方法可用來建立實體。 本教學課程中，建立實體。  
  
#### <a name="to-connect-to-the-wcf-service-and-create-entities"></a>連接到 WCF 服務，並建立實體  
  
1.  啟動商務資料目錄定義編輯器。 在 **開始**功能表上，按一下**Microsoft Business Data Catalog Definition Editor**。  
  
2.  在工具列上，按一下**新增 LOB 系統**。  
  
3.  在 [新增 LOB 系統] 視窗中，按一下**連接到 web 服務**。  
  
4.  在  **URL**方塊中，輸入 WCF 服務的 URL。 本教學課程中，URL 會是：  
  
    ```  
    https://<COMPUTER_NAME>:<PORT_NUMBER>/MS_SAMPLE_EMPLOYEE/InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE.svc  
    ```  
  
     當您測試是否成功，如中所述發行 WCF 服務時，URL 是可用[步驟 1： 使用 Oracle E-business 配接器，來建立及發佈 WCF 服務](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md)。  
  
5.  按一下 **[連接]**。  
  
6.  若要查看您在 WCF 配接器服務開發精靈中選取的作業，請按一下**新增 Web 方法** 索引標籤。您會看到下列方法：**選取**。  
  
7.  拖曳**選取**至設計介面的方法。 當您將方法拖曳至設計介面時，建立實體，且方法該實體的一部分。  
  
     ![將選取的方法加入至設計介面](../../adapters-and-accelerators/adapter-oracle-ebs/media/05-add-lob-system.gif "05_Add_LOB_System")  
  
8.  按一下 [確定] 。  
  
9. 在 **輸入 LOB 系統的名稱** 對話方塊中，輸入的名稱，在**LOB 系統名稱** 方塊中。 針對此範例中，呼叫它**MS_SAMPLE_EMPLOYEE**，然後按一下**確定**。  
  
10. 在商務資料目錄定義編輯器中，新建立的實體會列為**Entity0**。 重新命名的實體**員工**。 執行下列步驟來重新命名實體：  
  
    1.  依序展開**MS_SAMPLE_EMPLOYEE**節點，然後展開**實體**節點。  
  
    2.  選取  **Entity0**節點。  
  
    3.  在 屬性 窗格中，輸入**員工**中**名稱** 方塊中。  
  
         ![重新命名實體](../../adapters-and-accelerators/adapter-oracle-ebs/media/06-entity-name.gif "06_Entity_Name")  
  
##  <a name="Headers"></a> 指定使用者名稱和密碼標頭方法  
 建立 WCF 服務時選取作業 MS_SAMPLE_EMPLOYEE 介面資料表上 Oracle E-business Suite 中，您會指定使用者名稱和密碼標頭中的端點行為組態的一部分[步驟 1： 使用 Oracle若要建立及發佈 WCF 服務的 E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md)。 您必須指定相同的值，Select 方法屬性。  
  
#### <a name="to-specify-user-name-and-password-headers-for-the-select-method"></a>若要指定使用者名稱和密碼標頭 Select 方法  
  
1.  在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後展開**方法**節點。  
  
2.  按一下 **選取 **節點，並在 屬性 窗格中，按一下 省略符號 （...） 按鈕，針對**屬性** 方塊中。  
  
3.  在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**HttpHeaderUserName** for**名稱** 方塊中。 型別**MyUserHeader** for **PropertyValue**  方塊中。 選取 [ **System.String** for**型別**] 方塊中。  
  
4.  在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**HttpHeaderPassword** for**名稱** 方塊中。 同樣地，輸入**MyPasswordHeader** for **PropertyValue**  方塊中。 選取 [ **System.String** for**型別**] 方塊中。  
  
     ![將屬性加入](../../adapters-and-accelerators/adapter-oracle-ebs/media/07-propertviewcollection-editor.gif "07_PropertViewCollection_Editor")  
  
5.  按一下 [確定] 。  
  
##  <a name="Scenario1"></a> 使用商務資料清單 Web 組件的員工的案例 1： 查詢  
 若要建立的應用程式定義檔案可以用來搜尋員工的商務資料清單 Web 組件，並根據員工的名稱，您必須執行下列一組工作。  
  
1.  在 **選取 **方法，建立篩選器，並將它對應至**篩選**參數。  
  
2.  建立**Finder**方法執行個體**選取**方法。 A **Finder**方法會擷取篩選為基礎的記錄清單。  
  
#### <a name="to-create-a-filter-and-map-it-to-the-filter-parameter"></a>若要建立篩選器，並將它對應至篩選參數  
  
1.  建立篩選。  
  
    1.  在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後展開**方法**節點。  
  
    2.  依序展開**選取**方法，以滑鼠右鍵按一下**篩選**，然後按一下**加入篩選**。  
  
         ![將篩選加入至 SELECT 方法](../../adapters-and-accelerators/adapter-oracle-ebs/media/08-add-filter.gif "08_Add_Filter")  
  
    3.  在 [屬性] 窗格中，如**FilterType**屬性中，選取**等於**。  
  
    4.  在 屬性 窗格中，輸入**EmployeeName**中**名稱** 方塊中。  
  
         ![指定篩選條件屬性](../../adapters-and-accelerators/adapter-oracle-ebs/media/09-filter-properties.gif "09_Filter_Properties")  
  
2.  若要將篩選器對應**篩選條件**中的參數**選取**方法。  
  
    1.  在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後展開**方法**節點。  
  
    2.  依序展開**選取 **方法，然後展開**參數**節點。  
  
    3.  依序展開**篩選器**節點，然後按一下第二個**篩選**節點。  
  
    4.  在 [屬性] 窗格中，選取**EmployeeName**從**FilterDescriptor**清單。  
  
         ![將篩選條件對應至 Select 方法參數](../../adapters-and-accelerators/adapter-oracle-ebs/media/10-map-filter.gif "10_Map_Filter")  
  
#### <a name="to-create-a-finder-method-instance-for-the-select-method"></a>若要建立 Finder 方法執行個體，Select 方法  
  
1.  在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後展開**方法**節點。  
  
2.  依序展開**選取 **節點，以滑鼠右鍵按一下**執行個體**，然後按一下 **新增方法執行個體**。  
  
     ![新增方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")  
  
3.  在 [建立方法執行個體] 視窗中，按一下**Finder** for**方法執行個體類型**。 選取 **會傳回**for**的傳回 TypeDescriptor**。  
  
     ![建立 Finder 方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/12-create-method-instance.gif "12_Create_Method_Instance")  
  
4.  按一下 [確定] 。  
  
5.  在 屬性 窗格中，輸入**Finder_Instance**中**名稱** 方塊中。  
  
     ![指定 Finder 方法執行個體的名稱](../../adapters-and-accelerators/adapter-oracle-ebs/media/13-instance-property.gif "13_Instance_Property")  
  
##  <a name="Scenario2"></a> 案例 2： 從 Microsoft Office SharePoint Server MS_SAMPLE_EMPLOYEE 介面資料表上的全文檢索搜尋  
 若要建立可用來從 Microsoft Office SharePoint Server MS_SAMPLE_EMPLOYEE 介面資料表上執行的全文檢索搜尋的應用程式定義檔，您必須執行下列一組工作。  
  
-   在 **選取**方法，建立識別項，並將它對應至篩選參數和傳回值可儲存員工名稱。  
  
-   建立**特定的 Finder**方法執行個體**選取**。 **特定的 Finder**方法可以找出特定的記錄識別碼為基礎，也就是將員工的姓名。  
  
-   建立 ID Enumerator 方法執行個體。  
  
#### <a name="to-create-an-identifier-and-map-it-to-the-filter-parameter-and-employee-name-return-value"></a>建立識別項，並將其對應至篩選參數及員工名稱傳回值  
  
1.  建立的識別項**員工**實體。  
  
    1.  在 [中繼資料物件] 窗格中，依序展開**員工**節點。  
  
    2.  以滑鼠右鍵按一下**識別碼**節點，，然後選取**新增識別碼**。  
  
         ![建立識別項](../../adapters-and-accelerators/adapter-oracle-ebs/media/14-create-identifier.gif "14_Create_Identifier")  
  
    3.  在 屬性 窗格中，輸入**EmployeeName**中**名稱** 方塊中。  
  
    4.  選取 [ **System.String** for**型別**] 方塊中。  
  
         ![指定識別項屬性](../../adapters-and-accelerators/adapter-oracle-ebs/media/15-identifier-properties.gif "15_Identifier_Properties")  
  
2.  將識別碼對應至篩選參數，如**選取**方法。  
  
    1.  在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後展開**方法**節點。  
  
    2.  依序展開**選取 **方法，然後展開**參數**節點。  
  
    3.  依序展開**篩選條件**參數，然後按一下 第二個**篩選**節點。  
  
    4.  在 [屬性] 窗格中，選取**EmployeeName [Employee]** 從**識別項**清單。  
  
         ![設定 FILTER 參數的識別項](../../adapters-and-accelerators/adapter-oracle-ebs/media/16-set-identifier.gif "16_Set_Identifier")  
  
3.  將識別碼對應至員工名稱的傳回值。  
  
    1.  在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後展開**方法**節點。  
  
    2.  依序展開**選取 **方法，然後展開**參數**節點。  
  
    3.  依序展開**會傳回**節點，然後第二個**傳回**節點，則**項目**節點，然後再按一下**名稱**節點。  
  
    4.  在 [屬性] 窗格中，選取**EmployeeName [Employee]** 從**識別項**清單。  
  
#### <a name="to-create-a-specific-finder-method-instance-for-the-select-method"></a>若要建立特定的 Finder 方法執行個體，Select 方法  
  
1.  在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後**方法**節點。  
  
2.  依序展開**選取**節點，以滑鼠右鍵按一下**執行個體**，然後選取**新增方法執行個體**以開啟 [建立方法執行個體] 視窗。  
  
     ![新增方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")  
  
3.  在 [建立方法執行個體] 視窗中，選取**Specific Finder** for**方法執行個體類型**。 選取 **會傳回**for**的傳回 TypeDescriptor**。  
  
     ![新增 Specific Finder 方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/17-specific-finder.gif "17_Specific_Finder")  
  
4.  按一下 [確定] 。  
  
5.  在 屬性 窗格中，輸入**SpeciFinder_Instance** for**名稱** 方塊中。  
  
#### <a name="to-create-an-id-enumerator-method-instance-for-the-select-method"></a>若要建立 Id Enumerator 方法執行個體的 Select 方法  
  
1.  在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後**方法**節點。  
  
2.  依序展開**選取**節點，以滑鼠右鍵按一下**執行個體**，然後選取**新增方法執行個體**以開啟 [建立方法執行個體] 視窗。  
  
     ![新增方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")  
  
3.  在 [建立方法執行個體] 視窗中，選取**Id Enumerator** for**方法執行個體類型**。 選取 **會傳回**for**的傳回 TypeDescriptor**。  
  
     ![建立 Id Enumerator 方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/18-id-enumerator.gif "18_ID_Enumerator")  
  
4.  按一下 [確定] 。  
  
5.  在 屬性 窗格中，輸入**IDEnumerator_Instance** for**名稱** 方塊中。  
  
##  <a name="Defaults"></a> 設定預設參數的方法執行個體  
 Select 方法會要求您指定的資料行名稱。 因此，您需要指定的預設值**COLUMN_NAMES**稍早建立的搜尋、 特定搜尋工具和 Id Enumerator 方法執行個體的參數。 此外，您也應該指定的預設值**篩選**Id Enumerator 方法執行個體的參數。  
  
#### <a name="to-set-the-default-parameters-for-the-method-instances"></a>若要設定的方法執行個體的預設參數  
  
1.  在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後展開**方法**節點。  
  
2.  依序展開**選取 **節點，然後展開**參數**節點。  
  
3.  依序展開**COLUMN_NAMES**節點，，然後選取**COLUMN_NAMES**參數。  
  
4.  在 [屬性] 窗格中，按一下 [省略符號按鈕 （...），以針對**DefaultValues** ] 方塊中。  
  
5.  在  **DefaultValueView 集合編輯器** 對話方塊中，按一下**新增**，然後在 屬性 窗格中，按一下  **Finder_Instance**在**SelectMethodInstance**清單。  
  
     ![指定 Finder 執行個體的預設值](../../adapters-and-accelerators/adapter-oracle-ebs/media/19-finderinstance-defaults.gif "19_FinderInstance_Defaults")  
  
6.  型別`*`中**值** 方塊中。  
  
7.  同樣地，重複步驟 5 和 6 來新增的預設值**SpecificFinder_Instance**並**IDEnumerator_Instance**方法執行個體。  
  
8.  在 [ **DefaultValueView 集合編輯器**] 對話方塊中，按一下**確定**。  
  
9. 接下來，新增的預設值**篩選條件**參數**IDEnumerator_Instance**方法執行個體。 依序展開**篩選條件**節點，，然後選取**篩選**參數。  
  
10. 在 [屬性] 窗格中，按一下 [省略符號按鈕 （...），以針對**DefaultValues** ] 方塊中。  
  
11. 在  **DefaultValueView 集合編輯器** 對話方塊中，按一下**新增**，然後在 屬性 窗格中，按一下  **IDEnumerator_Instance**在**SelectMethodInstance**清單。  
  
12. 型別`%`中**值** 方塊中。  
  
     ![Id Enumerator 執行個體的預設值](../../adapters-and-accelerators/adapter-oracle-ebs/media/20-idenumeratorinstance-defaults.gif "20_IDEnumeratorInstance_Defaults")  
  
13. 在 [ **DefaultValueView 集合編輯器**] 對話方塊中，按一下**確定**。  
  
##  <a name="SSO"></a> 連線到 Oracle E-business Suite 中設定單一登入設定  
 執行本主題中的所有程序完成之後，您會建立可匯入 SharePoint 應用程式的應用程式定義檔。 從應用程式，您叫用的方法來擷取 Oracle E-business Suite 中的相關資料。 若要這麼做，您必須在 SharePoint 應用程式中建立 Oracle E-business Suite 中的使用者與使用者之間的對應。 您已匯入應用程式定義檔之後，您可以建立在 SharePoint 中央系統管理主控台中的這種對應。  
  
 不過，若要建立對應您必須設定屬性**SecondarySsoApplicationId**中商務資料目錄定義編輯器。  
  
#### <a name="to-set-the-secondaryssoapplicationid-property"></a>若要設定 SecondarySsoApplicationId 屬性  
  
1.  在 [中繼資料物件] 窗格中，依序展開**MS_SAMPLE_EMPLOYEE**節點，然後展開**執行個體**節點。  
  
2.  按一下  **MS_SAMPLE_EMPLOYEE_Instance**，並在 屬性 窗格中，按一下 省略符號 （...） 按鈕，針對**屬性** 方塊中。  
  
3.  在  **PropertyView 集合編輯器** 對話方塊中，按一下**新增**，然後在 屬性 窗格中，輸入**SecondarySsoApplicationId**的**名稱**  方塊中。 同樣地，輸入**OracleSSO** for **PropertyValue**  方塊中。 選取 [ **System.String** for**型別**] 方塊中。  
  
     ![新增 SSO 屬性](../../adapters-and-accelerators/adapter-oracle-ebs/media/21-sso.gif "21_SSO")  
  
4.  按一下 [確定] 。  
  
##  <a name="Export"></a> 匯出至檔案的應用程式定義  
 您現在已建立應用程式定義，其中包含 Oracle E-business Suite 執行個體中繼資料。 您必須將此定義匯出至 XML 檔案，可匯入至 Microsoft Office SharePoint Server。  
  
#### <a name="to-export-the-application-definition-to-a-file"></a>若要將應用程式定義匯出至檔案  
  
1.  在 [中繼資料物件] 窗格中，以滑鼠右鍵按一下**MS_SAMPLE_EMPLOYEE**節點，然後再按一下**匯出**。  
  
2.  將檔案儲存為 Employee.xml 中。  
  
## <a name="next-steps"></a>後續步驟  
 您現在必須建立 SharePoint 應用程式來擷取 Oracle E-business Suite 中的資料。 如需相關指示，請參閱 <<c0> [ 步驟 3： 建立 SharePoint 應用程式以擷取資料從 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md)。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程： 將資料呈現從 SharePoint 網站上的 Oracle E-business Suite](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)