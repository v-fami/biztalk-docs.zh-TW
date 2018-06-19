---
title: CreateEx 方法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CreateEx method
ms.assetid: b62bbe25-b24d-42a7-a44c-c83521a6f0a6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b163bfbe7811c37208297aa0a61bfe91cabacde4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238286"
---
# <a name="createex-method"></a>CreateEx 方法
建立新的記錄，使用一組的唯一索引鍵和指定的內容。  
  
## <a name="syntax"></a>語法  
  
```  
CreateEx  
(key1, key2, ..., keyn, interactiveMode, properties)  
```  
  
## <a name="parameters"></a>參數  
  
|參數|Description|  
|---------------|-----------------|  
|`Key in/out parameter`|個別索引鍵參數 (key1、key2、...keyn)，這些是必須提供的參數。<br /><br /> 這組索引鍵不得存在於伺服器資料庫中，也就是說，它們必須是唯一的。<br /><br /> 這些索引鍵對應於針對特定元件介面所定義的 CreateEx 索引鍵集。|  
|`interactiveMode`|處理時發生錯誤。<br /><br /> 在存取元件介面中的屬性時，Microsoft BizTalk Adapter for PeopleSoft Enterprise 會使用 PeopleSoft 提供的 API，這些 API 會讀取及寫入元件介面中的個別欄位；但這些變更並不會逐一傳播至 PeopleSoft 伺服器。 psjoa.jar (BizTalk Adapter for PeopleSoft Enterprise 的互動對象) 會先封裝所有變更，再以這個單一封裝將變更傳送至伺服器。<br /><br /> 如果有任何個別的更新失敗，將會傳回一般錯誤，而不會指出實際錯誤。 在互動模式設為 TRUE 的情況下，每個欄位更新都會個別傳送至伺服器。 雖然這對效能會有相當程度的影響，但卻能在更新失敗時 (例如用以設定欄位的值無效時) 提供具體的錯誤資訊。<br /><br /> interactiveMode 可提供最大效能，並可提供欄位更新層級的錯誤報告。 若要適當使用此功能，建議您平常進行呼叫時，將 interactiveMode 設為 FALSE。 這樣效能應該不會受到影響。 如果傳回錯誤，您可以將 interactiveMode 旗標設為 TRUE，再重試相同的呼叫。 當呼叫失敗時，伺服器會傳回更精確的錯誤訊息。|  
|`properties`|結構，包含元件介面的所有屬性。 呼叫 `CreateEx` 方法時，這些屬性即會插入到以指定索引鍵建立的記錄中。|  
  
## <a name="remarks"></a>備註  
 在某些情況下，呼叫 `CreateEx()` 時不使用明確的索引鍵集是很常見的做法，但 `CreateEx` 函式會傳回索引鍵。 在伺服器上觸發的 PeopleCode 支援這種行為。 例如，在建立訂單時，客戶可能不知道下一個可用的訂單編號為何。 指定 NEXT 做為訂單編號索引鍵，呼叫即會觸發 PeopleCode 來決定下一個可用的訂單編號。 這項資訊必須以 in/out 索引鍵參數傳回給呼叫端客戶。  
  
> [!NOTE]
>  若要讓此機制順利運作，索引鍵也必須是層級 0 的屬性。 否則將會傳回原始索引鍵。  
  
 如果在元件介面中啟用了 PeopleSoft Create 與 Save 函式，則會提供 BizTalk Adapter for PeopleSoft Enterprise `CreateEx()` 方法。  
  
## <a name="see-also"></a>另請參閱  
 [附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md)