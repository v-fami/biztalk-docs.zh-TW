---
title: "步驟 2： 定義與發佈 Contoso 的詞彙 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vocabularies, creating
- vocabularies, publishing
- private process tutorial, creating vocabularies
ms.assetid: e23880c0-772c-48c6-a6b5-32eb951527c8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15937a1235cc1776be38fe2b0e5529c19d3f6fd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-defining-and-publishing-the-vocabulary-for-contoso"></a>步驟 2： 定義與發佈 Contoso 的詞彙
在此實例中，Contoso 會實作商務原則，以確保即使發生緊急狀況，也一定有足夠的存貨。 您將使用 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 中的「商務規則編輯器」建立商務原則。 在此步驟中，您將建立在定義商務原則時要使用的詞彙。  
  
### <a name="to-add-a-new-vocabulary"></a>加入新詞彙  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **商務規則編輯器 」**。  
  
2.  在 [開啟規則存放區] 對話方塊中，按一下**確定**。  
  
3.  在 事實總管 窗格中，在**詞彙**索引標籤上，以滑鼠右鍵按一下**詞彙**，然後按一下 **新增詞彙**。  
  
4.  將詞彙**3A2PriceAvailabilityVocabulary**，然後按下**Enter**。  
  
### <a name="to-define-a-constant-vocabulary-value"></a>定義常數詞彙值  
  
1.  在 商務規則編輯器 中按一下**3A2PriceAvailabilityVocabulary**，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **新增定義**。  
  
2.  在**詞彙定義精靈**頁面上，選取**常數值、 值的範圍或值的集合**，然後按一下 **下一步**。  
  
3.  在**常數值、 值的範圍或值的集合**頁面上，於**定義名稱**方塊中，輸入**Emergency Quantity Needed**，然後按一下 [**下一步]**.  
  
4.  在**定義常數值**頁面上，於**值**方塊中，輸入**800**，然後按一下 **完成**。  
  
### <a name="to-define-an-xml-document-get-element"></a>定義 XML 文件的 Get 項目  
  
1.  商務規則編輯器 中的事實總管 窗格中，以滑鼠右鍵按一下**版本 1.0 （未儲存）**下**3A2PriceAvailabilityVocabulary**，然後按一下 **新增定義**.  
  
2.  在**VocabularyDefinition 精靈**頁面上，選取**XML 文件項目或屬性**，然後按一下 **下一步**。  
  
3.  在**XML 文件項目或屬性**頁面上，於**定義名稱**方塊中，輸入**Quantity Available**。  
  
4.  按一下**瀏覽**(旁**結構描述**欄位)，移至**ContosoPriceAndAvailability**專案在方案資料夾中，選取**ContosoPriceAndAvailability.xsd**結構描述，然後再按一下**開啟**。  
  
5.  在 [選取繫結] 對話方塊中，依序展開**rootPriceResponse**，依序展開**產品**，選取**NumberAvailable**項目，然後再按一下**確定**.  
  
6.  在**XML 文件項目或屬性**頁面上，於**文件類型**方塊中，確認值為**ContosoPriceAndAvailability.ContosoPriceSchema.rootPriceResponse**.  
  
7.  在**選取作業**區段中，選取**執行 「 取得 」 作業**，然後按一下 **完成**。  
  
### <a name="to-define-an-xml-document-set-element"></a>定義 XML 文件的 Set 項目  
  
1.  商務規則編輯器 中的事實總管 窗格中，以滑鼠右鍵按一下**版本 1.0 （未儲存）**下**3A2PriceAvailabilityVocabulary**，然後按一下 **新增定義**.  
  
2.  在**VocabularyDefinition 精靈**頁面上，選取**XML 文件項目或屬性**，然後按一下 **下一步**。  
  
3.  在**XML 文件項目或屬性**頁面上，於**定義名稱**方塊中，輸入**最後可用量**。  
  
4.  按一下**瀏覽**(旁**結構描述**欄位)，移至**ContosoPriceAndAvailability**專案在方案資料夾中，選取**ContosoPriceAndAvailability.xsd**結構描述，然後再按一下**開啟**。  
  
5.  在**選取繫結**對話方塊方塊中，展開  **rootPriceResponse**，依序展開**產品**，然後選取**NumberAvailable**項目。 按一下 **[確定]**。  
  
6.  在**XML 文件項目或屬性**頁面上，於**文件類型**方塊中，確認值為**ContosoPriceAndAvailability.ContosoPriceSchema.rootPriceResponse**.  
  
7.  在**選取作業**區段中，選取**執行 「 設定 」 作業**，然後按一下 **下一步**。  
  
8.  在**指定顯示名稱**頁面上，按一下**完成**。  
  
### <a name="to-save-and-publish-the-vocabulary"></a>儲存和發佈詞彙  
  
1.  商務規則編輯器 中的事實總管 窗格中，以滑鼠右鍵按一下**版本 1.0 （未儲存）**下**3A2PriceAvailabilityVocabulary**，然後按一下 **儲存**。  
  
2.  以滑鼠右鍵按一下該相同**1.0 版**節點，然後按一下**發行**。  
  
    > [!NOTE]
    >  讓 [商務規則編輯器] 保持開啟，供教學課程中的下個步驟使用。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 定義、 發佈與部署 Contoso 的商務原則](../../adapters-and-accelerators/accelerator-rosettanet/step-3-defining-publishing-and-deploying-the-business-policy-for-contoso.md)