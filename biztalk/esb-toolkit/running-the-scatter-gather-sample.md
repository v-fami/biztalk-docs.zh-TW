---
title: "執行分散-集中範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53676974-ea1f-4c95-9dbb-98fff92286fa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7dcafa519aac074ccb339373a591b590846c9341
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-scatter-gather-sample"></a>執行分散-集中範例
分散-集中範例會使用 Windows Form 測試用戶端應用程式隨附路線上手範例，示範此模式如何套用路線服務的功能。  
  
 **若要執行分散-集中範例**  
  
1.  如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。  
  
2.  在 Windows 檔案總管] 中開啟資料夾 \Source\Samples\Itinerary\Source\ESB。安裝所在的 Itinerary.Test[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再啟動 [名為 Esb.Itinerary.Test.exe 應用程式。  
  
3.  按一下**LoadItinerary**按鈕，然後再選取 範例路線名為 ScatterGatherItinerary.xml \Source\Samples\ScatterGather\Itineraries 資料夾中的。  
  
4.  清除**為要求回應**核取方塊，讓應用程式將會執行單向路線服務的作業。  
  
5.  （選擇性）設定**使用 WCF 服務**核取方塊，如果您想要使用 OnRamp.Itinerary.Response.WCF 應用程式接收位置而不使用預設 OnRamp.Itinerary.Response.SOAP 接收位置。  
  
6.  按一下**LoadMessage**按鈕，然後再從 \Source\Samples\Itinerary\Test\Data 資料夾選取 NAOrderDoc.xml 範例訊息。  
  
7.  按一下**SubmitRequest**  按鈕，將要求傳送至路線上手服務。 開啟資料夾 \Source\Samples\DynamicResolution\Test\FileDrop\Out 以查看回應訊息。  
  
 如需如何散佈蒐集的範例使用 ESB 行程服務資訊，請參閱[分散-集中範例的運作方式](../esb-toolkit/how-the-scatter-gather-sample-works.md)。