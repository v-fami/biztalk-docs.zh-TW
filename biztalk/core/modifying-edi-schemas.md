---
title: 修改 EDI 結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fa33c5e-17ca-4aaf-a1ca-1972a9bb45ac
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ac79b7a8dc6b33c7841003936c0b961bec812f8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023196"
---
# <a name="modifying-edi-schemas"></a>修改 EDI 結構描述
您可以修改 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中現有的 EDI 結構描述。 當您和交易夥伴都同意修改標準結構描述，而且可能還變更了相關的「訊息實作指南」(Message Implementation Guideline，MIG) 檔案，您可以使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 [BizTalk 編輯器] 來修改該結構描述。  
  
> [!NOTE]
>  有些結構描述修改 (欄位交互驗證和 HIPAA 子文件分割) 包括變更 EDI 結構描述中的註解。 這類變更無法透過「BizTalk 編輯器」完成，而是使用像是「記事本」這樣的文字編輯器來進行。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
## <a name="schema-naming-convention"></a>結構描述命名慣例  
 EDI 結構描述會用自己的根名稱和命名空間來識別。 您無法在相同的 BizTalk 群組中部署兩個具有相同根名稱和命名空間的結構描述。 您無法修改任何 EDI 結構描述的根名稱或是在根名稱中加入其他資訊，因為使用標準命名慣例的根名稱不能包含版本和文件類型。 因此，若您要在相同的 BizTalk 群組中部署兩個具有相同根名稱的結構描述，您必須分別為這兩個結構描述使用不同的命名空間。  
  
 公司在相同 BizTalk 群組中，針對兩個或更多個不同交易夥伴部署相同但為不同版本之結構描述的做法並不罕見。 但是我們現在討論的是具有相同版本和相同文件類型的兩個結構描述。 若要部署這些結構描述，您將必須針對個別結構描述使用不同的命名空間。  
  
## <a name="edi-schema-changes"></a>EDI 結構描述變更  
 您可以在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中對 EDI 結構描述進行下列變更：  
  
|以進行此動作|執行方式|  
|----------------|-------------|  
|變更列舉<br /><br /> (就像代碼清單中的值清單)|在內容中的項目，開啟**列舉型別編輯器**並新增值，或從列舉清單刪除一個值。|  
|變更資料元素的選用性|變更**Min Occurs**屬性。 變更為 0 時，欄位就成為選用項目，若是變更為 1，欄位就成為必要項目。|  
|變更資料元素可出現在檔案中的最多次數|變更**Max Occurs**屬性。|  
|變更在資料元素中的字元數目|變更**長度**屬性。|  
|變更資料元素的資料型別|變更**基底資料型別**或是**日期類型**屬性。|  
|加入自訂欄位|插入子欄位項目結構描述節點，並設定其屬性 (Property)。 **注意：** EDI 結構描述中的記錄中加入子欄位屬性不允許，因為會不保證的元素序列。 加入子欄位屬性 (Attribute) 會產生無效的結構描述。 您只可以在 EDI 結構描述的記錄中加入子欄位項目。|  
|加入自訂記錄|插入子欄位記錄結構描述節點，設定其屬性 (Property)，然後加入子欄位項目。|  
|刪除子欄位或記錄|刪除自訂欄位，或是包括子欄位項目的自訂記錄。|  
|啟用欄位交互驗證|將結構描述 appinfo 區段中註解中設定欄位交互驗證旗標**是**。 此旗標是**X12ConditionDesignator_Check** （適用於 X12 或 HIPAA 結構描述） 或**EdifactDependencyRule_Check** （適用於 EDIFACT 結構描述）。<br /><br /> 透過指定關係條件 (X12 和 HIPAA) 或相依性規則 (EDIFACT)，啟用針對特定項目的欄位交互驗證。 如需詳細資訊，請參閱 <<c0> [ 設定欄位交互驗證](../core/configuring-cross-field-validation.md)。<br /><br /> 您也需要設定**Edi 類型驗證**屬性設**是**。<br /><br /> 預設會針對 HIPAA 結構描述啟用欄位交互驗證。|  
|啟用 HIPAA 子文件分割|在其中一個 HIPAA 結構描述，您可以設定子文件分割中，設定**subdocument_break**並**Split_Without_Sibling_Data**屬性的結構描述**是**而**subdocument_creation_break**屬性結構描述中特定項目的**是**。<br /><br /> 您也需要設定**輸入批次處理選項**協議屬性設**交換分割為交易集**。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 分割 HIPAA 子文件](../core/splitting-hipaa-subdocuments.md)。|  
|新增觸發欄位至 HIPAA 文件|您可以允許 EDI 解譯器使用稱為觸發欄位的合格項目，為 HIPAA 文件建立唯一的 XML 記錄。 您必須指定描述區段的屬性與觸發值，才能為區段建立唯一的 XML 記錄。 如需詳細資訊，請參閱 < [HIPAA 結構描述觸發欄位註解](../core/hipaa-schema-trigger-field-annotations.md)。|  
|新增區段至 X12 交易集|當您新增區段至 X12 交易集時，會使用區段名稱的前 3 個字元做為區段識別碼。 因此，建議您命名區段時，必須讓前 3 個字元是唯一的。|  
|新增迴圈至 HIPAA 交易集|當您新增迴圈至 HIPAA 交易集時，建議您在迴圈名稱中包含 “Loop”。 迴圈的範例格式為 “TS837_2010AB_Loop”。 **注意：** 在迴圈中的第一個區段是必要的 （區段的 minOccurs 必須等於 1） 若要避免模稜兩可。|  
|新增 ‘any order loop’ 至 HIPAA 交易集|當交易集有多個相同區段具有不同語意時，您必須在子迴圈中定義它們。 使用 XML 註解的岐\<xs: all\>可讓以任何順序出現相同的區段。<br /><br /> 建議您在 ‘any order loop’ 的迴圈名稱中包含 “SubLoop”。 範例格式為"TS837Q1_2010A_SubLoop"**附註：** 的 any order loop 項目必須只能出現一次迴圈內。 為避免岐義，子迴圈的同層級項目必須將 maxOccurs 設為 1。|  
  
