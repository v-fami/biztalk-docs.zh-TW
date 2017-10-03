---
title: "如何建立元件介面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating component interfaces
- component interfaces, creating
ms.assetid: 9def053a-cbf6-4b34-b2e8-b2d03bffc5fe
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86ee68edba66b05d3c2541dd9c41cc074bd790b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-component-interfaces"></a>如何建立元件介面
您可以使用 PeopleSoft 應用程式設計工具建立元件介面。 (如需應用程式設計工具的詳細資訊，請參閱 PeopleSoft Enterprise 文件。)  
  
 您可以在元件檢視中新增記錄內的屬性。 在元件介面中，您可以刪除不想公開的屬性。 按一下屬性，然後再按一下，直到您可以輸入新的名稱，便能重新命名屬性。 如果您重新命名屬性，在元件介面內就只能用新名稱參考它，不能使用基礎元件名稱。  
  
 屬性相鄰的圖示可能各不相同。 例如，EMPLID 的圖示會指出它是基礎記錄內的索引鍵欄位。 NAME 的圖示會指出它是基礎記錄內的其他索引鍵欄位 (如需屬性圖示的完整清單，請參閱 PeopleBooks 文件)。  
  
### <a name="creating-a-new-component-interface"></a>建立新元件介面  
  
1.  開啟 PeopleSoft 應用程式設計工具。  
  
2.  在 [檔案]  功能表上，按一下 [新增] 。  
  
     ![](../core/media/psadapter-42-ps-new-compinterface.gif "PSAdapter_42_PS_New_CompInterface")  
  
3.  在**新增**對話方塊中，選取**元件介面**，然後按一下 **確定**。  
  
     ![](../core/media/psadapter-43-ps-selectsourcecomp.gif "PSAdapter_43_PS_SelectSourceComp")  
  
4.  在**選取元件介面的來源元件**視窗中，選取要做基礎 」 的元件介面，然後按一下 元件**選取**。  
  
     ![](../core/media/psadapter-44-ps-appdesigner1.gif "PSAdapter_44_PS_AppDesigner1")  
  
    > [!NOTE]
    >  若為大型元件介面，請手動公開元件屬性。  
  
5.  在**應用程式設計工具**對話方塊方塊中，選擇下列選項：  
  
    -   按一下**否**建立元件介面，而不會顯示屬性，並手動公開元件屬性。  
  
         a. 從左窗格的相關欄位拖曳至右窗格中。  
  
         b. 若要選取不同的函式來執行，以滑鼠右鍵按一下 靠右或向左窗格中，取決於哪一個窗格為作用中。  
  
         如需功能的完整清單，請參閱 PeopleBooks 文件。  
  
    -   按一下**是**建立元件介面，並顯示基礎元件介面的屬性。  
  
         ![](../core/media/psadapter-45-ps-appdesigner2.gif "PSAdapter_45_PS_AppDesigner2")  
  
## <a name="see-also"></a>另請參閱  
 [元件介面中的標準方法](../core/standard-methods-in-component-interfaces.md)   
 [附錄 c： 使用元件介面](../core/appendix-c-using-component-interfaces.md)   
 [附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md)