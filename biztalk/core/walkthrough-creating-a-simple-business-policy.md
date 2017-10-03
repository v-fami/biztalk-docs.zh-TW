---
title: "逐步解說： 建立簡單商務原則 |Microsoft 文件"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02d35735-dce2-4ee2-965e-dae307a125b0
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c894ab80926d2fad66af540c492dd053570aaa4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-creating-a-simple-business-policy"></a>逐步解說： 建立簡單商務原則
本逐步解說提供逐步程序，使用 「 商務規則編輯器 」 建立名為的簡單商務原則**ProcessPurchaseOrder**包含名為的規則**ApprovedRule**。 **ApprovedRule**規則需要使用者提交 XML 文件當做事實，並將值設定**狀態**欄位中的文件**Approved**如果值**數量**欄位是否小於或等於**500**。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先熟悉的商務規則架構，才能執行此逐步解說的基本概念。 如果您不熟悉 「 商務規則架構，我們建議您閱讀商務規則架構 」 架構概觀[商務規則引擎](../core/business-rules-engine.md)然後再執行本逐步解說。  
  
## <a name="overview-of-this-walkthrough"></a>此逐步解說的概觀  
 此逐步解說包含兩個程序，如下表所示。  
  
|程序標題|程序說明|  
|---------------------|---------------------------|  
|建立 PO 結構描述檔案|提供建立文件的結構描述的逐步指示**ProcessPurchaseOrder**原則會使用。|  
|建立 ProcessPurchaseOrder 原則|提供逐步指示，建立**ProcessPurchaseOrder**使用商務規則編輯器 」 的原則。|  
  
### <a name="to-create-the-po-schema-file"></a>建立 PO 結構描述檔案  
  
1.  在**啟動**功能表中，開啟**記事本**。  
  
2.  在 [ **檔案** ] 功能表上，指向 [ **新增**]，然後按一下 [ **檔案**]。  
  
3.  將下列 XML 文字複製到編輯器中：  
  
    ```  
    <?xml version="1.0" encoding="utf-16"?>  
    <xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://EAISolution.PurchaseOrder" targetNamespace="http://EAISolution.PurchaseOrder" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
      <xs:element name="PurchaseOrder">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="Header">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="ReqID" type="xs:string" />  
                  <xs:element name="Date" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
            <xs:element name="Item">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="Description" type="xs:string" />  
                  <xs:element name="Quantity" type="xs:int" />  
                  <xs:element name="UnitPrice" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
            <xs:element name="Status" type="xs:string" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:schema>  
    ```  
  
4.  在**檔案**功能表上，按一下 **另存 TextFile1.txt 為**。  
  
5.  值變更**另存新檔類型**從**文字文件 (\*.txt)**至**所有檔案**。  
  
6.  型別**PO.xsd**中**檔案名稱**文字方塊中，將目錄變更**C:\BRE-Walkthroughs**，變更的值**編碼**至**Unicode** ，然後按一下 **儲存**。  
  
    > [!NOTE]
    >  建立目錄**BRE 逐步解說**下**c:\\** 如果不存在，然後再按一下**儲存**。  
  
7.  關閉 [記事本]。  
  
### <a name="to-create-the-processpurchaseorder-business-policy"></a>建立 ProcessPurchaseOrder 商務原則  
  
1.  在**啟動**功能表中，開啟**商務規則編輯器 」**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
    > [!NOTE]
    >  「 商務規則編輯器 」 會顯示**開啟規則存放區**對話方塊中的電腦上第一次開啟時。 如果您看到**開啟規則存放區**對話方塊中，按一下 **確定**之後驗證的 SQL server 名稱和資料庫名稱。  
  
