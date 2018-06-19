---
title: 如何儲存、 重新命名，並關閉結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65e15d9e-40ae-4850-9c13-88033cb3b3bb
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a295bacf263e3ecad9a9aa081fb0d5d3be2f635
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "25972364"
---
# <a name="how-to-save-rename-and-close-schemas"></a>如何儲存、重新命名及關閉結構描述
在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，結構描述為 XML 結構描述定義 (XSD) 語言檔案，以 .xsd 副檔名存在檔案系統上。 當您使用「BizTalk 編輯器」開發結構描述時，需要定期儲存和關閉結構描述檔案，偶爾可能需要重新命名這些檔案。 本主題描述執行這些基本作業所需的步驟。  
  
### <a name="to-save-a-schema"></a>儲存結構描述  
  
1.  若有必要，在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中主要編輯視窗的頂端按一下適當的索引標籤，為您要儲存的結構描述啟動「BizTalk 編輯器」。  
  
2.  在**檔案**功能表上，按一下 * * 儲存 *\<名稱的結構描述\>* * *。  
  
     若結構描述之前有未儲存的變更，則其顯示在主要編輯視窗頂端索引標籤中的名稱結尾將不再有星號 (*) 以指示未儲存的變更。  
  
> [!NOTE]
>  您可以按一下以儲存新的名稱下的結構描述**儲存*\<名稱的結構描述\>* 為**上**檔案**功能表。  
  
> [!NOTE]
>  您可以儲存結構描述做為一部分的所有變更的項目儲存在專案中，依序按一下 **全部儲存** 上 **檔案** 功能表。  
  
#### <a name="to-rename-a-schema"></a>重新命名結構描述  
  
1.  在 方案總管中以滑鼠右鍵按一下您想要重新命名，然後按一下 結構描述 **重新命名**。  
  
2.  在 [方案總管] 中結構描述所在位置出現的 [編輯] 方塊中，輸入結構描述的新名稱，或改變它的現有名稱，然後按 ENTER。  
  
> [!NOTE]
>  您也要變更 **型別名稱** 當您重新命名的結構描述。 您變更 **型別名稱** 選取 **結構描述** 在 [方案總管] 並輸入新的名稱在 **型別名稱** [屬性] 視窗中。  
  
> [!IMPORTANT]
>  您不能重新命名任何一個已經用於其他結構描述的結構描述。 這包括已經被其他結構描述包含、匯入或重新定義的結構描述，以及已經為其建立升級的屬性結構描述。 若這麼做，所使用的結構描述將找不到重新命名的結構描述，因為它所包含的名稱已經不正確。  
  
> [!NOTE]
>  專案成員檔案 (如結構描述檔案) 的特定名稱選擇可能由於與 C# 保留字以及 .NET Framework 類型和命名空間名稱 (如 "System") 發生衝突，之後會導致編譯錯誤。 結構描述的範例包括 schema.xsd、XmlContent 及 RootNodes。 這是因為 **型別名稱** 屬性預設為基底 （不含副檔名） 部分的 **Filename** 屬性。 您可以明確的值變更解決這種類型的編譯錯誤 **型別名稱** 為不衝突的屬性。  
  
#### <a name="to-close-a-schema"></a>關閉結構描述  
  
1.  若有必要，在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中主要編輯視窗的頂端按一下適當的索引標籤，為您要關閉的結構描述啟動「BizTalk 編輯器」。  
  
2.  在 **[檔案]** 功能表上按一下 **[關閉]**。  
  
     會關閉已經關閉的結構描述之「BizTalk 編輯器」。  
  
## <a name="see-also"></a>另請參閱  
 [管理專案中的結構描述](../core/managing-schemas-within-projects.md)