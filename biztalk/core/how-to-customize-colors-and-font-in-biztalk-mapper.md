---
title: 如何自訂色彩和字型，在 BizTalk 對應工具 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.mapper.options.colors
ms.assetid: 494e4d70-8159-4721-9378-85bfc3c3d6f2
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 724d9e3c118afc4ef0ca369be17b36f439c5885e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22250390"
---
# <a name="how-to-customize-colors-and-font-in-biztalk-mapper"></a>如何在 BizTalk 對應工具中自訂色彩和字型
您可以變更 [格線] 檢視中與各種連結類型關聯的色彩以及所選取物件的色彩。 也可以變更用以顯示結構描述樹狀結構節點的字型。 本主題提供進行這類變更的逐步指示。  
  
 您也可以選擇自訂 BizTalk 對應工具的一般設定。 如需如何選擇設定資訊，請參閱[如何自訂 BizTalk 對應工具中的一般設定](../core/how-to-customize-general-settings-in-biztalk-mapper.md)。  
  
> [!NOTE]
>  這些指示需要執行中的 BizTalk 對應工具。  
  
### <a name="to-change-the-colors-and-font-used-in-biztalk-mapper"></a>變更 BizTalk 對應工具中所用的色彩和字型  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]的 **[工具]** 功能表上，按一下 **[選項]**。  
  
2.  在**選項**對話方塊方塊中，展開  **BizTalk 對應工具**節點，然後再按一下**色彩和字型**。  
  
     ![選取色彩和字型](../core/media/colorsfonts-options.gif "ColorsFonts_Options")  
  
3.  使用與各個色彩屬性關聯的下拉式色彩選擇器，變更各種連結類型、編譯器警告、格線前景以及格線背景的色彩。  
  
     可以使用以下色彩選項：  
  
    -   **子節點連結。** 用於繪製摺疊父系之子系連結的色彩。  
  
    -   **編譯器錯誤。** 用於繪製編譯器錯誤的色彩。  
  
    -   **編譯器連結。** 編譯器連結的色彩，編譯器連結是指編譯器指示詞連結。 設定來源與目的結構描述樹狀結構欄位間的連結時，會自動建立這類連結。  
  
    -   **呈現暗灰色的連結。** 用來繪製未選取或未反白顯示之連結的色彩。  
  
    -   **彈性連結。** 彈性連結的色彩，彈性連結是指從來源結構描述樹狀結構拖曳到目的結構描述樹狀結構的簡單值複製 (value-copy) 連結。 在建立此連結之後，連結的色彩就會變成固定連結的色彩。  
  
    -   **一般連結。** 用於繪製兩個端點都在檢視中之連結 (未選取任何項目時) 的色彩。  
  
    -   **格線背景。** 格線頁中背景的色彩。  
  
    -   **格線行。** 用於繪製格線行的色彩。  
  
    -   **反白顯示的連結。** 用於反白顯示連結的色彩。  
  
    -   **指示符合連結。** 用於繪製指示符合連結的色彩。  
  
    -   **部分不在範圍中的連結。** 用於繪製只有一個端點在檢視中之連結的色彩。  
  
    -   **結構描述節點字型色彩。** 用於繪製結構描述樹狀結構節點的色彩。  
  
    -   **搜尋結果。** 用於繪製結構描述樹狀結構上之搜尋相符項的色彩。  
  
    -   **選取的格線物件。** 用於繪製格線介面中的選項的色彩。  
  
    -   **完全超出範圍中的連結。** 用於繪製兩個端點都不在檢視中之連結的色彩。  
  
4.  按一下省略符號 (**...**) 按鈕位於右邊**結構描述節點字型**屬性值方塊。  
  
5.  在**字型**對話方塊中，變更主要編輯視窗中的檢視表中使用的字型。  
  
6.  按一下 **[確定]**。 就會套用選擇的設定。  
  
    > [!IMPORTANT]
    >  如果您不想要使用自訂的設定，請按一下**還原成預設值**中**選項** 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk 對應工具](../core/using-biztalk-mapper.md)