---
title: "執行多個 Web 服務範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b201c7c3-213a-4009-8872-5a4c1cbb8195
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ec54fabb7ed140fd88b5a2d5a07d788805c741e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-multiple-web-services-sample"></a>執行多個 Web 服務範例
多個 Web 服務範例會使用路線上手範例提供的 Windows Form 測試用戶端應用程式。  
  
 **若要執行多個 Web 服務範例**  
  
1.  如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。  
  
2.  在 Windows 檔案總管] 中開啟資料夾 \Source\Samples\Itinerary\Source\ESB。安裝所在的 Itinerary.Test[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再啟動 [名為 Esb.Itinerary.Test.exe 應用程式。  
  
3.  清除**使用 WCF 服務**核取方塊，以便可以利用用戶端路線。  
  
4.  按一下**負載路線**按鈕，然後再選取其中一個 \Source\Samples\MultipleWebServices\Itineraries 資料夾中的範例預定行程。  
  
5.  選取**兩個方式服務**核取方塊，讓應用程式將會執行雙向路線服務的作業。  
  
6.  按一下**LoadMessage**按鈕，然後再從 \Source\Samples\Itinerary\Test\Data 資料夾選取 NAOrderDoc.xml 範例訊息。  
  
7.  按一下**SubmitRequest**  按鈕，將要求傳送至路線上手服務。 等候回應訊息才會出現在**結果**方塊。  
  
 多個 Web 服務範例如何使用 ESB 行程服務的相關資訊，請參閱[多個 Web 服務範例的運作方式](../esb-toolkit/how-the-multiple-web-services-sample-works.md)。