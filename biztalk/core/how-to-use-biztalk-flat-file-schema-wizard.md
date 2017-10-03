---
title: "如何使用 BizTalk 一般檔案結構描述精靈 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7cb8b18-266d-422e-bdb8-1efefb6b4c8e
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff7d87959bd39b9040a495022c2b7bf352954848
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-biztalk-flat-file-schema-wizard"></a>如何使用 BizTalk 一般檔案結構描述精靈
在舊版 BizTalk Server 中，您必須在 BizTalk 結構描述編輯器中手動將註解新增至 XML 結構描述定義語言 (XSD) 結構描述，讓這些結構描述可被「一般檔案管線」元件所瞭解，例如一般檔案解譯器和一般檔案組合器。 您仍可使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 結構描述編輯器達成這個目的。 若要減少手動步驟的次數以及建立方案所需的時間，您可使用 BizTalk 一般檔案結構描述精靈，此精靈提供下列功能：  
  
-   使用真正的一般檔案執行個體做為輸入。  
  
-   包含視覺化設計介面，可處理分隔和位置一般檔案結構描述。  
  
-   使用可重新進入的精靈程序，可新增項目至結構描述和以互動方式定義一般檔案的相關註解。  
  
-   提供標記識別項和字元以及十六進位分隔符號的支援。  
  
-   自動決定標記識別線偏移以及子分隔順序。  
  
-   提供檔案格式的預覽功能。  
  
-   可讓您在交換執行個體中選取要用來定義一般檔案結構描述的慣用子資料。  
  
## <a name="how-to-start-the-biztalk-flat-file-schema-wizard"></a>如何啟動 BizTalk 一般檔案結構描述精靈  
 您可從 Microsoft Visual Studio [方案總管] 或 BizTalk 結構描述編輯器啟動此精靈。  
  
#### <a name="to-start-the-wizard-from-solution-explorer"></a>從方案總管啟動此精靈  
  
1.  在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟**方案總管 中**。  
  
2.  若要加入新的一般檔案結構描述，以滑鼠右鍵按一下 BizTalk 專案，然後選取**新增**。  
  
3.  按一下**新項目。**  
  
     ![方案總管功能表](../core/media/flatfileschemawizard-01.gif "FlatFileSchemaWizard_01")  
  
4.  在**加入新項目**視窗中，執行下列動作：  
  
    1.  在**類別**區段中，選取**結構描述檔案**。  
  
    2.  在**範本**區段中，選取**一般檔案結構描述精靈**。  
  
    3.  在**名稱** 文字方塊中，輸入新的結構描述的名稱。  
  
    4.  按一下 **[加入]**。  
  
         BizTalk 一般檔案結構描述精靈會開啟。  
  
#### <a name="to-start-the-wizard-from-the-schema-editor"></a>從結構描述編輯器啟動此精靈  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟**方案總管 中**。  
  
2.  若要加入新的一般檔案結構描述，以滑鼠右鍵按一下 BizTalk 專案，然後選取**新增**。 選取**新項目**按一下**新項目**。  
  
3.  在**加入新項目**視窗中，執行下列動作：  
  
    1.  在**類別**區段中，選取**結構描述檔案**。  
  
    2.  在**範本**區段中，選取**一般檔案結構描述**。  
  
    3.  在**名稱** 文字方塊中，輸入新的結構描述的名稱。  
  
    4.  按一下 **[加入]**。  
  
    5.  以滑鼠右鍵按一下**根**選取**從一般檔案執行個體定義記錄**。  
  
         BizTalk 一般檔案結構描述精靈現在會啟動。  
  
> [!NOTE]
>  如果您有結構描述編輯器中開啟工作結構描述，您只需要為所選取的節點上按一下滑鼠右鍵，然後選取**從一般檔案執行個體定義記錄**。  
  
> [!NOTE]
>  **從一般檔案執行個體定義記錄**選項已啟用選取的節點為不含子項目的記錄。 如果選取的節點包含子項目，此精靈就會刪除目前所有的子項目，然後產生新的子項目。 在刪除現有的子項目之前，精靈會先提示您進行確認。  
  
## <a name="considerations-for-using-the-flat-file-schema-wizard"></a>使用一般檔案結構描述精靈的考量  
 此節描述在使用 BizTalk 一般檔案結構描述精靈時，您應考量的問題。  
  
### <a name="working-with-multibyte-character-set-mbcs"></a>使用多位元組字元集 (MBCS)  
 根據預設，**計算位置，以位元組為單位**核取方塊未選取 [一般檔案結構描述資訊] 畫面上。 精靈會以字元為單位計算位置；也就是說，如果在位置一般檔案執行個體中有 MBCS 字元，位置就無法被正確計算。 藉由選取**計算位置，以位元組為單位**核取方塊，精靈會顯示與其他表示其位置長度的 MBCS 字元。 字元會顯示上的一個位置，以點號"•"填寫剩餘的長度。 所填入的點號數量將取決於以雙位元組字元集 (DBCS)、Unicode 或 UTF-8 格式儲存的檔案。  
  
### <a name="code-pages-supported-in-the-flat-file-schema-wizard"></a>一般檔案結構描述精靈中支援的字碼頁  
 以下是此精靈支援的字碼頁清單：  
  
-   阿拉伯文 (1256)  
  
-   ASCII (20127)  
  
-   波羅的海文 (1257)  
  
-   Big-Endian-UTF16 (1201)  
  
