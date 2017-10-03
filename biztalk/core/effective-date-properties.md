---
title: "Effective Date 屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- effective-dated items
- getHistoryItems parameter
- Effective Date
- EFFDT
- planned items, scheduling and tracking
ms.assetid: 0d9a153c-7ea5-41cf-9e4e-055e1c18f64b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34f1c4cf3579a3381c846ddbb9896b2e5be26f6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="effective-date-properties"></a>Effective Date 屬性
PeopleSoft Enterprise 藉由名為 Effective Date (縮寫為 EFFDT) 的特殊屬性，讓您排定與追蹤計畫項目。 這類項目可能已生效或是單純為計畫階段，端賴其日期比 PeopleSoft 目前日期早還是晚。  
  
 如果元件介面的屬性包含這類帶有生效日期 (亦即，欄位名稱為 EFFDT) 的項目，配接器會讓呼叫者能夠擷取整組值，或是僅擷取尚未生效 (而仍能變更) 的值。  
  
## <a name="gethistoryitems-parameter"></a>getHistoryItems 參數  
 如果元件介面具有帶有生效日期的屬性，配接器會提供名為 `getHistoryItems` 的額外參數給 Get 運算。 此參數為布林值類型，而且一旦設為 True，就會傳回所有帶有生效日期的項目。 這些項目包括所有帶有過去、現在與未來生效日期的項目。  
  
 如果將 `getHistoryItems` 參數設為 False，則只會傳回帶有現在與未來生效日期的項目。 如果您打算新增或變更這些項目 (因為過去項目已無法變更)，請選擇 False。  
  
 多個帶有生效日期的項目，其生效日期可能有相同的時候。 碰到這種情況時，則必須同時提供額外的 Effective Sequence (EFFSEQ) 屬性。 EFFSEQ 的值必須是唯一的，以便和帶有相同生效日期的項目有所區隔。 如需詳細資訊，請參閱 PeopleSoft 文件。  
  
## <a name="modifying-past-effective-dated-items"></a>修改帶有過去生效日期的項目  
 `correctionMode`引數中同時[UpdateEx](../core/updateex-method.md)和[DeleteOnly](../core/deleteonly-method.md)方法可讓您控制是否可以修改過去生效日期項目。 如果設為 true，則所有項目都可以修改。 否則，修改帶有生效日期的過去項目會產生例外狀況。  
  
 在元件介面上呼叫 `Update` 方法 (此方法已不再使用)，而該元件介面具有帶有生效日期的項目時，請務必注意您所加入的生效日期值不得比 PeopleSoft 目前的生效日期還早，否則呼叫會失敗並傳回例外狀況。 不過，您可以加入帶有目前生效日期的項目，這是因為設定屬性時會略過這類項目。 如果 Effective Sequence 屬性存在，則設定屬性期間會略過伺服器中所有具有相符 Effective Sequences 的帶有目前生效日期的項目。  
  
## <a name="see-also"></a>另請參閱  
 [附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md)