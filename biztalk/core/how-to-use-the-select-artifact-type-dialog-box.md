---
title: "如何使用選取成品類型對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Select Artifact Type dialog box
- artifacts, Select Artifact Type dialog box
- Orchestration Designer, items
ms.assetid: f0f767f1-4130-4ff0-a898-a089343ee71f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3027971059d99a921bd743ff28aca1617c5d628d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-select-artifact-type-dialog-box"></a>如何使用選取成品類型對話方塊
*項目*用來設定協調流程設計師 」 的協調流程的項目。 項目 (Item) 的範例包括結構描述、對應、管線、連接埠類型以及多部分訊息類型等。 在開發協調流程及其組成部分 (例如，連接埠圖形、轉換圖形和訊息) 時，所需參考的項目可能不在目前的協調流程中，但在目前的專案或在其他已編譯入 BizTalk Server 組件的其他專案中。 您使用**選取成品類型**對話方塊，即可尋找並設定協調流程內的項目時，然後指定項目。  
  
 **選取成品類型** 對話方塊可從許多協調流程設計師中的位置。 您可以選取\<從參考組件選取 > 下拉式清單中，會顯示組態選項，按一下此文字會開啟**選取成品類型** 對話方塊。  
  
 在選取項目 (Item) 之前，必須先選取想要設定的項目 (Element)。  
  
 您可以使用**選取成品類型**用於下列特定用途的對話方塊：  
  
|動作|目的|  
|------------|-------------|  
|選取管線|在設定直接 (早期) 繫結的連接埠時，選取管線屬性的管線。|  
|選取對應|選取要用於對應**轉換**圖形。|  
|選取結構描述|在建立多部分訊息類型時選取專案中的結構描述。|  
|選取連接埠類型|在建立連接埠時參考現有的連接埠類型。|  
|選取多部分訊息類型|在建立訊息時參考現有的多部分類型。|  
|選取 .NET 類型|在建立變數或訊息時參考現有的 .NET 類型。|  
  
 **參考窗格**  
  
 參考窗格**選取成品類型**對話方塊會顯示參考目前專案中，以及其他可用的組件中。 若要選取此窗格中的參考，請在該參考上按一下。 若要展開此窗格中的容器 (例如**組件**容器)，按一下旁邊的加號 （+）。  
  
 **項目 窗格**  
  
 項目窗格**選取成品類型**對話方塊會顯示目前在 [參考] 窗格中選取參考中包含的項目。 項目 窗格有兩個資料行，**項目**和**限定名稱**，其中顯示目前參考中的項目的相關資訊。  
  
### <a name="to-use-the-select-artifact-type-dialog-box"></a>使用選取成品類型對話方塊  
  
1.  展開**參考**的左窗格中的節點。 此窗格會顯示可用的專案和組件。  
  
2.  展開**組件**節點。 將列出一或多個組件，例如 SYSTEM.DLL 和 MICROSOFT.BIZTALK.PIPELINES.DLL。  
  
3.  按一下組件。 如果組件包含項目，則這些項目會顯示在右窗格中。 項目的完整格式名稱會顯示在右窗格的右方欄位中。  
  
    > [!NOTE]
    >  如果目前的專案含有項目，可以按一下該專案來檢視其項目並進行選擇。  
  
4.  在右窗格中選取的項目，按一下它，然後按一下 [**確定**結束**選取成品類型**] 對話方塊。 這會將該項目 (Item) 指定為已選取項目 (Element) 的類型。 若要關閉**選取成品類型**對話方塊，而不選取，然後指派一個項目，按一下**取消**。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程圖形](../core/orchestration-shapes.md)   
 [如何新增圖形至協調流程](../core/how-to-add-shapes-to-orchestrations.md)   
 [如何新增參數至協調流程](../core/how-to-add-parameters-to-orchestrations.md)