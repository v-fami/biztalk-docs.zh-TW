---
title: 步驟 2： 建立 Siebel 商務元件作業的應用程式定義檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75d34c48-0f2a-42e4-a60b-e04bcf2404e1
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c017d5e71cdd2a4281849647727364520ad77784
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967615"
---
# <a name="step-2-create-an-application-definition-file-for-siebel-business-component-operations"></a>步驟 2： 建立 Siebel 商務元件作業的應用程式定義檔案
![步驟 4 之 2](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **若要完成的時間：** 15 分鐘  
  
 **目標：** 商務資料目錄公開 （expose） 和入口網站中併入的營運 (LOB) 應用程式的資料。 若要併入您的入口網站中的這項資料，您必須建置可取用 Microsoft Office SharePoint Server 的應用程式定義檔。  
  
 Business Data Catalog Definition Editor 工具可讓您的商務資料目錄中建立應用程式定義檔案。 此工具會自動產生的 XML 定義檔。 因此，您不必以手動方式建立檔案的 xml 編輯器。  
  
 Microsoft Office SharePoint Server 應用程式所建立的目的是執行帳戶的商務元件，以擷取記錄清單上的查詢作業。 若要這麼做，您必須完成一的組工作中商務資料目錄定義編輯器。 本主題提供有關如何執行這些工作的指示。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須安裝 Microsoft Office SharePoint Server 2007 SDK 的一部分為商務資料目錄定義編輯器。 您可以下載從 SDK [ http://go.microsoft.com/fwlink/?LinkId=104130 ](http://go.microsoft.com/fwlink/?LinkId=104130)。  
  
-   您應該已發佈 WCF 服務，如中所述[步驟 1： 發佈為 WCF 服務的 Siebel 商務元件操作](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md)。  
  
## <a name="creating-an-application-definition-file"></a>建立應用程式定義檔案  
 本節提供逐步指示來建立 WCF 服務的應用程式定義檔。  
  
### <a name="connect-to-the-wcf-service-and-create-entities"></a>連線到 WCF 服務，並建立實體  
 您必須連接至 WCF 服務，以擷取 Web 服務描述語言 (WSDL) 服務。 商務資料目錄定義編輯器會根據 WSDL、 擷取方法。 這些方法可用來建立實體。 此範例中，您必須建立帳戶的商務元件上的查詢作業的一個實體。  
  
##### <a name="to-connect-to-the-wcf-service-and-create-entities"></a>若要連線到 WCF 服務，並建立實體  
  
1.  啟動商務資料目錄定義編輯器。 在 **開始**功能表上，按一下**Microsoft Business Data Catalog Definition Editor**。  
  
2.  在工具中，按一下**新增 LOB 系統**。  
  
3.  在 [新增 LOB 系統] 視窗中，按一下**連接到 web 服務**。  
  
4.  在 [URL] 方塊中，輸入 WCF 服務的 URL。 這個 URL 必須以下列格式：  
  
    ```  
    https://<computer_name>/Siebel_Account/BusinessObjects_Account_Account_Operation.svc?wsdl  
    ```  
  
     其中，BusinessObjects_Account_Account_Operation.svc 是建立 Siebel 合約的服務檔案。  
  
     您必須輸入的 URL 時，使用您要測試是否 WCF 服務發佈成功，如中所述[步驟 1： 發佈為 WCF 服務的 Siebel 商務元件操作](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md)。  
  
5.  按一下 **[連接]**。  
  
6.  按一下 **新增 Web 方法**索引標籤，查看您在 WCF 配接器服務開發精靈中選取的作業。 您會看到**查詢**方法。  
  
     ![新增 web 方法至 BDC 應用程式](../../adapters-and-accelerators/adapter-siebel/media/f9505cd3-67e3-4f99-b189-d010322a3137.gif "f9505cd3-67e3-4f99-b189-d010322a3137")  
  
7.  拖曳**查詢**方法至設計介面，然後按一下**確定**。  
  
8.  在 **輸入 LOB 系統的名稱** 對話方塊中，輸入的名稱，在**LOB 系統名稱** 方塊中。 此範例中，輸入`Siebel_Account`，然後按一下 **[確定]**。 實體， **Entity0**，會建立在商務資料目錄定義編輯器。  
  
    > [!IMPORTANT]
    >  Business Data Catalog Definition Editor 工具不會處理列舉的資料類型。 直到它遇到列舉的資料類型，並忽略其餘的欄位中，因此，商務資料目錄定義編輯器工具會匯入的欄位。 Business Data Catalog Definition Editor 工具也會顯示錯誤。 您可以忽略此錯誤，並依序按一下 [確定] 繼續進行。 您可以手動新增必要的欄位在應用程式定義檔中在稍後的階段。  
  
9. 變更實體名稱，以使用更多的易記名稱。 此範例中，變更**Entity0**要**帳戶**。  
  
    1.  依序展開**Siebel_Account**節點，然後展開**實體**節點。  
  
    2.  選取  **Entity0**節點。  
  
    3.  在 [屬性] 窗格中，輸入**帳號**中**名稱**欄位。  
  
         ![重新命名實體](../../adapters-and-accelerators/adapter-siebel/media/44eda1de-b348-4421-9c51-0355b51f4a90.gif "44eda1de-b348-4421-9c51-0355b51f4a90")  
  
### <a name="specify-user-name-and-password-headers-for-methods"></a>指定使用者名稱和密碼標頭方法  
 建立 WCF 服務時選取的商務元件作業在 Siebel 系統中，您會指定使用者名稱和密碼標頭為端點行為組態的一部分 ([步驟 1： 將 Siebel 商務元件作業發佈做為 WCF 服務](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md))。 您必須指定方法屬性相同的值。  
  
##### <a name="to-specify-user-name-and-password-headers-for-the-query-method"></a>若要指定查詢方法的使用者名稱和密碼標頭  
  
1.  在 [中繼資料物件] 窗格中，依序展開**帳戶**節點，然後展開**方法**節點。  
  
2.  按一下 **查詢**節點，並在 屬性 窗格中，按一下 省略符號 （...） 按鈕，針對**屬性**欄位。  
  
3.  在 PropertyView 集合編輯器 對話方塊中，按一下 **新增**，然後在 屬性 窗格中，輸入`HttpHeaderUserName`如**名稱**欄位。 同樣地，輸入`MyUserHeader`for **PropertyValue**欄位。 選取  **System.String** for**型別**欄位。  
  
     ![將屬性加入](../../adapters-and-accelerators/adapter-sap/media/9eef32ac-8a93-45dc-8d07-12b7dbf961ba.gif "9eef32ac-8a93-45dc-8d07-12b7dbf961ba")  
  
4.  在 PropertyView 集合編輯器 視窗中，按一下 **新增**，然後在 屬性 窗格中，輸入`HttpHeaderPassword`如**名稱**欄位。 同樣地，輸入`MyPassHeader`for **PropertyValue**欄位。 選取  **System.String** for**型別**欄位。  
  
5.  按一下 [確定] 。  
  
### <a name="set-up-single-sign-on-for-connecting-to-a-siebel-system"></a>設定單一登入為連接至 Siebel 系統  
 執行本主題中的所有程序完成之後，您將建立應用程式定義可以匯入 SharePoint 應用程式的 XML。 從應用程式，您會 （公開為 Web 方法） 的 Siebel 商務元件作業叫用來擷取 Siebel 系統的相關資料。 若要這麼做，您必須在 SharePoint 應用程式中建立 Siebel 系統中的使用者與使用者之間的對應。 您已匯入應用程式定義 XML 之後，您可以建立在 SharePoint 管理中心網站的此對應。  
  
 不過，若要建立對應您必須設定屬性**SecondarySsoApplicationId**中商務資料目錄定義編輯器。  
  
##### <a name="to-set-the-secondaryssoapplicationid-property"></a>若要設定 SecondarySsoApplicationId 屬性  
  
1.  在 [中繼資料物件] 窗格中，依序展開**Siebel_Account**節點，然後展開**執行個體**節點。  
  
2.  按一下  **Siebel_Account_Instance**和 屬性 窗格中按一下 省略符號 （...） 按鈕，針對**屬性**欄位。  
  
3.  在 PropertyView 集合編輯器 視窗中，按一下 **新增**，然後在 屬性 窗格中，輸入**SecondarySsoApplicationId**如**名稱**欄位。 同樣地，輸入**SiebelSSO** for **PropertyValue**欄位。 選取  **System.String** for**型別**欄位。  
  
     ![新增 SSO 屬性](../../adapters-and-accelerators/adapter-siebel/media/59ce70eb-498f-406b-965d-c273c2d6ed14.gif "59ce70eb-498f-406b-965d-c273c2d6ed14")  
  
4.  按一下 [確定] 。  
  
### <a name="requirement-perform-a-query-operation-on-the-account-business-component"></a>需求： 執行帳戶商務元件上的查詢作業  
 此範例中的第一個需求是建立可用來執行查詢作業帳戶商務元件上的應用程式定義。 若要達到此需求，您必須執行下列一組工作：  
  
-   在查詢方法中，建立篩選器，並將它對應至執行查詢作業的參數。 針對帳戶商務元件，您將會執行查詢，使用**SearchExpr**參數。 因此，您將對應至篩選**SearchExpr**參數。  
  
-   建立 Finder 方法執行個體的查詢方法。 搜尋方法擷取篩選為基礎的記錄清單。  
  
##### <a name="to-create-a-filter-and-map-it-to-the-searchexpr-parameter"></a>若要建立篩選器，並將它對應至 SearchExpr 參數  
  
1.  建立篩選的查詢方法。  
  
    1.  在 [中繼資料物件] 窗格中，依序展開**帳戶**節點，然後展開**方法**節點。  
  
    2.  展開的查詢方法，以滑鼠右鍵按一下**篩選條件**，然後按一下**加入篩選**。  
  
         ![將篩選新增至方法](../../adapters-and-accelerators/adapter-siebel/media/9cf7ccfd-6da0-44b7-b522-df327a74e7a2.gif "9cf7ccfd-6da0-44b7-b522-df327a74e7a2")  
  
    3.  在 [屬性] 窗格中，輸入`SearchExpression`for**名稱**欄位。  
  
    4.  針對**FilterType**屬性中，選取**等於**。  
  
         ![指定的篩選器名稱和類型](../../adapters-and-accelerators/adapter-siebel/media/9faa18e1-4d27-4ee4-960a-458f978812a7.gif "9faa18e1-4d27-4ee4-960a-458f978812a7")  
  
2.  若要將篩選器對應**SearchExpr**查詢方法中的參數。  
  
    1.  在 [中繼資料物件] 窗格中，依序展開**帳戶**節點，然後展開**方法**節點。  
  
    2.  展開查詢方法中，然後再展開**參數**節點。  
  
    3.  依序展開**AccountQueryInputRecord**節點，然後展開 第二個**AccountQueryInputRecord**節點。  
  
    4.  按一下  **SearchExpr**節點，然後在 屬性 窗格中，選取**SearchExpression**從**FilterDescriptor**清單。  
  
         ![將參數對應至篩選](../../adapters-and-accelerators/adapter-siebel/media/199c8ba7-d0e8-4fb4-9d73-9cf548512498.gif "199c8ba7-d0e8-4fb4-9d73-9cf548512498")  
  
        > [!IMPORTANT]
        >  **AccountQueryInputRecord**也包含 **QueryFields** 節點，其中又包含**項目**節點。 您必須先刪除**項目** 節點，否則帳戶商務元件上的查詢作業，可能無法提供想要的結果。 若要刪除**項目**節點，以滑鼠右鍵按一下節點，然後按**刪除**。  
  
##### <a name="to-create-a-finder-method-instance-for-query-method"></a>若要建立 Finder 方法執行個體的查詢方法  
  
1.  在 [中繼資料物件] 窗格中，依序展開**帳戶**節點，然後展開**方法**節點。  
  
2.  依序展開**查詢**節點，以滑鼠右鍵按一下**執行個體**，然後按一下**新增方法執行個體**以開啟 [建立方法執行個體] 視窗。  
  
     ![新增 Finder 方法執行個體](../../adapters-and-accelerators/adapter-siebel/media/c90e7784-4fb7-4eb5-baf5-efbefba4bb1f.gif "c90e7784-4fb7-4eb5-baf5-efbefba4bb1f")  
  
3.  在 [建立方法執行個體] 視窗中，按一下**Finder** for**方法執行個體類型**。  
  
4.  按一下 **會傳回**從**傳回 TypeDescriptor**一節。  
  
     ![新增 Finder 方法執行個體](../../adapters-and-accelerators/adapter-siebel/media/e8343988-d7c1-4b04-85b0-ca7d07097490.gif "e8343988-d7c1-4b04-85b0-ca7d07097490")  
  
5.  按一下 [確定] 。  
  
6.  在 [屬性] 窗格中，輸入`QueryAccount`for**名稱**欄位。  
  
     ![指定方法執行個體名稱](../../adapters-and-accelerators/adapter-siebel/media/401223f3-806f-4010-8646-d5ac0c0e9f67.gif "401223f3-806f-4010-8646-d5ac0c0e9f67")  
  
### <a name="remove-the-parameters-of-systemnullable-type"></a>移除 System.Nullable 類型的參數  
 查詢函式的傳回參數可能會包含屬於 System.Nullable 類型的參數。 在 應用程式定義這些參數的緣故，您可能會發生錯誤，同時 SharePoint 入口網站上呈現的 Siebel 資料。 因此，您必須將 System.Nullable 類型的參數移除應用程式定義。  
  
 此外，System.Nullable 類型的每個參數，商務資料目錄定義編輯器建立 System.Boolean 類型的另一個參數，並將"Specified"附加到參數名稱。 例如，參數 AccountRole 屬於 System.Nullable 型別。 因此，商務資料目錄定義編輯器會將 AccountRoleSpecified 參數加入至參數的清單。 您必須移除以及這類參數。  
  
> [!NOTE]
>  您可以看到在商務資料目錄定義編輯器中，選取參數，並查看 [值輸入參數**TypeName**屬性] 窗格中的屬性。  
  
> [!NOTE]
>  如果應用程式不包含 System.Nullable 類型的任何參數，您可以略過此步驟。  
  
##### <a name="to-remove-the-parameters-of-systemnullable-type-for-the-query-method"></a>若要移除的 System.Nullable Query 方法的型別參數  
  
1.  在 [中繼資料物件] 窗格中，依序展開**帳戶**節點，然後展開**方法**節點。  
  
2.  依序展開**查詢**節點，然後展開**參數**節點。  
  
3.  依序展開**會傳回**節點，然後展開 第二個**傳回**節點。  
  
4.  以滑鼠右鍵按一下您想要刪除此項目，然後選取的參數**刪除**。  
  
5.  在對話方塊中，按一下**確定**。  
  
### <a name="export-the-application-definition-to-a-file"></a>匯出至檔案的應用程式定義  
 您現在已建立應用程式定義，其中包含 Siebel 系統的執行個體中繼資料。 您必須將此定義匯出至 XML 檔案，可匯入至 Microsoft Office SharePoint Server。  
  
##### <a name="to-export-the-application-definition-to-a-file"></a>若要將應用程式定義匯出至檔案  
  
1.  以滑鼠右鍵按一下**Siebel_Account**節點中的中繼資料物件 窗格中，然後按一下**匯出**。  
  
2.  將檔案儲存為 Siebel_Account.xml 中。  
  
### <a name="modify-the-application-definition-file-to-include-specific-parameters"></a>修改應用程式定義檔，以包含特定的參數  
 如本主題稍早所述，「 商務資料目錄定義編輯器工具不會處理列舉的資料類型。 Business Data Catalog Definition Editor 工具匯入的欄位，直到它遇到列舉的資料類型，並忽略其餘的欄位。 因此，可能會省略您想要在您的應用程式中的某些欄位。 您可以手動編輯應用程式定義檔，以包含這些欄位。  
  
> [!NOTE]
>  您必須先確定您要加入的參數中的 WCF 配接器服務開發精靈所產生的.cs 檔案中有[步驟 1： 發佈為 WCF 服務的 Siebel 商務元件操作](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md)。  
  
 在此應用程式定義檔案中，您會決定要加入或移除的傳回參數**QueryAccount**方法。  
  
##### <a name="to-modify-the-application-definition-file"></a>若要修改應用程式定義檔  
  
1. 使用開啟的應用程式定義檔，Siebel_Account.xml，[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]或任何其他編輯器。  
  
2. 修改應用程式定義檔，來取代的參數**QueryAccount**方法。  
  
   1.  在應用程式定義檔案中，搜尋下列：  
  
       ```  
       <TypeDescriptor TypeName="BDC.AccountQueryRecord,Siebel_Account" Name="Item">  
       ```  
  
   2.  內`<TypeDescriptors>`標記中，取代現有`<TypeDescriptor>`具有下列項目：  
  
       ```  
  
       <TypeDescriptor TypeName="System.String, mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=<token>" Name="Id" />  
       <TypeDescriptor TypeName="System.String, mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=<token>" Name="Country" />  
       <TypeDescriptor TypeName="System.String, mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=<token>" Name="Name" />  
       <TypeDescriptor TypeName="System.String, mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=<token>" Name="Location" />  
       ```  
  
   3.  儲存並關閉檔案。  
  
   > [!TIP]
   >  您可以匯入更新的應用程式定義檔，在 商務資料目錄定義編輯器工具，以查看新加入的欄位。 不過，匯入之前您必須從 Business Data Catalog Definition Editor 工具中移除現有的"Siebel_Account 」 應用程式。  
  
## <a name="next-steps"></a>後續步驟  
 您現在必須建立 SharePoint 應用程式來擷取 Siebel 系統中的資料。 請參閱[步驟 3： 建立 SharePoint 應用程式以擷取資料從 Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md)如需相關指示。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1：在 SharePoint 網站上呈現 Siebel 系統的資料](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)