---
title: "如何設定運算質輸入參數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: bts10.mapper.functoid.inputs
ms.assetid: 2c8f773a-932c-423d-b3fe-724265304b0a
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6cd9843c46967c7d70a59b4917034e6a3795bb6d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-functoid-input-parameters"></a>如何設定運算質輸入參數
正確的設定對應中的運算質輸入參數，是在使用運算質時最重要也是最可能防止發生錯誤的其中一個方式。 您可以設定運算質輸入參數，如下所示：  
  
-   建立所連接的結構描述節點與個別運算質 （拖放滑鼠從結構描述節點的運算質） 的可見輸入的連結。  
  
-   直接編輯輸入參數使用的清單**設定\<運算質 > 運算質** 對話方塊。  
  
 此主題會逐步說明使用這些方法設定運算質的輸入參數。  
  
 使用拖曳方式建立運算質輸入參數，可方便您將與 XPath 規格有關的輸入參數指定給來源結構描述。 如需建立結構描述節點與運算質的輸入的參數資訊，請參閱[如何新增基本運算質加入至地圖](../core/how-to-add-basic-functoids-to-a-map.md)。 不過，**設定\<運算質 > 運算質**對話方塊卻是用機制來檢視所有運算質的輸入的參數、 建立和修改任何常數參數，以及重新排列必要時輸入參數的順序。  
  
 當您在格線頁上直接設定運算質的輸入參數 (繪製線條、從結構描述節點拖放滑鼠，然後連結至運算質) 時，如果輸入數目達到上限，游標就會變更成「無」狀態。 此外，狀態列會顯示該原因。 下圖顯示只接受一個輸入連結的運算質。  
  
 ![設定運算質輸入的參數無狀態](../core/media/configure-input-parameters-no-state.gif "Configure_input_parameters_NO_state")  
  
 您可以設定使用的指令碼處理 」 和 「 表格迴圈運算質**設定\<運算質 > 運算質** 對話方塊。 如需如何設定運算質的詳細資訊，請參閱[如何設定指令碼處理運算質](../core/how-to-configure-the-scripting-functoid.md)和[如何設定表格迴圈和表格擷取程式運算質](../core/how-to-configure-the-table-looping-and-table-extractor-functoids.md)。  
  
## <a name="prerequisites"></a>必要條件  
 這些指示需要執行中的 BizTalk 對應工具。  
  
## <a name="what-is-an-input-parameter"></a>什麼是輸入參數？  
 輸入參數可以是下列任何一項：  
  
-   從來源結構描述節點連至運算質的連結  
  
-   從運算質連至另一個有效運算質的連結  
  
-   常數值  
  
> [!NOTE]
>  有幾個運算質的這類**日期**，**時間**，**日期和時間**，和**Nil**，不需要任何輸入的參數。  
  
 下圖顯示的運算質 (以紅色反白顯示) 有兩個輸入參數 (Input[0] 與 Input[1]) 及一個常數參數 (Input[2])。  
  
 ![顯示運算質的輸入的參數](../core/media/identifying-input-parameters.gif "Identifying_input_parameters")  
  
## <a name="to-open-the-configure-functoid-functoid-dialog-box"></a>若要開啟 設定\<運算質 > 運算質對話方塊  
 您可以開啟**設定\<運算質 > 運算質**下列方式之一的對話方塊：  
  
-   在相關格線頁中，以滑鼠右鍵按一下運算質，然後**設定運算質輸入**。  
  
-   按兩下您要設定輸入參數的運算質。  
  
-   選取運算質，然後按一下省略符號 (**...**) 在 Visual Studio 的**屬性**視窗。  
  
-   選取運算質，然後按鍵盤的 ENTER。  
  
-   選取運算質，然後按鍵盤的 CTRL+M、CTRL+I。 如需對應工具快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
### <a name="to-insert-constant-input-parameters"></a>插入常數輸入參數  
  
1.  在**設定\<運算質 > 運算質**對話方塊中，選取**運算質輸入** 索引標籤。  
  
    > [!NOTE]
    >  **運算質輸入**預設會選取索引標籤。  
  
2.  按一下![常數輸入的參數新增至運算質](../core/media/add-input-parameters.gif "Add_input_parameters")  按鈕。 新的資料列隨即加入。  
  
3.  輸入新的輸入參數的值，然後按一下**確定**。  
  
    > [!NOTE]
    >  如果未啟用 [新增] 按鈕，運算質就不會接受或要求輸入參數，或者已經達到所允許輸入的最大數目。  
  
### <a name="to-edit-existing-constant-input-parameters"></a>編輯現有的常數輸入參數  
  
1.  在**設定\<運算質 > 運算質** 對話方塊中，按一下現有的常數輸入您想要編輯的參數。 目前值為選取核取方塊。  
  
    > [!IMPORTANT]
    >  您只能編輯常數輸入的參數。 無法編輯所有其他類型的輸入參數。 您只能予以重新排列或刪除。  
  
