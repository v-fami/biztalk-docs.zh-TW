---
title: 擴充服務導向解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scaling, service solutions
- service solution tutorial, scaling
ms.assetid: 6c22a68d-03e7-4174-b612-0e2246aa9413
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3026664d3a365630c93bf1c61d7cf635fdd9dc31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269174"
---
# <a name="scaling-the-service-oriented-solution"></a>擴充服務導向解決方案
若要在維持較低的訊息延遲時擴充解決方案以支援更高的輸送量，您必須使用解決方案的內嵌版本。 內嵌解決方案在與後端系統互動時會略過 MessageBox 資料庫。  
  
 您也可以新增 BizTalk Server 處理伺服器以執行協調流程。 如此可降低各個伺服器的使用率，以便快速處理新的要求。 您也可以擴大 MessageBox 伺服器，以便有足夠的額外容量來處理訊息輸送量。  
  
 不過，對服務導向架構解決方案而言，擁有多個 MessageBox 資料庫，並沒有好處。 多個 MessageBox 需要分散式交易協調器 (DTC) 交易。 這些交易會增加整體訊息延遲。  
  
 您可以藉由排除新增 MQSeries 標頭資訊的管線元件，以降低回應時間。 如需詳細資訊，請參閱[服務導向解決方案的實作重點](../core/implementation-highlights-of-the-service-oriented-solution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [開發服務導向解決方案](../core/developing-a-service-oriented-solution.md)