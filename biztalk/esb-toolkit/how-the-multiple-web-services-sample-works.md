---
title: 多個 Web 服務範例運作的方式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 16680ca7-16cc-47df-8c39-a3311d468a46
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b3d9faf350654be69015ea940b6b4f034d4de74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294158"
---
# <a name="how-the-multiple-web-services-sample-works"></a>多個 Web 服務範例運作的方式
多個 Web 服務範例會使用兩種不同技術來呼叫序列中的多個 Web 服務，同時仍然能夠正確的結果傳回給原始呼叫端。 一種方法會在回應管線中，使用自訂管線元件和其他方法使用自訂雙向路由協調流程為基礎路線服務會略過匝道引動過程完成 Web 要求/回應呼叫的需求服務。  
  
 自訂管線元件方法會使用轉寄站管線元件。 此元件有條件地將屬性升級為防止 Microsoft BizTalk 會處理所有的路線服務之前，將訊息路由回到上遞增的傳送管線。  
  
 自訂協調流程為基礎的服務方法會使用包含在 ESB TwoWayRouting 協調流程。在 \Source\Samples\MultipleWebSerivces\Source\ESB MultipleWebServices.Orchestrations 專案。MultipleWebServices.Orchestrations 資料夾。 此服務會處理相關聯的解析程式，以判斷雙向的 Web 服務的端點位址。 然後，它會設定動態 Solict-回應傳送埠命名為 RoutingPort 來傳送訊息至 Web 服務，並將結果傳回至協調流程。 協調流程然後前進的路線，並傳回產生的訊息到 MessageBox。  
  
 此範例包含的行程會使用一個或這兩種方法以確保訊息流程遵循路線所保留。 如需詳細資訊，請參閱[範例多個 Web 服務旅](../esb-toolkit/the-sample-multiple-web-services-itineraries.md)。