---
title: 如何產生執行個體訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff74c67a-7e73-4153-9ec4-e6e50464ee92
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a911e4b0f1167e8ec200dad65b8dacb94bb08be3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254398"
---
# <a name="how-to-generate-instance-messages"></a>如何產生執行個體訊息
在您已經建構結構描述之後，可以利用從結構描述產生範例執行個體訊息的方法來檢查您的工作。 在許多方面，查看執行個體訊息會比查看結構描述樹狀結構，或是結構描述的 XML 結構描述定義 (XSD) 語言表示法更為直接。 這是因為結構描述需要描述對應的執行個體訊息的所有可能變化，而且特定的執行個體訊息只需要使用結構描述指定的格式即可傳遞某些資料。 產生的執行個體訊息只是範例，可能無法顯示由對應的結構描述定義的所有結構。  
  
### <a name="to-explicitly-specify-a-file-to-contain-the-generated-instance-message"></a>明確指定檔案包含產生的執行個體訊息  
  
1.  在 方案總管 中，以滑鼠右鍵按一下您要產生執行個體訊息，然後按一下 結構的描述**屬性**。  
  
2.  如有必要，在 [屬性] 視窗中，依序展開**一般**區段**一般**索引標籤上，按一下其加號 （+） 圖示。  
  
3.  在**輸出執行個體檔案名稱**屬性值欄位中，輸入檔案名稱或使用省略符號 (**...**) 按鈕來瀏覽其產生的執行個體訊息檔案放置，然後按一下 [值] 欄位右端**儲存**。  
  
### <a name="to-specify-the-type-of-the-generated-instance-message"></a>指定產生的執行個體訊息類型  
  
1.  在 方案總管 中，以滑鼠右鍵按一下您要產生執行個體訊息，然後按一下 結構的描述**屬性**。  
  
2.  如有必要，在 [屬性] 視窗中，依序展開**一般**區段**一般**索引標籤上，按一下其加號 （+） 圖示。  
  
3.  在**產生執行個體輸出類型**屬性值欄位中，使用下拉式清單來選取  **XML**或**原生**為產生的執行個體訊息的型別。  
  
     **XML**是預設值。  
  
### <a name="to-generate-a-sample-instance-message-for-a-schema"></a>產生結構描述的範例執行個體訊息  
  
1.  在 方案總管 中，以滑鼠右鍵按一下您要產生執行個體訊息，然後按一下 結構的描述**產生執行個體**。  
  
2.  在 [輸出] 視窗中檢視結果。 成功和錯誤訊息會顯示在此視窗中。  
  
> [!NOTE]
>  若 [輸出] 視窗和/或 [工作清單] 視窗尚未開啟和顯示執行個體產生成功或失敗的資訊，您可以手動開啟它們。 如需有關管理這些視窗的詳細資訊，請參閱[管理其他 Visual Studio 視窗](../core/how-to-manage-other-visual-studio-windows.md)。  
  
> [!NOTE]
>  如果您未指定的值**根參考**屬性，BizTalk 編輯器產生結構描述中的第一個根節點的範例執行個體訊息。 如果您指定的值**根參考**屬性，BizTalk 編輯器會產生範例執行個體訊息的根。  
  
> [!NOTE]
>  在某些情況下，從特定結構描述產生的執行個體訊息，可能無法通過依據該相同結構描述進行的驗證。 如需這種情況下的詳細資訊，請參閱[已知問題與結構描述產生和驗證](../core/known-issues-with-schema-generation-and-validation.md)。 一般而言，您會想要編輯產生的執行個體訊息並變更它所包含的資料，如此它就可以更真實地代表您的實例。 然後再使用此變更過的執行個體訊息來驗證您的結構描述。  
  
## <a name="see-also"></a>另請參閱  
 [測試結構描述](../core/testing-schemas.md)   
 [結構描述驗證](../core/schema-validation1.md)   
 [執行個體訊息產生和驗證](../core/instance-message-generation-and-validation.md)