---
title: "Get 方法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Get method
ms.assetid: 0e621077-f0ef-495c-ba6b-0c6154f48113
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d56b060cc261f707a4aa7b0d6a496a62707c4dca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="get-method"></a>Get 方法
用來擷取屬性，根據輸入金鑰參數 (key1、 key2、... ...keyn)。 輸出參數是一個結構，裡面包含符合索引鍵參數之記錄的屬性。 如果元件介面只有一個執行個體 （也就是沒有任何索引鍵），Get 函式不包含任何索引鍵參數。 另請參閱[Find 方法](../core/find-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
Get (key1, key2, ... keyn, properties)  
Get (key1, key2, ... keyn, getHistoryItems, properties)  
```  
  
## <a name="parameters"></a>參數  
  
|參數|Description|  
|---------------|-----------------|  
|`key`|一組必須存在於伺服器資料庫中的參數；若不存在這些參數，將會出現錯誤。 這些索引鍵對應至針對特定元件介面所定義的一組 Get 索引鍵。|  
|`properties`|內含完整的元件介面屬性結構，完成呼叫時即會傳回這個結構。|  
|`getHistoryItems`|布林值。 如果元件介面的屬性包含層級低於 0 且帶有生效日期 (亦即，索引鍵欄位名稱為 EFFDT) 的項目，則需要額外的 `getHistoryItems` 參數。<br /><br /> 如果值為：<br /><br /> -為 true，所有的生效日期項目會傳回做為序列 （它可以在任何層級內嵌）。 這些項目包括所有帶有過去、現在與未來生效日期的項目<br />-False，會傳回的目前和所有未來生效日期項目。 如果以後會在同一個執行個體上進行更新呼叫，則 `getHistoryItems` 應設為 False。|  
  
### <a name="remarks"></a>備註  
 如果元件介面的屬性包含層級低於 0 且帶有生效日期 (亦即，索引鍵欄位名稱為 EFFDT) 的項目，則需要額外的 `getHistoryItems` 參數。 此參數類型為布林值， 而且一旦設為 True，即會傳回所有帶有生效日期的項目的序列 (可以以任何層級內嵌)。 這些項目包括所有帶有過去、現在與未來生效日期的項目。 如果將 `getHistoryItems` 參數設為 False，則只會傳回所有帶有現在與未來生效日期的項目。 如果以後會在同一個執行個體上進行更新呼叫，則 `getHistoryItems` 應設為 False。 另請參閱[UpdateEx 方法](../core/updateex-method.md)。  
  
 如果元件介面沒有索引鍵 (就像只可存在一個執行個體一樣)，則 `Get()` 方法的形式如下：  
  
```  
Get(properties)  
```  
  
 如需帶有生效日期之項目的詳細資訊，請參閱 PeopleSoft Enterprise 文件。  
  
> [!NOTE]
>  只有在元件介面中有啟用 PeopleSoft `Get()` 函式時，才會提供 BizTalk Adapter for PeopleSoft Enterprise `Get` 方法。  
  
## <a name="see-also"></a>另請參閱  
 [附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md)