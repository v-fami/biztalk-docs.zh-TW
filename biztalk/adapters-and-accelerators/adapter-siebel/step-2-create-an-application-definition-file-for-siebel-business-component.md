---
title: 步驟 2： 建立應用程式定義檔的 Siebel 商務元件操作 |Microsoft 文件
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
ms.openlocfilehash: 3bd1eaac434f4fc6bda55f6ab290740147d91997
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22227030"
---
# <a name="step-2-create-an-application-definition-file-for-siebel-business-component-operations"></a>步驟 2： 建立應用程式定義檔的 Siebel 商務元件操作
![步驟 4 之 2](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **若要完成的時間：** 15 分鐘  
  
 **目標：** 商務資料目錄公開，並從的特定業務 (LOB) 應用程式的資料合併至入口網站。 將此資料合併到您的入口網站，您必須建立 Microsoft Office SharePoint Server 可以使用應用程式定義檔。  
  
 商務資料目錄定義編輯器工具可讓您建立的商務資料目錄的應用程式定義檔。 此工具會自動產生的 XML 定義檔。 因此，您不必手動檔案在編輯器中建立 XML。  
  
 您正在建立 Microsoft Office SharePoint Server 應用程式的用途是執行查詢作業擷取的記錄清單帳戶商務元件上。 若要達成此目的，您必須完成一組工作中商務資料目錄定義編輯器。 本主題提供有關如何執行這些工作的指示。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須安裝 Microsoft Office SharePoint Server 2007 SDK 的一部份商務資料目錄定義編輯器。 您可以下載從 SDK [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130)。  
  
-   您應該已發佈 WCF 服務中所述[步驟 1： 發佈為 WCF 服務的 Siebel 商務元件操作](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md)。  
  
## <a name="creating-an-application-definition-file"></a>建立應用程式定義檔  
 本節提供逐步指示來建立 WCF 服務的應用程式定義檔。  
  
### <a name="connect-to-the-wcf-service-and-create-entities"></a>連接到 WCF 服務，並建立實體  
 您必須連接至 WCF 服務，以擷取 Web 服務描述語言 (WSDL) 服務。 從 WSDL，商務資料目錄定義編輯器中擷取的方法。 這些方法可以用來建立實體。 此範例中，您必須建立帳戶商務元件上的查詢作業的一個實體。  
  
##### <a name="to-connect-to-the-wcf-service-and-create-entities"></a>連接到 WCF 服務，並建立實體  
  
1.  啟動商務資料目錄定義編輯器。 在**啟動**功能表上，按一下  **Microsoft 商務資料目錄定義編輯器**。  
  
2.  在工具中，按一下  **LOB 系統**。  
  
3.  在 [新增 LOB 系統] 視窗中，按一下**連接到 Webservice**。  
  
4.  在 [URL] 方塊中，輸入 WCF 服務的 URL。 這個 URL 必須以下列格式：  
  
    ```  
    https://<computer_name>/Siebel_Account/BusinessObjects_Account_Account_Operation.svc?wsdl  
    ```  
  
     其中，BusinessObjects_Account_Account_Operation.svc 是針對 Siebel 合約建立服務檔案。  
  
     您必須輸入的 URL 時，使用您測試 WCF 服務發佈成功中, 所述是否[步驟 1： 發佈為 WCF 服務的 Siebel 商務元件操作](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md)。  
  
5.  按一下 **[連接]**。  
  
6.  按一下**新增 Web 方法**索引標籤，查看您在 WCF 配接器服務開發精靈中選取的作業。 您會看到**查詢**方法。  
  
     ![新增 web 方法至 BDC 應用程式](../../adapters-and-accelerators/adapter-siebel/media/f9505cd3-67e3-4f99-b189-d010322a3137.gif "f9505cd3-67e3-4f99-b189-d010322a3137")  
  
7.  拖曳**查詢**方法為設計介面，然後按一下**確定**。  
  
8.  在**輸入 LOB 系統的名稱**對話方塊內輸入名稱**LOB 系統名稱**方塊。 此範例中，輸入`Siebel_Account`，然後按一下 **確定**。 實體， **Entity0**，會建立在商務資料目錄定義編輯器。  
  
    > [!IMPORTANT]
    >  商務資料目錄定義編輯器工具不會處理列舉的資料型別。 因此，商務資料目錄定義編輯器工具直到它遇到列舉的資料型別，並忽略其餘的欄位匯入的欄位。 商務資料目錄定義編輯器工具也會提供錯誤。 您可以忽略此錯誤，並依序按一下 [確定] 繼續進行。 您可以手動新增必要的欄位在應用程式定義檔中在稍後的階段。  
  
9. 變更實體名稱使用更多的好記名稱。 例如，變更**Entity0**至**帳戶**。  
  
    1.  展開**Siebel_Account**  節點，然後展開**實體**節點。  
  
    2.  選取**Entity0**節點。  
  
    3.  在 [屬性] 窗格中，輸入**帳戶**中**名稱**欄位。  
  
         ![重新命名實體](../../adapters-and-accelerators/adapter-siebel/media/44eda1de-b348-4421-9c51-0355b51f4a90.gif "44eda1de-b348-4421-9c51-0355b51f4a90")  
  
### <a name="specify-user-name-and-password-headers-for-methods"></a>指定方法的使用者名稱和密碼標頭  
 建立時選取的商務元件操作的 WCF 服務在 Siebel 系統中，您會指定使用者名稱和密碼標頭做為端點行為組態的一部分 ([步驟 1： 發行 Siebel 商務元件操作做為 WCF 服務](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md))。 您必須指定方法屬性的相同值。  
  
##### <a name="to-specify-user-name-and-password-headers-for-the-query-method"></a>若要指定使用者名稱和密碼標頭的查詢方法  
  
1.  在 中繼資料物件 窗格中，依序展開**帳戶** 節點，然後展開**方法**節點。  
  
2.  按一下**查詢**] 節點，在 [屬性] 窗格中按一下 [省略符號 （...） 按鈕，針對**屬性**欄位。  
  
3.  在 PropertyView 集合編輯器 對話方塊中，按一下**新增**，然後在 屬性 窗格中，輸入`HttpHeaderUserName`如**名稱**欄位。 同樣地，輸入`MyUserHeader`如**PropertyValue**欄位。 選取**System.String**如**類型**欄位。  
  
     ![將屬性加入](../../adapters-and-accelerators/adapter-sap/media/9eef32ac-8a93-45dc-8d07-12b7dbf961ba.gif "9eef32ac-8a93-45dc-8d07-12b7dbf961ba")  
  
4.  在 [PropertyView 集合編輯器] 視窗中，按一下**新增**，然後在 [屬性] 窗格中，輸入`HttpHeaderPassword`的**名稱**欄位。 同樣地，輸入`MyPassHeader`如**PropertyValue**欄位。 選取**System.String**如**類型**欄位。  
  
5.  按一下 **[確定]**。  
  
### <a name="set-up-single-sign-on-for-connecting-to-a-siebel-system"></a>設定設定單一登入連接至 Siebel 系統  
 當您完成執行本主題中的所有程序之後，您將建立應用程式定義可以匯入 SharePoint 應用程式的 XML。 從應用程式，您會擷取來自 Siebel 系統的相關資料叫用 （公開為 Web 方法） 的 Siebel 商務元件操作。 若要啟用此功能，您必須在 SharePoint 應用程式中建立 Siebel 系統中的使用者與使用者之間的對應。 此對應中建立 SharePoint 管理中心網站後您已匯入應用程式定義 XML。  
  
 不過，若要建立對應您必須設定屬性**SecondarySsoApplicationId**中商務資料目錄定義編輯器。  
  
##### <a name="to-set-the-secondaryssoapplicationid-property"></a>若要設定 SecondarySsoApplicationId 屬性  
  
1.  在 中繼資料物件 窗格中，依序展開**Siebel_Account**  節點，然後展開**執行個體**節點。  
  
2.  按一下**Siebel_Account_Instance**在 屬性 窗格中按一下 省略符號 （...） 按鈕，針對**屬性**欄位。  
  
3.  在 [PropertyView 集合編輯器] 視窗中，按一下**新增**，然後在 [屬性] 窗格中，輸入**SecondarySsoApplicationId**的**名稱**欄位。 同樣地，輸入**SiebelSSO**如**PropertyValue**欄位。 選取**System.String**如**類型**欄位。  
  
     ![新增 SSO 屬性](../../adapters-and-accelerators/adapter-siebel/media/59ce70eb-498f-406b-965d-c273c2d6ed14.gif "59ce70eb-498f-406b-965d-c273c2d6ed14")  
  
4.  按一下 **[確定]**。  
  
### <a name="requirement-perform-a-query-operation-on-the-account-business-component"></a>需求： 執行帳戶商務元件上的查詢作業  
 此範例中的第一個需求是建立可以用來執行查詢作業帳戶商務元件上的應用程式定義。 若要達到此需求，您必須執行下列工作集合：  
  
-   在查詢的方法中，建立篩選器，並將它對應至其執行查詢作業的參數。 針對帳戶商務元件，您將會執行查詢，使用**SearchExpr**參數。 因此，您將對應的篩選條件**SearchExpr**參數。  
  
-   建立 Finder 方法執行個體的查詢方法。 搜尋方法擷取篩選條件的所有記錄的清單。  
  
##### <a name="to-create-a-filter-and-map-it-to-the-searchexpr-parameter"></a>若要建立篩選器，並將它對應至 SearchExpr 參數  
  
1.  建立篩選的查詢方法。  
  
    1.  在 中繼資料物件 窗格中，依序展開**帳戶** 節點，然後展開**方法**節點。  
  
    2.  展開的查詢方法，以滑鼠右鍵按一下**篩選**，然後按一下 **加入篩選條件**。  
  
         ![將篩選加入至方法](../../adapters-and-accelerators/adapter-siebel/media/9cf7ccfd-6da0-44b7-b522-df327a74e7a2.gif "9cf7ccfd-6da0-44b7-b522-df327a74e7a2")  
  
    3.  在 [屬性] 窗格中，輸入`SearchExpression`如**名稱**欄位。  
  
    4.  如**FilterType**屬性選取**等於**。  
  
         ![指定篩選器名稱與型別](../../adapters-and-accelerators/adapter-siebel/media/9faa18e1-4d27-4ee4-960a-458f978812a7.gif "9faa18e1-4d27-4ee4-960a-458f978812a7")  
  
2.  對應至篩選器**SearchExpr**中的查詢方法的參數。  
  
    1.  在 中繼資料物件 窗格中，依序展開**帳戶** 節點，然後展開**方法**節點。  
  
    2.  展開的查詢方法，然後再展開**參數**節點。  
  
    3.  展開**AccountQueryInputRecord** ] 節點，然後展開 [第二個**AccountQueryInputRecord**節點。  
  
    4.  按一下**SearchExpr**節點並在 [屬性] 窗格中，選取**SearchExpression**從**FilterDescriptor**清單。  
  
         ![將參數對應至篩選](../../adapters-and-accelerators/adapter-siebel/media/199c8ba7-d0e8-4fb4-9d73-9cf548512498.gif "199c8ba7-d0e8-4fb4-9d73-9cf548512498")  
  
        > [!IMPORTANT]
        >  **AccountQueryInputRecord**也包含 **# 10**節點，其中包含**項目**節點。 您必須刪除**項目** 節點，否則帳戶商務元件上的查詢作業，可能無法提供想要的結果。 若要刪除**項目** 節點，以滑鼠右鍵按一下節點，然後選取**刪除**。  
  
##### <a name="to-create-a-finder-method-instance-for-query-method"></a>若要建立 Finder 方法執行個體的查詢方法  
  
1.  在 中繼資料物件 窗格中，依序展開**帳戶** 節點，然後展開**方法**節點。  
  
2.  展開**查詢**] 節點，以滑鼠右鍵按一下**執行個體**，然後按一下 [**新增方法執行個體**開啟 [建立方法執行個體] 視窗。  
  
     ![新增 Finder 方法執行個體](../../adapters-and-accelerators/adapter-siebel/media/c90e7784-4fb7-4eb5-baf5-efbefba4bb1f.gif "c90e7784-4fb7-4eb5-baf5-efbefba4bb1f")  
  
3.  在 [建立方法執行個體] 視窗中，按一下**Finder**如**方法執行個體類型**。  
  
4.  按一下**傳回**從**傳回 TypeDescriptor** > 一節。  
  
     ![新增 Finder 方法執行個體](../../adapters-and-accelerators/adapter-siebel/media/e8343988-d7c1-4b04-85b0-ca7d07097490.gif "e8343988-d7c1-4b04-85b0-ca7d07097490")  
  
5.  按一下 **[確定]**。  
  
6.  在 [屬性] 窗格中，輸入`QueryAccount`如**名稱**欄位。  
  
     ![指定方法執行個體的名稱](../../adapters-and-accelerators/adapter-siebel/media/401223f3-806f-4010-8646-d5ac0c0e9f67.gif "401223f3-806f-4010-8646-d5ac0c0e9f67")  
  
### <a name="remove-the-parameters-of-systemnullable-type"></a>移除 System.Nullable 類型的參數  
 查詢函數的傳回參數可能會包含屬於 System.Nullable 類型的參數。 在應用程式定義這些參數的緣故，您可能會發生錯誤時，SharePoint 入口網站上的 Siebel 資料。 因此，您必須從應用程式定義移除 System.Nullable 類型的參數。  
  
 此外，System.Nullable 類型的每個參數，商務資料目錄定義編輯器建立 System.Boolean 類型的另一個參數和參數名稱中附加"了 Specified"。 例如，參數 AccountRole 是 System.Nullable 類型。 因此，商務資料目錄定義編輯器將 AccountRoleSpecified 參數加入至參數的清單。 您必須移除以及這類參數。  
  
> [!NOTE]
>  您可以看到在商務資料目錄定義編輯器中，選取參數，並查看的值輸入參數**TypeName**屬性 窗格中的屬性。  
  
> [!NOTE]
>  如果應用程式不包含任何 System.Nullable 類型的參數，您可以略過此步驟。  
  
##### <a name="to-remove-the-parameters-of-systemnullable-type-for-the-query-method"></a>若要移除 System.Nullable 類型的查詢方法的參數  
  
1.  在 中繼資料物件 窗格中，依序展開**帳戶** 節點，然後展開**方法**節點。  
  
2.  展開**查詢** 節點，然後展開**參數**節點。  
  
3.  展開**傳回**] 節點，然後展開 [第二個**傳回**節點。  
  
4.  以滑鼠右鍵按一下您想要刪除，然後選取 的參數**刪除**。  
  
5.  在對話方塊中，按一下 **確定**。  
  
### <a name="export-the-application-definition-to-a-file"></a>應用程式定義匯出至檔案  
 您現在已建立應用程式定義包含 Siebel 系統的執行個體中繼資料。 您必須將此定義匯出至 XML 檔案，可以匯入 Microsoft Office SharePoint Server。  
  
##### <a name="to-export-the-application-definition-to-a-file"></a>若要將應用程式定義匯出至檔案  
  
1.  以滑鼠右鍵按一下**Siebel_Account**節點中的中繼資料物件 窗格中，然後按一下**匯出**。  
  
2.  將檔案儲存為 Siebel_Account.xml。  
  
### <a name="modify-the-application-definition-file-to-include-specific-parameters"></a>修改應用程式定義檔，以包含特定的參數  
 如本主題稍早所述，商務資料目錄定義編輯器工具不會處理列舉的資料型別。 商務資料目錄定義編輯器工具匯入的欄位，直到它遇到列舉的資料型別，並忽略其餘的欄位。 因此，可能會省略您想要在應用程式中的某些欄位。 您可以手動編輯應用程式定義檔，以包含這些欄位。  
  
> [!NOTE]
>  您必須先確定您要加入的參數會出現在 WCF 配接器服務開發精靈中所產生的.cs 檔[步驟 1： 發佈為 WCF 服務的 Siebel 商務元件操作](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md)。  
  
 此應用程式定義檔中，您會加入或移除的傳回參數**QueryAccount**方法。  
  
##### <a name="to-modify-the-application-definition-file"></a>若要修改應用程式定義檔  
  
1.  使用開啟的應用程式定義檔 Siebel_Account.xml，[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]或任何其他編輯器。  
  
2.  修改應用程式定義檔，若要取代的參數**QueryAccount**方法。  
  
    1.  應用程式定義檔中搜尋下列：  
  
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
    >  您可以匯入更新的應用程式定義檔，在 商務資料目錄定義編輯器工具，以查看新加入的欄位。 不過，匯入之前您必須從商務資料目錄定義編輯器工具移除現有的"Siebel_Account 」 應用程式。  
  
## <a name="next-steps"></a>後續步驟  
 您現在必須建立 SharePoint 應用程式來擷取 Siebel 系統中的資料。 請參閱[步驟 3： 建立 SharePoint 應用程式以擷取資料從 Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md)如需相關指示。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1： 從 SharePoint 網站上的 Siebel 系統中呈現資料](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)