---
title: CallOrchestration （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- orchestrations, calling
- examples, orchestrations
ms.assetid: 0c4194f0-c1e2-419a-8a1a-a3c96e8d2667
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 614cbb4531d0d7052263e5e4c7d73ec209e9b685
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021876"
---
# <a name="callorchestration-biztalk-server-sample"></a>CallOrchestration （BizTalk Server 範例）
CallOrchestration 範例示範如何從一個協調流程呼叫另一個 BizTalk 協調流程。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例示範使用下列步驟順序呼叫另一個協調流程的協調流程：  
  
1.  主要協調流程收到訂單 (PO) 訊息。  
  
2.  主要協調流程呼叫次要協調流程，以決定 PO 的出貨價格。  
  
3.  次要協調流程計算要求的出貨價格，然後將它傳回主要協調流程。  
  
4.  主要協調流程使用傳回的出貨價格更新 PO 訊息。  
  
5.  主要協調流程將更新的 PO 訊息放到資料夾中供您檢閱。  
  
## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 此範例的主要目的是為您顯示如何從一個協調流程呼叫另一個協調流程。 呼叫協調流程的功能可讓您將商務程序切割為可重複使用的元件。 您可將常用的程序列入個別的協調流程中，供其他人重複使用。  
  
 在此範例中，**呼叫的協調流程**receivePO.odx 中的圖形叫用 findShippingPrice.odx，並會等待巢狀協調流程 findShippingPrice.odx 計算並傳回出貨價格傳送購買之前順序。 協調流程 findShippingPrice.odx 使用下列邏輯計算出貨價格：  
  
```  
If ( weight * shippingRate ) < minShippingPrice Then  
    shippingPrice = minShippingPrice  
Else  
    shippingPrice = weight * shippingRate  
End If  
```  
  
 範例 PO 輸入檔 InputPO.xml 指定重量為 20，使 PO 輸出訊息將其出貨價格從 10 變更為 20。  
  
> [!NOTE]
>  您無法從不可部分完成的協調流程呼叫執行時間很長的交易。  
  
> [!NOTE]
>  使用差異**呼叫的協調流程**圖形並**啟動協調流程**圖形是，在呼叫協調流程時，呼叫者會等待巢狀的協調流程傳回之後繼續進行。 若是從一個協調流程啟動另一個協調流程，在呼叫者初始化動作之後，呼叫者會繼續進行程序流程中的下一個步驟。 呼叫者所叫用的協調流程會獨立執行，直到完成程序流程。 如需詳細資訊，請參閱 <<c0> [ 如何設定呼叫協調流程圖形](../core/how-to-configure-the-call-orchestration-shape.md)。 另請參閱[如何設定啟動協調流程圖形](../core/how-to-configure-the-start-orchestration-shape.md)。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*範例路徑*\>\Orchestrations\CallOrchestration\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|描述|  
|---------------|-----------------|  
|CallOrchestration.btproj, CallOrchestration.sln|這個範例的專案及解決方案檔案。|  
|CallOrchestrationBinding.xml|用於自動化設定，例如連接埠繫結。|  
|Cleanup.bat|用來解除部署組件，以及將它從全域組件快取中移除。 移除傳送埠和接收埠。 視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|findShippingPrice.odx|做為次要協調流程的 BizTalk 協調流程，從主要協調流程 receivePO.odx 呼叫。|  
|InputPO.xml|符合 PO.xsd 檔案中定義之結構描述的範例 PO 輸入訊息。|  
|PO.xsd|結構描述，定義範例輸入檔案 InputPO.xml 等 PO 輸入訊息的結構，以及定義結構描述中之三個項目的屬性升級。|  
|PropertySchema.xsd|參與結構描述 PO.xsd 中之三個項目之屬性升級的屬性結構描述檔案。|  
|receivePO.odx|做為此範例中之主要協調流程的 BizTalk 協調流程。 它會從接收資料夾擷取 PO 訊息，然後呼叫另一個協調流程 findShippingPrice.odx，來計算和更新出貨價格。|  
|Setup.bat|用來建置和初始化此範例。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
  
#### <a name="to-build-and-initialize-the-callorchestration-sample"></a>建置和初始化 CallOrchestration 範例  
  
1. 在命令視窗中，瀏覽至下列資料夾：  
  
    \<*範例路徑*\>\Orchestrations\CallOrchestration\  
  
2. 執行檔案 Setup.bat，這會執行下列動作：  
  
   - 在 CallOrchestration 資料夾中建立此範例的輸入 (In) 和輸出 (Out) 資料夾。  
  
   - 編譯並部署此範例的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案，包括兩個協調流程。  
  
   - 建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。  
  
   - 啟用接收位置並啟動傳送埠。  
  
> [!NOTE]
>  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。  
  
## <a name="running-this-sample"></a>執行此範例  
  
#### <a name="to-run-the-callorchestration-sample"></a>執行 CallOrchestration 範例  
  
1.  將檔案 InputPO.xml 的複本放置到 In 資料夾。  
  
2.  觀察在 Out 資料夾中建立的 XML PO 更新檔案。 它包含已修改的原始 PO 訊息，此訊息包括如上述說明中計算出的出貨成本。 這個檔案的名稱的格式\< *MessageID*\>.xml，其中*\<MessageID\>* 會產生來唯一識別該訊息的 GUID.  
  
## <a name="uninstalling-this-sample"></a>解除安裝這個範例  
  
#### <a name="to-uninstall-the-callorchestration-sample"></a>解除安裝 CallOrchestration 範例  
  
1. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 命令視窗中，瀏覽至下列資料夾：  
  
    \<*範例路徑*\>\Orchestrations\CallOrchestration\  
  
2. 執行 Cleanup.bat。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程 (BizTalk Server Samples 資料夾)](../core/orchestrations-biztalk-server-samples-folder.md)