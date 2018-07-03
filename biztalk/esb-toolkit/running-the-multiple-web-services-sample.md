---
title: 執行多個 Web 服務範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b201c7c3-213a-4009-8872-5a4c1cbb8195
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 765d9785bde94f363ea56178f3cc0f500381d4e9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997519"
---
# <a name="running-the-multiple-web-services-sample"></a>執行多個 Web 服務範例
多個 Web 服務範例會使用路線入口範例提供的 Windows Forms 測試用戶端應用程式。  
  
 **若要執行多個 Web 服務範例**  
  
1. 如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。  
  
2. 在 Windows 檔案總管中，開啟資料夾 \Source\Samples\Itinerary\Source\ESB。您的安裝位置的 Itinerary.Test[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再啟動 名為 Esb.Itinerary.Test.exe 應用程式。  
  
3. 清除**使用 WCF 服務**核取方塊，以便可以利用用戶端路線。  
  
4. 按一下 **負載路線**按鈕，然後再選取其中一個 \Source\Samples\MultipleWebServices\Itineraries 資料夾中的範例路線。  
  
5. 選取 **兩個方式服務**核取方塊，讓應用程式會執行雙向路線服務作業。  
  
6. 按一下  **LoadMessage**按鈕，然後再選取 從 \Source\Samples\Itinerary\Test\Data 資料夾的 NAOrderDoc.xml 範例訊息。  
  
7. 按一下 [ **SubmitRequest** ] 按鈕，將要求傳送至路線入口匝服務。 等候回應訊息才會出現在**結果** 方塊中。  
  
   多個 Web 服務範例如何使用 ESB 路線服務的相關資訊，請參閱[多個 Web 服務範例運作方式](../esb-toolkit/how-the-multiple-web-services-sample-works.md)。