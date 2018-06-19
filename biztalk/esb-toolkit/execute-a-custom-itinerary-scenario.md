---
title: 執行自訂的路線案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fd69e29-e853-4b16-9966-29ab98dd5bea
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8659c5b37cba0520fb4a4c0f4c63c8d6ecff37be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294062"
---
# <a name="execute-a-custom-itinerary-scenario"></a>執行自訂的路線案例
您可以使用路線測試用戶端應用程式執行路線的自訂案例。  
  
### <a name="to-execute-a-custom-itinerary-scenario-using-the-itinerary-test-client-application"></a>若要執行的自訂的路線案例，使用行程測試用戶端應用程式  
  
1.  在 Windows 檔案總管 中開啟資料夾 \Source\Samples\Itinerary\Source\ESB。您的安裝位置的 Itinerary.Test\bin\Debug[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例和啟動名為 Esb.Itinerary.Test.exe 應用程式。  
  
2.  選取的服務型別在**ServiceType**下拉式清單中，指定要求的名稱，然後再選取**IsRequestResponse**核取方塊，如果這是要求/回應作業。 您可以指定雙向作業，並選擇使用 WCF 路線 Web 服務版本。若要這樣做，請選取 核取方塊後**Web 服務選項**應用程式視窗的頂端區段。  
  
3.  若要指定具有所選的服務中使用解析程式**AddResolversfortheService**視窗的區段，選取解析程式輸入從下拉式清單中，然後按一下**AddResolver**。 視需要，您可以新增一個以上的解析程式。 加入所有必要的解析程式之後，按一下**AddService**將叫用的服務新增至路線 按鈕。  
  
4.  如果您想要將多個服務引動過程新增至路線，重複步驟 2 和 3。 您也可以使用**RemoveService**和**ClearServices**按鈕，以修改在路線服務的清單。  
  
5.  如果您想要重複目前行程，在其他時候，完成目前的路線磁碟按一下儲存**SaveItinerary**  按鈕。 您可以重新載入，即可**LoadItinerary**  按鈕。 這表示您沒有指定的服務和解析程式在路線每次您執行此案例中使用不同的訊息或路線的 Web 服務設定。  
  
6.  載入適當的訊息。 若要這樣做，請輸入的路徑和名稱中的訊息**LoadMessage**文字方塊或按一下省略符號按鈕 （...），並選取必要的訊息檔案。  
  
7.  按一下**SubmitRequest**送出訊息以進行處理，您所指定的計劃設定的按鈕。 如果處理程序傳回結果，這會顯示在**結果**文字方塊。