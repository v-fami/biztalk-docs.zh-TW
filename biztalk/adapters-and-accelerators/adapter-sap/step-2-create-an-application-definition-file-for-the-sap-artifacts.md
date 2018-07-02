---
title: 步驟 2： 建立 SAP 成品的應用程式定義檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- application definition file, creating a
- Business Data Catalog Definition Editor
- Business Data Catalog
ms.assetid: d254b00e-dbeb-4167-ad57-6f0aa2e7a563
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92e97a54a6818456efd2f4ac55ca7e2fc5bc7c35
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970383"
---
# <a name="step-2-create-an-application-definition-file-for-the-sap-artifacts"></a>步驟 2： 建立 SAP 成品的應用程式定義檔案
![步驟 4 之 2](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **若要完成的時間：** 15 分鐘  
  
 **目標：** Microsoft SharePoint Server 中的商務資料目錄 」 功能會公開，並併入入口網站中的資料列的商務 (LOB) 應用程式。 若要併入您的入口網站中的這項資料，您必須建置可取用 Microsoft Office SharePoint Server 的應用程式定義檔。  
  
 Business Data Catalog Definition Editor 工具，適用於 Microsoft Office SharePoint Server 2007 SDK，可讓您的商務資料目錄中建立應用程式定義檔案。 此工具會自動產生 XML 檔案定義檔，因此您不需要手動建立檔案的 xml 編輯器。  
  
 Microsoft Office SharePoint Server 應用程式所建立的目的是：  
  
- 搜尋客戶名稱為主的 SAP 系統中的客戶。  
  
- 從擷取的客戶清單中選取客戶並擷取客戶詳細資料。  
  
- 從擷取的客戶清單中選取客戶，並擷取客戶的銷售訂單。  
  
  針對每個這些需求，您必須完成一的組 「 商務資料目錄定義編輯器 」 工具中的工作。 本主題提供有關如何執行這些工作的指示。  
  
## <a name="prerequisites"></a>必要條件  
  
-   請確定您已安裝 Microsoft Office SharePoint Server 2007 SDK 的一部分為商務資料目錄定義編輯器。 您可以下載從 SDK [ http://go.microsoft.com/fwlink/?LinkId=104130 ](http://go.microsoft.com/fwlink/?LinkId=104130)。  
  
-   發佈 WCF 服務中所述[步驟 1： 將 SAP 成品，做為 WCF 服務發佈](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md)。  
  
## <a name="creating-an-application-definition-file"></a>建立應用程式定義檔案  
 本主題提供逐步指示來建立 WCF 服務的應用程式定義檔。  
  
### <a name="connect-to-the-wcf-lob-service-and-create-entities"></a>連線到 WCF LOB 服務，並建立實體  
 您必須連接至 WCF 服務，以擷取 Web 服務描述語言 (WSDL) 服務。 商務資料目錄定義編輯器會根據 WSDL、 擷取方法。 這些方法可用來建立實體。 對於此範例中，兩個實體建立，每個客戶和銷售訂單。  
  
##### <a name="to-connect-to-the-wcf-service-and-create-entities"></a>連接到 WCF 服務，並建立實體  
  
1. 啟動商務資料目錄定義編輯器。 在 **開始**功能表上，按一下**Microsoft Business Data Catalog Definition Editor**。  
  
2. 在工具列上，按一下**新增 LOB 系統**。  
  
3. 在 [新增 LOB 系統] 視窗中，按一下**連接到 web 服務**。  
  
4. 在  **URL**方塊中，輸入 WCF 服務的 URL。 這個 URL 必須以下列格式：  
  
   ```  
   https://<computer_name>/Customer_Order/Rfc.svc?wsdl  
   ```  
  
    其中 Rfc.svc 是 Rfc 合約建立的檔案。  
  
    當您測試是否成功，如本主題中所述發行 WCF 服務時，URL 是可用[步驟 1： 將 SAP 成品，做為 WCF 服務發佈](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md)。  
  
5. 按一下 **[連接]**。  
  
6. 若要查看您在 WCF 配接器服務開發精靈中選取的作業，請按一下**新增 Web 方法** 索引標籤。您會看到下列方法：  
  
   - SD_RFC_CUSTOMER_GET  
  
   - BAPI_SALESORDER_GETLIST  
  
      ![新增 web 方法至 BDC 應用程式](../../adapters-and-accelerators/adapter-sap/media/ea411db2-5cf4-4486-83da-57d3fc332448.gif "ea411db2-5cf4-4486-83da-57d3fc332448")  
  
     將方法拖曳至設計介面。 請確定您將這兩種作業拖曳到不同的實體。  
  
     ![建立 web 方法的實體](../../adapters-and-accelerators/adapter-sap/media/ce4e9bc3-1eae-43ae-8375-e44cf19aaffc.gif "ce4e9bc3-1eae-43ae-8375-e44cf19aaffc")  
  
7. 按一下 [確定] 。  
  
8. 在 **輸入 LOB 系統的名稱** 對話方塊中，輸入的名稱，在**LOB 系統名稱** 方塊中。 針對此範例中，呼叫它**Customer_Order**，然後按一下**確定**。  
  
9. 在商務資料目錄定義編輯器中，兩個實體會列為**Entity0**並**Entity1**。 為這些實體指定易記名稱。 重新命名實體針對至 SD_RFC_CUSTOMER_GET**客戶**，並將實體重新命名針對至 BAPI_SALESORDER_GETLIST **SalesOrder**。 執行下列步驟來重新命名實體：  
  
    1.  依序展開**Customer_Order**節點，然後展開**實體**節點。  
  
    2.  選取  **Entity0**節點。  
  
    3.  在 屬性 窗格中，輸入**客戶**中**名稱** 方塊中。  
  
         ![重新命名實體](../../adapters-and-accelerators/adapter-sap/media/4e83a036-3ab7-4f74-9f67-420574219d3d.gif "4e83a036-3ab7-4f74-9f67-420574219d3d")  
  
    4.  選取  **Entity1**節點。  
  
    5.  在 屬性 窗格中，輸入**SalesOrder**中**名稱** 方塊中。  
  
### <a name="specify-user-name-and-password-headers-for-the-methods"></a>指定使用者名稱和密碼標頭方法  
 建立 WCF 服務時的所選的 Rfc SAP 系統中，您可以指定使用者名稱和密碼標頭做為端點行為組態的一部分。 請參閱[步驟 1： 將 SAP 成品發佈為 WCF 服務](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md)。 您必須指定方法屬性相同的值。  
  
##### <a name="to-specify-user-name-and-password-headers"></a>若要指定使用者名稱和密碼標頭  
  
1.  新增 SD_RFC_CUSTOMER_GET 方法的使用者名稱和密碼標頭。  
  
    1.  在 [中繼資料物件] 窗格中，依序展開**客戶**節點，然後展開**方法**節點。  
  
    2.  按一下 [SD_RFC_CUSTOMER_GET] 節點中，並在 [屬性] 窗格中，按一下 [省略符號 （...） 按鈕，針對**屬性**] 方塊中。  
  
    3.  在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**HttpHeaderUserName** for**名稱** 方塊中。 同樣地，輸入**MyUserHeader** for **PropertyValue**  方塊中。 選取 [ **System.String** for**型別**] 方塊中。  
  
         ![將屬性加入](../../adapters-and-accelerators/adapter-sap/media/9eef32ac-8a93-45dc-8d07-12b7dbf961ba.gif "9eef32ac-8a93-45dc-8d07-12b7dbf961ba")  
  
    4.  在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**HttpHeaderPassword** for**名稱** 方塊中。 同樣地，輸入**MyPassHeader** for **PropertyValue**  方塊中。 選取 [ **System.String** for**型別**] 方塊中。  
  
    5.  按一下 [確定] 。  
  
2.  新增 BAPI_SALESORDER_GETLIST 方法的使用者名稱和密碼標頭。  
  
    1.  在 [中繼資料物件] 窗格中，依序展開**SalesOrder**節點，然後展開**方法**節點。  
  
    2.  按一下 [BAPI_SALESORDER_GETLIST] 節點中，並在 [屬性] 窗格中，按一下 [省略符號 （...） 按鈕，針對**屬性**] 方塊中。  
  
    3.  在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**HttpHeaderUserName** for**名稱** 方塊中。 同樣地，輸入**MyUserHeader** for **PropertyValue**  方塊中。 選取 [ **System.String** for**型別**] 方塊中。  
  
    4.  在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**HttpHeaderPassword** for**名稱** 方塊中。 同樣地，輸入**MyPassHeader** for **PropertyValue**  方塊中。 選取 [ **System.String** for**型別**] 方塊中。  
  
    5.  按一下 [確定] 。  
  
### <a name="set-up-single-sign-on-for-connecting-to-the-sap-system"></a>連線到 SAP 系統中設定單一登入設定  
 執行本主題中的所有程序完成之後，您會建立可匯入 SharePoint 應用程式的應用程式定義檔。 從應用程式，您叫用來擷取相關的資料從 SAP 系統的 SAP 方法。 若要這麼做，您必須在 SharePoint 應用程式中建立 SAP 系統中的使用者與使用者之間的對應。 您已匯入應用程式定義檔之後，您可以建立在 SharePoint 中央系統管理主控台中的這種對應。  
  
 不過，若要建立對應您必須設定屬性**SecondarySsoApplicationId**中商務資料目錄定義編輯器。  
  
##### <a name="to-set-the-secondaryssoapplicationid-property"></a>若要設定 SecondarySsoApplicationId 屬性  
  
1.  在 [中繼資料物件] 窗格中，依序展開**Customer_Order**節點，然後展開**執行個體**節點。  
  
2.  按一下  **Customer_Order_Instance**，並在 屬性 窗格中，按一下 省略符號 （...） 按鈕，針對**屬性** 方塊中。  
  
3.  在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**SecondarySsoApplicationId** for**名稱** 方塊中。 同樣地，輸入**SAPSSO** for **PropertyValue**  方塊中。 選取 [ **System.String** for**型別**] 方塊中。  
  
     ![新增 SSO 屬性](../../adapters-and-accelerators/adapter-sap/media/1eb813e4-fed2-45c2-8902-9af5dd3369bf.gif "1eb813e4-fed2-45c2-8902-9af5dd3369bf")  
  
4.  按一下 [確定] 。  
  
### <a name="requirement-1-search-for-customers-based-on-customer-name"></a>需求 1： 客戶名稱為主的客戶搜尋  
 若要建立可以用來搜尋客戶名稱為主的客戶應用程式定義檔，您必須執行下列一組工作。  
  
-   在 SD_RFC_CUSTOMER_GET 方法中，建立篩選器，並將它對應至參數，其中儲存客戶的名稱。  
  
-   建立**Finder** SD_RFC_CUSTOMER_GET 方法的方法執行個體。 A **Finder**方法會擷取篩選為基礎的記錄清單。  
  
##### <a name="to-create-a-filter-and-map-it-to-the-customer-name-parameter"></a>若要建立篩選器，並將它對應至客戶名稱參數  
  
1.  建立篩選。  
  
    1.  在 [中繼資料物件] 窗格中，依序展開**客戶**節點，然後展開**方法**節點。  
  
    2.  展開 SD_RFC_CUSTOMER_GET 方法，以滑鼠右鍵按一下**篩選條件**，然後按一下**加入篩選**。  
  
         ![將篩選新增至方法](../../adapters-and-accelerators/adapter-sap/media/23eaab24-66e4-486f-8f99-02a5e0fef984.gif "23eaab24-66e4-486f-8f99-02a5e0fef984")  
  
    3.  在 屬性 窗格中，輸入**CustomerName**中**名稱** 方塊中。  
  
         ![指定的名稱篩選條件](../../adapters-and-accelerators/adapter-sap/media/0a0d0f85-a16a-4969-a122-097355141c27.gif "0a0d0f85-a16a-4969-a122-097355141c27")  
  
    4.  針對**FilterType**屬性中，選取**WildcardFilter**。  
  
2.  若要將篩選器對應**NAME1** SD_RFC_CUSTOMER_GET 方法中的參數。  
  
    1.  在 [中繼資料物件] 窗格中，依序展開**客戶**節點，然後展開**方法**節點。  
  
    2.  展開 SD_RFC_CUSTOMER_GET 方法，然後再展開**參數**節點。  
  
    3.  依序展開**NAME1**節點，然後按一下第二個**NAME1**節點。 **NAME1**參數會包含客戶的名稱。  
  
    4.  在 [屬性] 窗格中，選取**CustomerName**從**FilterDescriptor**清單。  
  
         ![將篩選器對應至方法參數](../../adapters-and-accelerators/adapter-sap/media/6cc4ef85-503c-4847-95cb-633b902a715d.gif "6cc4ef85-503c-4847-95cb-633b902a715d")  
  
##### <a name="to-create-a-finder-method-instance-for-the-sdrfccustomerget-method"></a>若要建立 Finder 方法執行個體 SD_RFC_CUSTOMER_GET 方法  
  
1.  在 [中繼資料物件] 窗格中，依序展開**客戶**節點，然後展開**方法**節點。  
  
2.  依序展開**SD_RFC_CUSTOMER_GET**節點，以滑鼠右鍵按一下**執行個體**，然後按一下**新增方法執行個體**以開啟 [建立方法執行個體] 視窗。  
  
     ![新增方法執行個體](../../adapters-and-accelerators/adapter-sap/media/f583f8ef-e364-4665-8514-db033219ba0b.gif "f583f8ef-e364-4665-8514-db033219ba0b")  
  
3.  在 [建立方法執行個體] 視窗中，按一下**Finder** for**方法執行個體類型**。 選取  **CUSTOMER_T** for**的傳回 TypeDescriptor**。  
  
     ![新增 Finder 方法執行個體](../../adapters-and-accelerators/adapter-sap/media/e9ae47f2-32f5-4586-8467-94e3713d2a06.gif "e9ae47f2-32f5-4586-8467-94e3713d2a06")  
  
4.  按一下 [確定] 。  
  
5.  在 屬性 窗格中，輸入**GetCustomerByName_Instance**中**名稱** 方塊中。  
  
     ![指定方法執行個體名稱](../../adapters-and-accelerators/adapter-sap/media/e44e02e8-b9fb-40ca-a55d-8bdc7ace02b5.gif "e44e02e8-b9fb-40ca-a55d-8bdc7ace02b5")  
  
### <a name="requirement-2-retrieve-details-for-a-specific-customer-from-the-list-of-customers"></a>需求 2： 擷取特定客戶從客戶清單的詳細資料  
 若要建立可以用來搜尋客戶名稱為主的客戶應用程式定義檔，您必須執行下列一組工作。  
  
-   在 SD_RFC_CUSTOMER_GET 方法中，建立識別項，並將它對應至參數，其中儲存客戶編號。  
  
-   建立**特定的 Finder** SD_RFC_CUSTOMER_GET 方法的方法執行個體。 A**特定的 Finder**方法會尋找特定的記錄，根據識別項。  
  
##### <a name="to-create-an-identifier-and-map-it-to-the-customer-number-parameter"></a>建立識別項，並將其對應至客戶的數字參數  
  
1.  建立的識別項**客戶**實體。  
  
    1.  在 [中繼資料物件] 窗格中，依序展開**客戶**節點。  
  
    2.  以滑鼠右鍵按一下**識別碼**節點，，然後選取**新增識別碼**。  
  
         ![新增識別碼至方法](../../adapters-and-accelerators/adapter-sap/media/3adeeda3-426c-41fe-8d5c-5ca5863fb430.gif "3adeeda3-426c-41fe-8d5c-5ca5863fb430")  
  
    3.  在 屬性 窗格中，輸入**CustomerID**中**名稱** 方塊中。  
  
    4.  選取 [ **System.String** for**型別**] 方塊中。  
  
         ![指定識別項的名稱](../../adapters-and-accelerators/adapter-sap/media/a2304bca-9a54-4d2b-ba9f-461cfaafccb0.gif "a2304bca-9a54-4d2b-ba9f-461cfaafccb0")  
  
2.  將識別碼對應至 SD_RFC_CUSTOMER_GET 方法的索引鍵參數。  
  
    1.  在 [中繼資料物件] 窗格中，依序展開**客戶**節點，然後展開**方法**節點。  
  
    2.  展開 SD_RFC_CUSTOMER_GET 方法，然後再展開**參數**節點。  
  
    3.  依序展開**KUNNR**參數，然後按一下 第二個**KUNNR**節點。  
  
    4.  在 [屬性] 窗格中，選取**CustomerID [Customer]** 從**識別項**清單。  
  
         ![將識別碼對應至參數](../../adapters-and-accelerators/adapter-sap/media/04ff6496-34a7-421b-ae9e-f9263895c153.gif "04ff6496-34a7-421b-ae9e-f9263895c153")  
  
3.  設定輸入和傳回參數之間的關聯。  
  
    1.  在 [中繼資料物件] 窗格中，依序展開**客戶**節點，然後展開**方法**節點。  
  
    2.  展開 SD_RFC_CUSTOMER_GET 方法，然後再展開**參數**節點。  
  
    3.  依序展開**CUSTOMER_T**節點，然後第二個**CUSTOMER_T**節點，然後在**項目**節點，然後再按一下**KUNNR**節點。  
  
    4.  在 [屬性] 窗格中，選取**CustomerID [Customer]** 從**識別項**清單。  
  
##### <a name="to-create-a-specific-finder-method-instance-for-the-sdrfccustomerget-method"></a>若要建立特定的 Finder 方法執行個體 SD_RFC_CUSTOMER_GET 方法  
  
1.  在 [中繼資料物件] 窗格中，依序展開**客戶**節點，然後**方法**節點。  
  
2.  依序展開**SD_RFC_CUSTOMER_GET**節點，以滑鼠右鍵按一下**執行個體**，然後選取**新增方法執行個體**以開啟 [建立方法執行個體] 視窗。  
  
     ![新增方法執行個體](../../adapters-and-accelerators/adapter-sap/media/f583f8ef-e364-4665-8514-db033219ba0b.gif "f583f8ef-e364-4665-8514-db033219ba0b")  
  
3.  在 [建立方法執行個體] 視窗中，選取**Specific Finder** for**方法執行個體類型**。 同樣地，選取**CUSTOMER_T** for**傳回 TypeDescriptor**。  
  
     ![新增 Specific Finder 方法執行個體](../../adapters-and-accelerators/adapter-sap/media/838eb512-b967-46e7-a865-0bf3651b02a1.gif "838eb512-b967-46e7-a865-0bf3651b02a1")  
  
4.  按一下 [確定] 。  
  
5.  在 屬性 窗格中，輸入**GetCustomerByNumber_Instance** for**名稱** 方塊中。  
  
     ![指定方法執行個體名稱](../../adapters-and-accelerators/adapter-sap/media/970f543c-cd06-4921-86c9-c110abdc7994.gif "970f543c-cd06-4921-86c9-c110abdc7994")  
  
### <a name="requirement-3-retrieve-sales-order-details-for-a-specific-customer-from-the-list-of-customers"></a>需求 3： 擷取特定客戶從客戶清單的銷售訂單詳細資料  
 若要建立可用來擷取特定客戶的銷售訂單詳細資料的應用程式定義檔，您必須執行下列一組工作。  
  
-   設定之間的關聯**客戶**並**SalesOrder**實體。  
  
-   建立**關聯**BAPI_SALESORDER_GETLIST 方法的方法。  
  
##### <a name="to-create-an-association-between-the-customer-and-salesorder-entities"></a>若要建立客戶和 SalesOrder 實體之間的關聯  
  
1.  在 [中繼資料物件] 窗格中，依序展開**SalesOrder**節點，然後展開**方法**節點。  
  
2.  展開 BAPI_SALESORDER_GETLIST 方法，然後再展開**參數**節點。  
  
3.  依序展開**CUSTOMER_NUMBER**節點，然後按一下 第二個**CUSTOMER_NUMBER**節點。  
  
4.  在 [屬性] 窗格中，選取**CustomerID [Customer]** 從**識別項**清單。  
  
     ![建立兩個實體之間的關聯](../../adapters-and-accelerators/adapter-sap/media/ae7e1e7a-a12b-4905-b002-2a04c7050848.gif "ae7e1e7a-a12b-4905-b002-2a04c7050848")  
  
##### <a name="to-create-an-association-method-instance-for-the-bapisalesordergetlist-method"></a>若要建立 Association 方法執行個體 BAPI_SALESORDER_GETLIST 方法  
  
1.  在 [中繼資料物件] 窗格中，依序展開**SalesOrder**節點，然後展開**方法**節點。  
  
2.  依序展開**BAPI_SALESORDER_GETLIST**節點，以滑鼠右鍵按一下**執行個體**，然後選取**新增方法執行個體**以開啟 [建立方法執行個體] 視窗。  
  
     ![新增 Association 方法執行個體](../../adapters-and-accelerators/adapter-sap/media/c62a0d01-d4f3-470e-92f1-8a5cf666f8da.gif "c62a0d01-d4f3-470e-92f1-8a5cf666f8da")  
  
3.  在 [建立方法執行個體] 視窗中，選取**關聯**for**方法執行個體類型**。  
  
4.  在 **來源實體**清單中，選取**客戶**。  
  
5.  在 **傳回 TypeDescriptor**清單中，選取**SALES_ORDERS**...  
  
     ![建立 Association 方法執行個體](../../adapters-and-accelerators/adapter-sap/media/15975b78-8932-41ce-8c10-41891fc1fb22.gif "15975b78-8932-41ce-8c10-41891fc1fb22")  
  
6.  按一下 [確定] 。  
  
7.  在 屬性 窗格中，輸入**SalesOrderForCustomer_Instance** for**名稱** 方塊中。  
  
     ![指定 Association 方法的名稱](../../adapters-and-accelerators/adapter-sap/media/0f1d13e4-e5a3-49ec-92a7-6329c6db1eb0.gif "0f1d13e4-e5a3-49ec-92a7-6329c6db1eb0")  
  
### <a name="remove-parameters-of-systemnullable-type"></a>移除 System.Nullable 類型的參數  
 在建立時**關聯**方法執行個體 BAPI_SALESORDER_GETLIST 方法中，您必須選取的傳回型別為 SALES_ORDERS。 如果您展開 SALES_ORDER 參數時，您會發現某些參數屬於 System.Nullable 類型。 您可以看到在商務資料目錄定義編輯器中，選取參數，並查看 值輸入參數**TypeName**屬性。  
  
 對於這類參數，商務資料目錄定義編輯器建立另一個參數具有相同名稱但加上"Specified"尾碼。 例如，看看參數*ITM_NUMBER*並*ITM_NUMBERSpecified*。 Microsoft Office SharePoint Server 不支援 System.Nullable 參數。 因此，當您嘗試包含 System.Nullable 參數類型的記錄時，它會擲回例外狀況。 因此，您必須先移除兩個參數 （使用和不含"Specified"後置詞和具有相同名稱） 從商務資料目錄定義編輯器  
  
##### <a name="to-remove-the-parameters-of-systemnullable-type"></a>若要移除 System.Nullable 類型的參數  
  
1.  在 [中繼資料物件] 窗格中，依序展開**SalesOrder**節點，然後展開**方法**節點。  
  
2.  依序展開**BAPI_SALESORDER_GETLIST**節點，然後展開**參數**節點。  
  
3.  依序展開**SALES_ORDERS**，展開 第二個**SALES_ORDERS**，然後展開**項目**。  
  
4.  以滑鼠右鍵按一下參數，其中包含在名稱中，"Specified"後的置詞，然後選取**刪除**。  
  
5.  以滑鼠右鍵按一下 已刪除，而不需要後置詞，參數名稱相同的參數，然後選取**刪除**。 一般而言，這個參數是正確"Specified"後置詞的參數之前。  
  
### <a name="set-default-parameters"></a>設定預設參數  
 BAPI_SALESORDER_GETLIST 採用兩個參數。 其中一個參數，TRANSACTION_GROUP，是預設參數。 因此，您必須設定此參數的預設值。  
  
##### <a name="to-set-the-default-value-for-transactiongroup"></a>若要設定的預設值為 TRANSACTION_GROUP  
  
1.  在 [中繼資料物件] 窗格中，依序展開**SalesOrder**節點，然後展開**方法**節點。  
  
2.  依序展開**BAPI_SALESORDER_GETLIST**節點，然後展開**執行個體**節點。  
  
3.  選取  **SalesOrderForCustomer_Instance**方法執行個體，並在 屬性 窗格中，按一下 省略符號按鈕 （...），以對**DefaultValues**  方塊中。  
  
4.  在 [編輯] 視窗中，依序展開**TRANSACTION_GROUP**節點，並針對**TRANSACTION_GROUP**方塊中，指定預設值 0。  
  
     ![指定方法執行個體的預設值](../../adapters-and-accelerators/adapter-sap/media/86e0a42d-61c0-4d5d-ba3f-55b328f79576.gif "86e0a42d-61c0-4d5d-ba3f-55b328f79576")  
  
5.  按一下 [ **關閉**]。  
  
### <a name="export-the-application-definition-to-a-file"></a>匯出至檔案的應用程式定義  
 您現在已建立應用程式定義，其中包含 SAP 系統的執行個體中繼資料。 您必須將此定義匯出至 XML 檔案，可匯入至 Microsoft Office SharePoint Server。  
  
##### <a name="to-export-the-application-definition-to-a-file"></a>若要將應用程式定義匯出至檔案  
  
1.  在 [中繼資料物件] 窗格中，以滑鼠右鍵按一下**Customer_Order**節點，然後再按一下**匯出**。  
  
2.  將檔案儲存為 Customer_Order.xml 中。  
  
## <a name="next-steps"></a>後續步驟  
 您現在必須建立 SharePoint 應用程式來擷取 SAP 系統中的資料。 請參閱[步驟 3： 建立 SharePoint 應用程式以擷取資料從 SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md)如需相關指示。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1：在 SharePoint 網站上呈現 SAP 系統的資料](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)