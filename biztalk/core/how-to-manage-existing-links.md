---
title: "如何管理現有連結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0db213b9-df84-4ebd-a59f-7691774d5031
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2e61bc8c7fbf015eba28666c63dbeabf57a39e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manage-existing-links"></a>如何管理現有連結
您有時可能需要變更連結的來源或目的、命名或重新命名連結，或刪除連結。 本主題針對執行這些類型的連結作業，提供逐步指示。  
  
### <a name="to-change-the-source-or-destination-of-a-link"></a>變更連結的來源或目的  
  
1.  在「BizTalk 對應工具」的格線頁中，按一下連結以選取連結。  
  
     格線頁中所選連結的端點會反白顯示。  
  
2.  將連結的任一端點拖曳至新的結構描述節點或要連接的運算質。  
  
     當您拖曳端點時，游標會變成十字形狀。 若您指向不能接受該連結的結構描述節點或運算質 (或其他物件)，則此游標會變成一個有線條劃過的圓圈。  
  
    > [!IMPORTANT]
    >  若您有二或多個連接到運算質的輸入連結，且您要將一或多個這些輸入連結重新導向至來源結構描述中的其他節點或其他運算質，則不會保留此原始運算質的輸入參數順序。 使用**設定\<運算質 > 運算質**對話方塊中，檢閱產生的輸入參數的順序，並視需要重新排序它們。 如需重新排序運算質的輸入的參數的詳細資訊，請參閱[編輯運算質屬性和輸入參數](../core/editing-functoid-properties-and-input-parameters.md)。  
  
### <a name="to-setedit-the-label-of-a-link"></a>若要設定/編輯連結的標籤  
  
1.  在「BizTalk 對應工具」的格線頁中，按一下連結以選取連結。  
  
     格線頁中所選連結的端點會反白顯示。  
  
2.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中提供的連結使用 （新） 名稱**標籤**屬性。  
  
### <a name="to-delete-a-link"></a>刪除連結  
  
1.  在「BizTalk 對應工具」的格線頁中，按一下連結以選取連結。  
  
     格線頁中所選連結的端點會反白顯示。  
  
2.  在**編輯**功能表上，按一下 **刪除**。  
  
     您可以也按 DELETE 鍵，或以滑鼠右鍵按一下連結，然後按一下**刪除**快顯功能表。  
  
    > [!NOTE]
    >  您可以大量選取多個連結和 (或) 運算質，然後用一道作業加以刪除。 您可以復原或重做大量刪除連結和 (或) 運算質的動作。 復原和重做作業的詳細資訊，請參閱[如何復原或重做使用者作業](../core/how-to-undo-or-redo-user-operations.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用連結指定記錄和欄位對應](../core/using-links-to-specify-record-and-field-mappings.md)