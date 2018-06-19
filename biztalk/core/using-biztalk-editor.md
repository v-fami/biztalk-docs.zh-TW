---
title: 使用 [BizTalk 編輯器] |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 22021272-f028-4db3-ad8a-fb89a5340910
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdb293e6255042a46ecef16855d723c38543310c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287894"
---
# <a name="using-biztalk-editor"></a>使用 BizTalk 編輯器

## <a name="overview"></a>概觀
「BizTalk 編輯器」位於 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Shell 中。 「BizTalk 編輯器」中的部分功能依賴 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Shell 的現有使用者介面項目。 例如，使用**檔案**，**編輯**，和**檢視**功能表，如同您對其他開發中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。 會提供此常用功能的相關資訊**協助**功能表。  
  
 當您新增結構描述至 BizTalk 專案、在 BizTalk 專案中開啟現有結構描述 (.xsd 檔案) 或按一下 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主編輯視窗中的索引標籤以重新啟動結構描述時，BizTalk 編輯器會變成作用中。  
  
> [!NOTE]
>  BizTalk 編輯器會使用 UTF-16 字元編碼，以儲存結構描述檔。  

## <a name="views"></a>檢視  
 下圖顯示 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Shell 中的各種不同檢視，這些檢視是 BizTalk 編輯器的一部分。  
  
 ![BizTalk 專案的不同部分](../core/media/differentpartsofbiztalkserver.gif "DifferentpartsofBizTalkServer")  
  
 BizTalk 編輯器是由下列 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Shell 中的檢視以及其相關對話方塊所組成：  
  
-   **結構描述樹狀結構。** 此檢視位於主左邊[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]編輯視窗。 您可以藉由在此檢視中建置描述結構描述定義的訊息之結構的樹狀結構，主動建構結構描述。 如需 BizTalk 結構描述結構描述樹狀結構檢視中的呈現方式的詳細資訊，請參閱[BizTalk 結構描述的表示法](../core/biztalk-representation-of-schemas.md)。  
  
-   **XSD 檢視。** 此檢視位於主右邊[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]編輯視窗。 它所顯示的 XML 結構描述定義 (XSD) 語言結構，會呈現您正在結構描述樹狀結構檢視中建構的結構描述。 此為唯讀檢視，可用來協助您適應您所建立之結構描述的 XSD 語法。 您可以依照您的慣用設定來調整檢視的分隔方式，呈現僅能看見 XSD 檢視的狀態。  
  
-   **方案總管 中。** 此檢視位於右邊[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]殼層。 其中會顯示 BizTalk 專案和所包含的各種項目。 使用 [方案總管] 可將新的和現有的結構描述加入專案，以及開啟已經是專案一部分的結構描述。 例如，若要建立新的結構描述，以滑鼠右鍵按一下方案總管] 視窗中的 BizTalk 專案中，按一下**新增**，按一下 [**新項目**，然後使用**加入新項目**對話方塊方塊，即可命名和建立新的結構描述。  
  
-   [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]  **屬性視窗。** 您可以使用此視窗，來檢查和設定大部分的結構描述和節點屬性。 當您在結構描述樹狀結構檢視中選取節點，或在 [方案總管] 視窗中選取結構描述時，該節點或結構描述的對應屬性會使用標準 Visual Studio 範例，顯示於 [屬性] 視窗中。 例如，屬性會分組成不同類別，並可根據這些類別或字母順序來顯示。 如需不同的屬性，就可以選取不同類型的節點或結構描述集合的詳細資訊，請參閱**結構描述屬性參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
 除了這些檢視之外，您可以與許多對話方塊互動。 當您在編輯複雜的屬性 (例如集合) 時，通常會開啟這些對話方塊。  
  
 本節將提供 BizTalk 編輯器中可用之檢視、命令和快速鍵的相關資訊。  
  
## <a name="next-steps"></a>後續的步驟 
  
-   [如何管理結構描述樹狀檢視](../core/how-to-manage-the-schema-tree-view.md)  
  
-   [如何管理 XSD 檢視](../core/how-to-manage-the-xsd-view.md)  
  
-   [如何管理 [屬性] 視窗](../core/how-to-manage-the-properties-window.md)  
  
-   [如何管理其他 Visual Studio 視窗](../core/how-to-manage-other-visual-studio-windows.md)  
  
-   [使用 BizTalk 編輯器命令](../core/using-biztalk-editor-commands.md)  
  
-   [使用大型結構描述](../core/working-with-large-schemas.md)