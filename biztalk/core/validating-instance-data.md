---
title: 驗證執行個體資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19c3ca83-0abf-42ba-8e29-653ff12d5e20
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86cde9d6133959e34ec09880be8a6beca5c37191
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287974"
---
# <a name="validate-instance-data"></a>驗證執行個體資料

## <a name="overview"></a>概觀
在測試對應程序期間，您可能想要針對來源與目的結構描述驗證執行個體資料，以確認執行個體資料符合結構描述的結構。 若要驗證針對來源或目的結構描述的執行個體訊息，以滑鼠右鍵按一下 方案總管 中的結構描述，然後按一下 **驗證執行個體**。  
  
> [!IMPORTANT]
>  若您在輸出中使用自訂資料或常數，則必須確認來源測試資料和目標常數值的資料型別是否有效。 當您驗證對應時，「BizTalk 對應工具」並不會檢查執行個體資料是否違反結構描述所定義的任何資料型別。 在您測試對應或驗證執行個體資料時，已完成此項檢查。  
  
 如需如何產生和驗證執行個體資料使用 BizTalk 編輯器的詳細資訊，請參閱[執行個體訊息產生和驗證](../core/instance-message-generation-and-validation.md)和[執行個體驗證](../core/instance-validation.md)。 執行個體時提供 SQL Server 登入。 **值**結構描述的節點屬性也會影響 BizTalk 產生執行個體資料的方式。 如需詳細資訊，請參閱**結構描述節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="see-also"></a>另請參閱  
-  [執行個體訊息產生和驗證](../core/instance-message-generation-and-validation.md)   
-  [如何驗證在 Visual Studio 中的結構描述](../core/how-to-validate-schemas-in-visual-studio.md)   
-  **對應屬性參考**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  
-  [測試對應](../core/testing-maps.md)