-   中歐語系 (1250)  
  
-   斯拉夫文 (1251)  
  
-   希臘文 (1253)  
  
-   希伯來文 (1255)  
  
-   日文 (Shift-JIS) (932)  
  
-   韓文 (949)  
  
-   Little-Endian-UTF16 (1200)  
  
-   簡體中文 (GBK) (936)  
  
-   簡體中文 (GB18030) (54936)  
  
-   泰文 (874)  
  
-   繁體中文 (Big5) (950)  
  
-   土耳其文 (1254)  
  
-   UTF-7 (65000)  
  
-   UTF-8 (65001)  
  
-   越南文 (1258)  
  
-   西歐語系 (1252)  
  
### <a name="record-types-in-the-flat-file-schema-wizard"></a>一般檔案結構描述精靈中的記錄類型  
 一般檔案在位置記錄中不可包含分隔記錄。 由於精靈是可重新進入基礎，選項按鈕所定義的類型**依分隔符號**和**依相對位置**已啟用或停用的父記錄格式您在精靈中定義之子系。 例如，  
  
-   如果精靈是對分隔記錄的子系執行，則兩個選項按鈕都會被選取。  
  
-   如果您的子系位置記錄中，執行精靈**依分隔符號**清除選項按鈕。  
  
### <a name="delimiter-symbols-in-the-flat-file-schema-wizard"></a>一般檔案結構描述精靈中的分隔符號  
 子分隔符號屬性下拉式清單包含下列常見的分隔符號：  
  
-   {CR}{LF}  
  
-   {CR}  
  
-   {LF}  
  
-   {TAB}  
  
-   {SPACE}  
  
-   {0x1A}  
  
-   &#124;  
  
-   ,  
  
-   ;  
  
 此屬性的預設值為 {CR}{LF}。 此屬性也是一個可編輯的文字方塊，可讓您指定子分隔符號做為字元序列或字元的十六進位值。 使用字元做為子分隔符號的範例包括 "a" 或 "street"。 十六進位分隔符號使用下列格式指定：  
  
-   {0xnnnn}。 例如，{0x0D}{0x0A}、{0x09} 或 {0x20}。  
  
 使用十六進位值序列的範例為 {0x0D}{0x0A}、{0x09}{0x20}。  
  
 如果您使用符號\\，{，或} 做為分隔符號，您必須取代分隔符號之前的額外反斜線符號，否則您會收到錯誤訊息。 例如，  
  
-   \\\\\\{，或\\}。  
  
### <a name="relative-positions-in-the-flat-file-schema-wizard"></a>一般檔案結構描述精靈中的相對位置  
  
#### <a name="setting-position-markers"></a>設定位置標記  
 使用滑鼠左鍵按一下位置選取方塊，若要設定新的位置標記行中的位置標記。 位置標記會以實線表示。 依照預設，位置標記行是在位置零的記錄開頭。 若要移除現有的位置標記行，使用滑鼠左鍵按一下它。  
  
### <a name="escape-characters-in-the-flat-file-schema-wizard"></a>一般檔案結構描述精靈中的逸出字元  
 逸出字元是隱藏其後任何特殊意義字元的單一字元。 如需詳細資訊，請參閱[逸出字元](../core/escape-characters.md)下的主題[方式解譯特殊字元做為欄位值的一部分](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)。 您可在精靈中使用逸出字元，以指定在剖析一般檔案執行個體時要使用的逸出字元。 預設值為空值，表示會使用在結構描述層級所指定的預設逸出字元。  
  
 逸出字元可指定為字元或十六進位值。 十六進位值使用下列格式指定：  
  
-   {0xnnnn}。 例如，{0x0D}{0x0A}、{0x09} 或 {0x20}。  
  
 如果您使用符號\\，{，或} 做為逸出字元，您必須取代分隔符號之前的額外反斜線符號，否則您會收到錯誤訊息，例如  
  
-   \\\\, \\{, \\}.  
  
### <a name="child-elements-in-the-flat-file-schema-wizard"></a>一般檔案結構描述精靈中的子項目  
 每個子項目包含**項目名稱**，**項目型別**，**資料型別**和**內容**。 您使用**項目名稱**文字方塊中輸入節點的有意義的名稱。 **項目型別**是下拉式清單具有下列值：  
  
-   **欄位項目**： 指定此節點會做為項目結構描述中建立。  
  
-   **欄位屬性**： 指定此節點會做為屬性結構描述中建立。  
  
-   **記錄**： 指定不含子系的記錄，將建立結構描述中。  
  
-   **重複記錄**： 指定不含子系的記錄將建立結構描述中，且其最大的項目設定為**Unbounded**。  
  
-   **忽略**： 不會建立這個節點的結構描述中。  
  
 根據預設所有項目屬於類型**欄位項目**而且其資料類型為**字串**。  
  
> [!NOTE]
>  子元素可以宣告為**欄位屬性**只有當沒有任何子系之前它會宣告為**欄位項目**，**記錄**或**重複記錄**。  
  
> [!NOTE]
>  您會看到驚嘆號前面**子節點**在下列情況：  
  
-   **欄位屬性**之後**欄位項目**，**記錄，**或**重複記錄**。  
  
-   此子項目沒有名稱。  
  
-   此子項目有重複的名稱。  
  
-   子項目的選定資料類型不適合內容。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk 一般檔案結構描述精靈逐步解說](../core/biztalk-flat-file-schema-wizard-walkthrough.md)