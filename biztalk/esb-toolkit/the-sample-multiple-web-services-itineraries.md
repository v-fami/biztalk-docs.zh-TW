---
title: "此範例多個 Web 服務旅 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f67a4c6-b547-4261-ab3f-db78603ac588
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df8beeda266ae29eb4bb3e7c2a373c9ac6fc2b2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-sample-multiple-web-services-itineraries"></a>此範例多個 Web 服務的行程
下表列出所有預先定義路線檔案包含多個 Web 服務範例。 這些位於 \Source\Samples\MultipleWebServices\Itineraries 資料夾中。  
  
|檔案名稱|Description|  
|---------------|-----------------|  
|OneWayMessagingMultipleServices.xml|這個單向路線 CNOrderDoc 訊息 NAOrderDoc 訊息轉換，然後將其路由至使用匝道 DynamicResolutionSolicitResp 加拿大訂單服務。 回應則轉換至 CNOrderDoc 訊息使用傳訊為基礎的轉換服務，然後它會路由傳送一次至使用匝道 DynamicResolutionSolicitResp 加拿大訂單服務。 傳回的回應會路由至使用路由服務在 Source\Samples\DynamicResolution\Test\Filedrop\Out 資料夾。|  
|TwoWayMessagingMultipleServices.xml|這個雙向路線 CNOrderDoc 訊息 NAOrderDoc 訊息轉換，然後將其路由至加拿大訂單服務。 它接著會從加拿大訂單服務回應、 將其轉換至 CNOrderDoc 訊息，然後再傳送至加拿大訂單服務。 然後會將結果傳回給呼叫者。 所有的轉換和路由會將透過傳訊服務。 這兩個關閉-坡道提升使用 DynamicResolutionSolicitRespForwarder 傳送埠。|  
|TwoWayMessagingOrchestrationMultipleServices.xml|這個雙向行程使用訊息服務 CNOrderDoc 訊息，NAOrderDoc 訊息轉換，然後它會路由傳送該訊息加拿大順序使用與服務 DynamicResolutionSolicitRespForwarder 傳送埠。 回應轉換使用協調流程為基礎的實作 「 轉換 」 服務，並將它然後傳遞至自訂 Microsoft.Practices.ESB.Routing.TwoWay 協調流程為基礎路線服務範例的一部分。 此服務會傳送訊息至相關聯的解析程式 （在此情況下，加拿大訂單服務），所指定的 Web 服務，然後它會接收並從服務傳回回應。 然後，此回應會傳送回呼叫端。|  
|TwoWayOrchestrationsMultipleServices.xml|這個雙向行程使用訊息服務 CNOrderDoc 訊息，NAOrderDoc 訊息轉換並再使用 Microsoft.Practices.ESB.Routing.TwoWay 協調流程來將該訊息路由至加拿大訂單服務，並傳回結果。 訊息則會轉換回 CNOrderDoc 訊息使用協調流程為基礎的轉換服務;之後，它會傳送回加拿大使用 Microsoft.Practices.ESB.Routing.TwoWay 協調流程為基礎路線服務的訂單服務。 然後會將結果傳回給呼叫者。|  
|TwoWay 部分-選取器 Required.xml|路由 NAOrderDoc 訊息服務傳送訊息給加拿大訂單服務透過 DynamicResolutionSolicitResp 匝道這兩個方式路線使用。 NAOrderDoc 轉換為 CNOrderDoc 使用傳訊為基礎的轉換服務和加拿大的服務呼叫。 然後會將回應傳回至呼叫端。|