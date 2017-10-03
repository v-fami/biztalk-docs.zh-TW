---
title: "步驟 3： 定義、 發佈與部署 Contoso 的商務原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, deploying
- policies, publishing
- private process tutorial, creating policies
- policies, creating
ms.assetid: 529b16d8-226b-4046-a95d-64162ebd59a3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cbdd1133145aada8b1a1abf0ccdde25547b7fed3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-defining-publishing-and-deploying-the-business-policy-for-contoso"></a>步驟 3： 定義、 發佈與部署 Contoso 的商務原則
在此步驟中，您將建立可保留每個產品一定單位數量的商務原則，讓 Contoso 製造商可以在緊急時使用這些存貨。  
  
### <a name="to-add-a-new-policy"></a>新增原則  
  
1.  在商務規則編輯器] 中 [原則總管] 窗格中，以滑鼠右鍵按一下**原則**，然後按一下 [**新增原則**。  
  
2.  將新原則**3A2PriceAvailabilityPolicy**，然後按下**Enter**。  
  
### <a name="to-add-a-policy-rule-to-enforce-the-emergency-quantity-needs"></a>新增原則規則以強制執行緊急數量需求  
  
1.  以滑鼠右鍵按一下**版本 1.0 （未儲存）**下**3A2PriceAvailabilityPolicy**，然後按一下 **新增規則**。  
  
2.  命名規則**Emergency Supply Rule-Quantity Exhausted**，然後按下**Enter**。  
  
3.  在右窗格中，「 商務規則編輯器 」 中以滑鼠右鍵按一下**條件**下 IF] 窗格中，指向**述詞**，然後按一下 [**小於等於**述詞。  
  
4.  在 [事實總管] 窗格中，依序展開**詞彙**，依序展開**3A2PriceAvailabilityVocabulary**，依序展開**1.0 版-已發佈**，選取**數量可用**，並將它拖曳至`argument1`編輯器介面上的預留位置。  
  
5.  重複步驟 4 拖曳**Emergency Quantity Needed**到`argument2`預留位置。  
  
6.  選取**最後可用量**，然後將它拖曳至拖曳**動作**THEN 窗格中。  
  
### <a name="to-add-a-policy-to-revise-the-number-available-field-in-the-response"></a>新增原則以修訂回應中的可用數目欄位  
  
1.  以滑鼠右鍵按一下**版本 1.0 （未儲存）**下**3A2PriceAvailabilityPolicy**，然後按一下 **新增規則**。  
  
2.  將新的規則**Emergency Supply Rule-Quantity Available**，然後按下**Enter**。  
  
3.  在右窗格中，「 商務規則編輯器 」 中以滑鼠右鍵按一下**條件**下 IF] 窗格中，指向**述詞**，然後按一下 [**大於**述詞。  
  
4.  在 [事實總管] 窗格中，依序展開**詞彙**，依序展開**3A2PriceAvailabilityVocabulary**，依序展開**1.0 版-已發佈**，選取**數量可用**，然後將它拖曳至拖曳`argument1`編輯器介面上的預留位置。  
  
5.  重複相同的步驟，藉由拖曳**Emergency Quantity Needed**到`argument2`預留位置。  
  
6.  選取**最後可用量**，然後將它拖曳至拖曳**動作**THEN 窗格中。  
  
7.  在 事實總管 窗格中，依序展開**1.0 版-已發佈**下**函式**，並拖曳`Subtract`函式到**0**旁的引數**最後可用量**THEN 窗格中。  
  
8.  拖曳**Quantity Available** (下**3A2PriceAvailabilityVocabulary**) 並將它放在`value1`THEN 窗格中的預留位置。  
  
9. 拖曳**Emergency Quantity Needed**，並將它放在`value2`THEN 窗格中的預留位置。  
  
### <a name="to-save-publish-and-deploy-the-business-policy"></a>若要儲存、發佈和部署商務原則  
  
1.  在 原則總管 窗格中，以滑鼠右鍵按一下**版本 1.0 （未儲存）**下**3A2PriceAvailabilityPolicy**，然後按一下 **儲存**。  
  
2.  以滑鼠右鍵按一下相同節點，然後**發行**。  
  
3.  以滑鼠右鍵按一下相同節點，然後**部署**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 4： 建立 HeaderHelper 專案](../../adapters-and-accelerators/accelerator-rosettanet/step-4-creating-the-headerhelper-project.md)