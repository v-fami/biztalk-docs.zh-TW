---
title: 建立連結 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps, links
- BizTalk Mapper, links
ms.assetid: e8596c50-62e9-40a7-ad61-29cbdb4f4fc9
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87570b82dc63a02c629e0fc024c2e44d57df1401
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238566"
---
# <a name="creating-links"></a>建立連結
BizTalk 對應工具可協助您自動化連結建立作業的部分項目。 簡單連結建立作業與簡單資料型別相似。 更加複雜的連結建立作業形式則比較類似程式設計語言中的結構指派。 例如，指定如何從輸入執行個體訊息將資料的多個項目移至對應的輸出執行個體訊息的單一連結建立作業。  
  
 使用下列方法建立連結：  
  
-   **簡單連結建立作業。** 在簡單連結建立作業中，可藉由拖曳以產生連結。 將來源結構描述中的欄位拖曳至目的結構描述中的欄位，可在輸出執行個體訊息中建立項目或屬性，並將項目或屬性的值插入訊息中。 這類連結可以之間直接建立**記錄**和**欄位**來源和目的地結構描述中的節點或它們可以包含一或多個運算質之間的連結路徑中**記錄**和**欄位**來源和目的地結構描述的節點。  
  
-   **結構連結。** 在建立結構連結時，您必須產生多個簡單連結之間同時**記錄**和**欄位**中擁有相同相對結構的來源和目的地結構描述的節點。 若要使用結構連結，則兩個結構描述相對部分的結構必須相同。 如需有關設定結構連結的詳細資訊，請參閱[如何自動連結記錄](../core/how-to-link-records-automatically.md)。  
  
-   **名稱相符連結。** 當您使用這個方法時，在相同的時間之間建立多個簡單連結**記錄**和**欄位**的名稱為基礎的來源和目的地結構描述中的節點**記錄**和**欄位**節點。 若要使用名稱相符連結，則來源與目的結構描述的結構必須非常相似，但並非完全相同。 如需設定名稱比對連結的詳細資訊，請參閱[如何自動連結記錄](../core/how-to-link-records-automatically.md)。  
  
    > [!NOTE]
    >  您也可以查看[如何管理現有連結](../core/how-to-manage-existing-links.md)如需有關如何變更/修改現有的連結資訊。  
  
## <a name="preserving-whitespace-in-a-link"></a>保留連結中的空白字元  
 如果您想要在對應至目標項目或運算質時保留來源項目中的空白字元，則需要撰寫自訂指令碼。  
  
 在對應工具或是執行階段系統中，不會保留空白字元。 對應工具與執行階段系統都使用 BTSXslTransform.Transform 來處理大量訊息的轉換，並透過 XPath 資料模型以便依賴 XmlReader 來瀏覽。  
  
 如需保留空白字元，您可以撰寫一份自訂指令碼來傳回所需的空白字元數。 例如，下列程式碼會永遠傳回一個包含 5 個空白字元的字串：  
  
```  
public string Whitespace(string param1)  
{  
  return "     ";  
}  
```  
  
 如果您連結的來源項目到此指令碼和目標元素的輸入做為輸出，執行對應時，輸出項目會包含 5 個空白字元。  
  
> [!NOTE]
>  如果您檢視輸出使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，項目會出現空白。 這是因為 XML 檢視器會將僅包含空白字元的項目視為空白。 若要查看空白字元，以滑鼠右鍵按一下 XML 檢視，然後選取**檢視原始檔**。  
  
## <a name="see-also"></a>另請參閱  
 [如何編輯連結屬性](../core/how-to-edit-link-properties.md)