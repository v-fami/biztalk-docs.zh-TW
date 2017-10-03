---
title: "逐步解說： 從文件執行個體建立一般檔案結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5e1453f-0380-4505-97a9-9d3526db0923
caps.latest.revision: "47"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9077e8c8b878b3e24319ef112eb391a3eaf4e0ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-creating-a-flat-file-schema-from-a-document-instance"></a>逐步解說：從文件執行個體建立一般檔案結構描述
此逐步解說為您顯示如何根據下列範例訂單，使用 BizTalk 一般檔案結構描述精靈從文件執行個體建立一般檔案結構描述。 如需 BizTalk 一般檔案結構描述精靈的簡介，請參閱[如何使用 BizTalk 一般檔案結構描述精靈](../core/how-to-use-biztalk-flat-file-schema-wizard.md)。  
  
 ![範例採購單](../core/media/flatfileschema-samplepurchaseorder.gif "FlatFileSchema_SamplePurchaseOrder")  
  
 訂單的每一行都會以標示為綠色的歸位換行字元 (CRLF) 結尾。 訂單會以顯示為紅色的 PO 標記開頭，後面加上日期。 兩個重複的固定位置欄位包含客戶資訊，並顯示為紫色。 註解欄位中之後, 就沒有以 ITEMS 標記包含多個以逗號 （，） 分隔的記錄和透過管道 (&#124;) 分隔的資料值開頭的重複欄位的顯示為藍色。  
  
## <a name="prerequisites"></a>必要條件  
 執行此逐步解說之前，請確定已在您的伺服器上安裝和設定下列軟體：  
  
-   Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]  
  
-   Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與**開發人員工具**安裝
  
 若要準備逐步解說中的文件執行個體，將下列複製到文字編輯器中，並將它儲存為文字檔。 請務必將所有列都複製摘要和換行。  
  
```
PO1999-10-20
US        Alice Smith         123 Maple Street    Mill Valley    CA 90952
US        Robert Smith        8 Oak Avenue        Old Town       PA 95819
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Confirm this is electric,ITEM926-AA|Baby Monitor|1|39.98|Confirm this is electric

```

  
## <a name="start-the-wizard"></a>啟動精靈  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟**方案總管 中**。  
  
2.  若要加入新的一般檔案結構描述，以滑鼠右鍵按一下專案，然後選取**新增**。 按一下**新項目**。  
  
3.  在**加入新項目**視窗中，執行下列動作：  
  
    1.  在**類別**區段中，選取**結構描述檔案**。  
  
    2.  在**範本**區段中，選取**一般檔案結構描述精靈**。  
  
    3.  在**名稱**欄位中，輸入**PurchaseOrder.xsd**新結構描述。  
  
    4.  按一下 **[加入]**。  
  
4.  當 BizTalk 一般檔案結構描述精靈開啟時，會出現歡迎頁面。   
    若要在未來執行精靈時，請略過這個畫面上，選取**不要再顯示此簡介頁面**方塊。 按 **[下一步]** ，繼續進行。  
  
## <a name="selecting-purchase-order-instance"></a>選取訂單執行個體  
  
-   在**一般檔案結構描述資訊**畫面上，選取您的執行個體，輸入下列資訊。 當您完成之後時，按一下 **下一步**才能繼續。  
  
    -   **執行個體檔案：**按一下**瀏覽**按鈕，以找出一般的檔案將會產生結構描述。 瀏覽至包含您在逐步解說的必要條件 > 一節中建立文字檔案的資料夾： 建立一般檔案結構描述的文件執行個體。  
  
    -   **記錄名稱：**類型**PO**因為將結構描述根名稱。  
  
    -   **目標命名空間：**類型**http://Flat_File_Project.PurchaseOrder**結構描述目標命名空間。  
  
    -   **字碼頁：**選取**utf-8 (65001)**從下拉式清單選取項目清單。  
  
    -   **計算以位元組為單位的位置：**核取此方塊，如果您想要以位元組為單位計算位置資料欄位。 依預設值，位置資料欄位會以字元為單位計算。 在此逐步解說中，保留**計算位置，以位元組為單位**未核取核取方塊。  
  
