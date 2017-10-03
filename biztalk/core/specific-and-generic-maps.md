---
title: "特定和一般對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps, specific
- maps, generic
ms.assetid: ee26dd13-affb-47c5-961a-f2377129de22
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6ad84e23c3981730ee4cf7655a42d87c46158e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="specific-and-generic-maps"></a>特定與一般對應
當您建立將資料轉換的對應時，您可以建立*特定*或*泛型*對應。  
  
 您可以使用特定對應，以符合特殊交易夥伴的需求。 當您有非常特殊的商務需求或與交易夥伴有特殊的商務協議時，請使用特定對應。 特定對應的優點在於它可自訂以符合特定交易夥伴的商務功能需求。 特定對應的缺點在於它不能與多個交易夥伴搭配使用。 若您將交易夥伴數目與那些交易夥伴交換的不同訊息類型數目相乘，則必須配置足夠的時間與資源來管理所有關聯的對應。  
  
 相反地，一般對應則設計為可搭配多個交易夥伴使用。 因此，您不需要開發與維護特殊商務文件的多個結構描述，而只需要為每個類型的商務文件建立一個結構描述，然後搭配所有交易夥伴使用。 雖然以一個對應搭配多個交易夥伴使用可節省時間與資源，但這些對應並非自訂，所以可能無法符合所有狀況的需求。  
  
 您可能要同時建立特定和一般對應，依照您的商務性質而定。  
  
## <a name="see-also"></a>另請參閱  
 [對應](../core/maps.md)   
 [使用 BizTalk 對應工具建立對應](../core/creating-maps-using-biztalk-mapper.md)