### <a name="to-modify-an-existing-edi-schema-in-biztalk-editor"></a>若要用 BizTalk 編輯器來修改現有的 EDI 結構描述  
  
1. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，將您要修改的結構描述加入到某個專案，然後用 [BizTalk 編輯器] 開啟該結構描述。  
  
   > [!NOTE]
   >  您可以在圖形表單中顯示的結構描述，依序按一下**EDI**  索引標籤底部的 結構描述編輯器 畫面。 使用表格式格式的結構描述節點更易於瀏覽。  
  
2. 若要變更資料元素或記錄的屬性，請在 [BizTalk 編輯器] 的左窗格中按一下適當的節點，然後在 [屬性] 視窗中變更其屬性。  
  
3. 若要變更列舉中的值，選取 在列舉**屬性**窗格中，然後按一下省略符號以開啟**列舉編輯器**。 若要加入或刪除值的清單，如有需要確保有一個值中的每一行**值**窗格。 按一下 [確定] 。  
  
4. 若要加入自訂欄位的結構描述，以滑鼠右鍵按一下主控台樹狀目錄中的 BizTalk 編輯器中的 記錄 節點，指向**插入結構描述節點**，然後按一下**子欄位項目**。 為該資料元素命名，然後將它拖曳到記錄中的適當位置。 視需要設定自訂欄位屬性的屬性。  
  
   > [!NOTE]
   >  不可以在 EDI 結構描述中的記錄上加入子欄位屬性 (Attribute)，因為這些項目沒有確定的順序。 加入子欄位屬性 (Attribute) 會產生無效的結構描述。  
  
5. 若要加入結構描述中的自訂記錄，以滑鼠右鍵按一下主控台樹狀目錄中的結構描述編輯器中的 [記錄] 節點，指向**插入結構描述節點**，然後按一下**子記錄**。 為該記錄命名，然後將它拖曳到結構描述中的適當位置。 將至少一個資料元素加入至該記錄。 視需要設定自訂記錄的屬性。  
  
6. 後結構描述完成所需的變更，您可以變更套用到結構描述屬性中，依序按一下 [根] 節點的目標命名空間 (\<結構描述\>)，然後變更**目標命名空間**屬性。  
  
7. 儲存結構描述。  
  
8. 驗證結構描述，以滑鼠右鍵按一下方案總管 中的結構描述，然後按一下**驗證結構描述**。  
  
   > [!NOTE]
   >  **驗證結構描述**命令將會驗證 EDI 結構描述，因為**Schema Editor Extension**屬性的根節點 (\<結構描述\>) 設定為**EDI結構描述編輯器延伸模組**。  
  
### <a name="to-modify-annotation-properties-in-an-existing-edi-schema"></a>若要修改現有 EDI 結構描述中的註解屬性  
  
1.  用文字編輯器 (例如 [記事本]) 開啟該結構描述。  
  
2.  若要啟用欄位交互驗證，請繼續執行下列動作。 如需詳細資訊，請參閱 <<c0> [ 設定欄位交互驗證](../core/configuring-cross-field-validation.md)。  
  
    1.  在頂端的 結構描述 appinfo 註釋，將設定欄位交互驗證旗標 (任一**X12ConditionDesignator_Check** X12 或 HIPAA 結構描述或**EdifactDependencyRule_Check** edifact結構描述） 至**是**。  
  
        > [!NOTE]
        >  欄位交互驗證旗標**是**預設會針對 BizTalk Server HIPAA 結構描述。  
  
    2.  在特定項目的註解中，針對該項目指定關係條件 (X12 或 HIPAA) 或相依性規則 (EDIFACT)。 如需有關這些設定的詳細資訊，請參閱 <<c0> [ 跨欄位區段驗證](../core/cross-field-segment-validation.md)。  
  
        > [!NOTE]
        >  在**驗證**頁面 (底下**交易集設定**一節) 的單向協議索引標籤**協議屬性**相關協議 對話方塊請確定**EDI 類型驗證**選取屬性。  
  
3.  若要啟用 HIPAA 子文件分割，請繼續執行下列動作。 如需詳細資訊，請參閱 <<c0> [ 分割 HIPAA 子文件](../core/splitting-hipaa-subdocuments.md)。  
  
    1.  在頂端的 結構描述 appinfo 註釋，將**subdocument_break**並**Split_Without_Sibling_Data**旗標**是**。  
  
    2.  在特定項目的應用程式資訊註解，請參閱**subdocument_creation_break**旗標設為**是**。  
  
        > [!NOTE]
        >  在**本機主機設定**頁面 (底下**交換設定**一節) 的單向協議索引標籤**協議屬性**針對相關的對話方塊協議，請確定**輸入批次處理選項**屬性設定為**交換分割為交易集**。  
  
## <a name="see-also"></a>另請參閱  
 [開發 EDI 結構描述](../core/developing-edi-schemas.md)