---
title: 如何開啟、 儲存、 關閉和重新命名對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9aa88ca7-a731-4295-8692-6dd36fdf0872
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a95ba8e22baa10a0b47721b8a8b3eb3554e2b8a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968759"
---
# <a name="how-to-open-save-close-and-rename-maps"></a>如何開啟、儲存、關閉和重新命名對應
在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以檔案形式存在以.btm 為副檔名的檔案系統中的對應。 不過，更常見的狀況是將對應作為 BizTalk 專案中的項目使用，您可以從 BizTalk 專案中執行如開啟、儲存和關閉對應等作業。  
  
### <a name="to-open-a-map"></a>開啟對應  
  
1.  在 [方案總管] 中，選取要開啟的對應。  
  
2.  在 **檢視**功能表上，按一下**開啟**。  
  
     對應就會在 BizTalk 對應工具中開啟。  
  
    > [!NOTE]
    >  您可以也在 [方案總管] 中，地圖上按一下滑鼠右鍵，然後按一下**開啟**，或直接按兩下 [方案總管] 中的對應。  
  
### <a name="to-save-a-map"></a>儲存對應  
  
1. 在 [方案總管] 中，選取要儲存的對應。  
  
2. 在上**檔案**功能表上，按一下 * * 儲存 *\<命名的對應\>* * *。  
  
### <a name="to-save-a-map-to-a-new-location"></a>將對應儲存至新位置  
  
1.  在 [方案總管] 中，選取要儲存至新位置的對應。  
  
2.  在上**檔案**功能表上，按一下**儲存*\<名稱的對應\>* 為**。  
  
3.  在 [**另存新檔**] 對話方塊中，瀏覽至您想要用來儲存對應的資料夾位置。  
  
4.  在 **檔名**方塊中，輸入檔案的名稱，然後按一下**儲存**。  
  
    > [!IMPORTANT]
    >  請勿使用下列對應名稱："XmlContent"、"SourceSchemas"、"TargetSchemas" 或 "XsltArgumentListContent"；若使用這些名稱將導致對應的 .NET 組件中產生的 C# 程式碼發生編譯問題。 如需問題和解決方法資訊，請參閱[疑難排解對應](../core/troubleshooting-maps.md)。  
  
### <a name="to-rename-a-map"></a>重新命名對應  
  
1.  在 方案總管 中，以滑鼠右鍵按一下您要重新命名，然後按一下 地圖**重新命名**。  
  
2.  在 [方案總管] 中對應所在位置出現的 [編輯] 方塊中，輸入對應的新名稱，或改變它的現有名稱，然後按 ENTER。  
  
> [!NOTE]
>  您也可以變更**型別名稱**時將它重新命名對應。 您變更**型別名稱**藉由選取**地圖**方案總管 中輸入新名稱**型別名稱**屬性 視窗中。  
  
#### <a name="to-close-a-map"></a>關閉對應  
  
1. 在 [方案總管] 中，選取要關閉的對應。  
  
2. 在 **[檔案]** 功能表上按一下 **[關閉]**。  
  
   > [!NOTE]
   >  您也可以按一下關閉圖示 ([**x**]) 中 Microsoft 的右上角[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]編輯視窗。  
  
## <a name="see-also"></a>另請參閱  
 [管理專案中的對應](../core/managing-maps-within-projects.md)