## <a name="select-purchase-order-data"></a>選取訂單資料  
  
-   在**選取文件資料** 畫面中，一般檔案的內容會顯示。 選取建立結構描述中，所需的資料，然後按一下**下一步**。  
  
    > [!NOTE]
    >  如果您想要使用的整份文件執行個體，您可以按**CTRL-A**全部選取。  
  
    > [!NOTE]
    >  請檢查**長行換行**方塊，如果您想要檢視整份文件執行個體內容包裝到精靈的 [編輯] 方塊。  
  
    > [!NOTE]
    >  如果您從交換執行個體建立結構描述，只要選取表示個別文件結構的部分。  
  
## <a name="delimit-purchase-order-record"></a>分隔訂單記錄  
  
-   因為訂單的每一行結尾所傳回的歸位字元與換行字元 (CRLF) 中，選取**依分隔符號**，然後按一下 **下一步**上**選取記錄格式**螢幕。  
  
## <a name="specify-purchase-order-record-property"></a>指定訂單記錄屬性  
  
-   在**分隔記錄**畫面上，輸入下列定義的結構描述的第一個層級，以及當您完成之後，按一下 **下一步**。  
  
    -   **子分隔符號：**選取**{CR} {LF}**。  
  
        > [!NOTE]
        >  **子分隔符號**屬性是可編輯的方塊與下拉式選取清單包含一組預設值。 **子分隔符號**可以指定為字元或十六進位值。 例如，  **\\{**或**{0x0D0A}**。  
  
    -   **逸出字元：**逸出字元是單一字元，抑制跟隨在它後面之字元的任何特殊意義。 請參閱[逸出字元](../core/escape-characters.md)如需詳細資訊。 在此逐步解說中，將它留白。  
  
        > [!NOTE]
        >  當使用 **\\** ， **{，**和**}**如**子分隔符號**或**逸出字元**、必須使用反斜線。 例如，  **\\ \\，**和 **\\{**。  
  
    -   請檢查**記錄具有標記識別項**方塊，然後輸入**PO**中**標記**。 在多個記錄檔中， **PO**將用來識別每個個別記錄。 按 **[下一步]** ，繼續進行。  
  
     ![分隔的記錄畫面](../core/media/flatfileschemawizard-delimitedrecord1.gif "FlatFileSchemaWizard_DelimitedRecord1")  
  
## <a name="define-the-element-in-the-purchase-order-record"></a>定義訂單記錄中的元素  
  
1.  精靈已在訂單記錄中識別四個項目；您現在必須定義項目屬性。 在第一個資料列中，執行下列動作：  
  
    1.  型別**日期**如**項目名稱**。  
  
    2.  選取**欄位項目**如**項目型別**。  
  
    3.  選取**日期**從下拉式選取清單中，為**資料型別**。  
  
2.  對下列項目重複步驟 a 到 c。 當您完成之後時，按一下 **下一步**。  
  
    |元素名稱|項目類型|資料類型|  
    |------------------|------------------|---------------|  
    |**客戶**|**重複記錄**||  
    ||**略過**||  
    |**項目**|**資料錄**||  
  
     ![子元素畫面](../core/media/flatfileschemawizard-childelements.gif "FlatFileSchemaWizard_ChildElements")  
  
    > [!NOTE]
    >  您可以選取多個資料列，然後變更其**項目型別**為單一型別，使用滑鼠和 SHIFT 或 CTRL 鍵。  
  
    > [!NOTE]
    >  按一下 [之後**下一步**上**子項目**] 畫面上，您將無法再按一下**回**重新定義，或對子項目進行任何變更。 您必須關閉精靈再加以重新啟動，才能定義一般檔案結構描述。  
  
3.  當您完成此程序中的步驟之後，就會產生結構描述的第一個層級，如下列擷取畫面所示。 已定義三個唯一項目，您將繼續進一步為訂單記錄中的項目定義子記錄。 按一下 **[下一步]**。  
  
     ![範例結構描述螢幕](../core/media/flatfileschemawizard-schema1.gif "FlatFileSchemaWizard_Schema1")  
  
## <a name="define-the-customer-record"></a>定義客戶記錄  
  
1.  因為我們定義**客戶**項目做為**重複記錄**型別和**項目**項目做為**記錄**輸入時，BizTalk一般檔案結構描述精靈現在會繼續進一步定義這兩個元素。 在**結構描述檢視**畫面上，選取**客戶**，然後按一下 **下一步**才能繼續。  
  
2.  若要使用客戶記錄，您必須選取表示該項目的資料。 因為它是重複記錄，所以任一行都可以用來定義記錄。 選取客戶資料的第一行，然後按一下**下一步**才能繼續。  
  
3.  在**選取記錄格式**頁面上，選取**依相對位置**，然後按一下 **下一步**。  
  
4.  精靈會提供視覺化工具，以顯示和計算欄位之間的距離。 在**位置記錄**頁面上，使用滑鼠左鍵按一下位置標示 10 來表示的 [名稱] 欄位的開始位置。 按一下下列位置標示，來表示其他的資料欄位：  
  
    |欄位名稱|位置標示|  
    |----------------|---------------------|  
    |街道|30|  
    |城市|50|  
    |state|65|  
    |postalcode|68|  
  
     按 **[下一步]** ，繼續進行。  
  
     ![位置記錄畫面](../core/media/flatfileschemawizard-positionalrecord.gif "FlatFileSchemaWizard_PositionalRecord")  
  
5.  在**子項目** 頁面上，您指定的子元素的屬性。 選取第一個資料列和型別**國家/地區**為**項目名稱**。 保留其他欄位的預設值。 輸入下列值的其他屬性**項目名稱**:  
  
    |元素名稱|值|  
    |------------------|-----------|  
    |**customer_Child2**|**fullName**|  
    |**customer_Child3**|**街道**|  
    |**customer_Child4**|**縣 （市)**|  
    |**customer_Child5**|**狀態**|  
    |**customer_Child6**|**郵遞區號**|  
  
     按 **[下一步]** ，繼續進行。  
  
     ![子元素畫面](../core/media/flatfileschemawizard-childelements2.gif "FlatFileSchemaWizard_ChildElements2")  
  
6.  客戶記錄的子項目會被建立，如下列擷取畫面所示。 按一下**下一步**來定義項目記錄的子項目。  
  
     ![範例結構描述螢幕](../core/media/flatfileschemawizard-schema2.gif "FlatFileSchemaWizard_Schema2")  
  
#### <a name="define-the-items-record"></a>定義項目記錄  
  
1.  在**結構描述檢視**頁面上，選取**項目**，然後按一下 **下一步**。  
  
2.  在**選取文件資料**頁面上，選取的整行開頭的項目，然後按一下 **下一步**以定義其子項目。  
  
3.  在**選取記錄格式**頁面上，選取**依分隔符號**，然後按一下 **下一步**。  
  
4.  在 [項目] 記錄中，會使用逗號來分隔個別的項目。 因此，在**分隔記錄**頁面上，輸入下列命令來定義項目記錄。 當您完成之後時，按一下 **下一步**。  
  
    -   選取**，**從**子分隔符號**下拉式選擇清單。  
  
    -   保留**逸出字元**文字方塊留白。  
  
    -   選取**記錄具有標記識別項**和型別**項目**中**標記**。  
  
         在多個項目記錄中，**項目**用來識別每個個別的記錄。  
  
5.  使用來自值**分隔記錄**頁面上，精靈會識別兩個子元素。 因為其中一個是重複記錄時，選取第一個項目，並輸入**項目**做項目名稱，然後選取**重複記錄**從下拉式清單選取項目清單**項目類型**. 請保留欄位中的其他預設值。 選取第二個資料列，然後選取**忽略**從**項目型別**清單。 當您按一下**下一步**，結構描述中建立項目記錄的下一個層級。 您可以繼續定義訂單結構描述的最後一個部分。  
  
6.  選取**項目**，然後按一下 **下一步**繼續**結構描述檢視**頁面。  
  
7.  在**選取文件資料**頁面上，選取**ITEM872 AA &#124;割草機 &#124; 1 &#124; 148.95 &#124;確認這是電動**。 按 **[下一步]** ，繼續進行。  
  
8.  在**選取記錄格式**頁面上，選取**依分隔符號**選項，因為個別項目以管道 (&#124;) 分隔。  
  
9. 在**分隔記錄**頁面上，輸入下列命令來定義項目記錄。 當您完成之後時，按一下 **下一步**。  
  
    -   選取**&#124;**從**子分隔符號**下拉式選取清單。  
  
    -   保留**逸出字元**文字方塊留白。  
  
10. 在**子項目**頁面上，此精靈已識別五個子項目。 選取第一個資料列，並輸入**productCode**如**項目名稱**。 請保留其他欄位中的預設值。 針對其餘的**項目名稱屬性**，輸入下列命令：  
  
    |元素名稱|值|  
    |------------------|-----------|  
    |**item_Child2**|**描述**|  
    |**item_Child3**|**數量**|  
    |**item_Child4**|**單價**|  
    |**item_Child5**|**附註**|  
  
     按 **[下一步]** ，繼續進行。  
  
11. 您已定義訂單結構描述的所有節點。 在**結構描述檢視**頁面上，按一下**完成**。  
  
12. 您現在可以檢視最後的訂單結構描述。 您也可以使用 BizTalk 結構描述編輯器修改此結構描述。 一般檔案屬性名稱資料表及屬性資料表中的，請參閱 <<c0>  **結構描述節點屬性**。 這個屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="summary"></a>摘要  
 在此逐步解說中，您學習到如何使用 BizTalk 一般檔案結構描述精靈，從文件執行個體建立一般檔案結構描述。  
  
## <a name="next-steps"></a>後續步驟  
  
### <a name="validate-po-instance"></a>驗證 PO 執行個體  
 若要確定 PurchaseOrder.xsd 結構描述可以正確剖析 PO 執行個體，請執行下列動作：  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**PurchaseOrder.xsd** ，然後選取 **屬性**。  
  
2.  在**屬性頁**，請確定**輸入執行個體檔案名稱**欄位指向您在逐步解說的必要條件 > 一節中建立的 PO 執行個體的位置： 建立一般檔案從文件執行個體的結構描述。 按一下**確定**以關閉對話方塊。  
  
3.  在 [方案總管] 中，以滑鼠右鍵按一下**PurchaseOrder.xsd**，然後選取**驗證執行個體**。 驗證元件就會開啟。  
  
4.  驗證完成後，會提供一個連結，讓您根據使用 PurchaseOrder.xsd 結構描述所得到的 PO 執行個體剖析結果來檢視 XML 輸出。 若要檢視 XML 輸出，請按住 Ctrl 並按一下該連結。  
  
### <a name="create-pipelines-for-the-schema"></a>建立結構描述的管線  
 現在您可根據 PurchaseOrder.xsd 結構描述建立接收或傳送管線，以搭配 BizTalk 應用程式使用。  
  
 若要建立新的管線，請參閱[如何建立新管線](../core/how-to-create-a-new-pipeline.md)。 若要設定一般檔案管線元件，請參閱[如何設定一般檔案組合器管線元件](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)和[如何設定一般檔案解譯器管線元件](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何使用 BizTalk 一般檔案結構描述精靈](../core/how-to-use-biztalk-flat-file-schema-wizard.md)   
 [使用 BizTalk 一般檔案結構描述精靈建立結構描述](../core/creating-schemas-using-biztalk-flat-file-schema-wizard.md)