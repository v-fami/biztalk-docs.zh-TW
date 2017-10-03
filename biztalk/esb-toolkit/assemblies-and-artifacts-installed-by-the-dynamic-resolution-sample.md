---
title: "組件和動態解析範例所安裝的成品 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d9ffdc4-1721-4202-839c-04e5bffe8668
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f564d2faceca0753d37bd9c045e403f5f016734
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="assemblies-and-artifacts-installed-by-the-dynamic-resolution-sample"></a>組件和成品安裝動態解析範例
下表列出的組件和成品安裝[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]動態解析 」 範例。  
  
|位置|類別目錄|名稱和版本的元件|  
|--------------|--------------|---------------------------------------|  
|BizTalk 應用程式 GlobalBank.ESB|協調流程|(無)|  
|BizTalk 應用程式 GlobalBank.ESB|傳送埠|DynamicResolutionSolicitResp|  
|||DynamicResolutionOneWay|  
|BizTalk 應用程式 GlobalBank.ESB|接收埠|DynamicResolutionReqResp|  
|||DynamicResolution|  
|BizTalk 應用程式 GlobalBank.ESB|接收位置|DynamicResolutionReqResp_SOAP<br /><br /> DynamicResolution_FILE|  
|BizTalk 應用程式 GlobalBank.ESB|結構描述|GlobalBank.ESB.DynamicResolution.Schemas.CNPurchaseOrderResponse 2.0.0.0 版|  
|||GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc 2.0.0.0 版|  
|||GlobalBank.ESB.DynamicResolution.Schemas.NAOrderResponse 2.0.0.0 版|  
|||GlobalBank.ESB.DynamicResolution.Schemas.CNOrderDoc 2.0.0.0 版|  
|||GlobalBank.ESB.DynamicResolution.Schemas.CNOrderResponse 2.0.0.0 版|  
|||GlobalBank.ESB.DynamicResolution.Schemas.CNPurchaseOrderDoc 2.0.0.0 版|  
|BizTalk 應用程式 GlobalBank.ESB|管線|GlobalBank.ESB.DynamicResolution.Pipelines.ESBReceiveSendXMLXML 2.0.0.0 版|  
|||GlobalBank.ESB.DynamicResolution.Pipelines.ESBReceiveXML 2.0.0.0 版|  
|||GlobalBank.ESB.DynamicResolution.Pipelines.ESBPassThrough 2.0.0.0 版|  
|BizTalk 應用程式 GlobalBank.ESB|資源|GlobalBank.ESB.DynamicResolution.Pipelines 2.0.0.0 版|  
|||GlobalBank.ESB.DynamicResolution.Schemas 2.0.0.0 版|  
|||GlobalBank.ESB.DynamicResolution.Transforms 2.0.0.0 版|  
|BizTalk 應用程式 GlobalBank.ESB|原則|CanadaSubmitOrderMaps.xml|  
|||GetCanadaEndPoint.xml|  
|||GetCanadaPurchaseEndPoint.xml|  
|||ResolveMap.xml|  
|||ResolveEndPoint.xml|  
|BizTalk 應用程式 GlobalBank.ESB|詞彙|DynamicRunTimeDocSpecs.xml<br /><br /> DynamicRunTimeEndPoints.xml<br /><br /> DynamicRunTimeMapTypes.xml<br /><br /> DynamicRunTimeServiceActions.xml|  
|BizTalk 應用程式 GlobalBank.ESB|地圖|GlobalBank.ESB.DynamicResolution.Transforms.SubmitPurchaseOrderResponseCN_To_SubmitOrderResponseNA 版本 = 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN 版本 = 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitPurchaseOrderRequestCN 版本 = 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderResponseCN_To_SubmitOrderResponseNA 版本 = 2.0.0.0|  
|全域組件快取|組件|GlobalBank.ESB.DynamicResolution.Pipelines 2.0.0.0 版|  
|||GlobalBank.ESB.DynamicResolution.Schemas 2.0.0.0 版|  
|||GlobalBank.ESB.DynamicResolution.Transforms 2.0.0.0 版|  
|%Program Files %\\[!INCLUDE[prague](../includes/prague-md.md)]\Pipeline 元件|管線元件|(無)|