2.  按一下![編輯常數輸入的參數](../core/media/edit-input-parameters.gif "Edit_input_parameters")  按鈕。 常數值，進行適當的變更，然後按一下 **確定**。  
  
     或者，您也可以按兩下常數輸入參數進行編輯，或按鍵盤的 F2。  
  
## <a name="to-select-multiple-input-parameters"></a>若要選取多個輸入參數  
 您可以按住 CTRL 鍵並按一下所要的列以選取多個輸入參數，然後執行下列任何作業。 您可以按鍵盤的 CTRL+A 選取所有列。  
  
-   上下移動選取項目。  
  
    > [!NOTE]
    >  如果大量選取範圍包含所有列中最上方/最下方的列，則您無法上/下移動選取項目。  
  
-   重新排列選取項目。  
  
-   刪除選取項目。  
  
### <a name="to-change-the-order-of-existing-input-parameters"></a>變更現有輸入參數的順序  
  
1.  在**設定\<運算質 > 運算質** 對話方塊中，按一下現有輸入您要移動到輸入參數順序清單中的不同位置的參數。  
  
2.  按一下![在清單中向上移動](../core/media/move-up-button.gif "Move_up_button")  按鈕，將參數清單中的參數向上移動。 視需要重複上述步驟，直到選取的輸入參數位於想要的位置。 或者，您也可以按鍵盤的向上鍵。 如需對應工具快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
     -或-  
  
     按一下![清單中向下移動](../core/media/move-down-button.gif "Move_down_button")  按鈕，將參數往參數清單中。 視需要重複上述步驟，直到選取的輸入參數位於想要的位置。 或者，您也可以按鍵盤的向下鍵。 如需對應工具快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
    > [!IMPORTANT]
    >  您可以將只會從輸入的順序重新排列**設定\<運算質 > 運算質** 對話方塊。 如果您選取最上層或最底部資料列，![在清單中向上移動](../core/media/move-up-button.gif "Move_up_button")或![清單中向下移動](../core/media/move-down-button.gif "Move_down_button")按鈕會變成停用，分別。  
  
### <a name="to-delete-an-input-parameter-by-deleting-the-input-link"></a>刪除輸入連結以刪除輸入參數  
  
1.  在相關的格線頁中，按一下與您要刪除的輸入參數對應的輸入連結。  
  
2.  在**編輯**功能表上，按一下 **刪除**。  
  
    > [!NOTE]
    >  或者，您可以按下 DELETE 鍵，或以滑鼠右鍵按一下相關格線頁中中的連結，然後按一下**刪除**從捷徑功能表。  
  
    > [!IMPORTANT]
    >  就會無訊息地刪除該輸入連結。 如果您不確定，可以隨時復原刪除。 如需復原/取消復原作業的詳細資訊，請參閱[如何復原或重做使用者作業](../core/how-to-undo-or-redo-user-operations.md)。  
  
### <a name="to-delete-existing-input-parameters-within-the-configure-functoid-functoid-dialog-box"></a>若要刪除設定中的現有輸入的參數\<運算質 > 運算質對話方塊  
  
1.  在**設定\<運算質 > 運算質** 對話方塊中，按一下現有輸入您想要刪除的參數。  
  
    > [!NOTE]
    >  您可以使用此方式刪除任何輸入參數，甚至是與某輸入連結有關的參數。  
  
2.  按一下![刪除選取範圍](../core/media/delete-button.gif "Delete_button")  按鈕。 就會從參數清單中刪除選取的現有輸入參數。 按一下 **[確定]**。  
  
     或者，您可以選取想要刪除的資料列，然後按下鍵盤上的 DELETE 鍵。  
  
    > [!IMPORTANT]
    >  就會無訊息地刪除該輸入參數。 如果您不確定，可以隨時復原刪除。 如需復原/取消復原作業的詳細資訊，請參閱[如何復原或重做使用者作業](../core/how-to-undo-or-redo-user-operations.md)。  
  
    > [!NOTE]
    >  當參數清單中沒有任何輸入參數時，就不會啟用刪除按鈕。  
  
## <a name="to-set-labels-and-comments-for-functoids"></a>設定運算質的標籤與註解  
 您可以設定標籤與註解的運算質使用**設定\<運算質 > 運算質** 對話方塊。  
  
1.  在**設定\<運算質 > 運算質**對話方塊中，按一下 [**標籤與註解**] 索引標籤。  
  
2.  型別**標籤**和**註解**，然後按一下 **確定**。  
  
    > [!IMPORTANT]
    >  如需如何使用標籤和註解的運算質和/或連結的詳細資訊，請參閱[如何標示連結](../core/how-to-label-a-link.md)和[如何加上標籤與註解的運算質](../core/how-to-label-and-comment-a-functoid.md)。  
  
## <a name="see-also"></a>另請參閱  
 [編輯運算質屬性和輸入的參數](../core/editing-functoid-properties-and-input-parameters.md)