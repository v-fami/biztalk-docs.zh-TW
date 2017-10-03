---
title: "如何管理 XSD 檢視 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3245ebf0-6128-47b4-8e88-ea06ececbc15
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 945f3fc4d8eac3b09279ea774209a9f43a0f6bd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manage-the-xsd-view"></a>如何管理 XSD 檢視
與 XSD 檢視相關的管理工作可以分為三類：變更其大小、變更其背景色彩和字型以及變更其重新整理特性。  
  
 最後一個類別，即重新整理特性，在使用自動重新整理可能造成長時間延遲的大型結構描述時最有用。 在此情況下，您可以停用自動 (連續) 重新整理，以必要時手動重新整理 XSD 檢視取代。  
  
 本主題提供這些工作的逐步解說。  
  
### <a name="to-make-the-xsd-view-taller-or-shorter"></a>使 XSD 檢視較高或較矮  
  
1.  將滑鼠指標移至 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主要編輯視窗的下邊緣 (在結構描述樹狀結構檢視旁會顯示 XSD 檢視)，直到指標變成標準的視窗垂直大小調整圖示。  
  
2.  按住滑鼠左鍵並上下拖曳視窗邊緣。  
  
     藉由垂直調整整個主要編輯視窗的大小，您已垂直調整 XSD 檢視的大小。  
  
### <a name="to-make-the-xsd-view-wider-or-more-narrow"></a>使 XSD 檢視較寬或較窄  
  
1.  移動滑鼠游標至 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主要編輯視窗中的窗格分割線 (用來分割 XSD 檢視和結構描述樹狀結構檢視)，直到游標變成標準的視窗水平調整大小圖示。  
  
2.  按住滑鼠左鍵並左右拖曳 (調整寬窄) 窗格邊緣。  
  
     藉由變更 XSD 檢視所使用的主要編輯視窗的大小 (相對於結構描述樹狀結構檢視的大小)，您已水平調整 XSD 檢視的大小。  
  
     您也可以水平調整整個主要編輯視窗的大小，使 XSD 檢視較寬或較窄。  
  
### <a name="to-change-the-background-color-andor-font-used-by-the-xsd-view"></a>變更 XSD 檢視所使用的背景色彩和/或字型  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]的 **[工具]** 功能表上，按一下 **[選項]**。  
  
2.  在**選項**對話方塊中，按一下 [BizTalk 編輯器] 資料夾中，並有必要，展開**結構描述顯示**類別目錄，按一下加號 （+） 圖示。  
  
3.  使用下拉式色彩選擇器來變更背景色彩和/或字型和 （或)**字型**對話方塊相關聯**XSD 檢視背景色彩**和**XSD 檢視字型**屬性，分別。  
  
     存取**字型**對話方塊中，使用省略符號 (**...**) 按鈕位於右邊**XSD 檢視字型**屬性值方塊。  
  
### <a name="to-turn-automatic-refresh-of-the-xsd-view-on-and-off"></a>開啟和關閉 XSD 檢視的自動重新整理  
  
-   在 BizTalk 編輯器 中，以下**XSD**索引標籤上，按一下 **關閉自動重新整理**或**開啟自動重新整理**。  
  
     自動重新整理關閉時，XSD 檢視為空白。  
  
    > [!IMPORTANT]
    >  依照預設，自動重新整理為開啟。 當您的結構描述變得越來越大，關閉自動重新整理功能，改為視需要手動重新整理結構描述也漸漸變得重要。  
  
### <a name="to-manually-refresh-the-xsd-view"></a>手動重新整理 XSD 檢視  
  
-   在**BizTalk**功能表上，按一下 **重新整理 XSD**。  
  
     會更新 XSD 檢視，以反映您對結構描述樹狀結構所做的任何變更。  
  
    > [!NOTE]
    >  您可以按一下也可以手動重新整理 XSD 檢視**重新整理 XSD**相關聯的結構描述樹狀目錄中，或按一下每個節點的捷徑功能表上**重新整理**下面的連結**XSD** XSD 檢視中的索引標籤。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk 編輯器](../core/using-biztalk-editor.md)