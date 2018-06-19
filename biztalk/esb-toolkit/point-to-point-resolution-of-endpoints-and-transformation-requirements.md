---
title: 端點的轉換需求點對點解析 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4c570bf-8274-4779-ae83-2aef2bf57ded
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8899c5f713f1c9ebfe299d3e431754dd8b9794d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294462"
---
# <a name="point-to-point-resolution-of-endpoints-and-transformation-requirements"></a>點對點的端點和轉換需求的解決方式
在此使用情況下，Web 服務用戶端會呼叫 Web 服務，而不需要透過 ESB。 直接通訊的兩個點，但用戶端會發出的呼叫之前，它必須解決的 Web 服務端點。 呼叫 Web 服務可以是單向或要求-回應。 達到這個目的的一個方法是使用 ESB 的動態解析功能，如圖 1 所示。  
  
 ![點 &#45; 若要 &#45;端點的端點解析](../esb-toolkit/media/ch3-pointtopoint.gif "Ch3 PointToPoint")  
  
 **圖 1**  
  
 **解決使用 UDDI 端點**  
  
 解析程式服務 」 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。 此範例示範如何呼叫 ESB 解析程式服務來執行解析，可讓您測試解析，因為您正在開發的後端存放區，例如通用描述、 探索與整合 (UDDI)，XML 路徑語言 (XPath) 的內容Static 或 BizTalk Server 商務規則引擎中的原則。  
  
 如需詳細資訊，請參閱[安裝及執行 「 解析程式服務 」 範例](../esb-toolkit/installing-and-running-the-resolver-service-sample.md)。