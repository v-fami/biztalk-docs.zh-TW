---
title: "攔截器 EventSource 項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d78846c1-3984-43af-a13f-9d5c0a66d3b5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35b5cd6b2e872f689988f3d10d18df002f66d6a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="interceptor-eventsource-element"></a>攔截器 EventSource 項目
**EventSource**項目會提供一或多個出現在攔截器組態檔中的事件來源的相關資訊。 除了事件來源名稱，您還必須指出技術和來源的資訊清單。  
  
## <a name="format"></a>格式  
 `EventSource` 項目有三個屬性，而且會根據所包含的結構描述，決定是否使用子項目。 例如，WCF 結構描述 WcfInterceptorConfiguration.xsd 提供了 `NamespaceMapping` 項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性名稱|Description|  
|--------------------|-----------------|  
|名稱|此事件來源的名稱。 此名稱由**OnEvent**參考來源的項目。|  
|技術|裝載資訊清單中所指出事件來源的技術類型。 使用 "WF" 代表 Windows Workflow Foundation，而 "WCF" 代表 Windows Communication Framework。|  
|資訊清單|做為事件來源之類型的組件限定類別名稱。 例如，使用 IPv4 位址的 `TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0, Culture=neutral, PublicKeyToken=b17a5c561934e08`<br /><br /> 如果您沒有公開金鑰 Token，請使用 `PublicKeyToken=null`。|  
  
## <a name="example"></a>範例  
 下列範例包含兩個**EventSource**項目，一個目標 WF 和 WCF 一個做為目標。  
  
```  
<!-- WF -->  
<ic:EventSource Name="OrderWorkflow" Technology="WF" Manifest="SimpleWorkflow.OrderWorkflow, SimpleWorkflow, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
<!-- WCF -->  
<ic:EventSource Name="PurchaseService" Technology="WCF" Manifest="Service.IProcessPOContract, DuplexService, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
```