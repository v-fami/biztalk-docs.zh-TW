---
title: 要求-回應的解析度，端點並轉換需求 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1bfdae-2651-402c-b164-16db663aaa95
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72f442f1d9df457a3c1384f1d717e29c17b433f4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294566"
---
# <a name="request-response-resolution-of-endpoints-and-transformation-requirements"></a>要求-回應的端點和轉換需求的解決方式
在此使用情況下，用戶端應用程式會提交要求訊息至上手，並接收回應。 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]做為用戶端和目標服務端點之間的暫留處理器，並使用 ESB 解析器和配接器架構，執行動態訊息轉換和路由符合上手組態，如圖所示1。  
  
 ![要求 &#45;回應的端點解析](../esb-toolkit/media/ch3-requestresponse.gif "Ch3 要求回應")  
  
 **圖 1**  
  
 **要求-回應的端點和轉換需求的解決方式**  
  
 動態解析 」 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。 它會顯示如何套用動態轉換和解析雙向的情況下使用 XML 路徑語言 (XPath)、 通用描述、 探索與整合 (UDDI)，靜態的或在 BizTalk Server 商務規則引擎中的原則。  
  
 如需詳細資訊，請參閱本文中的雙向傳訊案例[安裝及執行動態解析範例](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)。