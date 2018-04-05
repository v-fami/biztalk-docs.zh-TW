---
title: UpdateEx 方法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UpdateEx method
ms.assetid: 2fa9c9cc-fd01-4765-8c31-facac188a19d
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a6a64c6709eb9806612518c551372ba45d1a454
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="updateex-method"></a>UpdateEx 方法
用來更新屬性，根據輸入金鑰參數 (key1、 key2、... ...keyn)。 使用 `UpdateEx` 時，您無法刪除集合中的項目。 有一種個別的方法可協助刪除。 如需詳細資訊，請參閱[DeleteOnly 方法](../core/deleteonly-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
UpdateEx (key1, key2, ... keyn, correctionMode, interactiveMode,  
    properties)  
```  
  
## <a name="parameters"></a>參數  
  
|參數|Description|  
|---------------|-----------------|  
|`key`|一組參數，其必須存在於伺服器資料庫中，不然會發生錯誤。 這些金鑰對應至 Get Keys 集合，如為特定元件介面所定義：|  
|`correctionMode`|一個布林值旗標。 設定為 true 時，允許透過更新欄位值或透過將新項目插入集合，修改具有生效日期項目的元件介面。 特別是允許修改 EFFDT 在目前生效日期之前的項目。 此旗標若未設定為 TRUE，對這些項目所做的任何修改都會導致 PeopleSoft 伺服器傳回錯誤。<br /><br /> `correctionMode` 引數只會對包含生效日期項目的那些元件介面公開。 否則，並不會顯示在引數中。<br /><br /> 您應該避免在生產環境中，將 `correctionMode` 設定為 TRUE。 (這也是 PeopleSoft 提供的建議)。您不應該修改由過去 EFFDT 金鑰判斷為已經發生的事件。 這樣可以建立稽核線索。 `UpdateEx` 中若有 `correctionMode` 旗標，即允許略過此安全機制。 建議的作法是針對要停用的過去事件，在項目中設定一個欄位，然後新增 (而不是刪除) 更新的項目。|  
|`interactiveMode`|用於進行錯誤處理的旗標。<br /><br /> 存取元件介面中的屬性時，BizTalk Adapter for PeopleSoft Enterprise 會使用 PeopleSoft 提供的 API，來讀取和寫入元件介面中的個別欄位，不過不會每次變更都傳播至 PeopleSoft 伺服器。 而是讓 psjoa.jar (BizTalk Adapter for PeopleSoft Enterprise 會與之互動) 封裝所有變更，然後以一個封裝的形式，將變更傳送至伺服器。 如果有任何個別的更新失敗，將會傳回一般錯誤，而不會指出實際錯誤。 在互動模式設為 TRUE 的情況下，每個欄位更新都會個別傳送至伺服器。 雖然這對效能會有相當程度的影響，但卻能在更新失敗時 (例如用以設定欄位的值無效時) 提供具體的錯誤資訊。<br /><br /> `interactiveMode` 可提供最大效能，並提供欄位更新層級的錯誤報告。 若要適當使用此功能，建議您平常進行呼叫時，將 `interactiveMode` 設為 FALSE。 這樣效能應該不會受到影響。 如果傳回錯誤，就會透過將 `interactiveMode` 旗標設定為 TRUE，再次嘗試執行相同的呼叫。 當呼叫失敗時，伺服器會傳回更精確的錯誤訊息。|  
  
### <a name="remarks"></a>備註  
 當您呼叫此函式時，會以輸入參數屬性來取代對應至金鑰的記錄屬性。 含有原始記錄的所有集合都會遭到刪除，並以輸入參數來予以取代。 這些集合的大小不一定要相符，因為 `UpdateEx` 內的程序是要刪除所有現有集合項目，然後插入指定的項目。  
  
 如果元件介面的屬性包含生效日期項目，因為原始清單會被取代，所以屬性參數必須包含所有未來的生效日期項目。 這樣可提供新增和刪除未來生效日期項目的機制，不過，如果屬性也包含過去生效日期項目，就會傳回錯誤，因為您無法修改過去生效日期項目。 如果目前生效日期項目也包含在內，則會被忽略。 這可讓用戶端來呼叫`Get()`與`getHistoryItems`參數設定為 False，修改任何未來生效日期項目或加入新未來生效日期的項目，和傳遞結構做為參數`UpdateEx()`函式。  
  
 如果在只能有一個執行個體存在的情況下，元件介面沒有金鑰，`UpdateEx()` 方法的表單如下：  
  
```  
UpdateEx(correctionMode, interactiveMode, properties)  
```  
  
> [!NOTE]
>  如果已啟用元件介面中的 PeopleSoft `UpdateEx()` 與 `Get` 函式，就會提供 BizTalk Adapter for PeopleSoft Enterprise `Save` 方法。  
  
## <a name="see-also"></a>另請參閱  
 [附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md)