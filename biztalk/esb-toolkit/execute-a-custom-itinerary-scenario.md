---
title: 執行自訂路線案例 |Microsoft Docs
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
ms.openlocfilehash: 9dc7b746f636b6f90462d296f12827fb0492dd23
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009551"
---
# <a name="execute-a-custom-itinerary-scenario"></a>執行自訂路線案例
您可以使用路線測試用戶端應用程式執行自訂路線案例。  

### <a name="to-execute-a-custom-itinerary-scenario-using-the-itinerary-test-client-application"></a>若要執行自訂路線案例使用路線測試用戶端應用程式  

1. 在 Windows 檔案總管中，開啟資料夾 \Source\Samples\Itinerary\Source\ESB。您的安裝位置的 Itinerary.Test\bin\Debug[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]取樣，並啟動名為 Esb.Itinerary.Test.exe 應用程式。  

2. 選取中的服務型別**ServiceType**下拉式清單中，指定要求的名稱，然後再選取**IsRequestResponse**核取方塊，如果這是要求/回應作業。 您可以指定雙向作業，並選擇要使用 WCF 的路線 Web 服務版本;若要這樣做，請選取 核取方塊後**Web 服務選項**應用程式視窗的頂端區段。  

3. 若要指定具有所選的服務中使用解析程式**AddResolversfortheService**視窗中，選取解析程式從下拉式清單中，輸入，然後再按一節**AddResolver**。 您可以視需要新增一個以上的解析程式。 新增所有必要的解析程式之後，請按一下**AddService**按鈕以新增這個服務引動過程的路線。  

4. 如果您想要將更多服務引動過程新增至路線，重複步驟 2 和 3。 您也可以使用**RemoveService**並**ClearServices**按鈕，以修改的服務清單中的路線。  

5. 如果您想要在另一次重複執行目前的路線，磁碟儲存完成目前的路線，即可**SaveItinerary**  按鈕。 您可以重新載入，即可**LoadItinerary**  按鈕。 這表示您沒有服務和解析程式指定行程中，每次您執行此案例中使用不同的訊息或路線的 Web 服務的設定。  

6. 載入適當的訊息。 若要這樣做，請輸入的路徑和名稱中的訊息**LoadMessage**文字方塊或按一下省略符號按鈕 （...），並選取必要的訊息檔案。  

7. 按一下  **SubmitRequest**按鈕來提交訊息以進行您所指定的路線設定的處理。 如果處理傳回的結果，這會顯示在**結果**文字方塊。
