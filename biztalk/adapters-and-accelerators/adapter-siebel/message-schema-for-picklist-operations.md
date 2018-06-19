---
title: 挑選清單作業的訊息結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- picklist operations, message schemas for
- picklist operations, message actions
- picklist operations, message
ms.assetid: c0b62a8c-5a68-47ea-8676-1580601b5ec9
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d72a16e99e38649a6fb8d74178d2b5da1d059dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22221902"
---
# <a name="message-schema-for-picklist-operations"></a>挑選清單作業的訊息結構描述
挑選清單是在商務元件中的特殊欄位型別。 它們代表使用者可以從中挑選指派的單一值的值的集合。 挑選清單都是不同類型。 如需挑選清單和其類型的詳細資訊，請參閱 Siebel 文件。  
  
 挑選清單型別，這是靜態繫結的挑選清單，其中顯示的配接器所列舉的挑選清單為設計階段配接器所產生的中繼資料中的類型。 這包含一組靜態的挑選清單型別必須在執行階段指定的值。  靜態繫結的挑選清單的指定值，同時您一定要指定屬於集的值。  
  
 下列範例將示範靜態繫結的挑選清單類型的結構描述：  
  
```  
<element name="[FIELD_NAME]RequiredPickListType" nillable="true" type="ns1:[FIELD_NAME]RequiredPickListType" />  
<simpleType name="[FIELD_NAME]RequiredPickListType">  
<restriction base="string">  
  <enumeration value="value1" />  
  <enumeration value="value2" />  
  …  
</restriction>  
</simpleType>  
```  
  
 [FIELD_NAME] = 業務元件中的挑選清單欄位名稱  
  
 以下代表靜態繫結的挑選清單型別的 proxy 體驗：  
  
```  
[BC]InsertRecord[] insertRecs = new [BC]InsertRecord[1];  
insertRecs[0] = new [BC]InsertRecord();  
insertRecs[0].[BC_STATIC_PICKLIST_FIELD] = [BC_PICKLIST_FIELD_NAME]OptionalPickListType.value1;  
```  
  
 [BC_STATIC_PICKLIST_FIELD] = BC 靜態繫結的挑選清單欄位  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)