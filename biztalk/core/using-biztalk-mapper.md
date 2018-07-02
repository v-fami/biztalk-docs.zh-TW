---
title: 使用 BizTalk 對應工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.mapper.grid
ms.assetid: 07c69603-ee79-44b2-80b1-6ae4e4c8fb4e
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dfa3ac3d03e5f9537284ea4e4371ab5a443d2b42
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967527"
---
# <a name="using-biztalk-mapper"></a>使用 BizTalk 對應工具

## <a name="overview"></a>概觀
BizTalk 對應工具位於 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Shell 中。 「BizTalk 對應工具」中的某些功能依賴 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Shell 的使用者介面項目。 例如，使用**檔案**，**編輯**，並**檢視**功能表，如同您會在其他開發[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。 會提供此常用功能的相關資訊**協助**功能表。  
  
 當您新增對應至 BizTalk 專案、開啟現有對應 (.btm 檔案) 或按一下 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主編輯視窗中的索引標籤以重新啟動對應時，「BizTalk 對應工具」會變成作用中。  
  
> [!NOTE]
>  「BizTalk 對應工具」使用 UTF-16 字元編碼來儲存對應檔。  
>
>  當您將現有的成品到 BizTalk 專案時，建置動作一律會設定為**BtsCompile**。 即使您重新命名現有的構件，其建置動作設為預設值**BtsCompile**。 因此，新增或重新命名現有的成品時，您必須根據是否要建置該特定成品來適當設定建置動作。  

## <a name="parts-of-the-biztalk-mapper"></a>組件的 BizTalk 對應工具  
 下圖顯示 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中 BizTalk 對應工具的各個部分。  
  
 ![BizTalk 對應工具](../core/media/mapper-views.gif "Mapper_Views")  
  
 其中每個檢視的功能如下：  
  
- **Visual Studio 對應工具公用程式功能區。** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Mapper 提供公用程式功能區，以呈現此對應工具的相關命令。 此功能區會提供來源結構描述資訊、來源與目的結構描述相關性檢視的切換按鈕、用來顯示或隱藏完全在範圍外之連結的切換按鈕、用來開啟或關閉自動捲動功能的切換開關、用來移動瀏覽對應工具介面的按鈕、縮放控制項，以及搜尋文字方塊。 下圖顯示您可以在格線頁面上方看見的公用程式功能區。  
  
   ![對應工具功能區](../core/media/mapper-ribbon.gif "Mapper_Ribbon")  
  
- **來源結構描述樹狀結構檢視。** 此檢視與目的結構描述樹狀結構檢視和格線檢視共用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主編輯視窗。  
  
   就如其名所示，此檢視會顯示描述執行個體訊息的結構描述，而這些訊息是對應的來源。 定義對應的連結會從來源結構描述樹狀結構檢視引導至格線檢視，最後引導至目的結構描述樹狀結構檢視。  
  
   如需 BizTalk 結構描述結構描述樹狀結構檢視中的呈現方式的詳細資訊，請參閱[BizTalk 結構描述的表示法](../core/biztalk-representation-of-schemas.md)。  
  
- **目的結構描述樹狀結構檢視。** 此檢視與來源結構描述樹狀結構檢視和格線檢視共用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主編輯視窗。  
  
   就如其名所示，此檢視會顯示描述執行個體訊息的結構描述，而這些訊息是對應的目的地。 定義對應的連結會從格線檢視 (最終是從來源結構描述樹狀結構檢視) 引導至目的結構描述樹狀結構檢視。  
  
   如需 BizTalk 結構描述結構描述樹狀結構檢視中的呈現方式的詳細資訊，請參閱[BizTalk 結構描述的表示法](../core/biztalk-representation-of-schemas.md)。  
  
- **格線檢視。** 此檢視與來源結構描述樹狀結構檢視和目的結構描述樹狀結構檢視共用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主編輯視窗，其中來源結構描述樹狀結構檢視靠左，而目的結構描述樹狀結構檢視靠右。  
  
   就如其名所示，此檢視扮演定義對應時的關鍵角色，其中包含了連結與運算質來控制來源執行個體訊息中的資料如何轉換成符合目的結構描述的執行個體訊息。  
  
   格線檢視可以有多個圖層 (稱為格線頁)，可讓您將複雜的對應組織成對應的邏輯子部分。 一般而言，格線頁所使用的空間多過於一次可顯示的空間，有多種有效的方法可讓您在格線頁中捲動。  
  
   您可以在此檢視中主動作業以建構對應。  
  
- **Visual Studio 工具箱視窗。** 您可以使用此檢視以顯示可用於 BizTalk 對應中的運算質，並作為拖放運算質以放置在格線頁中之作業的來源。  
  
   顯示在工具箱中的運算質會根據其類別來組織。 如需有關可用的運算質的詳細資訊，請參閱[運算質在對應中的](../core/functoids-in-maps.md)。 另請參閱**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 
  
- **Visual Studio 屬性視窗。** 您可以使用此檢視及其相關的對話方塊，以檢查和設定連結的屬性以及您所建立用以定義對應之運算質的屬性。  
  
   當您在格線檢視中的格線頁中選取連結或運算質時，在來源或目的結構描述樹狀結構檢視中，選取的結構描述節點，或選取中的地圖**方案總管 中**視窗，該連結、 運算質的對應屬性結構描述節點或對應中會出現**屬性**視窗中使用標準 Visual Studio 的慣例。 例如，屬性會分組成不同類別，並可根據這些類別或字母順序來顯示。  
  
   如需不同的可供連結、 運算質、 結構描述節點或對應本身的屬性集的詳細資訊，請參閱**對應屬性參考**而**結構描述屬性參考**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
- **Visual Studio 工作清單] 和 [輸出視窗。** 您可以使用這些檢視以檢查驗證、編譯及測試 BizTalk 對應的結果，其使用方式與在編譯原始程式碼和建置其他專案類型時使用這些檢視的方式相同。  
  
  除了這些檢視之外，您可以與許多對話方塊互動。 當您在編輯複雜的屬性 (例如運算質的輸入參數) 時，通常會開啟這些對話方塊。  
  
  您時常會將 [方案總管] 視窗與「BizTalk 對應工具」搭配使用。 比方說，若要建立新的對應，以滑鼠右鍵按一下 BizTalk 專案中的**方案總管**] 視窗中，按一下**新增**，按一下 [**加入新項目**，然後使用**加入新項目**對話方塊，即可命名和建立新的對應。  
  
## <a name="next-steps"></a>後續的步驟
  
-   [使用 BizTalk 對應工具命令](../core/using-biztalk-mapper-commands.md)  
  
-   [使用格線頁](../core/working-with-grid-pages.md)  
  
-   [如何管理檢視](../core/how-to-manage-views.md)  
  
-   [如何自訂色彩和字型，在 BizTalk 對應工具](../core/how-to-customize-colors-and-font-in-biztalk-mapper.md)  
  
-   [如何展開和摺疊結構描述樹狀結構](../core/how-to-resize-the-schema-picker-and-expand-and-collapse-the-schema-trees.md)  
  
-   [如何復原或重做使用者作業](../core/how-to-undo-or-redo-user-operations.md)  
  
-   [如何搜尋對應項目](../core/how-to-search-for-map-items.md)  
  
-   [在 BizTalk 對應工具中使用增強功能](../core/using-enhanced-features-in-biztalk-mapper.md)  
  
-   [如何檢視資訊提示和工具提示](../core/how-to-view-infotip-and-tooltip.md)  
  
## <a name="see-also"></a>另請參閱  
 [如何最佳化連結顯示](../core/how-to-optimize-the-display-of-links.md)