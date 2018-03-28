---
title: 如何開啟、 儲存、 關閉和重新命名對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9aa88ca7-a731-4295-8692-6dd36fdf0872
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9383dd3751f9ccdd7790b0215e596eba95dc4a45
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-open-save-close-and-rename-maps"></a>如何開啟、儲存、關閉和重新命名對應
在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，對應為檔案系統中存在的檔案以.btm 為副檔名。 不過，更常見的狀況是將對應作為 BizTalk 專案中的項目使用，您可以從 BizTalk 專案中執行如開啟、儲存和關閉對應等作業。  
  
### <a name="to-open-a-map"></a>開啟對應  
  
1.  在 [方案總管] 中，選取要開啟的對應。  
  
2.  在 **檢視** ] 功能表上，按一下 [ **開啟**。  
  
     對應就會在 BizTalk 對應工具中開啟。  
  
    > [!NOTE]
    >  您可以也在方案總管 中的對應上按一下滑鼠右鍵，然後按一下 **開啟**, ，或只要按兩下 方案總管 中的對應。  
  
### <a name="to-save-a-map"></a>儲存對應  
  
1.  在 [方案總管] 中，選取要儲存的對應。  
  
2.  在**檔案**功能表上，按一下 * * 儲存 *\<名稱的對應\>* * *。  
  
### <a name="to-save-a-map-to-a-new-location"></a>將對應儲存至新位置  
  
1.  在 [方案總管] 中，選取要儲存至新位置的對應。  
  
2.  在**檔案**功能表上，按一下 **儲存*\<名稱的對應\>*為**。  
  
3.  在 **將檔案另存新檔** 對話方塊中，瀏覽至您想要用來儲存對應的資料夾位置。  
  
4.  在 **檔名** 方塊內輸入檔案的名稱，然後按一下  **儲存**。  
  
    > [!IMPORTANT]
    >  請勿使用下列對應名稱："XmlContent"、"SourceSchemas"、"TargetSchemas" 或 "XsltArgumentListContent"；若使用這些名稱將導致對應的 .NET 組件中產生的 C# 程式碼發生編譯問題。 如需問題和解決方法資訊，請參閱[疑難排解對應](../core/troubleshooting-maps.md)。  
  
### <a name="to-rename-a-map"></a>重新命名對應  
  
1.  在 方案總管中以滑鼠右鍵按一下您想要重新命名，然後按一下 對應 **重新命名**。  
  
2.  在 [方案總管] 中對應所在位置出現的 [編輯] 方塊中，輸入對應的新名稱，或改變它的現有名稱，然後按 ENTER。  
  
> [!NOTE]
>  您也要變更 **型別名稱** 時將它重新命名對應。 您變更 **型別名稱** 選取 **對應** 在 [方案總管] 並輸入新的名稱在 **型別名稱** [屬性] 視窗中。  
  
#### <a name="to-close-a-map"></a>關閉對應  
  
1.  在 [方案總管] 中，選取要關閉的對應。  
  
2.  在 **[檔案]** 功能表上按一下 **[關閉]**。  
  
    > [!NOTE]
    >  您也可以按一下關閉圖示 ([**x**]) 的 Microsoft 右上角[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]編輯視窗。  
  
## <a name="see-also"></a>另請參閱  
 [管理專案中的對應](../core/managing-maps-within-projects.md)