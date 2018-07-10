---
title: 如何新增判斷提示運算質至對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccdd79a2-b70f-489b-8711-e00a50d8e2d8
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4cfeabbbeac860e927854fb79c90d2b1608b9c3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015271"
---
# <a name="how-to-add-assert-functoids-to-a-map"></a>如何新增判斷提示運算質至對應
**Assert**運算質可讓您測試對應中條件的相關假設。 例如，如果您執行一些計算來確定產品採購的額外折扣，您可能會判斷提示額外的折扣，是使用邏輯運算質不能超過 100 美元 (**Greater Than**或**Less Than**)。  

> [!NOTE]
>  **Assert**運算質只會引發開發組建中或當**產生偵錯資訊**專案組建設定中的屬性設定為**True**。 當編譯 BizTalk 應用程式以供部署及**產生偵錯資訊**屬性設定為**False** （預設值），判斷提示都會被忽略。  

 如需概念性資訊**Assert**運算質，請參閱[判斷提示運算質](../core/assert-functoid.md)。  

## <a name="add-the-assert-functoid-to-a-map-and-configure-it"></a>新增判斷提示運算質至對應並加以設定  

1. 具有[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)][工具箱]，按一下 [**進階運算質**来選取該運算質類別索引標籤。 顯示所選類別中的進階運算質清單。  

2. 拖曳**Assert**運算質 (![判斷提示運算質](../core/media/advanced-assert-functoid.gif "advanced_assert_functoid")) 從工具箱拖曳至格線頁上的適當位置。  

   > [!NOTE]
   >  運算質將放置在顯示的格線頁上。 若要將運算質放在其他格線頁上，必須先顯示該格線頁。 
   >    
   >  若您要建構使用一個以上運算質的對應，您必須考慮其左右相對位置。 運算質是由左至右執行。 某個運算質的輸出，只能是其較右邊另一個運算質的輸入。  

3. 此運算質必須有正好三個輸入參數，而且會產生一個輸出參數。 若要建立的第一個參數**Assert**運算質建立輸入的連結，方法是將輸出拖曳某個其他**邏輯**運算質或從輸入執行個體訊息中的變數布林值欄位。  

4. 若要建立的第二個輸入的參數**Assert**運算質，來源結構描述中的欄位節點建立輸入的連結**Assert**運算質，或是插入常數。  

5. 若要建立的第三個輸入的參數**Assert**運算質，來源結構描述中的欄位節點建立輸入的連結**Assert**運算質，或是插入常數。  

6. 若要使用的輸出參數**Assert**運算質，建立輸出連結，藉由拖曳**Assert** 」 運算質至目的結構描述中的欄位。  

   > [!NOTE]
   >  與其他運算質的輸出一樣**Assert**運算質可用來當做另一個運算質的輸入。  

## <a name="see-also"></a>另請參閱  
- **判斷提示運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]   
- [將進階運算質新增至對應](../core/adding-advanced-functoids-to-a-map.md)
