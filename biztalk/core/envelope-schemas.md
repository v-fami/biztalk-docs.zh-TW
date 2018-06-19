---
title: 信封結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af296c30-95dc-4fef-9aa3-bea2f2cd8caf
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9008e77e388a93b1750c9b9ba34679ed519db459
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970604"
---
# <a name="envelope-schemas"></a>信封結構描述

## <a name="overview"></a>概觀
您可以使用和建立商務文件的 XML 結構描述一樣的方式，來建立信封結構描述。 您可以從格式正確的 XML 信封執行個體訊息、「文件類型定義」(DTD) 或信封結構描述的 XML-Data Reduced (XDR) 表示法建立結構描述。 或者，您可以結合或不結合其他結構描述，來建立新的結構描述。 由於信封結構描述通常較大多數商務文件結構描述小且簡單，因此建立新的信封結構描述通常是一種可行的替代方法。  
  
 若要定義為信封結構描述的結構描述，您需要設定**信封**屬性**結構描述**節點的值**是**。 當您定義信封結構描述時，您應該指向信封的**Body XPath**送給父節點僅包含\<任何\>子項目。 為了讓 XML 組合器能夠使用信封，父節點不可包含任何其他項目。  
  
 當您將**信封**屬性**是**，它表示實際訊息內容 （稱為訊息內文） 的 XML 執行個體訊息的某處存在於根**記錄**這個結構描述中所指定的節點**Body XPath**該節點的屬性。 因此，您也必須根據下列各種條件，設定其他的屬性：  
  
-   如果信封結構描述具有單一根節點，您必須設定**Body XPath**該根的屬性。  
  
-   若信封結構描述具有多重根目錄和**根參考**屬性未設定，您必須設定**Body XPath**所有根節點的屬性。  
  
-   若信封結構描述具有多重根目錄和**根參考**屬性時，您必須設定**Body XPath**屬性對應根**記錄**節點。 您可以選擇設定**Body XPath**剩餘根節點的屬性。  
  
-   不論信封結構描述是否有單一根節點或多個根節點，設定 **[根參考**不是必要屬性。  

這些屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="see-also"></a>請參閱  
 [不同類型的 BizTalk 結構描述](../core/different-types-of-biztalk-schemas.md)   
 [如何建立信封的結構描述](../core/how-to-create-schemas-for-envelopes.md)