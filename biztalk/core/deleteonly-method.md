---
title: "DeleteOnly 方法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DeleteOnly method
ms.assetid: 99e1d7af-1450-439b-882f-de677e593bee
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3982c67b4c2eb572a57a4ad602b1d302f9b53ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deleteonly-method"></a>DeleteOnly 方法
可讓您刪除集合中的項目。  
  
## <a name="syntax"></a>語法  
  
```  
DeleteOnly(key1, key2, ..., keyn, correctionMode, interactiveMode,  
    properties)  
```  
  
## <a name="parameters"></a>參數  
  
|參數|Description|  
|---------------|-----------------|  
|`key`|是一組必須提供的參數。 這組索引鍵必須存在於伺服器資料庫中，否則會發生錯誤。 這些金鑰對應至 Get Keys 集合，如為特定元件介面所定義：|  
|`correctionMode`|一個布林值旗標。 若 設定為 True，則允許刪除集合中帶有過去有效日期的項目 。 特別是，允許刪除其 EFFDT 在目前有效日期前的項目。 此旗標若未設定為 TRUE，對這些項目所做的任何修改都會導致 PeopleSoft 伺服器傳回錯誤。 **注意：** `correctionMode`引數只公開包含生效日期項目的那些元件介面。 否則，該引數不會顯示為引數的一部分。|  
|`interactiveMode`|用於錯誤處理。<br /><br /> 在存取元件介面中的屬性時，BizTalk Adapter for PeopleSoft Enterprise 會使用 PeopleSoft 提供的 API，這些 API 會讀取及寫入元件介面中的個別欄位；但這些變更並不會逐一傳播至 PeopleSoft 伺服器。 psjoa.jar (BizTalk Adapter for PeopleSoft Enterprise 的互動對象) 會先封裝所有變更，再以這個單一封裝將變更傳送至伺服器。 如果有任何個別的更新失敗，將會傳回一般錯誤，而不會指出實際錯誤。 在互動模式設為 TRUE 的情況下，每個欄位更新都會個別傳送至伺服器。 雖然這對效能會有相當程度的影響，但卻能在更新失敗時 (例如用以設定欄位的值無效時) 提供具體的錯誤資訊。<br /><br /> `interactiveMode` 參數可提供最大效能，並可提供欄位更新層級的錯誤報告。 若要適當使用此功能，建議您平常進行呼叫時，將 `interactiveMode` 設為 FALSE。 這樣效能應該不會受到影響。 如果傳回錯誤，您可以將 interactiveMode 旗標設為 TRUE，再重試相同的呼叫。 當呼叫失敗時，伺服器會傳回更精確的錯誤訊息。|  
|`properties`|包含伺服器上現有結構的子集。 所有 分葉項目都會被刪除 。|  
  
## <a name="remarks"></a>備註  
 屬性具有與此元件介面的 `CreateEx` 或 `UpdateEx` 方法相同的資料型別，但是，只有索引鍵值比較重要。 會忽略 非索引鍵值 。 這些 索引鍵值必須符合伺服器上的索引鍵值，否則會引發例外狀況 。  
  
 以下示範索引鍵值的使用方式。 如果集合包含下列項目：  
  
-   item0  
  
-   item1  
  
-   item2  
  
-   item3  
  
 您可以在屬性中提供 item1 和 item3 的索引鍵，以刪除 item1 和 item3。  
  
-   item1  
  
-   item3  
  
 呼叫之後，伺服器在集合中就會剩下下列項目：  
  
-   item0  
  
-   item2  
  
 第二個範例顯示底下包含其他集合的項目：  
  
-   item0  
  
    -   item0a  
  
-   item1  
  
    -   item1a  
  
    -   item1b  
  
    -   item1c  
  
-   item2  
  
    -   item2a  
  
    -   item2b  
  
 您可以提供 item1b 和 item2 的索引鍵，以刪除 item1b 與全部的 item2。  
  
-   item1  
  
    -   item1b  
  
-   item2  
  
 為 item2 提供空白子集合，會將 item2 變成分葉，而使整個子分支都遭到刪除。 呼叫之後，伺服器中會剩下下列項目：  
  
-   item0  
  
    -   item0a  
  
-   item1  
  
    -   item1a  
  
    -   item1c  
  
## <a name="see-also"></a>另請參閱  
 [附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md)