2.  在原則總管] 視窗中，以滑鼠右鍵按一下**原則**，然後按一下 [**新增原則**。  
  
3.  編輯原則的名稱， **[policy1]**至**ProcessPurchaseOrder**按下 ENTER。 您也可以變更原則的名稱**屬性**視窗。  
  
4.  以滑鼠右鍵按一下**1.0 版**，然後按一下  **AddNewRule**。  
  
5.  編輯名稱，將規則和**Rule1**至**ApprovalRule**按下 ENTER**。** 您也可以變更中規則的名稱**屬性**視窗。  
  
6.  在 事實總管 視窗中，按一下**XML 結構描述** 索引標籤。  
  
7.  以滑鼠右鍵按一下**結構描述**，按一下 **瀏覽**，然後選取**PO.xsd**您稍早建立的檔案。  
  
8.  在 [屬性] 視窗中變更的值**文件類型**屬性從**PO**至**[ruletest.po]**。  
  
    > [!NOTE]
    >  您將建立 BizTalk 專案，名為**RuleTest**稍後[逐步解說： 叫用的原則，從協調流程](../core/walkthrough-invoking-the-policy-from-an-orchestration.md)逐步解說。 逐步解說中，您將加入， **PO.xsd**檔案加入專案中，建立會叫用的協調流程**ProcessPurchaseOrder**原則，然後再測試該原則。 若要測試的原則，從協調流程，您需要確定您變更**文件類型**屬性**\<專案名稱 >。\<SchemaName >**，也就是**[ruletest.po]**在此情況下。  
  
     ![BRE &#45;逐步解說 &#45;ChangeDocType](../core/media/e9a370fd-d9b2-48f0-ad0e-85a5428a9c21.gif "e9a370fd-d9b2-48f0-ad0e-85a5428a9c21")  
  
9. 在 [事實總管] 視窗中，依序展開**PurchaseOrder**，然後展開**項目**。  
  
10. 在 IF 窗格 （上方） 右邊，以滑鼠右鍵按一下**條件**，按一下 **述詞**，然後按一下 **小於或等於**。  
  
     ![商務規則編輯器 &#45;小於或等於](../core/media/1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7.gif "1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7")  
  
11. 拖曳**數量**節點從 [事實總管] 視窗**引數 1** [IF] 窗格中。  
  
     ![商務規則編輯器 &#45;DragQuantity](../core/media/4742eca6-4a8a-401d-8989-cab4e8025fb3.gif "4742eca6-4a8a-401d-8989-cab4e8025fb3")  
  
     ![商務規則編輯器 &#45;UseQuantity](../core/media/ee4f61b1-0f15-4329-b0b5-9badd21dcd61.gif "ee4f61b1-0f15-4329-b0b5-9badd21dcd61")  
  
12. 在 IF 窗格中，按一下 **引數 2**，型別`500`，然後按 ENTER 鍵。  
  
13. 拖曳**狀態**節點從 [事實總管] 視窗右下角的商務規則編輯器 [THEN] 窗格。  
  
     ![商務規則編輯器 &#45; DragStatus](../core/media/3617251a-a192-4aec-9474-81f6290c0832.gif "3617251a-a192-4aec-9474-81f6290c0832")  
  
14. 在 [THEN] 窗格中，按一下**\<輸入的值 >** ，然後輸入**Approved**。  
  
15. 在原則總管] 視窗中，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 [**儲存**。  
  
## <a name="comments"></a>註解  
  
-   原則中可能有一或多個規則。 您會加入另一個規則**DeniedRule**，請在[逐步解說： 將規則新增至原則](../core/walkthrough-adding-a-rule-to-the-policy.md)逐步解說。  
  
-   您可以修改原則，以便在原則處於「已儲存」狀態時加入更多規則、變更條件和變更動作。  
  
-   您可以設定規則的執行，藉由指定**優先順序**商務規則編輯器 」 中的規則上的屬性。 例如，如果您按一下**ApprovedRule** 原則總管 視窗中的節點，您可以看到**優先順序**屬性 視窗中的屬性。 數字愈大，規則的優先順序愈高。  
  
-   您可以使用 XML 結構描述、資料庫或 .NET 組件做為原則的資料來源。 在此逐步解說中，您已使用 XML 結構描述做為資料來源。 您應該將結構描述的 XML 文件執行個體當做事實提交至規則引擎來執行原則。  
  
## <a name="next-steps"></a>後續步驟  
 現在您已完成此逐步解說中，執行[逐步解說： 測試原則](../core/walkthrough-testing-the-policy.md)逐步解說，它可讓您測試的逐步指示**ProcessPurchaseOrder**原則您在本逐步解說中建立。  
  
## <a name="see-also"></a>另請參閱  
 [關於商務規則](../core/about-business-rules.md)